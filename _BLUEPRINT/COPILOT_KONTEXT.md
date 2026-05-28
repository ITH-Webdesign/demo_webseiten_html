# Copilot-Kontext — IT Happens GbR / Yannick

> **Für Copilot**: Lies diese Datei vollständig bevor du irgendeine Zeile Code schreibst.
> Sie enthält meine Arbeitsweise, Standards und Designphilosophie.
> Jedes Projekt bekommt eine **individuelle, auf den Kunden zugeschnittene** Webseite —
> kein Copy-Paste, kein generischer Look. Frag mich nach dem Kundenbriefing bevor du anfängst.

---

## Wer ich bin & was ich mache

Ich (Yannick, IT Happens GbR) baue moderne Webseiten für lokale Unternehmen mit veralteter Online-Präsenz.
Ich recherchiere Unternehmen selbst, baue eine Demo ihrer neuen Website und schicke dem Kunden den Link —
ohne vorherigen Auftrag. Überzeugt die Demo, entsteht daraus ein bezahlter Auftrag.

**Ziel der Webseite**: Den Kunden beeindrucken. Nicht den Kunden seines Kunden — sondern den
Unternehmer selbst, der entscheiden soll ob er mich beauftragt.

---

## Tech-Stack (immer)

- **Reines HTML / CSS / JavaScript** — kein React, kein Vite, kein Build-Tool
- **GSAP 3.12.5** via cdnjs CDN, **am Ende von `<body>`** (kein render-blocking im `<head>`)
- `gsap.registerPlugin(ScrollTrigger)` immer als erstes nach den Script-Tags
- **Google Fonts** via CDN mit `<link rel="preconnect">` im `<head>`
- **Keine CSS-Frameworks** (kein Tailwind, kein Bootstrap) — eigenes CSS mit Design-Tokens
- **Vercel** für Deployment (statisch, auto-deploy von GitHub `main`)
- **IONOS** für Produktionshostings — Linux-Server = Dateipfade case-sensitive!

---

## Animationen & Interaktion

### Was ich bereits erfolgreich gebaut habe und wieder verwenden kann:
- **Curtain Intro**: Vorhang-Animation beim ersten Seitenaufruf (sessionStorage + `navigation.type`)
  - Regel: nur bei `reload` oder erstem Besuch — nie beim Zurücknavigieren (Back-Button)
- **Scroll Reveals**: `.anim-up` Klasse + GSAP ScrollTrigger
- **Nav scroll-hide**: Navigation versteckt sich beim Runterscrollen, erscheint beim Raufscrollen
- **Card-Flip**: 3D-Flip auf Hover (Desktop CSS `:hover`) + Tap-Toggle für Touch (`.is-flipped` via JS)
- **Scroll Progress Bar**: schmaler Balken oben in Akzentfarbe
- **Parallax**: Hintergrundbilder mit unterschiedlicher Scroll-Geschwindigkeit
- **Magnetic Buttons**: Button bewegt sich leicht Richtung Mauszeiger

### Regeln:
- Animiere **nur** `transform` und `opacity` — nie `width`, `height`, `top`, `margin`
- `ease: 'none'` bei scrub-Animationen (sonst fühlt sich scrub falsch an)
- Alle Animationen in `gsap.matchMedia()` wrappen:
  - `(prefers-reduced-motion: no-preference)` → Animationen aktiv
  - `(prefers-reduced-motion: reduce)` → Elemente sofort sichtbar, kein Bewegung
- Touch-Geräte: Tilt/Hover-Effekte weglassen oder durch Tap ersetzen
- GSAP Debug-Marker (`markers: true`) vor Deployment entfernen

---

## CSS-Architektur

### Design Tokens (immer in `:root`, immer anpassen)
```css
:root {
  --primary:    /* Haupthintergrundfarbe */;
  --accent:     /* Akzentfarbe (CTAs, Highlights) */;
  --gold:       /* Sekundärer Akzent (Preise, Details) */;
  --cream:      /* Heller Text auf dunklem BG */;
  --ink:        /* Dunkler Text auf hellem BG */;
  --serif:      /* Headline-Font */;
  --sans:       /* Body-Font */;
  --container:  min(1200px, 90vw);
  --section-py: clamp(5rem, 10vw, 9rem);
  --radius:     12px;
  --transition: 0.25s ease;
}
```

### Responsive Typografie (immer `clamp()`)
```css
/* Headlines */
font-size: clamp(2.5rem, 6vw, 6rem);

/* Body */
font-size: clamp(0.95rem, 1.1vw, 1.05rem); /* nie unter 16px */

/* Section-Titles */
font-size: clamp(2rem, 4vw, 3.5rem);
```

