# 2026-05-10 GPT Image2 구매전환형 PDP 재현 매뉴얼

## 목적
이 문서는 이번 ROKA 로카티 v3 상세페이지와 같은 수준의 결과물을 반복 제작하기 위한 운영 매뉴얼이다. 목표는 단순히 예쁜 이미지를 만드는 것이 아니라, 다음 조건을 동시에 만족하는 `구매전환형 한국 이커머스 상세페이지`를 재현하는 것이다.

- 제품 사실 기반
- 자연스러운 모델 착용형 썸네일
- 모바일 스크롤 전환 구조
- 한글 텍스트가 이미지 안에 직접 렌더링된 섹션
- 과장/허위/플랫폼 위험 문구 제거
- contact sheet QA와 선택 재생성
- 최종 납품 폴더, manifest, Obsidian 로그까지 남기는 방식

## 최종 기준 산출물 예시
기준 결과물은 아래 폴더의 v3 버전이다.

`Assets/58973715_ROKA_Regenerated_PDP_Harness/04_final_v3_conversion/`

기준 파일:
- `58973715_ROKA_v3_conversion_thumbnail_model.png`
- `58973715_ROKA_v3_conversion_thumbnail_model.jpg`
- `58973715_ROKA_v3_conversion_full_detail_page.png`
- `58973715_ROKA_v3_conversion_full_detail_page.jpg`
- `58973715_ROKA_v3_conversion_contact_sheet.jpg`
- `manifest.json`

기준 로그:
- `2026-05-10 ROKA 로카티 v3 구매전환 개선 제작 로그.md`

## 전체 운영 원칙

### 1. 소스 이미지는 증거, 최종 이미지는 신규 제작
공급사/도매 상세페이지 이미지를 그대로 crop/복붙하지 않는다. 소스는 다음 용도로만 사용한다.

- 제품 형태 확인
- 로고/프린트/색상/소매/후면 디테일 확인
- 소재/마감/사이즈표 OCR 근거 확인
- 금지해야 할 과장 문구 식별
- 생성 이미지 QA 기준

### 2. 썸네일 기본값은 모델 착용형
사용자 선호상, 대표 이미지는 제품과 어울리는 자연스러운 모델이 착용한 라이프스타일 이미지가 기본이다.

단, 쿠팡처럼 대표 이미지 규정이 엄격한 플랫폼에서는 product-only 흰 배경 썸네일을 별도로 유지한다.

모델 착용형 썸네일 조건:
- 정사각형 1024x1024
- 제품을 착용한 자연스러운 모델
- 제품 전면 핵심 디테일 노출
- 후면 디자인이 중요한 상품이면 작은 인셋으로 후면 노출
- 광고 문구, 가격, 할인, 배지, 리뷰, 랭킹, 가짜 인증 없음
- 모델은 제품 카테고리와 어울리되 과장된 상황 연출 금지

### 3. 상세페이지는 구매 흐름으로 설계
예쁜 이미지 나열이 아니라 고객의 구매 결정을 돕는 순서로 구성한다.

권장 흐름:
1. Thumbnail — 모델 착용형 대표 이미지
2. Hook — 3초 안에 왜 볼 만한 상품인지 전달
3. Buying Reasons — 구매 이유를 디테일 카드로 정리
4. Daily Fit / Use Imagination — 일상 착용 또는 사용 상상
5. Strongest Visual Proof — 가장 강한 시각 포인트 확대
6. Material / Finish Check — 소재와 마감은 확인형 문구로 신뢰 형성
7. Size / Option Confidence — 사이즈·옵션·구성 불안 제거
8. Use Scenes — 사용 장면 구체화
9. Safe Trust Check — 공식성/기능성/인증/라이선스 오해 방지
10. Final Choice — 핵심 포인트와 구매 전 확인사항 요약

## 작업 폴더 구조

상품별로 아래 구조를 만든다.

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
    accepted copy of generated sections
  04_final_v3_conversion/
    <product>_v3_conversion_thumbnail_model.png
    <product>_v3_conversion_thumbnail_model.jpg
    <product>_v3_conversion_full_detail_page.png
    <product>_v3_conversion_full_detail_page.jpg
    <product>_v3_conversion_contact_sheet.jpg
    manifest.json
```

## Evidence Ledger 작성법

이미지를 만들기 전에 반드시 제품 사실을 아래처럼 나눈다.

```yaml
confirmed_from_page_text:
  - 상품명
  - 옵션명
  - 가격/배송 정책이 필요한 경우
confirmed_from_source_image_ocr:
  - 소재 표기
  - 사이즈표
  - 마감/프린팅/구성품 표기
confirmed_from_visual_inspection:
  - 색상
  - 로고 위치
  - 제품 실루엣
  - 모델/착용 방식
safe_general:
  - 데일리룩
  - 야외활동
  - 선물 준비
