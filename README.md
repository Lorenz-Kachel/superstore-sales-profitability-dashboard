# Superstore – Umsatz- und Profitabilitätsanalyse (Power BI)

Ein dreiseitiges, interaktives Power-BI-Dashboard zur Analyse von Umsatz, Gewinn und Profitabilität eines fiktiven US-Einzelhandelsunternehmens ("Sample Superstore"). Entstanden, um praktische Erfahrung mit Power BI, Power Query und DAX zu sammeln.

## Datensatz

[Sample Superstore Dataset](https://www.kaggle.com/datasets/vivek468/superstore-dataset-final) (Kaggle) – 9.994 Bestellpositionen eines fiktiven US-Einzelhandelsunternehmens mit Angaben zu Umsatz, Gewinn, Rabatt, Produktkategorie, Kunde, Region und Bundesstaat über mehrere Jahre.

## Aufbau des Dashboards

### Seite 1 – Übersicht
Schneller Gesamtüberblick über die wichtigsten Kennzahlen: Umsatz- und Gewinnentwicklung über die Zeit, Umsatz und Gewinn nach Produktkategorie und Region, Top-5-Produkte nach Umsatz.

![Übersicht](seite1_uebersicht.png)

### Seite 2 – Regionalanalyse
Detaillierte geografische Auswertung: Umsatz nach Bundesstaat (Flächenkartogramm), umsatzstärkste und -schwächste Bundesstaaten, Umsatzentwicklung je Region über die Zeit, sowie eine Matrix mit bedingter Formatierung (Umsatz nach Region und Kategorie). Mit Slicern nach Region, Segment und Kategorie filterbar.

![Regionalanalyse](seite2_regionalanalyse.png)

### Seite 3 – Profitabilitätsanalyse
Zwei Streudiagramme zeigen den Zusammenhang zwischen Umsatz und Gewinn sowie zwischen Rabatt und Gewinnmarge je Produktgruppe, ergänzt um die gewinnstärksten und -schwächsten Produkte.

![Profitabilitätsanalyse](seite3_profitabilitaet.png)

## Erkenntnisse aus der Analyse

- **Rabatt und Gewinnmarge hängen zusammen:** Produktgruppen mit geringerem durchschnittlichem Rabatt weisen tendenziell eine höhere Gewinnmarge auf. Am deutlichsten zeigt sich das bei Tables: hohe Umsätze, aber durch überdurchschnittlich hohe Rabatte eine negative Marge.
- **Nicht jeder Umsatz ist gleich profitabel:** Copiers erzielen bei mittlerem Umsatz den höchsten Gewinn und sind damit die profitabelste Produktgruppe, während Paper bei niedrigem Umsatz eine überdurchschnittlich hohe Marge erreicht – eine kleine, aber profitable Nische.
- **Regionale Unterschiede:** South ist mit Abstand die umsatzschwächste Region, während West und East deutlich stärker abschneiden – die Matrix mit bedingter Formatierung macht das auf einen Blick sichtbar.

## Tech Stack

- Power BI Desktop
- Power Query (Datenimport, -bereinigung, Datentyp- und Formatkorrekturen)
- DAX (eigene Measures)

## DAX-Measures

```dax
Umsatz = SUM('Sample - Superstore'[Sales])
Gewinn = SUM('Sample - Superstore'[Profit])
Profit Margin = DIVIDE(SUM('Sample - Superstore'[Profit]), SUM('Sample - Superstore'[Sales]))
Anzahl Bestellungen = DISTINCTCOUNT('Sample - Superstore'[Order ID])
```

## Was ich dabei gelernt habe

- Datenimport und -bereinigung in Power Query, u. a. Korrektur von Datums- und Zahlenformaten (Gebietsschema-Einstellungen bei importierten US-Daten)
- Grundlagen von DAX: eigene Measures mit `SUM`, `DIVIDE` und `DISTINCTCOUNT`
- Unterschiedliche Aggregationsarten richtig einsetzen (z. B. Durchschnitt statt Summe bei Rabatten)
- Umgang mit verschiedenen Visual-Typen, u. a. Streudiagramm, Flächenkartogramm und Matrix mit bedingter Formatierung
- Strukturierung eines Dashboards über mehrere Seiten, inklusive Slicern und Top-N-Filtern

## Hinweis zu den Daten

Die Originaldaten sind in US-Dollar angegeben (fiktives US-Unternehmen); die Formatierung wurde entsprechend auf USD eingestellt, auch wenn das Dashboard sonst auf Deutsch beschriftet ist.
