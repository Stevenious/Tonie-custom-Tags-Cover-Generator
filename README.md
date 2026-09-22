# TagGen Orbit 5 · Prerelease

**Deine Geschichten. Dein System.**

![TagGen Orbit](assets/orbit-logo.svg)

Ein Cover für einen Tag. Ein Arbeitsstapel für zwölf Geschichten. Orbit verbindet Tonie-Suche, Gestaltung, private NFC-Dateien und A4-Druck in einer einzigen `index.html` für GitHub Pages.

## Schnell starten

1. `index.html` in das GitHub-Pages-Verzeichnis legen; bestehende Datei vorher sichern.
2. Tonie suchen und anklicken. Figurenbilder werden bei gleicher Trefferqualität bevorzugt.
3. Cover anpassen und auf den Druckbogen legen – oder mit **＋ In Sammlung** sammeln.
4. Papierformat wählen und bei **100 % / tatsächliche Größe** drucken.

Die App benötigt keinen Build, Account oder Server. Beide Tonie-Kataloge werden weiterhin asynchron geladen; ein Browser-Cache und optionaler JSON-Import dienen als Ausweichmöglichkeiten. Online-Bilder sind ohne passende CORS-Freigabe sichtbar und druckbar, aber nicht immer als PNG exportierbar.

## Neu: Eine Sammlung für zwölf Custom Tags

Eine benannte Arbeitsliste hält Coverzustand und optionale NFC-Originaldatei zusammen. Die Sammlung wird im Browser gespeichert; **Sammlung sichern** erzeugt eine private `.orbit-collection`-Datei für Backups oder den Wechsel zwischen iPhone und Desktop. Mehrere Sammlungen können als getrennte Dateien verwaltet werden; im Browser ist jeweils eine aktiv.

### Ich habe zwölf NFC-Dumps

**Sammlung → NFC-Dateien gemeinsam laden → Vorschläge prüfen → Stapel auf Druckbogen.**

- Mehrere Flipper `.nfc`- und Safari `.nfc.txt`-Dateien gemeinsam auswählen.
- Orbit prüft die Dateistruktur und sucht anhand des Dateinamens nach dem Titel.
- Nur ein eindeutiger Titelbezug wird automatisch bestätigt. Mehrdeutige Ergebnisse benötigen eine Auswahl im Studio.
- **Cover** öffnet den Editor; **Motiv wählen** öffnet die Bibliothek. **In Sammlung übernehmen** speichert das Ergebnis zurück.
- Sobald alle Einträge bestätigt sind, können bis zu zwölf Cover gemeinsam auf den Druckbogen gelegt werden.

Die Zuordnung über einen Dateinamen ist keine kryptografische Identifikation des Audioinhalts. Tag-UID und Audio-ID werden getrennt gespeichert.

### Ich starte mit den Covern

**Studio → suchen → Cover gestalten → ＋ In Sammlung.**

Alternativ fügt **Bibliotheksseite übernehmen** die aktuell sichtbaren vier bzw. acht Treffer hinzu. Wiederholte Seitenübernahme erzeugt keine doppelten Katalogeinträge. So lassen sich mehrere Suchen zu einem Stapel kombinieren.

Am Sammlungseintrag öffnet **NFC suchen** die bestehende Dump-Suche mit dem Titel. Eine Datei aus dem Repository auswählen oder eine eigene laden, danach **Geladenen Dump zuordnen**. Die Zuordnung wird ausdrücklich bestätigt. Ein fehlender Dump blockiert den Coverdruck nicht.

### Mein Druckbogen ist schon vorbereitet

**Sammlung → Druckbogen übernehmen** kopiert belegte Cover in freie Sammlungsplätze. Mehrfach vorhandene Cover bleiben einzelne Einträge. Ein Stapel ersetzt einen belegten Druckbogen erst nach Bestätigung; **Rückgängig** stellt den vorherigen Bogen wieder her.

## Dateiformate und Datenschutz

| Datei | Zweck |
| --- | --- |
| `.taggen` | Bestehendes Projektformat für Editor, Druckbogen, Papier und Kalibrierung; ggf. aktuell verknüpfte NFC-Datei |
| `.orbit-collection` | Private Sammlung mit bis zu zwölf Coverzuständen und deren Original-NFC-Dateien |
| Öffentliches Cover-Paket | Bestehender Export ohne Audio-IDs und NFC-Daten |
| `.nfc` | Unverändert gespeicherter Original-Dump aus der Werkstatt/Sammlung |
| `.png` | Gerastertes Einzelcover, sofern die Bildquelle den Export zulässt |

**Private Sammlungen können Passwörter und Speicherinhalte enthalten.** Sie sind kein öffentliches Community-Paket. Es erfolgt kein Upload der Sammlung an einen Orbit-Server. Falls der Browser-Speicher voll oder gesperrt ist, weist Orbit auf die Dateisicherung hin. Online-Bildverweise bleiben netzabhängig, wenn die Quelle keine Einbettung erlaubt.

## Formate

| Format | Raster / Plätze |
| --- | --- |
| Frei Ø25 mm | 7 × 10 / 70 |
| Frei Ø30 mm | 6 × 8 / 48 |
| Frei Ø40 mm | 3 × 4 / 12 oder 4 × 6 / 24 |
| Münzkapsel Ø43 mm | 3 × 4 / 12 |
| Avery Zweckform 6223-10, Ø30 mm | 6 × 8 / 48 |
| Avery Zweckform L3415-10, Ø40 mm | 4 × 6 / 24 |

