diff --git a//dev/null b/README.md
index 0000000000000000000000000000000000000000..4766273f50d5a82a6fab6debf4fbca9841b0412d 100644
--- a//dev/null
+++ b/README.md
@@ -0,0 +1,61 @@
+# Bonus Score-Board Web-App
+
+Diese kleine Web-Anwendung ersetzt das bisherige Excel-Makro. Sie ist komplett statisch und benötigt keinen Build-Prozess. Das bedeutet, dass du sie direkt aus dem Projektordner öffnen und bearbeiten kannst.
+
+## Voraussetzungen
+- Ein aktueller Browser (Chrome, Edge, Firefox oder Safari)
+- Optional: Ein Editor wie Visual Studio Code, um den Code komfortabel zu bearbeiten
+
+## App starten
+Es gibt zwei Möglichkeiten, die Seite zu öffnen:
+
+1. **Direkt im Browser:**
+   - Navigiere im Datei-Explorer zu dem Ordner, der `index.html` enthält.
+   - Doppelklicke auf `index.html` – der Browser öffnet die App sofort.
+
+2. **Mit einem lokalen Webserver (empfohlen zum Entwickeln):**
+   - Öffne den Ordner in Visual Studio Code.
+   - Installiere ggf. die Erweiterung **Live Server**.
+   - Klicke unten rechts auf „Go Live“ oder starte den Server per Rechtsklick auf `index.html` → „Open with Live Server“.
+   - Der Browser öffnet sich automatisch unter einer Adresse wie `http://127.0.0.1:5500/`.
+
+## Daten anpassen
+Die Demo-Daten befinden sich im `<script>`-Teil am Ende der Datei [`index.html`](index.html). Entscheidend für die Dropdowns sind zwei Strukturen:
+
+- `const MONTHS = [...]` – definiert die verfügbaren Monate inklusive Kurz- und Langform.
+- `const defaultData = { ... }` – enthält alle Mitarbeitenden, ihre Personalnummern und Monatsdaten.
+
+### Neue Personalnummer hinterlegen
+1. Öffne `index.html` in deinem Editor.
+2. Suche nach `const defaultData = {`.
+3. Füge unterhalb der bestehenden Einträge einen neuen Block ein:
+   ```js
+   "4711": {
+       name: "Max Beispiel",
+       role: "Filialleiter",
+       months: {
+           "Januar": sampleRows({ /* Kennzahlen hier eintragen */ }),
+           "Februar": sampleRows({ /* weitere Kennzahlen */ }),
+       },
+   },
+   ```
+   - Der Schlüssel (`"4711"`) ist die Personalnummer, die im Dropdown erscheint.
+   - Unter `months` legst du beliebige ausgeschriebene Monatsnamen an. Für jeden Monat wird automatisch ein Dropdown-Eintrag erzeugt, sobald der Mitarbeitende ausgewählt ist.
+
+### Monate in der Auswahl ändern
+1. Suche im selben Skriptblock nach `const MONTHS = [`.
+2. Ergänze oder entferne Einträge wie `{ short: "Jan", full: "Januar" }`.
+   - `short` wird in der Auswahl oben rechts angezeigt (entspricht dem bisherigen Kürzel in Zelle `K1`).
+   - `full` muss exakt dem Schlüssel unter `months` entsprechen (z. B. `"Januar"`).
+
+Sobald du die Datei speicherst und den Browser neu lädst, erscheinen die neuen Personalnummern und Monate in den Dropdowns. Falls du Daten aus dem Browser-Cache entfernen möchtest, klicke in der App auf „Zurücksetzen“, um wieder die Inhalte aus `defaultData` zu laden.
+
+## Gestaltung ändern
+- Die Styles findest du im `<style>`-Block im `<head>` der `index.html`.
+- Farben, Abstände und Layout lassen sich dort über CSS-Variablen (z. B. `--primary`) oder direkte Regeln anpassen.
+
+## Nützliche Tipps
+- Der Browser speichert die Eingaben automatisch in `localStorage`. Mit der Schaltfläche „Zurücksetzen“ kannst du den Stand wieder auf die Standardwerte setzen.
+- Um die PDF-Vorschau zu testen, nutze den „PDF Vorschau“-Button. Die Druckansicht orientiert sich am Layout unterhalb der Tabelle.
+
+Viel Erfolg beim Anpassen! Bei Fragen kannst du direkt im Code Kommentare hinterlassen oder zusätzliche Hinweise ergänzen.
