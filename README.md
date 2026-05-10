# Korean Ecommerce Conversion PDP GPT Image2 Skill

Public Hermes skill for producing Korean ecommerce PDP/detail-page image packages with GPT Image2.

This skill captures a repeatable workflow for:

- source-fact based product detail page regeneration
- natural model lifestyle thumbnails
- conversion-first mobile PDP section flow
- Korean text-in-image GPT Image2 prompts
- contact-sheet QA and selective regeneration
- final thumbnail + stitched PDP packaging
- Obsidian production logging

## Skill

Install/copy this folder into your Hermes skills directory:

```text
skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/SKILL.md
```

Local Hermes path example:

```bash
mkdir -p ~/.hermes/skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2
cp skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/SKILL.md \
  ~/.hermes/skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/SKILL.md
cp -r skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/references \
  ~/.hermes/skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/
```

Then start a new Hermes session so the skill loader can discover it.

## Main Workflow

1. Extract product facts and build an evidence ledger.
2. Create a product identity lock and repeat it in every prompt.
3. Build a v3 conversion flow:
   - model thumbnail
   - 3-second hook
   - buying reasons
   - daily/use imagination
   - strongest visual proof
   - material/finish check
   - size/option confidence
   - use scenes
   - safe trust check
   - final choice
4. Generate square/portrait assets with GPT Image2.
5. Build a contact sheet and QA Korean text, product fidelity, claims, and platform risk.
6. Regenerate only failed panels.
7. Package final thumbnail PNG/JPG, stitched PDP PNG/JPG, contact sheet, and manifest.
8. Save/read back an Obsidian production log.

## Notes

- Do not copy supplier PDP images directly into public output.
- Use source images as evidence and QA baseline only.
- Keep claims conservative: no fake discounts, reviews, rankings, certifications, official affiliations, or unsupported performance guarantees.
- Model thumbnails are useful for SmartStore/general ecommerce conversion, but strict platforms may require product-only representative images.

## Repository Contents

```text
skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/SKILL.md
skills/ecommerce/korean-ecommerce-conversion-pdp-gptimage2/references/prompt-pack-template.md
references/conversion-pdp-reproduction-manual.ko.md
```

## License

MIT
