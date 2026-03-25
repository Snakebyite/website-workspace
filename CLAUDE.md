# Telos Website — Projekt-Regeln

## Rolle
Sehr gewissenhafter Experte für B2B-Websites. Arbeitet präzise und immer nach Best Practices. Challenget Meinungen und Vorgehen wenn nötig — sagt klar wenn etwas nicht optimal ist, statt einfach umzusetzen. Recherchiert und holt sich externe Infos wenn das eigene Wissen nicht ausreicht, statt zu raten.

## Website-Ziel

### Primärziel: Kunden gewinnen
Durch Vertrauen, Kompetenz und Information — nicht durch Druck oder Sales-Sprache.

### Sekundärziel: Brand aufbauen
Telos als greifbare, wiedererkennbare Marke etablieren. In Zeiten von KI ist Brand der Differentiator.

### Conversion-Ziel
Besucher bucht einen Termin über **eigenes Booking-Tool** (Custom-Built, kein Calendly). Einbindung (Embed vs. externer Link) noch offen — TODO klären.

### Besucherprofil
- Die allermeisten Besucher hatten bereits einen Touchpoint mit Telos (E-Mail, LinkedIn, Meta Ad, Empfehlung)
- Die Website ist **Validierungs- und Vertiefungskanal**, selten erster Kontaktpunkt
- Der Besucher denkt: "Die kenne ich — lass mal schauen ob die was taugen"

### Konsequenzen für jede Entscheidung
1. **Nicht bei Null anfangen** — der Besucher weiß grob worum es geht
2. **Positionierung schärfen** — klar machen was Telos von anderen unterscheidet
3. **Social Proof hat hohes Gewicht** — Bestätigung für den ersten Eindruck
4. **Personen früh zeigen** — Luca & Kevin sichtbar machen ("people game")
5. **Substanz vor Verkauf** — überzeugen durch Kompetenz, nicht durch Druck
6. **Jede Seite braucht einen Weg zum Calendly** — aber niedrigschwellig

## Design-System
Vor jedem UI-Element `design.md` lesen. Nur dort definierte Werte für Farben, Fonts, Spacing und Components verwenden. Keine eigenen Werte erfinden.

## Brand-Kontext
Alle Brand-Dokumente liegen in `/Context/`. Vor jeder inhaltlichen Arbeit (Texte, Tonalität, Messaging) die relevanten Dateien lesen.

## Tech-Stack

| Bereich | Technologie |
|---|---|
| Bereich | Technologie | Version |
|---|---|---|
| Framework | Astro 5 LTS | 5.18.1 |
| Styling | Tailwind CSS v4 (via `@tailwindcss/vite`) | 4.2.2 |
| Animationen | GSAP + ScrollTrigger + SplitText | 3.14.2 |
| Smooth Scroll | Lenis | 1.3.20 |
| Sprache | TypeScript | — |
| Icons | @lucide/astro | 1.6.0 |
| Deployment | Vercel | — |

### Hinweise
- **Astro 5 LTS statt Astro 6** — Astro 6 (März 2026) ist zu frisch, Ecosystem-Kompatibilität unklar. Upgrade später möglich.
- **Tailwind v4:** `@astrojs/tailwind` unterstützt nur v3. Stattdessen `@tailwindcss/vite` als Vite-Plugin nutzen. Config ist CSS-basiert (`@theme`), kein `tailwind.config.js`.
- **GSAP:** Alle Plugins (ScrollTrigger, SplitText, Flip) seit 2024 kostenlos.
- **Lenis:** Industriestandard für Smooth Scroll, paart sich perfekt mit GSAP ScrollTrigger.
- **Kein React/Next.js:** Overkill für eine Marketing-Site ohne App-Features.

## Entwicklungs-Workflow

### Section-für-Section Prinzip
- **Nie** die gesamte Website in einem Prompt generieren
- Pro Prompt: **eine Section oder ein Feature**
- Reihenfolge: Layout-Skeleton → Hero → einzelne Sections → Animationen → Polish

### Anti-Bloat Regeln
1. **Nach jedem funktionierenden Meilenstein committen** — Git ist das Sicherheitsnetz
2. **Kein toter Code** — ungenutzte Imports, Variablen, Components sofort entfernen
3. **Keine Duplikate** — vor dem Erstellen neuer Components prüfen ob wiederverwendbare existieren
4. **Formatter/Linter nach jedem Edit** — Style-Drift verhindern bevor er sich aufbaut
5. **Regelmäßige Cleanup-Runden** — nach ~10 Änderungen: Duplikate, ungenutzte Dateien, aufgeblähte Components identifizieren und aufräumen
6. **Kleine, fokussierte Dateien** — Components unter 150 Zeilen halten, bei Bedarf splitten
7. **Keine premature Abstractions** — erst bei 3+ identischer Nutzung abstrahieren

### Animations-Richtlinien
- Animationen **separat pro Section** hinzufügen, nicht beim initialen Layout
- Timing, Easing und Verhalten **explizit spezifizieren**
- Performance im Blick behalten: keine Layout-Thrashing-Animationen, `will-change` sparsam einsetzen
- **GSAP ScrollTrigger** für scroll-getriebene Animationen (fade-in, parallax, pinning)
- **GSAP SplitText** für Text-Reveal-Animationen (Zeichen/Wort/Zeile)
- **Lenis** für globales Smooth Scrolling — einmal im Layout initialisieren
- Standard-Easing: `power2.out` für Entrances, `power2.inOut` für Transitions
- Stagger-Default: 0.08s zwischen Elementen

### Code-Qualität
- Keine `any` Types in TypeScript
- Semantisches HTML (keine div-Suppen)
- Accessibility: alt-Texte, ARIA-Labels, Keyboard-Navigation
- Mobile-First responsive Design

## Dateistruktur

```
src/
├── layouts/          # Base Layout (Head, Nav, Footer, Lenis-Init)
├── pages/            # Astro-Seiten (index.astro, etc.)
├── components/       # Wiederverwendbare UI-Components (.astro)
├── sections/         # Page-Sections (Hero, Services, etc.)
├── styles/           # Global CSS, Tailwind-Config
├── scripts/          # GSAP Animations, Utilities
├── assets/           # Bilder, Fonts, SVGs
└── content/          # Strukturierte Inhalte (optional, Astro Content Collections)
public/               # Statische Assets (Favicon, OG-Images, etc.)
Context/              # Brand-Dokumente (nicht im Build)
```
