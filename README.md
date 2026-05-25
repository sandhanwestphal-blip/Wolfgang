# Sandhan-Design Website Template

Professionelles Astro-Website-Template für Einzelpersonen und Kleinunternehmen.  
Warm, minimalistisch, sofort einsetzbar.

---

## Platzhalter ersetzen

Vor dem ersten Einsatz alle Platzhalter per **Suchen & Ersetzen** (Strg+H in VS Code) befüllen:

| Platzhalter | Bedeutung | Beispiel |
|---|---|---|
| `KUNDE_NAME` | Vollständiger Name | `Maria Müller` |
| `KUNDE_BERUF` | Berufsbezeichnung | `Heilpraktikerin` |
| `KUNDE_EMAIL` | E-Mail-Adresse | `maria@example.de` |
| `KUNDE_ORT` | Ort/Stadt | `Leipzig` |
| `KUNDE_URL` | Cloudflare Pages URL | `mariamueller01.pages.dev` |
| `KUNDE_TEL` | Telefonnummer | `+49 171 1234567` |
| `KUNDE_ADRESSE` | Straße + Hausnummer | `Musterstr. 1` |
| `KUNDE_PLZ` | Postleitzahl | `04109` |
| `KUNDE_THEMA` | Kernthema für About-Sektion | `Heilung und Transformation` |
| `CF_PROJECT` | Cloudflare Projektname | `mariamueller01` |
| `WEB3FORMS_KEY` | web3forms Access Key | `abc123...` |

---

## Projektstruktur

```
src/
├── layouts/
│   └── Layout.astro        # HTML-Gerüst, SEO-Meta-Tags, Fonts
├── pages/
│   ├── index.astro          # Startseite
│   ├── danke.astro          # Danke-Seite nach Formular
│   ├── impressum.astro      # Impressum
│   └── datenschutz.astro    # Datenschutzerklärung
└── components/
    ├── Nav.astro            # Navigation (Desktop + Mobile)
    ├── Hero.astro           # Hero-Sektion mit Foto
    ├── About.astro          # Über-mich mit Timeline
    ├── Leistungen.astro     # Leistungen/Methoden als Karten
    ├── Kontakt.astro        # Kontaktformular + Infos
    └── Footer.astro         # Footer mit Links
public/
├── favicon.svg              # Favicon (K = Kunde, anpassen!)
├── robots.txt
├── sitemap.xml
└── .nojekyll
```

---

## Deployment

### Einmalig einrichten

1. **GitHub-Repo erstellen** (aus diesem Template → "Use this template")
2. **Cloudflare Pages** → New Project → GitHub-Repo verbinden
   - Build command: `npm run build`
   - Build output: `dist`
   - Node.js version: `20`
3. **GitHub Secrets** im Repo hinterlegen:
   - `CLOUDFLARE_API_TOKEN` (Cloudflare → My Profile → API Tokens)
   - `CLOUDFLARE_ACCOUNT_ID` (Cloudflare → rechte Seite auf der Übersicht)
4. In `deploy.yml` den Projektnamen `CF_PROJECT` ersetzen
5. Alle Platzhalter befüllen → Pushen → Live!

### Danach: Nur pushen

```bash
git add .
git commit -m "update content"
git push
```
→ GitHub Actions baut und deployed automatisch.

---

## Farben anpassen

In `src/layouts/Layout.astro` → `<style is:global>` → `:root`:

```css
:root {
  --sand:       #f5efe6;   /* Hintergrundfarbe hell */
  --warm:       #e8ddd0;   /* Hintergrundfarbe warm */
  --terracotta: #c17f5a;   /* Akzentfarbe */
  --deep:       #1a1410;   /* Dunkelfarbe / Überschriften */
  --text:       #3d2f25;   /* Fließtext */
  --text-light: #7a6555;   /* Subtexte */
}
```

---

## Foto hinzufügen

1. Foto in `public/` ablegen, z.B. `public/KUNDE_FOTO.jpg`
2. In `Hero.astro` den Platzhalter-`<div>` durch `<img>` ersetzen:
   ```html
   <img src="/KUNDE_FOTO.jpg" alt="KUNDE_NAME" />
   ```
3. OG-Image für Social Media: Foto auch als `public/og-image.jpg` speichern

---

## web3forms einrichten (Kontaktformular)

1. Kostenlos registrieren auf [web3forms.com](https://web3forms.com)
2. Access Key kopieren
3. `WEB3FORMS_KEY` in `Kontakt.astro` ersetzen
4. Fertig — keine Server, keine Konfiguration

---

## Tech Stack

- **Framework**: [Astro](https://astro.build) 4.x (statisch, kein JS by default)
- **Fonts**: Cormorant Garamond + Jost (Google Fonts)
- **Kontaktformular**: [web3forms](https://web3forms.com) (kostenlos)
- **Hosting**: [Cloudflare Pages](https://pages.cloudflare.com) (kostenlos)
- **CI/CD**: GitHub Actions + Wrangler

---

*Erstellt von [Sandhan-Design](https://github.com/Sandhan-Design)*
