# Regeln für Vorlesungsfolien

Diese Regeln ergänzen die [zentralen Projektregeln](../AGENTS.md) und gelten für alle Quarto-Folien unter `vorlesungen/` (`vorlesungen/**/*.qmd`), einschließlich ihrer Notizen.

## Aktivierende Einstiegsfrage je Vorlesung

Beginne jede Vorlesungseinheit mit einer themenbezogenen Frage als erster inhaltlicher Folie nach der Titelfolie, vor Agenda und Lernzielen. Die Frage soll vorhandene Vorstellungen herausfordern und Vorwissen aktivieren: etwa eine begründete Vermutung, Vorhersage oder Entscheidung zu einem greifbaren Fall verlangen. Knüpfe an die dokumentierten Vorkenntnisse oder verständliche Alltagserfahrungen an. Die Frage muss einen Bezug zum Lernziel der Einheit haben und ohne die erst noch einzuführenden Begriffe bearbeitbar sein; vermeide Fangfragen.

Plane eine kurze Denk- und gegebenenfalls Austauschphase im Zeitbudget ein. Lasse Antworten und ihre Begründungen sammeln, bevor du die fachliche Auflösung gibst. Nimm die Antwort auf der Einstiegsfolie nicht vorweg. Die vollständigen `::: notes` erläutern den Vorwissensbezug, erwartbare Antworten, typische Fehlvorstellungen, nötige Annahmen, eine fachlich begründete Auflösung und den Übergang zum Thema. Sie müssen neben den Moderationshinweisen auch einen verständlichen Lerntext enthalten.

Greife die Frage im Verlauf oder spätestens am Abschluss erneut auf und beantworte sie mit dem inzwischen erarbeiteten Wissen. Mache sichtbar, welche anfängliche Vorstellung bestätigt, präzisiert oder korrigiert wird. Passe beim Ableiten einer neuen Vorlesung aus dem Template die Beispielfrage an deren Thema und Vorkenntnisse an.

Diese Vorgabe gilt beim Erstellen und inhaltlichen Überarbeiten einer Einheit. Reine Ausgabeprüfungen oder kleine technische Änderungen lösen keine automatische Umstrukturierung bestehender Vorlesungen aus.

## Sichtbare Abschnitte und Orientierung

Füge vor jedem neuen größeren inhaltlichen Themenblock eine eigene Abschnittsfolie mit einer prägnanten Zwischenüberschrift ein. Verwende dieselben Abschnittsbezeichnungen wie in der Agenda bzw. im Lernweg der Einheit. Eine knappe Standortangabe soll sichtbar machen, was bereits erarbeitet wurde und welche Frage der folgende Abschnitt behandelt. Die aktivierende Einstiegsfrage bleibt die erste inhaltliche Folie nach der Titelfolie.

Orientiere die Gliederung an zusammenhängenden Themen und Lernzielen; nicht jede einzelne Inhaltsfolie benötigt eine zusätzliche Abschnittsfolie. Auch Abschnittsfolien beginnen mit `##` und erhalten eigene `::: notes`. Verwende dafür keine Ebene-1-Überschriften oder `---` als Folientrenner, damit Vortrag und Handout dieselben Foliengrenzen verwenden.

Die Abschnittsnotizen führen wie ein kurzer Kapitelanfang in den folgenden Gedankengang ein: Sie verbinden bisherige Ergebnisse mit dem neuen Problem und erläutern dessen Bedeutung für das Lernziel. Ergänze diese Orientierung beim Erstellen und im beauftragten Umfang inhaltlicher Überarbeitungen; reine Renderprüfungen und kleine technische Änderungen gliedern bestehende Inhalte nicht automatisch neu.

## UTF-8 bei Folien-Edits

Deutsche `.qmd`-Folien sind unter Windows **UTF-8-fragil**: Editor-/Patch-Tools können Unicode stillschweigend zerstören (typisch: `→` wird zu `?`, Umlaute/`—` zu Mojibake). Vor dem finalen Rebuild immer prüfen.

### Nach jedem Edit prüfen

```powershell
python -c "from pathlib import Path; t=Path(r'vorlesungen/DATEI.qmd').read_text(encoding='utf-8'); print('arrows', t.count('\u2192'), 'qmarks', t.count(' ? '), 'fffd', t.count('\ufffd'))"
```

