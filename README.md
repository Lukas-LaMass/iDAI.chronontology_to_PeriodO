## iDAI.chronontology to PeriodO

Dieses Repositorium enthält Beschreibungen des Workflows und dabei unterstützende Skripte, um Perioden aus iDAI.chronontology in PeriodO zu überführen.

Dieser Workflow wurde im Projekt FAIR.rdm im DFG-geförderten SPP 2143 "Entangeld Africa" entwickelt.

iDAI.chronontlogy und PeriodO funktionieren unterschiedlich, daher sind mehrer Schritte nötig, um Daten aus Chronontology in PeriodOs Schema umzuwandeln.

1. Zuvor muss bestimmt werden, welche Perioden in PeriodO importiert werden sollen. Hierzu beitet sich ein Auszug der Chronontology-Konkordanz an.

2. Die Lokalisierung der Orte wird benötigt. PeriodO nutzt zur Ortsreferenz Wikidata, Chronontology den iDAI.gazetteer. Außerdem unterscheidet Chronontology zwischen drei verschiedenen Ortstypen (Kerngebiet, Region, namensgebend).
Um herauszufinden, welche Orte für die getroffene Auswahl von Perioden relevant sind, muss das Skript "Harvest_Chronontology_Localizations.ipynb" ausgeführt werden.

3. Die festgestellten Orte müssen mit Wikidata abgegleichen werden. Wenn es zu einem Ort keine Übereinstimmung gibt, muss dieser angelegt werden. Den exakten Workflow hierzu beschreibt "Gazetteer_to_Wikidata.ipynb". Für Ergänzungen kann der Code in "Add_Data_via_Quickstatements" angepasst werden.

4. Das Hauptskript "Chronontology_to_PeriodO.ipynb benötigt lediglich eine Liste der zu konvertierenden Perioden mit der Info "ChronoID" sowie die zuovor generierten Tabellen mit den Gazetteer- und Wikidata-Verweisen. Da PeriodO über keine API verfügt, nutzt das Skript eine vorprogrammiert den Client im Browser und lädt die angelegten Perioden als Backup-File herunter. Darin werden letzte Ergänzungen vorgenommen. Die Herstellung der Relation hasPart/isPartOf wird ebenfalls bald in diesen Schritt integriert werden.

5. Das Resultat kann als Backup-File in den PeriodO-Client hochgeladen werden.
