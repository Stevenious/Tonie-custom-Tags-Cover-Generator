<div align="center">

# 🏷️ TagGen Studio V2 – Phoenix

**Das professionelle, webbasierte Cover- und Etiketten-Studio für Tonies-Tags.**

[Features](#-features) • [Architektur](#-architektur) • [Hosting](#-hosting) • [Druckanleitung](#-druck--bastelanleitung) • [Danksagung](#-credits--danksagung) • [Lizenz](#-lizenz)

<br/>

[![Status](https://img.shields.io/badge/status-production%20ready-success?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)](LICENSE)
[![Tech](https://img.shields.io/badge/tech-HTML5%20%2F%20CSS3%20%2F%20VanillaJS-orange?style=flat-square)](https://github.com)
[![Flipper Zero](https://img.shields.io/badge/flipper-NFC%20Supported-ff8200?style=flat-square)](https://github.com)

</div>

---

## ⚡ Über das Projekt

**TagGen Studio V2 (Phoenix)** ist der ultimative, plattformunabhängige Nachfolger für alle Kreativ-Tonies und Maker. Entwickelt als pfeilschnelle Single-Page-Applikation verbindet es eine Figma/Canva-inspirierte Studio-Oberfläche mit einer robusten Live-Datenbank aus den offiziellen `tonies.json`-Quellen.

Egal ob runde Kapseln, Token oder genormte Avery-Zweckform-Etiketten: TagGen Studio V2 bringt Ordnung auf deine A4-Druckbögen – komplett im Browser und ohne Installation.

---

## 🚀 Features

### 🎨 Studio-Editor mit Multi-Path Typografie
* **Konzentrischer Kreistext ohne Überlappungen:** Dreifach getrennter SVG-Textpfad für die Serie oben (`#path-top`), die Tonie-ID/UID auf einem Innenbogen (`#path-uid`) und den Titel unten (`#path-bottom`).
* **Pro-Transformations-Steuerung:** Stufenloser Zoom (50 % bis 200 %) sowie präzise **X- und Y-Achsen-Verschiebung**, um Motive millimetergenau in der Münzkapsel zu zentrieren.
* **Dynamische Schriftgrößen-Skalierung:** Regler von 70 % bis 150 % mit prozentualer Live-Anzeige.
* **Drag & Drop Bildimport:** Eigene Grafiken oder Fotos per Drag & Drop direkt auf die Kapsel ziehen.

### 🐬 Flipper Zero Live-Integration
* **Automatischer Dump-Abgleich:** Fragt das Dump-Repository `nortakales/flipper-zero-tonies` (Branch `master`) live ab und priorisiert den deutschen Katalog (`German/`).
* **24-Stunden Smart-Cache:** Verhindert GitHub-API-Limits durch intelligentes Caching im `localStorage`.
* **Badge-Anzeige:** Tonies mit existierendem Dump werden mit einem dezenten Badge (`🐬 FZ Dump`) in der Bibliothekskachel und auf dem Cover markiert.
* **Schnellfilter:** Per Klick auf *„Nur mit FZ-Dump“* wird der Katalog auf sofort flashbare Tonies gefiltert.
* **Direkter `.nfc`-Export:** Generiert per Klick eine vollständige ICODE SLIX `.nfc`-Datei mit korrekt formatierter UID für den Flipper Zero.

### 🖨️ Print Studio V2
* **Genormte Bogenformate:**
  * **43 mm Münzkapsel (12er • 3×4):** Perfekt angepasst für klassische runde Münzkapseln.
  * **40 mm Avery Zweckform (24er • 4×6):** Genormt für Avery-Etikettenbogen (z. B. L3415 / 5080).
  * **40 mm Standard (12er • 3×4)**
  * **30 mm Avery Zweckform (48er • 6×8):** Für kompakte Etikettenbögen (z. B. 6223).
  * **Frei definierbar:** Beliebiger Durchmesser in mm frei wählbar.
* **Interaktives Layout:** 
  * Volle **Drag & Drop**-Unterstützung zum Tauschen von Stickerpositionen auf dem Bogen.
  * Pfeiltasten (`◀` und `▶`) zum sequentiellen Verschieben auf dem Bogen.
  * Duplizieren (`＋`), NFC-Export (`🏷️`) und Entfernen (`✕`) direkt am Sticker.
  * Export aller auf dem Bogen platzierten UIDs als Textliste.

---

## 🏛️ Architektur

```
taggen-studio/
├── index.html           # Standalone Single-Page Application (HTML5, SVG, Vanilla JS)
├── flipper_index.json   # Optionaler Offline-Fallback Index für Flipper Zero Dumps
├── README.md            # Dokumentation & Handbuch
└── LICENSE              # MIT Lizenz
```

* **Zero Build & Zero Dependencies:** Keine NPM-Pakete, kein Node.js, kein Webpack – läuft sofort in jedem Browser.
* **Offline-Resilient:** Falls kein Internetzugang besteht oder GitHub-Limits greifen, schaltet TagGen nahtlos auf den lokalen Fallback um.

---

## 🌐 Hosting

### Netlify (Empfohlen)
Den Projektordner einfach per Drag & Drop in das [Netlify Drop Dashboard](https://app.netlify.com/drop) ziehen. Die Web-App ist innerhalb von 5 Sekunden online.

### GitHub Pages
1. Navigiere in deinem Repository zu **Settings > Pages**.
2. Wähle unter **Branch** den Branch `main` oder `master` und den Ordner `/ (root)` aus.
3. Auf **Save** klicken – die Seite ist nach wenigen Augenblicken erreichbar.

---

## 🖨️ Druck- & Bastelanleitung

1. **Cover gestalten:** Gewünschten Tonie auswählen oder eigenes Bild einfügen, per Zoom und Achsen ausrichten und mit `+ Auf den Druckbogen` ablegen.
2. **Druckbogen vorbereiten:** Im **Print Studio** das Etikettenformat wählen und die Positionen ordnen.
3. **Druckereinstellungen:**
   * Klick auf `🖨️ Drucken`.
   * **Skalierung auf 100 % stellen** (Option *„An Seite anpassen“* zwingend deaktivieren!).
   * **Hintergrundgrafiken aktivieren.**
4. **Fertigstellen:** Auf Fotopapier (180–230 g/m²) oder Etikettenpapier drucken, mit einem 43-mm-Stanzer ausstanzen und in die Kapsel einsetzen.

---

## 🤝 Credits & Danksagung

Ein besonderer Dank geht an die Community und Maker, die dieses Projekt ermöglichen:

* **[RFIDFriend](https://github.com):** Für die hervorragende Arbeit, den Support und die Bereitstellung hochwertiger **Custom UID Tags (Magic Tags / SLIX)** für die Tonie-Community.
* **Toniebox Reverse Engineering Team:** Für die Bereitstellung und kontinuierliche Pflege der weltweiten `tonies-json`-Datenbank.
* **nortakales / flipper-zero-tonies:** Für die Kuration und Pflege der Community-NFC-Dumps.

---

## 📄 Lizenz

Dieses Projekt ist unter der [MIT License](LICENSE) lizenziert.
