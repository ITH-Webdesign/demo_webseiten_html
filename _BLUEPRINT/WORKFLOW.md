# IT Happens — Blueprint: Kunden-Demo Workflow

> **Ziel**: Du findest ein Unternehmen mit veralteter Website, baust eine moderne Demo,
> stellst sie kostenlos online — und der Kunde erhält den Link. Überzeugt er sich,
> wird daraus ein Auftrag.

---

## Das Konzept in 30 Sekunden

```
Schlechte Website gefunden  →  Demo bauen (mit Copilot)  →  Auf Vercel deployen
       →  Link an Kunden schicken  →  Auftrag
```

Deine Demo-Seiten in diesem Workspace zeigen dem Kunden das Design-Repertoire.
Das neue Projekt ist dann **seine individuelle Webseite** — mit echten Inhalten, Logo, Adresse.

---

## Phase 1 — Zielkunden finden

### Wo suchen?
- **Google Maps** → Branche + Stadt → Bewertungen 3,0–4,0 Sterne (oft schlechte Online-Präsenz)
- **Google-Suche**: `"Branche" "Ort"` → erste Ergebnisseiten anschauen
- Lokale Branchenverzeichnisse (Das Örtliche, Gelbe Seiten)

### Kriterien für eine schlechte Website
- Kein responsives Layout (auf dem Handy unlesbar)
- Kein SSL/HTTPS (Browser zeigt "Nicht sicher")
- Design vor 2015 (Flash, starr, Comic Sans)
- Ladezeit > 3 Sekunden
- Keine klare Navigation / kein CTA
- Keine Öffnungszeiten oder Kontaktdaten sichtbar
- Favicon fehlt, keine Social-Media-Verlinkung

### Besonders geeignete Branchen
Restaurant / Café / Bar · Barbershop / Friseur · Handwerksbetrieb · Zahnarzt / Arzt ·
Autohaus / KFZ · Architekt / Innenarchitekt · Kosmetik / Spa · Hotel / Pension ·
Fitnessstudio · Anwaltskanzlei · Steuerberater

---

## Phase 2 — Recherche & Inhalte sammeln (15–20 Min.)

Besuche die bestehende Website + Google Maps und notiere im `KUNDENBRIEFING.md`:

| Was | Wo finden |
|-----|-----------|
| Name, Inhaber, Gründungsjahr | Website About/Impressum |
| Adresse, Telefon, E-Mail | Website Footer/Kontakt |
| Öffnungszeiten | Website, Google Maps |
| Leistungen + Preise | Website, Menü, Preisliste |
| USPs / Besonderheiten | About-Text, Bewertungen lesen |
| Fotos / Logo | Website (Rechtsklick → Speichern), Google Maps |
| Social-Media-Links | Website Footer, Google Maps |
| Domain des Kunden | URL-Leiste |

> **Tipp Bilder**: Wenn keine guten Bilder vorhanden sind, schreib im Briefing welche
> Stimmung/Motiv gebraucht wird — Copilot kann Platzhalter beschreiben, die du per
> Unsplash/Pexels (kostenlos) ergänzt.

---

## Phase 3 — Neues Projekt anlegen

### 3.1 GitHub-Repo erstellen
```
1. github.com → New Repository
2. Name: demo_[Unternehmensname]  (z.B. demo_friseur-mueller)
3. Public ✓  (Vercel braucht Lesezugriff)
4. README: ja
5. Create repository → Clone URL kopieren
```

### 3.2 Lokal einrichten
```powershell
# In deinen Webdesign-Ordner wechseln
cd "C:\Users\yanni\IT Happens GbR\..."

# Repo clonen
git clone https://github.com/ITH-Webdesign/demo_[name].git
cd demo_[name]

# Starter-Template reinkopieren
Copy-Item "..\Demo_Webseiten_Static\_BLUEPRINT\starter\index.html" ".\index.html"

# KUNDENBRIEFING anlegen (Vorlage kopieren + ausfüllen)
Copy-Item "..\Demo_Webseiten_Static\_BLUEPRINT\KUNDENBRIEFING_TEMPLATE.md" ".\KUNDENBRIEFING.md"

# Bilder-Ordner
mkdir bilder
```

### 3.3 Bilder einfügen
- `bilder/hero.jpg` — Hauptbild (mind. 1920px breit)
- `bilder/about.jpg` — Portrait / Innenraum
- `bilder/logo.png` — Logo mit transparentem Hintergrund (wenn vorhanden)
- Weitere: nach Bedarf

---

## Phase 4 — Mit Copilot bauen

### Einstiegs-Prompt (in VS Code Chat, `@workspace`):
```
Lies KUNDENBRIEFING.md und baue die index.html basierend auf dem Starter-Template.
Passe alle Platzhalter an, setze echte Inhalte ein, wähle die passende Farbpalette
aus dem Design-Abschnitt des Briefings und füge alle angegebenen Sektionen hinzu.
```

### Folge-Prompts für spezifische Verbesserungen:
```
Mach die Hero-Animation beeindruckender mit einem Curtain-Wipe-Effekt.
```
```
Füge eine Galerie-Sektion mit [X] Bildern aus dem bilder/-Ordner hinzu.
```
```
Erstelle eine zweite Seite speisekarte.html / leistungen.html mit [Inhalt].
```
```
Optimiere die mobile Ansicht — prüfe 375px Breite.
```

