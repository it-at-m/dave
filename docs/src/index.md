
With [DAVe](https://opensource.muenchen.de/software/dave.html), traffic counts can be commissioned, recorded and graphically evaluated using various diagrams.

DAVe was [developed](https://opensource.muenchen.de/in-house-development.html) with these services:

* `backend` with Java Spring Boot
* three frontends with TypeScript and Vue.js 
    * `adminportal-apigateway` for administraton 
    * `selfserviceportal-apigateway` for counting point operators can upload their data records manually here
    * `frontend-apigateway` to see the counting points on the map
* `eai`

## Persistence

The data is stored in two different databases: 

* the data relevant for the search, such as location or street names, is stored in ElasticSearch. This enables a very high-performance search with search suggestions in real time. 
* The traffic data from the counts that is not required for the search is stored in a relational database postgresQL.


## Dependencies

### ElasticSearch


### Postgresql

### KeyCloak

Identity and access management for all three frontends are managed with KeyCloak.
[Example KeyCloak configuration](https://github.com/it-at-m/dave-backend/blob/sprint/sso-config/sso-client.json)


## Deploy

DAVe can be installed and operated via [helm chart](https://artifacthub.io/packages/helm/it-at-m/dave?modal=install).

