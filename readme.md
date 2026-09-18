<div align="center">

  <h1>🏷️ TagGen Studio V2 – Phoenix</h1>
  <p><strong>Das professionelle, webbasierte Cover- und Etiketten-Studio für Tonies-Tags.</strong></p>

  <p>
    <a href="#features">Features</a> •
    <a href="#architektur">Architektur</a> •
    <a href="#installation--hosting">Hosting</a> •
    <a href="#lizenz">Lizenz</a>
  </p>

  <img src="https://img.shields.io/badge/status-production%20ready-brightgreen?style=flat-square" alt="Status">
  <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License">
  <img src="https://img.shields.io/badge/tech-HTML5%20%2F%20TailwindCSS%20%2F%20VanillaJS-orange?style=flat-square" alt="Tech">
</div>

---

## ⚡ Über das Projekt

**TagGen Studio V2 (Phoenix)** ist der ultimative, plattformunabhängige Nachfolger für alle Kreativ-Tonies und Maker. Entwickelt als pfeilschnelle Single-Page-Applikation verbindet es eine Figma/Canva-inspirierte Studio-Oberfläche mit einer robusten Live-Datenbank aus den offiziellen `tonies.json`-Quellen.

Egal ob runde Kapseln, Token oder genormte Avery-Zweckform-Etiketten: TagGen Studio V2 bringt Ordnung auf deine A4-Druckbögen – komplett im Browser und ohne Installation.

---

## 🎨 Key Features

*   **Intelligente Live-Datenbank:** Nahtlose Anbindung an die offizielle Tonies-Datenbank mit Echtzeit-Suche, Kategorie-Filtern und lokalem Favoritensystem (`★`).
*   **Figma-inspiriertes Studio & Focus-Mode:** Aufgeräumte 3-Spalten-Architektur, die bei der Motivwahl oder im Druckmodus automatisch in den Vollbildmodus umschaltet.
*   **Präziser Canvas-Editor:** 
    *   Stufenloser Zoom- und Positions-Regler (`X/Y`) für perfekte Bildausrichtung.
    *   **Drag & Drop:** Eigene Bilddateien können direkt per Drag & Drop auf den Editor gezogen werden.
    *   Optional ein-/ausblendbare Typografie für Serie, Titel und Audiocode (UID).
*   **Fehlerfreies SVG-Text-Rendering:** Mathematisch optimierte, aufrechte Textbögen auf der Unterseite – garantiert ohne ineinander gequetschte oder gespiegelte Buchstaben.
*   **Profi Print Studio:**
    *   Unterstützung für freie Raster (Schere/Stanzer) und Avery Zweckform Etiketten.
    *   **Direkte Sticker-Aktionen:** Hover-Buttons direkt auf dem Bogen zum sekundenschnellen Duplizieren (`+`) oder Löschen (`✕`).
    *   Batch-Fill-Funktion zum automatischen Füllen des gesamten A4-Bogens.
*   **Export & Print:** Hochauflösender PNG-Export (300 DPI) und direkter A4-PDF/Druckmodus mit millimetergenauer Skalierungshilfe.

---

## 🧩 Technische Architektur

Entgegen herkömmlicher, schwerfälliger Frameworks setzt TagGen Studio V2 auf eine extrem saubere **modulare Vanilla-JavaScript-Architektur**, gekapselt in klare Namespaces (`App`, `Library`, `Editor`, `PrintStudio`, `Export`). 

*   Kein schwerer Build-Step (Webpack/Vite) notwendig.
*   Läuft zu 100% statisch und offlinefähig.
*   Kann bei Bedarf in Sekundenschnelle in separate `.js`- und `.css`-Dateien aufgeteilt werden.

---

## 🚀 Installation & GitHub Pages Hosting

Da die Applikation vollständig statisch ist, lässt sie sich in weniger als einer Minute kostenlos über **GitHub Pages** hosten:

1. Erstelle ein neues Repository auf GitHub (z.B. `taggen-studio`).
2. Lade die finale `index.html` direkt in das Hauptverzeichnis des Repositories hoch.
3. Gehe in deinem Repository auf **Settings** ➔ **Pages**.
4. Wähle unter *Build and deployment* den Branch `main` (oder `master`) als Quelle aus und klicke auf **Save**.
5. Nach wenigen Sekunden ist deine Instanz unter `https://<dein-username>.github.io/taggen-studio/` live!

---

## 💡 Lokale Verwendung

Lade dir einfach die aktuelle `index.html` herunter und öffne sie per Doppelklick in einem beliebigen modernen Browser (Chrome, Firefox, Safari, Edge). Es ist kein Node.js-Server oder Webserver erforderlich!

---

## 📜 Lizenz

Veröffentlicht unter der [MIT License](LICENSE). 
Frei zur privaten Nutzung, Weiterentwicklung und Anpassung.