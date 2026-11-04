# Quizfragen für quizacademy

Diese Regeln ergänzen die [zentralen Projektregeln](../AGENTS.md).

Gilt beim Erstellen und Überarbeiten von CSV-Dateien in `quizacademy/` (`quizacademy/**/*.csv`). Zielgruppe: Bachelor EIT, DHBW Stuttgart, mit den im Kurskontext dokumentierten Vorkenntnissen. Fragen, Antwortoptionen und Erläuterungen müssen auf den behandelten Konzepten und Lernzielen der zugehörigen Vorlesung beruhen. Falsche Optionen dürfen gezielt falsche Kombinationen oder Verallgemeinerungen dieser Konzepte enthalten; unbekanntes Zusatzwissen darf nicht über die Lösung entscheiden. Keine Messwerte, APIs oder Hardwareläufe erfinden. Rechenfragen mit ausdrücklich angegebenen didaktischen Ausgangsdaten sind erlaubt; Ergebnisse müssen rechnerisch geprüft sein.

## Syntax nicht ändern

Semikolon, eine Kopfzeile, genau vier Optionen, genau eine richtige Antwort:

```text
Frage;Typ;Antwort 1;Korrekt 1;Antwort 2;Korrekt 2;Antwort 3;Korrekt 3;Antwort 4;Korrekt 4;Erläuterung
```

`Typ` bleibt `Multiple Choice`. Korrektheit nur `correct` oder `incorrect`. Kein Semikolon in Frage, Antwort oder Erläuterung. Spalten weder ergänzen noch umbenennen. Bestehende Dateien behalten ihre Fragenzahl, sofern nicht ausdrücklich anders verlangt.

## Schwierigkeit

Richte Fragen an den Lernzielen aus. Begriffsfragen sind für grundlegende Lernziele zulässig; vermeide bloßes Wiedererkennen wörtlich kopierter Folientexte. Prüfe bei passenden Lernzielen Anwendung, Rechnung und Unterscheidungen: notwendige gegen hinreichende Aussage, zwei ähnlich benannte Größen, erlaubter Sonderfall gegen verbotene Verallgemeinerung. Falsche Optionen bilden typische Fehlvorstellungen aus derselben Vorlesung ab, keine absurden Außenseiter.

Formuliere die nötigen Voraussetzungen so, dass unter ihnen genau eine Option richtig ist. Die Erläuterung begründet in einem oder zwei Sätzen die richtige Antwort und die maßgebliche Abgrenzung zu den falschen Optionen. Halte Fragestellungen eindeutig und vermeide unnötige Verneinungen und sprachliche Fangfragen.

Prüfe fachabhängige Annahmen nach den [einschlägigen Fachregeln](../FACHREGELN.md). Nenne insbesondere Wortbreite, Vorzeicheninterpretation, Anfangszustand oder Zeitmodell, wenn sie über die richtige Antwort entscheiden und nicht bereits im Kurskontext eindeutig festgelegt sind. Code mit undefiniertem Verhalten darf keine vermeintlich eindeutig vorhersagbare Ausgabe als richtige Antwort voraussetzen.

## Antwortgestaltung

Richtige Antworten dürfen nicht systematisch durch Länge, Detailgrad, Grammatik oder wiederkehrende Zusätze erkennbar sein. Formuliere alle Optionen als vergleichbar präzise, in sich abgeschlossene Aussagen. Nutze keine feste Längenquote und verlängere falsche Optionen nicht künstlich. Verteile die Positionen der richtigen Antworten ohne auffälliges Muster.

## Qualitätsprüfung

Prüfe vor dem Abschluss die unveränderte Kopfzeile, elf Spalten je Zeile, `Multiple Choice`, vier nichtleere und unterschiedliche Antwortoptionen sowie genau ein `correct` und drei `incorrect`. Prüfe außerdem fachliche Eindeutigkeit, Bezug zu Vorlesung und Lernziel, Rechenergebnisse und unbeabsichtigte Lösungshinweise. Berichte nur Prüfungen, die tatsächlich durchgeführt wurden.
