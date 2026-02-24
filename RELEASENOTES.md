# Release-Notes

## [Sprint 6] 2026-02-04 - 2026-02-25
* Anpassungen des Datenmodells mit Änderungen der Entität `Fahrbeziehungen` zu `Verkehrsbeziehungen` und Erweiterung um den `Längsverkehr` und `Querungsverkehr`. Es handelt sich um eine Schnittstellenänderung, die nicht rückwärtskompatibel ist. ([FV-105](https://jira.muenchen.de/browse/FV-105))
* Anpassung der Steuerung des Filtermenüs Zeitauswahl. ([FV-149](https://jira.muenchen.de/browse/FV-149))
* Anpassung der Steuerung des Filtermenüs Fahrzeugauswahl. ([FV-150](https://jira.muenchen.de/browse/FV-150))
* Hierarchie der Fahrzeugart bezogenen Daten für den Belastungsplan überarbeitet ([FV-225](https://jira.muenchen.de/browse/FV-225))
* CSV-Validierung für das Feld "nach" implementiert ([FV-241](https://jira.muenchen.de/browse/FV-241))

## [Sprint 5] 2026-01-14 - 2026-02-03
* Konfiguration von mandanten-spezifischen Einstellungen (Datenportal-Header, Kartenzentrum) ([FV-94](https://jira.muenchen.de/browse/FV-94), [FV-161](https://jira.muenchen.de/browse/FV-161), [FV-162](https://jira.muenchen.de/browse/FV-162))
* Hochladen und Plausibilisieren der Fußverkehrsdaten ([FV-60](https://jira.muenchen.de/browse/FV-60))
* Keycloak SSO-Config bereitstellen und dokumentieren ([FV-68](https://jira.muenchen.de/browse/FV-68))
* Bug: Anzeige der Verkehrsarten im Adminportal beim Bearbeiten einer Zählung ([FV-179](https://jira.muenchen.de/browse/FV-179))
* Bug-Produktion: Falsche Vorauswahl der Verkehrsarten nach einer Änderung der Zeitauswahl im Datenportal ([FV-148](https://jira.muenchen.de/browse/FV-148))
* Bug-Produktion: Standardmäßige Anzeige der Layer für Stadtbezirke und -viertel beim Anlegen einer neuen Zählstelle ([FV-172](https://jira.muenchen.de/browse/FV-172))
* Bug-Produktion: Der Abstand „Logo – Text“ beim PDF-Report entspricht nicht den Gestaltungsrichtlinien der LHM. ([FV-180](https://jira.muenchen.de/browse/FV-180))
* LCM: Umstellen des Optionsmenüs der Zählstellen auf v-model. ([FV-160](https://jira.muenchen.de/browse/FV-160))
* Opensourcesetzung der Geodaten-EAI. ([FV-107](https://jira.muenchen.de/browse/FV-107))

## [Sprint 4] 2025-12-03 - 2026-01-14 
* Document-Storage Opensource gestellt [FV-110](https://jira.muenchen.de/browse/FV-110))
* Sample Stack aktualisiert ([FV-101](https://jira.muenchen.de/browse/FV-101))
* Auswahl der Fahrbeziehung für die neuen Zählarten im Adminportal ermöglicht ([FV-97](https://jira.muenchen.de/browse/FV-97))
* Validierung der ausgewählten Knotenarme abhängig von der Zählart eingebaut. ([FV-102](https://jira.muenchen.de/browse/FV-102))
* Validierung der ausgewählten Kategorien abhängig von der Zählart eingebaut. ([FV-104](https://jira.muenchen.de/browse/FV-104))
* Beim Klick auf den Homebutton wird nun die Gesamtauswertung zurückgesetzt. ([DAVE-788](https://jira.muenchen.de/browse/DAVE-788))
* Umstellung von policy-as-code auf dependency-review  ([FV-157](https://jira.muenchen.de/browse/FV-157))

## [Sprint 3] 2025-10-22 - 2025-11-12
* Konfigurierbarkeit des Report-Logos ermöglicht ([FV-51](https://jira.muenchen.de/browse/FV-51))
* Swagger-UI in Backend integriert ([FV-93](https://jira.muenchen.de/browse/FV-93))
* Dokumentation der CSV-Struktur und Verlinkung der Dokumentation in Self-Service-Portal ([FV-35](https://jira.muenchen.de/browse/FV-35), [FV-59](https://jira.muenchen.de/browse/FV-59))
* Bugfix bei Datumsformat während Verwendung der englischen Sprache im Browser ([FV-90](https://jira.muenchen.de/browse/FV-90))
* Integration der neuen Zählarten FjS, QjS und Qu in Backend, Datenportal, Adminportal und Self-Service-Portal ([FV-47](https://jira.muenchen.de/browse/FV-47), [FV-49](https://jira.muenchen.de/browse/FV-49))
* Bugfix bei der Auswahl der Fahrzeuge in der Gesamtauswertung ([DAVE-757](https://jira.muenchen.de/browse/DAVE-757))
* Bugfix bei der Anzeige des Messzeitraums im Belastungsplan ([DAVE-758](https://jira.muenchen.de/browse/DAVE-758))
* Bugfix bei der Anzeige der Anzeige der Gesamtauswertung, wenn RAD und KFZ-Messstellen ausgewählt wurden ([DAVE-759](https://jira.muenchen.de/browse/DAVE-759))
* Optimierung der DAVe-DB für Kalendertage und Unauffällige Tage ([DAVE-767](https://jira.muenchen.de/browse/DAVE-767))
* Bugfix beim Laden der neuangelegten Zählstelle ([FV-91](https://jira.muenchen.de/browse/FV-91))