needs_confirmation:
  - 기능성 수치
  - 라이선스
  - 인증 여부
blocked:
  - 공식 군납
  - 1위/최저가
  - UV 차단 보장
  - 냉감/흡습속건 보장
```

## Product Identity Lock
모든 이미지 생성 프롬프트에 제품 고정 블록을 반복한다. GPT Image2는 섹션마다 제품 형태가 달라질 수 있으므로 매번 넣는다.

ROKA 로카티 예시:

```text
CRITICAL PRODUCT IDENTITY LOCK
- Black crewneck short-sleeve t-shirt only.
- Small white "R.O.K.A" print on left chest when front is visible.
- Large white "KOREA" with smaller "ARMY" underneath when back is visible.
- Small Korean flag detail on sleeve when sleeve is visible.
- Black body, white print, small red/blue flag accent only.
- Not long sleeve, not hoodie, not polo, not camo, not official uniform, not tactical gear, no extra patches, no fake emblems.
- If using a model, model is a normal Korean adult customer in casual lifestyle pose, not a soldier; no salute, no weapons, no military base.
```

다른 상품에서는 이 블록을 제품별로 구체화한다.

## 프롬프트 구조
각 섹션 프롬프트는 아래 구조로 통일한다.

```text
DELIVERABLE
- Korean ecommerce conversion-focused PDP image.
- Section id: <section_id>
- Aspect: square or portrait.
- Create a NEW generated sales image from product facts. Do NOT copy supplier images, crops, layout, or old text artifacts.

CONVERSION ROLE
- <이 섹션의 구매전환 역할>

CRITICAL PRODUCT IDENTITY LOCK
- <제품 고정 블록>

VISUAL DIRECTION
- <구도, 모델/제품/카드 구성>
- Premium Korean ecommerce design.
- Mobile-readable bold Korean sans-serif typography.

EXACT TEXT TO RENDER
- <이미지 안에 들어갈 정확한 한국어 문구>

STRICT TEXT RULES
- Render ONLY the exact text above plus product-native prints/logos.
- Do not add extra Korean words, English slogans, prices, badges, ratings, or CTA buttons.

CLAIM / PLATFORM RULES
- No price, discount, review count, ranking, fake certification, award, official supply claim.
- Use 확인/표기/구매 전 확인 language for material, function, certification, officialness, license.
```

## 섹션별 카피 패턴

### 00 모델 착용형 썸네일
- 텍스트 없음
- 제품 고유 로고/프린트만 허용
- 모델 착용 + 후면 인셋 조합 추천

### 01 Hook
목적: 첫 3초 안에 상품의 매력을 전달한다.

예시:
- `한 장으로 완성되는 로카 무드`
- `앞은 깔끔하게`
- `뒤는 확실하게`
- `블랙 반팔 티셔츠`

### 02 Buying Reasons
목적: 상품 디테일을 구매 이유로 번역한다.

예시:
- `구매 이유는 디테일에 있습니다`
- `전면 R.O.K.A 포인트`
- `후면 KOREA ARMY 프린팅`
- `소매 태극기 디테일`

### 03 Daily Fit
목적: 고객이 실제 착용/사용 장면을 상상하게 한다.

예시:
- `데일리룩에도 자연스럽게`
- `블랙 컬러로 코디는 쉽게`
- `앞면은 과하지 않게`
- `뒷면은 포인트 있게`

### 04 Strong Visual Proof
목적: 상품의 가장 강한 시각 포인트를 확대한다.

예시:
- `뒷모습에서 완성되는 존재감`
- `KOREA ARMY 프린팅`
- `선명한 화이트 대비`
- `전면은 심플하게`

### 05 Material / Finish Check
목적: 과장 없이 소재·마감 확인 포인트를 보여준다.

예시:
- `디테일까지 꼼꼼하게 확인`
- `원단 질감 확인`
- `봉제 마감 확인`
- `전·후면 프린팅 확인`

주의:
- `시원합니다`, `빠르게 마릅니다`, `변형 없습니다`처럼 보장형 표현 금지
- 기능성은 수치/시험성적서가 없으면 `확인 필요` 또는 `상품정보 확인`으로 처리

### 06 Size / Option Confidence
목적: 구매 실패 불안을 줄인다.

예시:
- `사이즈 실패를 줄이는 실측 체크`
- `95부터 120까지`
- `가슴 48~60cm`
- `총기장 67~77cm`
- `1~2cm 오차 가능`

### 07 Use Scenes
목적: 상품 활용도를 보여준다.

예시:
- `어디에 입어도 활용도 있게`
- `팀웨어`
- `야외활동`
- `데일리룩`
- `선물 준비`

### 08 Safe Trust Check
목적: 공식성·기능성·라이선스 오해를 줄인다.

예시:
- `구매 전 꼭 확인하세요`
- `공식 군납 상품이 아닙니다`
- `기능성 수치는 상품정보를 확인하세요`
- `상표·라이선스 관련 안내를 확인하세요`

### 09 Final Choice
목적: 마지막 선택 전 핵심 포인트를 요약한다.

예시:
- `마지막으로 한 번 더 확인하세요`
- `전면 R.O.K.A`
- `후면 KOREA ARMY`
- `소매 태극기 디테일`
- `사이즈 95~120`

## 이미지 생성 실행 패턴
Hermes 환경에서는 `plugins.image_gen.openai-codex` provider를 사용했다.

핵심 실행 패턴:

```python
import importlib, os, shutil, sys, json, time
from pathlib import Path

