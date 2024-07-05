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

## Installation instructions

Here are the steps to install the necessary stack via docker-compose to start DAVe Frontend (Datenportal):

1. Clone the repository: First, you need to clone the repository by running the following command in the terminal:
```
git clone https://github.com/it-at-m/dave-frontend
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
