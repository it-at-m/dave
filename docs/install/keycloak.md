# DAVe — Keycloak integration and Helm installation

This document describes how to integrate DAVe (backend, frontends and EAIs) with Keycloak when installing via the Helm chart. 
It focuses on Keycloak-specific configuration, the Spring Boot properties you must provide, recommended spring.profiles.active values 
and examples.

Contents
- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Quickstart (Helm) — Keycloak enabled](#quickstart-helm--keycloak-enabled)
- [Keycloak realm & client setup](#keycloak-realm--client-setup)
- [All Spring Boot properties to initialize](#all-spring-boot-properties-to-initialize)
- [spring.profiles.active — recommended profiles](#springprofilesactive--recommended-profiles)

---

## Overview

DAVe uses OAuth2/OIDC for authentication and authorization. In production we recommend integrating DAVe with Keycloak (or another OIDC provider). 
The backend typically operates as a resource server (validating JWTs), the EAIs use OAuth2 client credentials flow 
and the user-facing SPAs use an authorization code flow (with PKCE).

This guide explains:
- How to configure Keycloak (realm, clients)
- Which Spring Boot properties to set (and how they map to environment variables)
- Which profiles to activate with spring.profiles.active
- How to pass values into the Helm chart (values.yaml) safely using Secrets/ConfigMaps

---

## Prerequisites

- A running Keycloak instance reachable from the cluster (internal or external)
- A Helm-enabled Kubernetes cluster (see docs/install/kubernetes.md for general prerequisites)
- Kubernetes secrets for client secrets, DB credentials and S3 credentials (do not store secrets in plaintext in values.yaml)
- Knowledge of your public hostnames (for redirect URIs)

---

## Quickstart (Helm) — Keycloak enabled

1. Prepare Keycloak (see [next section](#keycloak-realm--client-setup)).
2. Store Keycloak client secret in your dave-backend-service-secret in Kubernetes. 
3. Create a values file that sets Keycloak URLs, realm and injects Spring properties via env variables or config maps. See the list of configuration items [below](#all-spring-boot-properties-to-initialize).
4. Install (or upgrade) the chart:

```bash
helm install dave it-at-m/dave --namespace dave -f my-values-keycloak.yaml
# or
helm upgrade dave ./dave -f values.yaml -f values-${ENVIRONMENT}.yaml -f my-values-keycloak.yaml --install
```

5. Verify pods and login flow.

---

## Keycloak realm & client setup

Follow these steps to prepare Keycloak to work with DAVe:
- Create a realm (example: `dave`). 
- Import the client configuration from [sso-client.json](https://github.com/it-at-m/dave-backend/blob/sprint/sso-config/sso-client.json).
- Import the authorization from this [sso-authorisation.json](https://github.com/it-at-m/dave-backend/blob/sprint/sso-config/sso-authorisation.json) into the client.
- Configure the DAVe client roles from [sso-client-roles.json](https://github.com/it-at-m/dave-backend/blob/sprint/sso-config/sso-client-roles.json).

> WARNING: Do not import the referenced client configuration unchanged.
> The linked JSON currently contains a wildcard redirect URI (*) and enables direct access grants. 
> Importing this into a production realm permits redirects to arbitrary destinations; 
> provide an environment-specific configuration with explicit callback URIs 
> and only the required grant types. (github.com)

Important endpoints (Keycloak standard endpoints):
- Issuer URL: https://<keycloak-host>/realms/<realm>
- Authorization endpoint: https://<keycloak-host>/realms/<realm>/protocol/openid-connect/auth
- Token endpoint: https://<keycloak-host>/realms/<realm>/protocol/openid-connect/token
- Userinfo endpoint: https://<keycloak-host>/realms/<realm>/protocol/openid-connect/userinfo
- JWKs URI: https://<keycloak-host>/realms/<realm>/protocol/openid-connect/certs

---

## All Spring Boot properties to initialize

Below is a consolidated list of properties you must set for DAVe backend, frontends and EAIs to integrate with Keycloak. 
You can provide these either via environment variables (recommended) or via application.yml configuration for local development. 
For environment variables, Spring Boot relaxed binding maps uppercase underscored names to property names.

Mapping examples:
- spring.security.oauth2.client.registration.keycloak.client-id
  -> environment variable: SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_KEYCLOAK_CLIENT_ID 

A. Common (for Backend, Frontends & EAIs)
- SPRING_PROFILES_ACTIVE
  -  see [below](#springprofilesactive--recommended-profiles)
  
- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_KEYCLOAK_CLIENTID
  - Example: dave 

- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_KEYCLOAK_CLIENT_SECRET

- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_KEYCLOAK_SCOPE
  - Example: "LHM,LHM_Extended,openid"
  
B. Backend (resource server) recommended properties
- SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUER_URI
  - Example: https://keycloak.example.com/auth/realms/dave
  
- SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_JWK_SET_URI
  - Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/certs
  
- SPRING_SECURITY_OAUTH2_RESOURCE_USERINFOURI
  -  Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/userinfo
  
- SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUERURI
  - Example: https://keycloak.example.com/auth/realms/dave
  
- SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_JWKSETURI
  - Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/certs
  
- SPRING_SECURITY_OAUTH2_CLIENT_PROVIDER_KEYCLOAK_TOKEN_URI
  - Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/token
  
- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_KEYCLOAK_AUTHORIZATION_GRANT_TYPE
    - e.g., client_credentials

- If the project uses Keycloak's adapter (legacy), properties might include:
  - keycloak.realm
  - keycloak.auth-server-url
  - keycloak.resource
  - keycloak.credentials.secret
  - keycloak.bearer-only

C. Frontends (OAuth2 client) properties
- SPRING_SECURITY_OAUTH2_CLIENT_PROVIDER_KEYCLOAK_ISSUERURI: 
  - e.g. https://keycloak.example.com/auth/realms/dave 
  
- SPRING_CLOUD_GATEWAY_SERVER_WEBFLUX_ROUTES_0_URI
  - Example: https://keycloak.example.com/

- SPRING_CLOUD_GATEWAY_SERVER_WEBFLUX_ROUTES_0_FILTERS_0 
  - e.g. RewritePath=/api/sso/userinfo, /auth/realms/dave/protocol/openid-connect/userinfo
  
- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_KEYCLOAK_SCOPE: 
  - Typically: "roles,openid,profile"

D. EAI properties
- SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUERURI
  - e.g. https://keycloak.example.com/auth/realms/dave
  
- SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_JWKSETURI
  - Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/certs

- SPRING_SECURITY_OAUTH2_RESOURCE_USERINFOURI
  - Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/userinfo

E. Geodata-EAI properties
- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_SSO_MOBIDAM_MESSWERTE_AUTHORIZATIONGRANTTYPE 
  - client_credentials 
  
- SPRING_SECURITY_OAUTH2_CLIENT_REGISTRATION_SSO_MOBIDAM_MESSWERTE_CLIENTAUTHENTICATIONMETHOD
  - e.g. client_secret_post

- SPRING_SECURITY_OAUTH2_CLIENT_PROVIDER_SSO_MOBIDAM_MESSWERTE_TOKENURI
  - e.g. https://keycloak.example.com/auth/realms/mobidam/protocol/openid-connect/token

- SPRING_SECURITY_OAUTH2_CLIENT_PROVIDER_KEYCLOAK_TOKEN_URI
  - Typically: https://keycloak.example.com/auth/realms/dave/protocol/openid-connect/token
  
- SPRING_SECURITY_OAUTH2_CLIENT_PROVIDER_SSO-MOBIDAM-MESSWERTE_TOKENURI
  - e.g. https://keycloak.example.com/auth/realms/mobidam/protocol/openid-connect/token


---

## spring.profiles.active — recommended profiles

The "no-security"-Profile is enabled by default. To use Keycloak, you have to disable it in spring.profiles.active per deployment. 
This activates the security mode of all services and protects them against unauthorized access.

Recommended example:
- Backend (resource server): SPRING_PROFILES_ACTIVE=dev


---

