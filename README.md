# Visualisierung von Geodaten (DTM) | SoSe25

Zusammenfassung aller Aufgaben im Kurs Visualisierung von Geodaten (DTM), mit Layout, Arbeitsschritte, sowie Vor,- und Nachteilen der angewendeten Methoden.
Autor: Nick Bitter

## Dasymetrische Choroplethenkarte

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/Choroplethenkarte%20u.%20Dasymetrische%20Choropletenkarte.png)

Arbeitsschritte
- Download der LOR-Daten mit Bevölkerungsstatistik, CLC-Daten und der Geometrie Berlin 
- Verknüpfen der Geometrie Berlin mit den Bevölkerungsdaten
- Filterung der CLC-Daten über Ausdruck: "c18" = '111' OR '112' um Urbane-Räume-Layer zu erhalten
- Speicherung der Daten und Auflösen des Layers
- Verschneiden der restlichen Flächen als unbewohnte Gebiete
- Verschneidung der Bevölkerungsdaten mit den Urbanen Räumen
- Berechnung der reduzierten Fläche in neuer Spalte in der Attributtabelle
- Abgestufte Symbolisierung zur Visualisierung
- Einwohner pro m² = Einwohnern / Fläche /10000 
- Klassifizierung mittels natürlicher Unterbrechungen (Jenks)
- für die Symbolisierung, ein Farbverlauf von Weiß nach Rot

### Vorteile
- Nur bewohnte Flächen werden berücksichtigt, unbewohnte (Wälder, Parks, Wasser) sind ausgeschlossen
- Realistischere Darstellung von Verteilungen, da nur die tatsächlich genuzte Fläche dargestellt wird
- Keine Flächenverzerrungen, die bei klassischen Choroplethenkarten zu falschen Interpretationen führen
- Bessere Vergleichbarkeit zwischen Regionen

### Nachteile
- Genaue Daten liegen nicht immer vor
- Die Erstellung ist komplexer als bei klassischen Choropletenkarten, durch zusätzliche Berechnungen und Modellierungen
- Die Ansicht könnte in Fällen schwerer zu verstehen sein
- Auch "nicht urbaner Raum" kann bewohnt sein (Falsche Darstellung möglich)

## Gitterchoroplethenkarten

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/Kirschb%C3%A4ume_Berlin.png)

Arbeitsschritte
- Download der Daten von FIS Broker (Baumbestand), Geometrie Berlin
- Erzeugen der Hexagone mit Forschungswerkzeuge - Gitterer zeugen
- Seitenlänge von 500m für die Hexagone wählen
- Verschneidung der Hexagone mit der Fläche von Berlin
- Einladen der Punktdaten (Baumbestand)
- Summe der Punkte in einem Hexagon bestimmen (Attribute nach Position verknüpfen)
- Abgestufte Symbolisierung zur Visualisierung
- Klassifizierung mittels natürlicher Unterbrechungen (Jenks)
- Bei Symbolisierung ist weiß = 0

### Vorteile
- Unabhängig von administrativen Grenzen, das erlaubt objektivere und vergleichbare räumliche Betrachtung
- Alle Rasterzellen gleich groß, somit besser vergleichbar
- Je nach Daten oder Aesthetik, flexibel in Auflösung und Form
- Geeignet für flächenhafte Daten
- Vermeidung von unrealistischen Werten aufgrund von zu kleinen oder großen Flächen

### Nachteile 
- Rechenaufwand und hohe Datenmenge erforderlich bei vielen kleinen Rasterzellen
- Verzerrung oder Verfälschung der Aussage bei großen Rasterzellen
- Rasterzellen ignorieren natürliche oder administrative Grenzen

## Punktrasterkarte

![]()

Arbeitsschritte
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
- Einfach und schnell zu verstehen
- Anschaulich und viele Informationen in einer Ansicht
- Unterschiedliche Punktgrößen zum Darstellen von Daten
- Sowohl in einer Gesamtdarstellung als auch in getrennten thematischen Karten umsetzbar.

