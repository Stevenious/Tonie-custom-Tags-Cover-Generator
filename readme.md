```
  _____           _____            _____ _             _ _        __      _____  
 |_   _|_ _  __ _/ ____|          / ____| |           | (_)       \ \    / /__ \ 
   | | / _` |/ _` | |  __  ___ _ _| (___ | |_ _   _  __| |_  ___   \ \  / /   ) |
   | || (_| | (_| | | |_ |/ _ \ '_ \\___ \| __| | | |/ _` | |/ _ \   \ \/ /   / / 
  _| |_\__,_|\__, | |__| |  __/ | | |___) | |_| |_| | (_| | | (_) |   \  /   / /_ 
 |_____|     |___/ \_____|\___|_| |_|_____/ \__|\__,_|\__,_|_|\___/     \/   |____|
                                  [ P H O E N I X ]
```

# 🏷️ TagGen Studio V2 – Phoenix

**High-Performance Client-Side Vector Label Designer, Print Layout Matrix & Web-Hardware NFC Flasher for Tonie Replacement Tags**[cite: 10, 14]





[]()
[](LICENSE)

[Live Demo](#-live-demo--deployment) • [Key Features](#-key-features) • [Hardware & Protocol](#-hardware-stack--architektur) • [Dos & Don'ts](#-community--maker-dos-and-donts) • [Print Setup](#-druckmatrix--masse) • [Credits](#-credits--ecosystem)



---

## ⚡ TL;DR

**TagGen Studio V2 (Phoenix)** ist eine kompromisslose, vollständig clientseitige Single-Page-Applikation (SPA) für das Toniebox-Maker-Ökosystem[cite: 10, 14]. Die Suite vereint:
1. **Multi-Path SVG Typography:** Perfekt zentrierter Kreissatz ohne Textkollisionen für Serien, UIDs und Titel[cite: 10, 14].
2. **Dynamic Print Matrix:** Skalierbare A4-Druckbögen (Münzkapseln, Avery Zweckform) mit nativem Drag & Drop[cite: 10, 14].
3. **Flipper Zero Cache Layer:** Live-Sync mit dem `flipper-zero-tonies`-Dump-Archiv via GitHub API v3[cite: 10, 14].
4. **Dump Studio (Web-to-Hardware):** Direktes Beschreiben von ICODE SLIX Magic Tags (Block 0) aus dem Browser heraus über **ESP32 + NXP PN5180** – via Web Serial (USB) oder Web Bluetooth (BLE)[cite: 14].

---

## 🚀 Key Features

### 🎨 1. Curved Vector Engine (Editor)
* **Separater 3-Pfad-Kreissatz:**
  * `#path-top`: Serienname am oberen Rand[cite: 14].
  * `#path-uid`: Konzentrisch geführter Innenbogen oberhalb des Titels – verhindert Überlappen bei 16-stelligen Hex-IDs[cite: 14].
  * `#path-bottom`: Folgentitel am unteren Kreisbogen[cite: 14].
* **Matrix-Transformation:** 2D-Achsenjustierung ($X/Y \pm 40\%$) und Zoom (50 % bis 200 %) für passgenaue Ausrichtung von Cover-Artworks[cite: 14].
* **Schriftgrößen-Normalisierung:** Responsive SVG-Skalierung (70 % bis 150 %) via Dynamic DOM Attributes[cite: 14].

### 📚 2. Tonie-Cloud Library & Dump-Detection
* **Multi-Source Fetcher:** Asynchrone Anbindung an die weltweite `tonies-json`-Community-Datenbank[cite: 10, 14].
* **Dump Auto-Matching:** Heuristischer Abgleich der Audio-ID und normalisierter Titel gegen das `nortakales/flipper-zero-tonies`-Archiv (Priorisierung des `German/`-Zweigs)[cite: 10, 14].
* **Non-Blocking Smart Cache:** 24h LocalStorage-Caching inklusive `AbortController`-Timeout (6s), um API-Rate-Limits zu umgehen[cite: 14].

### 🖨️ 3. Print Studio V2
* **Natives HTML5 Drag & Drop:** Tauschen und Reorganisieren von Stickerpositionen direkt auf dem Bogen[cite: 10, 14].
* **Präzisions-Presets:**
  * `43 mm (3×4)`: Standard für 43-mm-Münzkapseln[cite: 10, 14].
  * `40 mm (4×6)`: Avery Zweckform L3415 / 5080[cite: 10, 14].
  * `40 mm (3×4)`: 12er-Nutzen[cite: 10, 14].
  * `30 mm (6×8)`: Avery Zweckform 6223[cite: 10, 14].
  * `Custom`: Millimetergenaue Durchmesser-Definition[cite: 10, 14].

### 📲 4. Dump Studio (Web-to-NFC Bridge)
* **In-Browser Firmware Flasher:** Direkte Installation der RFIDfriend NFC-Archiver Firmware auf ESP32-WROOM-Boards via `` (ESP Web Tools 10)[cite: 14].
* **Dual-Stack Connection:**
  * **USB (Web Serial API):** 115200 Baud Stream für macOS, Windows, Linux, Android[cite: 14].
  * **BLE (Web Bluetooth API):** Nordic UART Service (`6e400001-b5a3-f393-e0a9-e50e24dcca9e`) für drahtlose Workflows[cite: 14].

---

## 🛠️ Hardware-Stack & Architektur

```
┌─────────────────────────────────────────────────────────────┐
│                    Browser (Client-Side)                    │
│   TagGen Studio V2 (HTML5 / SVG / CSS3 / Vanilla ES6+)      │
└──────────────┬───────────────────────────────┬──────────────┘
               │ Web Serial (USB)              │ Web Bluetooth (BLE)
               │ (115200 Baud)                 │ (Nordic UART Service)
               ▼                               ▼
┌─────────────────────────────────────────────────────────────┐
│                     ESP32-WROOM Board                       │
│             Firmware: RFIDfriend NFC-Archiver               │
└──────────────────────────────┬──────────────────────────────┘
                               │ SPI Interface
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                      NXP PN5180 RFID                        │
│                High-Power ISO/IEC 15693 RF                  │
└──────────────────────────────┬──────────────────────────────┘
                               │ 13.56 MHz RF Field
                               ▼
               ┌───────────────────────────────┐
               │    Magic Tag (ICODE SLIX-L)   │
               │   Custom Block 0 UID Flashed  │
               └───────────────────────────────┘
```


🔌 Pinout: ESP32 DevKit v1 ↔ NXP PN5180 (Klick zum Ausklappen)

| PN5180 Pin | ESP32 GPIO | Beschreibung |
| :--- | :--- | :--- |
| **3.3V** | 3V3 | Spannungsversorgung |
| **GND** | GND | Masse |
| **MISO** | GPIO 19 | SPI Master In Slave Out |
| **MOSI** | GPIO 23 | SPI Master Out Slave In |
| **SCK** | GPIO 18 | SPI Serial Clock |
| **NSS** | GPIO 5 | SPI Chip Select |
| **BUSY** | GPIO 16 | Handshake Busy Signal |
| **RST** | GPIO 17 | Hardware Reset |



---

## 📋 Community & Maker Dos and Don'ts

### 🎯 Drucken & Konfektionierung

> [!IMPORTANT]
> **DO:** Schalte im Druckdialog deines Browsers die Skalierung zwingend auf **Exakt 100 %** und deaktiviere Optionen wie *„An Seite anpassen“* oder *„Seitenränder ausgleichen“*. Aktiviere stets die Option **„Hintergrundgrafiken drucken“**[cite: 10, 14].

> [!WARNING]
> **DON'T:** Normales 80g-Kopierpapier verwenden. Die Farben bluten aus und die Kapsel wirkt matt. Verwende mindestens **180–230 g/m² Fotopapier** (glänzend oder matt) oder hochwertige Glanz-Klebefolien[cite: 10, 14].

### 📡 Flashen & NFC Tags

> [!TIP]
> **DO (Hardware-Auswahl):** Nutze für die Toniebox ausschließlich **ICODE SLIX / SLIX-L kompatible Magic Tags** (ISO 15693) mit veränderbarer UID in Block 0. Standard Mifare Classic 1K (ISO 14443A) oder NTAG213/215 Tags werden von der Toniebox **nicht** erkannt.

> [!CAUTION]
> **DON'T (Mobile Apple iOS):** Versuche nicht, Magic Tags direkt über Safari auf dem iPhone zu beschreiben. Apple blockiert hardwarenahe ISO 15693-Schreibkommandos und Web Bluetooth in Safari. Nutze stattdessen auf dem iPhone den **Bluefy Browser** für Web Bluetooth oder steuere den ESP32 vom Desktop aus an[cite: 12, 14].

### 💻 GitHub & Repository-Pflege

* **DO:** Halte die Codebase frei von Node/NPM-Build-Schritten. Der Charme dieses Projekts liegt in der Zero-Dependency-Portabilität: Ein Download der `index.html` genügt, um lokal autark zu arbeiten[cite: 10, 14].
* **DON'T:** Große `.nfc`-Dumps direkt in dieses Front-End-Repository committen. Nutze die dynamische API-Verbindung zum `nortakales`-Archiv[cite: 10, 14].

---

## 🖨️ Druckmatrix & Maße

| Vorlage / Typ | Nutzen | Maße | Empfohlene Verwendung |
| :--- | :--- | :--- | :--- |
| **Münzkapsel Standard**[cite: 10, 14] | 12 (3 × 4)[cite: 10, 14] | Ø 43 mm[cite: 10, 14] | 43 mm Acryl-Münzkapseln (perfekte Passform) |
| **Avery Zweckform 24er**[cite: 10, 14] | 24 (4 × 6)[cite: 10, 14] | Ø 40 mm[cite: 10, 14] | Etikettenbogen L3415 / 5080[cite: 10, 14] |
| **Avery Zweckform 12er**[cite: 10, 14] | 12 (3 × 4)[cite: 10, 14] | Ø 40 mm[cite: 10, 14] | Kompakte Stickerbögen |
| **Avery Zweckform 48er**[cite: 10, 14] | 48 (6 × 8)[cite: 10, 14] | Ø 30 mm[cite: 10, 14] | Mini-Tags & Klebepunkte (6223)[cite: 10, 14] |
| **Custom Size**[cite: 10, 14] | 12 (3 × 4)[cite: 10, 14] | Variabel | Beliebige Token & Sondermaße[cite: 10, 14] |

---

## 🌐 Live-Demo & Deployment

### Lokaler Schnellstart (Instant Webserver)
```bash
# Repo klonen
git clone https://github.com/Stevenious/Tonie-custom-Tags-Cover-Generator.git
cd Tonie-custom-Tags-Cover-Generator

# Lokalen Server starten (verhindert CORS-Einschränkungen bei lokalen Fallbacks)
python -m http.server 8080
```
Anschließend im Browser öffnen: `http://localhost:8080`

### 1-Klick Deployment
* **Netlify Drop:** Ziehe das gesamte Projektverzeichnis per Drag & Drop auf app.netlify.com/drop.
* **GitHub Pages:** Einstellungen öffnen (`Settings > Pages`), Source auf Branch `main` / `master` setzen, speichern.

---

## 🤝 Credits & Ecosystem

* **RFIDfriend:** Hardware-Design, NFC-Archiver Firmware und Expertise für Custom-UID Magic Tags (SLIX / SLIX-L)[cite: 10, 14].
* **Toniebox Reverse Engineering Team:** Für die Bereitstellung und Kuration der weltweiten `tonies-json`-Stammdaten[cite: 10, 14].
* **nortakales / flipper-zero-tonies:** Für das umfassende Community-Archiv an kompatiblen Flipper Zero `.nfc`-Dumps[cite: 10, 14].
* **Espressif Systems & ESP Web Tools:** Für das offene Web-Serial-Flasher-Framework[cite: 14].

---

## 📄 Lizenz & Rechtlicher Hinweis

Veröffentlicht unter der [MIT License](LICENSE)[cite: 10]. 

*Disclaimer: TagGen Studio V2 ist ein unabhängiges Open-Source-Projekt von Maker für Maker. Alle Markennamen, Warenzeichen und Produktabbildungen (z. B. Toniebox®, Tonies®) sind Eigentum der jeweiligen Rechteinhaber und dienen hier ausschließlich der Identifikation und Kompatibilitätsbeschreibung.*


Möchtest du, dass ich dir direkt die passende `README.md`-Datei als Download generiere, oder sollen wir noch ein Code-Beispiel für den ESP32-UART-Empfangs-Sketch mit aufnehmen?



Soll ein Troubleshooting-Abschnitt ergänzt werden, falls der COM-Port des ESP32 unter Windows nicht erkannt wird (z. B. CH340 / CP2102 Treiber)?
