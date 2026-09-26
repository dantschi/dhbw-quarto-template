# DHBW Quarto Vorlesungstemplate — Einrichtung

> **Hinweis:** Dies ist ein **inoffizielles Dozenten-Template**, keine offizielle DHBW-Software.

GitHub-Template-Repository für Vorlesungswebsites an der **DHBW Stuttgart**: Quarto-Website, Reveal.js-Folien (Apple-/DHBW-Design), PDF-Handouts, Übungsblätter und Publish über GitHub Actions.

Die **GitHub-Pages-Startseite** ist der Inhalt von [`README.md`](README.md) (Kursübersicht wie bei [mct1](https://dantschi.github.io/mct1/)). Diese Datei (`TEMPLATE.md`) beschreibt nur die technische Einrichtung.

## Was enthalten ist

| Bereich | Inhalt |
|---------|--------|
| Website | Quarto-Projekt (`_quarto.yml`); Startseite = `README.md` via `index.qmd` |
| Folien | Reveal.js unter `vorlesungen/*.qmd`, Design in `assets/styles/` |
| Diagramme | Mermaid nativ; WaveDrom/PlantUML über `seandavi/quarto-livefigures` (siehe `dhbw-diagramme.mdc`) |
| Handout | Profil `handout` (`_quarto-handout.yml`) → PDF mit Folie + Dozentennotizen |
| Übungsblätter | `labs/*.qmd` mit Profil `solution`; Vorlage: `labs/lab_template.qmd` |
| CI/CD | `.github/workflows/publish.yml` → Website auf `gh-pages` + Handout- + Lab-PDFs |
| KI-Kontext | Cursor-Rules unter `.cursor/rules/` |

## Neues Modul anlegen

1. Auf GitHub **Use this template** → neues Repository erstellen.
2. Repository klonen; mit [Quarto](https://quarto.org/) lokal arbeiten.
3. Alle `[…]`-Platzhalter in `_quarto.yml`, `README.md`, `vorlesungen/01_kickoff.qmd` und optional in `.cursor/rules/` ersetzen.
4. Weitere Vorlesungen als `vorlesungen/0N_….qmd` anlegen (`format: revealjs`, Notizen in `::: notes`).
5. Übungsblätter als `labs/lab_NN_….qmd` anlegen (Vorlage: `labs/lab_template.qmd`).
6. Design/Livefigures möglichst unverändert lassen.

| Datei | Aktion |
|-------|--------|
| `_quarto.yml` | **Ersetzen:** `[Modulname]`, `[Modulkürzel]`, `[GITHUB-USER]`, `[REPO]` |
| `README.md` | **Ersetzen:** Kursinhalt, Einheiten-Tabelle, Literatur, Tools |
| `index.qmd` | behält `{{< include README.md >}}` |
| `vorlesungen/01_kickoff.qmd` | **Ersetzen:** Folieninhalt und Notizen |
| `labs/lab_01_beispiel.qmd` | **Ersetzen** oder aus `lab_template.qmd` ableiten |
| `.cursor/rules/dhbw-*.mdc` | optional **Ersetzen:** Modulbezug |

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
Diagramme: Node ≥ 18 für Livefigures; Entscheidungsbaum in `.cursor/rules/dhbw-diagramme.mdc`.

## Publish mit GitHub Actions

Workflow: [`.github/workflows/publish.yml`](.github/workflows/publish.yml)

**Trigger:** Push auf `main` oder manuell (*Actions* → *Publish Quarto Website*).

**Ablauf:** Website rendern → PDF-Handouts → Übungsblatt-PDFs → Publish auf Branch **`gh-pages`**.

**Einmalig:** Branch `gh-pages` vorhanden; *Settings → Pages* → Deploy from branch `gh-pages`; Actions mit Schreibrechten; für öffentliche Kursseiten Repo **public** stellen.

**Hinweis:** Hochschullogos und Marken sind nicht Teil der CC-BY-Lizenz — siehe [`LICENSE`](LICENSE) und den Abschnitt *OER und Lizenz* in der `README.md`.