### Nachteile
- Die Wahl der Punktdichte kann zu einer falschen Wahrnehmung der tatsächlichen Werte führen
- Zu große Unterschiede in den Datenwerten können zu Überlappungen bzw. großen freien Flächen ohne sichtbare Datenwerte führen
- Wenn Punkte sich überlappen, wird es unübersichtlich
- Punte können als Standorte verstanden werden

## Value-by-alpha Mapping

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/Wahlergebnisse_21_25.png)

Arbeitsschritte
- Download der Daten: Wahldaten und Geometrie von der Bundeswahlleitung
- Datenaufbereitung auf 5 Parteien (CDU + CSU, SPD, Grüne, Linke, AfD) und nur Zweitstimme ist relevant
- Verknüpfen der Geometrie mit den Sachdaten über die Wahlkreisnummer
- Neue Felder berechnen
- Ermitteln des Wahlsiegers je Wahlkreis + übernehmen der Prozentzahl in je eine neue Spalte
- Die Wahlkreise werden in die Farbe der Partei des Wahlsiegers kategorisiert
- Eine Fläche wird über die Wahlkreise gelegt, die ihre Intensität je nach prozentualer Anteile am Gesamtergebnis anpasst
- Durch Legende oder Text sollte klar werden, warum die Flächen unterschiedlich Intensiv dargestellt werden

### Vorteile
- Zwei Variablen auf einer Ebene
- Bessere Gewichtung nach Bedeutung durch die Intensität der Farbe
- Gibt den Daten mehr Kontext, zeigt Veränderung auch bei wiederholtem Wahlsieg

### Nachteile
- Aufwendige Datenaufbereitung
- Hohe Transparenz kann dazu führen, dass Karten schwer lesbar sind
- Es werden keine präzisen Werte dargestellt
- Abgrenzung von ähnlichen Farben fällt schwer

## Tilemaps

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/MP_Deu.png)

Arbeitsschritte
- Download der Daten von DESTATIS (Statistisches Bundesamt)
- Erzeugen eines Gitters über Deutschland mit einer Seitenlänge von 150km
- Gitterzellen löschen, bis der Umriss von Deutschland zu erkenn ist und 16 Zellen über bleiben
- Neue Spalten in der Attributtabelle des Gitters mit den Abkürzungen der Bundesländer füllen
- Aufbereiten und verknüpfung der Sachdaten
- Symbolisierung abgestuft in 5 Gruppen

### Vorteile
-	Daten bzw. Inhalt rückt in den Vordergrund da alle Kacheln gleich groß sind
-	Kompakte und klar strukturierte Darstellung
- Die Karte ist übersichtlich und lässt leichte Interprätation zu

### Nachteile
-	Genaue Lage, natürliche Formen und Größenunterschiede gehen verloren.
-	Die Ansicht kann verwirrend wirken
  
## Flowmaps

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/REF_KAZ.png)

Arbeitsschritte
- Download der Datenvon UNHCR, Geometriedaten von Naturalearth 
- Bearbeitung der Sachdaten 
- Verknüpfung von Sachdaten mit Geometriedaten
- Erstellen der Zentroide (Mittelpunkte) für alle Länder-Geometrien die gebraucht werden
- Erstellen eines extra Punktes vom Ausgangspunkt
- Eigenes KBS einrichten (Orthographische Projektion:+proj=ortho +lat_0=50.3 +lon_0=30.3 +x_0=0+ y_0=0 +a=6371000 +b=6371000 +units=m +no_defs)
- Berechnen der X- und Y-Koordinate in der Attributtabelle des Punktlayers
- Einfügen der Koordinaten in die Attributtabelle vom Ausgangspunkt
- mit dem Werkzeug XY to Line Linien Zwischen dem Ausgangspunkt und den anderen Zentroiden
- Symbolisierung der Erde über Markierung und Füllung die erstellen (Farbe und Glow)

### Vorteile
- Kann Beziehungen zwischen Objekten in einer Karte darstellen
- Gute Visualisierung von Mengen und Richtungen
- Hoher Informationsgehalt
- Anschauliche Globus-ähnliche Darstellung
  
