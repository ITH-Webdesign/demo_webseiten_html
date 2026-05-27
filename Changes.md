# Changelog — Demo Webseiten Static

---

## 27.05.2026 (Update 2) — Autor: Yannick

### Demo_Flammerie — `index.html` + `speisekarte.html` (Änderungen)

**3D Card-Flip-Animation für Speisenkarten**
- Alle `.dish`-Karten in `index.html` (6 Gerichte) und `speisekarte.html` (15 Gerichte) auf eine 3D-Flip-Interaktion umgebaut
- Desktop: Karte dreht sich beim Hover automatisch um (CSS `:hover`, kein JavaScript erforderlich)
- Touch/Mobile: Antippen der Karte flippt sie hin und her (JS `.is-flipped`-Toggle)
- Rückseite zeigt das Gericht-Bild im vollen Kartenformat mit Gradient-Overlay sowie Name, Nummer und Preis
- Vorherige GSAP-Tilt-Animation (`initCardTilt`) entfernt und durch Touch-kompatible Flip-Logik ersetzt
- Flip-Dauer: 0,7 s mit `cubic-bezier(0.4, 0, 0.2, 1)` für natürliche Rotation
- HTML-Struktur pro Karte: `.dish > .dish__inner > .dish__front` + `.dish__back`

---

## 27.05.2026 — Autor: Yannick

### Demo_Flammerie — `speisekarte.html` (neu)
- Vollständige Speisekarte-Unterseite erstellt (`speisekarte.html`)
- Identisches Design-System wie `index.html` (Farben, Schriften, Tokens)
- Alle 15 echten Gerichte von flammerie-zum-ochsen.de integriert:
  - 12 herzhafte Flammkuchen in einem 4-spaltigen Grid mit Tags (Klassiker, Vegetarisch, Beliebt, Scharf, Regional, Süss-Pikant, Saison)
  - 3 süße Flammkuchen in einem 3-spaltigen Grid
- „All you can eat"-Sektion mit Preiskarte (21,90 € / Kinder 12,90 €), drei Feature-Punkten und Reservierungs-CTA
- CTA-Band in Ember-Orange am Ende der Seite
- Gleiche Navigation wie Startseite (Links zeigen zurück zu `index.html`)
- Identischer Footer mit Öffnungszeiten und Kontakt
- GSAP Scroll-Reveals, 3D-Karten-Tilt und Fortschrittsbalken
- SEO: eigene `meta description`, OG-Tags, `aria`-Attribute

### Demo_Flammerie — `index.html` (Änderungen)

**Verlinkung Speisekarte**
- „Vollständige Speisekarte"-Button: `href="#contact"` → `href="speisekarte.html"`
- Footer-Nav „Speisekarte": `href="#menu"` → `href="speisekarte.html"`

**Gutscheine-Sektion**
- Neue Sektion `#gutscheine` zwischen Story und CTA-Band eingefügt
- Inhalte von der echten Website übernommen und ans Design angepasst
- Zwei-Spalten-Layout: Text links, dekorative CSS-Gutscheinkarte rechts
- CTA „Per Mail anfordern" mit vorausgefülltem `mailto:`-Link
- CTA „Öffnungszeiten & Adresse" scrollt zu `#contact`
- „Gutscheine" in Desktop-Navigation, Hamburger-Menü und Footer ergänzt

**Curtain-Intro-Animationslogik**
- Startanimation erscheint nur beim echten ersten Besuch oder bei Seitenneu-laden (F5)
- Kein erneutes Abspielen beim Zurücknavigieren von Unterseiten (Back-Button oder Link-Klick)
- Technisch umgesetzt mit `sessionStorage` + `performance.getEntriesByType('navigation')[0].type`:
  - `reload` → Animation spielt immer
  - `navigate` + Flag gesetzt → Animation wird übersprungen
  - `back_forward` → Animation wird übersprungen

**Button-Fix**
- Neuen Button-Variant `.btn--ghost-light` hinzugefügt (helle Variante für dunkle Hintergründe)
- „Öffnungszeiten & Adresse"-Button in der Gutscheine-Sektion von `.btn--ghost` auf `.btn--ghost-light` umgestellt

---
