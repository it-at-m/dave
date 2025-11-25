# Inhaltsverzeichnis

tbd

# CSV-Datei

# Namenskonvention beim Dateinamen

Für eine Zählung ist je in der Zählung berücksichtigten Knotenarm eine CSV-Datei zu erstellen. 
Die Namenskonvention der CSV-Datei ist wie folgt.

`<ZAEHLSTELLENNUMMER>_<DATUM>_Knotenarm_<KNOTENARM_NUMMER>.csv`

| Element            | Beschreibung                                                                                                                                             | Beispiel   |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| ZAEHLSTELLENNUMMER | Die alphanumerische Nummer der Zählstelle                                                                                                                | -          |
| DATUM              | Das Tagesdatum der Zählung im [ISO-Format](https://de.wikipedia.org/wiki/ISO_8601) (`YYYY-MM-DD`)                                                        | 2021-10-06 |
| KNOTENARM_NUMMER   | Die Nummer des Knotenarms welcher durch die CSV-Datei repräsentiert wird. Bei einer Verkehrsbeziehung handelt es sich um die Nummer des Quellknotenarms. |            |

# Dateiformat

|              |                |
|--------------|----------------|
| Dateiendung  | `.csv`         |
| Trennzeichen | Semikolon `; ` |
| Kodierung    | UTF-8          |

# Metainformationen im Header der CSV-Datei

Jede CSV-Datei enthält zu Beginn einen zweizeiligen und elfspaltigen Header mit Metainformationen zur Zählung.

```csv
Zählstellennummer;Zählart;Datum;Knotenarmnummer;;;;;;;
61103;<ZAEHLART>;2022-07-06;4;;;;;;;
```

| Headerfeld        | Beschreibung                                                                                                                                             |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Zählstellennummer | Die alphanumerische Nummer der Zählstelle                                                                                                                |
| Zählart           | Das Kürzel der beauftragten Zählart                                                                                                                      |
| Datum             | Das Tagesdatum der Zählung im [ISO-Format](https://de.wikipedia.org/wiki/ISO_8601) (`YYYY-MM-DD`)                                                        |
| Knotenarmnummer   | Die Nummer des Knotenarms welcher durch die CSV-Datei repräsentiert wird. Bei einer Verkehrsbeziehung handelt es sich um die Nummer des Quellknotenarms. |

# Zählinformationen in der CSV-Datei

Nach den Header mit dem Metainformationen zur Zählung beginnt ab der dritten Zeile der eigentliche Inhalt mit den Zählungsdaten.
Die dritte Zeile der CSV-Datei enthält die Spaltenüberschriften für die in den nachfolgenden Zeilen aufgelisteten Zähldaten.

```csv
Zählstellennummer;Zählart;Datum;Knotenarmnummer;;;;;;;
61103;<ZAEHLART>;2022-07-06;4;;;;;;;
Intervallnummer;nach;Strassenseite;Richtung;Pkw;Lkw;Lz;Bus;Krad;Rad;Fuss
25;<NACH>;<HIMMELSRICHTUNG>;<BEWEGUNGSRICHTUNG>;1;0;0;0;0;0;0
```
| Spaltenfeld     | Beschreibung                                                                                                                                                                                           |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Intervallnummer | Die mit der Ziffer 1 beginnende aufsteigende Nummer des fünfzehnminütigen Intervalls eines Tages.                                                                                                      | 
| nach            | Der Zielknotenarm bei Zählen einer Verkehrsbeziehung. Handelt es sich um eine Zählung welche keine Verkehrsbeziehnung mit einem Quell- und Zielknotenarm darstellt, so ist dieses Feld leer zu lassen. |
| Strassenseite   | tbd                                                                                                                                                                                                    |
| Richtung        | tbd                                                                                                                                                                                                    |
| Pkw             | Die Anzahl der gezählten Personenkraftwagen als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                      |
| Lkw             | Die Anzahl der gezählten Lastkraftwagen als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                          |
| Lz              | Die Anzahl der gezählten Lastzüge als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                                |
| Bus             | Die Anzahl der gezählten Busse als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                                   |
| Krad            | Die Anzahl der gezählten Krafträder als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                              |
| Rad             | Die Anzahl der gezählten Fahrräder als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                               |
| Fuss            | Die Anzahl der gezählten Fußgänger als ganzzahlige Dezimalzahl. Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                               |


