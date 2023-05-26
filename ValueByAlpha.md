# Value By Alpha Maps in QGIS

## Datenquelle: (Wahlkreisgeometrien & Wahlergebnisse)
[Bundestagswahl 2021](https://www.bundeswahlleiterin.de/bundestagswahlen/2021/ergebnisse.html)

Tabelle (kerg1) mit Wahlergebnissen bereinigen: 

<img width="1151" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/73f97a05-a605-4073-9bd1-5e7b034fde0b">

## QGIS:
1.) Vergleich SPD und CDU: Stimmenstärkere Partei regelbasiert darstellen
Regelname Olaf: 
```
"_kergSPD" >  "_kergCDU" 
```
Regelname Armin: 
```
"_kergSPD" <  "_kergCDU" 
```
2.) Ebene "Alpha" ergänzen und auf Symbolebene 1 setzen
<img width="816" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/5bdcbf65-d3a9-475f-810e-d6cc9060195c">

3.) Regel für Ebene "Alpha": Über "Einfache Füllung" unter "Füllfarbe" > "Datendefinierte Übersteuerung" ("data defined override" > "Bearbeiten"
<img width="1068" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/2442ab8c-43ff-4bf4-acf8-dcda38184b9a">

Grundprinzip:
set_color_part(
'black',
'alpha',
126)

126 durch scale_liear plus Funktion ersetzen: 
set_color_part(
'black',
'alpha',
scale_linear(
"G",
100000, 200000,
230,0)
 )
 
10000 Stimmen werden schwarzer dargestellt (weniger) als Stimmen 20000 --> 230 ist weniger Opaque als 0 --> Dadruch sind Stimmen
20000 stärker dargestellt. 

### N: Proportional zu der Anzahl der gültigen Stimmen
Anzahl der Gültigen Stimmen "G" durch Fläche dividieren: 
set_color_part(
'black',
'alpha',
scale_linear(
"G"/($area/1000000),
100000, 200000,
230,0)
 )
 
 
### N2: Für einen weißen Filter:
set_color_part(
'white',
'alpha',
scale_linear(
"G"/($area/1000000),
0, 1000,
200, 0
)
)
