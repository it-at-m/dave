# Struktur der CSV-Datei

## Inhaltsverzeichnis

- [Namenskonvention beim Dateinamen](#namenskonvention-beim-dateinamen)
- [Dateiformat](#dateiformat)
- [Metainformationen im Header der CSV-Datei](#metainformationen-im-header-der-csv-datei)
- [Zähldaten in der CSV-Datei](#zähldaten-in-der-csv-datei)

## Namenskonvention beim Dateinamen

Für eine Zählung ist je in der Zählung berücksichtigten Knotenarm eine CSV-Datei zu erstellen. 
Die Namenskonvention der CSV-Datei ist wie folgt:

`<ZAEHLSTELLENNUMMER>_<DATUM>_Knotenarm_<KNOTENARM_NUMMER>.csv`

| Element            | Beschreibung                                                                                                                                             | Beispiel   |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| ZAEHLSTELLENNUMMER | Die alphanumerische Nummer der Zählstelle                                                                                                                | -          |
| DATUM              | Das Tagesdatum der Zählung im [ISO-Format](https://de.wikipedia.org/wiki/ISO_8601) (`YYYY-MM-DD`)                                                        | 2021-10-06 |
| KNOTENARM_NUMMER   | Die Nummer des Knotenarms welcher durch die CSV-Datei repräsentiert wird. Bei einer Verkehrsbeziehung handelt es sich um die Nummer des Quellknotenarms. | 1 bis 8    |

## Dateiformat

|              |               |
|--------------|---------------|
| Dateiendung  | `.csv`        |
| Trennzeichen | Semikolon `;` |
| Kodierung    | UTF-8         |

## Metainformationen im Header der CSV-Datei

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

## Zähldaten in der CSV-Datei

Nach den Header mit dem Metainformationen zur Zählung beginnt ab der dritten Zeile der eigentliche Inhalt mit den Zählungsdaten.
Die dritte Zeile der CSV-Datei enthält die Spaltenüberschriften für die in den nachfolgenden Zeilen aufgelisteten Zähldaten.

```csv
Zählstellennummer;Zählart;Datum;Knotenarmnummer;;;;;;;
61103;<ZAEHLART>;2022-07-06;4;;;;;;;
Intervallnummer;nach;Strassenseite;Richtung;Pkw;Lkw;Lz;Bus;Krad;Rad;Fuss
25;<NACH>;<HIMMELSRICHTUNG>;<BEWEGUNGSRICHTUNG>;1;0;0;0;0;0;0
```
| Spaltenfeld     | Beschreibung                                                                                                                                                                                                |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Intervallnummer | Die mit der Ziffer 1 beginnende aufsteigende Nummer des fünfzehnminütigen Intervalls eines Tages.                                                                                                           | 
| nach            | Der Zielknotenarm beim Zählen einer Verkehrsbeziehung. <br/>Handelt es sich um eine Zählung welche keine Verkehrsbeziehung mit einem Quell- und Zielknotenarm darstellt, so ist dieses Feld leer zu lassen. |
| Strassenseite   | Die Himmelsrichtung als N, O, S, W, NO, SO, SW oder NW für die Zählarten QjS und FjS; <br/>Ansonsten wird das Feld leer gelassen.                                                                           |
| Richtung        | EIN oder AUS für die Zählart FjS; <br/>N, O, S, W, NO, SO, SW oder NW für die Zählart Qu; <br/>Ansonsten wird das Feld leer gelassen.                                                                       |
| Pkw             | Die Anzahl der gezählten **Personenkraftwagen** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                  |
| Lkw             | Die Anzahl der gezählten **Lastkraftwagen** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                      |
| Lz              | Die Anzahl der gezählten **Lastzüge** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                            |
| Bus             | Die Anzahl der gezählten **Busse** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                               |
| Krad            | Die Anzahl der gezählten **Krafträder** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                          |
| Rad             | Die Anzahl der gezählten **Fahrräder** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                           |
| Fuss            | Die Anzahl der gezählten **Fußgänger** als ganzzahlige Dezimalzahl. <br/>Es darf keine Zifferngruppierung (z.B. durch Tausendertrennzeichen) durchgeführt werden.                                           |

Die nachfolgende Tabelle listet die Intervallnummer mit der jeweiligen Start- und Endeuhrzeit auf. 
Ein Tag besteht somit aus 96 fünfzehn minütigen Intervallen beginnen bei 00:00 Uhr des Zähltages bis 00:00 des Folgetages.

| Intervallnummer | Startuhrzeit | Endeuhrzeit          |
|-----------------|--------------|----------------------|
| 1               | 00:00        | 00:15                |
| 2               | 00:15        | 00:30                | 
| 3               | 00:30        | 00:45                | 
| 4               | 00:45        | 01:00                | 
| 5               | 01:00        | 01:15                |
| 6               | 01:15        | 01:30                | 
| 7               | 01:30        | 01:45                | 
| 8               | 01:45        | 02:00                | 
| 9               | 02:00        | 02:15                |
| 10              | 02:15        | 02:30                | 
| 11              | 02:30        | 02:45                | 
| 12              | 02:45        | 03:00                | 
| 13              | 03:00        | 03:15                |
| 14              | 03:15        | 03:30                | 
| 15              | 03:30        | 03:45                | 
| 16              | 03:45        | 04:00                | 
| 17              | 04:00        | 04:15                |
| 18              | 04:15        | 04:30                | 
| 19              | 04:30        | 04:45                | 
| 20              | 04:45        | 05:00                | 
| 21              | 05:00        | 05:15                |
| 22              | 05:15        | 05:30                | 
| 23              | 05:30        | 05:45                | 
| 24              | 05:45        | 06:00                | 
| 25              | 06:00        | 06:15                |
| 26              | 06:15        | 06:30                | 
| 27              | 06:30        | 06:45                | 
| 28              | 06:45        | 07:00                | 
| 29              | 07:00        | 07:15                |
| 30              | 07:15        | 07:30                | 
| 31              | 07:30        | 07:45                | 
| 32              | 07:45        | 08:00                | 
| 33              | 08:00        | 08:15                |
| 34              | 08:15        | 08:30                | 
| 35              | 08:30        | 08:45                | 
| 36              | 08:45        | 09:00                | 
| 37              | 09:00        | 09:15                |
| 38              | 09:15        | 09:30                | 
| 39              | 09:30        | 09:45                | 
| 40              | 09:45        | 10:00                | 
| 41              | 10:00        | 10:15                |
| 42              | 10:15        | 10:30                | 
| 43              | 10:30        | 10:45                | 
| 44              | 10:45        | 11:00                | 
| 45              | 11:00        | 11:15                |
| 46              | 11:15        | 11:30                | 
| 47              | 11:30        | 11:45                | 
| 48              | 11:45        | 12:00                | 
| 49              | 12:00        | 12:15                |
| 50              | 12:15        | 12:30                | 
| 51              | 12:30        | 12:45                | 
| 52              | 12:45        | 13:00                | 
| 53              | 13:00        | 13:15                |
| 54              | 13:15        | 13:30                | 
| 55              | 13:30        | 13:45                | 
| 56              | 13:45        | 14:00                | 
| 57              | 14:00        | 14:15                |
| 58              | 14:15        | 14:30                | 
| 59              | 14:30        | 14:45                | 
| 60              | 14:45        | 15:00                | 
| 61              | 15:00        | 15:15                |
| 62              | 15:15        | 15:30                | 
| 63              | 15:30        | 15:45                | 
| 64              | 15:45        | 16:00                | 
| 65              | 16:00        | 16:15                |
| 66              | 16:15        | 16:30                | 
| 67              | 16:30        | 16:45                | 
| 68              | 16:45        | 17:00                | 
| 69              | 17:00        | 17:15                |
| 70              | 17:15        | 17:30                | 
| 71              | 17:30        | 17:45                | 
| 72              | 17:45        | 18:00                | 
| 73              | 18:00        | 18:15                |
| 74              | 18:15        | 18:30                | 
| 75              | 18:30        | 18:45                | 
| 76              | 18:45        | 19:00                | 
| 77              | 19:00        | 19:15                |
| 78              | 19:15        | 19:30                | 
| 79              | 19:30        | 19:45                | 
| 80              | 19:45        | 20:00                | 
| 81              | 20:00        | 20:15                |
| 82              | 20:15        | 20:30                | 
| 83              | 20:30        | 20:45                | 
| 84              | 20:45        | 21:00                | 
| 84              | 21:00        | 21:15                |
| 85              | 21:15        | 21:30                | 
| 86              | 21:30        | 21:45                | 
| 87              | 21:45        | 22:00                | 
| 88              | 22:00        | 22:15                |
| 90              | 22:15        | 22:30                | 
| 91              | 22:30        | 22:45                | 
| 92              | 22:45        | 23:00                | 
| 93              | 23:00        | 23:15                |
| 94              | 23:15        | 23:30                | 
| 95              | 23:30        | 23:45                | 
| 96              | 23:45        | 00:00 des Folgetages | 

