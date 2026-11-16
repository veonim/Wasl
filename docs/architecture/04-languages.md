# English and Urdu

Both languages ship in the first release, and right-to-left layout is built into the base styles so Urdu is never a retrofit.

- **Routing.** Locale-prefixed URLs, `/en/...` and `/ur/...`, handled by next-intl. The first visit picks from the browser's language; the choice is then saved to a cookie and to the user profile.
- **Direction.** The root element sets `dir="rtl"` for Urdu. All styling uses logical properties (Tailwind `ms-`, `me-`, `ps-`, `pe-`, `text-start`), never left or right. Directional icons such as arrows and chevrons flip; logos and numbers do not. The trust graph view mirrors too, with the viewer on the right in Urdu.
- **Type.** Urdu uses Noto Nastaliq Urdu, self-hosted. Nastaliq needs more line height than Latin text, so Urdu gets its own line-height and font-size scale.
- **Interface text.** Message files per locale in the frontend, `messages/en.json` and `messages/ur.json`. The API returns error codes and message keys, not sentences.
- **User content.** Cause titles, stories and updates live in translation tables. A presenter can write in one language or both. A cause missing a language falls back to the one it has, with a visible note. No machine translation in the MVP.
- **Formats.** Western digits in both languages for amounts, so figures match bank statements. Dates and currency are formatted through `Intl` for the locale.
- **Mixed text.** Fields that can hold either language use `dir="auto"`, so an English name inside an Urdu page renders correctly.
- **Search.** PostgreSQL full-text search uses the `simple` configuration plus trigram matching for Urdu, which has no built-in stemmer.
- **Email.** Templates exist in both languages and are sent in the recipient's saved locale.
- **Share previews.** Generated in the language of the shared link.

## Rule for every change

No user-facing string is merged in one language only. End-to-end tests run in both locales.
