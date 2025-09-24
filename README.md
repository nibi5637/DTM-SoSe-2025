# Visualisierung von Geodaten (DTM) | SoSe25

Abschlussprojekt in Form einer Zusammenfassung von allen Aufgaben im Kurs Visualisierung von Geodaten (DTM), mit Layout, anleitung zur Erstellung des Layouts, sowie Vor,- und Nachteilen der angewendeten Methoden.

## Dasymetrische Choroplethenkarte

![](https://github.com/Fefiro/DTM/blob/main/01_Gegen%C3%BCberstellung.jpg)

Erstellung der Karte
- Download der LOR-Daten (Daten zur Bevölkerungsstatistik), CLC-Daten und der Geometrie Berlin 
- Verbinden der Geometrie (Berlin) mit den Sachdaten (Bevölkerungsdaten) mittels einer Verknüpfung
- Filterung der CLC-Daten nach den Urbanen-Räumen (111,112)
- Speicherung der Daten und Auflösen
- Verschneiden der restlichen Flächen als unbewohnte Gebiete
- Verschneidung der Bevölkerungsdaten mit den Urbanen Räumen
- Berechnung der Flächen
- für die Visualisierung wird eine abgestufte Symbolisierung verwendet
- der Wert wird aus den Einwohnern / Fläche /10000 als Einwohner pro m² berechnet
- es werden 5 Klassen nach Jenks gebildet
- es ist darauf zu achten, dass die Klassen nicht verbunden sind
- für die Symbolisierung wird ein Farbverlauf von Weiß (gering) nach Rot (hoch) genommen
- für die Druckzusammenstellen werden die beiden Kartenbilder platziert
- Überschrift, Maßstab, Maßstabsbalken, Quellen, Legende und Ersteller hinzugefügt

### Vorteile
- Realistischere Darstellung von Verteilungen, sie zeigen Daten dort, wo sie tatsächlich auftreten
- Vermeidung von Flächenverzerrungen, die bei klassischen Choroplethenkarten zu falschen Interpretationen führen. Dasymetrische Karten reduzieren diesen Effekt
- Höhere Genauigkeit bei kleinen Flächen, besonders nützlich bei Phänomenen die räumlich ungleich verteilt sind (z. B. Bewohner)
- Vermeidung von falscher Darstellung, Indem unbedeutende Flächen nicht dargestellt werden
- Bessere Vergleichbarkeit zwischen Regionen, da die Darstellung an reale Nutzungsflächen angepasst ist

### Nachteile
- Die notwendigen Daten wie z.B. Landnutzungsdaten liegen nicht immer vor
- Die Erstellung ist komplexer als bei klassischen Choropletenkarten, da zusätzliche Berechnungen und Modellierungen notwendig sind
- Die Karten können für manche Betrachter schwerer zu verstehen sein, da die Flächen nicht mehr direkt mit administrativen Einheiten - übereinstimmen
- Die Verteilung innerhalb einer Einheit ist noch immer modelliert und bildet die Verhältnisse nicht exakt ab

## Gitterchoroplethenkarten

![](https://github.com/Fefiro/DTM/blob/main/02_Kirschatlas%20Berlin.png)

Erstellung der Karte
- Download der Daten: Kirschbäume (FIS Broker), Geometrie Berlin
- Erzeugen der Hexagone mit Gittererzeugen
- Verschneidung der Hexagone mit der Fläche von Berlin
- Einladen der Punktdaten (Kirschbäume)
- Punkte (Bäume) in Polygon zählen: beim Zähler ist darauf zu achten, dass in jedem Feld ein Attribut steht, also am besten ID nehmen
- für die Visualisierung wird eine abgestufte Symbolisierung verwendet
- als Feld wird das neu erstellt Zählerfeld genommen
- es werden 5 Klassen nach Jenks gebildet
- es ist darauf zu achten, dass die Klassen nicht verbunden sind
- für die Symbolisierung wird ein Farbverlauf von Weiß (gering) nach Rot (hoch) genommen
- für die Druckzusammenstellen wird das Kartenbilder platziert
- Überschrift, Maßstab, Maßstabsbalken, Quellen, Legende und Ersteller hinzugefügt

### Vorteile
- Unabhängig von administrativen Grenzen, das erlaubt objektivere, vergleichbare räumliche Betrachtung
- Gleiche Flächengröße, also besser vergleichbar, kein Flächenverzerrungseffekt durch große Gebiete mit wenig Kirschbäumen)
- Förderung räumlicher Genauigkeit, ermöglichen Gitterkarten eine sehr differenzierte Darstellung räumlicher Muster
- Geeignet für flächenhafte Daten, da diese kontinuierlich über den Raum variieren und nicht an politische Grenzen gebunden sind (meistens)
- Vermeidung von unrealistischen Werten aufgrund von zu kleinen oder großen Flächen (Wie bei Dasymetrische Choroplethenkarten)

### Nachteile 
- Jede Rasterzelle wird separat analysiert und dargestellt  Hohe Datenmenge erforderlich
- Die Verarbeitung und Darstellung großer Rasterdaten kann rechenaufwendig sein
- Durch die starke Generalisierung können kleine räumliche Unterschiede verloren gehen oder verfälscht werden


## Punktrasterkarte

![](https://github.com/Fefiro/DTM/blob/main/03_Karte_AirBNB_A3.png)

Erstellung der Karte
- Download der Daten: Übernachtungsdaten und Geometrie der Stadt von airbnb
- Erzeugen eines Gitternetzes über das Stadtgebiet z.B. 500m mit Gittererzeugen
- Verschneidung des Gitternetzes und der Geometrie der Stadt
- Einladen der Punktdaten (nach Übernachtungsart: Hotel, privat, usw.)
- Punkte (Übernachtungsart) in Polygon zählen: beim Zähler ist darauf zu achten, dass in jedem Feld ein Attribut steht, also am besten ID nehmen
- die Gitternetze werden ausgeblendet
- für die Visualisierung wird eine abgestufte Symbolisierung verwendet
- als Feld wird das neu erstellt Zählerfeld genommen
- es werden 5 Klassen nach Jenks gebildet (es darauf zu achten, dass Ganzzahlen verwendet werden)
- Zum einen wird die Zahl über die Größe definiert zum anderen über die Farbe
- Für die Übernachtungsarten werden verschieden Farben verwendt
- für die Druckzusammenstellen wird das Kartenbilder platziert
- Überschrift, Maßstab, Maßstabsbalken, Quellen, Legende und Ersteller hinzugefügt

### Vorteile
- Vorteile ähnlich zu Gitterchoroplethenkarte, durch nutzen der Punkte kann eine Karte unter die Punkte gelegt werden, was bei der räumlichen Orientierung hilft
- Nutzung der Punktgröße zum Darstellen von Daten, die Punktgröße kann angepasst werden, um sowohl große als auch kleine Datenmengen effektiv darzustellen

### Nachteile
- Die Wahl der Punktdichte kann zu einer falschen Wahrnehmung der tatsächlichen Werte führen.
- Zu große Unterschiede in den Datenwerten können zu Überlappungen bzw. großen freien Flächen ohne sichtbare Datenwerte führen
- Bei zu hoher Punktdichte kann die Karte überladen wirken, während eine zu geringe Dichte wichtige Details verlieren lässt.

## Value-by-alpha Mapping

![](https://github.com/Fefiro/DTM/blob/main/04_UE_4.png)

Erstellung der Karte
- Download der Daten: Wahldaten und Geometrie von der Bundeswahlleitung
- Bereinigen der Wahldaten (auf 5 Parteien und Zweitstimme)
- Verknüpfen der Geometrie mit den Sachdaten über die Wahlkreisnummer
- Ermitteln des Wahlsiegers je Wahlkreis + übernehmen der Prozentzahl in je eine neue Spalte
- Die Wahlkreise werden in die Farbe der Partei des Wahlsiegers kategorisiert
- Regelbasiert wird eine Fläche über die Wahlkreise gelegt, die die Intensität der Flächen anhand der Prozentualen Anteile am Gesamtergebnis stärker (höhere Anteil), blasser (geringer Anteil) darstellt
- für die Druckzusammenstellen werden die Kartenbilder für 2021 und 2025 platziert
- Überschrift, Maßstab, Maßstabsbalken, Quellen, Legende und Ersteller hinzugefügt
- zusätzlich muss entweder aus der Legende deutlich werden, warum die Flächen blasser sind, oder es muss einen Hinweistext geben

### Vorteile
- Bessere Gewichtung nach Bedeutung
→ Dunkle Farben = viele Wähler (großer Einfluss)
→ Blassere Farben = weniger Wähler (geringerer Einfluss)
- Zusätzliche Dimension ohne Karte mehr hinzuzufügen, anstatt ein zweites Diagramm oder eine komplexe Visualisierung zu nutzen, wird die Bedeutung eines Gebiets durch Transparenz vermittelt
•- Gibt den Daten mehr Kontext, die Karte vermittelt realistischer, wo politische Mehrheiten tatsächlich stark existieren

### Nachteile
- Hohe Transparenz kann dazu führen, dass Karten schwer lesbar sind, insbesondere bei komplexen Datensätzen
- Oft nur grobe Einschätzung von Größenordnungen möglich, anstatt präzise Werte darzustellen
- Transparenzwerte können je nach Bildschirm oder Druckqualität variieren

## Tilemaps

![](https://github.com/Fefiro/DTM/blob/main/05_Geburten%20in%20DE.png)

Erstellung der Karte
- Download der Daten: Statistisches Bundesamt
- Erstellen eines Gitters über Deutschland (150km)
- Löschen der Gitterflächen, sodass der Umriss von Deutschland zu erkenn ist; 16 Teile, eins pro Bundesland
- Aufbereiten der Sachdaten, es ist darauf zu achten, dass ein Verknüpfungsfeld zwischen Sachdaten und Geometrie geschaffen wird
- Symbolisierung abgestuft in 5 Gruppen
- Für die Druckzusammenstellen wird das Kartenbild platziert
- Überschrift, Quellen, Legende und Ersteller hinzugefügt

### Vorteile
•	Gleiche visuelle Repräsentation, große Flächenländer wie Bayern oder Niedersachsen erhalten nicht mehr Platz als kleine Stadtstaaten wie Bremen oder Hamburg
•	Fokus auf den Inhalt, da alle Kacheln gleich groß sind, lenkt nichts von der Farbskala ab
•	Kompakte und klar strukturierte Darstellung
Die Karte ist übersichtlich, platzsparend und symmetrisch, ideal für Präsentationen oder Dokument

### Nachteile
•	Da alle Regionen in einer standardisierten Form dargestellt werden, gehen natürliche Formen und Größenunterschiede verloren.
•	Die Optik kann für Nutzer ungewohnt sein, da sie eher abstrakt gestaltet ist

## Flowmaps

![](https://github.com/Fefiro/DTM/blob/main/06_Studenten.png)

Erstellung der Karte
- Download der Daten: Bereitgestellte Studentenaustauschdaten, Geometriedaten von Naturalearth 
- Bearbeitung der Sachdaten 
- Verknüpfung von Sachdaten mit Geometriedaten
- Erstellen der Zentroide für die Länder die gebraucht werden
- Erstellen eines extra Punktes vom Ausgangspunkt sie die Symbolisierung
- Berechnen der X- und Y-Koordinate in der Attributtabelle des Punktlayers
- Einfügen der X- und Y-Koordinate in die Attributtabelle der Hauptstadt wo die Flüchtlinge herkommen
- mit dem Werkzeug XY to Line Linien Zwischen der Hauptstadt der Flüchtlinge und dem Zentroid des Fluchtlandes erstellen Projektion: +proj=ortho +lat_0=50.3 +lon_0=30.3 +x_0=0+ y_0=0 +a=6371000 +b=6371000 +units=m +no_defs
- Symbolisierung der Erde mit dem Punkt der Hauptstadt eine Ausdehnung von 12742000 m im Maßstab einstellen, über Markierung und Füllung die Erde erstellen (Farbe, Glow
- Farbe für die Staaten festlegen
- Flüchtlingszahlen über abgestufte Punkte und Linien darstellen
- für die Druckzusammenstellen wird das Kartenbilder platziert
- Überschrift, Quellen, Legende und Ersteller hinzugefügt

### Vorteile
- Darstellung von Objekten in einer Karte zueinander, flowmaps können Beziehungen zwischen Objekten in einer Karte anzeigen und nicht nur die Daten des Objekts
- Gute Visualisierung von Mengen und Richtungen, die Dicke oder Farbe der Pfeile macht Unterschiede in Menge oder Stärke sofort sichtbar (z.B. Menge an Flüchtlingen oder Studenten)
- Höherer Informationsgehalt und visuell ansprechender als Tabellen, flowmaps visualisieren Daten, welche sonst nur in Tabellen ablesbar wären auf einen Blick verständlich

### Nachteile
- Bei hohen Datenmengen können sich Linien überlagern und die Karte unübersichtlich machen
- Die Richtung und Stärke der Flüsse kann schwer zu erfassen sein, besonders wenn die Linien komplex verlaufen
- Darstellung nur bei recht großräumigen Daten möglich
- Es sind präzise Daten zu Bewegungen oder Strömen nötig, die nicht immer verfügbar sind

## Mesh-Daten

![](https://github.com/Fefiro/DTM/blob/main/07_Orkan_Kyrill.png)

Link zum GIF: https://cloud.bht-berlin.de/index.php/s/BYnH22q3Ei4iNc7

Erstellung der Karte
- Download der gegeben Wetterdaten im grip-Format (von Copernicus)
- Einladen der grip-Daten
- Hinzufügen eines Deutschland-Umriss zur Orientierung
- Symbolisiert wird der Wind als Fläche und als Linie
- Erstellen eines Punktlayers der für die Darstellung der Zeit benötigt wird und in der Beschriftung mit format_date( @map_start_time, 'd. MMMM yyyy')  || '\n'  ||  format_date( @map_start_time, 'HH:mm') eingestellt wird
- Die Druckzusammenstellung findet auf dem Hauptoberfläche statt und nicht in dem Layout.
- In Ansicht Dekoration wird ein Titel, Maßstab, Quellen und der Ersteller hinzugefügt

- Für die Animation muss man die Konsole Zeitsteuerungsfenster aufrufen
- Einstellen der Bildrate, Animationsbereich und Abschnitt
- Speichern der einzelnen Bilder 
- Zusammenfügen der einzelnen Bilder zu einen GIF mit einem Browserprogramm oder über Photoshop

### Vorteile
- Darstellung zeitlicher Entwicklungen 
- Analyse Raum-Zeit-Zusammenhänge, so kann man z. B. beobachten, wie schnell sich ein Wetterereignis ausbreitet oder wie sich Umweltwerte mit der Zeit verändern
- Darstellung Mehrer Größen gleichzeitig, die in einem Mesh-Datensatz enthaltenen Informationen kann man zeitgleich visualisieren oder kombinieren und dadurch zusammenhänge leichter erkennen.
- Erstellung eines GIFS
- Man kann die Mesh-Daten als GIF darstellen und damit auch außerhalb einer Gis-Programms nutzen, z.B. einer Präsentation oder einem Text.

### Nachteile
- Sie können große Datenmengen erzeugen, die viel Speicherplatz benötigen
- Die Analyse und Visualisierung von Mesh-Daten erfordert leistungsstarke Programme und Hardware
- Unterschiedliche Mesh-Datenformate können die Interoperabilität zwischen verschiedenen GIS-Systemen erschweren
- Die feine Auflösung kann es schwierig machen, übergeordnete Muster zu erkennen

## Animation in GIS

![](https://github.com/Fefiro/DTM/blob/main/09_Meteor%20Lesbar.png)

Erstellung der Karte
- Downlaoad der Daten: Download der Daten von https://tammojan.github.io/meteormap/ für den die Alpha Capricornids im Juni 2024 als csv
- einladen der csv über die Koordinaten
- bei den Einzelsymbolen den Typ Markierung wählen und als Unterpunkt den Geometriegenerator, dort Ausdruck make_line ( @geometry, make_point( "LonEnd", "LatEnd" )) eingeben
- für die weitere Visualisierung eine interpolierte Linie erzeugen und die wie gewünscht visualisieren
- eine dunkle Hintergrundkarte verwenden
- für das Druckzusammenstellen wird das Kartenbilder auf dem gesamten Blatt platziert
- Überschrift, Quellen und Ersteller hinzugefügt

### Vorteile
- Veränderung über einen Zeitraum sichtbar machen
- Bewegungen sichtbar machen, durch die Nutzung von Animationen kann man Bewegungen, wie in der Wetterkarte oder beim den Meteoritenschauern die Räumliche Veränderung der Objekte sichtbar machen.
- Abbilden von mehreren Datenquellen, man kann mehre Datensätze nutzen, z.B: Meteoriten und Beobachtungsstationen und beobachten in welchem räumlichen Verhältnis beide zueinanderstehen.

### Nachteile
- Animationen mit vielen Layern oder großen Datensätzen können deinen Rechner stark beanspruchen und kann zu Verzögerungen oder Abstürzen führen.
- Die exportierten Videos unterstützen nur bestimmte Formate ,was die Weiterverarbeitung und Nutzung einschränken kann.
- Die Vorbereitung der Daten (z. B. Zeitstempel) kann aufwendig sein.
- Animationen lenken manchmal von der eigentlichen Aussage ab und können die Übersichtlichkeit beeinträchtigen.


## 3D-Gebäudemodelle

![](https://github.com/Fefiro/DTM/blob/main/08_Dresden.png)

Erstellung der Karte
- Download der Daten: Digitale 3D-Stadtmodelle von Geodaten Sachsen: Dresden
- Unter Symbolisierung auf 2,5D stellen
- für die Höhe H_Objekt wählen und den Winkel auf 90° stellen, Schatten deaktivieren
- die Symbolisierung wieder auf Einzelsymbol stellen und jetzt individuell einfärben
- bei 3D-Ansicht den Versatz noch mit H_Objekt - H_Absolut einstellen
- Visualisierung unter Ansicht 3D-Kartenansicht erstellen
- Das Produkt ist ein Screenshot daraus

### Vorteile
- Realitätsnähere Darstellung. 3D-Gebäudemodelle können die Realität viel besser darstellen als es eine Karte kann. Vor allem wenn es weniger um die Positionen von Gebäuden, sondern um deren Eigenschaften, wie Höhe oder Form geht.
- Abschätzen von Höhenunterschieden. Dadurch das die Höhe der Gebäude sichtbar ist kann man auch einschätzen, wie die Höhenunterschiede der Gebäude sich aufeinander auswirken. Z.B: Verdecken sich Gebäude gegenseitig oder gibt es bestimmte Sichtlinien die Eingehalten werden müssen.
- Einfacher verständlich für Laien. Leihen die mit komplizierten Karten mit Höhenangaben überfordert wären können 3D-Modelle viel besser verstehen, da diese eher der Realität entsprechen und einfach wiederzuerkennen sind.
- Viele Anwendungen in der Stadtplanung. Viele der oben genannten Beispiel sind vor allem in der Stadtplanung wichtig, hier kann man auch Modelle von potenziellen Neubauten untersuchen und die Auswirkungen auf das Stadtbild beobachten.

### Nachteile
- 3D-Modelle benötigen detaillierte Höhendaten die oft große Datenmengen verursachen und zu hohen Downloadzeiten führen.
- Die Darstellung und Interaktion mit 3D-Modellen ist sehr rechenintensiv, insbesondere bei Echtzeit-Visualisierungen.
- Abhängig von der Datenquelle können Ungenauigkeiten in der Höhendarstellung oder Modellierungsfehler auftreten.
- Der gewählte Bildausschnitt muss sich explizit für eine 3D-Darstellung anbieten 
- Nicht jeder Nutzer oder jede Plattform kann 3D-Daten effizient darstellen.
