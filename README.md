<!-- TODO TEMPLATE-TEIL BEGINN: Für eine konkrete Veranstaltung diesen gesamten Block bis einschließlich TODO TEMPLATE-TEIL ENDE löschen. -->

# DHBW Quarto Vorlesungstemplate

Ein Template zum Entwerfen, Prüfen und Veröffentlichen von Vorlesungsmaterial an der DHBW Stuttgart, insbesondere für informationstechnische Fächer im Studiengang Elektro- und Informationstechnik. Es verbindet Quarto-Websites, Vorträge, Handouts, Übungen, Quizfragen und gemeinsame Anleitungen für KI-Tools.

Dies ist ein inoffizielles Dozenten-Template, keine offizielle DHBW-Software.

> **TODO beim Anlegen einer echten Veranstaltung:** Ersetzen Sie die Platzhalter in der [Homepage-Vorlage weiter unten](#modulname-modulkürzel). Löschen Sie danach den gesamten oberen Template-Teil zwischen `TODO TEMPLATE-TEIL BEGINN` und `TODO TEMPLATE-TEIL ENDE`, einschließlich beider Kommentarzeilen. Der Veranstaltungsinhalt unterhalb der Endmarkierung bleibt erhalten.

## Was das Template enthält

| Bereich | Funktion |
|---------|----------|
| Kurswebsite | `index.qmd` übernimmt den Inhalt dieser README als Startseite. |
| Vorlesungen | Reveal.js-Folien mit vollständigen Lernnotizen, aktivierender Einstiegsfrage und späterer Auflösung. |
| Handouts | PDF mit Folieninhalt und zugehörigen Lernnotizen. |
| Übungsblätter | Gemeinsame Quarto-Quelle für Studierenden-PDF und getrennte Musterlösung. |
| Programmieraufgaben | Optionaler Startcode, Referenzlösung und Tests; geprüftes Startcode-ZIP als Download. |
| Quizfragen | QuizAcademy-CSV mit Formatvalidator sowie Regeln für Verständnis, Transfer und angemessenen Anspruch. |
| KI-Unterstützung | Toolübergreifende `AGENTS.md`-Regeln, Fachregeln, Kursglossar und sechs Aufgaben-Skills. |
| Gemeinsamer Build | Versionsgebundene Werkzeuge für Cloud und GitHub Actions; Veröffentlichung erst nach erfolgreicher Prüfung. |

Die Quellen liegen unter `vorlesungen/`, `labs/`, `quizacademy/` und für Programmierprojekte unter `code/labs/`. Layout, Diagramme und Profile sind vorbereitet. Die technische Anleitung und alle Konventionen stehen in [TEMPLATE.md](TEMPLATE.md).

## So funktioniert der Ablauf

1. Kursrahmen, Lernziele und Begriffsfestlegungen in der unteren Homepage-Vorlage und in [GLOSSAR.md](GLOSSAR.md) pflegen.
2. Folien, Lernnotizen, Übungen und Quizfragen aus diesen Vorgaben entwickeln. Die [Projektregeln](AGENTS.md) und [Fachregeln](FACHREGELN.md) unterstützen konsistente, fachlich geprüfte Inhalte.
3. Den gemeinsamen Build ausführen. Er erzeugt Website, Handouts, beide Übungsblattfassungen und vorhandene Startcode-Pakete zunächst in einem frischen Arbeitsverzeichnis. Nur ein vollständig erfolgreicher Lauf übernimmt die angeforderten Ergebnisse.
4. Frische Ausgaben fachlich und visuell prüfen. Die veröffentlichbaren Materialien liegen in `_site/`; ein erfolgreicher Build allein belegt keine didaktische Qualität.
5. GitHub Actions führt bei Pull Requests und Pushes auf `main` denselben vollständigen Build aus. Nach Erfolg veröffentlicht der Workflow auf `main` die geprüften Materialien auf `gh-pages`.

## Schnellstart

Erstellen Sie über **Use this template** ein eigenes GitHub-Repository und klonen Sie es. Die gemeinsame Build-Umgebung unterstützt Linux x86_64 mit Debian 13 oder Ubuntu 24.04; das mitgelieferte Programmierbeispiel benötigt Python 3.12. Voraussetzungen und Werkzeugversionen sind unter [Build-Umgebung einrichten](TEMPLATE.md#build-umgebung-einrichten) beschrieben.

```bash
# Einmalig: Systempakete benötigen Root-Rechte oder sudo.
bash scripts/setup.sh --system-deps
bash scripts/setup.sh

# In jeder neuen Bash-Sitzung aktivieren und Materialien bauen.
source scripts/activate.sh
python3 scripts/build-materials.py all

# Website lokal ansehen.
quarto preview
```

Für gezielte Arbeitsstände stehen `website`, `handouts`, `labs` und `code` als Teilbefehle des Builders bereit. Der vollständige Abschluss verwendet `all`. Weitere Aufrufe und Ausgabepfade stehen unter [Lokal arbeiten](TEMPLATE.md#lokal-arbeiten).

## Eine Veranstaltung aus dem Template erstellen

- Platzhalter in `_quarto.yml` und der unteren Homepage-Vorlage durch die tatsächlichen Kursdaten ersetzen.
- Beispiele in `vorlesungen/`, `labs/`, `code/labs/` und `GLOSSAR.md` passend zum Kurs übernehmen oder ersetzen. Unbenutzte Beispiel- und Probeklausurzeilen aus der Kursübersicht entfernen.
- Den oberen Template-Teil an den TODO-Markierungen vollständig löschen. `index.qmd` behält seinen Include von `README.md`: Solange der obere Teil vorhanden ist, zeigt die Website beide Teile; danach zeigt sie nur die Veranstaltung.
- Die übernommene Veranstaltung mit dem vollständigen Build prüfen. Details stehen unter [Neues Modul anlegen](TEMPLATE.md#neues-modul-anlegen).

Das mitgelieferte [Python-Beispiel „Suchen und Zählen“](code/labs/lab_02_suchen/README.md) zeigt die Trennung von Startcode, Referenzlösung und Tests. Sein Download entsteht beim Build unter `_site/labs/lab_02_suchen-startcode.zip`. Anleitung und Paketkonventionen stehen unter [Programmieraufgaben mit Startcode](TEMPLATE.md#programmieraufgaben-mit-startcode).

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

Dokumentieren Sie Modul, Semester, Vorkenntnisse, Lernziele, Zeitbudget und gegebenenfalls Sprache, Hardware und Zeitmodell im Abschnitt „Kursrahmen und Lernziele“ der untenstehenden Homepage-Vorlage. Bereits bekannte Angaben werden übernommen; die Skills fragen nur entscheidende Lücken nach. Größere didaktische Umstrukturierungen werden standardmäßig begründet vorgeschlagen. Ein Review ändert ohne Korrekturauftrag keine Materialien; ein erfolgreicher Build ersetzt keine fachliche Prüfung.

Weitere Hinweise einschließlich des CSV-Validators stehen unter [Projekt-Skills verwenden](TEMPLATE.md#projekt-skills-verwenden).

Für einen größeren Review können Sie ein [abgegrenztes Prüfpaket](.agents/skills/material-review/references/pruefpaket-vorlage.md) verwenden. Es hält Materialien, Lernziele, Voraussetzungen und Prüfgrenzen fest und ermöglicht getrennte fachliche und didaktische Prüfblicke ohne bisherigen Chatverlauf, sofern das KI-Tool dies unterstützt. Ein [ausgefülltes Beispiel](.agents/skills/material-review/examples/pruefpaket-lab-02-suchen.md) liegt bei.

Die Skills berücksichtigen außerdem [Verständnis, Folienabstand und Prüfungsvorbereitung](TEMPLATE.md#aufgaben-für-verständnis-und-prüfungsvorbereitung): eigenständige Denkschritte, passende Hilfen und einen abgestuften Anspruch. Die Einschätzung richtet sich nach Lernzielen und vorhandenen Prüfungsvorgaben; tatsächliche Bearbeitungszeiten und Rückmeldungen helfen bei der Kalibrierung.

## Homepage-Vorlage für die Veranstaltung

> **TODO:** Ab der folgenden Endmarkierung steht der spätere Veranstaltungsinhalt. Passen Sie ihn an Ihren Kurs an und entfernen Sie den darüberliegenden Template-Teil wie oben beschrieben. Die Lizenzangaben am Ende gehören weiterhin zur Veranstaltung.

<!-- TODO TEMPLATE-TEIL ENDE: Bis einschließlich dieser Kommentarzeile löschen; die folgende Veranstaltungs-Homepage behalten. -->

<!-- TODO VERANSTALTUNG: Platzhalter und Beispielzeilen durch reale Kursdaten und Materialien ersetzen; diesen Kommentar anschließend entfernen. -->

# [Modulname] ([Modulkürzel])

Herzlich willkommen zur Vorlesung **[Modulname] ([Modulkürzel])** an der Dualen Hochschule Baden-Württemberg Stuttgart[, Studiengang …].

**Dozent:in:** [Dozent:in]\
**Kurswebsite:** [[GITHUB-USER].github.io/[REPO]](https://[GITHUB-USER].github.io/[REPO]/)\
*Hinweis: Quellen im Repo unter [`vorlesungen/`](vorlesungen/) und [`labs/`](labs/).*\
**Repository:** [github.com/[GITHUB-USER]/[REPO]](https://github.com/[GITHUB-USER]/[REPO])

[Beschreibung]

## Kursrahmen und Lernziele

| Rahmen | Angaben zur Veranstaltung |
|--------|---------------------------|
| Studiengang und Studienrichtung | [Studiengang / Studienrichtung] |
| Semester | [Semester] |
| Vorausgesetzte Kenntnisse | [Vorkenntnisse] |
| Präsenz- und Selbstlernzeit | [Umfang und Zeitbudget] |
| Prüfungsform und Hilfsmittel | [Vorgesehene Prüfungsform und erlaubte Hilfsmittel] |
| Technische Voraussetzungen | [Bei Bedarf: Sprache und Version, Zielplattform, Werkzeuge, Zeitmodell] |
| Modulvorgaben | [Modulhandbuch mit Fassung und Fundstelle; offene Vorgaben kennzeichnen] |

Nach Abschluss der Veranstaltung können Sie:

- [Beobachtbares Lernziel 1]
- [Beobachtbares Lernziel 2]
- [Beobachtbares Lernziel 3]

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

Das [Kursglossar](GLOSSAR.md) erklärt die bevorzugten Fachbegriffe, ihre Bedeutung und die Zuordnung zu Synonymen und API-Namen. Diese Bezeichnungen gelten gemeinsam für Folien, Übungen und Quiz.

### Programmieraufgaben mit Startcode

Laden Sie das zum Übungsblatt gehörende Startcode-ZIP herunter, entpacken Sie es und lesen Sie zuerst die enthaltene `README.md`. Sie beschreibt die benötigte Sprache und Version, Einrichtung, Ausführung und Tests sowie die zu bearbeitenden Dateien. Nummerierte TODOs gehören zur Übung; noch nicht bestandene Funktionstests können der dokumentierte Ausgangszustand sein.

Das jeweilige Paket enthält die Anleitung, Startcode und freigegebene Tests. Die Referenzlösung ist kein Bestandteil des Startcode-ZIPs. Quelltexte und Lösungen in einem öffentlichen Repository sind dennoch einsehbar; das ZIP ist keine Zugriffsbeschränkung.

## OER und Lizenz

Dieses Vorlesungsmaterial ist eine **Open Educational Resource (OER)**. Die Vorlesungsinhalte – Texte, Code und Diagramme – stehen unter der Lizenz **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)**.

Sie dürfen diese Inhalte teilen und bearbeiten, sofern Sie die Urheberschaft angemessen nennen. Der vollständige Lizenztext liegt in der Datei [`LICENSE`](LICENSE) im Repository.

**Ausnahme:** Hochschullogos und andere geschützte Markenzeichen (einschließlich des DHBW-Logos) sind von dieser Lizenz **ausdrücklich ausgenommen**. Sie unterliegen dem Markenrecht der jeweiligen Rechteinhaber und dürfen ohne deren Genehmigung nicht übernommen oder weiterverwendet werden.
