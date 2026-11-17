# UI design

The screens are drawn on a design canvas outside this repository. This folder records where it is, what has been drawn and the design language the frontend must follow, so the build does not depend on anyone remembering the canvas.

| File | Holds |
| --- | --- |
| [design-language.md](design-language.md) | The working specification: tokens, glass recipes, components, states, motion, graph requirements, right-to-left rules |
| [reference.md](reference.md) | The SUMMIT reference supplied by the product owner, verbatim |

**Canvas:** https://claude.ai/artifact/WgUcH6u95rWf43shSzK2w3 (private to its owner until shared)

**Status:** all MVP screens drawn in the SUMMIT style as a first draft. Not yet reviewed, and not checked as rendered.

## Screens drawn

All content on the canvas is invented sample data. The currency shown (Rs) is a placeholder; the target country is undecided (Q-01).

### Browse and trust

| Screen | Artboard | Shows |
| --- | --- | --- |
| Cause page | `Main` | Trust panel with two paths, the case, the full case record, donate card, presenter card, sharing |
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
| Present a cause | `Submit` | The five-part form: the case in both languages, beneficiary and consent, money breakdown, case documents with publish choice, private identity and bank details |
| Assisted submission | `AssistedSubmit` | Staff entering a cause on a presenter's behalf, with the confirm-before-review rule |
| Presenter dashboard | `PresenterDashboard` | A live cause with status steps, raised, paid out and available, the proof-of-use deadline; a cause with changes requested; finished cases |
| Payout and proof of use | `Disbursement` | The proof-of-use form, the payout request locked until proof is posted, payout history |

### Donor

| Screen | Artboard | Shows |
| --- | --- | --- |
| Donation complete | `DonationSuccess` | Confirmation, fee breakdown, the path the donor gave through |
| Donor history | `DonorHistory` | Totals and a table of donations with path, proof-of-use status and receipt |

### Staff

| Screen | Artboard | Shows |
| --- | --- | --- |
| Verifier queue | `VerifierQueue` | Filter tabs and the table of causes waiting, with flags |
| Verifier review | `VerifierReview` | The case and evidence beside the baseline checklist, notes and the three decisions |
| Admin console | `Admin` | Payout approvals, a reported cause with donations paused, the latest audit log entries |

## Not drawn

These are covered by the design language and existing screens, and have no artboard of their own.

- **Urdu versions of most screens.** Three phone screens are drawn in Urdu. Every other screen mirrors by the rules in the design language.
- **Phone layouts of most screens.** Pages are fluid and stack; only three phone layouts are drawn explicitly.
- **Donation failure and cancel pages.** Same layout as Donation complete with different copy.
- **Password reset.** Same layout as Sign in.
- **Admin sub-pages:** users, causes, refunds and the full audit log. They use the table and list-row components.
- **Error, loading and empty states**, which are specified in the design language.
- **A logo.** The wordmark is a placeholder (Q-10).

## Known limits of the canvas

- **The graphs are static placeholders.** They show the visual style only. The build must render real, data-driven, interactive graphs; the requirements are in [design-language.md](design-language.md#graphs).
- **Nothing is interactive.** Buttons, filters and forms do not respond.
- **Motion is not shown** beyond hover lifts.
- **The Urdu copy was machine-written** and needs a native reader.
