# DHBW Quarto Vorlesungstemplate

GitHub-Template-Repository für Vorlesungswebsites an der **DHBW Stuttgart**: Quarto-Website, Reveal.js-Folien (Apple-/DHBW-Design) und automatisches Publish inkl. PDF-Handout über GitHub Actions.

## Was enthalten ist

| Bereich | Inhalt |
|---------|--------|
| Website | Quarto-Projekt (`_quarto.yml`), Startseite, Sidebar |
| Folien | Reveal.js unter `vorlesungen/*.qmd`, Design in `assets/styles/` |
| Handout | Profil `handout` (`_quarto-handout.yml`) → PDF mit Folie + Dozentennotizen |
| CI/CD | `.github/workflows/publish.yml` → Website auf `gh-pages` + PDF-Handout |
| KI-Kontext | Cursor-Rules unter `.cursor/rules/` |

## Neues Modul anlegen

1. Auf GitHub **Use this template** → neues Repository erstellen (sinnvoller Name, z. B. `mct1-vorlesung`).
2. Repository klonen und lokal mit [Quarto](https://quarto.org/) arbeiten.
3. Platzhalter `[…]` ersetzen, insbesondere in:

| Datei | Typische Platzhalter |
|-------|----------------------|
| `_quarto.yml` | `[Modulname]`, `[Modulkürzel]`, `[GITHUB-USER]`, `[REPO]` (`site-url`) |
| `index.qmd` | Titel, Beschreibung, Literatur, Tools |
| `vorlesungen/01_kickoff.qmd` | Folieninhalt, Zielgruppe, Themen |
| `.cursor/rules/dhbw-*.mdc` | Modulbezug (optional) |

4. Weitere Vorlesungen als `vorlesungen/0N_….qmd` anlegen (`format: revealjs`, Notizen in `::: notes`).
5. Design und Mermaid-Farben möglichst unverändert lassen (`assets/styles/slides.scss`, `custom.scss`).

## Lokal arbeiten

```bash
# Website inkl. Folien
quarto preview

# Einzelne Vorlesung (Vortrag; Notizen nur mit Taste S)
quarto preview vorlesungen/01_kickoff.qmd

# PDF-Handout (Hochformat: Folieninhalt + Notizen)
quarto render vorlesungen/01_kickoff.qmd --profile handout --to pdf
# → _handout/vorlesungen/01_kickoff.pdf
```

Voraussetzungen für das PDF-Handout: Quarto, LaTeX/TinyTeX, für Mermaid-Diagramme ein Headless-Chrome (`quarto install chrome-headless-shell`).

## Publish mit GitHub Actions

Workflow: [`.github/workflows/publish.yml`](.github/workflows/publish.yml)

**Trigger:** Push auf `main` oder manuell unter *Actions* → *Publish Quarto Website* → *Run workflow*.

**Ablauf:**

1. Quarto + TinyTeX einrichten  
2. Website rendern (`quarto render` → `_site/`)  
3. PDF-Handout bauen  
   `quarto render vorlesungen/01_kickoff.qmd --profile handout --to pdf`  
4. PDF nach `_site/vorlesungen/01_kickoff-handout.pdf` kopieren  
5. Mit `quarto-dev/quarto-actions/publish` nach **GitHub Pages** (`gh-pages`) veröffentlichen  

Die Website wird auch dann publiziert, wenn das Handout scheitert; der Job endet in dem Fall trotzdem mit Fehler (sichtbar in Actions).

### Einmalige Einrichtung für Pages

1. Branch `gh-pages` muss auf dem Remote existieren (beim Template ggf. bereits angelegt; sonst einmalig leeren Branch pushen oder lokal `quarto publish gh-pages` ausführen).
2. Unter *Settings → Pages*: Quelle **Deploy from a branch** → Branch **`gh-pages`** / `/ (root)`.
3. Unter *Settings → Actions → General*: Workflow-Berechtigung **Read and write**.
4. **Öffentliches** Repository (oder bezahlter Plan): GitHub Pages für private Repos im kostenlosen Account ist eingeschränkt. Für eine öffentliche Kurswebsite das Repo auf **public** stellen.

Veröffentlichte URL typischerweise:

`https://[GITHUB-USER].github.io/[REPO]/`

(entspricht `website.site-url` in `_quarto.yml`)

### Handout auf der Website

Nach erfolgreichem Lauf z. B.:

`https://[GITHUB-USER].github.io/[REPO]/vorlesungen/01_kickoff-handout.pdf`

Weitere Vorlesungen: im Workflow analoge `quarto render … --profile handout --to pdf`-Schritte ergänzen und die PDFs nach `_site/vorlesungen/` kopieren.

## Projektstruktur (Kurz)

```
_quarto.yml              # Website & Vortrags-Folien
_quarto-handout.yml      # Profil „handout“ (PDF-Skript)
index.qmd                # Kurs-Startseite (Inhalt für Studierende)
vorlesungen/             # Reveal.js-Vorlesungen
assets/styles/           # SCSS (Website, Folien, Handout-Druck)
filters/notes-handout.lua
.github/workflows/publish.yml
.cursor/rules/           # Cursor-Regeln für konsistente Inhalte
```

## Lizenz

Vorlesungsinhalte in abgeleiteten Kurs-Repos sollten als OER unter **[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)** gekennzeichnet werden (Vorlage dazu in `index.qmd`). Das **DHBW-Logo** und andere Markenzeichen sind davon ausgenommen und unterliegen dem Markenrecht der jeweiligen Rechteinhaber. Details und der Lizenztext liegen in [`LICENSE`](LICENSE).
