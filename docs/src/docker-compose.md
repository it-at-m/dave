


DAVe __should be__ installed and operated via [helm chart](https://artifacthub.io/packages/helm/it-at-m/dave?modal=install).
But for a basic peek or development environments on what DAVe has to offer, we provide a docker-compose file that starts up the following components:

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
