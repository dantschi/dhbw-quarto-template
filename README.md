<!-- ============================================================
     TEMPLATE-HINWEIS — gesamten Abschnitt nach dem Kopieren löschen
     (von TEMPLATE-START bis TEMPLATE-ENDE inklusive dieser Kommentare)
     ============================================================ -->
<!-- TEMPLATE-START -->

## Template verwenden *(nach dem Kopieren löschen)*

Dieses Repository ist ein **generisches DHBW-Vorlesungstemplate** (Quarto-Website + Reveal.js-Folien, Apple-/DHBW-Design, GitHub-Pages-Publish).

### 1. Repository übernehmen

1. Nutzen Sie **Use this template** / Fork bzw. kopieren Sie das Repository.
2. Benennen Sie das Repo sinnvoll (z. B. `meinmodul-vorlesung`).
3. Aktivieren Sie unter *Settings → Pages* die Quelle **GitHub Actions** (Workflow `.github/workflows/publish.yml` bleibt unverändert).

### 2. Platzhalter ersetzen

Ersetzen Sie alle `[…]`-Platzhalter in:

| Datei | Typische Platzhalter |
|-------|----------------------|
| `_quarto.yml` | `[Modulname]`, `[Modulkürzel]`, `[GITHUB-USER]`, `[REPO]` |
| `README.md` | `[Beschreibung]`, Literatur, Tools |
| `index.qmd` | Titel |
| `vorlesungen/01_kickoff.qmd` | Folieninhalt, Zielgruppe, Themen |
| `.cursor/rules/dhbw-*.mdc` | Modulbezug, Zielgruppe (optional) |

### 3. Inhalte anpassen

- Weitere Vorlesungen als `vorlesungen/0N_….qmd` anlegen.
- Pro Vorlesung zwei Formate im YAML setzen:

```yaml
format:
  revealjs: default              # Vortrag (Notes nur mit Taste S)
  handout-revealjs:
    output-file: 0N_titel-handout.html   # Studienskript
```

- **Vortrag:** `quarto render vorlesungen/0N_….qmd --to revealjs` — Speaker Notes nur in der Speaker View (**S**).
- **Handout-PDF:** Handout-HTML öffnen → Taste **E** (Druckansicht) → Drucken als PDF. Dialog: **A4**, **Hochformat**, Ränder **Standard** (nicht „Keine“), Hintergrundgrafiken an.
- Design und Mermaid-Farben nicht ändern — Vorgaben liegen in `assets/styles/` (`slides.scss` / `custom.scss` / `handout.scss`).
- Lokal prüfen: `quarto preview` bzw. `quarto render`.

### 4. Aufräumen

Löschen Sie **diesen gesamten Abschnitt** (von `TEMPLATE-START` bis `TEMPLATE-ENDE`), damit er nicht auf der Kurswebsite erscheint.

<!-- TEMPLATE-ENDE -->


# [Modulname] ([Modulkürzel])

Herzlich willkommen zur Vorlesung **[Modulname] ([Modulkürzel])** an der Dualen Hochschule Baden-Württemberg Stuttgart.

[Beschreibung]

## Literatur

Die zentrale Referenz dieses Moduls ist:

> **[Autor:innen]**  
> *[Werktitel]*  
> [Verlag]

Definitionen, Terminologie und didaktischer Aufbau orientieren sich an diesem Standardwerk.

## Tools & Ressourcen

| Tool | Einsatz | Link |
|------|---------|------|
| **[Tool 1]** | [Kurzbeschreibung] | [Link] |
| **[Tool 2]** | [Kurzbeschreibung] | [Link] |

## OER & Lizenz

Die Vorlesungsinhalte dieses Materials (Texte, Code, Diagramme) sind eine **Open Educational Resource (OER)** und stehen unter der Lizenz **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)**.

Sie dürfen diese Inhalte teilen und bearbeiten, sofern Sie die Urheberschaft angemessen nennen. Der vollständige Lizenztext liegt in der Datei [`LICENSE`](LICENSE) im Repository.

**Ausnahme:** Das Logo der Dualen Hochschule Baden-Württemberg (DHBW) sowie andere geschützte Markenzeichen sind von der CC-BY-4.0-Lizenz ausdrücklich ausgenommen. Sie unterliegen dem Markenrecht der jeweiligen Inhaber und dürfen nicht ohne entsprechende Genehmigung verwendet werden.
