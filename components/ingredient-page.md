# Biotaderm Ingredient Record Specification

**Version 2, 22 July 2026. Single source of truth.**

*This document supersedes both the Ingredient Record Specification (v1) and the Ingredient Page Template Kit. Those two are retired. Everything needed to produce one ingredient page record now lives here: the build target, the component model, the disciplines, the canonical values and the output format.*

*To use it: hand this document to Claude in a fresh chat, name the ingredient, and point at the project's evidence-graded reference for that ingredient. Claude returns a paste-ready record sheet in the format defined in section 8.*

---

## 1. How to use this in a future chat

1. Provide this spec and name the ingredient.
2. Make sure the project's evidence-graded reference is available (the Multi Review or Ingredient Reference files). Claude grounds every claim in it and does not write from memory.
3. Claude reads the reference, picks the archetype, drafts the fields per the disciplines in section 6, grades each claim, and returns the record sheet.
4. Before finalising, Claude flags any provenance, form or evidence conflict rather than assuming past one (section 6.3). Bladderwrack is the cautionary case: the material is a UK oil infusion, not a French aqueous extract, which changed both the source line and what could be claimed.

The governing principle for the whole page: nothing here is meant to be padded out. If a module has nothing true to say for a given ingredient, leave it off. An honest short page beats a padded long one, and on this brand the short page is often the more persuasive.

---

## 2. The build target

The page renders from one content metaobject, `ingredient_blog_meta`, which the article references through a single metafield `custom.ingredient_blog_meta`. A second shared metaobject, `ethos_icon`, holds the ethos icons. The theme section resolves the record once with `article.metafields.custom.ingredient_blog_meta.value` and reads each field as `mf.<key>`.

### `ingredient_blog_meta` fields

| Field | Key | Type | Req |
| --- | --- | --- | --- |
| Eyebrow chips | `chipy` | List · single line | ✓   |
| Botanical name | `botanical_name` | Single line | ✓   |
| INCI (pure, no brackets) | `inci` | Single line | ✓   |
| Standfirst lead | `standfirst_lead` | Multi-line | ✓   |
| Standfirst emphasis | `standfirst_emphasis` | Single line | ✓   |
| Photo | `photo` | File (image) | ✓   |
| Photo alt / caption | `photo_alt_caption` | Single line | ✓   |
| What it is (body) | `what_it_is_body` | Multi-line | ✓   |
| At a glance: role | `at_a_glance_role` | Single line | ✓   |
| At a glance: source | `at_a_glance_source` | Single line | ✓   |
| At a glance: processing | `at_a_glance_processing` | Single line | ✓   |
| At a glance: also known as | `at_a_glance_also_known_as` | Single line | ✓   |
| Function intro | `function_intro` | Single line | ✓   |
| Function card title | `function_card_title` | List · single line | ✓   |
| Function card body | `function_card_body` | List · single line (HTML) | ✓   |
| Function card chip text | `function_card_chip_text` | List · single line | ✓   |
| Function card chip colour | `function_card_chip_colour` | List · colour | ✓   |
| Modest bonus | `modest_bonus` | Multi-line | –   |
| Teardown intro | `teardown_intro` | Multi-line | –   |
| Teardown marketed as | `dont_claim_marketed_as` | List · single line | –   |
| Teardown correction | `dont_claim_correction` | List · single line (HTML) | –   |
| Teardown closing | `teardown_closing` | Multi-line | –   |
| On the label (body) | `on_the_label_body` | Multi-line | ✓   |
| Label string | `label_string` | Single line | ✓   |
| Label highlight term | `label_highlight_term` | Single line | ✓   |
| Label note | `label_note` | Multi-line | –   |
| Suitability (body) | `suitability_body` | Multi-line | ✓   |
| Suitability chip text | `suitability_chip_text` | List · single line | ✓   |
| Suitability chip colour | `suitability_chip_colour` | List · colour | ✓   |
| Patch-test line | `patch_test_line` | Single line | –   |
| Ethos icons | `ethos` | List · metaobject → `ethos_icon` | ✓   |
| Reference citation | `reference_citation` | List · single line (HTML) | ✓   |
| Reference link | `reference_link` | List · URL | ✓   |
| Footer scope line | `footer_scope_line` | Single line | ✓   |

The article title carries the common name and the handle carries the slug, so those are not fields. `chipy` is the real key for the eyebrow chips, an odd spelling that the section matches. Leave it unless the field and the liquid are renamed together.

### `ethos_icon` fields

