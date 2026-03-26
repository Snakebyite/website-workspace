# Telos — Design System

## Color System

### Base
| Token | Hex | Usage |
|---|---|---|
| background | #0A0A0A | Page background |
| surface | #141414 | Cards, elevated elements |
| surface-elevated | #1C1C1C | Modals, dropdowns, hover states |
| border | rgba(255,255,255, 0.05) | Subtle borders for depth |
| border-hover | rgba(255,255,255, 0.10) | Border on hover/focus |

### Text
| Token | Hex | Usage |
|---|---|---|
| text-primary | #EFEFEF | Headlines, primary body text |
| text-secondary | #888888 | Supporting text, labels, captions |
| text-muted | #555555 | Disabled states, metadata |

### Accent (Telos Green — Dark-Mode-adaptiert)
| Token | Hex | Usage |
|---|---|---|
| accent | #4CAF82 | CTAs, Buttons — Telos Green aufgehellt für Dark-Mode-Kontrast |
| accent-hover | #348066 | Hover-State — Original-Brandfarbe als Hover |
| accent-text | #6BAF96 | Links, Text-Akzente — heller für Lesbarkeit auf dunklem Grund |
| accent-subtle | rgba(76, 175, 130, 0.12) | Badge-Backgrounds, Highlight-Flächen |

### Regeln
- Accent nur für interaktive Elemente: Buttons, Links, Hover-States
- Kein Accent als Hintergrundfarbe für ganze Sections
- Monochrom ist der Normalzustand, Accent ist der Ausnahmefall
- Kontrast prüfen: Text auf Background muss min. 4.5:1 WCAG AA erfüllen

---

## Typography

### Font Stack
| Rolle | Font | Fallback |
|---|---|---|
| Headlines | Instrument Serif (Serif) | Georgia, serif |
| Body | Satoshi (Sans-Serif) | system-ui, sans-serif |

### Type Scale
| Element | Size (Desktop) | Weight | Letter-Spacing | Line-Height |
|---|---|---|---|---|
| H1 (Hero) | 64px / 4rem | Medium (500) | -0.04em | 1.1 |
| H2 (Section) | 48px / 3rem | Medium (500) | -0.03em | 1.15 |
| H3 (Sub-Section) | 32px / 2rem | Medium (500) | -0.02em | 1.2 |
| H4 | 24px / 1.5rem | Medium (500) | -0.01em | 1.3 |
| Body Large | 20px / 1.25rem | Regular (400) | 0 | 1.6 |
| Body | 16px / 1rem | Regular (400) | 0 | 1.6 |
| Small / Caption | 14px / 0.875rem | Regular (400) | 0.01em | 1.5 |
| Button | 16px / 1rem | Medium (500) | 0.01em | 1 |
| Label / Overline | 12px / 0.75rem | Medium (500) | 0.08em | 1.4 |
| Pull-Quote | 24px / 1.5rem | Regular (400) | -0.01em | 1.4 |

### Regeln
- Headlines: Instrument Serif, tight letter-spacing (negativ)
- Body: Satoshi, normales letter-spacing
- **Label/Overline:** Satoshi, uppercase, weites letter-spacing (0.08em). Für Kategorien, Tags, Section-Identifier (z.B. "STRATEGIE / 2024").
- **Pull-Quotes & Testimonials:** Instrument Serif darf auch außerhalb von Headlines für kuratorische Texte eingesetzt werden — Zitate, Testimonials, Hero-Sublines. Nicht für Body-Copy.
- Keine weiteren Fonts. Zwei reichen.
- Mobile: H1 runter auf 40px, H2 auf 32px, H3 auf 24px

---

## Spacing

### Scale
| Token | Value |
|---|---|
| xs | 4px |
| sm | 8px |
| md | 16px |
| lg | 24px |
| xl | 32px |
| 2xl | 48px |
| 3xl | 64px |
| 4xl | 96px |
| 5xl | 128px |
| section-gap | 160px |

### Regeln
- Sections: 160px Abstand (Desktop), 96px (Mobile)
- Großzügig mit Whitespace. Premium = Raum lassen.
- Lieber zu viel Platz als zu wenig.

