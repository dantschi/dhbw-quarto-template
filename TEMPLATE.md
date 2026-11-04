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
| CI/CD | `.github/workflows/publish.yml` → Website auf `gh-pages` + Handout- + Lab-PDFs |
| KI-Kontext | Toolübergreifende Regeln in [`AGENTS.md`](AGENTS.md), ergänzt durch [`FACHREGELN.md`](FACHREGELN.md) sowie Regeln in `vorlesungen/` und `quizacademy/` |

## Neues Modul anlegen

1. Auf GitHub **Use this template** → neues Repository erstellen.
2. Repository klonen; mit [Quarto](https://quarto.org/) lokal arbeiten.
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

## Lokal arbeiten

```bash
quarto preview
quarto preview vorlesungen/01_kickoff.qmd
quarto render vorlesungen/01_kickoff.qmd --profile handout --to pdf
# → _handout/vorlesungen/01_kickoff.pdf

quarto render labs/lab_01_beispiel.qmd --to pdf
quarto render labs/lab_01_beispiel.qmd --to pdf --profile solution
./build_labs.sh
```

PDF-Handout: Quarto, TinyTeX/LaTeX; für Mermaid: `quarto install chrome-headless-shell`.  
Diagramme: Node ≥ 18 für Livefigures; siehe [Diagramm-Entscheidungsbaum](AGENTS.md#diagramm-entscheidungsbaum).

Das reguläre Handout entsteht mit `--profile handout --to pdf`. Optional erzeugt `quarto render vorlesungen/01_kickoff.qmd --profile handout --to revealjs` ein HTML-Handout mit sichtbaren Notizen. Vortrag und Handouts haben eigene Layoutvorgaben; das Erweiterungsformat `handout-revealjs` ist eine zusätzliche Variante. Details und Prüfungen stehen unter [Ausgabeformate und Prüfung](AGENTS.md#ausgabeformate-und-prüfung).

## Publish mit GitHub Actions

Workflow: [`.github/workflows/publish.yml`](.github/workflows/publish.yml)

**Trigger:** Push auf `main` oder manuell (*Actions* → *Publish Quarto Website*).

**Ablauf:** Website rendern → PDF-Handouts → Übungsblatt-PDFs → Publish auf Branch **`gh-pages`**.

**Einmalig:** Branch `gh-pages` vorhanden; *Settings → Pages* → Deploy from branch `gh-pages`; Actions mit Schreibrechten; für öffentliche Kursseiten Repo **public** stellen.

**Hinweis:** Hochschullogos und Marken sind nicht Teil der CC-BY-Lizenz — siehe [`LICENSE`](LICENSE) und den Abschnitt *OER und Lizenz* in der `README.md`.
