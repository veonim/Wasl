# Design language

[One sentence: where the visual direction comes from, and the decision that set it.]

## Character

- **[Quality].** [What it means for this product.]

## Tokens

### Colour

| Token | Value | Use |
| --- | --- | --- |
| `--[name]` | `[#hex]` | [Where it is used] |

### Type

| Token | Family | Size | Weight | Use |
| --- | --- | --- | --- | --- |
| `h1` | [Family] | [Size] | [Weight] | Page title |
| `body` | [Family] | [Size] | [Weight] | Body |

### Shape and spacing

| Token | Value | Use |
| --- | --- | --- |
| `radius-md` | [px] | [Use] |
| `space-md` | [rem] | [Use] |

### CSS variables

```css
:root {
  --[name]: [value];
}
```

## Components

| Component | Specification |
| --- | --- |
| Primary button | [Fill, text, radius, height, when to use] |

## States

| State | Treatment |
| --- | --- |
| Hover | [ ] |
| Focus | [ ] |
| Selected | [ ] |
| Disabled | [ ] |
| Error | [ ] |
| Loading | [ ] |
| Empty | [ ] |

## Motion

[Where motion is used, where it is not, and the reduced-motion rule.]

## Accessibility

- Text contrast at least 4.5:1.
- Touch targets at least 44px.
- State never shown by colour alone.

## Departures from the reference

| Reference | This project | Why |
| --- | --- | --- |
| [What the reference says] | [What we do instead] | [Reason] |

## Do and do not

- Do [ ].
- Do not [ ].