| Field | Key | Type |
| --- | --- | --- |
| Icon | `icon` | Image (File) |
| Label | `label` | Single line text |
| Colour | `colour` | Color |

---

## 3. How the repeating groups work

Four groups are parallel lists walked by index, so within a group every list stays in the same order and length: **function cards** (`function_card_title` + `_body` + `_chip_text` + `_chip_colour`), **teardown** (`dont_claim_marketed_as` + `_correction`), **references** (`reference_citation` + `reference_link`), and **suitability chips** (`suitability_chip_text` + `_colour`).

A function card with no evidence tag takes `N/A` as its `function_card_chip_text`, with any colour to hold the slot, and the section hides it. Single-line list bodies (`function_card_body`, `dont_claim_correction`, `reference_citation`) hold inline HTML on one line, no block tags. Multi-line fields hold their own block HTML (`<p>`, `<em>`, `<a>`) and are output raw.

---

## 4. The component model

The page is a fixed spine with a few optional modules that turn on or off by ingredient. The spine never changes, so every page feels like part of one library. The modules are where an ingredient gets to be itself.

Each component below gives its keys, its target length, and the one rule that matters most for it.

### 4.1 Breadcrumb and eyebrow chips (required)

Two or three short descriptors telling the reader what kind of ingredient this is before they read a word. Tara used *Texture ingredient · Galactomannan · In every formula*.

- **Keys:** `chipy`. The breadcrumb label is the article title.
- **Length:** 2 to 3 chips, each 1 to 3 words.
- **Rule:** the chips classify, they do not sell. *Signature algae*, *Prebiotic*, *Hero oil* are fine. *Miracle*, *powerhouse* are not.

### 4.2 Name and subtitle (required)

- **Keys:** `botanical_name`, `inci`. The H1 common name is the article title.
- **Rule:** common name in the H1 so it is human, botanical and INCI in the subtitle so it is precise. The subtitle INCI stays pure, no brackets.

### 4.3 Standfirst (required)

One or two short paragraphs saying, in plain terms, what this ingredient is here to do, closing on a single emphasised line that states the honest headline.

- **Keys:** `standfirst_lead`, `standfirst_emphasis`.
- **Length:** lead 40 to 60 words; emphasis line 12 to 20 words.
- **Rule:** the emphasis line is where the archetype declares itself. Texturiser: *a texture ingredient, not an active*. Hero oil: *the oil this skin type is built around*. Never overreach here. The reader trusts or bounces on this line.

### 4.4 Ingredient photo (required)

A single image of the raw ingredient, sitting between the standfirst and the anchor nav, with a caption beneath it.

- **Keys:** `photo`, `photo_alt_caption`.
- **Length:** one line.
- **Caption:** the caption is the alt text. Write it once. That keeps the page accessible, gives search something honest to read, and spares maintaining two strings that drift. The same field feeds both.
- **Rule:** describe the actual material plainly, not the mood. *Tara gum, the purified seed powder, milled cold, and nothing else* does the job. Let it carry a quiet point about the ingredient where it can.

### 4.5 Section anchor nav (required, automatic)

Lists only the sections actually present. If the teardown module is off, its tab disappears. No manual copy.

### 4.6 What it is, and the At a glance card (required)

- **Keys:** `what_it_is_body`; `at_a_glance_role`, `at_a_glance_source`, `at_a_glance_processing`, `at_a_glance_also_known_as`.
- **Length:** body 1 to 2 paragraphs. Card values are short phrases.
- **Rule:** introduce any technical term the moment it is used (galactomannan, palmitoleic acid), the way a good chemist would to a curious customer. Research language throughout.

### 4.7 What it does in our formulas (required)

One to three function cards, each a single claim with a plain one-line explanation and an optional evidence tag.

- **Keys:** `function_intro`; `function_card_title`, `function_card_body`, `function_card_chip_text`, `function_card_chip_colour`; `modest_bonus` optional.
- **Length:** intro one line. Card titles short, bodies one line.
- **Evidence tags:** case by case, not on every page. Never invent a grade. Use `N/A` to hide a tag while keeping the lists aligned.
- **Modest bonus:** an optional callout for a real but minor, early-evidence benefit deliberately not headlined. Use sparingly. It is a trust device, not a second helping of claims.
- **Rule:** every card must survive a sceptic reading the reference behind it. If it would not, soften it or cut it.

### 4.8 What the research does not show (optional)

The teardown. An intro line plus one to three *Marketed as X* accordion items, each opening to where the claim actually comes from.

