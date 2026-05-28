# Kundenbriefing

> **Hinweis für Copilot**: Lies diese Datei vollständig durch und baue/passe die `index.html`
> anhand dieser Angaben an. Nutze den Tech-Stack aus `_BLUEPRINT/starter/index.html`.
> Halte dich an die angegebenen Design-Entscheidungen. Ersetze ALLE Platzhalter durch echte Inhalte.

---

## Unternehmen

| Feld | Wert |
|------|------|
| **Name** | |
| **Branche** | <!-- z.B. Restaurant, Barbershop, Handwerk, Zahnarzt --> |
| **Inhaber / Ansprechpartner** | |
| **Gegründet / seit** | |
| **Aktuelle Website** | <!-- URL der bestehenden Seite --> |
| **Ziel-Domain** | <!-- z.B. www.muster-gmbh.de --> |

---

## Standort & Kontakt

```
Straße + Nr.:     
PLZ + Ort:        
Telefon:          +49 
E-Mail:           
WhatsApp:         (optional)
Google Maps Link: 
```

---

## Öffnungszeiten

| Tag | Uhrzeit |
|-----|---------|
| Montag | Geschlossen |
| Dienstag | 00:00 – 00:00 |
| Mittwoch | 00:00 – 00:00 |
| Donnerstag | 00:00 – 00:00 |
| Freitag | 00:00 – 00:00 |
| Samstag | 00:00 – 00:00 |
| Sonntag | Geschlossen |

> Besonderheiten / Hinweise zu Öffnungszeiten:

---

## Leistungen / Angebot

> Liste hier alle Leistungen, Gerichte, Produkte oder Dienstleistungen auf.
> Für Restaurants: Name, Beschreibung, Preis. Für Handwerk: Art der Arbeit.

```
1.  Name:           Preis:       Beschreibung:
2.  Name:           Preis:       Beschreibung:
3.  Name:           Preis:       Beschreibung:
4.  Name:           Preis:       Beschreibung:
5.  Name:           Preis:       Beschreibung:
6.  Name:           Preis:       Beschreibung:
```

---

## Über das Unternehmen (About/Story)

> Was macht dieses Unternehmen besonders? Geschichte, Werte, Team, Auszeichnungen.
> Gerne als Stichpunkte — Copilot formuliert daraus einen Text.

```
-
-
-
-
```

---

## USPs (Alleinstellungsmerkmale)

> Was hebt dieses Unternehmen von der Konkurrenz ab?

```
1.
2.
3.
```

---

## Zielgruppe & Tonalität

| Feld | Beschreibung |
|------|-------------|
| **Hauptzielgruppe** | <!-- z.B. Familien, Geschäftskunden, 30-60 Jährige --> |
| **Tonalität** | <!-- z.B. herzlich & familiär / professionell & seriös / modern & jung --> |
| **Sprache** | Deutsch |

---

## Design-Entscheidungen

### Stil
<!-- Wähle einen oder beschreibe frei:
     Warm Minimalism · Cinematic Editorial · Dark Premium · Technical Bold
     Soft UI · Glassmorphism · Brutalism · Clean Professional -->
**Stil:**

### Farbpalette
<!-- Entweder aus WORKFLOW.md Branchenpaletten wählen oder eigene Farben -->
```
--primary:    #        (Hintergrundfarbe)
--accent:     #        (Akzentfarbe: CTAs, Highlights)
--gold:       #        (Sekundärer Akzent: Preise, Details)
--cream:      #        (Heller Text / helle Flächen)
--ink:        #        (Dunkler Text auf hellen Flächen)
```

### Schriften
<!-- Empfehlungen in WORKFLOW.md → Design nach Branche
     Oder eigene Auswahl von fonts.google.com -->
```
--serif:  
--sans:   
```

### Logo / Branding
- Logo vorhanden: Ja / Nein
- Logo-Datei: `bilder/`
- Primärfarbe des Logos:

---

## Sektionen (Seitenaufbau)

> Markiere welche Sektionen gebaut werden sollen. Reihenfolge = Anordnung auf der Seite.

- [ ] Curtain Intro-Animation (mit Logo + Firmenname)
- [ ] Hero (Vollbild-Bild mit Überschrift + CTA)
- [ ] About / Über uns / Unsere Geschichte
- [ ] Leistungen / Speisekarte / Galerie
- [ ] Testimonials / Kundenmeinungen
- [ ] Gutscheine / Sonderangebote
- [ ] FAQ
- [ ] CTA-Band (Akzentfarbiger Aufruf zur Aktion)
- [ ] Öffnungszeiten & Kontakt
- [ ] Unterseiten: ____________

---

## Bilder

| Datei | Inhalt | Status |
|-------|--------|--------|
| `bilder/hero.jpg` | Hauptbild (mind. 1920px) | ☐ |
| `bilder/about.jpg` | Inhaber / Innenraum / Team | ☐ |
| `bilder/logo.png` | Logo transparent | ☐ |
| `bilder/` | | ☐ |
| `bilder/` | | ☐ |

> Bildquellen falls keine eigenen Bilder: [Pexels](https://pexels.com) · [Unsplash](https://unsplash.com)
> Suchbegriffe: ________________

---

## Social Media

```
Instagram:  
Facebook:   
TikTok:     
LinkedIn:   
```

---

## Besonderheiten / Sonstige Hinweise

```
-
-
-
```

---

## Technische Anforderungen

- Hosting: Vercel (Standard) / IONOS
- Framework: Reines HTML/CSS/JS (kein React, kein Build-Tool)
- GSAP: Ja (via cdnjs CDN)
- Zweite Unterseite benötigt: Ja / Nein → `____________.html`
- Formular benötigt: Ja (Mailto) / Nein
- Cookie-Banner: Ja / Nein
