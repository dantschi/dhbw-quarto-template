# [Modulname] ([Modulkürzel])

Herzlich willkommen zur Vorlesung **[Modulname] ([Modulkürzel])** an der Dualen Hochschule Baden-Württemberg Stuttgart[, Studiengang …].

**Dozent:in:** [Dozent:in]  
**Kurswebsite:** [[GITHUB-USER].github.io/[REPO]](https://[GITHUB-USER].github.io/[REPO]/  
*Hinweis: Quellen im Repo unter [`vorlesungen/`](vorlesungen/) und [`labs/`](labs/).*  
**Repository:** [github.com/[GITHUB-USER]/[REPO]](https://github.com/[GITHUB-USER]/[REPO])

[Beschreibung]

> **Template-Hinweis:** Einrichtungsanleitung und technische Doku stehen in [`TEMPLATE.md`](TEMPLATE.md). Diese Datei (`README.md`) ist die **GitHub-Pages-Startseite** — bitte wie bei einem fertigen Kurs pflegen (Platzhalter ersetzen, Einheiten-Tabelle erweitern).

## Kursübersicht

Der rote Faden der Veranstaltung:

**[Ebene 1] → [Ebene 2] → [Ebene 3] → [Ebene 4]**

Pro Einheit: Folien (Reveal.js), Handout-PDF sowie Übungsblatt (Studierende / Musterlösung). Für Programmieraufgaben gibt es optional ein Startcode-ZIP. Links verweisen auf die Kurswebsite (relativ, funktioniert lokal und auf Pages).

| Einheit | Thema | Schwerpunkt | Folien | Handout | Übungsblatt | Musterlösung | Startcode |
|--------:|-------|-------------|:------:|:-------:|:-----------:|:------------:|:---------:|
| 1 | [Thema Einheit 1] | [Schwerpunkt] | [HTML](vorlesungen/01_kickoff.html) | [PDF](vorlesungen/01_kickoff-handout.pdf) | [PDF](labs/lab_01_beispiel.pdf) | [PDF](labs/lab_01_beispiel-musterloesung.pdf) | — |
| 2 | [Thema Einheit 2] | [Schwerpunkt] | [HTML](vorlesungen/02_….html) | [PDF](vorlesungen/02_…-handout.pdf) | [PDF](labs/lab_02_suchen.pdf) | [PDF](labs/lab_02_suchen-musterloesung.pdf) | [ZIP](labs/lab_02_suchen-startcode.zip) |

**Hinweise:** Folien im Browser öffnen (Speaker View: Taste **S**). Handout-PDF = Folieninhalt mit Skriptnotizen. Quelltexte unter [`vorlesungen/`](vorlesungen/) und [`labs/`](labs/).

### Probeklausur

| Dokument | Studierende | Musterlösung |
|----------|:-----------:|:------------:|
| Probeklausur | [PDF](labs/probeklausur.pdf) | [PDF](labs/probeklausur-musterloesung.pdf) |

*(Zeile entfernen oder anpassen, wenn keine Probeklausur vorgesehen ist.)*

## Literatur

Zentrale Referenz dieses Moduls:

> **[Autor:innen]**  
> *[Werktitel]*  
> [Verlag]

Definitionen, Terminologie und didaktischer Aufbau orientieren sich an diesem Standardwerk.

Zur Vertiefung empfohlen:

> **[Autor:innen Vertiefung]**  
> *[Werktitel Vertiefung]*  
> [Verlag]

## Tools und Ressourcen

| Tool | Einsatz | Link |
|------|---------|------|
| **[Tool 1]** | [Beschreibung/Tools] | [Link] |
| **[Tool 2]** | [Beschreibung/Tools] | [Link] |

### Kursglossar

Das [Kursglossar](GLOSSAR.md) erklärt die bevorzugten Fachbegriffe, ihre Bedeutung und die Zuordnung zu Synonymen und API-Namen. Diese Bezeichnungen gelten gemeinsam für Folien, Übungen und Quiz. Im Template enthält das Glossar gekennzeichnete Beispiele, die beim Anlegen eines konkreten Kurses angepasst werden.

### Programmieraufgaben mit Startcode

Laden Sie das zum Übungsblatt gehörende Startcode-ZIP herunter, entpacken Sie es und lesen Sie zuerst die enthaltene `README.md`. Sie beschreibt die benötigte Sprache und Version, Einrichtung, Ausführung und Tests sowie die zu bearbeitenden Dateien. Nummerierte TODOs gehören zur Übung; noch nicht bestandene Funktionstests können der dokumentierte Ausgangszustand sein.

Das Template enthält als Beispiel [Blatt 2: Suchen und Zählen](labs/lab_02_suchen.pdf) mit einem [Python-Startprojekt](labs/lab_02_suchen-startcode.zip) für Python 3.12. Das ZIP enthält die Anleitung, Startcode und öffentliche Tests. Die Referenzlösung wird getrennt geprüft und ist kein Bestandteil des Startcode-ZIPs. Die Codequellen im öffentlichen Repository sind dennoch einsehbar; das ZIP ist keine Zugriffsbeschränkung.

Für Lehrende stehen die Autoren- und Build-Konventionen unter [Programmieraufgaben mit Startcode](TEMPLATE.md#programmieraufgaben-mit-startcode).

## KI-Skills verwenden

Für die Arbeit mit diesem Template stehen sechs projektbezogene Skills unter `.agents/skills/` bereit. Öffnen Sie das Repository als Arbeitsverzeichnis in Ihrem KI-Tool und beachten Sie die [Projektregeln](AGENTS.md), die passenden [Fachregeln](FACHREGELN.md) und die Begriffsfestlegungen im [Kursglossar](GLOSSAR.md).

| Skill | Verwendung |
|-------|------------|
| [kurs-planen](.agents/skills/kurs-planen/SKILL.md) | Kursrahmen, Lernziele, Einheitenfolge und Zeitbudget planen |
| [einheit-erstellen](.agents/skills/einheit-erstellen/SKILL.md) | Folien mit vollständigen Lernnotizen, Beispielen und Übungen erstellen oder überarbeiten |
| [uebungsblatt-erstellen](.agents/skills/uebungsblatt-erstellen/SKILL.md) | Aufgaben und überprüfte Musterlösungen mit getrennten PDF-Versionen erstellen |
| [quiz-erstellen](.agents/skills/quiz-erstellen/SKILL.md) | QuizAcademy-Fragen aus vorhandenen Vorlesungen erstellen und das CSV-Format prüfen |
| [material-review](.agents/skills/material-review/SKILL.md) | Fachliche und didaktische Befunde mit Fundstellen und Verbesserungsvorschlägen erhalten |
| [material-validieren](.agents/skills/material-validieren/SKILL.md) | Frische HTML-/PDF-Ausgaben bauen und auf Vollständigkeit, Lesbarkeit und Lösungstrennung prüfen |

Nennen Sie im Auftrag den gewünschten Skill und das konkrete Ziel, zum Beispiel:

> Nutzen Sie den Skill `einheit-erstellen` für eine 90-minütige Einheit zu synchronen Automaten. Übernehmen Sie Vorkenntnisse und technische Annahmen aus dem Kurskontext. Erhalten Sie bei der Überarbeitung vorhandene Struktur und Inhalte.

Die automatische Skill-Erkennung hängt vom KI-Tool ab. Falls nötig, geben Sie die Anleitung ausdrücklich vor: „Lesen Sie `.agents/skills/einheit-erstellen/SKILL.md` und bearbeiten Sie meinen Auftrag nach diesem Ablauf.“ Befehle aus den Anleitungen werden im Repository-Stamm ausgeführt.

Dokumentieren Sie Modul, Semester, Vorkenntnisse, Lernziele, Zeitbudget und gegebenenfalls Sprache, Hardware und Zeitmodell im Kurskontext dieser README. Bereits bekannte Angaben werden übernommen; die Skills fragen nur entscheidende Lücken nach. Größere didaktische Umstrukturierungen werden standardmäßig begründet vorgeschlagen. Ein Review ändert ohne Korrekturauftrag keine Materialien; ein erfolgreicher Build ersetzt keine fachliche Prüfung.

Weitere Hinweise einschließlich des CSV-Validators stehen unter [Projekt-Skills verwenden](TEMPLATE.md#projekt-skills-verwenden).

Die Skills berücksichtigen außerdem [Verständnis, Folienabstand und Prüfungsvorbereitung](TEMPLATE.md#aufgaben-für-verständnis-und-prüfungsvorbereitung): eigenständige Denkschritte, passende Hilfen und einen abgestuften Anspruch. Die Einschätzung richtet sich nach Lernzielen und vorhandenen Prüfungsvorgaben; tatsächliche Bearbeitungszeiten und Rückmeldungen helfen bei der Kalibrierung.

## OER und Lizenz

Dieses Vorlesungsmaterial ist eine **Open Educational Resource (OER)**. Die Vorlesungsinhalte – Texte, Code und Diagramme – stehen unter der Lizenz **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)**.

Sie dürfen diese Inhalte teilen und bearbeiten, sofern Sie die Urheberschaft angemessen nennen. Der vollständige Lizenztext liegt in der Datei [`LICENSE`](LICENSE) im Repository.

**Ausnahme:** Hochschullogos und andere geschützte Markenzeichen (einschließlich des DHBW-Logos) sind von dieser Lizenz **ausdrücklich ausgenommen**. Sie unterliegen dem Markenrecht der jeweiligen Rechteinhaber und dürfen ohne deren Genehmigung nicht übernommen oder weiterverwendet werden.
