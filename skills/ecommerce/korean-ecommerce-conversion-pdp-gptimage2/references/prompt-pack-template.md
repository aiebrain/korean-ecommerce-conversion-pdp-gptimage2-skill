# Conversion PDP Prompt Pack Template

Use this JSON-like structure to build a product-specific prompt pack.

```json
{
  "product_no": "<product_code>",
  "version": "v3_conversion",
  "strategy": "model thumbnail + hook -> buying reasons -> use imagination -> proof -> risk reduction -> trust -> final choice",
  "identity_lock": "CRITICAL PRODUCT IDENTITY LOCK ...",
  "claim_rules": [
    "No price/discount/review/ranking/fake certification",
    "Use confirmation language for material/function/license",
    "No unsupported performance claims"
  ],
  "prompts": [
    {
      "section_id": "00_thumbnail_conversion_model",
      "aspect": "square",
      "role": "representative",
      "approved_text": [],
      "visual_direction": "natural fitting model lifestyle thumbnail with product-native marks only",
      "prompt": "..."
    },
    {
      "section_id": "01_hook_why_buy",
      "aspect": "portrait",
      "role": "stop",
      "approved_text": ["한 장으로 완성되는 <상품 무드>", "앞은 깔끔하게", "뒤는 확실하게"],
      "visual_direction": "hero section with product/model and immediate reason to care",
      "prompt": "..."
    }
  ]
}
```

## QA Prompt

```text
QA this Korean ecommerce PDP contact sheet. Check conversion flow, Korean text readability/typos/pseudo Hangul, product consistency, unsafe claims, fake badges, platform risks, severe crop/layout. Return panel-by-panel PASS/CONDITIONAL/REGENERATE and note if any image should be regenerated.
```
