# Digitalisierte Marktkommunikation

Übersicht über ausgewählte Libraries und Tools mit denen Hochfrequenz eine echte Digitalisierung der Marktkommunikation in der deutschen Energiewirtschaft vorantreibt

## Hintergrund

Die Spezifikationen und Regeln, denen die Marktkommunikation der deutschen Energiewirtschaft unterliegt, sind nur schlecht bis gar nicht digitalisiert:

- Technische Dokumente liegen allgemein nur im PDF- oder Wordformat vor und sind nicht maschinenlesbar
- Message Implementation Guides (MIG) und Anwendungshandbücher (AHB) sind weder selbst- noch zueinander konsistent:
  - Feld- und Strukturnamen in MIG und AHB stimmen nicht überein
  - Es gibt keinen direkt Weg, eine Zeile aus dem AHB im MIG wiederzufinden (z.b. über eindeutige IDs)
- Vermeintlich boolsche Logik folgt keiner boolschen Logik
- Entscheidungsbäume (EBD) sind keine Bäume sondern nur Tabellen
- Änderungshistorien sind unvollständig und schwer verständlich
- u.v.m.

Hochfrequenz entwickelt Tools, die diese Mängel adressieren. Dieses Repository soll einen Überblick verschaffen.

## Übersicht

Die öffentlichen 🌍 Tools und Libraries unterliegen in der Regel der MIT-Lizenz und sind gut dokumentiert.
Bei Interesse an den nicht-öffentlichen/privaten 🔒 Repositories, bitte eine Nachricht an info (at) hochfrequenz.de oder [@JoschaMetze](https://github.com/JoschaMetze) schicken.

<!-- ORDER BY Name ASC -->

| Name & Link                                                                                                                 |     | Grundlage     | Zweck                                                                                                            | Tech Stack                                                                     |
| --------------------------------------------------------------------------------------------------------------------------- | --- | ------------- | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [ahbicht](https://github.com/Hochfrequenz/ahbicht/) 🦅                                                                      | 🌍  | AHBs          | Parser und Evaluationsframework für Ausdrücke der Form `Muss [1] U ([2] O [3])[901] U [543]`                     | Python ([lark](https://github.com/lark-parser/lark))                           |
| [ahbicht-functions](https://github.com/Hochfrequenz/ahbicht-functions)                                                      | 🔒  | AHBs          | Serverless Backend, das AHBicht Features via REST verfügbar macht                                                | Python (Azure Functions)                                                       |
| [ahbicht-functions-frontend](https://github.com/Hochfrequenz/ahbicht-functions-frontend/)                                   | 🔒  | AHBs          | Visualisierung von AHB-Expressions                                                                               | Typescript ([d3.js](https://d3js.org/))                                        |
| [edi_energy_scraper](https://github.com/Hochfrequenz/edi_energy_scraper)                                                    | 🌍  | edi-energy.de | automatisierter Download von Dokumenten auf edi-energy.de                                                        | Python ([Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/))      |
| [edi_energy_mirror](https://github.com/Hochfrequenz/edi_energy_mirror)                                                      | 🌍  | edi-energy.de | git-basierte, automatisierte Versionierung der Dokumente auf edi-energy.de                                       |                                                                                |
| [EDILibrary](https://github.com/Hochfrequenz/EDILibrary)                                                                    | 🌍  | AHBs & MIGs   | Parser und Template-Enginge für EDIFACT-Nachrichten                                                              | C#                                                                             |
| [EDILibraryHost](https://github.com/Hochfrequenz/EDILibraryHost)                                                            | 🔒  | AHBs & MIGs   | Serverless Backend zum Parsen, Erstellen und Versenden von EDIFACT-Nachrichten                                   | C# (Azure Functions)                                                           |
| [edifact-templates](https://github.com/Hochfrequenz/edifact-templates/)                                                      | 🔒  | AHBs & MIGs   | Daten-Repo: Gescrapte, maschinenlesbare AHBs, Templates für alle EDIFACT-Formate der deutschen Energiewirtschaft |                                                                                |
| [transformer.bee]()🐝                                                                                                       | 🔒  | AHBs & MIGs   | Bidirektionale, stabile und ein-eindeutige Konvertierung zwischen EDIFACT↔BO4E                                   | C# ([JUST.net](https://github.com/WorkMaze/JUST.net))                          |
| [MIG AHB Utility Stack (maus)](https://github.com/Hochfrequenz/mig_ahb_utility_stack) 🐭                                    | 🌍  | AHBs & MIGs   | Datenmodell und Matching-Logik zur Zusammenführung maschinenlesbarer MIGs und AHBs                               | Python ([attrs](https://www.attrs.org/))                                       |
| [ebd_parser-backend](https://github.com/Hochfrequenz/ebd_parser-backend/)                                                   | 🔒  | EBDs          | Backend von [entscheidungsbaumdiagramm.de](https://www.entscheidungsbaumdiagramm.de/)                            | Python ([Flask](https://flask.palletsprojects.com/en/2.2.x/))                  |
| [ebd_parser-frontend](https://github.com/Hochfrequenz/ebd_parser-frontend/)                                                 | 🔒  | EBDs          | Frontend von [entscheidungsbaumdiagramm.de](https://www.entscheidungsbaumdiagramm.de/)                           | TypeScript ([vue.js](https://vuejs.org/))                                      |
| [ebddocx2table](https://github.com/Hochfrequenz/ebddocx2table)                                                              | 🔓  | EBDs          | Scraping-Tool um docx-Dateien mit EBDs maschinenlesbar zu machen                                                 | Python ([python-docx](https://github.com/python-openxml/python-docx))          |
| [ebdtable2graph](https://github.com/Hochfrequenz/ebdtable2graph)                                                            | 🔓  | EBDs          | Core-Logik, die EBD-Tabellen in maschinenlesbare Graphen/Bäume umwandelt                                         | Python ([networkx](https://networkx.org/)) + [PlantUML](https://plantuml.com/) |
| [machine-readable_entscheidungsbaumdiagramme](https://github.com/Hochfrequenz/machine-readable_entscheidungsbaumdiagramme/) | 🔒  | EBDs          | Daten-Repo: Alle Entscheidungsbäume/Graphen, maschinenlesbar in verschiedenen Formaten (puml, dot, svg)          |                                                                                |
| [ahb_conditions_and_packages](https://github.com/Hochfrequenz/edi_energy_ahb_conditions_and_packages)                       | 🌍  | AHBs          | Daten-Repo: Alle Bedingungen und Pakete aus den Anwendungshandbüchern maschinenlesbar aufbereitet                |                                                                                |
| [machine-readable_anwendungshandbuecher](https://github.com/Hochfrequenz/machine-readable_anwendungshandbuecher)            | 🔒  | AHBs          | Daten-Repo: Alle Anwendungshandbücher, maschinenlesbar in verschiedenen Formaten                                 |                                                                                |
| [kohlrahbi](https://github.com/Hochfrequenz/kohlrahbi) 🥬                                                                   | 🌍  | AHBs          | Scraping-Library für PDF- und DOCX-Anwendungshandbücher (Veröffentlichung wird vorbereitet)                      | Python ([python-docx](https://github.com/python-openxml/python-docx))          |
| [mako.bee]() 🐝                                                                                                             | 🔒  | MaKo allg.    | Backend zur Orchestrierung von Marktkommunikationsprozessen in Micro-Service Landschaften                        | C# ([ELSA](https://github.com/elsa-workflows/elsa-core))                       |

## Hochfrequenz

Die [Hochfrequenz Unternehmensberatung GmbH](https://www.hochfrequenz.de) hat ihren Sitz in Grünwald (nahe München), feste Büros in Berlin und Bremen und Home Offices in ganz
Deutschland. Wir leben Digitalisierung und entwickeln u.a. die oben vorgestellten Open Source-Lösungen für die deutsche Energiewirtschaft.
Auf [Kununu](https://www.kununu.com/de/hochfrequenz-unternehmensberatung1) sind wir unter den bestbewerteten Arbeitgebern der Branche. Wir freuen uns jederzeit über Bewerbungen
talentierter Entwickler\*innen und Fachexpert\*innen, z.B.
als [Full Stack Entwickler\*in](https://www.hochfrequenz.de/index.php/karriere/aktuelle-stellenausschreibungen/full-stack-entwickler).