### Was ich vermeide:
- Feste `px`-Größen für Schrift oder Abstände die auf Mobile brechen
- Emoji als Icons → immer SVG (Heroicons: heroicons.com)
- Placeholder-Text als Label in Formularen
- Harte `height`-Angaben auf Containern die Text enthalten
- `!important` außer als letzte Notlösung
- Generisches Stock-Foto-Feeling (lieber keine Bilder als schlechte)

---

## Was eine moderne Webseite ausmacht

### Das Wichtigste zuerst:
1. **Auf dem Handy perfekt** — die meisten Kunden-Kunden schauen mobil
2. **Schnell** — keine Ladezeit > 2 Sekunden (CDN-Fonts, optimierte Bilder)
3. **Klare Hierarchie** — ein primärer CTA pro Seite, kein Informationschaos
4. **Vertrauen** — Telefonnummer klickbar, echte Adresse, Öffnungszeiten stimmen
5. **Charakter** — die Seite soll nach dem Unternehmen riechen, nicht nach Template

### Technisch:
- HTTPS (Vercel macht das automatisch)
- Kein leerer Bildschirm beim Laden (Preloader oder sofort sichtbarer Content)
- Alle `<img>` haben `alt`-Attribute
- Interaktive Elemente haben `cursor: pointer`
- Hover-States auf allem Klickbaren (150–300ms transition)
- Kontrast mindestens WCAG AA (4,5:1 für Fließtext)
- `<meta name="description">` ausgefüllt (max. 160 Zeichen)
- `<title>` spezifisch, nicht nur "Startseite"

---

## Designphilosophie: Jede Seite ist einzigartig

**Das ist der wichtigste Punkt.** Jeder Kunde bekommt ein individuelles Design.
Das bedeutet in der Praxis:

- **Farbpalette**: Von der Branche und Identität des Unternehmens ableiten, nicht aus einer festen Liste kopieren
- **Typografie**: Das Font-Paar zur Persönlichkeit wählen — ein rustikaler Handwerksbetrieb bekommt andere Schriften als eine moderne Zahnarztpraxis
- **Layout-Struktur**: Nicht immer Hero → About → Services → Kontakt. Die Reihenfolge der Erzählung hängt davon ab was den Kunden überzeugt
- **Stimmung**: Wärme, Kühle, Energie, Ruhe — das lese ich aus dem Unternehmen heraus
- **Animationen dosieren**: Manchmal ist wenig mehr. Ein ruhiges Spa braucht sanfte Fades, kein Feuerwerk

Richtlinien für gängige Branchen (als Ausgangspunkt, nicht als Vorschrift):

| Branche | Stimmung | Farbtendenz | Font-Tendenz |
|---------|----------|-------------|--------------|
| Restaurant / Gastro | Warm, einladend | Erdtöne, Dunkelbraun, Creme | Serif (Fraunces, Playfair) + Sans |
| Barbershop / Friseur | Dark Premium, maskulin | Fast-Schwarz, Gold | Playfair + Inter Tight |
| Handwerk / KFZ | Solide, vertrauenswürdig | Navy, Orange, Off-White | Space Grotesk + Inter |
| Zahnarzt / Arzt | Sauber, professionell, hell | Weiß, Blau, Hellgrau | DM Serif + DM Sans |
| Architekt / Design | Minimalistisch, reduziert | Fast-Weiß oder Fast-Schwarz | Cormorant + Inter Tight |
| Kosmetik / Spa | Sanft, feminin, premium | Pastell, Rose Gold, Creme | Cormorant + Montserrat |
| Anwalt / Steuerberater | Seriös, edel | Dunkelblau, Weiß, Gold | Libre Baskerville + Inter |

---

## Projekt-Checkliste (vor Kundensend)

- [ ] Alle BUSINESSNAME / PLACEHOLDER ersetzt
- [ ] Telefonnummer klickbar (`tel:+49...`)
- [ ] E-Mail klickbar (`mailto:...`)
- [ ] Öffnungszeiten korrekt
- [ ] Google Maps Link korrekt
- [ ] Bilder laden (Pfade prüfen — Linux: case-sensitive!)
- [ ] Mobile-Test bei 375px (Chrome DevTools)
- [ ] Kein leerer Bildschirm beim Laden
- [ ] GSAP-Debug-Marker entfernt
- [ ] Meta-Title und Description ausgefüllt
- [ ] Vercel-URL im Browser getestet
- [ ] Alle Links funktionieren (kein `href="#"` vergessen)
