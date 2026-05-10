---
name: korean-ecommerce-conversion-pdp-gptimage2
description: "Use when creating or improving Korean ecommerce PDP/detail-page images with GPT Image2 for higher purchase conversion: source-fact extraction, natural model thumbnails, conversion-first section flow, Korean text-in-image prompts, contact-sheet QA, selective regeneration, stitching, and Obsidian logging."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [korean-ecommerce, pdp, detail-page, gpt-image2, conversion, smartstore, coupang, obsidian]
    related_skills: [ebrain-detail-page-builder, obsidian]
---

# Korean Ecommerce Conversion PDP with GPT Image2

## Overview

Use this skill to reproduce the quality of the ROKA v3 conversion-focused detail page: a Korean ecommerce thumbnail plus a long stitched PDP made from GPT Image2-generated sections. The workflow is optimized for Korean SmartStore/general mall conversion while keeping platform and legal-risk claims under control.

The deliverable is not just a set of pretty images. It is a complete production package:

1. source-fact and evidence ledger
2. conversion-first section structure
3. natural model lifestyle thumbnail
4. Korean text-in-image prompt pack
5. raw and accepted section images
6. contact sheet QA
7. selective regeneration for failed panels
8. final thumbnail PNG/JPG
9. final stitched PDP PNG/JPG
10. manifest and Obsidian production log

## When to Use

Use when the user says things like:

- `구매전환을 높게 나오도록 상세페이지 다시 제작해봐`
- `지금 상세페이지와 같은 퀄리티로 다시 만들 수 있게 해줘`
- `썸네일에는 제품과 어울리는 모델이 들어가게 해줘`
- `GPT Image2로 한글이 들어간 상세페이지 섹션 만들어줘`
- `스마트스토어용 전환형 상세페이지 제작해줘`
- `기존 공급사 이미지를 그대로 쓰지 말고 정보 기반으로 새로 만들어줘`

Do not use this as-is for strict legal/spec tables, medical/regulated claims, or marketplace pages where product rights cannot be verified. In those cases, first build a safer evidence ledger and ask for missing compliance data only if it materially changes the output.

## Core Principles

1. **Source images are evidence, not final artwork.** Do not copy/crop/paste supplier detail-page images as the final design. Use them to verify product facts, OCR size/material claims, and build the product identity lock.
2. **Thumbnail defaults to natural model lifestyle.** For this workflow, the preferred main thumbnail uses a model that fits the product and creates purchase imagination. Keep a product-only white-background thumbnail only when the target platform requires it.
3. **The first three sections sell the page.** Start with hook, buying reasons, and daily/use imagination before moving into material, size, and trust checks.
4. **Every prompt repeats product identity.** GPT Image2 can drift across sections. Repeat silhouette, color, logos, options, and what the product is not in every prompt.
5. **Korean text must be QA'd visually.** GPT Image2 can produce plausible-looking but wrong Korean. Use contact sheet QA and regenerate only failed panels.
6. **Claims stay conservative.** No price, discount, fake reviews, ranking, fake certification, official affiliation, or unsupported performance guarantees.
7. **Finish with files and logs.** The task is not complete until final images, manifest, QA result, and Obsidian log are saved and read back.

## Default Folder Structure

Create a product harness folder under the user's project or Obsidian assets directory:

```text
Assets/<product_code>_<Product>_Regenerated_PDP_Harness/
  00_harness_v3_conversion/
    prompt-pack-v3-conversion.json
    evidence-ledger.json
    qa-rubric.yaml
  01_raw_generations_v3_conversion/
    00_thumbnail_conversion_model.png
    01_hook_why_buy.png
    ...
  02_accepted_sections_v3_conversion/
    accepted section copies
  04_final_v3_conversion/
    <product>_v3_conversion_thumbnail_model.png
    <product>_v3_conversion_thumbnail_model.jpg
    <product>_v3_conversion_full_detail_page.png
    <product>_v3_conversion_full_detail_page.jpg
    <product>_v3_conversion_contact_sheet.jpg
    manifest.json
```

## Evidence Ledger

Before writing prompts, classify every product fact:

```yaml
confirmed_from_page_text:
  - product name
  - options
  - visible marketplace facts
confirmed_from_source_image_ocr:
  - material wording
  - size table
  - finish/print/components wording
confirmed_from_visual_inspection:
  - silhouette
  - color
  - logo and print placement
  - front/back/side details
safe_general:
  - daily styling
  - gifting
  - outdoor/general use scenes
needs_confirmation:
  - performance figures
  - certification
  - license/IP rights
blocked:
  - official supply claims
  - lowest price / No.1 / fake reviews
  - UV/cooling/sweat-drying guarantees without evidence
```