---

## Layout

### Container
| Breakpoint | Max-Width | Padding |
|---|---|---|
| Mobile | 100% | 16px (px-4) |
| Tablet (768px) | 100% | 32px (px-8) |
| Desktop (1024px) | 1280px | 32px (px-8) |

### Grid
- CSS Grid oder Flexbox, kein festes Spalten-System
- Hero: Full Viewport Height (min-h-dvh)
- Content Sections: Centered Container (max-w-7xl)

### Editorial Layout
- **Asymmetrie ist der Default.** Nicht alles zentriert, nicht alles symmetrisch. Bewusste 2/3 + 1/3 oder 3/5 + 2/5 Splits für Text-Bild-Kombinationen.
- **Grid-Brüche erlaubt.** Einzelne Elemente (z.B. Hero-Headline, Pull-Quotes) dürfen aus dem Container ausbrechen oder versetzt stehen.
- **Overlap sparsam einsetzen.** Headline die ein Bild um 1–2rem überlappt kann editorial wirken — aber max. 1x pro Page, nicht als Pattern wiederholen. Responsive-Verhalten explizit definieren.
- **Auf Mobile wird alles linear.** Asymmetrische Layouts stacken auf Mobile zu einer einzelnen Spalte. Die Asymmetrie lebt nur auf Desktop/Tablet.

---

## Elevation & Depth

Tiefe entsteht durch Farbabstufung und Licht, nicht durch Linien.

