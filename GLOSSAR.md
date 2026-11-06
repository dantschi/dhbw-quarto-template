# Kursglossar

Dieses Glossar hält die im konkreten Kurs verwendeten Begriffe und ihre Bedeutung
fest. Es ergänzt die [Terminologieregeln](AGENTS.md#präzise-terminologie).
Übernehmen Sie nur Einträge, die zum Kurskontext in [README.md](README.md) passen.
Die Beispiele unten sind Vorlagen zur Anpassung; sie legen weder ein
Realzeitsysteme-Modul noch die Verwendung einer bestimmten API im Kurs fest.

## Pflege im konkreten Kurs

- Dokumentieren Sie je Eintrag den bevorzugten Begriff, Bedeutung und Kontext,
  zulässige Synonyme bzw. englische Namen und gegebenenfalls die Zuordnung zu
  Pseudocode oder einer konkreten API mit Sprache und Version.
- Ergänzen Sie die Stelle der Einführung, etwa Einheit und Folientitel, sowie
  eine geprüfte fachliche Fundstelle. Erfinden Sie keine bereits erfolgte
  Einführung oder Quellenangabe. Für die Vorlagenbeispiele ist noch keine
  Kurseinheit festgelegt.
- Verwenden Sie die festgelegte Bezeichnung in Folien, Notizen, Aufgaben,
  Musterlösungen, Quizfragen und Codeerläuterungen. Erklären Sie benötigte
  abweichende Namen bei der Einführung und halten Sie ihre Zuordnung hier fest.
- Erhalten Sie tatsächliche API-Namen und unterscheiden Sie abweichende
  Bedeutungen. Ein Glossareintrag rechtfertigt keine pauschale Umbenennung von
  Code oder fachlich unterschiedlichen Konzepten.

## Vorlagenbeispiel: Mutex und Operationen

Das Beispiel unterscheidet ein Synchronisationsobjekt von den Operationen auf
diesem Objekt. Es verwendet abstrakten Pseudocode mit `acquire(m)` und
`release(m)`; das sind keine ausführbaren Bibliotheksaufrufe. Im Beispiel wartet
`acquire(m)` gegebenenfalls und kehrt erst nach erfolgreichem Erwerb zurück.
Zeitüberschreitungen, Fehler und nicht blockierende Varianten sind in diesem
vereinfachten Modell ausgeblendet.

| Bevorzugter Begriff | Bedeutung und Kontext | Zulässige englische Bezeichnung | Pseudocode |
|--------------------|----------------------|---------------------------------|------------|
| Mutex | Synchronisationsobjekt für gegenseitigen Ausschluss beim Zugriff auf einen geschützten Bereich. | mutex; mutual exclusion lock, sofern im Kontext eindeutig | `m` bezeichnet das Objekt. |
| Mutex erwerben | Exklusiven Zugriff anfordern; geschützte Zugriffe beginnen erst nach erfolgreichem Erwerb. | acquire a mutex | `acquire(m)` |
| Mutex freigeben | Den erworbenen exklusiven Zugriff beenden, sodass ein wartender Teilnehmer den Mutex erwerben kann. | release a mutex | `release(m)` |

Das Wort „Lock“ ist kontextabhängig: Es kann ein Objekt, einen Zustand oder als
Verb eine Operation bezeichnen. Verwenden Sie es nicht ohne Erklärung
abwechselnd für diese Bedeutungen. Ein Wechsel zwischen `acquire` und `lock`
im selben generischen Pseudocode benötigt eine begründete Zuordnung.

### Zuordnung zu konkreten APIs

Die Namen realer APIs bleiben erhalten. Die folgende Tabelle ordnet Operationen
zu; sie behauptet keine vollständige Gleichheit ihrer Semantik.

| API-Beispiel | Erwerb | Freigabe |
|--------------|--------|----------|
| Python 3.12, Objekt `lock` aus `threading.Lock()` | `lock.acquire()` | `lock.release()` |
| C++ seit C++11, Objekt `mutex` vom Typ `std::mutex` | `mutex.lock()` | `mutex.unlock()` |

Prüfen und erläutern Sie bei Übernahme in einen Kurs die für das Beispiel
relevanten API-Eigenschaften, insbesondere Besitzregeln, Rekursion,
Rückgabewerte und mögliche Fehler. Diese Eigenschaften folgen nicht allein aus
den ähnlichen Operationsnamen. Dokumentation zu den Vorlagenbeispielen:
[Python 3.12: Lock Objects](https://docs.python.org/3.12/library/threading.html#lock-objects)
und [C++: `std::mutex`](https://en.cppreference.com/w/cpp/thread/mutex).
