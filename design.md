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
| text-secondary | #999999 | Supporting text, labels, captions |
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
- **Ausnahme:** `accent-text` darf als Highlight für Kernbegriffe in Headlines verwendet werden (z.B. Brand-Claim "Best Interest Advisor"). Sparsam — max. 1 Highlight pro Headline.
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
| H1 (Hero) | 72px / 4.5rem | Medium (500) | 0 (normal) | 1.1 |
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
- Headlines: Instrument Serif, tight letter-spacing (negativ). Ausnahme H1 Hero: `tracking-normal` (0) — Live-Feedback ergab dass -0.04em zu cramped wirkt bei der Hero-Größe.
- Body: Satoshi, normales letter-spacing
- **Label/Overline:** Satoshi, uppercase, weites letter-spacing (0.08em). Für Kategorien, Tags, Section-Identifier (z.B. "STRATEGIE / 2024").
- **Pull-Quotes & Testimonials:** Instrument Serif darf auch außerhalb von Headlines für kuratorische Texte eingesetzt werden — Zitate, Testimonials, Hero-Sublines. Nicht für Body-Copy.
- Keine weiteren Fonts. Zwei reichen.
- Mobile: H1 (Hero) runter auf 44px (2.75rem), H2 auf 32px, H3 auf 24px

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
| Radial Glow | Hinter Hero-Headline, hinter Key-Visuals | `radial-gradient(ellipse at center, rgba(76,175,130,0.06) 0%, transparent 70%)` — Accent-Farbe, sehr niedrige Opacity (0.03–0.08) |
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

## Visual Language

Definiert was als Bildmaterial auf der Seite erscheint und wie es behandelt wird. Diese Regeln verhindern generische Platzhalter-Visuals.

### Primäre Visuals: Echte Arbeit zeigen
- **Marketplace-Screenshots:** Amazon Seller Central Dashboards, Listing-Ansichten, Analytics-Graphen. In Browser-Chrome oder Device-Frame. Zeigt Kompetenz durch Spezifität.
- **Vorher/Nachher:** Listing-Optimierungen, Ranking-Verbesserungen, Traffic-Kurven. Konkreter Beweis statt vager Versprechen.
- **Daten als Visual:** Große Zahlen (z.B. "+340% organischer Traffic") in Instrument Serif auf Display-Größe SIND das Visual. Die Zahl ist der Hero, die Erklärung sekundär.

### People Photography
- Luca & Kevin: echte Fotos, nicht Studio-perfekt. Candid oder semi-candid.
- **Kein kreisrunder Avatar-Crop.** Rechteckig mit großzügigen Proportionen.
- Farbig oder leicht entsättigt — kein Schwarz-Weiß-Filter, kein Duotone.

