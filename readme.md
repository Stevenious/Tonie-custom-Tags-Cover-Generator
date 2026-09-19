🦅 TagGen Studio V2.6.6 LTS – Phoenix

Community Edition · Tonie Tag & NFC

TagGen Studio Phoenix ist ein browserbasierter Tonie Cover-, Tag- und NFC-Editor für die Community.
Die Anwendung läuft vollständig als einzelne index.html und kann direkt über GitHub Pages bereitgestellt werden.

V2.6.6 LTS – Phoenix
Stabilitäts- und Community-Fokus · Single-File WebApp · GitHub Pages Ready

⸻

✨ Was ist TagGen Studio?

TagGen Studio verbindet mehrere Werkzeuge rund um individuelle Tonie-Tags in einer einzigen WebApp:

* 🔎 Tonie-Datenbank durchsuchen
* 🖼️ Cover auswählen und bearbeiten
* ✏️ Serien-, Titel- und Audio-ID-Daten anpassen
* ⭐ Favoriten verwalten
* 🏷️ individuelle Cover für Tags erstellen
* 🖨️ Druckbögen für verschiedene Tag-/Cover-Formate erstellen
* 📡 NFC-Hardware über USB oder BLE ansprechen
* 💾 Projekte speichern und wieder laden
* 🔍 NFC-Dumps mit Datenbankeinträgen abgleichen
* 📱 Responsive Oberfläche für Desktop und mobile Geräte

Das Ziel von Phoenix ist eine möglichst einfache Oberfläche:

Daten suchen → Cover bearbeiten → Druckbogen erstellen → NFC vorbereiten

⸻

🚀 Live-Version

Die aktuelle Community-Version kann direkt über GitHub Pages betrieben werden.

TagGen Studio Phoenix

https://stevenious.github.io/Tonie-custom-Tags-Cover-Generator/

⸻

🧩 Kernfunktionen

🔎 Tonie-Datenbank

TagGen Studio verwendet die öffentlichen Tonie-Datenquellen:

* tonies.json
* toniesV2.json

Dabei werden V1- und V2-Daten getrennt verarbeitet.

Die V2-Datenbank wird unter anderem aus den verschachtelten:

article
 └── data[]
      ├── series
      ├── episode
      ├── image
      ├── language
      ├── track-desc[]
      └── ids[]

aufbereitet.

Dadurch können Informationen aus beiden Datenquellen für die Suche und den Editor zusammengeführt werden.

⸻

🖼️ Cover Editor

Der integrierte Editor ermöglicht die direkte Bearbeitung eines Covers.

Verfügbare Einstellungen:

* Serie
* Titel
* Audio-ID
* Bild
* Zoom
* horizontale Position
* vertikale Position
* Schriftgröße

Die Vorschau wird direkt im Browser aktualisiert.

⸻

⭐ Favoriten

Häufig verwendete Tonies können als Favoriten gespeichert werden.

Die Favoriten werden lokal im Browser gespeichert und stehen beim nächsten Besuch weiterhin zur Verfügung.

Es ist keine Benutzeranmeldung erforderlich.

⸻

🖨️ Print Studio

Mit dem Print Studio können mehrere Cover auf einem Druckbogen zusammengestellt werden.

Unterstützte Presets:

Format	Layout
43 mm	3 × 4
40 mm	4 × 6
40 mm	3 × 4
30 mm	6 × 8
Custom	frei definierbar

Die Druckpositionen sind in Millimetern definiert und für A4-Druckbögen ausgelegt.

Funktionen

* Cover auf Druckbogen platzieren
* Positionen per Drag & Drop tauschen
* einzelne Cover entfernen
* Druckbogen leeren
* Projekt exportieren
* Projekt wieder importieren
* Druckansicht direkt aus dem Browser

⸻

📡 NFC Studio

Phoenix besitzt ein integriertes NFC-Studio für kompatible Hardware.

USB

Die Kommunikation erfolgt über:

