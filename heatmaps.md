*Airbnb Heatmap für Singapore*

Quelle Datensatz:
http://insideairbnb.com/get-the-data

1. 
Runterladen der Dateien: 
listings.csv
neighbourhoods.geojson --> Ersetzt Shapefile (Shapefile-Type eigentlich veraltet)

2.
Einfügen von der CSV-Datei Listings --> Da Punktkoordinaten festlegen, dass x der Variable "longitude" und y der Variable "latitude" im File Listings entspricht. Verwendete Projektion ist: EPSG:24500 - Kertau 1968 / Singapore Grid - Projected (Ansonsten Projektion mit den Units "degree" wir wollen aber Meter.
![image](https://github.com/NDautel/DTM/assets/84902755/8867ce48-8a96-4c77-93c6-b750c7a6adde)
![image](https://github.com/NDautel/DTM/assets/84902755/40c9f61b-a126-4b6a-9179-2f470b6d4b2a)


Hier gibt es einige ungültige Punkte, da Angaben zu Latitude und/oder Longitude fehlen. Diese Punkte werden aber nicht projeziert, müssen also nicht explizit gelöscht werden. 

3. Daten bereinigen:
D.h. Zahlen in der Kategorie Preis, die willkürlich oder unrealistisch sind ausschließen. Hier wurden keine Daten ausgeschlossen. Allerdings gibt es unplausieble Zahlen/Kategorien in der Kategorie Typ der Unterkunft (room_type). Diese werden aber im folgenden Schritt so oder so ausgefiltert.

5. Layer vier Mal duplizieren und folgend umbenennen sowie jeweils auch filtern, siehe screenshot: 
   -Entire Apartment
   -Private room
   -Shared room
   -Hotel room
   ![image](https://github.com/NDautel/DTM/assets/84902755/11fcadf3-3b3c-437a-8921-f50cd9e1c368)

6.  Grid erzeugen:
Unter Researchtools/Forschungswerkzeuge --> Create Grid --> Hexagon/Sechseck auswählen. 
Gitterausdehnung auf Karte festlegen (siehe screenshot) oder Freihändig
Die Seitenlänge des Sechsecks soll 250m betragen (da Singapore recht klein ist) daher muss bei der Horizontal bzw. Vertical spacing folgender Wert eingetragen werden: 433,0130
![image](https://github.com/NDautel/DTM/assets/84902755/c8bf28a2-8e39-4fc4-9e7a-db737909e661)

Diese Zahl ergibt sich aus der unten angegeben Berechnung da es sich hierbei um die kurze Diagonale (d2) eines Sechsecks handelt:

https://rechneronline.de/pi/sechseck.php
<img width="660" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/68458c59-72af-45b0-9dc3-d77034560065">

8.  
   

