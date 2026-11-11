# Beispielprüfpaket: Übungsblatt 2 „Suchen und Zählen“

Dieses Paket bereitet ein abgegrenztes fachliches und didaktisches Review vor.
Es ist ein ausgefülltes Template-Beispiel, kein bereits ausgeführter Materialreview
und keine offizielle Modulbeschreibung. Korrekturen, Commit und Veröffentlichung sind nicht beauftragt.

## Stand und Verwendung

- Grundlage bei Erstellung: Commit `578e3da2f55d82325007576e2a3043f4070dc85d`.
  Maßgeblich ist der **Arbeitsstand; Commit plus uncommitted Änderungen beachten**.
  Vor jedem Review aktuellen Commit, `git status --short` und relevante Änderungen im Bericht festhalten;
  dieses Beispiel friert spätere Änderungen an Quellen oder Regeln nicht ein.
- Alle Codepfade gelten relativ zum Repository-Stamm. Lies die aufgeführten Dateien selbst;
  unzugängliche oder nicht gelesene Pflichtquellen begrenzen die Abdeckung.
- Ein frischer Prüfer erhält dieses Paket und die Leseliste, keinen Chatverlauf,
  keine interne Entwurfsbegründung und keine vorweggenommene Bewertung.
  Projektregeln und gemeinsam zugängliche Dateien bleiben dabei verfügbar.
