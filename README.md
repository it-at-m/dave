# DAVe

<span style="font-size:5.0em;">Under construction</span>

## Business goals
Docs for [DAVe, a application for evaluating traffic counts](https://opensource.muenchen.de/software/dave.html).

## Technical description

### Stack
* Java 11
* Spring Boot
* ElasticSearch
* Postgres
* Typescript
* Vuejs
* Vuetify
* Leaflet

### Architecture

![Architecture](img/DAVe_Architektur_LS2.drawio.png)

**Data Portal**
 See https://github.com/it-at-m/dave-frontend for more infos.

**Admin Portal**
See https://github.com/it-at-m/dave-admin-portal for more infos.

**Selfservice Portal**
See https://github.com/it-at-m/dave-selfservice-portal for more infos.

**Backend-Service**
See https://github.com/it-at-m/dave-backend for more infos.

**EAI Reports**
See https://github.com/it-at-m/dave-eai for more infos.

**EAI S3**
Still under construction.

**EAI GEO**
Internal component for provisioning of traffic detector counts. Not published as Opensource. 

## Installation instructions

For a basic peek on what DAVe has to offer, we provide a docker-compose file that starts up the following components:

* ElasticSearch
* Kibana
* H2 database
* DAVe backend
* DAVe frontend (data portal)

The security functions for login etc. are switched off.

With the preset profile "sample", a sample counting station with a sample count is imported into the database and index.

Here are the steps to install the necessary stack to run the application:

1. Clone the repository: First, you need to clone the repository by running the following command in the terminal:
```
git clone https://github.com/it-at-m/dave-frontend
git checkout sprint
```

2. Install Docker and Docker Compose: You need to have Docker and Docker Compose installed on your system. If you don't have them installed, you can follow the official documentation to install them. You can use the following commands to check if they are installed:
```
docker --version
docker-compose --version
```

3. Build the images: Next, you need to build the Docker images by navigating to dave-frontend-github/stack directory and running the following command in the terminal:
```
docker-compose build
```

4. Start the containers: After the images are built, you can start the containers by running the following command in the terminal:
```
docker-compose up
```

5. Access the application: Once the containers are up and running, you can access it by navigating to http://localhost:8082 in your web browser.

That's it! You have successfully installed and started the application stack for DAVe Frontend.