Die beiden runden Avery-Geometrien und die Kalibrierung wurden aus der zuvor vom Nutzer am Drucker abgenommenen Version übernommen. A4-Vorschau und Druck-CSS bleiben getrennt. Die Druckausgabe enthält nur Cover, keine Menüleiste oder Sammlung.

**Quadratische Kapseln – aktualisierte Recherche:** Im [RevvoX-Thread „Square Custom Tags“](https://forum.revvox.de/t/square-custom-tags/1703) verwenden mehrere Nutzer QUADRUM-Kapseln. Genannt werden 43 × 43 mm (max. 43,5 mm) für den Papiereinleger; gedruckt wird auf Normalpapier, 24 Cover pro A4-Blatt, anschließend ausgeschnitten. Das [Hersteller-Außenmaß](https://www.leuchtturm.de/quadrum-muenzkapseln.html) beträgt 50 × 50 × 6,25 mm und ist nicht das Covermaß. Das ist ein konkreter Bedarf für ein freies Quadratformat; eine Häufigkeitsverteilung oder ein bevorzugtes quadratisches Avery-Produkt ist daraus nicht ableitbar. In diesem Build bleibt der Editor rund.

## Was die Community-Recherche nahelegt

Die folgenden Primärquellen beschreiben konkrete Wünsche, aber keine repräsentative Erhebung der gesamten Community:

- [TeddyCloud #157 – Labels und Gruppierung](https://github.com/toniebox-reverse-engineering/teddycloud/issues/157): unterschiedliche Tag-Arten sollen leichter unterscheidbar und gruppierbar werden. Orbit greift dies mit einer benannten privaten Arbeitsliste auf.
- [TeddyCloud #156 – Bild für Custom Tags](https://github.com/toniebox-reverse-engineering/teddycloud/issues/156): eigene Bilder sollen die Identifikation erleichtern. Orbit hält Bild und Titel beim Sammlungseintrag zusammen.
- [RFIDfriend NFC Archiver](https://github.com/RFIDfriend/NFC-Archiver): ESP32/PN5180, ISO15693, BLE-Protokoll und eigene App-/Hardwarepfade. Die Hardware bleibt ein optionaler Werkstattbereich.
- [Tonie-Kataloge](https://github.com/toniebox-reverse-engineering/tonies-json): Metadatenquelle für die vorhandene Suche.
- [Flipper-Tonie-Dateien](https://github.com/nortakales/flipper-zero-tonies): bestehende Suchquelle für NFC-Dumps; nicht jeder Katalogeintrag hat dort eine Datei.

Daraus folgt für Orbit: **weniger wiederholte Eingaben, sichtbare Zuordnungen, korrigierbare Vorschläge und ein wiederverwendbarer Druckstapel.** Eine tiefere TeddyCloud-Integration ist für diesen Nutzen nicht erforderlich.

## Brand

TagGen Orbit behält das bekannte Orbit-T-Zeichen. Das SVG ist als `assets/orbit-logo.svg` beigefügt; das App-Logo ist direkt in der HTML eingebettet, sodass `index.html` alleine deploybar bleibt.

- Rose `#DA2355`: Hauptaktion
- Tinte `#172033`: Text
- Blau `#2863DC`: Links
- Helles Glas, klare Flächen, Systemschrift
- Claim: **Deine Geschichten. Dein System.**

## Tests und Grenzen

Siehe [TEST_REPORT.md](TEST_REPORT.md). Die tatsächlichen JavaScript-Eventhandler und Zustandsänderungen wurden automatisiert mit DOM-/Netzwerk-Testdoubles und einem Canvas-Renderer geprüft. Das ist **keine neue Safari-/Desktop-Browser-Abnahme**: Ein echter Browserlauf war in dieser Umgebung wegen fehlender Browserdateien und fehlgeschlagenem Download nicht möglich. Die bisherigen Nutzerabnahmen betreffen die Ausgangsversion.

NFC-Schreiben, UID-Änderung, direkte TeddyCloud-Synchronisation, quadratische Cover und browserinterne Verwaltung beliebig vieler Sammlungen sind nicht Teil dieses Prereleases. Das bestehende BLE-Modul bleibt ein experimenteller lesender Adapter.

## Nächster Schritt zur V5-Freigabe

Eine Geräteabnahme mit dem fertigen Build: zwölf Einträge sammeln, einen Vorschlag ändern, Sammlung sichern/laden und einen Bogen drucken. Danach anhand realer Nutzung entscheiden, ob mehrere Sammlungen im Browser oder ein verifiziertes Quadratformat den größeren Nutzen bringen.


## Prerelease 2 · Rückmeldung aus der Geräteabnahme

- „Weiteres Motiv“ und „Bibliothek“ öffnen explizit die Bibliothek, auch wenn vorher der Editor aktiv war.
- Dump-Suche gleicht ä/ae, ö/oe, ü/ue und ß/ss an; Repository-Pfade bleiben unverändert.
- Mobil stehen Format und Druckaktion vor der Vorschau. Projekte, Kalibrierung und Hinweise sind unter der Vorschau gebündelt. Zwei Sprungbuttons machen Bogen und weitere Optionen direkt erreichbar.
- „Das versunkene Schiff“ ist im am 22.09.2026 geprüften Fuenf-Freunde-Ordner nicht enthalten. Die App ersetzt einen fehlenden Dump nicht durch eine andere Folge.
