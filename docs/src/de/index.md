
Mit [DAVe](https://opensource.muenchen.de/software/dave.html) können Verkehrszählungen in Auftrag gegeben, aufgezeichnet und anhand verschiedener Diagramme grafisch ausgewertet werden.

DAVe besteht aus folgenden Diensten:


* [Backend](https://github.com/it-at-m/dave-backend) mit Java Spring Boot
* drei Frontends mit TypeScript und Vue.js
  * [Admin-Portal](https://github.com/it-at-m/dave-admin-portal) für die Verwaltung
     * [Selbstbedienungsportal](https://github.com/it-at-m/dave-selfservice-portal), in dem die Betreiber der Zählstellen ihre Datensätze manuell hochladen können
  * [Frontend](https://github.com/it-at-m/dave-frontend) zur Anzeige der Zählstellen auf der Karte
  * [EAI-Berichte](https://github.com/it-at-m/dave-eai) (optional) Unternehmensanwendungsintegration für andere Spezialverfahren (z. B. Ausgabe der Koordinaten aller Zählstellen in einer CSV-Datei, Empfang der Daten aller Zählungen für einen bestimmten Monat im JSON-Format).


![Architektur](../../../../img/DAVe_Architektur_LS2.drawio.png)


## Persistenz

Die Daten werden in zwei verschiedenen Datenbanken gespeichert:

* Die für die Suche relevanten Daten, wie Standort- oder Straßennamen, werden in ElasticSearch gespeichert. Dies ermöglicht eine sehr leistungsfähige Suche mit Suchvorschlägen in Echtzeit.
* Die Verkehrsdaten aus den Zählungen, die für die Suche nicht benötigt werden, werden in einer relationalen Datenbank PostgreSQL gespeichert.

## Konfiguration

### Identitäts- und Zugriffsverwaltung

Die Identitäts- und Zugriffsverwaltung für alle drei Frontends wird mit KeyCloak verwaltet.
[Beispiel für eine KeyCloak-Konfiguration](https://github.com/it-at-m/dave-backend/blob/sprint/sso-config/sso-client.json)


### Stadtbezirke

DAVe strukturiert die Zählbezirke entsprechend den Stadtbezirken.
Um diese Stadtbezirke zu konfigurieren, muss die Variable „city-district-mapping-config-url” in der [dave-backend application.yml](https://github.com/it-at-m/dave-backend/blob/sprint/src/main/resources/application.yml) gesetzt werden.
Diese Datei muss dann über ConfigMap zum Klassenpfad hinzugefügt werden.

[Diese ConfigMap muss als Vorlage erstellt werden.](https://github.com/it-at-m/helm-charts/issues/98)


## Bereitstellung

DAVe __sollte__ über [Helm Chart](https://artifacthub.io/packages/helm/it-at-m/dave?modal=install) installiert und betrieben werden.
Für einen ersten Einblick oder für Entwicklungsumgebungen, um zu sehen, was DAVe zu bieten hat, stellen wir jedoch eine [Docker-Compose-Datei](docker-compose.md) zur Verfügung.
