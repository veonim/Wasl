# Design language

Wasl's design language is the SUMMIT glassmorphism reference supplied by the product owner (decision D-011), applied to a donation platform. The reference itself is kept verbatim in [reference.md](reference.md). This file is the working specification: every screen and every component in the build follows it.

## Character

From the reference: glassmorphism, light mode, keywords *altitude, parallax, peak*. Density 5 of 10, variance 6 of 10, motion 8 of 10.

For Wasl this means:

- **Light and airy.** A pale sky ground with a warm glow, like first light on a ridge. Content floats on frosted glass above it.
- **One dark ink.** Deep navy carries text, primary actions and trust links. There is no second brand colour.
- **Warmth marks what matters.** The warm glow colour is reserved for selection, positive status and the single most important surface on a page.
- **Serif voice.** Georgia gives the product a considered, trustworthy tone, closer to a letter than an app.
- **Calm where money and evidence are involved.** Glass and glow set the mood; forms, tables and review screens stay plain and legible.

## Tokens

### Colour

| Token | Value | From reference | Use |
| --- | --- | --- | --- |
| `--ink` | `#0c1420` | primary | Text, primary buttons, trust links, progress fill, the viewer's node, staff header |
| `--sky` | `#e8eef8` | secondary | Page ground, quiet badges, text on the dark staff header |
| `--steel` | `#8fa4c4` | tertiary | Borders on inputs and secondary controls, table header rules, thin graph lines, dashed upload areas |
| `--glow` | `#ffd9a0` | palette | Selected states, positive and current-step badges, callouts, glow shadows |
| `--haze` | `#a9bcd8` | palette | Background gradient only |
| `--ink-muted` | `#42546F` | derived | Secondary text, captions, hints |
| `--ink-soft` | `#1f2c40` | derived | Long body copy on glass |
| `--white` | `#FFFFFF` | derived | Text on ink |

Derived values exist because `--steel` fails contrast as a text colour. See Departures.

### Background

One page background everywhere:

```css
background:
  radial-gradient(900px 520px at 88% -6%, rgba(255,217,160,0.9) 0%, rgba(255,217,160,0) 62%),
  radial-gradient(900px 700px at -5% 35%, rgba(169,188,216,0.9) 0%, rgba(169,188,216,0) 65%),
  linear-gradient(180deg, #e8eef8 0%, #d3dff0 100%);
```

The warm glow sits at the top end corner, the haze at the start side. In right-to-left layouts the two swap sides. On a phone the radii shrink to about 420px.

### Type

| Token | Family | Size | Weight | Use |
| --- | --- | --- | --- | --- |
| `h1` | Georgia | 2.5rem (40px), line height 1.15 | 700 | Page title |
| `h2` | Georgia | 1.375rem to 1.5rem | 700 | Card and section titles |
| `body-md` | Georgia | 1rem (16px), line height 1.5 | 400 | Body |
| `body-lg` | Georgia | 1.125rem to 1.1875rem | 400 | Lead sentences, the trust sentence |
| `caption` | Georgia | 0.875rem | 400 | Hints, table headers, metadata |
| `figure` | Georgia | 1.5rem to 2rem | 700 | Amounts and counts |
| `label-ui` | system-ui | 0.875rem | 400 to 600 | Small uppercase labels, timestamps, codes |
| Urdu, all roles | Noto Nastaliq Urdu | same sizes | 400 to 700 | Line height about 2.2; headings about 2.0 |

- Font stack for English: `Georgia, 'Times New Roman', serif`.
- Emphasis is weight 700, not colour.
- Amounts use Western digits in both languages.
- No text below 13px.

### Shape

| Token | Value | Use |
| --- | --- | --- |
| `rounded-sm` | 4px | Progress segments, small marks |
| `rounded-md` | 8px | Buttons, inputs, inset panels, list rows |
| `rounded-lg` | 16px | Cards, dialogs, navigation panels |
| `rounded-full` | 999px | Pills, chips, avatars, graph nodes |

### Spacing

Base scale from the reference: `sm` 1rem, `md` 2rem, `lg` 4rem.

| Use | Value |
| --- | --- |
| Page gutter | 24px desktop, 16px phone |
| Card padding | 28px desktop, 16px phone |
| Gap between cards | 24px |
| Gap between fields | 16 to 18px |
| Label to control | 6px |
| Page top and bottom padding | 40px and 80px |

Content widths: 1200px for browsing and consoles, about 860px for forms, about 480px for sign-in.

### Depth

| Level | Recipe | Use |
| --- | --- | --- |
| Glass | fill `rgba(255,255,255,0.55)`, `backdrop-filter: blur(18px)`, border `1px solid rgba(255,255,255,0.75)`, shadow `0 8px 32px rgba(12,20,32,0.10)` | Every card |
| Glass, raised | fill `rgba(255,255,255,0.62)`, `blur(22px)`, border `rgba(255,255,255,0.9)`, shadows `0 18px 60px rgba(255,217,160,0.45)` and `0 8px 32px rgba(12,20,32,0.12)` | The one focal surface on a page |
| Header | fill `rgba(255,255,255,0.5)`, `blur(18px)`, bottom border `rgba(255,255,255,0.75)` | Public and member header |
| Inset | fill `rgba(232,238,248,0.7)`, no blur, radius 8px | Panels inside a card |
| Control | fill `rgba(255,255,255,0.6)`, border `1px solid #8fa4c4` | Inputs, secondary buttons, list rows |
| Alert outline | glass with `2px solid #0c1420` | A card that needs a decision or carries a warning |

