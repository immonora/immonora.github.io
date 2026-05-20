# immonora Landing Page — CLAUDE.md

## Überblick

Statische GitHub-Pages-Website für **immonora** — eine SaaS-Plattform zur Immobilienverwaltung, die sich aktuell in der Entwicklung befindet. Ziel der Seite: Besucher informieren + zur Warteliste / Newsletter anmelden.

**Live-URL:** https://immonora.github.io  
**Repository:** https://github.com/immonora/immonora.github.io  
**Deployment:** GitHub Pages (Branch `main`, Root `/`)

---

## Dateistruktur

```
immonora-landing/
├── index.html    ← Gesamte Website (HTML + CSS + JS, alles in einer Datei)
└── CLAUDE.md     ← Diese Datei
```

Die gesamte Seite lebt in einer einzigen `index.html`. Kein Build-Prozess, kein Framework, kein npm — direkt über GitHub Pages ausgeliefert.

---

## Design-System

Das Design orientiert sich am internen immonora-Produkt (`/Users/alex/immonora`).

| Variable | Wert |
|---|---|
| Font | Geist (Google Fonts) |
| Accent | `oklch(0.62 0.17 264)` — Indigo/Violett |
| Hintergrund | `#080810` — fast schwarz |
| Surface | `#0f0f18` |
| Text | `#f0f0f8` |
| Text sekundär | `#9898b0` |
| Radius | 12px / 20px (lg) |

**Wichtig:** Kein Tailwind, keine externen CSS-Frameworks. Alle Styles sind inline im `<style>`-Block der `index.html`.

---

## Sections der Seite

1. **Nav** — Logo, Markenname, "In Entwicklung"-Badge
2. **Hero** — Headline, Subtext, E-Mail-Signup-Formular
3. **Features** — 6-Card-Grid: KI-Automatisierung, Kommunikation, App, Verwaltung, Finanzen, Dokumente
4. **How it works** — 3 Schritte: Objekte anlegen → Mieter einladen → KI übernimmt
5. **CTA** — Zweites Signup-Formular mit Card-Design
6. **Footer** — Logo, Copyright, Links (Kontakt, Datenschutz, Impressum)

---

## Newsletter / Signup

**Wichtig: Kontaktdaten werden aktuell NICHT gespeichert.** Das Formular zeigt nur eine lokale Toast-Bestätigung — kein Backend, keine Datenbank. E-Mails gehen verloren.

Für echte Leads muss ein E-Mail-Service integriert werden.

**Empfohlene Optionen:**
- **Mailchimp** — `handleSignup()` in `index.html` via fetch an Mailchimp-API anpassen
- **ConvertKit** — Embedded Form oder API
- **Resend + eigene API** — wenn später ein Backend entsteht

Die Funktion `handleSignup(event, source)` in `index.html` ist der Integrationspunkt. Dort fetch-Aufruf ergänzen.

---

## Deployment (GitHub Pages)

```bash
# Einmalig: Remote hinzufügen
git remote add origin https://github.com/immonora/immonora.github.io.git

# Pushen
git push -u origin main
```

GitHub Pages ist für `immonora/immonora.github.io` automatisch aktiv (org.github.io-Repositories werden automatisch veröffentlicht). Kein separates Aktivieren nötig.

---

## Häufige Änderungen

### Headline anpassen
In `index.html` das `<h1>`-Tag suchen und Text anpassen.

### Feature-Karte hinzufügen
Im `.features-grid`-Div eine neue `.feature-card` mit `.feature-icon`, `.feature-title` und `.feature-desc` einfügen.

### Newsletter-Service integrieren
In der Funktion `handleSignup()` den Kommentarbereich durch einen `fetch()`-Aufruf zum jeweiligen Service ersetzen.

### Datenschutz- / Impressums-Seiten
Neue HTML-Dateien im Root anlegen (`datenschutz.html`, `impressum.html`) und die Links im Footer anpassen.

### Farben ändern
CSS-Variablen im `:root`-Block oben im `<style>`-Tag anpassen — insbesondere `--accent` für die Hauptfarbe.

### Markenname "immonora" hervorheben
Die CSS-Klasse `.brand` erzeugt einen modernen Gradient-Texteffekt (Indigo → Blau-Violett, fett) für den Markennamen im Fließtext. Verwendung: `<strong class="brand">immonora</strong>`. Bereits eingesetzt in: Hero-Sub, Features-Sub, Feature-Card (Web & Mobile), How-Sub, Step-Desc (Schritt 2), CTA-Sub.
