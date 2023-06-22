*Airbnb Heatmap für Singapore*

Quelle Datensatz:
http://insideairbnb.com/get-the-data

1. 
Runterladen der Dateien: 
listings.csv
neighbourhoods.geojson --> Ersetzt Shapefile (Shapefile-Type eigentlich veraltet)

2.
Einfügen von der CSV-Datei Listings --> Da Punktkoordinaten festlegen, dass x der Variable "longitude" und y der Variable "latitude" im File Listings entspricht. DIE PROJEKTION WIRD HIER NOCH NICHT ANGEPASST!
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
--> Die Seitenlänge des Sechsecks soll 250m betragen (da Singapore recht klein ist) daher muss bei der Horizontal- bzw. Vertical Spacing folgender Wert eingetragen werden: 433,0130
![image](https://github.com/NDautel/DTM/assets/84902755/c19b39a4-bb80-409b-ba05-d2224d19c4fe)


Diese Zahl ergibt sich aus der unten angegeben Berechnung, da es sich hierbei um die kurze Diagonale (d2) eines Sechsecks handelt:

https://rechneronline.de/pi/sechseck.php

<img width="660" alt="image" src="https://github.com/NDautel/DTM/assets/84902755/68458c59-72af-45b0-9dc3-d77034560065">

HIER MUSS DIE PROJEKTION UMGESTELLT WERDEN,z.B. auf EPSG:24500 - Kertau 1968 / Singapore Grid - Projected, da ansonsten die Maßeinheit degree und nicht Meter ist!

8.* Im Grid Layer: Nach Position selektieren
   Zentroide für jeden room-layer bilden d.h. entire_apart, private, shared, hotel:
   ![image](https://github.com/NDautel/DTM/assets/84902755/b4c202b3-2a57-466e-a144-0cf63e634109)
   
   ![image](https://github.com/NDautel/DTM/assets/84902755/69695654-da67-4920-a3ae-3f2590588958)

Dann nach Position selektieren als Eingabe Grid und dann jeweils die Zentroide der verschiedenenen Kategorien: 
   ![image](https://github.com/NDautel/DTM/assets/84902755/92b7258f-936c-4c3d-b658-2e47520fc4e9)
   ![image](https://github.com/NDautel/DTM/assets/84902755/f379182f-948b-4fc6-adb7-64122199279b)
   ![image](https://github.com/NDautel/DTM/assets/84902755/9e4fb8ca-79fa-400d-8395-9f948b50ec7b)


"Selected Features" jeweils für entire, private, shared, hotel in einen gesonderten Layer exportieren
![image](https://github.com/NDautel/DTM/assets/84902755/e2aa0ddf-45c0-4fb9-bb29-3afbcb212142)

10.
Wir wollen jetzt jeweils für jedes Grid Element statistische Maßzahlen, speziell den Durchschnitt definieren. 
 
Dafür in der Processing Toolbox "Join attributes by location"/"Attribute nach Position verknüpfen"
![image](https://github.com/NDautel/DTM/assets/84902755/ee429a83-106b-4664-a647-ee3c5c150db3)
![image](https://github.com/NDautel/DTM/assets/84902755/e653266e-e2bd-4f2e-a29e-511ed5e9e454)
![image](https://github.com/NDautel/DTM/assets/84902755/e1ceb6bc-0740-47da-b8a2-00e6002d7f0d)

*Mann kann auch den Schritt 8:) weglassen und direkt aus dem Grid auswählen?

11. 



   