### Nachteile
- Linien können sich bei hohen Datenmengen überlagern und die Karte unübersichtlich machen
- Durch die Globus-ähnliche Darstellung können nicht alle Länder gut dargestellt werden
- Darstellung nur bei recht großräumigen Daten möglich

## Mesh-Daten

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/Kyrill.gif)

Link zum GIF: https://cloud.bht-berlin.de/index.php/s/BYnH22q3Ei4iNc7

Arbeitsschritte
- Download der Verwaltungsgränzen Deutschlands und Wetterdaten im grip-Format von Copernicus
- Einladen der grip-Daten  (Mesh-Layer mit Zeitstempel)
- Symbolisiert wird Windgeschwindigkeit als Farbflächen (Farbverlauf violett zu orange) und Windrichtung als Pfeile darstellen (Abstände und Stil anpassen)
- Erstellen eines Punktlayers: für die Darstellung der Zeit und in der Beschriftung mit format_date( @map_start_time, 'd. MMMM yyyy')  || '\n'  ||  format_date( @map_start_time, 'HH:mm') eingestellt wird
- Layout durch Dekorationen ergänzen

- Für die Animation muss man die Konsole Zeitsteuerungsfenster aufrufen
- Einstellen der Bildrate, Animationsbereich und Abschnitt
- Speichern der einzelnen Bilder 
- GIF erstellen mit einem Browserprogramm oder über Photoshop

### Vorteile
- Zeitliche Entwicklung wird dargestellt
- Darstellung mehrer Größen gleichzeitig
- Kombination aus Farben und Pfeilen ermöglicht gute Interpretation
- Erstellung eines GIFS möglich

### Nachteile
- Große Datenmengen benötigen viel Speicherplatz und lange Downloadzeit
- Aufwendige Erstellung
- Keine detaillierte Ansicht

## Animation in GIS

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/Lyriden.png)

Arbeitsschritte
- Downlaoad der Daten von Meteor-Map
- Hintergrund wählen
- einladen der csv über die Koordinaten
- Mit dem „Geometrie nach Ausdruck“-Tool eine Linie für jeden Meteor erstellen ( @geometry, make_point( "LonEnd", "LatEnd" ))
- Einen Farbverlauf für die Linien wählen um einen Meteorschweif darzustellen


### Vorteile
- Dynamische Animationen machen zeitliche Entwicklungen leicht verständlich
- Es ist möglich mehre Datensätze zu nutzen
- Farbverlauf der Linien sorgt für eindrucksvolle Darstellung

### Nachteile
- Große Datenmengen benötigen viel Speicherplatz und lange Downloadzeit
- Weiterverarbeitung und Nutzung ist einschränkt
- Die Vorbereitung der Daten kann aufwendig sein
- Wird bei hoher Punktdichte unübersichtlich

## 3D-Gebäudemodelle

![](https://github.com/nibi5637/DTM-SoSe-2025/blob/main/Dresden_3D.png)

Arbeitsschritte
- Download der Daten der Digitale 3D-Stadtmodelle von Geodaten-Sachsen
- Unter Symbolisierung auf 2,5D stellen
- Als Höhe H_Objekt wählen und den Winkel auf 90° stellen, Schatten deaktivieren
- die Symbolisierung wieder auf Einzelsymbol stellen und einfärben
- Visualisierung unter Ansicht 3D-Kartenansicht erstellen

### Vorteile
- Realistische und anschauliche Darstellung
- Vermittelt besseren räumlichen Eindruck der Stadtstrukturen
- Abschätzen von Höhenunterschieden ist möglich
- Interaktive Erkundung duch Zoom oder Perspektivenwechsel möglich 

### Nachteile
- Große Datenmengen benötigen viel Speicherplatz und lange Downloadzeit
- Die Darstellung und Interaktion mit ist sehr rechenintensiv
- Der gewählte Bildausschnitt muss sich explizit für eine 3D-Darstellung anbieten
- Vereinfachte Gebäudeformen
- Modelle veralten schnell
