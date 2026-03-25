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

### Accent
| Token | Hex | Usage |
|---|---|---|
| accent | #3ECFB4 | CTAs, Links, aktive States — sparsam einsetzen |
| accent-hover | #32A896 | Hover-State für Accent-Elemente |

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
| Headlines | Domaine Display (Serif) | Georgia, serif |
| Body | Inter (Sans-Serif) | system-ui, sans-serif |

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

### Regeln
- Headlines: Domaine Display, tight letter-spacing (negativ)
- Body: Inter, normales letter-spacing
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

---

## Components

### Buttons
| Variante | Style |
|---|---|
| Primary | bg: #3ECFB4, text: #0A0A0A, radius: 12px, padding: 16px 32px |
| Primary Hover | bg: #32A896 |
| Secondary | bg: transparent, border: rgba(255,255,255, 0.10), text: #EFEFEF, radius: 12px |
| Secondary Hover | border: rgba(255,255,255, 0.20) |
| Text Link | text: #3ECFB4, underline on hover |

### Cards
- Background: surface (#141414)
- Border: rgba(255,255,255, 0.05)
- Border-Radius: 16px (rounded-2xl)
- Padding: 32px
- Hover: border wird rgba(255,255,255, 0.10)

### Badges
- Background: rgba(62, 207, 180, 0.10) (accent mit 10% opacity)
- Text: #3ECFB4
- Border-Radius: 8px
- Padding: 4px 12px

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
2. **Raum lassen.** Im Zweifel mehr Whitespace.
3. **Text und Bild in Symbiose.** Keine Visuals als Dekoration, alles hat eine Funktion.
4. **Natürlicher Flow.** Keine harten Section-Brüche, der Scroll soll sich fließend anfühlen.
5. **Details zeigen Sorgfalt.** Micro-Interactions, saubere Hover-States, konsistente Abstände.