### Tonal Layering (Default)
- **Grenzen durch Farbwechsel statt Borders.** Eine Card auf `surface` (#141414) gegen `background` (#0A0A0A) braucht keinen Border — der Helligkeitsunterschied reicht.
- **Borders nur als Fallback** wenn interaktive Affordance nötig ist (z.B. Hover-State, Touch-Target-Klarheit). Dann: `rgba(255,255,255, 0.05)`, auf Hover `0.10`.
- **Keine 1px solid Borders für Section-Trennung.** Sections werden durch Spacing (section-gap) und Tonal Shifts getrennt.

### Shadows
- **Ambient Shadows für schwebende Elemente:** Modals, Flyouts, Dropdowns.
- Wert: `box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3)` — weich, diffus, nie grau.
- **Keine Drop-Shadows auf Cards.** Cards nutzen Tonal Layering statt Schatten.

### Navigation (Sticky)
- Background: `rgba(10, 10, 10, 0.9)` — solid dunkel mit leichter Transparenz.
- **Kein `backdrop-blur`** — zu GPU-intensiv in Kombination mit Lenis + GSAP ScrollTrigger. Der Performance-Preis ist den Effekt nicht wert.

---

## Components

### Buttons
| Variante | Style |
|---|---|
| Primary | bg: #4CAF82 (accent), text: #0A0A0A, radius: 12px, padding: 16px 32px |
| Primary Hover | bg: #348066 (accent-hover), transition: color-shift (kein scale, kein grow) |
| Secondary | bg: transparent, border: rgba(255,255,255, 0.10), text: #EFEFEF, radius: 12px |
| Secondary Hover | border: rgba(255,255,255, 0.20) |
| Text Link | text: #6BAF96 (accent-text), underline on hover |

### Cards
- Background: surface (#141414) — Tonal Layering gegen background reicht als Abgrenzung
- Border: optional, nur wenn interaktive Affordance nötig. Dann rgba(255,255,255, 0.05)
- Border-Radius: 16px (rounded-2xl)
- Padding: 32px
- Hover: subtiler Background-Shift zu surface-elevated (#1C1C1C) ODER border rgba(255,255,255, 0.10)

### Badges
- Background: rgba(76, 175, 130, 0.12) (accent-subtle)
- Text: #6BAF96 (accent-text)
- Border-Radius: 8px
- Padding: 4px 12px

### Listen & Dividers
- **Kurze Listen (< 6 Items):** Whitespace als Trennung (spacing lg–xl zwischen Items). Keine Divider.
- **Lange Listen (6+ Items):** Subtile Divider erlaubt — `rgba(255,255,255, 0.05)`, 1px. Scannability geht vor Ästhetik.

### Icons
- Icons **unterstützen** Text, ersetzen ihn nie. Kein Icon ohne Label.
- Einsatz: neben Service-Beschreibungen, Benefit-Listen, Feature-Cards.
- Nicht in der primären Navigation — Text-first.
- Farbe: text-secondary (#888888) im Normalzustand, text-primary (#EFEFEF) bei Hover.

---

## Backgrounds & Visual Depth

Das dunkle Farbschema braucht bewusste Tiefe, sonst wirkt die Seite flach. Solid-Color-Backgrounds allein reichen nicht.

### Techniken
| Technik | Anwendung | Umsetzung |
|---|---|---|
| Radial Glow | Hinter Hero-Headline, hinter Key-Visuals | `radial-gradient(ellipse at center, rgba(62,207,180,0.06) 0%, transparent 70%)` — Accent-Farbe, sehr niedrige Opacity (0.03–0.08) |
| Noise/Grain Overlay | Global auf `<body>` oder auf großen Dark-Flächen | SVG-Noise-Texture als `background-image`, Opacity 0.03–0.05. Verhindert Color-Banding und gibt Textur |
| Soft Vignette | Section-Backgrounds | Subtiler radialer Gradient von transparent zu leicht dunkler am Rand |
| Gradient Sections | Übergang zwischen Sections | Sanfter Gradient von `#0A0A0A` → `#0F0F0F` → `#0A0A0A` statt harter Farbwechsel |

### Regeln
- **Subtilität ist Pflicht.** Wenn man den Effekt sofort sieht, ist er zu stark. Man soll ihn *fühlen*, nicht *sehen*.
- **Accent-Glows nur hinter Focal Points** — nie als Flächen-Dekoration. Max. 1–2 pro Viewport.
- **Kein Gradient als Design-Ersatz.** Gradients unterstützen Hierarchie, sie ersetzen keine Komposition.
- **Noise-Overlay ist global, nicht pro Section.** Einmal anwenden, konsistent halten.
- **Performance:** CSS-Gradients bevorzugen. Noise als kleine tileable SVG/PNG (< 5KB). Keine Canvas-basierten Effekte.

---

## Animation

### Easing
| Typ | Value | Verwendung |
|---|---|---|
| Entrance | power2.out | Elemente die reinkommen |
| Transition | power2.inOut | State-Changes, Hover |
| Micro | ease-out, 200ms | Buttons, Links, kleine Interactions |

### Scroll-Animationen (GSAP ScrollTrigger)
- Fade-in + translate-y (20px): Standard-Entrance für Elemente
- Stagger: 0.08s zwischen Elementen
- SplitText für Headline-Reveals (Wort für Wort)
- Scrub-Animationen für parallax-artige Effekte

### Regeln
- Animation unterstützt den Content, steht nie im Vordergrund
- Kein Bounce, kein Overshoot
- 200ms für Micro-Interactions (Hover, Focus)
- Scroll-Animationen: subtil, nicht dramatisch
- prefers-reduced-motion respektieren

---

## Allgemeine Prinzipien

1. **Monochrom ist der Default.** Accent nur als Akzent, nie als Hauptfarbe.
2. **Raum lassen.** Wenn ein Layout "voll" wirkt, ist es nicht mehr premium. Im Zweifel mehr Whitespace.
3. **Text und Bild in Symbiose.** Keine Visuals als Dekoration, alles hat eine Funktion.
4. **Natürlicher Flow.** Keine harten Section-Brüche, der Scroll soll sich fließend anfühlen.
5. **Details zeigen Sorgfalt.** Micro-Interactions, saubere Hover-States, konsistente Abstände.
6. **Tonal Layering vor Borders.** Grenzen durch Farbabstufung definieren, nicht durch Linien. Borders nur als Fallback für Affordance.
7. **Editorial, nicht Template.** Asymmetrische Layouts, bewusste Grid-Brüche, versetztes Text-Bild-Spiel. Die Seite soll sich *designed* anfühlen, nicht zusammengebaut.
8. **Text-first.** Icons ergänzen, ersetzen aber nie Text. Navigation, CTAs und Headlines sprechen für sich.