**One raised surface per page.** It is the trust panel on a cause page, the active task on a dashboard, the decision form on a review screen.

Where `backdrop-filter` is unsupported, raise the glass fill to `rgba(255,255,255,0.85)`.

### CSS variables

```css
:root {
  --ink: #0c1420;
  --ink-soft: #1f2c40;
  --ink-muted: #42546F;
  --sky: #e8eef8;
  --steel: #8fa4c4;
  --glow: #ffd9a0;
  --haze: #a9bcd8;
  --glass: rgba(255,255,255,0.55);
  --glass-raised: rgba(255,255,255,0.62);
  --glass-border: rgba(255,255,255,0.75);
  --inset: rgba(232,238,248,0.7);
  --control: rgba(255,255,255,0.6);
  --rule: rgba(12,20,32,0.12);
  --shadow: 0 8px 32px rgba(12,20,32,0.10);
  --shadow-glow: 0 18px 60px rgba(255,217,160,0.45);
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;
  --font-serif: Georgia, 'Times New Roman', serif;
  --font-urdu: 'Noto Nastaliq Urdu', serif;
  --font-ui: system-ui, sans-serif;
}
```

These map directly to the Tailwind theme in `apps/web`. Components use the tokens, never raw hex values.

## Components

| Component | Specification |
| --- | --- |
| Primary button | `--ink` fill, white text, weight 700, radius 8px, height 52px (48px in dense rows). One per form or card. |
| Secondary button | Control fill, steel border, ink text, weight 700, radius 8px, height 48px. |
| Disabled button | Fill `rgba(143,164,196,0.2)`, steel border, muted text, `not-allowed` cursor. Always paired with a line saying what unlocks it. |
| Text input, select, textarea | Control fill, steel border, radius 8px, height 48px, 14px side padding. Label above in weight 700 at 15px; hint below in caption. |
| Choice card (radio) | A full-width row with radio, title and description. Selected: glow fill and `2px` ink border. |
| Checkbox row | 20px box, text beside it, whole row at least 44px tall. |
| Chip, filter | Pill, 44px tall. Selected: glow fill, `2px` ink border, weight 700. Unselected: control fill, steel border. |
| Badge, status | Pill, 13px, weight 700. Positive or current: glow fill. Neutral or pending: sky fill with steel border. On a card: ink fill with white text. |
| Card | Glass, radius 16px, 28px padding, title in `h2`. |
| Callout | Glow fill with `2px` ink border for something the user must act on; inset fill for information. |
| Stat tile | Inset panel: caption above, figure below. |
| Progress bar | Track `rgba(143,164,196,0.3)`, ink fill, 8 to 10px tall, fully rounded. Always with the numbers in text. |
| Stepper | Equal segments 4px tall. Done: ink. Current: glow with a glow shadow and a bold label. Upcoming: steel at low opacity. |
| Table | No outer border. Header in caption, muted, with a steel rule beneath. Rows divided by `--rule`. Amounts end-aligned. Wrapped in a horizontally scrolling box. |
| List row | Control fill, `--rule` border, radius 8px, title in weight 700 with a caption line. |
| Upload area | Inset fill with a dashed steel border, a title, a hint and a secondary button. |
| Dialog | A glass card, raised when it is the focus. Used for setting trust, inviting and endorsing. |
| Member header | Glass header: wordmark at the start, navigation, language switch, account. |
| Staff header | Solid ink with white text and "Wasl staff". Staff screens are visibly different from member screens. |
| Wordmark | وصل in Noto Nastaliq Urdu beside "Wasl" in Georgia 700. A logo is still an open question (Q-10). |
| Photo placeholder | Until real photography exists: a tinted panel with a dashed border and a label. |

Icons are simple line icons, 2px stroke, ink colour. No emoji.

## States

| State | Treatment |
| --- | --- |
| Hover, button | Lifts 1px with shadow `0 6px 20px rgba(12,20,32,0.16)`, over 200ms. |
| Hover, link | Colour shifts from ink to muted. Links stay underlined. |
| Focus | A visible 2px ink outline with a 2px offset on every interactive element. |
| Selected | Glow fill plus a `2px` ink border. Never colour alone. |
| Disabled | Low-opacity steel fill, muted text, with the reason stated nearby. |
| Error | `2px` ink border on the field, a message in ink weight 700 beneath, and a line icon. No red: the palette has none, and errors must not rely on colour. |
| Loading | Glass skeleton blocks pulsing between two opacities. |
| Empty | A sentence saying what will appear here and one action to make it happen. |

## Motion

The reference is animated. Wasl keeps the character and limits where it runs.

