# UI design

The screens are drawn on a design canvas outside this repository. This file records where it is, what has been drawn, and the visual rules the frontend must follow, so the build does not depend on anyone remembering the canvas.

**Canvas:** https://claude.ai/artifact/WgUcH6u95rWf43shSzK2w3 (private to its owner until shared)

**Design reference:** [reference.md](reference.md), the SUMMIT glassmorphism reference supplied by the product owner (decision D-011). Every screen follows it.

**Status:** first draft in the SUMMIT style, not yet reviewed.

## Screens drawn

| Screen | Canvas artboard | Shows | Spec |
| --- | --- | --- | --- |
| Cause page, desktop, English | `Main` | Trust panel with two paths, the case, the full case record, donate card, presenter card, sharing | [trust model](../product/03-trust-model.md) |
| Causes listing, desktop, English | `Home` | Search, filters, sort by closeness, cards with a trust chip for connected and unconnected causes | [overview](../product/01-overview.md) |
| My network, desktop, English | `Network` | The viewer's graph to two links, link levels, people who trust you, causes within reach | [trust model](../product/03-trust-model.md) |
| Cause page, phone, Urdu | `MobileUrdu` | Right-to-left layout, Nastaliq type, trust path stacked vertically, case record summary | [languages](../architecture/04-languages.md) |

All content on the canvas is invented sample data. The currency shown (Rs) is a placeholder; the target country is undecided (Q-01).

## Screens not yet drawn

- Sign-up, sign-in and verification
- Presenter submission form and dashboard
- Assisted submission (admin)
- Setting a trust level, inviting, endorsing
- Cause page with no path, and the guest view
- Donation return pages and donor history
- Verifier queue and review screen
- Disbursement request and proof-of-use form
- Admin console
- Phone layouts for listing and My network, and Urdu for every screen

## Visual rules

These apply the SUMMIT reference to Wasl. Where the reference and accessibility conflict, the adjustment is listed under "Departures from the reference".

### Colour

| Token | Value | Use |
| --- | --- | --- |
| Primary | `#0c1420` | Text, primary buttons, trust links, progress, the "You" node |
| Secondary | `#e8eef8` | Page ground, quiet badges |
| Tertiary | `#8fa4c4` | Borders on inputs and secondary controls, thin graph lines |
| Glow | `#ffd9a0` | Selected states, positive badges, the glow behind the trust panel |
| Haze | `#a9bcd8` | Background gradient |
| Text muted | `#42546F` | Secondary text (darkened from tertiary for contrast) |
| Text strong muted | `#1f2c40` | Long body copy on glass |

**Page background:** a vertical gradient from `#e8eef8` to `#d3dff0`, with a warm `#ffd9a0` glow at the top end corner and a `#a9bcd8` haze at the start side.

### Glass

| Surface | Recipe |
| --- | --- |
| Card | `rgba(255,255,255,0.55)` fill, `backdrop-filter: blur(18px) saturate(1.2)`, 1px `rgba(255,255,255,0.75)` border, shadow `0 8px 32px rgba(12,20,32,0.10)`, radius 16px |
| Header | `rgba(255,255,255,0.5)` fill, `blur(18px)`, bottom border `rgba(255,255,255,0.75)` |
| Trust panel | Stronger glass: `rgba(255,255,255,0.62)`, `blur(22px)`, plus a `#ffd9a0` glow shadow, so it is the brightest surface on the page |
| Inset fill inside a card | `rgba(232,238,248,0.7)` |
| Control (input, secondary button) | `rgba(255,255,255,0.6)` fill, 1px `#8fa4c4` border |

### Type

- English, headings and body: Georgia. Headings 700; h1 is 2.5rem.
- Urdu, all text: Noto Nastaliq Urdu, line height about 2.2. Georgia has no Urdu glyphs.
- system-ui is the fallback for small Latin interface labels where Georgia reads poorly.
- Amounts use Western digits in both languages.

### Shape and spacing

- Radius: 16px for cards, 8px for controls, 4px for small marks, full for pills and chips.
- Spacing scale: 1rem, 2rem, 4rem, with half steps inside components.

### Motion

The reference is animated (motion 8 of 10). On the canvas only hover lifts and transitions are drawn. In the build:

- Buttons and cards lift slightly on hover with a soft shadow.
- The background glow drifts slowly; graph links draw in when the trust panel appears.
- All motion is disabled under `prefers-reduced-motion`.

### Trust graph conventions

- **Link level is shown by line weight**, never by colour alone: thin for *know them*, medium for *trust them*, thick for *would vouch by name*.
- **Nodes:** the viewer is a solid dark pill; people the viewer trusts directly carry the warm glow fill; people further out are plain glass with a tertiary border; the presenter has a dark outline.
- **Every graph has the same content in words.** The trust panel leads with a sentence, and the network page offers a list view.
- **The trust panel is the most prominent element on a cause page**, above the story.
- **Privacy is stated in the interface:** "Only you see these paths."
- On a phone the path stacks vertically. In Urdu the layout mirrors.

### Accessibility

- Touch targets are at least 44px high.
- Text contrast is at least 4.5:1 against the glass it sits on.
- Real buttons, links, inputs and labels; no clickable divs.
- Pages are fluid: side columns stack under the content on a phone.

### Departures from the reference

| Reference | Wasl | Why |
| --- | --- | --- |
| Tertiary `#8fa4c4` as a text colour | `#42546F` for secondary text | `#8fa4c4` on light glass fails 4.5:1 contrast |
| Georgia everywhere | Noto Nastaliq Urdu for Urdu | Georgia has no Urdu glyphs |
| Heavy animation | Restrained motion, off under reduced-motion | Donation and verification screens must stay readable and calm |
