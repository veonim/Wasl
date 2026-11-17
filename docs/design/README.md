# UI design

The screens are drawn on a design canvas outside this repository. This folder records where it is, what has been drawn and the design language the frontend must follow, so the build does not depend on anyone remembering the canvas.

| File | Holds |
| --- | --- |
| [design-language.md](design-language.md) | The working specification: tokens, glass recipes, components, states, motion, graph requirements, right-to-left rules |
| [reference.md](reference.md) | The SUMMIT reference supplied by the product owner, verbatim |

**Canvas:** https://claude.ai/artifact/WgUcH6u95rWf43shSzK2w3 (private to its owner until shared)

**Status:** all MVP screens drawn in the SUMMIT style as a first draft. Not yet reviewed, and not checked as rendered.

**Core rule shown on every money-related screen:** no money flows through Wasl (D-013). Screens show the presenter's payment details and a record of gifts; none of them takes a payment.

## Screens drawn

All content on the canvas is invented sample data. The currency shown (Rs) is a placeholder; the target country is undecided (Q-01).

### Browse and trust

| Screen | Artboard | Shows |
| --- | --- | --- |
| Cause page | `Main` | Trust panel with two paths, the case, the full case record, the give card (confirmed total, the no-money statement, the presenter's payment details with account title, "I have given"), presenter card, sharing |
| Causes listing | `Home` | Search, filters, sort by closeness, cards with a trust chip for connected and unconnected causes |
| My network | `Network` | The viewer's graph to two links, link levels, people who trust you, causes within reach |
| Cause page, phone, Urdu | `MobileUrdu` | Right-to-left layout, Nastaliq type, trust path stacked vertically, case record summary |
| Causes listing, phone, Urdu | `MobileHomeUrdu` | Search, filter chips and cause cards in Urdu |
| My network, phone | `MobileNetwork` | Graph and list toggle, radial graph, selected-person card |

### Accounts and trust actions

| Screen | Artboard | Shows |
| --- | --- | --- |
| Sign up | `SignUp` | Account fields, language choice, the introduced-by field |
| Sign in | `SignIn` | Email or phone and password, note on the staff second step |
| Verify phone | `Verify` | Three-step progress and the code entry |
| Trust panel states | `TrustStates` | Signed in with no path, guest, and the notice when a vouch on the path has failed before |
| Trust actions | `TrustControls` | Setting a trust level, inviting someone, endorsing a cause |

### Presenter

| Screen | Artboard | Shows |
| --- | --- | --- |
| Present a cause | `Submit` | The five-part form: the case in both languages, beneficiary and consent, money breakdown, case documents with publish choice, identity for the reviewer, and the payment details donors will use |
| Assisted submission | `AssistedSubmit` | Staff entering a cause on a presenter's behalf, with the confirm-before-review rule |
| Presenter dashboard | `PresenterDashboard` | A live cause with status steps; amounts confirmed received, waiting to be confirmed and accounted for; the proof-of-use deadline; a cause with changes requested; finished cases |
| Gifts and proof of use | `GiftsProof` | Gifts reported by donors for the presenter to confirm or mark not received, adding an unrecorded gift, and the proof-of-use form |

### Donor

| Screen | Artboard | Shows |
| --- | --- | --- |
| Record a gift | `RecordGift` | The donor records a gift they sent directly: amount, date, method, reference, optional proof; what happens next; the path kept with the gift |
| Donor history | `DonorHistory` | Totals and a table of recorded gifts with path, whether the presenter confirmed, and proof-of-use status |

### Staff

| Screen | Artboard | Shows |
| --- | --- | --- |
| Verifier queue | `VerifierQueue` | Filter tabs and the table of causes waiting, with flags |
| Verifier review | `VerifierReview` | The case and evidence beside the baseline checklist, notes and the three decisions |
| Admin console | `Admin` | Changed payment details waiting for a check, a reported cause with its payment details hidden, the latest audit log entries |

## Not drawn

These are covered by the design language and existing screens, and have no artboard of their own.

- **Urdu versions of most screens.** Three phone screens are drawn in Urdu. Every other screen mirrors by the rules in the design language.
- **Phone layouts of most screens.** Pages are fluid and stack; only three phone layouts are drawn explicitly.
- **Presenter's payment methods screen** and the **gift recorded confirmation**. They use the form and callout components.
- **Disputed gifts** in the admin console.
- **Password reset.** Same layout as Sign in.
- **Admin sub-pages:** users, causes and the full audit log. They use the table and list-row components.
- **Error, loading and empty states**, which are specified in the design language.
- **A logo.** The wordmark is a placeholder (Q-10).

## Known limits of the canvas

- **The graphs are static placeholders.** They show the visual style only. The build must render real, data-driven, interactive graphs; the requirements are in [design-language.md](design-language.md#graphs).
- **Nothing is interactive.** Buttons, filters and forms do not respond.
- **Motion is not shown** beyond hover lifts.
- **The Urdu copy was machine-written** and needs a native reader.
