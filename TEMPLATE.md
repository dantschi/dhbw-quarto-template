# DHBW Quarto Vorlesungstemplate — Einrichtung

> **Hinweis:** Dies ist ein **inoffizielles Dozenten-Template**, keine offizielle DHBW-Software.

GitHub-Template-Repository für Vorlesungswebsites an der **DHBW Stuttgart**: Quarto-Website, Reveal.js-Folien (Apple-/DHBW-Design), PDF-Handouts, Übungsblätter und Publish über GitHub Actions.

Die **GitHub-Pages-Startseite** ist der Inhalt von [`README.md`](README.md) (Kursübersicht wie bei [mct1](https://dantschi.github.io/mct1/)). Diese Datei (`TEMPLATE.md`) beschreibt nur die technische Einrichtung.

## Was enthalten ist

| Bereich | Inhalt |
|---------|--------|
| Website | Quarto-Projekt (`_quarto.yml`); Startseite = `README.md` via `index.qmd` |
| Folien | Reveal.js unter `vorlesungen/*.qmd`, Design in `assets/styles/` |
| Diagramme | Mermaid, WaveDrom/PlantUML sowie Schaltpläne und berechnete Plots (siehe [Diagramm-Entscheidungsbaum](AGENTS.md#diagramm-entscheidungsbaum)) |
| Handout | Profil `handout` (`_quarto-handout.yml`) → PDF mit Folie + Dozentennotizen |
| Übungsblätter | `labs/*.qmd` mit Profil `solution`; Vorlage: `labs/lab_template.qmd` |
| Build und CI/CD | Gemeinsame Skripte in `scripts/`; GitHub Actions prüft Website und PDFs, veröffentlicht auf `gh-pages` |
| KI-Kontext | Toolübergreifende Regeln in [`AGENTS.md`](AGENTS.md), ergänzt durch [`FACHREGELN.md`](FACHREGELN.md) sowie Regeln in `vorlesungen/` und `quizacademy/` |

## Neues Modul anlegen

1. Auf GitHub **Use this template** → neues Repository erstellen.
2. Repository klonen und die unten beschriebene [Build-Umgebung einrichten](#build-umgebung-einrichten).
3. Alle `[…]`-Platzhalter in `_quarto.yml`, `README.md`, `vorlesungen/01_kickoff.qmd` und optional in `AGENTS.md` ersetzen.
4. Weitere Vorlesungen als `vorlesungen/0N_….qmd` anlegen (`format: revealjs`, jede Folie mit `## Titel`, Notizen in `::: notes`).
5. Übungsblätter als `labs/lab_NN_….qmd` anlegen (Vorlage: `labs/lab_template.qmd`).
6. Design/Livefigures möglichst unverändert lassen.

| Datei | Aktion |
|-------|--------|
| `_quarto.yml` | **Ersetzen:** `[Modulname]`, `[Modulkürzel]`, `[GITHUB-USER]`, `[REPO]` |
| `README.md` | **Ersetzen:** Kursinhalt, Einheiten-Tabelle, Literatur, Tools |
| `index.qmd` | behält `{{< include README.md >}}` |
| `vorlesungen/01_kickoff.qmd` | **Ersetzen:** Folieninhalt und Notizen |
| `labs/lab_01_beispiel.qmd` | **Ersetzen** oder aus `lab_template.qmd` ableiten |
| `AGENTS.md`, `vorlesungen/AGENTS.md`, `quizacademy/AGENTS.md` | optional **Anpassen:** Modulbezug und Zielgruppe |

## Kurskontext festlegen

Vor dem Entwurf einer konkreten EIT-Vorlesung in `README.md` einen Abschnitt „Kursrahmen und Lernziele“ pflegen. Darin Modulname und -kürzel, Semester bzw. Studienrichtung, Vorkenntnisse, Präsenz- und Selbstlernzeit, Prüfungsform, Literatur und Werkzeuge zentral festhalten. Vorgaben aus einem vorliegenden Modulhandbuch mit dessen Fassung benennen; offene Angaben und Annahmen kenntlich machen.

Für informationstechnische Inhalte je nach Bedarf außerdem Programmiersprache und Standard bzw. Laufzeitversion, Zielplattform mit Controller/Kern und Architekturvariante, Toolchainversion mit relevanten Compileroptionen sowie das Zeitmodell dokumentieren. Die passenden Abschnitte der [Fachregeln](FACHREGELN.md) nach dem Inhalt der Einheit wählen; beispielsweise können bei einem Scheduling-Thema in Mikrocomputertechnik beide Fachabschnitte gelten.

Für jede Einheit wenige überprüfbare Lernziele formulieren und passende Übungen bzw. Verständnisprüfungen sowie ein Zeitbudget zuordnen. Die [Projektregeln](AGENTS.md#kurskontext-und-lernziele) beschreiben die Anforderungen an Lernziele, Quellen, Rechenprüfungen und reproduzierbare Laboraufgaben.

## Mit KI-Tools arbeiten

Die Projektregeln stehen in normalen Markdown-Dateien im verbreiteten `AGENTS.md`-Format. KI-Tools mit entsprechender Unterstützung, einschließlich Cursor, können sie als Projektanweisungen einlesen:

| Datei | Geltungsbereich |
|-------|----------------|
| [`AGENTS.md`](AGENTS.md) | Kurskontext und Lernziele, akademische Genauigkeit, EIT-Rechen- und Laboraufgaben, Tech-Stack, Diagramme und lesbares Design |
| [`FACHREGELN.md`](FACHREGELN.md) | Je nach Inhalt zusätzliche Modellannahmen und Prüfungen für Informatik, Digitaltechnik, Mikrocomputertechnik und Realzeitsysteme |
| [`vorlesungen/AGENTS.md`](vorlesungen/AGENTS.md) | Zusätzlich für Vorlesungsfolien: vollständige Notizen und UTF-8-Prüfungen |
| [`quizacademy/AGENTS.md`](quizacademy/AGENTS.md) | Zusätzlich für Quiz-CSV-Dateien: Format, Lernzielbezug, Schwierigkeit und Antwortgestaltung |

Die zentralen Regeln gelten immer zusätzlich zu den Regeln im jeweiligen Unterordner. `AGENTS.md` weist das KI-Tool an, für fachliche Inhalte die passenden Abschnitte aus `FACHREGELN.md` zu lesen. Bei einem KI-Tool ohne automatische `AGENTS.md`-Unterstützung die zentrale Datei und die für die Aufgabe relevanten ergänzenden Dateien ausdrücklich als Kontext übergeben. Die Regeln werden nur hier gepflegt; es sind keine separaten Cursor-Regeldateien erforderlich.

### Projekt-Skills verwenden

Unter `.agents/skills/` liegen sechs Aufgabenanleitungen im `SKILL.md`-Format. Die zentralen Regeln legen Qualitätsanforderungen fest; Skills beschreiben dazu Eingaben, Arbeitsschritte, Ergebnisse und Abschlussprüfungen.

| Skill | Beispielauftrag |
|-------|-----------------|
| [einheit-erstellen](.agents/skills/einheit-erstellen/SKILL.md) | „Erstelle eine Einheit zu endlichen Automaten mit vollständigen Lernnotizen.“ |
| [material-review](.agents/skills/material-review/SKILL.md) | „Prüfe diese Timer-Beispiele fachlich und didaktisch.“ |
| [uebungsblatt-erstellen](.agents/skills/uebungsblatt-erstellen/SKILL.md) | „Erstelle zur Einheit ein Übungsblatt samt Musterlösung.“ |
| [quiz-erstellen](.agents/skills/quiz-erstellen/SKILL.md) | „Erzeuge acht QuizAcademy-Fragen zur vorhandenen Vorlesung.“ |
| [kurs-planen](.agents/skills/kurs-planen/SKILL.md) | „Plane die Einheitenfolge aus diesen Modulvorgaben und dem Zeitbudget.“ |
| [material-validieren](.agents/skills/material-validieren/SKILL.md) | „Baue und prüfe alle Ausgabeformate des Kurses.“ |

Die automatische Erkennung von `.agents/skills/` hängt vom KI-Tool ab. Bei Bedarf die jeweilige `SKILL.md` ausdrücklich als Anleitung übergeben; sämtliche Verweise gelten relativ zu dieser Datei. Es ist keine automatische Aktivierung weiterer Skills erforderlich: Deren Prüfabläufe können direkt gelesen und die vorhandenen Skripte aufgerufen werden.

Bei Überarbeitungen erhalten die Skills standardmäßig die vorhandene Struktur und die Inhalte. Größere didaktische Umstrukturierungen werden begründet vorgeschlagen; bereits beauftragte Änderungen werden ohne zusätzliche Freigabeschritte bearbeitet. Die [gemeinsame Arbeitsweise](.agents/skills/references/arbeitsweise.md) beschreibt auch den Umgang mit fehlenden Kursangaben. Es müssen nicht für jeden Aufruf alle Kursdaten erneut eingegeben werden.

Der Quiz-Skill enthält einen Formatvalidator für eine oder mehrere CSV-Dateien:

```bash
python3 .agents/skills/quiz-erstellen/scripts/validate_quiz.py quizacademy/datei.csv
```

Dieser prüft das Dateiformat und die formalen Antwortbedingungen. Ob Fragen, Optionen und Erläuterungen fachlich richtig und didaktisch geeignet sind, wird gesondert geprüft. Die Skripttests laufen mit `python3 -m unittest discover -s tests -v`.

## Build-Umgebung einrichten

Cloud-Umgebung und GitHub Actions verwenden dieselben Setup- und Build-Skripte. Das Setup unterstützt Linux x86_64 mit Debian 13 oder Ubuntu 24.04. Es benötigt `curl`, `python3`, `tar`, `xz`, `sha256sum` und `dpkg-deb`; die Systemabhängigkeiten für den Browser und die SVG-Konvertierung installiert der erste Aufruf mit Root-Rechten bzw. `sudo`:

```bash
bash scripts/setup.sh --system-deps
bash scripts/setup.sh
source scripts/activate.sh
```

Das Setup prüft die Downloads mit SHA-256 und installiert folgende festgelegte Versionen im nicht versionierten Verzeichnis `.tools/` des Repositorys. Versionen und Prüfsummen werden zentral in [`scripts/toolchain.env`](scripts/toolchain.env) gepflegt:

| Werkzeug | Version |
|----------|---------|
| Quarto | 1.11.9 |
| Node.js | 24.22.1 |
| Chrome Headless Shell für Mermaid-PDFs | 157.0.8103.38 |
| TinyTeX mit vollständigem Paketbestand | 2026.11 |
| `rsvg-convert` für SVGs in PDFs | 2.60.0 |

`source scripts/activate.sh` in jeder neuen Shell ausführen. Die Aktivierung wählt die installierten Werkzeuge einschließlich Browser und TeX und berücksichtigt die Proxy-Konfiguration der Cloud-Umgebung. Das Setup kann erneut ausgeführt werden. Für eine gemeinsame Installation außerhalb des Checkouts kann vor Setup und Aktivierung `DHBW_TOOLCHAIN_DIR` auf ein beschreibbares Verzeichnis gesetzt werden. Im Build werden fehlende TeX-Pakete nicht automatisch nachinstalliert; nötige Änderungen am Paketbestand gehören zur gemeinsamen Toolchain.

Die festgelegten Renderwerkzeuge verringern Unterschiede zwischen Cloud und CI. Betriebssystem und Systembibliotheken bleiben Teil der Umgebung; bytegleiche Ausgaben über verschiedene Betriebssysteme hinweg sind damit nicht garantiert. PlantUML benötigt bei einem Cache-Miss weiterhin Zugriff auf den konfigurierten Kroki-Dienst.

## Lokal arbeiten

```bash
# Vollständige Prüfung wie in GitHub Actions
python3 scripts/build-materials.py all

# Bei der Bearbeitung gezielt einen Bereich bauen
python3 scripts/build-materials.py website
python3 scripts/build-materials.py handouts
python3 scripts/build-materials.py labs
# Kompatibler Kurzaufruf für beide Lab-Versionen
bash build_labs.sh

# Vorschau nach Aktivierung der Build-Umgebung
quarto preview
quarto preview vorlesungen/01_kickoff.qmd
```

Der gemeinsame Build erstellt die Website, zu allen Vorlesungen unter `vorlesungen/` ein PDF-Handout und zu nummerierten Übungsblättern sowie `probeklausur.qmd` beide PDF-Versionen. Er berücksichtigt auch Unterordner; Vorlagen sowie versteckte und interne Verzeichnisse bleiben ausgenommen. Er rendert in ein frisches Arbeitsverzeichnis und übernimmt die Ergebnisse erst, wenn alle angeforderten Renderläufe erfolgreich waren. Fehlende, leere oder fehlgeschlagene Pflichtausgaben führen zu einem Fehler.

Die veröffentlichbaren Dateien liegen gemeinsam in `_site/`:

| Ausgabe für die Beispieldateien | Pfad |
|--------------------------------|------|
| Folien | `_site/vorlesungen/01_kickoff.html` |
| PDF-Handout | `_site/vorlesungen/01_kickoff-handout.pdf` |
| Übungsblatt für Studierende | `_site/labs/lab_01_beispiel.pdf` |
| Musterlösung | `_site/labs/lab_01_beispiel-musterloesung.pdf` |

Für bestehende lokale Abläufe werden Handouts zusätzlich unter `_handout/vorlesungen/` und Lab-PDFs mit den Suffixen `-studierende.pdf` bzw. `-musterloesung.pdf` unter `labs/_output/` abgelegt. Vorhandene PDFs im Quellordner sind kein Nachweis für einen erfolgreichen Build. Nach einem fehlgeschlagenen Build können dort noch Ergebnisse eines früheren erfolgreichen Laufs liegen; veröffentlicht werden darf nur nach erfolgreichem vollständigem Build.

Das reguläre Handout verwendet das Profil `handout` und PDF als Zielformat. Optional erzeugt `quarto render vorlesungen/01_kickoff.qmd --profile handout --to revealjs` ein HTML-Handout mit sichtbaren Notizen; es gehört nicht zum vollständigen Pflicht-Build. Vortrag und Handouts haben eigene Layoutvorgaben; das Erweiterungsformat `handout-revealjs` ist eine zusätzliche Variante. Details und Prüfungen stehen unter [Ausgabeformate und Prüfung](AGENTS.md#ausgabeformate-und-prüfung), die Werkzeugwahl unter [Diagramm-Entscheidungsbaum](AGENTS.md#diagramm-entscheidungsbaum).

## Publish mit GitHub Actions

Workflow: [`.github/workflows/publish.yml`](.github/workflows/publish.yml)

**Trigger:** Pull Request, Push auf `main` oder manuell (*Actions* → *Build and publish Quarto materials*).

Der Build-Job prüft die Build-Skripte, richtet die gemeinsame Toolchain ein und führt `python3 scripts/build-materials.py all` aus. Website, PDF-Handouts und beide Versionen der Übungsblätter müssen erfolgreich entstehen. Die vollständige Website einschließlich PDFs steht bei einem erfolgreichen Lauf 14 Tage als Artefakt `course-materials` zum Herunterladen bereit; Pull Requests veröffentlichen nichts.

Ein eigener Deploy-Job veröffentlicht nur auf `main` und nur nach erfolgreichem Build die bereits geprüften Dateien auf **`gh-pages`**. Er rendert nicht erneut und installiert über `scripts/setup.sh --quarto-only` nur das dafür benötigte Quarto. Nur dieser Job erhält Schreibrechte auf Repository-Inhalte.

**Einmalig:** Branch `gh-pages` anlegen und unter *Settings → Pages* als Veröffentlichungsquelle auswählen (*Deploy from a branch*). Die Repository-Richtlinien müssen dem Deploy-Job die angeforderten Schreibrechte erlauben. Für öffentliche Kursseiten das Repository **public** stellen.

**Hinweis:** Hochschullogos und Marken sind nicht Teil der CC-BY-Lizenz — siehe [`LICENSE`](LICENSE) und den Abschnitt *OER und Lizenz* in der `README.md`.
