# Biotaderm Design System

A working design system for **Biotaderm** (the trading name of Welcombe Skincare), handmade in Welcombe, north Devon. It exists to keep everything Biotaderm makes visually and verbally consistent, and to give Claude Design a faithful brief to work from.

This is a distilled first version: the visual and verbal foundations, plus one worked component (the ingredient page). It is built to be extended.

## How to use this in Claude Design

Claude Design builds visuals from written descriptions rather than from an imported token library. So the way to use this system is to give Claude Design the relevant part of it as context, then prototype against it.

1. Upload this folder (or paste the relevant module) at the start of a Claude Design session.
2. Reference the tokens by name. "Use Seaglass `#6BBBCC` for the Balanced skin type" reads better to the tool than a bare hex, because the name carries the rule.
3. State the governing rule up front for anything colour-led: the skin-type hue leads, the style tone supports. See `01-colour.md`.
4. Recommended first prototype: the ingredient page (`components/ingredient-page.md`). It is the most repeatable surface on the site, so it is the highest-leverage thing to get right once.

Two production notes carried over from earlier work. Web SVG coming out of Claude Design needs a cleanup pass (SVGO, a sane `viewBox`, accessibility markup, `currentColor` where colour should inherit) before it goes near the theme. Anything destined for a physical label needs a Figma or Illustrator pass. Claude Design generates from descriptions and cannot vectorise an existing raster file.

## Index

| File | What it covers |
| --- | --- |
| `00-principles.md` | Brand essence, the voice dial, the non-negotiable disciplines |
| `01-colour.md` | Full palette, the two colour axes, the Tide style ramp, ethos-icon colours, usage rules |
| `02-typography.md` | Type families, the full scale, heading colour ramp |
| `03-icons.md` | Icon style, the eight ethos icons, the skin-type icon |
| `04-graphics.md` | The organic interlocking-shapes device |
| `05-photography.md` | The three settings, composition, light, editing |
| `06-layout.md` | Label logic and web layout grammar |
| `components/ingredient-page.md` | The worked component |
| `tokens/tokens.json` | Machine-readable colour and type tokens |
| `OPEN-QUESTIONS.md` | Known inconsistencies and decisions still open |

## Source of truth

Source of truth is split by layer. The Biotaderm Brand Voice Google Doc governs wording and voice. The v2 Ingredient Record Specification governs ingredient page structure, disciplines and canonical values including the ethos library. The Canva Brand Guidelines govern visual style, with the caveat that the July 2026 export is known to be out of date on the ethos set and the bladderwrack provenance. Where this system departs from any of them, it is flagged in `OPEN-QUESTIONS.md` rather than quietly overriding.
