# CLAUDE.md – Projektkontext für Claude Code

## Worum es geht
Interaktiver CV (persönliche Website) von **Luca Gfeller**, gehostet über **GitHub Pages**.
Basis ist das gekaufte **InBio HTML-Template** (Rainbow-Themes, ThemeForest, Regular License),
Variante **„Technician – Light“**. Reines statisches HTML/CSS/JS – kein Build-Schritt, kein Backend.

Kommunikation mit Luca auf **Deutsch** (Schweiz: „ss“ statt „ß“).
Die Website-Texte in der Sprache, die in `INHALTE.md` vorgegeben ist.

## Struktur
- `index.html` – die Website (einzige Seite, Tab-basiert)
- `assets/css/style.css` – kompiliertes Haupt-CSS. **Direkt hier ändern** oder besser eigene
  Anpassungen in `assets/css/custom.css` sammeln (anlegen und nach `style.css` einbinden).
  Das SCSS in `assets/scss/` ist nur Referenz; es gibt keinen Build-Prozess.
- `assets/js/main.js` – Template-JS (jQuery). Kontaktformular sendet per AJAX an Formspree.
- `assets/images/` – Platzhalterbilder (graue Flächen mit Massangaben). Lucas eigene Bilder
  liegen in `assets/images/eigene/`.
- `_vorlagen/` – alle anderen Demo-Varianten und Einzelelemente des Templates. Nur als
  Referenz zum Abschauen von Sektionen/Komponenten. Wird vor dem Go-live gelöscht.
- `INHALTE.md` – Lucas CV-Inhalte. **Das ist die Quelle für alle Texte.**

## Aufbau von index.html (Technician-Layout)
- **Header-Banner** (`.bg_image--9`, Bild per CSS: `assets/images/eigene/banner.jpg`, Bagger bei Sonnenaufgang, 350px hoch, `background-size: cover`)
- **Profilkarte**: Foto (190×190), Name, Berufsbezeichnung, Social-Icons,
  Infos (Email, Birthday, Phone, Location) – ca. Zeile 30–95
- **Tab-Navigation** (vertikal Desktop / unten fixiert auf Mobile):
  1. **About** (`#v-pills-Javascript`) – Foto 500×664, Über-mich-Text, Liste, Kennzahlen, Brand-Logos
  2. **Resume** (`#v-pills-Design`) – „Education Quality“, „Job Experience“, „Design Skill“
     und „Development“ (Progressbars)
  3. **Work** (`#v-pills-Wordpress`) – Portfolio-Karten (800×600) mit Modal
  4. **Blog** (`#v-pills-settings`) – Blog-Karten mit Modal
  5. **Contact** (`#v-pills-python`) – Kontaktinfos + Formular
- Die Tab-IDs sind historisch falsch benannt (z. B. „Javascript“ = About) – nicht verwirren lassen.
  Umbenennen ist ok, dann aber `id`, `href` und `aria-*` konsistent mitändern.
- Am Ende: Modals für Portfolio/Blog und das **Demo-Switcher-Modal** („DEMOS“-Leiste rechts).

## Aufgaben (To-do)
1. Texte aus `INHALTE.md` einsetzen (Profil, About, Resume, Skills, Kontakt).
2. Bilder aus `assets/images/eigene/` einbinden, ungenutzte Platzhalter entfernen.
3. Template-Ballast entfernen:
   - Demo-Switcher („DEMOS“-Leiste + zugehöriges Modal mit allen Demo-Links)
   - Blog-Tab inkl. Modals, falls nicht gebraucht
   - Brand-/Kundenlogos, „Our trusted clients“ u. ä.
   - Platzhalter-Sektionen, für die es in `INHALTE.md` keine Inhalte gibt
4. `<title>`, `<meta name="description">`, Favicon (`assets/images/favicon.ico`), `lang`-Attribut anpassen.
5. Kontaktformular: `action="https://formspree.io/f/DEINE-FORM-ID"` mit Lucas Formspree-ID ersetzen.
   Feldnamen: `contact-name`, `contact-phone`, `email` (als Reply-To), `subject`, `contact-message`.
6. `_vorlagen/` löschen, nicht benötigte Bilder/Assets entfernen (Repo schlank halten).

## Design-Entscheidungen
- Luca bewirbt sich als **Baumaschinenmechaniker** – Bildsprache und Texte darauf ausrichten.
- **Akzentfarbe: Orange `#d95f0e`** (statt Template-Pink `#ff014f`), passend zum Banner.
  Definiert in `assets/css/style.css` unter `:root` (`--color-primary`, `--color-subtitle: #c4530b`,
  `--gradient-red-hover: #d95f0e → #a8440a`). Neue Elemente immer mit diesen Variablen einfärben.
- Profilbild: `assets/images/eigene/profil.jpg` (400×400, grauer Kachelhintergrund).

## Regeln
- **Responsive erhalten**: Nach Änderungen immer Desktop (1440px) und Mobile (390px) prüfen.
  Bootstrap-5-Grid und bestehende Klassen nutzen statt eigener Layout-Hacks.
- **Kein PHP, kein Server-Code** – GitHub Pages kann nur statische Dateien.
- Keine Demo-Bilder aus der Live-Preview verwenden (nicht lizenziert).
- Template-Klassen und -Struktur möglichst beibehalten, damit Animationen/JS weiter funktionieren.
- Persönliche Daten (Telefon, Geburtsdatum, Adresse) nur veröffentlichen, wenn sie in
  `INHALTE.md` ausdrücklich freigegeben sind.
- Keine Inhalte erfinden: Fehlt etwas in `INHALTE.md`, bei Luca nachfragen.

## Lokal testen
```bash
python3 -m http.server 8000   # → http://localhost:8000
```
Oder in VS Code die Erweiterung „Live Server“ nutzen.

## Deployment
Repo `<username>.github.io` → Settings → Pages → Deploy from branch `main` / root.
`.nojekyll` ist vorhanden (verhindert Jekyll-Verarbeitung).
