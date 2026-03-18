# Design Spec — stefanschmitt.biz v8

## Farbpalette

### Hintergrund & Oberflächen
- **Page Background**: `#f4f4f5` (Zinc-100, warmes Hellgrau)
- **Card Background**: `#ffffff` (Weiß)
- **Inline-Elemente** (Stats, Programme-Badges, Tech-Tags): `#f4f4f5` (gleich wie Page-BG)

### Text
- **Primary** (Überschriften, Namen, Bold): `#18181b` (Zinc-900, fast schwarz)
- **Mid** (Fließtext, Beschreibungen): `#3f3f46` (Zinc-700)
- **Muted** (Subtexte, Meta): `#71717a` (Zinc-500)
- **Dim** (Zeiträume, Badges, Fußzeile): `#a1a1aa` (Zinc-400)

### Akzentfarben (für Section-Borders links an Cards)
- **Blau** `#2563eb` / BG `#dbeafe` — Experience
- **Grün** `#059669` / BG `#d1fae5` — Speaking
- **Amber** `#d97706` / BG `#fef3c7` — Teaching
- **Violet** `#7c3aed` / BG `#ede9fe` — Projects & Education
- **Slate** `#64748b` — References

### Borders
- **Standard**: `#e4e4e7` (Zinc-200)
- **Hover**: `#d4d4d8` (Zinc-300)

---

## Typografie

### Font
- **Family**: `Inter` (Google Fonts), Fallback: `-apple-system, BlinkMacSystemFont, sans-serif`
- **Weights geladen**: 400, 500, 600, 700

### Größen & Gewichte

| Element | Size | Weight | Color | Anmerkung |
|---|---|---|---|---|
| Hero-Name (h1) | 26px | 700 | --text | `letter-spacing: -0.5px` |
| Card-Titel (Org-Namen) | 17px | 700 | --text | `letter-spacing: -0.3px` |
| Speaking-Titel | 20px | 700 | --text | `letter-spacing: -0.3px` |
| Teaching Org-Name | 15px | 600 | --text | |
| Hero-Subtitle | 14px | 400 | --text-muted | |
| Fließtext (Hero Intro) | 15px | 400 | --text-mid | `line-height: 1.75` |
| Card Fließtext | 14px | 400 | --text-mid | `line-height: 1.7` |
| Teaching Text | 13px | 400 | --text-mid | `line-height: 1.7` |
| Rollen-Name | 14px | 600 | --text (erste Rolle: --blue) | |
| Rollen-Zeitraum | 11px | 400 | --text-dim | `font-variant-numeric: tabular-nums` |
| Org-Beschreibung | 12px | 400 | --text-muted | |
| Stat-Zahl | 17px | 700 | --text | `letter-spacing: -0.5px` |
| Stat-Label | 10px | 400 | --text-dim | |
| Topic-Titel | 14px | 600 | --text | |
| Topic-Beschreibung | 12px | 400 | --text-muted | `line-height: 1.55` |
| Event-Pill | 12px | 500 | --text-mid | |
| Programme-Badge | 10px | 600 | --text-dim | `uppercase, letter-spacing: 0.3px` |
| CTA-Button | 14px | 600 | weiß auf --text | |
| Profil-Links | 14px | 400 | --text-mid | |
| Status-Badge | 12px | 500 | --green | |
| Referenz-Zitat | 14px | 400 | --text-mid | `italic, line-height: 1.75` |
| Referenz-Name | 13px | 600 | --text | |
| Referenz-Rolle | 11px | 400 | --text-dim | |
| Footer | 12px | 400 | --text-dim | |

### Bold-Regeln
- **700 (Bold)**: Nur Hero-Name, Org-Namen (BD, FS), Speaking-Titel, Stat-Zahlen, Projekt-Name, Logo-Initialen
- **600 (Semibold)**: Rollen-Namen, Teaching-Org, Topic-Titel, Referenz-Name, CTA-Button, Profil-Status, Programme-Badges
- **500 (Medium)**: Event-Pills, Status-Badge
- **400 (Regular)**: Alles andere (Fließtext, Beschreibungen, Zeiträume, Zitate)

---

## Spacing & Layout

### Grid
- **Max-Width**: 1060px
- **Card Gap**: 12px
- **Padding Page**: 28px oben, 16px seitlich, 24px unten

### Card-Innen
- **Standard-Padding**: 28px
- **Hero-Padding**: 32px
- **Topic-Card Padding**: 18px horizontal, 20px vertikal
- **Border-Radius**: 14px

### Section-Border
- **Breite**: 3px links
- **Farbe**: je nach Section (siehe Akzentfarben)

### Hintergrund-Muster
- Karo/Grid: horizontale + vertikale Linien
- **Farbe**: `rgba(0,0,0,0.04)` (4% Schwarz)
- **Größe**: 24px × 24px Raster
- **Technik**: Zwei überlagerte `linear-gradient` auf dem `body`

---

## Bento-Grid Spaltenverteilung

| Reihe | Links | Rechts | Verhältnis |
|---|---|---|---|
| Hero + Profil | Hero: 7 cols | Profil: 5 cols | Links breiter |
| Experience | BD: 6 cols | FS: 6 cols | Gleich |
| Speaking | Topics gestapelt: 4 cols | Speaking-Main: 8 cols | **Rechts breiter** |
| Teaching | FS: 6 cols | ETS: 6 cols | Gleich |
| Education + Projekt | Edu: 4 cols | Hiremark: 8 cols | **Rechts breiter** |
| Referenzen | Ref 1: 4 cols | Ref 2: 4 cols | Ref 3: 4 cols | Gleich |

---

## Interaktionen

### Hover
- **Cards**: Nur `border-color` wird leicht dunkler (#e4e4e7 → #d4d4d8). Kein translateY, kein Shadow, kein Scale.
- **Profil-Links**: Textfarbe wechselt zu --blue
- **CTA-Button**: `opacity: 0.85`
- **Section-Border links bleibt IMMER** in der Sektionsfarbe (auch bei Hover)

### Animation
- Cards faden beim Scrollen ein: `opacity: 0 → 1`, `translateY(8px) → 0`
- Duration: 0.4s ease
- Trigger: IntersectionObserver bei 8% Sichtbarkeit

### Status-Dot
- Grüner Punkt neben "Open to speaking" pulst sanft
- `animation: pulse 2.5s ease-in-out infinite` (Opacity 1 → 0.35 → 1)

---

## Inhaltliche Entscheidungen

- **Kein Nav-Bar**: Bento beginnt direkt oben
- **Kein Contact-Section**: Kontakt ist im Profil-Card oben rechts
- **Kein X/Twitter**: Nur Email + LinkedIn
- **Kein Calendly**: Speaking-Anfragen über Email (mailto mit Subject)
- **Kein Slider**: Referenzen alle sichtbar nebeneinander
- **Keine Section-Labels**: Farbige linke Borders zeigen Zugehörigkeit
- **Speaking CTA**: Schwarzer Button "Invite me to speak →" (nicht Akzentfarbe)
- **Podcasts**: kursiv dargestellt in Event-Liste
- **Erste Rolle bei BD**: in Blau hervorgehoben (aktuellste Position)