Web Serial API

Standard-Baudrate:

115200

BLE

Für Bluetooth Low Energy wird das Nordic-UART-Profil verwendet.

Service:

6e400001-b5a3-f393-e0a9-e50e24dcca9e

Characteristic:

6e400002-b5a3-f393-e0a9-e50e24dcca9e

Das Flash-Kommando wird als JSON übertragen.

Beispiel:

{
  "cmd": "write_magic_tag",
  "uid": "E00403XXXXXXXXXX"
}

Die tatsächliche NFC-Kompatibilität hängt von der verwendeten Hardware und deren Firmware ab.

⸻

🔍 NFC Dump Matching

Phoenix kann zusätzlich bekannte NFC-Dumps mit den Einträgen der Datenbank abgleichen.

Dabei werden drei Match-Stufen verwendet:

🟢 Exact

Die Audio-ID bzw. eine bekannte ID stimmt direkt mit einem Dump überein.

🔵 Strong

Serie und Titel stimmen mit einer Dump-Struktur überein.

🟡 Fuzzy

Der Titel lässt sich einem bekannten Dump-Dateinamen zuordnen.

Damit kann direkt in der Datenbank erkannt werden, ob für einen Eintrag ein passender Dump vorhanden ist.

⸻

💾 Lokaler Cache

Da die Tonie-Datenbanken relativ groß sind, verwendet Phoenix einen lokalen Browser-Cache.

Dadurch kann die Anwendung nach einem erfolgreichen ersten Laden die Datenbank auch bei späteren Ladeproblemen verwenden.

Phoenix behandelt dabei getrennt:

V1 Database Cache
V2 Database Cache
Dump Index Cache
Favorites

Ungültige oder beschädigte Cache-Daten werden erkannt und verworfen.

⸻

🛡️ LTS-Stabilität

V2.6.6 LTS legt besonderen Wert auf zuverlässiges Laden der Datenbank.

Unter anderem:

* längeres Netzwerk-Timeout
* HTTP-Caching
* Fehlerbehandlung beim JSON-Laden
* getrenntes V1/V2 Parsing
* V2 data[] Flattening
* Unterstützung für verschachtelte ids[]
* Cache-Fallback
* ungültige Cache-Daten werden entfernt
* Dump-Index blockiert nicht das Laden der Hauptdatenbank

Ein Fehler beim optionalen Dump-Abgleich soll dadurch nicht mehr den eigentlichen Tonie-Datenbankstart verhindern.

⸻

📱 Browser-Kompatibilität

TagGen Studio ist als moderne Browser-WebApp konzipiert.

Für die vollständige Funktionalität werden moderne Browser-APIs verwendet.

Empfohlen

* Google Chrome
* Microsoft Edge
* Chromium-basierte Browser
* aktuelle Safari-Versionen für unterstützte Web-Funktionen

Für NFC-Hardware können zusätzliche Browser- und Betriebssystemanforderungen gelten.

Insbesondere Web Serial und Web Bluetooth sind nicht in allen Browsern verfügbar.

⸻

🌐 GitHub Pages

TagGen Studio ist bewusst als Single-File-WebApp aufgebaut.

Die Grundstruktur kann daher sehr einfach gehalten werden:

Tonie-custom-Tags-Cover-Generator/
│
├── index.html
├── README.md
└── ...

Die Anwendung benötigt für die eigentliche Oberfläche keinen klassischen Backend-Server.

GitHub Pages kann die index.html direkt ausliefern.

⸻

🏗️ Technischer Aufbau

Phoenix verwendet eine modulare JavaScript-Struktur innerhalb der einzelnen HTML-Datei.

Wichtige Module:

App
 └── View Routing
Data
 ├── Tonie Database
 ├── V1 Parser
 ├── V2 Parser
 ├── Cache
 └── Dump Matching
Library
 └── Database / Favorites
Search
 └── Suche & Filter
Editor
 └── Cover Editor
PrintStudio
 └── Druckbogen
