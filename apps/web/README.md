# Wasl web app

Next.js app: every screen for donors, presenters, verifiers and admins, in English and Urdu with right-to-left layout. It holds no business logic and talks only to the Wasl API.

**Status:** placeholder. The app is created in module M1:

| Task | Adds |
| --- | --- |
| `M1-T13` | Next.js app with TypeScript, Tailwind and the base layout |
| `M1-T13a` | Design tokens and base components from the [design language](../../docs/design/design-language.md) |
| `M1-T14`, `M1-T15` | English and Urdu routes, language switcher, right-to-left layout |
| `M1-T16` | API client generated from the OpenAPI schema |
| `M1-T17`, `M1-T18` | Sign-up, sign-in, verification, password reset, signed-in shell |

Target layout, from [repository and tooling](../../docs/architecture/05-repo-and-tooling.md):

```text
apps/web/
  src/app/[locale]/   routes: public, donor, presenter, verifier, admin
  src/components/
  src/lib/api/        client generated from OpenAPI
  messages/           en.json, ur.json
```

Tooling: pnpm, TypeScript, ESLint, Prettier, Vitest, Playwright.
