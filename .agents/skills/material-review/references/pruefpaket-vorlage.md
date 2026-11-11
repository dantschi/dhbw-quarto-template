# Vorlage für ein abgegrenztes Prüfpaket

Diese Vorlage ergänzt [material-review](../SKILL.md). Sie überträgt die Idee
frischer Prüfperspektiven aus dem [EGM-Review-Loop](https://github.com/google/elephant-goldfish-model/blob/main/skills/egm-review-loop/SKILL.md)
auf Lehrmaterial. Ein ausgefülltes Paket beschreibt einen Prüfauftrag; es ist
noch kein ausgeführter Review oder Qualitätsnachweis.

## Paket vorbereiten

- Begrenze das Paket auf einen zusammenhängenden Themenbereich, etwa eine Einheit
  mit ihren Übungen und Quizfragen. Teile umfangreiche Kurse in passende Pakete;
  nenne nötige Querverweise ausdrücklich.
- Fülle die folgenden Felder aus den tatsächlich vorliegenden Materialien und
  Vorgaben. Übernimm relevante Entscheidungen neutral mit Quelle, ohne Chatverlauf,
  Autorenrechtfertigungen, gewünschtes Urteil oder frühere Prüferurteile beizulegen.
- Verwende Dateipfade relativ zum Repository-Stamm. Bei Ausschnitten zusätzlich
  Folientitel, Aufgaben- bzw. Fragekennung und den nötigen Kontext nennen. Eine
  Quellenliste begrenzt den Auftrag, sie ist keine technische Zugriffssperre.
- Gib beiden Prüfrollen denselben festgehaltenen Materialstand. Ändern sich Quellen
  während der Prüfung, kennzeichne die betroffenen Ergebnisse und aktualisiere das
  Paket für die Nachprüfung. Ein Commit allein erfasst keine uncommitteten Änderungen.
- Markiere fehlende Angaben als offen und Schätzungen als solche. Frage nur nach,
  wenn eine belastbare Prüfung davon abhängt; prüfe unabhängige Teile weiter.
- Ein Paket kann direkt im Auftrag stehen. Eine gesonderte Datei ist nur nötig,
  wenn sie angefordert oder für Wiederverwendung sinnvoll ist. Das
  [Beispielpaket](../examples/pruefpaket-lab-02-suchen.md) zeigt einen konkreten Zuschnitt.

## Ausfüllbares Paket

```markdown
# Prüfpaket: [Einheit oder Thema]

## 1. Auftrag und Stand

- Ziel und Prüfschwerpunkt: [konkreter Auftrag]
- Umfang: [Einheit, Abschnitt, Aufgaben-/Fragekennungen; vollständig oder Stichprobe]
- Ausgeschlossen: [Bereiche, die nicht geprüft werden]
- Stand: [Commit oder Snapshot; uncommittete Dateien mit ihrem konkreten Stand benennen]
- Arbeitsverzeichnis: [Repository-Stamm]
- Status: vorbereitet; fachliche und didaktische Prüfung noch nicht durchgeführt.

## 2. Kursrahmen mit Quellen

- Zielgruppe, Semester und Vorkenntnisse: [Angaben und Fundstelle]
- Lernziele und Zusammenhang mit Nachbareinheiten: [Angaben und Fundstelle]
- Bearbeitungszeit, Hilfen und Hilfsmittel: [Vorgabe oder gekennzeichnete Schätzung]
- Prüfungsform und Anforderungen: [belegte Vorgaben oder offen]
- Fachliche Annahmen: [Sprache/Version, Plattform, Zahlendarstellung, Zeitmodell, soweit relevant]
- Offene Angaben und deren Folgen für die Prüfung: [konkret]

## 3. Materialien und Regeln

| Pfad oder genaue Quelle | Zu prüfender Ausschnitt und Zweck | Rolle |
|---|---|---|
| [Vorlesungsquelle samt notes] | [Folien/Abschnitt] | [Fachprüfung/Lernweg/beide] |
| [Übung, Quiz, Startcode, Daten oder öffentliche Tests] | [Aufgaben/Fragen] | [Rolle] |
| [Musterlösung/Referenzcode] | [zugehörige Lösungen; Lesephase angeben] | [Rolle] |
| [frische HTML-/PDF-/ZIP-Ausgabe, falls vorhanden] | [Zuordnung zur Quelle] | [Rolle] |
| [Projekt- und Bereichsregeln, einschlägige Fachregeln, Kursglossar] | [relevante Abschnitte] | beide |
| [fachliche Quellen mit Ausgabe/Version und Fundstelle] | [zu belegende Aussagen] | [Rolle] |

Fehlende zugehörige Materialien ausdrücklich aufführen; keine Vorlesung oder
Quizzuordnung allein aus einer ähnlichen Dateinummer ableiten. Allgemeine Regeln
bleiben gültig, ersetzen aber keine fehlenden Modulvorgaben oder Fachquellen.

## 4. Tatsächliche Nachweise

- Build-/Teststatus: [nicht ausgeführt oder Befehl, Ergebnis und geprüfter Stand]
- Frische und Herkunft gerenderter Ausgaben: [belegt oder nicht geprüft]
- Visuelle Prüfung: [Ausgaben/Seiten/Folien oder nicht durchgeführt]
- Weitere Nachweise und Grenzen: [Rechnung, Simulation, Messung, studentische Rückmeldungen]

Vorhandene Dateien gelten nicht automatisch als frisch oder erfolgreich geprüft.
Aus dem Quelltext erwartete Resultate sind von tatsächlich beobachteten zu trennen.

## 5. Getrennte Prüfaufträge

Fachprüfung: Kontrolliere Aussagen, Annahmen, Rechnungen, Code, Randfälle und
Lösungen. Leite kritische Ergebnisse möglichst selbst her und vergleiche sie erst
danach mit der Referenz. Prüfe Widersprüche und Terminologie zwischen den
aufgeführten Materialien. Benenne nicht belegbare Aussagen als offene Fragen.

Lernweg und Lösbarkeit: Gib den erkennbaren Gedankengang zuerst kurz in eigenen
Worten wieder. Prüfe anhand der dokumentierten Vorkenntnisse die Begriffseinführung
und fehlende Zwischenschritte. Bei Vorlesungen Einstiegsfrage, Abschnittsorientierung
und Skriptfluss prüfen; bei Aufgaben Anspruch und selbstständige Lösbarkeit.
Foliennähe nur anhand tatsächlich zugehöriger Materialien beurteilen.
Nutze eine getrennte Studierendenversion zunächst ohne Musterlösung, sofern sie
vorliegt, und vergleiche anschließend die Lösung. Ist diese Trennung nicht möglich,
benenne die Grenze; behaupte keinen unbeeinflussten Lösungsversuch.

Beide Rollen lesen nur das Paket und die erforderlichen aufgeführten Materialien
und Regeln als Ausgangskontext. Weitere benötigte Quellen oder Abhängigkeiten
gezielt benennen. Keine Dateien ändern und keine Autorenabsicht aus dem Chat ergänzen.
Ein KI-Prüfer bildet das Vorwissen tatsächlicher Studierender nicht verlässlich nach.

## 6. Erwarteter Bericht je Prüfrolle

- Rolle und tatsächlich geprüfter Stand.
- Kurze Inhaltsrekonstruktion bei der Lernwegprüfung.
- Priorisierte Befunde: Datei und Zeile bzw. Folie/PDF-Seite/Fragekennung,
  konkreter Beleg oder Gegenbeispiel, Auswirkung und ausführbarer Korrekturvorschlag.
- Einordnung als gesicherter Fehler, begründete Verbesserung oder offene Fachfrage.
- Abdeckung: je Material/Kriterium vollständig, stichprobenartig oder nicht geprüft;
  tatsächliche Rechnungen, Tests und Sichtprüfungen getrennt ausweisen.
- Offene Angaben und Grenzen; bei ausbleibenden Befunden verbleibende Prüflücken nennen.

## 7. Zusammenführung und Nachprüfung

Die koordinierende Instanz verifiziert Befunde an Quellen und Gegenbeispielen,
entfernt Doppelungen und klärt widersprüchliche Bewertungen. Uneinigkeit wird
nicht durch Mehrheitsentscheid oder ein vorausgesetztes Autorenurteil aufgelöst.
Kennzeichne nicht durchgeführte Prüfaufträge und nicht bestätigte Befunde.

Ein reiner Review endet mit Bericht. Nur beauftragte Korrekturen umsetzen und
betroffene Stellen gezielt erneut prüfen. Bei geändertem Materialstand Paket,
Zeilen-/Seitenangaben und Nachweise aktualisieren; keine automatische Freigabeschleife.
```

## Frischer Kontext und Grenzen

Bei unterstützten Werkzeugen die getrennten Prüfaufträge an neue Agenten ohne
übernommene Gesprächshistorie geben, bei Codex beispielsweise mit
`fork_turns: "none"`. Projektanweisungen und Zugriff auf Dateien können trotzdem
bestehen; daraus folgt keine vollständige technische oder fachliche Unabhängigkeit.
Ein Rollenwechsel im selben Gespräch ist kein frischer Kontext.

Sind solche Agenten nicht verfügbar, den normalen Review fortsetzen und die
fehlende frische Zweitperspektive ausdrücklich nennen. Ein ausdrücklich verlangter
unabhängiger Prüfauftrag gilt dann als nicht durchgeführt. Bei kleinen Korrekturen
kann der normale Review ohne dieses Paket ausreichen.