- `arrows` sollte zum Inhalt passen (nicht plötzlich 0)
- ` ? ` zwischen Wörtern (z. B. `Software ? Hardware`) deutet auf verlorene `→`
- `\ufffd` oder typische CP1252-Mojibake (`Ã¤`, `â€”`) → Encoding kaputt

### Sicher editieren

- **Bevorzugt:** Python-Skript mit `\uXXXX`-Escapes und `Path.write_text(..., encoding='utf-8', newline='\n')`
- Unter Windows PowerShell 5.1 erzeugt `Set-Content -Encoding UTF8` ein BOM; in PowerShell 7 bei Bedarf ausdrücklich `-Encoding utf8NoBOM` verwenden. Eine BOM kann die Mermaid-Erkennung beeinträchtigen — siehe [Tech-Stack und Quarto-Konventionen](../AGENTS.md#tech-stack-und-quarto-konventionen).
- Kein UTF-8-BOM in `.qmd`

### Typische Reparatur

1. Datei als `utf-8` lesen; falls kaputt, Herkunftscode (oft `cp1252`) → korrekt als `utf-8` speichern
2. Ersetzungen: ` ? ` → `→` (`\u2192`); Umlaute und `—` (`\u2014`) gezielt wiederherstellen
3. Vor Rebuild erneut zählen/prüfen — erst dann Quarto rendern

## Verbindliche Regel: Vorlesungsnotizen von Anfang an vollständig erstellen

Geltungsbereich: Diese Regel gilt bei der Erstellung, Ergänzung und Änderung aller Vorlesungsfolien und ihrer Notizen im jeweiligen EIT-Modul. Modulname, Semester, Vorkenntnisse und Lernziele ergeben sich aus dem zentralen Kurskontext in `README.md`.

Zielgruppe: Bachelorstudierende der DHBW Stuttgart im Studiengang Elektro- und Informationstechnik. Setze nur ausdrücklich benannte Vorkenntnisse voraus. Führe neue Begriffe und anspruchsvolle Zusammenhänge verständlich ein.

Grundsatz: Erstelle Folieninhalt, Abbildungen und zugehörige Notizen gemeinsam. Eine Folie ist erst fertig, wenn ihre Notizen die Inhalte fachlich korrekt, nachvollziehbar und zusammenhängend erklären. Die Notizen einer Einheit bilden über die Foliengrenzen hinweg ein durchgehendes Skript bzw. Lehrbuchkapitel, das mit den zugehörigen Folien ohne zusätzliche mündliche Erläuterung verständlich und im Handout flüssig lesbar ist. Sichtbare Abbildungen, Formeln und Code dürfen dabei vorausgesetzt werden; ihre Kernaussagen, Zusammenhänge und nötigen Herleitungen müssen im Text erklärt sein.

### 1. Vollständige Erklärung für jede Folie

Schreibe zu jeder Folie passende Notizen. Reine Wiederholungen der Stichpunkte, kurze Schlagwortlisten, Platzhalter und Hinweise wie „hier näher erklären“ sind unzulässig. Vermittle den Bezug zum Lernziel der Einheit, die Motivation, die wesentlichen Aussagen, ihre Zusammenhänge und die praktische Bedeutung. Eine formelhafte Wiederholung des Lernziels auf jeder Folie ist nicht erforderlich. Beantworte insbesondere: Was bedeutet das? Warum ist es so? Unter welchen Voraussetzungen gilt es? Was folgt daraus?

Auch Titel-, Überblicks-, Übungs- und Abschlussfolien erhalten sinnvolle Notizen: Orientierung und Voraussetzungen, Aufgabenverständnis und Lösung oder eine begründete Zusammenfassung der wichtigsten Erkenntnisse.

### 2. Begriffe und Abkürzungen verständlich einführen

Erkläre neue fachliche Abkürzungen bei ihrer Einführung in den Notizen der betreffenden Folie: ausgeschriebene Bezeichnung, verständliche deutsche Bedeutung und Funktion im konkreten Zusammenhang. Definiere ebenso neue Fachbegriffe, englische Begriffe, Symbole und relevante Codebezeichner. Orientiere dich dabei an den dokumentierten Vorkenntnissen.

Bereits eingeführte Begriffe müssen auf späteren Folien nicht vollständig erneut definiert werden. Gib eine kurze lokale Erinnerung, wenn ein Begriff lange nicht verwendet wurde, seine Bedeutung vom Kontext abhängt oder sonst ein Missverständnis droht. Ein Glossar und präzise Verweise dürfen dabei helfen. Für ausdrücklich einzeln nutzbare Folien müssen die zum Verständnis notwendigen Erklärungen lokal vorhanden sein. Führe auch in den Notizen keine neuen Begriffe ohne Erklärung ein.

### 3. Zusammenhänge und Übergänge verständlich machen

Ordne jede fachliche Folie kurz in den bisherigen Gedankengang ein. Erläutere, welches Problem sie löst und welche offene Frage zur nächsten Folie führt. Übergänge müssen den inhaltlichen Zusammenhang erklären; „Als Nächstes betrachten wir …“ allein reicht nicht.

Schreibe natürliche, zusammenhängende deutsche Prosa mit einem fortlaufenden Erklärungsbogen: Begriffe einführen, Aussagen begründen, an Beispielen entwickeln und Ergebnisse für den nächsten Gedankenschritt nutzen. Halte die Notizen der jeweiligen Folie zugeordnet, führe längere Argumentationen aber über mehrere Folien hinweg verständlich weiter. Benenne bei Rückverweisen den Gegenstand und seine Bedeutung; vermeide unvermittelte Begriffssprünge und unnötige Wiederholungen derselben Einführung.

Nutze übersichtliche Absätze und bei Bedarf kurze Listen. Vermeide ein mechanisch wiederholtes Schema, isolierte Folienkommentare wie „Hier sehen Sie …“ ohne Erklärung und unnötige Füllsätze. Setze erforderliche Moderationshinweise kurz vom eigentlichen Lerntext ab, damit dieser auch wie ein Skript gelesen werden kann.

### 4. Beispiele, Formeln und Übungen vollständig ausarbeiten

Ergänze bei abstrakten oder schwierigen Inhalten ein geeignetes Beispiel, Gegenbeispiel oder eine Verständnisfrage mit begründeter Antwort. Verwende nach Möglichkeit ein durchgängiges Beispiel, dessen Größen und Annahmen konsistent bleiben.

Erkläre Formeln einschließlich aller Größen, Einheiten, Voraussetzungen und ihrer Bedeutung. Zeige bei Rechenbeispielen die Ausgangswerte, den Rechenweg, Zwischen- und Endergebnisse sowie deren Interpretation. Begründe verwendete Näherungen und Rundungen und führe die [ingenieurwissenschaftliche Rechenprüfung](../AGENTS.md#ingenieurwissenschaftliche-rechenprüfung) durch. Dokumentiere zu Übungen eine nachvollziehbare Musterlösung in den Notizen und erläutere typische Fehlannahmen.

### 5. Abbildungen und Code ausdrücklich erläutern

Erkläre vorhandene Abbildungen in den Notizen: Elemente, Pfeile, Leserichtung, Zustände, Achsen, Einheiten, Farben und die daraus abzuleitende Kernaussage. Ergänze eine fachlich aussagekräftige Abbildung, wenn eine räumliche Beziehung, ein Ablauf, ein Zustandswechsel oder ein Zeitverhalten dadurch deutlich verständlicher wird. Eine Sammlung von Textkästen genügt dafür nicht.

Erkläre Code mit Sprache beziehungsweise Befehlssatz, Zweck, Voraussetzungen, Ein- und Ausgaben, relevanten Variablen beziehungsweise Registern sowie dem Ablauf. Erläutere gegebenenfalls Initialisierung, Lebensdauer, Fehlerfälle und Nebenläufigkeit. Kennzeichne Auslassungen und Vereinfachungen so, dass Lehrcode nicht mit einer vollständigen Implementierung verwechselt wird.

### 6. Annahmen, Gültigkeitsgrenzen und Nachweise offenlegen

Trenne allgemeine Prinzipien von Aussagen über konkrete Hardware, Softwareversionen und vereinfachte Modelle. Benenne jeweils relevante Anfangszustände, Modellannahmen, Zählkonventionen und Grenzen. Unterscheide insbesondere Quellcodeverhalten, Befehlssatz, Mikroarchitektur und gemessenes Laufzeitverhalten.

Erfinde keine Repository-Beispiele, Dateipfade, APIs, Messwerte, Compilerergebnisse oder erfolgreich ausgeführten Versuche. Prüfe, welche Werkzeuge und Quellen tatsächlich verfügbar sind. Kennzeichne Beispiele ohne entsprechende Ausführung als Lehrcode, Pseudocode oder Modellrechnung. Behaupte eine Simulation, einen Hardwareversuch oder eine Validierung mit einer Toolchain bzw. einem Messgerät nur, wenn diese tatsächlich erfolgt ist; benenne dann die verwendeten Bedingungen und Werkzeuge.

Eigene Zahlenbeispiele sind erlaubt, müssen aber ausdrücklich als didaktische Annahmen gekennzeichnet, plausibel gewählt und rechnerisch geprüft werden. Installiere keine zusätzliche Toolchain und erweitere keine verpflichtenden Laboraufgaben allein zur Erfüllung dieser Regel. Ungeklärte Fachfragen müssen sichtbar eingegrenzt werden; verdecke sie nicht durch scheinbar sichere Formulierungen.

### 7. Ausführlichkeit am Erklärungsbedarf ausrichten

Als Orientierung gelten etwa 70–120 Wörter für einfache Orientierungsfolien, 150–250 Wörter für typische fachliche Folien und 250–400 Wörter für anspruchsvolle Rechen-, Code- oder Zustandsbeispiele. Dies sind keine Mindestmengen oder harten Grenzen. Vollständigkeit, Verständlichkeit und fachliche Präzision entscheiden über die Länge. Teile eine überladene Folie sinnvoll auf, statt ihre Notizen zu einem unübersichtlichen Textblock auszubauen.

### 8. Qualitätsprüfung vor dem Abschluss durchführen

Prüfe jede Folie einschließlich ihrer Notizen, bevor du die Vorlesung als fertig meldest:

- Aktiviert die erste inhaltliche Folie mit einer passenden Frage das Vorwissen, sind erwartbare Antworten und Auflösung in den Notizen ausgearbeitet und wird die Frage später nachvollziehbar beantwortet?
- Sind neue Themenblöcke durch Abschnittsfolien mit passenden Zwischenüberschriften erkennbar, und bleibt die Position im Lernweg sichtbar?
- Lassen sich die Notizen in ihrer Reihenfolge als durchgehendes Skript lesen, mit nachvollziehbaren Übergängen, begründeten Aussagen und passenden Rückverweisen?
- Sind neue Begriffe, Abkürzungen, Symbole und relevante Codebezeichner eingeführt und kontextabhängige Bedeutungen lokal geklärt? Sind ausdrücklich einzeln nutzbare Folien für sich verständlich?
- Sind Motivation, Bedeutung, Voraussetzungen und Folgerungen verständlich?
- Sind Beispiele, Rechnungen und Übungslösungen vollständig, dimensionskonsistent und plausibel?
- Werden Abbildungen und Code so erklärt, dass Studierende sie selbst nachvollziehen können?
- Sind Aussagen zwischen Folientext, Abbildungen, Code, Notizen und Zusammenfassung widerspruchsfrei?
- Sind Übergänge inhaltlich begründet und Annahmen sowie Nachweisgrenzen ausdrücklich benannt?
- Sind relevante Eingaben, Anfangszustände, Zahlendarstellungen und Zeit-/Ereigniskonventionen gemäß den [einschlägigen Fachregeln](../FACHREGELN.md) angegeben und die Darstellungen gegeneinander geprüft?
- Decken die Übungen die Lernziele der Einheit ab und passt der Umfang zum Zeitbudget?

Lies die Notizen im geprüften Umfang zusätzlich am Stück, nicht nur einzeln neben den jeweiligen Folien. Prüfe dabei den roten Faden, fehlende Erklärungen an Abschnittswechseln, Begriffssprünge und unnötige Wiederholungen.

Behebe erkannte Mängel unmittelbar. Prüfe auch das erzeugte Ausgabeformat, soweit die nötigen Werkzeuge verfügbar sind: Abschnittswechsel müssen im Vortrag und Handout erkennbar, Notizen enthalten und richtig zugeordnet sowie Abbildungen und Beschriftungen lesbar sein. Berichte anschließend knapp, welche Prüfungen tatsächlich erfolgt sind und welche Grenzen verbleiben. Eine erfolgreich erzeugte Datei allein ist kein Nachweis fachlicher oder didaktischer Qualität.

Abnahmekriterium: Die Vorlesung ist erst abgeschlossen, wenn jede Folie diese Anforderungen erfüllt. Qualitätslücken dürfen nicht als spätere Ergänzung der Notizen offengelassen werden.
