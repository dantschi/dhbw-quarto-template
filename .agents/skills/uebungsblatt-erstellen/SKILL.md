---
name: uebungsblatt-erstellen
description: Erstellt oder überarbeitet Übungs- und Laborblätter als nummerierte Quarto-Quelle mit überprüfter Musterlösung und getrennten PDF-Versionen.
---

# Übungsblatt erstellen

## Einsatz und Grundlagen

Verwenden, wenn Übungen, Programmieraufgaben oder Laborversuche zu einer Einheit erstellt oder angepasst werden.
Der Skill erzeugt ein bearbeitbares Blatt und dessen Musterlösung aus einer gemeinsamen Quelle.

Vor Beginn lesen:

- [Gemeinsame Arbeitsweise](../references/arbeitsweise.md) und [Projektregeln](../../../AGENTS.md)
- Einschlägige Abschnitte der [Fachregeln](../../../FACHREGELN.md)
- [Kurskontext](../../../README.md), zugehörige Einheit und vorhandene Übungsblätter
- [Blattvorlage](../../../labs/lab_template.qmd), [Lab-Konfiguration](../../../labs/_quarto.yml)
  und [Lösungsprofil](../../../labs/_quarto-solution.yml)
- Für Einrichtung und Ausgaben die [technische Anleitung](../../../TEMPLATE.md)

## Eingaben klären

Ermitteln: Thema/Einheit, Lernziele, Vorkenntnisse, Bearbeitungszeit, Einzel-/Gruppenarbeit und erlaubte Hilfsmittel.
Bei Software und Hardware benötigte Versionen, Plattform und tatsächliche Verfügbarkeit berücksichtigen.
Vorhandene Angaben zuerst aus dem Kurskontext und den Quellen übernehmen.
Nur entscheidende Lücken erfragen; didaktische Beispielwerte und andere tragfähige Annahmen kennzeichnen.

Bei Überarbeitungen bestehende Aufgabenfolge und Inhalte grundsätzlich erhalten.
Größere Änderungen der Schwierigkeit oder des didaktischen Aufbaus begründet vorschlagen.
Bereits beauftragte Änderungen direkt ausarbeiten; das Blatt nicht an einer Zwischenfreigabe stoppen.

## Ablauf

1. **Zuordnung herstellen.** Jede Aufgabe einem beobachtbaren Lernziel zuordnen.
   Bearbeitung und Besprechung realistisch bemessen; passende Progression und typische Fehlannahmen berücksichtigen.
2. **Kanonische Quelle anlegen.** Die Vorlage nach `labs/lab_NN_thema.qmd` übernehmen oder das bestehende Blatt bearbeiten.
   Eine freie Nummer passend zum Kurs verwenden; keine zweite unabhängige Lösungsquelle erzeugen.
3. **Aufgaben formulieren.** Voraussetzungen, benötigte Hilfsmittel, Eingaben und erwartete Arbeitsergebnisse angeben.
   Relevante Randbedingungen, Darstellungen und Bewertungskriterien verständlich beschreiben.
   Aufgaben müssen mit den bereitgestellten Informationen lösbar sein.
4. **Versuche reproduzierbar beschreiben.** Bei Laboraufgaben Aufbau, Parameter, Arbeitsschritte und Auswertung angeben.
   Zulässige Daten und nötige Skripte im Repository erhalten; konkrete Hardware- und API-Aussagen belegen.
   Messungen, Simulationen und Modellrechnungen unterscheidbar benennen.
5. **Musterlösung vollständig ausarbeiten.** Rechenweg, Begründung, Ergebnis und typische Fehler erläutern.
   Lösungsinhalte ausschließlich in profilgebundene Bereiche schreiben:

   ```markdown
   ::: {.content-visible when-profile="solution"}
   **Musterlösung Aufgabe 1**

   Nachvollziehbarer Lösungsweg und Ergebnis.
   :::
   ```

   Auch lösungsverratende Hinweise oder Abbildungen entsprechend behandeln.
   Die Aufgabenstellung muss ohne Lösungsblöcke vollständig bleiben.
6. **Fachlich gegenprüfen.** Die Aufgaben aus Studierendensicht lösen und Angaben gegen Lösungen abgleichen.
   Rechnungen unabhängig prüfen; Code mit relevanten Normal-/Randfällen prüfen, soweit Werkzeuge verfügbar sind.
   Fachabhängige Modellannahmen und Nachweisgrenzen offenlegen; keine Ausführung oder Messung erfinden.
7. **Beide Fassungen bauen.** Aus dem Repository-Stamm die gemeinsame Umgebung verwenden:

   ```bash
   source scripts/activate.sh
   python3 scripts/build-materials.py labs
   ```

   Fehlende Einrichtung anhand der technischen Anleitung herstellen; Renderfehler beheben.
8. **Lösungstrennung kontrollieren.** Beide frisch erzeugten PDFs öffnen und ihren Text/Inhalt vergleichen.
   Prüfen, dass Lösungen und Lösungskennzeichnungen nur in der Musterlösung erscheinen.
   Zusätzlich Aufgaben, Abbildungen, Formeln, Arbeitsraum und Seitenumbrüche auf Vollständigkeit und Lesbarkeit prüfen.
   Eine bloße Existenzprüfung oder Suche nach dem Wort „Musterlösung“ reicht nicht aus.
9. **Einbindung und Abschluss.** Bei Bedarf Kursübersicht auf die beiden vorgesehenen Ausgabepfade ergänzen.
   `python3 scripts/build-materials.py all` als vollständigen Projektcheck ausführen.
   Änderungen, tatsächliche Prüfungen und verbleibende Grenzen knapp berichten.

## Ergebnisse

- Eine nummerierte `.qmd`-Quelle mit vollständigen Aufgaben und profilgebundenen Musterlösungen
- Benötigte Daten, Diagrammquellen und Hilfsskripte für nachvollziehbare Bearbeitung
- Studierenden-PDF `_site/labs/lab_NN_thema.pdf`
- Lösungs-PDF `_site/labs/lab_NN_thema-musterloesung.pdf`
- Abschlussbericht einschließlich belegter Lösungstrennung und fachlicher Prüfungen

## Abschlussprüfung

- Sind jede Aufgabe und ihre Lösung unter denselben dokumentierten Annahmen korrekt und vollständig?
- Passen Schwierigkeit, Hilfsmittel und Umfang zum Kurs und zum Zeitbudget?
- Sind beide PDFs frisch, lesbar und auf Lösungstrennung geprüft?
- Sind tatsächlich ausgeführte Versuche und lediglich hergeleitete Ergebnisse klar unterschieden?

## Beispielaufträge

- „Erstellen Sie Blatt 3 zu Zweierkomplement und Überlauf mit 45 Minuten Bearbeitungszeit.“
- „Ergänzen Sie das Interrupt-Labor um eine Aufgabe zu gemeinsam genutzten Daten samt Musterlösung.“