| Where | Motion |
| --- | --- |
| Page background | The glow and haze drift slowly, a few percent of the viewport over 20 to 30 seconds, and shift slightly on scroll for a parallax feel. |
| Cards | Fade and rise 8px on first appearance, staggered by 60ms. |
| Buttons and cards | Hover lift, 200ms ease. |
| Trust panel | Path links draw from the viewer outward, 400ms per link. |
| Graph | Nodes ease into position on load and when depth changes. |
| Success | The confirmation mark glows in once. |

Rules:

- No motion on forms while typing, on tables, or on the verifier and admin screens beyond hover.
- Everything is disabled under `prefers-reduced-motion`; content appears in its final state.
- Nothing loops except the background drift.

## Graphs

**A graph in Wasl is a real graph.** It is rendered from the API's nodes and links with a computed layout, and it responds to the person using it. A static picture of pills joined by lines is not acceptable in the build. The graphs on the design canvas are placeholders that show the visual style only.

Requirements for the trust panel graph and the My network graph:

| Area | Requirement |
| --- | --- |
| Data | Drawn from the nodes and links the API returns for this viewer. No hand-placed positions, no hard-coded people. |
| Layout | Computed. Radial by distance from the viewer by default: the viewer at the centre, one ring per link of distance. The same data always gives the same picture. |
| Direction | Links are directed. An arrowhead or taper shows who trusts whom. |
| Level | Line weight shows the trust level: thin for *know*, medium for *trust*, thick for *would vouch by name*. |
| Nodes | The viewer: solid ink with a glow. Directly trusted people: glow fill, ink border. Further people: glass with a steel border. Presenters: ink outline. Causes: a distinct shape attached to their presenter. |
| Pan and zoom | Drag to pan, scroll or pinch to zoom, with a fit-to-view control. |
| Highlight | Hovering or focusing a node highlights every path from the viewer to it and dims the rest. |
| Select | Clicking or tapping a node opens a card: the path in words, their causes, and the control to set trust. |
| Expand | A node can be expanded to load its neighbours, within the depth limit and the visibility rules. |
| Depth | A control switches between one, two and three links and re-lays the graph. |
| Scale | Stays readable with hundreds of nodes: distant nodes cluster, labels appear by zoom level, and layout runs off the main thread if needed. |
| Privacy | Shows only what the viewer is entitled to see. "Only you see this view" is stated on the screen. |
| Words | Every graph has an equivalent list view, and the trust panel leads with the path as a sentence. |
| Keyboard | Nodes are reachable and operable by keyboard. |
| Languages | Mirrored in Urdu, with the viewer's side swapped. Labels use the Urdu face. |
| Motion | Nodes ease into place; off under reduced motion. |
| Style | Glass, ink and glow from this file. The graph sits on an inset panel inside a glass card. |

The library is chosen in module M3. Cytoscape.js is the working candidate.

## Right-to-left and Urdu

- The whole layout mirrors: start and end swap, the background glow and haze swap sides, directional icons flip.
- Use logical properties only (`margin-inline-start`, `text-align: start`). Never left or right.
- Urdu uses Noto Nastaliq Urdu at line height about 2.2. Controls keep their height; Nastaliq needs the extra leading inside them.
- Amounts and Latin names inside Urdu text are wrapped so they keep left-to-right order.
- On a phone the trust path stacks vertically, which reads the same in both directions.

## Accessibility

- Text contrast at least 4.5:1 on the glass it sits on; 3:1 for text 24px and larger.
- Touch targets at least 44px.
- State is never shown by colour alone: selection adds a border and weight, levels use line weight, status uses words.
- Real buttons, links, inputs and labels.
- Pages are fluid. Side columns stack under content on a phone, toolbars wrap, tables scroll inside their own box.
- Glass must stay legible over the brightest part of the background; if it does not, raise the fill opacity.

## Departures from the reference

| Reference | Wasl | Why |
| --- | --- | --- |
| Tertiary `#8fa4c4` as a general colour | `#42546F` for secondary text; `#8fa4c4` for borders and lines only | `#8fa4c4` on light glass fails 4.5:1 contrast |
| Georgia everywhere | Noto Nastaliq Urdu for Urdu | Georgia has no Urdu glyphs |
| Motion 8 of 10 | Motion on the background, entrances, the trust panel and the graph; none on forms, tables or staff screens | Money and evidence screens must stay calm and readable |
| Writing mode and CSS filters listed as features | Not used | No need has come up; vertical text does not suit Urdu or forms |
| No error colour in the palette | Errors use an ink border, bold text and an icon | Keeps to the palette and does not rely on colour |

## Do and do not

- Do keep one raised glass surface per page.
- Do use the glow colour sparingly: selection, positive status, one callout.
- Do put the numbers next to every progress bar and the words next to every graph.
- Do not introduce new colours. If a state seems to need one, use border, weight or an icon.
- Do not stack glass on glass more than one level; use an inset panel inside a card.
- Do not animate anything a person is reading or typing into.
- Do not ship a graph that is a static drawing.
