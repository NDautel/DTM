https://www.unhcr.org/refugee-statistics/download/?url=S6d4Vb

https://www.naturalearthdata.com/downloads/110m-cultural-vectors/

Join

Zentroide

Löschen der überflüssigen Spalten bis auf 
Keep:
Year
Country of Origin 
Country of Origin (ISO) 
Country of asylum 
Refugees under UNHCR's mandate


Definiton einer Projektion über Einstellungen 

+proj=ortho +lat_0=49.1 +lon_0=31,2 + x_0 = 0 +y_0=0 +a=6370100 +b=6370100 +units=m +no_defs 


Für den Kreis/Hailo effekt um die Erde
buffer(make_point(0,0),6350000, 20)





____

Geldtransfer:
https://www.knomad.org/data/remittances
Vorbereitung:
a.) Länder Shapefile laden
b.) Deutschland Shapefile laden
c.) CSV Money_Stream vorbereiten

Schritte in QGIS:

1. Zentroide für alle Länder erstellen
2. Im Zentroide layer: Im Feldrechner dann jedem Land seine Koordinate zuweisen --> Neues Feld erzugen z.B. x_dest --> Command: 
 ```
$x
 ```
--> Weist dann die Längengerade dem jeweiligen Punkt zu. 
Das Gleiche noch einmal für y_dest.
![image](https://github.com/NDautel/DTM/assets/84902755/f6db3fc6-20b7-4284-a5d9-e763a401d847)

3. "Shape tools" Plug-in installieren: 
![image](https://github.com/NDautel/DTM/assets/84902755/4d096e8f-fa9a-4210-b308-5bc55a61f6de)

4. Einzelpunkt-layer nur für Deutschland erzeugen (Für später, damit man ein Polygon darum "buffern"/zeichnen kann--> Schritt 6.
5. Verbindung erzeugen zwischen Original country (Germany -> x/y_origin) und den Empfängerländern (x/y_dest)

Orthogonale Projektion für Deutschland:

+proj=ortho +lat_0=51.134 +lon_0=10.288 + x_0 = 0 +y_0=0 +a=6370100 +b=6370100 +units=m +no_defs 

Erklärung Bestandteile der Projektion:
lon_0 = x_koordinate Deutschland
lat_0 = y_Koordinate Deutschland
+a    = Elipsoid Umfang (definieren)
+b    = Elipsoid Umfang (definieren)
--> Für perfekte Kugel gleiche Zahl
units = Meter etc.

6.![image](https://github.com/NDautel/DTM/assets/84902755/548cc102-9941-470f-8c48-47813c40e8f5)
!!! Nicht vergessen Projektion für den Punkt auch auf die Orthogonale ändern (Da default Einheiten degrees sind, wir aber Meter haben wollen) 

7. 



Fragen: 

Koordindaten y_origin ändert sich, wenn ich x_Origin anlege und statt Komma dann ein Punkt und eine Dezimalzahl weniger, warum?

![image](https://github.com/NDautel/DTM/assets/84902755/aaa097f2-02f7-4f96-b73c-ae4a0b013e88)