For risky source wording, convert to confirmation language:

- Prefer: `상세 이미지에 쿨론 표기 확인`
- Prefer: `기능성 수치는 상품정보를 확인하세요`
- Avoid: `쿨론이라 시원합니다`, `빠르게 마릅니다`, `공식 인증 제품입니다`

## Product Identity Lock

Build a product-specific block and repeat it in every section prompt.

Template:

```text
CRITICAL PRODUCT IDENTITY LOCK
- Product category: <exact category>.
- Color/material/finish: <source-confirmed visual details>.
- Front/side/back identifiers: <logos, prints, patches, buttons, labels>.
- Options/components: <only source-confirmed options/components>.
- Do NOT change into: <wrong product forms/categories>.
- Do NOT add: <extra patches/logos/certifications/components>.
- If using a model: <normal lifestyle model rules; no unsafe/official implication>.
```

## Conversion Section Flow

Use this as the default v3 conversion structure. Adjust labels and count by product, but preserve the psychology.

| no | section | role | image goal |
|---:|---|---|---|
| 00 | thumbnail_conversion_model | representative | natural model wearing/using product, square |
| 01 | hook_why_buy | stop | 3-second reason to care |
| 02 | buying_reasons | reason | feature-to-benefit detail cards |
| 03 | daily_fit_or_use | imagination | normal usage/fit scene |
| 04 | strongest_visual_proof | desire/proof | strongest product visual enlarged |
| 05 | material_finish_safe | trust | material/finish checks without guarantees |
| 06 | size_option_confidence | reduce risk | size/options/components and tolerance |
| 07 | use_scenes | deepen | where the product fits in life |
| 08 | safe_trust_check | compliance/trust | official/function/license/certification cautions |
| 09 | final_choice | convert | final recap and pre-purchase checklist |

## Prompt Template

Each image prompt should use this shape:

```text
DELIVERABLE
- Korean ecommerce conversion-focused PDP image.
- Section id: <section_id>
- Aspect: square or portrait.
- Create a NEW generated sales image from product facts. Do NOT copy supplier images, crops, layout, or old text artifacts.

CONVERSION ROLE
- <section role and buyer objection answered>

CRITICAL PRODUCT IDENTITY LOCK
- <product-specific lock>

VISUAL DIRECTION
- <model/product/card composition>
- Premium Korean ecommerce design, high contrast, clean accent colors.
- Mobile-readable bold Korean sans-serif typography.

EXACT TEXT TO RENDER
- <line 1>
- <line 2>
- <line 3>

STRICT TEXT RULES
- Render ONLY the exact text above plus product-native logos/prints.
- Do not add extra Korean words, English slogans, prices, badges, ratings, or CTA buttons.

CLAIM / PLATFORM RULES
- No price, no discount, no review count, no ranking, no fake certification, no award, no official supply claim.
- Use 확인/표기/구매 전 확인 language for material, function, certification, officialness, license.
- No random Korean, no pseudo Hangul, no watermark, no tool UI.
```

## Copy Patterns

### Thumbnail
No added headline. Product-native print/logo only. Model and back/detail inset are allowed when useful.

### Hook
- `한 장으로 완성되는 <상품 무드>`
- `앞은 깔끔하게`
- `뒤는 확실하게`
- `<핵심 카테고리>`

### Buying Reasons
- `구매 이유는 디테일에 있습니다`
- `<전면 포인트>`
- `<후면/핵심 기능 포인트>`
- `<소매/옵션/구성 디테일>`

### Daily Fit / Use Imagination
- `데일리룩에도 자연스럽게`
- `<색상/형태로 코디는 쉽게>`
- `<과하지 않은 포인트>`
- `<강한 포인트>`

### Material / Finish Safe
- `디테일까지 꼼꼼하게 확인`
- `원단 질감 확인`
- `봉제 마감 확인`
- `전·후면 프린팅 확인`

### Size / Option Confidence
- `사이즈 실패를 줄이는 실측 체크`
- `<옵션 범위>`
- `<대표 치수 range>`
- `1~2cm 오차 가능`

### Safe Trust Check
- `구매 전 꼭 확인하세요`
- `<공식/인증 오해 방지 문구>`
- `<기능성 수치 확인 문구>`
- `<상표·라이선스/주의사항 확인 문구>`

## Generation Runtime Pattern

When the Hermes OpenAI/Codex provider is available, use it directly:

```python
import importlib, os, shutil, sys
from pathlib import Path

repo = Path('/home/aiebrain/.hermes/hermes-agent')
sys.path.insert(0, str(repo))
os.chdir(repo)
os.environ['OPENAI_IMAGE_MODEL'] = 'gpt-image-2-medium'

mod = importlib.import_module('plugins.image_gen.openai-codex')
provider = mod.OpenAICodexImageGenProvider()
res = provider.generate(prompt, aspect_ratio='portrait')
if not res.get('success'):
    raise RuntimeError(res)
shutil.copy2(Path(res['image']), output_path)
```

Recommended aspects:

- thumbnail: `square` → 1024x1024
- detail section: `portrait` → 1024x1536

## Packaging

Use PIL to create:

- thumbnail PNG and JPG
- stitched full PDP PNG and JPG
- contact sheet JPG
- manifest.json

Rules:

- The stitched PDP should usually include sections 01~09, not the thumbnail.
- Resize each section to width 1024 before stitching.
- JPG quality 92, progressive.
- Contact sheet includes 00~09 for QA.
- Verify with `file` and `du -h`.

## QA Protocol

### Contact Sheet QA

Ask vision QA:

```text
QA this Korean ecommerce PDP contact sheet. Check conversion flow, Korean text readability/typos/pseudo Hangul, product consistency, unsafe claims, fake badges, platform risks, severe crop/layout. Return panel-by-panel PASS/CONDITIONAL/REGENERATE and note if any image should be regenerated.
```

### Thumbnail QA

Ask vision QA:

```text
QA this final thumbnail only. Requirements: natural model lifestyle thumbnail, square, product consistency, no added marketing text/price/badge/fake certification/reviews/weapons/uniform implication. Verdict PASS/CONDITIONAL/REGENERATE.
```

### Regenerate If

- key Korean copy is misspelled
- pseudo Hangul or unclear generated terms appear
- product category or identity drifts
- fake certification, price, ranking, or review appears
- official affiliation or unsupported performance is implied
- severe crop/layout/watermark/tool UI appears

### Conditional Accept If

- minor label duplication exists but meaning is safe
- small non-critical text is imperfect
- platform-specific alternative may be needed, but the general PDP is safe

## Obsidian Log Requirements

Save a production log with:

- stated goal
- current/vPrevious diagnosis
- vNew conversion strategy
- source-fidelity lock
- prompt pack path
- generated file paths
- dimensions and file sizes
- QA results
- regeneration history
- final cautions

Read back the note before reporting completion.

## Common Pitfalls

1. **Making a product-only thumbnail when the user wants conversion emotion.** For this user's ecommerce PDP flow, default to natural fitting model lifestyle unless platform rules require product-only.
2. **Copying supplier detail pages.** Do not reuse old layouts/text artifacts; regenerate from source facts.
3. **Forgetting the product identity lock.** GPT Image2 may change garment type, package, color, logo placement, or options if not constrained in every prompt.
4. **Trusting Korean text without QA.** Always contact-sheet QA. Regenerate unclear words such as pseudo-Korean fragments.
5. **Making safety copy sound like internal QA.** Customer-facing trust copy should be clear and natural: `구매 전 꼭 확인하세요`, not overly bureaucratic.
6. **Overclaiming material/function.** If a source says `쿨론`, do not claim cooling/quick-dry without evidence. Use `표기 확인` or `상품정보 확인` language.
7. **Ignoring platform differences.** SmartStore/general mall can use model lifestyle thumbnails; Coupang may need product-only white-background variants.
8. **Skipping manifest and logs.** Without manifest, paths, QA, and regeneration history, the workflow is not reproducible.

## Verification Checklist

- [ ] Source facts and visual identity were extracted.
- [ ] Evidence ledger separates confirmed, visual, safe-general, needs-confirmation, and blocked claims.
- [ ] Product identity lock exists and is repeated in every prompt.
- [ ] Thumbnail prompt uses natural fitting model unless strict platform requires product-only.
- [ ] Section flow covers hook, buying reasons, use imagination, proof, risk reduction, trust, and final choice.
- [ ] Prompt pack saved under `00_harness_v3_conversion/`.
- [ ] All section images generated and copied to raw/accepted folders.
- [ ] Final thumbnail PNG/JPG and stitched PDP PNG/JPG created.
- [ ] Contact sheet and manifest created.
- [ ] `file` and `du -h` verification completed.
- [ ] Contact sheet QA completed.
- [ ] Failed panels regenerated and contact sheet rebuilt.
- [ ] Final thumbnail QA completed.
- [ ] Obsidian log written and read back.