NfcStudio
 └── USB / BLE
Storage
 └── Projektdateien
UI
 └── Cards / Toasts / Status

Die Anwendung benötigt dadurch keinen Build-Prozess.

⸻

🎨 Phoenix Design

Phoenix verwendet ein bewusst reduziertes Interface.

Grundprinzip:

Nicht möglichst viele Funktionen anzeigen – sondern die benötigten Funktionen schnell erreichbar machen.

Das Design verwendet eine helle Oberfläche mit dem Phoenix-Rot als primäre Akzentfarbe.

Phoenix Red
#e11d48

Die Oberfläche ist für Desktop und kleinere Displays responsive aufgebaut.

⸻

📂 Projektdateien

Projekte können als JSON-Datei exportiert werden.

Beispiel:

TagGen_Phoenix_Project.json

Die Projektdatei enthält unter anderem:

* Druckformat
* Cover
* Positionen
* Zoom
* Textdaten
* Audio-ID
* weitere Editor-Einstellungen

Dadurch kann ein vorbereiteter Druckbogen später wieder geöffnet werden.

⸻

🔒 Datenschutz

TagGen Studio benötigt grundsätzlich:

* kein Benutzerkonto
* kein eigenes Backend
* keine Anmeldung
* keine persönliche Profildatenbank

Favoriten und lokale Projektdaten werden im Browser gespeichert.

Bei Verwendung von externen Datenquellen gelten zusätzlich deren jeweilige Nutzungs- und Datenschutzbedingungen.

⸻

📚 Datenquellen

Die Tonie-Datenbank basiert auf den öffentlich verfügbaren Daten des Community-Projekts:

toniebox-reverse-engineering / tonies-json

Die Anwendung lädt die Daten zur Laufzeit aus den veröffentlichten JSON-Dateien.

Die Datenbank ist daher nicht Bestandteil des TagGen-Quellcodes.

⸻

🤝 Community Edition

TagGen Studio Phoenix wurde mit Blick auf die Tonie Tag & NFC Community entwickelt.

Das Projekt soll praktische Werkzeuge für:

* individuelle Tags
* Covergestaltung
* NFC-Projekte
* Druckvorbereitung
* Datenbankrecherche

in einer gemeinsamen Oberfläche bündeln.

Beiträge, Fehlerberichte und Verbesserungsvorschläge sind willkommen.

⸻

🐛 Bug Reports

Bei einem Fehler bitte möglichst folgende Informationen angeben:

Browser:
Betriebssystem:
Gerät:
TagGen Version:
Fehlerbeschreibung:
Schritte zum Reproduzieren:
Browser-Konsole / Fehlermeldung:

Besonders hilfreich sind konkrete Fehlermeldungen aus der Browser-Konsole.

⸻

💡 Feature Requests

Neue Funktionen sollten möglichst zum bestehenden Phoenix-Konzept passen:

* einfach
* übersichtlich
* community-orientiert
* ohne unnötige Komplexität
* möglichst ohne Backend
* GitHub-Pages-kompatibel

⸻

⚠️ Hinweis

TagGen Studio ist ein Community-Projekt und steht in keiner offiziellen Verbindung zu Tonies GmbH.

Tonie® und entsprechende Marken gehören ihren jeweiligen Rechteinhabern.

Die Verwendung von Daten, Bildern, NFC-Technologien und Dumps muss jeweils im Rahmen der geltenden Rechte, Lizenzen und gesetzlichen Bestimmungen erfolgen.

⸻

📜 Lizenz

Die Lizenz des Projekts und seiner einzelnen Bestandteile richtet sich nach den im Repository angegebenen Lizenzbedingungen.

Für externe Datenquellen gelten deren jeweilige Lizenzen und Nutzungsbedingungen.

⸻

🦅 TagGen Studio Phoenix

V2.6.6 LTS

Search. Design. Print. Tag.

Made for the Tonie Tag & NFC Community.

⸻
