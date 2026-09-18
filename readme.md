# 🎨 TagGen Studio

**Der Next-Generation Cover-Generator für Custom NFC-Tags (Magic Tags).**

TagGen Studio ist eine rasante, browserbasierte Single-Page-Application (SPA), mit der du im Handumdrehen perfekte, runde Aufkleber für deine selbstgemachten NFC-Tags erstellen und ausdrucken kannst. Entwickelt für die Maker-Community, 100% offline-fähig (PWA) und ohne nervige Backend-Abhängigkeiten.

🔗 **[Hier geht's zur Live-Version (Live Demo)](#)** *(<-- Trage hier deinen Netlify oder GitHub Pages Link ein)*

![TagGen Studio Preview](https://placehold.co/800x400/C02741/FFFFFF?text=TagGen+Studio+Screenshot) *(<-- Ersetze dies später durch einen echten Screenshot deines Tools)*

---

## ✨ Features

*   **⚡️ Live-Datenbank:** Zieht sich die aktuellste Community-JSON (V2) automatisch aus dem GitHub-Repo und cacht sie ressourcenschonend im Browser.
*   **🎛️ Simpel- & Pro-Modus:**
    *   *Simpel:* Motiv suchen, klicken, auf den Bogen legen.
    *   *Pro:* Bildausschnitt verschieben (X/Y), stufenloser Zoom, Schriftgrößen-Anpassung und eigene UIDs eintragen.
*   **🔄 Gebogener SVG-Text:** Titel und Seriennamen schmiegen sich mathematisch perfekt an die runde Kante des Aufklebers an (inkl. cleverem Filter für redundante Folgentitel).
*   **📐 Intelligente Druck-Engine:** 
    *   **Freies Raster:** 25mm, 30mm, 40mm und 43mm (perfekt für Münzkapseln) mit optionalen Schnittmarken!
    *   **Avery Zweckform:** Exakt abgestimmte Margins für vorgestanzte DIN-A4 Bögen (z.B. L3415 für 40mm, oder 30mm Bögen).
*   **🖱️ Drag & Drop:** Ziehe fertig generierte Sticker frei auf dem virtuellen Druckbogen umher – ideal, um angefangene Klebebögen weiterzuverwenden.
*   **💾 Multi-Export:**
    *   Direkter, maßstabsgetreuer Browser-Druck.
    *   Hochauflösender **300dpi PNG-Export**.
    *   Vektorbasiertes **PDF**.
    *   **JSON-Export** für den Flipper Zero.
*   **📱 PWA Ready:** Installiere TagGen Studio als native App auf deinem Smartphone oder Desktop. Einmal geladen, funktioniert das Tool auch komplett offline!
*   **🌗 Ergonomisch:** Integrierter Light- und Dark-Mode.

---

## 🚀 Quick Start / Benutzung

Da TagGen Studio komplett im Client (deinem Browser) läuft, gibt es keinen komplizierten Installationsprozess.

### Option 1: Live nutzen
Klicke einfach auf den Link zur Live-Demo. Du kannst die Seite auf deinem Smartphone über das Browser-Menü auch "Zum Startbildschirm hinzufügen" (PWA-Installation).

### Option 2: Lokal hosten / Forken
1. Lade dir die `index.html` aus diesem Repository herunter.
2. Mache einen Doppelklick darauf. Die App öffnet sich in deinem Browser – fertig!
3. Alternativ: Forke das Repository und aktiviere **GitHub Pages** in den Repo-Einstellungen, um deine eigene Instanz zu hosten.

---

## 📖 Anleitung: So erstellst du einen Bogen

1. **Suchen & Finden:** Gib im Suchfeld einen Titel, eine Serie oder eine ID ein. Klicke auf die gewünschte Kachel.
2. **Cover Editor:** Passe den Text an. Aktiviere den blauen **PRO-Modus**, um das Hintergrundbild perfekt zu zentrieren, heranzuzoomen oder eine eigene NFC-ID auf den Rand zu drucken. Klicke auf *"+ Auf den Druckbogen legen"*.
3. **Druckbogen anpassen:** Wähle aus, ob du ein *Freies Raster* (für Schere/Stanzer, inkl. Schnittmarken) oder *Avery Zweckform* (vorgestanzt) nutzen möchtest.
4. **Exportieren:** Drucke den Bogen aus. **WICHTIG:** Achte beim Drucken darauf, dass die Skalierung in den Druckereinstellungen auf **100%** bzw. **"Tatsächliche Größe"** steht!

---

## 🛠️ Tech-Stack

*   **HTML5 / CSS3 / Vanilla JavaScript:** Keine schweren Frameworks wie React oder Vue. Eine einzige, pfeilschnelle Datei.
*   **html2pdf.js:** Für den sauberen PDF-Export.
*   **html2canvas:** Für den 300dpi PNG-Render.
*   **SVG Paths:** Für die verlustfreie Text-Krümmung.

---

## 🤝 Mitwirken (Contributing)

Feedback, Bug-Reports und Pull Requests sind jederzeit willkommen! 
Wenn du ein neues Druckformat hinzufügen möchtest, kannst du einfach die `formatConfigs` in der `index.html` um die passenden Millimeter-Angaben erweitern.

---

*Haftungsausschluss: Dieses Tool ist ein inoffizielles Community-Projekt und steht in keiner Verbindung zur Boxine GmbH.*