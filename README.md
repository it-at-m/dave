# DAVe

[DAVe](https://opensource.muenchen.de/software/dave.html) 
(short for "Datenbank und Auswertung von Verkehrszählungen", meaning "Database and Analysis of Traffic Counts"),
is a specialized system to help Mobility Departments to document and analyze traffic trends.

With [DAVe](https://opensource.muenchen.de/software/dave.html), traffic counts can be commissioned, recorded and graphically evaluated using various diagrams.


## Stack

* Java 21
* Spring Boot 3
* ElasticSearch 8
* PostgreSQL
* Typescript
* Vuejs 3
* Vuetify 3
* Leaflet


## Architecture

![Architecture](docs/src/img/Architektur_LS2.drawio.png)


* [Data Portal](https://github.com/it-at-m/dave-frontend)
* [Admin Portal](https://github.com/it-at-m/dave-admin-portal)
* [Selfservice Portal](https://github.com/it-at-m/dave-selfservice-portal)
* [Backend-Service](https://github.com/it-at-m/dave-backend)
* [EAI Reports](https://github.com/it-at-m/dave-eai)
* [Document-Storage](https://github.com/it-at-m/dave-document-storage)
* _EAI GEO_ Internal component for provisioning of traffic detector counts. Not published as Opensource.


## Roadmap

<img src="img/DAVe_Roadmap.png" alt="Roadmap" width="850">


A detailed board of what opensource features and issues are currently treated can be observed under:
[DAVe working public](https://github.com/orgs/it-at-m/projects/14/views/1)


## Set up

To get started with the DAVe components please refer to the documentation here: https://github.com/it-at-m/dave-backend/blob/sprint/stack/readme.md#dave-sample-stack


## Documentation

We offer different sources of documentation, depending on the role of the reader:
* User Manual: [2025_DAVe_Anwenderhandbuch_Datenportal_v1.1.pdf](2025_DAVe_Anwenderhandbuch_Datenportal_v1.1.pdf) (german)
* Developer Manual: [/docs](docs/src/index.md) (english)


## Contributing

If you want to contribute to the project, please look into our [CONTRIBUTING.md](/CONTRIBUTING.md)


## License

Distributed under the MIT License. See [LICENSE](LICENSE) file for more information.


## Contact

it@M - opensource@muenchen.de