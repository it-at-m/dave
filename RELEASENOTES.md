# Release-Notes

## [Sprint 12] 2026-06-11 - 2026-07-01

* Fehlerhafte Pfeilbenennung im Belastungsplan FjS wurde korrigiert ([FV-399](https://jira.muenchen.de/browse/FV-399))
* Hinweistext Differenzdatendarstellung geändert ([FV-420](https://jira.muenchen.de/browse/FV-420))
* Graphische Anpassungen BLP Qu, FjS ([FV-364](https://jira.muenchen.de/browse/FV-364))
* Hinzufügen der Blockauswahl von 19-22 Uhr für 16h-Zählung ([FV-290](https://jira.muenchen.de/browse/FV-290))
* Ausweisung der Zählwerte im BLP für Qu-Zählungen implementiert ([FV-239](https://jira.muenchen.de/browse/FV-239))
* SSP Reiter Knoten&Lage Tabellendarstellung erweitert ([FV-304](https://jira.muenchen.de/browse/FV-304))
* Bugfix in Zeitreihenanzeige und Belastungsplan bezüglich Differenzdatendarstellung ([FV-371](https://jira.muenchen.de/browse/FV-371))
* Bugfix: Verrutschter Pfeil korrigiert in KnotenverkehrForm für Qu ([FV-434](https://jira.muenchen.de/browse/FV-434))

## [Sprint 11] 2026-05-21 - 2026-06-10
* Darstellung langer Straßennamen im Belastungsplan ([FV-366](https://jira.muenchen.de/browse/FV-366), [FV-376](https://jira.muenchen.de/browse/FV-376), [FV-203](https://jira.muenchen.de/browse/FV-203))
* Zentrale Steuerung des Releasings implementiert ([FV-327](https://jira.muenchen.de/browse/FV-327))
* Die Kartenlayer wurden geändert, sodass andere Layer für Stadtbezirke, Stadtviertel und Lichtsignalanlagen verwendet werden ([FV-315](https://jira.muenchen.de/browse/FV-315))
* Belastungspläne QjS, FjS und Qu: Stauchung der Zählwerte entfernt, Schriftarten und -größe angepasst, Position der Legende an bisherige BLPs angeglichen ([FV-373](https://jira.muenchen.de/browse/FV-373))
* Bugfix: Der Belastungsplan wird nun nach einem Zählstellenwechsel über die kleine Karte angezeigt ([FV-374](https://jira.muenchen.de/browse/FV-374))
* BLP QJS Schriftart und Pfeile wie bei bestehenden Zählarten umgesetzt ([FV-354](https://jira.muenchen.de/browse/FV-354))

## [Sprint 10] 2026-04-29 - 2026-05-20
* Ausweisung der Zählwerte im BLP für QjS-Zählungen implementiert ([FV-237](https://jira.muenchen.de/browse/FV-237))
* Fehlerhafter PDF Export korrigiert ([FV-325](https://jira.muenchen.de/browse/FV-325))
* Darstellung BLP Qu ([FV-183](https://jira.muenchen.de/browse/FV-183))
* Konfigurative Einbindung der Kartenlayer in die Anwendung implementiert ([FV-34](https://jira.muenchen.de/browse/FV-34))
* Anpassung der Auswertung Zeitreihe hinsichtlich Fußverkehr ([FV-184](https://jira.muenchen.de/browse/FV-184))
* Bugfix: Stadtbezirke, Stadtviertel und Lichtsignalanlagen werden auf der Karte nun angezeigt ([FV-315](https://jira.muenchen.de/browse/FV-315))
* Bugfix: Der Export der Listenausgabe funktioniert nun. Bisher wurde eine Fehlermeldung geliefert ([FV-319](https://jira.muenchen.de/browse/FV-319))
* Bugfix: Die schematische Darstellung beim PDF-Export der Listenausgabe ist nun korrekt ausgerichtet ([FV-320](https://jira.muenchen.de/browse/FV-320))
* Bugfix: Beim Export des Belastungsplans für die Zählarten QjS und FjS sind der Nordpfeil und die Knotenarmnummern verrutscht. Diese werden nun an der richtigen Stelle angezeigt ([FV-361](https://jira.muenchen.de/browse/FV-361))
* Bugfix: Ergänzung bei BLP Messtellen um größere Abstände zwischen den Werten auf Nord- und Südseite. ([FV-200](https://jira.muenchen.de/browse/FV-200))
* Deaktivieren der Checkbox "Differenzdaten darstellen" im Filtermenü Zählungsvergleich für die neuen Zählarten QjS, FjS und Qu ([FV-293](https://jira.muenchen.de/browse/FV-293))
* Plausibilisierung der Knotenarmnummer beim Hochladen im Selfserviceportal implementiert ([FV-353](https://jira.muenchen.de/browse/FV-353))
* Tech: Automatisieren des Release-workflows ([FV-326](https://jira.muenchen.de/browse/FV-326))

## [Sprint 9] 2026-04-01 - 2026-04-29
* Refaktoring zum Speichern der Zählungen. Beim persistieren der Zählung werden keine Aggregationen über mehrere Bewegungsbeziehungen (Verkehrsbeziehung, Längsverkehr oder Querungsverkehr) mehr durchgeführt. Dies wird nun beim Laden der Zähldaten gemacht. Zusätzlich findet beim persistieren keine Ermittlung der Spitzenstunde mehr statt. Dies wird ebenfalls beim Laden und nach der Aggregationen über die Bewegungsbeziehungen durchgeführt. Es handelt sich um eine Schnittstellenänderung, die nicht rückwärtskompatibel ist. ([FV-126](https://jira.muenchen.de/browse/FV-126))
* Prüfung der CSV-Daten bei Abschließen der Zählung für FJS und QU implementiert ([FV-174](https://jira.muenchen.de/browse/FV-174))
* Gesamtanzahl Tageswert im BLP mit Klammer zeigen ([FV-200](https://jira.muenchen.de/browse/FV-200))
* Anpassung des Reiters "Knoten & Lage" einer Zählung im Self-Serviceportal im die Auflistung der Verkehrsbeziehungen für die neuen Zählarten FjS und Qu aus dem Reiterinhalt zu entfernen. ([FV-295](https://jira.muenchen.de/browse/FV-295))
* Darstellung des Belastungsplans für die Zählungsart FjS implementiert ([FV-182](https://jira.muenchen.de/browse/FV-182))
* Fix um beim Abwählen von Knotenarmen im Adminportal die entsprechenden Verkehrsbeziehungen zu löschen ([FV-296](https://jira.muenchen.de/browse/FV-296))
* Validierungen der Zählarten QjS, FjS und Qu beim Erstellen und Bearbeiten von Zählungen im Adminportal entfernt, um ein einheitliches Speicherverhalten umzusetzen ([FV-287](https://jira.muenchen.de/browse/FV-287))
* Bugfix: Beim Download des CSV-Musters im Selfservice-Portal enthält der Dateiname nun das Datum im korrekten Format `YYYY-MM-DD` ([FV-303](https://jira.muenchen.de/browse/FV-303))
* Bugfix: Bei der Funktion zur Prüfung eines Kalendertages bezüglich Auffälligkeiten kann im Adminportal nur noch ein Kalendertag in der Vergangenheit gewählt werden. ([FV-138](https://jira.muenchen.de/browse/FV-138))
* Bugfix: Hinzufügen des neuen Profil `no-security-messwerte-eai` um den abgesicherten Zugriff auf die messwerte-eai ein oder ausschalten zu können.. ([FV-322](https://jira.muenchen.de/browse/FV-322))
* Anpassung Filtermenü Zählungsvergleich Zeitreihe für die neuen Zählarten ([FV-262](https://jira.muenchen.de/browse/FV-262))
* Ersetzen der Checkbox "Alles auswählen" im Adminportal im Reiter Verkehrsarten durch einen Button und Beheben eines Bugs bei dem der Text der Checkbox/des Buttons "Alles auswählen" anzeigt, obwohl alle Verkehrsarten ausgewählt sind. Außerdem werden die Verkehrsarten bei Änderung im Adminportal nun korrekt gespeichert.  ([FV-323](https://jira.muenchen.de/browse/FV-323))
* Bugfix: Im Zeitauswahl Filter für bestehende Zählarten ist Tageswert ausgegraut wenn nur Rad gewählt ist bei 24h Zählungen ([FV-270](https://jira.muenchen.de/browse/FV-270)).
* Darstellung des Belastungsplans für Zählungsart QjS implementiert ([FV-181](https://jira.muenchen.de/browse/FV-181))
* Kopieren von Zaehlungen ohne Verkehrsbeziehungen, Querungsverkehr und Laengsverkehr wieder ermöglich. ([FV-279](https://jira.muenchen.de/browse/FV-279))
* Bugfix: Die Ausrichtung des Belastungsplans verwendet nun die korrekten Himmelsrichtung-Enums. ([FV-266](https://jira.muenchen.de/browse/FV-266))

## [Sprint 8] 2026-03-18 - 2026-04-01
* Zwei fehlende Semikolon im Self-Service-Portal Download CSV-Template korrigiert. ([FV-268](https://jira.muenchen.de/browse/FV-268))
* Fix um bei Zählungen für die neuen Zählarten QJS, FJS und QU alle Fahrzeugkategorien mit einem Klick an- oder abwählen zu können. ([FV-236](https://jira.muenchen.de/browse/FV-236))
* Filtern nach Verkehrsbeziehungen im Filtermenü  ([FV-130](https://jira.muenchen.de/browse/FV-130))

## [Sprint 7] 2026-02-25 - 2026-03-18

* Umbenennung mehrerer Labeltexte im Datenportal, Adminportal und Selfserviceportal. ([FV-167](https://jira.muenchen.de/browse/FV-167))
* Refactoring hin zur Aggregation über Bewegungsbeziehungen (Verkehrsbeziehung, Laengsverkehr, Querungsverkehr) und Spitzenstundenbildung beim Laden der Zaehldaten einer Zählung. ([FV-127](https://jira.muenchen.de/browse/FV-127))
* Bereinigen der vorberechneten Daten ([FV-128](https://jira.muenchen.de/browse/FV-128))

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