- **Keys:** `teardown_intro`, `dont_claim_marketed_as`, `dont_claim_correction`, `teardown_closing`.
- **When to use it:** when the ingredient carries real, sourceable overclaims circulating in the market, or when the supplied form does not carry the benefits the published literature describes. Tara, argan, most superfruit ingredients and bladderwrack all qualify. A straightforward active often does not.
- **Length:** marketed claim 2 to 4 words; correction 1 to 3 sentences, sourced to the real material or plant part.
- **Rule:** name the claim, then name where it really comes from, calmly. No competitor names, no sneer. The tone is a chemist setting the record straight, not a brand scoring points. Corrections point outward at the market, never inward at the library.

### 4.9 On the label and in the range (required)

Body plus a card showing how the ingredient reads on a real label, with the ingredient highlighted.

- **Keys:** `on_the_label_body`, `label_string`, `label_highlight_term`, `label_note`.
- **Length:** body 1 paragraph; note one line.
- **Rule:** `label_highlight_term` must match the label entry exactly, brackets and all, or the mark will not land. Point to the product pages for exact percentages rather than repeating them here. Naming rules are in section 6.5.

### 4.10 Is it suitable for me? (required)

Body on tolerance and safety, plus suitability chips and the ethos icon row.

- **Keys:** `suitability_body`, `suitability_chip_text`, `suitability_chip_colour`, `ethos`, `patch_test_line`.
- **Length:** body 1 paragraph; 2 to 4 suitability chips; exactly 3 ethos icons.
- **Rule:** state tolerance, do not promise outcomes. Avoid *non-comedogenic* unless the evidence is clean, which it is not for argan. The patch-test line runs on anything touching sensitive skin.

### 4.11 The research behind this page (required)

The fixed discipline line, then numbered references.

- **Keys:** `reference_citation`, `reference_link`.
- **Fixed line, never altered:** *We review the published literature. We do not conduct the studies below.*
- **Length:** 3 to 6 references, full citation with DOI link.
- **Rule:** independent sources first, supplier documents last and clearly marked. This line is the whole research-integrity promise in one sentence, and it appears on every page unchanged.

### 4.12 Footer CTA band (required)

- **Keys:** `footer_scope_line`.
- **Rule:** the scope line must be literally true per ingredient. *Found in every Biotaderm formulation*, or *Found in the Balanced and Oily ranges* where an ingredient is not universal. Not everything is in every formula.

---

## 5. Canonical values

### Ethos library

Eight records exist. Each page references the three most appropriate. The set is settled.

| Label | Colour | Icon file |
| --- | --- | --- |
| Gentle, skin friendly | #627879 | GentleColour.svg |
| Microbiome friendly | #963C3D | MicrobiomeColour.svg |
| Climate Clear | #68903C | ClimateClearColour.svg |
| Formulation Clear | #8A9CA2 | FormulationClearColour.svg |
| Cruelty Free | #A0AF99 | CrueltyColour.svg |
| Natural | #7BB65C | NaturalColour.svg |
| Evidence-led | #D15A63 | ScienceColour.svg |
| Business Clear | #6B6E31 | EthicalColour.svg |

Pick the three that genuinely fit the ingredient, ingredient-descriptive icons first (Natural, Gentle skin friendly, Microbiome friendly, Evidence-led), with the brand-wide ones (Cruelty Free, Climate Clear, Formulation Clear, Business Clear) filling the third slot when the descriptive pool is thin. Never claim an ethos the ingredient has not earned. Tara gum takes Natural and Gentle skin friendly honestly, but not Microbiome friendly, since its page says plainly that the microbiome claims belong elsewhere.

Two icon filenames differ from their labels: Evidence-led is ScienceColour.svg, Business Clear is EthicalColour.svg.

### Chip colours

One colour per label, held across the whole library. When a new label appears, give it one colour and add it here so it stays fixed everywhere.

**Evidence chips**, by strength tier:

| Text | Colour |
| --- | --- |
| Well characterised | #68903C (green) |
| Small sensory studies | #9A8F2E (amber) |
| Emerging evidence | #9A8F2E (amber) |

**Suitability chips:**

| Text | Colour |
| --- | --- |
| Vegan-friendly | #68903C |
| Sensitive-skin suitable | #627879 |
| No known safety concerns | #6B6E31 |

---

## 6. Disciplines (non-negotiable)

These sit above every field and override any wording that drifts.

### 6.1 Voice

