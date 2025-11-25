# Inhaltsverzeichnis

tbd

# CSV-Datei

# Namenskonvention des Dateinamens

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

| Headerfeld        |                                                                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Zählstellennummer | Die alphanumerische Nummer der Zählstelle                                                                                                                |
| Zählart           | Das Kürzel der beauftragten Zählart                                                                                                                      |
| Datum             | Das Tagesdatum der Zählung im [ISO-Format](https://de.wikipedia.org/wiki/ISO_8601) (`YYYY-MM-DD`)                                                        |
| Knotenarmnummer   | Die Nummer des Knotenarms welcher durch die CSV-Datei repräsentiert wird. Bei einer Verkehrsbeziehung handelt es sich um die Nummer des Quellknotenarms. |
