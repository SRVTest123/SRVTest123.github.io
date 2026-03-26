## 📢 News-Bereich verwalten (news.json)

Die Neuigkeiten auf der Startseite werden dynamisch aus der Datei `news.json` geladen. Um neue Beiträge zu erstellen oder die Reihenfolge zu ändern, bearbeite diese Datei.

### 🆕 Neuen Beitrag erstellen
1. Öffne die `news.json`.
2. Kopiere einen bestehenden Block (alles zwischen `{` und `}`).
3. Füge ihn an der gewünschten Stelle ein.
4. **Wichtig:** Achte darauf, dass alle Blöcke durch ein **Komma** getrennt sind. Nach dem letzten Block darf **kein** Komma stehen.

### ↕️ Reihenfolge ändern
Die Webseite zeigt die Nachrichten in der Reihenfolge an, in der sie in der Datei stehen (von oben nach unten). 
* Um eine Nachricht nach oben zu schieben, bewege den gesamten `{...}` Block in der Datei weiter nach oben.

### 🖼️ Bilder einbinden
Damit ein Bild korrekt angezeigt wird, müssen zwei Dinge stimmen:
1. **Speicherort:** Das Bild muss im selben Ordner wie die `index.html` liegen.
2. **Dateiname:** Der Name in der `news.json` muss **exakt** (inkl. Groß-/Kleinschreibung) mit der Datei übereinstimmen.
   * *Beispiel:* `"bild": "wassertemperatUr.jpg"` funktioniert NUR, wenn die Datei auch ein großes **U** im Namen hat.
   * Wenn kein Bild angezeigt werden soll, nutze: `"bild": ""`

### 🛠️ Syntax-Check (Beispiel)
So sollte der Inhalt der `news.json` aussehen:

```json
[
  {
    "id": 3,
    "titel": "Neuester Beitrag",
    "datum": "März 2026",
    "text": "Dieser Text erscheint ganz oben auf der Seite.",
    "bild": "foto.jpg"
  },
  {
    "id": 2,
    "titel": "Älterer Beitrag",
    "datum": "Februar 2026",
    "text": "Dieser Text steht unter dem neuesten Beitrag.",
    "bild": ""
  }
]
