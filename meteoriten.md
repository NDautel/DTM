https://github.com/tammojan/meteormap

https://tammojan.github.io/meteormap/

per steuerng folgende Punkte durch klicken auswählen:
DE000M,DE000F,DE000H,DE000G,DE000P,DE0004,DE0005,DE0006,DE0007,DE0008,DE0009,DE0003,DE0003,DE0002,DE0001,DE000Q,DE000B,DE000S,PL0001,PL0006,PL0005,DE000C,DE000J,DE000K,DE000R

Projektion nur unten rechts ändern, damit ändert man den Ansichtswinkel auf die Großkarte, die Projektionen für die Layer bleiben (in diesem Beispiel) gleich. 

Linien auf Pfeile ändern:
(minute 8 Screenshot)

Äußeres Glühen hinzufügen, Pfeilkopf verschmälern, so dass es aussieht wie Meteoiren

Dann die Dateien für den ganzen August runterladen, auch wieder von folgenden Stationen
DE000M,DE000F,DE000H,DE000G,DE000P,DE0004,DE0005,DE0006,DE0007,DE0008,DE0009,DE0003,DE0003,DE0002,DE0001,DE000Q,DE000B,DE000S,PL0001,PL0006,PL0005,DE000C,DE000J,DE000K,DE000R

Dynamische Zeitstellenung--> Bei Properties/Eigenschaften--> Zeitlich im layer WholeAugust aktivieren (minute 23)

Oben in der Leiste Zeitstuerung aktivieren (Auf Uhr klicken)
In der Zeitsteuerung oben auf dem Zahnrad die Framerate erhöhen (mehr Bilder pro Sekunde) 

Animation speichern über das Disketensymbol

In Einstellungen --> Zeitlich --> "Objekte über Zeit sammeln"
Objekte über Zeit Sammeln wenn es z.B. eine route ist.

Temporären Layer erstellen, Punktgeometrie (Name Legende) bei Großbritanien setzen und dann Label als Einzelsymbol hinzufügen (Bei Layer legende)
Dann neben "Wert" in der Legendenansicht (labels) auf das Epsilon klicken und folgendes eintragen:
'Sternschnuppen'   || '\n'  ||   format_date(  @map_start_time, 'dd MMMM yyyy') 
--> Das N ist für einen Absatz die zwei Striche zum Verketten der Strings
