# Colour

## The two axes

Biotaderm's colour system runs on two axes that must never be confused for one another.

- **Skin type is the primary axis.** Each of the five skin types carries a distinct, saturated coastal hue. This hue is load-bearing: it is on the label, and it is how a customer identifies their product. It leads on every surface.
- **Style (Flow / Core / Deep) is the secondary axis.** It is a single low-chroma ramp running light to deep, sitting underneath the skin-type hue and never competing with it. Style is a texture-and-richness signal, not a second identity.

The one rule that prevents collisions: **on any surface, the skin-type hue leads and the style tone supports.** Skin type gets the icon and the accent. Style gets the FLOW / CORE / DEEP wordmark, a thin rule, or a restrained background wash.

## Primary colours

| Name | Hex | Used for |
| --- | --- | --- |
| Seaglass | `#6BBBCC` | Logo, Balanced skin type, website primary, link text |
| Coral | `#F47D5E` | Logo, Dry skin type, website secondary, link hover |
| Tansy | `#C2CA53` | Logo, Oily skin type, website tertiary |
| Black | `#000000` | Company name, print text |

## Skin-type hues (fixed, load-bearing)

| Skin type | No. | Colour | Hex |
| --- | --- | --- | --- |
| Dry Sensitive | 1 | Seakale | `#80A89E` |
| Dry | 2 | Coral | `#F47D5E` |
| Balanced | 3 | Seaglass | `#6BBBCC` |
| Oily | 4 | Tansy | `#C2CA53` |
| Oily Sensitive | 5 | Heather | `#A37594` |

Do not reassign these. They are printed on packaging and customers navigate by them.

## Style ramp: Tide (chosen)

The style axis uses the **Tide** ramp: the muted, weighty end of the north Devon Atlantic that the bright skin-type hues do not occupy. Wet rock, the grey-green swell off Welcombe Mouth, deep water under a flat sky.

| Style | Colour | Hex | Reading |
| --- | --- | --- | --- |
| Flow | Foam | `#D7E0DD` | Lightest formulation, face |
| Core | Tidewater | `#4E6D6C` | Middle, body |
| Deep | Atlantic | `#263E40` | Richest, hands and feet |

**Short leash.** Tide is the most place-rooted of the candidates and the closest to the sea-green skin types, so use it only as a small accent: the wordmark, a thin rule, a restrained wash. Never a large field of it beside a Dry Sensitive or Balanced product, or it blurs into skin type, which is the whole thing this axis is designed to avoid.

### Saved alternatives

Kept on file in case the direction shifts.

- **Driftwood** (warm, earthy): Flow `#E7DFD8`, Core `#876C66`, Deep `#4C3A2E`.
- **Stone** (cool, clinical): Flow `#D9DADB`, Core `#6D6E71`, Deep `#3C3E40`.

## Ethos-icon colours

Each ethos icon is monochrome in a single palette colour, using tints of that colour for fill against outline. Do not recolour them outside these assignments.

| Icon | Colour | Hex |
| --- | --- | --- |
| Microbiome Friendly | Madder | `#963C3D` |
| Gentle, skin friendly | Pebble | `#627879` |
| Climate Clear | Gorse | `#68903C` |
| Formulation Clear | Seamist | `#8A9CA2` |
| Cruelty Free | Lambsear | `#A0AF99` |
| Science Led | Tulip | `#D15A63` |
| Business Clear | Saltmarsh | `#6B6E31` |
| Natural or Naturally Derived | Meadow | `#7BB65C` |

The Natural icon is drawn in green in the guidelines artwork but was never given a named token. Meadow is the one green not otherwise spoken for, so it is the natural home. Watch: Meadow sits close to Gorse (Climate Clear), so keep the two green icons from touching without separation. See `OPEN-QUESTIONS.md`.

## Ink and text tones

Website headings step down through the ink ramp; body sits on Ink Body.

| Role | Name | Hex |
| --- | --- | --- |
| H1 | Ink Black | `#161617` |
| H2 | Ink Deep | `#3F4042` |
| H3 | Ink Strong | `#414245` |
| H4 | Ink Mid | `#4B4C4F` |
| Body | Ink Body | `#494A4D` |

## Backgrounds

| Name | Hex |
| --- | --- |
| Background | `#FFFFFF` |
| GorseBackground | `#FBFBF2` |
| StoneBackground | `#FAF7F5` |
| Oyster (dividers, watermark) | `#E0E1E2` |

## Full secondary palette and tints

Every colour carries a Light and Dark variant for panels and text. The Light variants are saturated pastels for backgrounds and panels; the Dark variants are for text set on the matching Light tint. This is the reference set.

Secondary hues: Saltmarsh `#6B6E31`, Seamist `#8A9CA2`, Seakale `#80A89E`, Madder `#963C3D`, Gorse `#68903C`, Pebble `#627879`, Lambsear `#A0AF99`, Heather `#A37594`, Tulip `#D15A63`.

Logo secondary: Meadow `#7BB65C`, Conker `#BE7346`, Driftwood `#876C66`, Loam `#886B4C`.

Light tints: SaltmarshLight `#F0F2C9`, SeaglassLight `#C4EAF2`, SeamistLight `#CEE9F2`, SeakaleLight `#D8F2EC`, MadderLight `#F2C4C4`, GorseLight `#DDF2C7`, PebbleLight `#C4F0F2`, LambsearLight `#DCF2D3`, HeatherLight `#F2E1ED`, TansyLight `#EFF2C7`, TulipLight `#F2C9CC`, CoralLight `#F2D7D0`.

Dark tones: SaltmarshDark `#323317`, SeaglassDark `#3D6A75`, SeamistDark `#596569`, SeakaleDark `#546E67`, MadderDark `#5C2526`, GorseDark `#3E5624`, PebbleDark `#495A5B`, LambsearDark `#6C7667`, HeatherDark `#86617A`, TansyDark `#525523`, TulipDark `#7A343A`, CoralDark `#9D513D`.

## Usage and accessibility

- Skin-type hue leads, style tone supports. Restated because it is the rule that matters most.
- For text on a colour's Light tint, use that colour's Dark variant, never plain black. Example: text on SeakaleLight `#D8F2EC` uses SeakaleDark `#546E67`.
- Ink tones on white backgrounds for body and headings, per the ramp above.
- The organic-shapes graphic device multiplies where colours overlap. Keep those overlaps as multiply, not opaque stacking. See `04-graphics.md`.
- Do not recolour ethos icons or the graphic device outside the brand palette.
