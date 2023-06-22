*Airbnb Heatmap für Singapore*

Quelle Datensatz:
http://insideairbnb.com/get-the-data

1. 
Runterladen der Dateien: 
listings.csv
neighbourhoods.geojson --> Ersetzt Shapefile (Shapefile-Type eigentlich veraltet)

2.
Einfügen von der CSV-Datei Listings --> Da Punktkoordinaten muss man hier die Projektion nicht anpassen, sondern lediglich festlegen, dass x der Variable "longitude" und y der Variable "latitude" im File Listings entspricht.
![image](https://github.com/NDautel/DTM/assets/84902755/8867ce48-8a96-4c77-93c6-b750c7a6adde)

3. Daten bereinigen. D.h. Zahlen in der Kategorie Preis, die willkürlich oder unrealistisch sind ausschließen. Hier wurden keine Daten ausgeschlossen. Allerdings gibt es komische Zahlen/Kategorien in der Kategorie Typ der Unterkunft (room_type). Diese werden aber im folgenden Schritt so oder so ausgefiltert.

4. Layer vier Mal duplizieren und folgend umbenennen sowie jeweils auch filtern, siehe screenshot: 
   -Entire Apartment
   -Private room
   -Shared room
   -Hotel room
   ![image](https://github.com/NDautel/DTM/assets/84902755/11fcadf3-3b3c-437a-8921-f50cd9e1c368)

5.  
   

