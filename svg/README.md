# Readme für die Verwendung der SVG's

Für jede Grafik existieren zwei Dateien. Eine Datei (xxx_inkscape.svg) ist die SVG-Datei zum Bearbeiten mittels des Programms InkScape.
Diese enthält Programm spezifische Elemente und ist daher nicht dazu geeignet direkt im Code genutzt zu werden. Daher muss nach erfolgter Bearbeitung
das SVG als 'Normales SVG' (xxx_plain.svg) gespeichert werden. Diese Datei enthält dann nur noch die SVG konformen Teile, kann aber nicht mehr vernünftig 
mittels InkScape weiterverarbeitet werden.

Die Files (xxx_auswahl_plain.svg) werden im Adminportal, SelfServiceportal und Datenportal verwendet. 
Die Files (xxx_belastungsplan_plain.svg) hingegen werden nur im Datenportal benötigt.


# Aktueller Stand
* Gehbeziehung_auswahl ist fertig und bereits im Test.
* QJS_auswahl ist ebenso fertig und im Test. 
* fjs_belastungsplan ist soweit fertig, bis auf die Legenden in den Ecken. Ebenso fehlt noch die sinnvolle Benennung der ID's für die Knotenarme 5, 6, 7 und 8.
* qu_belastungsplan ist soweit fertig, bis auf die Legenden in den Ecken. Ebenso fehlt noch die sinnvolle Benennung der ID's.
* qjs_belastungsplan ist vom Gerüst her fertig. Bei der Schriftgröße besteht noch Abstimmungsbdarf mit dem Fachbereich. Es gibt hier auch der Wunsch, dass sich die Höhe
der Pfeile prozentual an die Belastung anpasst. Das würde ich aber erst nachgelagert machen, da dies nicht zwingend notwendig ist für den Einbau im Code. Hierbei muss dann darauf geachtet werden,
dass die Position der Pfeile unverändert bleibt und diese gleichmäßig zur Mitte des Pfades hin schrumpfen.

Bei der Benennung der ID's an das Backend halten. Himmelsrichtung für die Straßenseite und die Bewegungsrichtung mittels Ein / Aus kennzeichnen. 
Das muss in allen Plänen passend sein für die spätere Zuordnung im Code.

Die Legenden sollen einheitlich sein. Daher für die neuen Belastungspläne nur einmal erstellen und dann in die anderen beiden einfügen und auf die identischen
Positionen verfrachten. Im Idealfall auch mit dem bestehendem Belastungsplan abgleichen, damit diese weitestgehend gleich sind.

Bei der Querung stehen die Werte in den farbigen Pfeilen, daher muss hier auch immer die passende Schriftfarbe verwendet werden. Diese kann im dazugehörigen Style-Element angepasst werden.