The Quiet Chemist: precise, transparent, warm, dry understatement, no superlatives. UK English. No em dashes. Vary sentence length. Personality is allowed but the register stays sober.

Understating a real benefit is as much an accuracy failure as overstating one, so grade honestly in both directions.

Restraint is shown, not stated. No line praises the brand for its own honesty or accuracy, and no line casts doubt on another page, another ingredient or our own discipline. Teardown corrections point outward at the market, never inward at the library.

*Support, not control* is available as a motif where it fits naturally, not as a slogan to bolt on.

### 6.2 Claims and research language

Biotaderm reviews the published science; it does not run it. Use "the research shows", "studies suggest", "the evidence points to". Never "our research", "we've proven" or "clinically tested".

The fixed research line under references is: *We review the published literature. We do not conduct the studies below.*

No medical, anti-ageing, sebum-control or microbiome-treatment claims. Microbiome language is always support, never treat or balance.

Grade evidence quality plainly, well characterised against emerging, and translate the internal grade into that plain signal rather than exposing the rubric. The public page never shows Strong, Moderate, Limited or Insufficient.

Every claim traces to a reference in section 4.11. If it cannot, it does not go on the page.

### 6.3 Trace every claim to the actual material

The single most important claims rule. A benefit only belongs on the page if it holds for the ingredient in the exact form supplied. Check form (oil infusion against aqueous or fucoidan-rich extract; the water-soluble actives do not partition into an oil), plant part (seed oil against peel or pod), and route (topical against oral).

Where the supplied form differs from the studied form, the headline benefits usually do not transfer, and that belongs in the teardown, not the function cards. Flag any such mismatch to Richard before finalising.

### 6.4 Coastal sourcing

For the algae only, the Devon coast is kinship and inspiration, never supply chain. Use "the same Atlantic species we know from our coast". Never "harvested from our shores" or "wild-gathered". Nothing else on the site gets a coastal line.

State the true provenance of the material and never guess it. If the source documents disagree, and some still say "produced in France" for a UK-supplied material, flag it rather than pick one.

### 6.5 INCI and label formatting

The label card shows how the ingredient reads on a real pack: a genuine slice of one product's INCI list, a few names either side of the ingredient, with an ellipsis at each end.

Names take the on-pack bracketed form, common name between the botanic name and the form: Helianthus Annuus (Sunflower) Seed Oil, Caesalpinia Spinosa (Tara) Gum. An ingredient with a common name but no form suffix takes the bracket at the end: Tocopherol (Vitamin E). Plain chemicals carry none.

This bracketed form appears on the label card only. The `inci` field and the subtitle stay pure INCI. `label_highlight_term` must match the label entry exactly, brackets and all.

Source of truth for names is the May 2026 Product Labels document. Spelling watch: Vetiveria Zizanioides (not Zizanoides), Rosa Canina (Rose Hip) Seed Oil (not Fruit Oil).

### 6.6 Fragrance and allergens

Never write *fragrance-free* and never write *essential-oil-free*, anywhere on any page. The range contains vetiver. The accurate claim is *no synthetic fragrance*.

### 6.7 No fabrication

Never invent a citation, author, title or statistic. Apply the same scepticism to any AI-synthesis output (SciSpace and similar) as to marketing copy. If a figure or source cannot be verified in the primary reference, leave it out. State evidence gaps rather than filling them from adjacent literature.

---

## 7. Archetypes

Four moulds. They share the spine and differ in which optional modules run and where the emphasis sits. Pick the closest, then adjust.

**A. Supporting and texturiser.** Gums, emulsifiers, buffers, preservation components, glycerin. Headline is texture or function, not treatment. Function cards describe formulation jobs. Teardown usually **on**, since these are the ingredients the market most oversells. Evidence tags modest and often well characterised on the mechanical claims. Suitability leans on the long food and cosmetic safety record. Tara is the exemplar.

**B. Plant oil.** The hero oils per family: evening primrose, jojoba, rose hip, grape seed, pomegranate, baobab, tamanu, argan, sea buckthorn. Headline is what this oil is made of and why that suits this skin. Function cards on barrier support, feel and fatty-acid profile. Teardown usually **off**, with two exceptions: argan, where non-comedogenic must not be claimed because its oleic acid can raise permeability, and any oil sold on a superfruit reputation where the actives sit in the peel or juice rather than the seed. Evidence tags optional. Coastal line off.

