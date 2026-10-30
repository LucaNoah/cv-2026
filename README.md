# Interaktiver CV – Luca Gfeller

Persönliche CV-Website auf Basis des **InBio HTML-Templates** (Rainbow-Themes, ThemeForest – Regular License).
Gehostet über **GitHub Pages**.

## Struktur

```
index.html          ← die eigentliche Website (Startseite)
assets/
  css/style.css     ← Haupt-Stylesheet (aus SCSS kompiliert)
  scss/             ← SCSS-Quelldateien (optional, für grössere Design-Anpassungen)
  js/main.js        ← Template-JavaScript (Kontaktformular → Formspree)
  images/           ← Bilder (Demo-Bilder durch eigene ersetzen!)
_vorlagen/          ← alle anderen Demo-Varianten & Elemente zum Abschauen
```

## Lokal ansehen

```bash
python3 -m http.server 8000
# → http://localhost:8000
```
Die Demos findest du unter `http://localhost:8000/_vorlagen/<datei>.html`.

## Kontaktformular einrichten (Formspree)

1. Kostenlos registrieren auf <https://formspree.io> und ein neues Formular erstellen.
2. Die Form-ID kopieren (z. B. `xyzabcd`).
3. In `index.html` `DEINE-FORM-ID` ersetzen:
   `action="https://formspree.io/f/xyzabcd"`

## Veröffentlichen auf GitHub Pages

1. Neues Repository **`<github-username>.github.io`** auf GitHub erstellen.
2. Code pushen:
   ```bash
   git remote add origin https://github.com/<github-username>/<github-username>.github.io.git
   git push -u origin main
   ```
3. Im Repository: **Settings → Pages → Source: „Deploy from a branch“ → `main` / `root`**.
4. Nach 1–2 Minuten ist die Seite unter `https://<github-username>.github.io` online.

## Vor dem Go-live

- [ ] Gewünschte Demo-Variante als `index.html` übernehmen
- [ ] Texte, CV-Daten, Links ersetzen
- [ ] Demo-Bilder durch eigene ersetzen (Demo-Bilder sind **nicht** lizenziert!)
- [ ] Nicht genutzte Sektionen entfernen
- [ ] `_vorlagen/` löschen
- [ ] Formspree-ID eintragen
- [ ] `<title>`, Favicon und Meta-Beschreibung anpassen
