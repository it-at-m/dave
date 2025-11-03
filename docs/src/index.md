
With [DAVe](https://opensource.muenchen.de/software/dave.html), traffic counts can be commissioned, recorded and graphically evaluated using various diagrams.

DAVe consists of the following services:

* [backend](https://github.com/it-at-m/dave-backend) with Java Spring Boot
* three frontends with TypeScript and Vue.js 
    * [admin-portal](https://github.com/it-at-m/dave-admin-portal) for administraton
    * [selfservice-portal](https://github.com/it-at-m/dave-selfservice-portal) for counting point operators can upload their data records manually here
    * [frontend](https://github.com/it-at-m/dave-frontend) to see the counting points on the map
* [EAI Reports](https://github.com/it-at-m/dave-eai) (optional) Enterprise application integration for other specialist procedures (e.g. output coordinates of all counting points in a CSV file, receive data of all counts for a specific month in json format).


![Architecture](../../img/DAVe_Architektur_LS2.drawio.png)


## Persistence

The data is stored in two different databases: 

* the data relevant for the search, such as location or street names, is stored in ElasticSearch. This enables a very high-performance search with search suggestions in real time. 
* The traffic data from the counts that is not required for the search is stored in a relational database PostgreSQL.

## Configuration

### Identity and access management

Identity and access management for all three frontends are managed with KeyCloak.
[Example KeyCloak configuration](https://github.com/it-at-m/dave-backend/blob/sprint/sso-config/sso-client.json)


### urban districts

DAVe structures the counting districts according to city districts.
To configure these city districts, the variable ‘city-district-mapping-config-url’ must be set in the [dave-backend application.yml](https://github.com/it-at-m/dave-backend/blob/sprint/src/main/resources/application.yml).
This file must then be added to the classpath via ConfigMap.

[This ConfigMap must be created as a template.](https://github.com/it-at-m/helm-charts/issues/98)


## Deploy

DAVe __should be__ installed and operated via [helm chart](https://artifacthub.io/packages/helm/it-at-m/dave?modal=install).
But for a basic peek or development environments on what DAVe has to offer, we provide a [docker-compose file](docker-compose.md).


