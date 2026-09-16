# Tonie Custom Tags Cover Generator 🎧

[![Netlify Status](https://api.netlify.com/api/v1/badges/heartfelt-lolly-d89eca/deploy-status)](https://heartfelt-lolly-d89eca.netlify.app)
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Format](https://img.shields.io/badge/Formate-43mm%20%7C%2040mm-rose)](#unterst%C3%BCtzte-formate)

Ein leichtgewichtiges, browserbasiertes Tool zum schnellen und millimetergenauen Erstellen von Druckbögen für **Tonie Custom Tags / RFID-Münzkapseln**. 

Wähle Cover aus dem offiziellen Tonie-Katalog, lade eigene Motive hoch, passe Zoom, Position und Drehung an und drucke einen passgenau skalierten A4-Bogen.

👉 **Live-App nutzen:** [https://heartfelt-lolly-d89eca.netlify.app](https://heartfelt-lolly-d89eca.netlify.app)

---

## ✨ Features

- 🔍 **Direkte Tonie-Datenbanksuche:** Zugriff auf über 6.500 Titel (Hörspiele, Musik, Wissen, Disney) via [tonies-json](https://github.com/toniebox-reverse-engineering/tonies-json).
- 🖼️ **Eigene Motive:** Bildupload für eigene Audio-Dateien oder seltene Tonies.
- 🎛️ **Live-Editor:** Stufenloser Zoom, Rotation, X/Y-Verschiebung, Hintergrundfarben und optionale Schnittlinien.
- 🔤 **Kreis-Textaufschrift:** Optionaler gebogener Text entlang des Kapselrandes.
- 📄 **A4-Druckbogen:** Automatische Anordnung der Cover im 1:1-Maßstab auf einer oder mehreren A4-Seiten.
- 💾 **Export-Optionen:** Direktes Drucken über den Browser oder High-Res PNG-Download (300 DPI).
- 📱 **PWA-fähig:** Kann auf dem Smartphone (iOS / Android) wie eine native App zum Home-Bildschirm hinzugefügt werden.

---

## 📐 Unterstützte Formate

| Format | Zweck | Raster (A4) | Details |
| :--- | :--- | :--- | :--- |
| **43 mm** | Münzkapseln | 4 × 5 (20 pro Seite) | Optimiert für gängige 43-mm-Münzkapseln für Custom NFC-Tags |
| **40 mm** | Klebeetiketten | 4 × 6 (24 pro Seite) | Passgenau für vorgestanzte Bögen **Avery Zweckform L3415** |

---

## 🖨️ Wichtige Druckeinstellungen

Damit die Maße millimetergenau auf deinen Kapseln oder Etiketten landen:

1. **Skalierung:** Im Druckdialog unbedingt auf **„100 %“** bzw. **„Tatsächliche Größe“** / **„Standard“** stellen (nicht „An Seite anpassen“!).
2. **Ränder:** Seitenränder auf **„Keine“** bzw. **„Minimum“** setzen.
3. **Hintergrundgrafiken:** Die Option *„Hintergrundgrafiken drucken“* muss aktiviert sein.

---

## 💻 Lokale Entwicklung

Das Projekt ist eine reine Single-Page-App ohne Build-Step:

1. Repository klonen:
   ```bash
   git clone https://github.com/Stevenious/Tonie-custam-Tags-Cover-Generator.git
   cd Tonie-custam-Tags-Cover-Generator
   ```
2. Datei `index.html` direkt im Browser öffnen oder mit einem lokalen Webserver starten:
   ```bash
   npx serve .
   ```

---

## ⚖️ Rechtlicher Hinweis & Disclaimer

* Dieses Projekt ist ein privates Fan-Werkzeug und steht in **keiner offiziellen Verbindung zur tonies GmbH**.
* Alle angezeigten Cover-Motive stammen aus der frei zugänglichen Tonies-Datenbank und sind Eigentum der jeweiligen Rechteinhaber (u. a. tonies GmbH und Lizenzgeber).
* Die Nutzung ist ausschließlich für **private, nicht-kommerzielle Zwecke** bestimmt. Der Weiterverkauf oder die kommerzielle Nutzung der erstellten Druckbogen ist nicht gestattet.
