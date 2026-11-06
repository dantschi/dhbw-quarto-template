---
name: quiz-erstellen
description: QuizAcademy-Fragen aus vorhandenen Vorlesungen erstellen oder überarbeiten, mit Lernzielbezug, plausiblen Distraktoren, fachlicher Prüfung und validierter CSV-Ausgabe. Verwenden bei Aufträgen zu Quizfragen oder QuizAcademy-CSV-Dateien.
---

# Quiz erstellen oder überarbeiten

## Einsatz und Kontext

Nutze diesen Skill für konkrete Quizaufträge auf Basis vorhandener Lehrinhalte. Ein reines Review ohne Änderungen gehört zu `material-review`; der Quarto-Build ersetzt keine Quizprüfung.

Lies die [gemeinsame Arbeitsweise](../references/arbeitsweise.md), die [Projektregeln](../../../AGENTS.md), die [Quizregeln](../../../quizacademy/AGENTS.md) und die zum Inhalt passenden [Fachregeln](../../../FACHREGELN.md). Diese Regeln bleiben die maßgebliche Quelle für Format und Qualität.

## Benötigte Eingaben

- Zugehörige Vorlesungsquellen und Lernziele bzw. gewünschte Themen und Vorkenntnisse.
- Ziel-CSV oder gewünschte neue Datei unter `quizacademy/`; bei neuen Quizzen die gewünschte Fragenzahl und das Niveau, soweit vorgegeben.
- Relevante Modellannahmen, beispielsweise Wortbreite, Sprachstandard, Anfangszustand, Controller oder Scheduling-Modell.

Nutze vorhandenen Kurskontext und Quellen zuerst. Kläre nur Angaben, deren Fehlen keine eindeutigen, stoffgerechten Fragen zulässt. Sonstige Annahmen im Arbeitsbericht benennen; eine für die Lösung entscheidende Annahme muss in Kurskontext oder Frage eindeutig feststehen.

## Ablauf

1. Lies Vorlesung und vorhandene CSV vollständig im beauftragten Umfang. Ordne die behandelten Lernziele den geplanten Fragen zu. Bei Überarbeitung vorhandene Struktur, Themenabdeckung und Fragenzahl erhalten, soweit der Auftrag nichts anderes verlangt. Größere Umstrukturierungen begründet vorschlagen; bereits angeforderte Änderungen ohne zusätzliche Freigabeschleife umsetzen.
2. Entwickle Aufgaben, die Begriffsverständnis, Anwendung oder fachliche Unterscheidung entsprechend dem Lernziel prüfen. Formuliere jede Frage so, dass unter den genannten Voraussetzungen genau eine Antwort richtig ist. Unbekanntes Zusatzwissen darf die Lösung nicht bestimmen.
3. Leite die richtige Antwort nachvollziehbar her und konstruiere drei plausible Distraktoren aus typischen Fehlvorstellungen. Prüfe jede Option unabhängig, einschließlich relevanter Randfälle. Unterscheide etwa Zweierkomplement und vorzeichenlose Darstellung, Parität und Genau-eins, oder Messung und WCET-Nachweis gemäß Fachregel.
4. Schreibe eine knappe Erläuterung mit Begründung der Lösung und der maßgeblichen Abgrenzung. Prüfe unbeabsichtigte Hinweise durch Länge, Grammatik, Antwortposition oder wiederkehrende Zusätze; keine feste Längenquote anwenden.
5. Speichere das Quiz als UTF-8-CSV mit der unveränderten Elf-Spalten-Kopfzeile und den Feldwerten aus den Quizregeln. Verwende eine echte CSV-Schreibfunktion für korrektes Escaping von Anführungszeichen. Semikolons innerhalb eines Feldes sind auch bei CSV-Quoting gemäß Projektregel unzulässig. Vorhandene Dateien nicht stillschweigend umkodieren oder Fragen entfernen.
6. Führe den [Formatvalidator](scripts/validate_quiz.py) aus. Der folgende Aufruf gilt aus dem Repository-Stamm; ersetze den Beispielpfad durch die tatsächliche Datei:

   ```bash
   python3 .agents/skills/quiz-erstellen/scripts/validate_quiz.py quizacademy/einheit_01.csv
   ```

   Mehrere Dateien können gemeinsam angegeben werden; `--help` beschreibt den Aufruf. Der Validator benötigt nur Python-Standardbibliothek, verändert nichts und meldet Dateipfad, Datensatz und Zeile bei strukturellen Fehlern. Korrigiere Fehler und wiederhole die betroffene Prüfung.
7. Prüfe anschließend fachlich, ob Quelle, Lernziel, Annahmen, richtige Antwort und Erläuterung zusammenpassen. Eine erfolgreiche CSV-Prüfung beweist weder die fachliche Eindeutigkeit noch einen tatsächlich ausgeführten Import in QuizAcademy.

## Ergebnis und Abschluss

- Die beauftragten Quiz-CSV-Dateien enthalten vollständige Fragen und Erläuterungen ohne unangeforderte Änderung der Fragenzahl.
- Berichte knapp Quellenbezug, Fragenzahl und Abdeckung, wichtige Änderungen sowie tatsächlich ausgeführte Prüfungen und offene fachliche Grenzen.
- Nenne Formatprüfung und fachliche Prüfung getrennt. Behaupte einen Import oder eine Ausführung von Lehrcode nur nach tatsächlicher Durchführung. Veröffentlichung und Git-Operationen richten sich nach dem Nutzerauftrag.

## Beispielaufträge

- „Erstelle acht Quizfragen zu `vorlesungen/03_zahlendarstellung.qmd`, Schwerpunkt Zweierkomplement und Überlauf, unter `quizacademy/03_zahlendarstellung.csv`."
- „Überarbeite die Distraktoren in diesem Quiz zur Prioritätsinversion. Erhalte Fragenzahl und Themenstruktur und prüfe die vorausgesetzten Scheduling-Annahmen."
