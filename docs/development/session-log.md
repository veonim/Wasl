# Session log

Append-only. One entry per working session, newest at the bottom. Keep entries short: what was done, what was decided, what is next. Detail belongs in the module files and design docs.

## Entry format

```text
## YYYY-MM-DD: short title

**Module:** M? or "design"
**Done:** what was finished, with task IDs
**Decided:** decision IDs added or changed, or "nothing"
**Left open:** anything half-finished or newly discovered
**Next:** the next task
```

---

## 2026-11-16: design and project setup

**Module:** design
**Done:**
- Wrote the product and architecture design: overview, flows, trust model, seeding plan, system, data model, API, languages, repo and tooling, payments, security and compliance.
- Set up the docs as the source of truth, with `CLAUDE.md` as the anchor.
- Created the development process, roadmap, six module files, decision log and open-questions list.

**Decided:** D-001 to D-010. Fifteen standing assumptions recorded (A-01 to A-15).
**Left open:** The design is a first draft and has not been reviewed by the product owner. Twenty-two open questions (Q-01 to Q-22).
**Next:** `M1-T01`, repository scaffold.

## 2026-11-16: first UI screens

**Module:** design
**Done:**
- Drew four screens on the design canvas: cause page (desktop, English), causes listing, My network, cause page (phone, Urdu).
- Added `docs/design/README.md` with the canvas link, the screens drawn and still to draw, and the colour, type and trust-graph conventions.

**Decided:** nothing confirmed. The palette, typefaces and graph conventions are a working proposal pending Q-10 (brand).
**Left open:** The screens were not checked as rendered and have not been reviewed. The Urdu copy needs a native reader. Eleven groups of screens are still to draw.
**Next:** review of the four screens, then the sign-up, submission and no-path screens; or `M1-T01` if build starts first.

## 2026-11-16: SUMMIT design reference applied

**Module:** design
**Done:**
- Saved the product owner's SUMMIT glassmorphism reference verbatim in `docs/design/reference.md`.
- Restyled the four canvas screens to it: navy, pale blue and warm glow palette, Georgia type, glass cards with backdrop blur.
- Rewrote the visual rules in `docs/design/README.md`, including the glass recipes and three departures from the reference made for contrast, Urdu type and calm motion.

**Decided:** D-011, visual design follows the SUMMIT reference. Q-10 narrowed to logo only.
**Left open:** The restyled screens were not checked as rendered. Motion is specified but only hover states are drawn.
**Next:** review of the four screens, then the sign-up, submission and no-path screens in the same style.

## 2026-11-17: remaining screens and design language

**Module:** design
**Done:**
- Drew the remaining 16 screens in the SUMMIT style: sign-up, sign-in, verify, trust panel states, trust actions, submission form, assisted submission, presenter dashboard, payout and proof of use, donation complete, donor history, verifier queue, verifier review, admin console, and two more phone layouts. The canvas now holds 20 artboards.
- Wrote `docs/design/design-language.md`: tokens, glass recipes, components, states, motion, graph requirements, right-to-left rules, departures from the reference.
- Rewrote `docs/design/README.md` as the screen inventory with what is not drawn and the limits of the canvas.
- Added design tokens and base components as task `M1-T13a`, and split the graph work in M3 into a shared graph component plus its two uses.

**Decided:** D-012, graphs must be real, data-driven, interactive graphs. The product owner asked that the canvas graphs not be rebuilt now; they stay as style placeholders.
**Left open:** Screens not checked as rendered and not reviewed. Urdu copy needs a native reader. Urdu and phone versions exist for only a few screens; the rest follow the design language.
**Next:** design review, then `M1-T01`.