- Frische Zweitperspektiven nach dem [EGM-Grundgedanken](https://github.com/google/elephant-goldfish-model/blob/main/docs/codex.md#fresh-context-reviewers)
  sind optional. Ohne getrennten Kontext erfolgt ein entsprechend gekennzeichnetes Review nach `material-review`.

## Dokumentierter Kontext und Ziele

Die Projektregeln richten das Template an Bachelorstudierende der Elektro- und
Informationstechnik an der DHBW Stuttgart. Dieses Blatt ist ausdrücklich ein
didaktisches Informatikbeispiel; ein konkretes Modul und Semester sind nicht festgelegt.
`README.md` enthält noch Platzhalter für Kursdaten, Literatur, Prüfungsform und Hilfsmittel.
Offizielle Modulziele, Prüfungsnähe und Passung zur gesamten Lehrveranstaltung bleiben daher offen.

Das Blatt setzt Python-Funktionen, Listen, Vergleiche und Schleifen voraus.
Dokumentiert sind Python 3.12, ein Texteditor und ausschließlich die Standardbibliothek,
keine besondere Hardware. Geplant sind 20–30 Minuten Einzelarbeit samt Tests und Auswertung;
dies ist eine Schätzung, keine Modulvorgabe oder empirisch bestätigte Bearbeitungszeit.

Zu prüfen sind die aus dem Blatt abgeleiteten Lernziele:
lineare Suche nach dem ersten Treffer implementieren, alle Treffer zählen,
Normal- und Randfälle prüfen sowie Korrektheit, Terminierung und Vergleichsaufwand begründen.
Der Vertrag umfasst endliche Listen ganzer Zahlen und einen ganzzahligen Zielwert,
keine Listenänderung und keine ungültigen Eingabetypen. Jeder Ganzzahlvergleich zählt
als eine Operation; Bitlängen und reale Laufzeitmessungen sind ausgeblendet.

## Umfang und verbindliche Leseliste

| Quelle | Umfang und Zweck |
| --- | --- |
| `labs/lab_02_suchen.qmd` | Vollständiges Blatt einschließlich profilgebundener Lösungen und Begründungen. |
| `code/labs/lab_02_suchen/README.md` | Eigenständig nutzbare Anleitung, Einrichtung, Aufgaben- und Abgabevertrag. |
| `code/labs/lab_02_suchen/starter/search.py` | Beide Schnittstellen und beabsichtigte nummerierte TODOs. |
| `code/labs/lab_02_suchen/tests/check.py` | Alle vier Testgruppen, Import und JSON-/Exitcode-Verhalten. |
| `code/labs/lab_02_suchen/solution/search.py` | Vollständige ausführbare Referenz für den Fachabgleich. |
| `code/labs/lab_02_suchen/lab.json` | Laufzeit, Befehle, Paketdateien und getrennte Starter-/Referenzerwartungen. |

Verbindlich sind `AGENTS.md` (insbesondere Terminologie, Aufgabenanspruch und Modellannahmen),
`FACHREGELN.md` Abschnitt „Informatik“, `code/labs/AGENTS.md`, `GLOSSAR.md`,
`.agents/skills/references/arbeitsweise.md` und `.agents/skills/material-review/SKILL.md`.
Für Profile und frische Ausgaben zusätzlich `labs/_quarto.yml`, `labs/_quarto-solution.yml`,
`TEMPLATE.md` Abschnitt „Programmieraufgaben mit Startcode“ und
`.agents/skills/material-validieren/SKILL.md` heranziehen. Der Kontext stammt aus `README.md` und `_quarto.yml`.
Das Glossar enthält bislang Vorlagenbeispiele; daraus keine erfolgte Einführung von Suchbegriffen ableiten.

Keine thematisch passende Vorlesung 02 oder zugehörige Quizdatei liegt diesem Paket zugrunde.
Platzhalterlinks in der Kursübersicht belegen keine vorhandenen Folien.
Ausgeschlossen sind andere Übungsblätter, ein vollständiges Buildskript-Review,
Hardwareverhalten, bitgenaue Python-Kostenanalyse und eine empirische Lernwirksamkeitsprüfung.
Ein Vergleich des Aufgabenanspruchs mit tatsächlich unterrichteten Folien bleibt offen.

## Prüfauftrag A: Fachprüfung und Konsistenz

- Gleiche Vertrag und Beispiele zwischen Blatt, Projekt-README, Starter, Referenz und Tests ab:
  erster nullbasierter Index oder `-1`, vollständige Trefferzahl oder `0`, leere Listen,
  Duplikate, fehlende Werte und unveränderte Eingabelisten.
- Prüfe beide Referenzfunktionen unabhängig von den Tests; bewerte Schleifeninvarianten,
  Terminierung und die Aussagen zu schlechtestem Fall, Vergleichszahl und Speicherbedarf im genannten Modell.
- Prüfe die Zuordnung von TODOs, erlaubten Schleifen und ausgeschlossenen fertigen Such-/Zählfunktionen.
  Beabsichtigte `NotImplementedError` sind keine eigenmächtig zu schließenden Defekte.
- Prüfe, welche Vertragsverletzungen die öffentlichen Tests erkennen und welche offenbleiben;
  einzelne bestandene Fälle sind kein allgemeiner Korrektheitsbeweis.
- Gleiche die PDF-Musterlösung mit `solution/search.py` ab und kontrolliere die Paketdateiliste.
  Die im Blatt erwähnten früheren Zusatztests gelten ohne aktuellen Nachweis nicht als Prüfung dieses Reviews.

## Prüfauftrag B: Lernweg und selbstständige Lösbarkeit

- Lies zuerst Aufgaben, Projekt-README und Starter aus Sicht des genannten Vorwissens.
  Nutze dafür die frische Studierenden-PDF oder zunächst die Quellabschnitte ohne Lösungsblöcke;
  lies Lösungen erst nach einer eigenen knappen Beschreibung des erwarteten Lösungswegs.
  Diese Reihenfolge garantiert keine Geheimhaltung und ersetzt keine Rückmeldungen von Studierenden.
- Beschreibe je Aufgabe Lernziel, eigenständigen Denkschritt, benötigte Kenntnisse und Hilfen.
  Prüfe insbesondere die Unterscheidung von Index, Wert, Vorhandensein und Anzahl.
- Prüfe, ob Einrichtung, Arbeitsverzeichnis, Versionsprüfung, erwartete Anfangsfehler und Abschluss
  ohne zusätzliche Erklärung verständlich sind und der entpackte Download allein ausreicht.
- Beurteile 20–30 Minuten anhand der Schritte und Hilfen als Schätzung. Kennzeichne mögliche Hürden
  bei Begründung und Kostenmodell; behaupte weder Unter-/Überforderung noch Prüfungsnähe ohne Beleg.
- Gleiche anschließend Lösungen und Hilfen ab: keine unbeabsichtigt sichtbaren Lösungen im
  Studierenden-PDF oder ZIP, verständliche Begründungen und keine unerklärten Begriffswechsel.

## Technische Erwartungen und noch zu prüfende Ausgaben

`lab.json` verlangt Python `3.12.*`. Import aus `starter/` und `solution/` soll Exitcode 0 liefern.
`python3 ../tests/check.py` soll im Starter Exitcode 1 mit `tests: 4`,
`failures: ["test_first", "test_notfound", "test_count", "test_empty"]` und `errors: []` liefern;
die Referenz soll Exitcode 0 mit `tests: 4`, leeren `failures` und leeren `errors` liefern.
Prüfläufe nur gemäß Validierungsskill in temporären Arbeitskopien durchführen, Quellen und Tests erhalten.

| Erwarteter Pfad | Vor jedem Review frisch nachzuweisen |
| --- | --- |
| `_site/labs/lab_02_suchen.pdf` | Studierendenfassung: vollständige Aufgaben, keine Lösungsblöcke, Lesbarkeit. |
| `_site/labs/lab_02_suchen-musterloesung.pdf` | Lösungsfassung: Aufgaben und vollständige Lösungen, Lesbarkeit und Seitenzuordnung. |
| `_site/labs/lab_02_suchen-startcode.zip` | Nur `lab_02_suchen/README.md`, `lab_02_suchen/starter/search.py`, `lab_02_suchen/tests/check.py`; entpackt eigenständig prüfen. |

Diese Pfade sind erwartete Ausgaben, keine aktuellen Erfolgsnachweise. Vorhandensein in `_site/`
genügt nicht. Ein aktueller Lauf von `source scripts/activate.sh` und anschließend
`python3 scripts/build-materials.py labs` muss mit Zeitpunkt, Exitstatus und Ausgabepfaden belegt sein.
PDFs tatsächlich ansehen und den Umfang nennen; fehlt ein frischer Lauf, bleiben Layout,
Lösungstrennung und Downloadvalidierung ungeprüft. Dieses Paket behauptet keinen solchen Lauf.

## Befunde, Synthese und Abdeckungsbericht

Jeder Befund enthält: **Priorität** (hoch/mittel/gering), **Fundstelle** (Datei und aktuelle Zeile,
bei Ausgabe zusätzlich PDF-Seite), **Beleg** (Text, Gegenbeispiel, Rechnung oder tatsächlicher Lauf),
**Auswirkung**, **konkrete Korrektur** und **Grenze/Unsicherheit**. Fehler, Verbesserungen und offene
Fachfragen getrennt kennzeichnen. Keine Befunde zur Erfüllung einer Mindestzahl erfinden.

Der Hauptagent verifiziert Befunde, führt Doppelungen zusammen und berichtet Meinungsunterschiede.
Nach beauftragten Korrekturen nur betroffene Aussagen und Abhängigkeiten erneut prüfen, Fundstellen aktualisieren.
Der Abschluss nennt je Prüfauftrag **durchgeführt / teilweise / nicht durchgeführt** mit Grund,
gelesene Quellen, tatsächliche Befehle samt Version und Ergebnis, betrachtete PDF-Seiten und ZIP-Prüfung,
offene Befunde sowie die Grenzen durch fehlende Kurs-, Folien-, Prüfungs- und Studierendendaten.
Ein ausgefallener Prüfer ist „nicht durchgeführt“, kein befundfreies Review.
