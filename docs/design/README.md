# UI design

The screens are drawn on a design canvas outside this repository. This file records where it is, what has been drawn, and the visual rules the frontend must follow, so the build does not depend on anyone remembering the canvas.

**Canvas:** https://claude.ai/artifact/WgUcH6u95rWf43shSzK2w3 (private to its owner until shared)

**Status:** first draft, not yet reviewed. No brand identity exists yet (see Q-10 in [open questions](../open-questions.md)); the look below is a working proposal.

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

### Colour

| Token | Value | Use |
| --- | --- | --- |
| Ground | `#F4F6F5` | Page background |
| Surface | `#FFFFFF` | Cards, header |
| Ink | `#12211E` | Body text, the "You" node |
| Muted | `#51605C` | Secondary text |
| Line | `#DCE3E0` | Card borders, dividers |
| Line strong | `#A9B8B3` | Input and secondary button borders |
| Primary | `#0B6E5F` | Buttons, links, trust links, progress |
| Primary dark | `#084F45` | Link hover, text on primary tint |
| Primary tint | `#E3F1EE` | Selected states, positive badges |
| Caution tint | `#FBF0DC` with text `#7A4A00` | "Not yet checked" and similar |

### Type

- English headings: Space Grotesk, 600 to 700
- English body: Inter, 16px base
- Urdu, all text: Noto Nastaliq Urdu, line height about 2.2
- Amounts use Western digits in both languages

### Trust graph conventions

- **Link level is shown by line weight**, never by colour alone: thin grey for *know them*, medium green for *trust them*, thick green for *would vouch by name*.
- **Nodes:** the viewer is a solid dark pill; people the viewer trusts directly are tinted green; people further out are white with a grey border; the presenter has a dark outline.
- **Every graph has the same content in words.** The trust panel leads with a sentence, and the network page offers a list view.
- **The trust panel is the most prominent element on a cause page**, above the story, with a green outline.
- **Privacy is stated in the interface:** "Only you see these paths."
- On a phone the path stacks vertically. In Urdu the layout mirrors.

### Components and accessibility

- Touch targets are at least 44px high.
- Corner radius: 16px for cards, 10 to 12px for controls, full for pills and chips.
- Text contrast is at least 4.5:1.
- Real buttons, links, inputs and labels; no clickable divs.
- Pages are fluid: side columns stack under the content on a phone.