### Screenshot-Behandlung
- Abgerundete Ecken (8px) auf Screenshots
- Auf Dark-Background: Screenshots auf `surface` (#141414) Fläche platzieren oder mit subtle Border (`rgba(255,255,255, 0.05)`) abgrenzen
- Optional: Ambient Shadow (`0 20px 50px rgba(0,0,0,0.3)`) für schwebenden Effekt
- Responsive: Screenshots skalieren proportional, werden nie verzerrt

### Verboten
- **Kein Stock.** Keine generischen "Menschen am Laptop" Bilder.
- **Keine abstrakten Illustrationen.** Keine Blob-Shapes, keine schwebenden Geometrie-Formen, keine dekorativen SVG-Patterns.
- **Keine KI-generierten Bilder.** Keine Midjourney/DALL-E Visuals.
- **Keine dekorativen Gradient-Blobs.** Gradients dienen der Tiefe (siehe Backgrounds & Visual Depth), nie als Dekoration.

---

## Section Archetypes

Konkrete Kompositions-Vorgaben für jeden Section-Typ. Diese ersetzen die generischen AI-Defaults.

### Hero
**AI-Default (vermeiden):** Zentriertes H1 + Subtitle + CTA + abstrakter Gradient rechts.

**Telos-Komposition:**
- **Layout:** Split — H1 linksbündig (55–60%), Arbeits-Artefakt rechts (40–45%). Oder: Full-width H1 mit Artefakt darunter, Kante-zu-Kante.
- **Headline:** H1 in Instrument Serif, bewusste Zeilenumbrüche die Schlüsselwörter betonen. Nicht zentriert.
- **Subline:** 1 Satz in Body Large, text-secondary. Abstand zum H1: spacing xl (32px).
- **CTA:** Primary + Secondary Button, links unter der Subline. Nicht zentriert.
- **Visual:** Realer Screenshot, Dashboard oder Daten-Visualisierung. Kein abstraktes Hero-Image.
- **Radial Glow:** Dezenter Accent-Glow hinter dem Focal Point (Headline oder Visual).

### Social Proof / Logos
**AI-Default (vermeiden):** "Trusted by" Überschrift + 5 Logos in einer Reihe, zentriert, mit Borders.

**Telos-Komposition:**
- **Kein "Trusted by" Headline.** Die Logos sprechen für sich.
- Logos in einer Reihe, monochromatisch (text-muted Farbe, ~40% Opacity).
- Keine Borders, keine Card-Container. Logos direkt auf Background.
- Kompakte Section — wenig vertikaler Raum (spacing 3xl oben/unten). Dient als Atempause, nicht als eigene Section.
- Alternative: Weglassen wenn nicht genug starke Brand-Names vorhanden sind. Lieber keine Logos als schwache.

### Services / Leistungen
**AI-Default (vermeiden):** 3 gleiche Cards nebeneinander, je mit Icon + Titel + 2-Zeilen-Beschreibung.

**Telos-Komposition:**
- **Kein Card-Grid.** Stattdessen: gestapelte Full-Width-Rows.
- Jeder Service bekommt eine eigene Row: Headline links, Beschreibung + ggf. Visual rechts (60/40 Split).
- **Variierende visuelle Gewichtung:** Ein Haupt-Service groß und prominent, 2–3 sekundäre Services kompakter darunter. Nicht alles gleich gewichten.
- Label/Overline über jeder Service-Headline (z.B. "MARKETPLACE SEO", "LISTING-OPTIMIERUNG").
- Zwischen den Rows: spacing 2xl–3xl. Innerhalb einer Row: spacing xl.

### Prozess / How It Works
**AI-Default (vermeiden):** Nummerierte Steps 1-2-3 horizontal nebeneinander mit Icons.

**Telos-Komposition:**
- **Vertikal statt horizontal.** Steps untereinander, alternierend Text links/rechts (oder alle links mit visueller Verbindungslinie).
- Jeder Step: Nummer (Display-Size, text-muted) + Headline (H3) + kurze Beschreibung (Body, text-secondary).
- Die Verbindung zwischen Steps: subtile vertikale Linie in text-muted Farbe oder spacing allein.
- **Kein Icon pro Step.** Die Nummer ist die visuelle Ankerfunktion.

### Ergebnisse / Case Studies
**AI-Default (vermeiden):** 3 Cards mit Metrics-Icons.

**Telos-Komposition:**
- **Ein Case Study groß featured** (60% Section-Breite): Screenshot + Daten + Kontext.
- 2–3 sekundäre Ergebnisse als kompakte Rows darunter (kein Card-Grid).
- **Große Zahlen als Typografie:** "+127% Umsatz" in Instrument Serif, H2-Größe. Die Zahl ist das Visual.
- Kontext-Label darunter in Small/Caption: "Organischer Traffic nach 6 Monaten".
- Surface-Background (#141414) für die gesamte Section um sie vom Rest abzusetzen.

### Testimonials
**AI-Default (vermeiden):** Quote-Card mit rundem Avatar-Bild + Name + Rolle.

**Telos-Komposition:**
- **Großes Pull-Quote** in Instrument Serif (Pull-Quote Size, 24px). Kein Anführungszeichen-Icon.
- Person: Name + Rolle + Firmenname in einer Zeile darunter, Small/Caption, text-secondary.
- Foto der Person: rechteckig, neben dem Quote oder darunter. Kein kreisrunder Crop.
- Bei mehreren Testimonials: 1 großes + 2 kompaktere. Nicht alle gleich groß.
- **Kein Karussell als Default.** Testimonials untereinander, verschiedene Größen. Karussell nur wenn 5+ Testimonials.

### Team / Personen
**AI-Default (vermeiden):** 2 gleiche Cards mit Foto + Name + Bio-Text.

**Telos-Komposition:**
- **Persönlich, nicht schematisch.** Luca & Kevin bekommen eine zusammenhängende Section, kein Card-Grid.
- Großes Foto (oder 2 Fotos) mit Text daneben — asymmetrisch (z.B. Foto 45%, Text 55%).
- Rollen und Persönlichkeit zeigen: nicht nur "Co-Founder" sondern was sie antreibt. Kurze Sätze.
- Kann auch als 2 Rows gestaltet werden (Luca links-aligned, Kevin rechts-aligned für Rhythmus).

### CTA / Booking
**AI-Default (vermeiden):** Zentriertes H2 + Button auf farbigem/Gradient-Hintergrund-Banner.

**Telos-Komposition:**
- **Kein farbiger Banner.** CTA lebt auf Background (#0A0A0A) oder Surface (#141414).
- Layout: Headline links, Button rechts. Oder: Headline + 1 Satz Kontext + Button, links-aligned in einer schmalen Spalte (max-w-2xl).
- Der CTA fühlt sich an wie ein natürlicher nächster Schritt, nicht wie eine Werbeanzeige.
- **Wiederholung:** Jede Seite hat mindestens 2 CTA-Touchpoints — einen mid-page (nach Proof/Results), einen am Ende.

---

## Content Rhythm

Die Abfolge der Sections bestimmt das Scroll-Erlebnis. Zwei dichte Sections hintereinander = Ermüdung. Zwei leere hintereinander = Langeweile.

### Intensitäts-Map (Homepage)

```
Section          | Dichte   | Dominantes Element
─────────────────|──────────|───────────────────
Hero             | HOCH     | Headline + Visual
Social Proof     | NIEDRIG  | Logos, Atempause
Services         | MITTEL   | Text + Struktur
Ergebnisse       | HOCH     | Zahlen + Screenshots
Team             | MITTEL   | Fotos + Persönlichkeit
Testimonials     | NIEDRIG  | Pull-Quote, Raum
CTA              | MITTEL   | Headline + Button
```

### Regeln
- **Dicht und sparsam müssen alternieren.** Nie 2x HOCH oder 2x NIEDRIG hintereinander.
- **Kein pauschales Section-Alternieren.** Alle Sections stehen auf `background` (#0A0A0A). `surface` (#141414) nur als bewusste Ausnahme für eine einzelne hervorgehobene Section (z.B. Ergebnisse/Case Studies). Rhythmus entsteht durch Spacing und Content-Dichte, nicht durch Hintergrundfarbwechsel — auf Dark ist der Shift zu subtil und Cards verlieren ihr Tonal Layering.
- **Die Seite baut wie ein Gespräch auf:** Hook → Substanz → Beweis → Mensch → Bestätigung → Nächster Schritt.
- **Keine Section ist optional bei der Komposition.** Auch eine "leere" Section (Social Proof, Testimonial) braucht bewusstes Spacing und Typografie-Hierarchie.

---

## Anti-Patterns

Explizite Blacklist der häufigsten AI-generierten Layout-Klischees. Wenn eine dieser Kompositionen im Output auftaucht, ist das ein Fehler.

### Layout
1. ❌ **3 gleiche Cards nebeneinander** für Services/Features/Benefits. Stattdessen: variierende Gewichtung, Rows, oder asymmetrische Splits.
2. ❌ **Zentriertes H1 + Subtitle + CTA** als Hero. Stattdessen: linksbündig, mit realem Visual.
3. ❌ **Nummerierte horizontale Steps** für Prozesse. Stattdessen: vertikal, alternierend.
4. ❌ **Full-Width farbiger Banner** für CTA-Section. Stattdessen: auf Background, integriert in den Flow.
5. ❌ **Gleich große Team-Cards** mit Foto-Kreis + Name + Bio. Stattdessen: asymmetrisch, persönlich.

### Visuals
6. ❌ **Abstrakte Gradient-Blobs** als Dekoration neben Headlines oder in Hero-Sections.
7. ❌ **Stock-Fotos** von Menschen an Laptops, Handshakes, oder Büro-Szenen.
8. ❌ **Generische Icon-Grids** (Icon + Titel + 2 Zeilen) als Feature-Darstellung.
9. ❌ **Kreisrunde Avatar-Crops** für Team-Fotos oder Testimonials.
10. ❌ **Dekorative SVG-Shapes** (Kreise, Dreiecke, Wellenlinien) ohne Funktion.

### Typografie & Content
11. ❌ **"Trusted by leading companies"** oder ähnliche generische Social-Proof-Headlines.
12. ❌ **Gleichförmige Quote-Cards** mit Anführungszeichen-Icon für Testimonials.
13. ❌ **Lorem-ipsum-artige Filler-Texte** wie "We deliver innovative solutions for your business needs."
14. ❌ **Jede Section gleich strukturiert** (Overline + H2 + Body + Grid). Sections müssen sich in Komposition und Dichte unterscheiden.

---

## Design-Referenzen

Websites die den gewünschten Qualitätsstandard definieren. Nicht kopieren — als Kompass für Kompositions-Entscheidungen nutzen.

| Site | Mitnehmen | Nicht mitnehmen |
|---|---|---|
| [notion.com](https://notion.com/de) | Video/Animation als Hero-Visual statt statischem Bild. Alternierender Rhythmus: dicht → sparsam → dicht. Produkt-Screenshots als primäre Visuals. | Maskottchen-Character (passt nicht zu B2B Consulting). |
| [tilt.com](https://tilt.com/) | Typografisches Selbstbewusstsein — Hero mit reiner Headline, kein Hero-Image. Micro-Quotes statt ausladender Testimonials. Unendlicher Logo-Carousel. | Fintech-Ästhetik, Stock-Overlay-Stil. |
| [resend.com](https://resend.com/) | Radikaler Minimalismus. Dark Theme mit Code als Visual. Jedes Element hat eine Funktion, null Dekoration. Contextual CTAs statt Banner. | Zu developer-fokussiert für B2B Consulting. Kein Wärme-Element. |
| [status.app](https://status.app/) | Asymmetrische Text-Bild-Splits die sich abwechseln (links/rechts). Device-Mockups als Hero-Visual. Große Abstände zwischen Sections. Parallax auf Scroll. | Web3-Ästhetik, zu viele Download-CTAs. |

### Wie die Referenzen nutzen
- **Vor dem Bau einer Section:** Prüfen wie die Referenz-Sites den gleichen Section-Typ lösen. Nicht kopieren, aber als Messlatte für Kompositions-Qualität verwenden.
- **Bei Unsicherheit:** Wenn eine Komposition "generisch" wirkt, gegen die Referenzen prüfen. Würde diese Section auf notion.com oder resend.com bestehen?
- **Kombination:** Telos mischt die typografische Autorität von Tilt mit der Produkt-Zentrierung von Notion und dem dunklen Minimalismus von Resend.

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
