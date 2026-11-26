# Familienfinanzen Gerber – Einrichtung

Die App besteht aus wenigen Dateien und braucht keinen eigenen Server. Die Daten liegen auf jedem Gerät und in einem gemeinsamen Ordner in Google Drive. Kosten: keine.

Einmaliger Aufwand: ca. 30–45 Minuten. Am einfachsten am PC.

---

## 1. App ins Internet stellen (GitHub Pages)

1. Auf https://github.com ein Gratis-Konto anlegen (falls noch keines vorhanden).
2. Oben rechts **+ → New repository**. Name: `finanzen`. **Private** wählen geht nur mit Bezahl-Abo; **Public** ist in Ordnung, denn das Repository enthält nur den Programmcode, keine Daten.
3. Im neuen Repository **Add file → Upload files**, alle Dateien aus diesem Ordner hineinziehen (index.html, config.js, sw.js, manifest.webmanifest, icon.svg, icon-192.png, icon-512.png). **Commit changes**.
4. **Settings → Pages**: Source «Deploy from a branch», Branch `main`, Ordner `/ (root)`, **Save**.
5. Nach 1–2 Minuten ist die App erreichbar unter `https://DEIN-NAME.github.io/finanzen/`. Diese Adresse notieren.

## 2. Google-Zugang einrichten (Google Cloud)

1. https://console.cloud.google.com öffnen, mit deinem Google-Konto anmelden.
2. Oben **Projekt auswählen → Neues Projekt**, Name `Familienfinanzen`, erstellen.
3. **APIs & Dienste → Bibliothek** → «Google Drive API» suchen → **Aktivieren**.
4. **APIs & Dienste → OAuth-Zustimmungsbildschirm** (bzw. «Google Auth Platform»):
   - Nutzertyp **Extern**, App-Name `Familienfinanzen Gerber`, deine E-Mail als Support- und Kontaktadresse.
   - Bereiche/Scopes: nichts weiter nötig.
   - **Testnutzer**: deine Gmail-Adresse **und Annikas** Gmail-Adresse hinzufügen.
   - Veröffentlichungsstatus bleibt **Testen**. Das ist für den privaten Gebrauch gedacht und reicht.
5. **APIs & Dienste → Anmeldedaten → Anmeldedaten erstellen → OAuth-Client-ID**:
   - Anwendungstyp **Webanwendung**.
   - **Autorisierte JavaScript-Quellen**: `https://DEIN-NAME.github.io` (ohne /finanzen und ohne Schrägstrich am Ende).
   - Erstellen. Die angezeigte **Client-ID** kopieren (endet auf `.apps.googleusercontent.com`).
6. In GitHub die Datei `config.js` öffnen → Stift-Symbol → Client-ID zwischen die Anführungszeichen eintragen → **Commit changes**.

## 3. Ersteinrichtung (Lukas)

1. App-Adresse öffnen → **Einstellungen → Neuen Ordner anlegen**.
2. Mit Google anmelden. Google zeigt «Google hat diese App nicht überprüft» – das ist bei privaten Apps normal: **Erweitert → Weiter zu Familienfinanzen Gerber**, Zugriff erlauben.
3. In Google Drive ist jetzt der Ordner **Familienfinanzen Gerber** mit `daten.json`, `Belege` und `Backups`.
4. Bisherige Daten übernehmen: In der bisherigen App (in Claude) unter Übersicht **Backup herunterladen**, dann hier **Einstellungen → Backup / Daten importieren**.
5. Den Ordner **Familienfinanzen Gerber** in Google Drive mit Annika teilen (Rechtsklick → Freigeben → Annikas Adresse, Rolle **Bearbeiter**).

## 4. Annika verbinden

1. Annika öffnet dieselbe App-Adresse → **Einstellungen → Geteilten Ordner verbinden** → mit ihrem Google-Konto anmelden (gleiche Warnung, gleich vorgehen).
2. Ab jetzt arbeiten beide mit denselben Daten. Wer gleichzeitig denselben Eintrag ändert: die spätere Änderung gilt.

## 5. Aufs Handy

- **Android (Chrome):** App-Adresse öffnen → Menü ⋮ → **Zum Startbildschirm hinzufügen / App installieren**.
- **iPhone (Safari):** App-Adresse öffnen → Teilen-Symbol → **Zum Home-Bildschirm**. Falls die Google-Anmeldung in der installierten App hängt, die App einmal in Safari öffnen und dort anmelden.

## Im Alltag

- **+ Beleg**: Foto aufnehmen, Betrag und Text eingeben, speichern. Das Foto landet in Drive unter `Belege/<Jahr>`.
- Ohne Internet wird lokal gespeichert und später synchronisiert.
- Oben steht der Status. «Antippen zum Synchronisieren» bedeutet: Google-Anmeldung ist abgelaufen (nach ca. 1 Stunde) – einmal antippen genügt.
- Jeden Tag mit Synchronisation entsteht automatisch eine Kopie in `Backups`.

## Gut zu wissen

- Die App hat Zugriff auf Google Drive. Sie liest und schreibt aber nur im Ordner «Familienfinanzen Gerber». Der Code ist offen einsehbar.
- Die Daten (`daten.json`) sind eine gewöhnliche Textdatei und lassen sich auch ohne die App öffnen.
- Neue Version der App: geänderte Dateien in GitHub hochladen, fertig.