### Bewährte Muster (bereits in Demos umgesetzt):
- **Curtain Intro**: `sessionStorage` + `navigation.type` → nur bei Reload/Erstbesuch
- **Card-Flip**: `.dish__inner` mit `rotateY(180deg)` auf Hover/Touch
- **Scroll Reveals**: `.anim-up` + GSAP ScrollTrigger
- **Nav scroll-hide**: hide on scroll down, show on scroll up
- **Ghost-Button auf dunklem BG**: `.btn--ghost-light`

---

## Phase 5 — Vercel Deploy

### Einmalig: Vercel mit GitHub verbinden
1. [vercel.com](https://vercel.com) → Login mit GitHub
2. "New Project" → "Import Git Repository"
3. Repo `demo_[name]` auswählen
4. Framework Preset: **"Other"** (statisches HTML)
5. Build Command: leer lassen
6. Output Directory: leer lassen (oder `.`)
7. → **Deploy**

### Ergebnis
URL: `https://demo-[name].vercel.app`

Jeder Push auf `main` → Vercel deployed automatisch neu (kein manuelles Upload).

### Optional: Custom Domain für den Kunden
- In Vercel → Domains → `demo.[kundendomain].de` hinzufügen
- CNAME-Eintrag beim Hoster des Kunden setzen

---

## Phase 6 — Präsentation beim Kunden

### Nachricht an den Kunden (Vorlage):
```
Guten Tag [Name],

ich habe Ihnen eine moderne Neugestaltung Ihrer Website als kostenlosen Vorschlag gebaut:
👉 https://demo-[name].vercel.app

Kein Auftrag, kein Risiko — einfach anschauen und melden wenn Sie Interesse haben.

Mit freundlichen Grüßen
Yannick — IT Happens GbR
```

### Übergabe wenn Auftrag zustande kommt:
1. Finales Repo auf IONOS Hosting deployen (oder Vercel beibehalten)
2. Domain des Kunden auf Vercel/IONOS zeigen lassen
3. CMS anbinden (optional): Netlify CMS, Tina CMS (beides kostenlos für statische Sites)

---

## Technischer Stack (Kurzreferenz)

| Was | Wie |
|-----|-----|
| Animationen | GSAP 3.12.5 via cdnjs CDN |
| Scroll-Trigger | `gsap.registerPlugin(ScrollTrigger)` |
| Smooth Scroll | CSS `scroll-behavior: smooth` |
| Fonts | Google Fonts via CDN (`preconnect`) |
| Hosting Demos | Vercel (kostenlos, auto-deploy von GitHub) |
| Hosting Produktion | IONOS Shared Hosting (Linux = case-sensitive Pfade!) |
| Bilder Quellen | Pexels, Unsplash (kostenlos + kommerziell nutzbar) |
| Icons | Keine Emoji-Icons! → [Heroicons](https://heroicons.com) (SVG) |

---

## Design-Entscheidungen nach Branche

### Restaurant / Gastro / Flammerie
```
primary:  #1F1209  (Dunkelbraun)
accent:   #C2410C  (Ember Orange)
gold:     #B8862F  (Warmes Gold)
cream:    #F4E8D3  (Warmes Weiß)
fonts:    Fraunces (Serif) + Inter Tight (Sans)
style:    Warm Minimalism, Cinematic
```

### Barbershop / Friseur
```
primary:  #0D0D0D  (Fast Schwarz)
accent:   #D4A017  (Gold)
cream:    #F5F0E8  (Warm White)
fonts:    Playfair Display + Inter Tight
style:    Dark Premium, Editorial
```

### Handwerksbetrieb / KFZ
```
primary:  #1A2332  (Dark Navy)
accent:   #E07B39  (Orange)
cream:    #F5F2EE  (Off White)
fonts:    Space Grotesk + Inter
style:    Technical, Bold, Trust
```

### Zahnarzt / Arzt (Light Mode)
```
primary:  #FFFFFF  (Weiß)
accent:   #2563EB  (Vertrauens-Blau)
text:     #111827  (Fast Schwarz)
muted:    #6B7280  (Grau)
fonts:    DM Serif Display + DM Sans
style:    Clean, Professional, Soft UI
```

### Architekt / Innenarchitekt
```
primary:  #FAFAFA  (Off White — Light Mode)
accent:   #1A1A1A  (Schwarz)
gold:     #8B7355  (Warmgrau-Beige)
fonts:    Cormorant Garamond + Inter Tight
style:    Brutalism Light, Editorial, Refined
```

### Kosmetik / Spa / Beauty
```
primary:  #FAF7F4  (Warm White — Light Mode)
accent:   #C9956C  (Rose Gold)
text:     #2C1810  (Dark Brown)
fonts:    Cormorant Garamond + Montserrat
style:    Soft UI, Organic Fluidity
```

---

## Checkliste vor dem Kundensend

- [ ] Alle Platzhalter ersetzt (kein "BUSINESSNAME" o.ä. im HTML)
- [ ] Telefonnummer korrekt und klickbar (`tel:+49...`)
- [ ] E-Mail korrekt (`mailto:...`)
- [ ] Öffnungszeiten stimmen
- [ ] Bilder laden korrekt (Pfade case-sensitive prüfen!)
- [ ] Mobil getestet (Chrome DevTools → 375px)
- [ ] Kein leerer Bildschirm beim Laden
- [ ] GSAP-Debug-Marker entfernt (`markers: true` entfernen)
- [ ] Meta-Title und Description ausgefüllt
- [ ] Vercel-URL erreichbar
