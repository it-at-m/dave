
With [DAVe](https://opensource.muenchen.de/software/dave.html), traffic counts can be commissioned, recorded and graphically evaluated using various diagrams.

DAVe consists of the following services:

* [backend](https://github.com/it-at-m/dave-backend) with Java Spring Boot
* three frontends with TypeScript and Vue.js 
    * [admin-portal](https://github.com/it-at-m/dave-admin-portal) for administraton
    * [selfservice-portal](https://github.com/it-at-m/dave-selfservice-portal) for counting point operators can upload their data records manually here
    * [frontend](https://github.com/it-at-m/dave-frontend) to see the counting points on the map
* [EAI Reports](https://github.com/it-at-m/dave-eai) (optional) Enterprise application integration for other specialist procedures (e.g. output coordinates of all counting points in a CSV file, receive data of all counts for a specific month in json format).

Further details in the [System specification](./de/SysSpec-arc42.md) (only in German)


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

### Map center
DAVe's default map center is Munich Central. This can be configured through the dave.map.center attributes 
as in [dave-backend application.yml](https://github.com/it-at-m/dave-backend/blob/sprint/src/main/resources/application.yml). 

[This ConfigMap must be created as a template.](https://github.com/it-at-m/helm-charts/issues/98)

### Map layers

The maps displayed in DAVe can be configured in the [dave-backend application.yml](https://github.com/it-at-m/dave-backend/blob/sprint/src/main/resources/application.yml). The two variables `dave.map.base-layers` and `dave.map.overlay-layers` each contain a list of map layers.

The map layers configured in the `dave.map.base-layers` variable are the base maps. By default, the first item in the list is displayed in DAVe. Other maps can be selected in the GUI. At least one map layer must be configured for the backend to start.

The overlay layers configured in the `dave.map.overlay-layers` variable can be displayed in addition to the base maps. They can be selected in the GUI. These layers can represent features such as city districts or traffic light locations on the map.

## Deploy

DAVe __should be__ installed and operated via [helm chart](https://artifacthub.io/packages/helm/it-at-m/dave?modal=install).
But for a basic peek or development environments on what DAVe has to offer, we provide a [docker-compose file](docker-compose.md).


