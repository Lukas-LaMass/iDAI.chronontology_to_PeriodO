# Readme des Repos

## iDAI.chronontology to PeriodO

This repository contains the workflow description and supporting scripts for transferring periods from [iDAI.chronontology](https://chronontology.dainst.org/) to [PeriodO](https://perio.do/en/).

This workflow was developed in the [FAIR.rdm] ([https://www.dainst.blog/entangled-africa/en/p11-data-management-en/](https://www.dainst.blog/entangled-africa/en/p11-data-management-en/)) in the [DFG](https://www.dfg.de/)-funded [SPP 2143 “Entangled Africa”](https://www.dainst.blog/entangled-africa/en).

<aside>
💡

The background to this workflow is FAIR.rdm's endeavor to enter the metadata of the research data generated in SPP 2143 into the ARIADNE portal. iDAI.chronontology is used as the reference system for periods in SPP 2143. However, ARIADNE relies on the canonical dataset from PeriodO. This workflow was therefore developed to make the chronologies of Entangled Africa visible in PeriodO as well.

</aside>

iDAI.chronontology and PeriodO work differently, so several steps are necessary to convert data from Chronontology into PeriodO's schema.

<aside>
💡

It is advisable to familiarize yourself with the structures of Chronontology and PeriodO before starting this workflow. At this point, it is important to note that PeriodO is primarily intended for the personal organization of chronologies. In order for data to be included in the canonical dataset, contact must be made with the persons responsible for PeriodO.

</aside>

### Workflow steps

1. First, you need to decide which periods to import into PeriodO. An excerpt from the Chronontology concordance is a good place to start.
2. You'll need to locate the periods. PeriodO uses Wikidata for location references, while Chronontology uses iDAI.gazetteer. In addition, Chronontology distinguishes between three different location types (core area, region, eponymous).
To find out which locations are relevant for the selected periods, the script “Harvest_Chronontology_Localizations.ipynb” must be executed. More detailed descriptions of this step can also be found there.
3. The locations identified must be compared with Wikidata. If there is no match for a location, it must be created from scratch. The exact workflow for this is described in “Gazetteer_to_Wikidata.ipynb.” For subsequent additions to locations already created in Wikidata, the code in “Add_Data_via_Quickstatements.ipynb” can be adapted.
4. The main script “Chronontology_to_PeriodO.ipynb” only requires a list of the periods to be converted with the “ChronoID” information in one column and the previously generated tables with the gazetteer and Wikidata references. Since PeriodO does not have an API, the script uses preprogrammed operations and controls the client in the web browser. It then downloads the created periods as a backup file. Final additions are made to this file. The final modified backup file is saved in the working directory.
5. The result can be uploaded as a backup file to the PeriodO client, where a quality check should be performed. Important to note: As long as the Wikidata locations used have not been indexed by PeriodO, the periods cannot be edited individually in the client.

---

### iDAI.chronontology zu PeriodO

Dieses Repositorium enthält die Beschreibung des Workflows und dabei unterstützende Skripte, um Perioden aus [iDAI.chronontology](https://chronontology.dainst.org/) in [PeriodO](https://perio.do/en/) zu überführen.

Dieser Workflow wurde im Projekt [FAIR.rdm](https://www.dainst.blog/entangled-africa/en/p11-data-management-en/) im [DFG](https://www.dfg.de/)-geförderten [SPP 2143 "Entangeld Africa"](https://www.dainst.blog/entangled-africa/en) entwickelt.

<aside>
💡

Der Hintergrund dieses Workflows ist FAIR.rdms Bestreben, die Metadaten der im SPP 2143 erzeugten Forschungsdaten im [ARIADNE Portal](https://portal.ariadne-infrastructure.eu/) einzugeben. Als Referenzsystem für Perioden wird im SPP 2143 iDAI.chronontology verwendet. ARIADNE greift jedoch auf das Canonical-Dataset von PeriodO zurück. Deswegen wurde dieser Workflow entwickelt, um die Chronologien von Entangled Africa auch in PeriodO sichtbar zu machen.

</aside>

iDAI.chronontlogy und PeriodO funktionieren unterschiedlich, daher sind mehrere Schritte nötig, um Daten aus Chronontology in PeriodOs Schema umzuwandeln.

<aside>
💡

Es ist ratsam, sich vor diesem Workflow mit den Strukturen von Chronontology und PeriodO zu befassen. An dieser Stelle kann nur der sehr wichtige Umstand festgehalten werden, dass PeriodO in erster Linine zur persönlichen Organisation von Chronologien dient. Damit Daten schließlich in das Canonical-Dataset aufgenommen werden, muss Kontakt zu den für PeriodO verantwortlichen Personen hergestellt werden.

</aside>

### Arbeitsschritte des Workflows

1. Zuvor muss bestimmt werden, welche Perioden in PeriodO importiert werden sollen. Hierzu beitet sich ein Auszug der Chronontology-Konkordanz an.
2. Die Lokalisierung der Perioden wird benötigt. PeriodO nutzt zur Ortsreferenz Wikidata, Chronontology den iDAI.gazetteer. Außerdem unterscheidet Chronontology zwischen drei verschiedenen Ortstypen (Kerngebiet, Region, namensgebend).
Um herauszufinden, welche Orte für die getroffene Auswahl von Perioden relevant sind, muss das Skript "Harvest_Chronontology_Localizations.ipynb" ausgeführt werden. Dort finden sich auch nähere Beschreibungen zu diesem Schritt.
3. Die festgestellten Orte müssen mit Wikidata abgegleichen werden. Wenn es zu einem Ort keine Übereinstimmung gibt, muss dieser neu angelegt werden. Den exakten Workflow hierzu beschreibt "Gazetteer_to_Wikidata.ipynb". Für nachträgliche Ergänzungen in bereits angelegten Orten in Wikidata kann der Code in "Add_Data_via_Quickstatements.ipynb" angepasst werden.
4. Das Hauptskript "Chronontology_to_PeriodO.ipynb benötigt lediglich eine Liste der zu konvertierenden Perioden mit der Info "ChronoID" in einer Spalte sowie die zuovor generierten Tabellen mit den Gazetteer- und Wikidata-Verweisen. Da PeriodO über keine API verfügt, nutzt das Skript vorprogrammierte Operationen und steuert den Client im Webbrowser an. Anschließend lädt es die angelegten Perioden als Backup-File herunter. Darin werden letzte Ergänzungen vorgenommen. Das finale modifizierte Backup-File wird im Arbeitsverzeichnis gespeichert.
5. Das Resultat kann als Backup-File in den PeriodO-Client hochgeladen werden, wo eine Qualitätskontrolle erfolgen sollte. Wichtig zu beachten: Solange die verwendeten Wikidata-Orte nicht durch PeriodO indiziert worden sind, lassen sich die Perioden nicht im Client einzeln manuell bearbeiten.