repo = Path('/home/aiebrain/.hermes/hermes-agent')
sys.path.insert(0, str(repo))
os.chdir(repo)
os.environ['OPENAI_IMAGE_MODEL'] = 'gpt-image-2-medium'

mod = importlib.import_module('plugins.image_gen.openai-codex')
provider = mod.OpenAICodexImageGenProvider()
res = provider.generate(prompt, aspect_ratio='portrait')
shutil.copy2(Path(res['image']), output_path)
```

권장 aspect:
- 썸네일: `square`, 1024x1024
- 상세 섹션: `portrait`, 1024x1536

## 최종 패키징

PIL로 아래를 만든다.

1. 썸네일 PNG/JPG
2. 상세페이지 합본 PNG/JPG
3. contact sheet JPG
4. manifest.json

합본 규칙:
- 상세페이지 합본에는 00 썸네일을 넣지 않는다.
- 상세 합본은 01~09 섹션을 세로로 연결한다.
- 모든 섹션은 1024px width로 맞춘다.
- JPG는 quality 92, progressive 권장.

## QA 루틴

### 1차 QA — contact sheet
질문 예시:

```text
QA this Korean ecommerce PDP contact sheet.
Check conversion flow, Korean text readability/typos/pseudo Hangul, product consistency, unsafe claims, fake badges, platform risks, severe crop/layout.
Return panel-by-panel PASS/CONDITIONAL/REGENERATE and note if any image should be regenerated.
```

### 2차 QA — 재생성 후 contact sheet
재생성한 패널이 있으면 contact sheet를 다시 만들고 다음을 확인한다.

- 문제가 된 한글이 수정됐는가
- pseudo Hangul이 사라졌는가
- 제품 형태가 바뀌지 않았는가
- 새 문구가 더 위험한 주장으로 바뀌지 않았는가

### 3차 QA — 썸네일 단독
질문 예시:

```text
QA this final thumbnail only. Requirements: natural model lifestyle thumbnail, square, product consistency, no added marketing text/price/badge/fake certification/reviews/weapons/uniform implication. Verdict PASS/CONDITIONAL/REGENERATE.
```

## 재생성 기준
무조건 재생성:
- 핵심 한글 오탈자
- pseudo Hangul
- 제품 카테고리 변경
- 로고/색상/형태 심각한 왜곡
- 가격/할인/리뷰/랭킹/인증/공식성 허위 문구 생성
- 무기/군복/의료/안전/과장 기능성 암시
- 심각한 crop/레이아웃 깨짐

조건부 허용:
- 작은 보조 라벨 반복
- 의미는 맞지만 조금 어색한 한국어
- 제품 표현은 맞지만 플랫폼별로 더 보수적인 버전이 필요할 때

## 최종 보고 형식

```text
완료했습니다.

저장 폴더:
<final folder>

최종 파일:
1. 썸네일 PNG
2. 썸네일 JPG
3. 전체 상세페이지 PNG
4. 전체 상세페이지 JPG
5. contact sheet
6. manifest

QA:
- 썸네일: PASS
- 상세페이지: PASS 중심
- 재생성 내역: <있으면 기록>
- 남은 주의: <권리/라이선스/소재/사이즈/배송 등>
```

## 이번 작업에서 배운 핵심 레슨
1. 전환형 썸네일은 product-only보다 모델 착용형이 감정/착용 상상에 유리하다.
2. 다만 엄격 플랫폼용 product-only 썸네일은 별도 유지하는 것이 안전하다.
3. GPT Image2는 한글을 잘 렌더링하지만, `클로` 같은 불명확한 단어가 생길 수 있어 반드시 contact sheet QA가 필요하다.
4. 안전/신뢰 섹션은 내부 QA 문구처럼 쓰면 전환을 떨어뜨릴 수 있으므로 고객용 표현으로 바꿔야 한다.
5. 군/국기/상표 관련 상품은 디자인 자체가 매력 포인트이면서 동시에 플랫폼 리스크이므로, 최종 상세페이지에 공식성/라이선스 확인 문구를 넣는 것이 안전하다.
6. 최종 로그에는 생성 런타임, 파일 경로, QA, 재생성 내역, 남은 확인 사항까지 기록해야 다음 상품에서 동일 품질을 재현할 수 있다.
