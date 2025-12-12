# DAVe

> Under construction

With [DAVe](https://opensource.muenchen.de/software/dave.html), traffic counts can be commissioned, recorded and graphically evaluated using various diagrams.

* User Manual: [2025_DAVe_Anwenderhandbuch_Datenportal_v1.1.pdf](/2025_DAVe_Anwenderhandbuch_Datenportal_v1.1.pdf) (german)
* Developer Manual: [/docs](/docs/src/index.md) (english)


### Stack
* Java 21
* Spring Boot 3
* ElasticSearch 8
* PostgreSQL
* Typescript
* Vuejs 3
* Vuetify 3
* Leaflet

### Architecture

![Architecture](docs/src/img/Architektur_LS2.drawio.png)


* [Data Portal](https://github.com/it-at-m/dave-frontend)
* [Admin Portal](https://github.com/it-at-m/dave-admin-portal)
* [Selfservice Portal](https://github.com/it-at-m/dave-selfservice-portal)
* [Backend-Service](https://github.com/it-at-m/dave-backend)
* [EAI Reports](https://github.com/it-at-m/dave-eai)
* _EAI S3_ Still under construction.
* _EAI GEO_ Internal component for provisioning of traffic detector counts. Not published as Opensource.


## Roadmap

### Q1 2025: 
- Start integrating counting data from traffic detectors

### Q4 2025
- Release the detector interface
- Start integrating counting data from pedestrian traffic

### Q1 2026
- Implement tenant specific configurations
- Gather all repositories in one mono repo

### Q2 2026
- Release pedestrian traffic features
