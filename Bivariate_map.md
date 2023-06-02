# DTM
## Bivariate Maps:

![Black Hispanic Bivariate Map](https://github.com/NDautel/DTM/assets/84902755/f65c5c5f-f3b8-4f1a-be39-f2f0d73c0c16)

Die zwei Vergleichskarten in GIS aufbereiten: 
1. <br>
Global Happiness Index Tabelle laden entweder von der [Global Happiness Seite](https://worldhappiness.report/ed/2023/#appendices-and-data) [Global Happiness Report Excel](https://happiness-report.s3.amazonaws.com/2023/DataForFigure2.1WHR2023.xls) <br>
ODER <br>
[Keggle](https://www.kaggle.com/datasets/unsdsn/world-happiness)  <br>
ODER  <br>
[GitHub](https://github.com/AminMirlohi/WorldHappinessReport) (Eine von vielen Angeboten)

2. Tabelle laden via "Layer" -> "Add Layer" -> "Add delimited text layer" -> Fieldname z.B. "WHR2023" -> Check: "custom delimiters": "comma" & "semicolon" & "Tab" -> Check: "First record has field name" & "Detect field types" (Sometimes it helps to uncheck and recheck again to make sure it really will work) --> "Add"
3. IF string to numerical conversion is necessary use "Refactor fields" from the processing toolbox.  
4. Laden des Shapefiles (World_countries_generalized) z.B. von [ESRI](https://hub.arcgis.com/datasets/2b93b06dc0dc4e809d3c8db5cb96ba69/explore)
5. Verbinden Tabelle mit "World_countries_generalized"  via "properties" -> "joins" via "Country" and "Countryname" 
6. Layer neu speichern, damit der Join permanent ist: Rechtsklick layer -> "Export" -> "Safe feature as" -> Name z.B. "Happy2023"
7. Duplicate "Happy2023" TWICE and rename one to e.g. "GDP" and one to "Freed"
8. Beide Layer müssen gefiltert werden damit NULL Values nicht beachtet/angezeigt werden:
rechtsklick layer --> "Filter" -> Einfügen der Regel
 ```
 "Ladder sco" IS NOT NULL
  ```
<img width="1179" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/835a6db9-27da-40ee-9efe-ddf690008b31">

<img width="669" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/ad58f5e5-0224-4070-944f-1a7a652e8f00">

10. Um einen Farbverlauf wie oben in der ersten Abbildung dargestellt zu erreichen, müssen wir unsere Daten mit den Markern A,B,C für den Freedom index und 1,2,3 für das "GDP" --> 
![Tabelle_Auslesen_der_Hexwerte](https://github.com/NDautel/DTM/assets/84902755/8b22cadc-0ee4-4686-b6c2-ceadc9ca1a88)

Im Fieldcalculator neues Feld in Kopie "GDP" folgendes anlegen -> rechtklick layer -> "Open Attribute table" -> "Field calculator" -> check "Neues Feld anlegen" 
 ```
CASE 
WHEN  "Logged GDP" > 10.2 THEN 3
WHEN  "Logged GDP" <= 10.2 AND "Logged GDP" > 9.1
THEN 2
ELSE 1
END
```
bzw. küzer

```
CASE 
WHEN "Logged GDP" > 10.2 THEN 3
WHEN "Logged GDP" > 9.1 THEN 2
ELSE 1
END
```
--> Die Zahlen sind die Klassengrenzen <br>
<img width="266" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/6a567910-b39e-4006-94a0-9a75f00ea671">

In zweiter Kopie "Freed" folgendes anlegen 
```
CASE 
WHEN "Freedom to" > 0.852 THEN C
WHEN "Freedom to" > 0.76 THEN B
ELSE A
END
```
11. Hexwerte mit dem Colorpicker tool auslesen und dann im folgenden Schema nach eintragen: <br>
<img width="289" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/edec47aa-a739-4a66-bb86-a34bea58532a">


![Tabelle_Auslesen_der_Hexwerte](https://github.com/NDautel/DTM/assets/84902755/8b22cadc-0ee4-4686-b6c2-ceadc9ca1a88)

https://lms.bht-berlin.de/pluginfile.php/1957619/course/section/465894/bivariate_samples.png

![bivariate_samples](https://github.com/NDautel/DTM/assets/84902755/ad69e3a5-b11f-4a10-9eb8-599f7b6d095d)

Unten links schwache Farben etc. 

___

Arbeitsaufgabe 8 nacharbeiten: 
Geo Vis: Alpha map  Alphawerte anpassen
Abstufungen in Legende darstellen und erklären was das ist
Konturlinien anpassen —> Dünner und evtl. hellgrau


—> Vielleicht als Gitterchoropletenkarte?