**C. Pre/postbiotic and functional actives.** Inulin, ferments, allantoin, gluconolactone, chlorella. Headline is supports the skin's own microbiome, with the still-developing evidence said out loud rather than hidden. Function cards cautious. Teardown usually **off**, with the honesty handled inline in the body. Never imply live cultures for a postbiotic. Allantoin carries the honesty line that it is usually synthesised.

**D. Signature algae.** Bladderwrack, and chlorella where framed as signature. Headline carries the coastal kinship, stated as kinship not sourcing, always paired with the true provenance. Grade strictly by form: an oil infusion carries mainly lipophilic material, principally fucoxanthin, giving a genuine but modest antioxidant character, while the water-soluble fucoidan and phlorotannin benefits stay in the aqueous literature. Those do not go in the function cards. Teardown is **on**, and it is where the form mismatch is explained. Bladderwrack is the exemplar.

---

## 8. Output format

Return a single markdown record sheet with these sections, in this order.

1. **Title and intro line** naming the ingredient and its archetype.
2. **Order of entry:** reuse the existing ethos library, create the `ingredient_blog_meta` record, link it to the article. Include the full eight-record ethos library table only on the first record of a build; later records just reference the three chosen.
3. **Single-line and list-of-string fields**, as a plain `` - `key`: value `` list. List-of-string values shown pipe-separated for reading, with a note that they are entered as separate list items. `ethos` names the three chosen icons.
4. **Function cards** as a table: `#`, `function_card_title`, `function_card_body`, `function_card_chip_text`, `function_card_chip_colour`.
5. **Suitability chips** as a table: `#`, `suitability_chip_text`, `suitability_chip_colour`.
6. **Teardown** as a table, omitted if the module is off: `#`, `dont_claim_marketed_as`, `dont_claim_correction`.
7. **References** as a table: `#`, `reference_citation`, `reference_link`.
8. **Multi-line body fields**, each in a fenced ```html block with the block HTML written in: `standfirst_lead`, `what_it_is_body`, `on_the_label_body`, `suitability_body`, and any of `modest_bonus`, `teardown_intro`, `teardown_closing` that are used.
9. **The article:** title, handle, template `article.ingredient`, and the `custom.ingredient_blog_meta` link.
10. **Search fields:** SEO title in the form *[Common] ([Botanical]) | Biotaderm*; meta description under 160 characters; slug in the form `/blogs/ingredients/[common-name-hyphenated]`.
11. **Notes as you enter it:** provenance, form and claims flags, plus the label-slice source and any spelling watch.

The two worked examples, the Tara record (archetype A, teardown on) and the bladderwrack record (archetype D, oil-infusion honesty), are the reference for tone and shape.

---

## 9. Blank fill-in worksheet

*Copy this block per ingredient. Leave optional fields empty to switch a module off.*

```
COMMON NAME:
BOTANICAL (italic):
INCI (pure, no brackets):
ARCHETYPE (A/B/C/D):
CHIPS (2–3, 1–3 words each):

STANDFIRST LEAD (40–60 words):
STANDFIRST EMPHASIS LINE (12–20 words):

PHOTO — image file:
PHOTO ALT TEXT (one line, doubles as the caption):

WHAT IT IS — BODY (1–2 paras):
AT A GLANCE:
  Role:
  Source:
  Processing:
  Also known as:

WHAT IT DOES — intro line:
  CARD 1  title / one-line body / chip text + chip colour (or N/A to hide):
  CARD 2  title / one-line body / chip text + chip colour (or N/A to hide):
  CARD 3  title / one-line body / chip text + chip colour (or N/A to hide):
  MODEST BONUS (optional) — one short para:

WHAT THE RESEARCH DOES NOT SHOW (optional — leave blank to omit):
  intro line:
  Marketed as ___ / correction:
  Marketed as ___ / correction:
  Marketed as ___ / correction:
  closing line:

ON THE LABEL — body (1 para):
  real INCI slice from one product, ellipsis each end, on-pack bracket form:
  highlight term (must match the label entry exactly, brackets and all):
  where-it-sits note:

SUITABILITY — body (1 para):
  suitability chips (2–4), each text + colour:
  ethos icons (exactly 3, from the settled library):
  patch-test line (sensitive-touching ingredients only):

REFERENCES (3–6, independent first, supplier last, with DOI):
  1.
  2.
  3.

FOOTER SCOPE LINE (must be literally true):

SEO TITLE:  [Common] ([Botanical]) | Biotaderm
META DESCRIPTION (<160 chars):
SLUG:  /blogs/ingredients/[common-name-hyphenated]

FLAGS FOR RICHARD (provenance / form / evidence conflicts):
```
