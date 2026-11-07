# Rumah123 Carousel Output Specification

## 1. Purpose

This file defines the machine-readable output expected from the content and creative planning agent before HTML/CSS rendering.

The agent must produce:
- A structured Instagram carousel content and design plan.
- A maximum of 6 slides per carousel.
- One Instagram caption for the entire carousel.
- Asset requirements for the rendering process.
- Validation results and unresolved issues.

The output must be ready for the downstream rendering workflow.

## 2. Hard Constraints

- Return valid JSON when JSON output is requested.
- Do not wrap JSON in Markdown code fences.
- Use the exact field names and data types defined below.
- Do not include comments or trailing commas in JSON.
- Do not invent asset paths, URLs, QR destinations, or source details.
- Use `null` or an empty array when information is unavailable, as permitted by the schema.
- Generate a minimum of 1 and a maximum of 6 slides.
- Do not exceed 6 slides under any circumstances.
- Use fewer slides when the article can be communicated effectively with fewer slides.
- Generate exactly one Instagram caption for the entire carousel.
- The caption must be relevant to the article and consistent with the carousel content.
- All slide content and caption claims must be grounded in the provided article.
- Each slide must define its own visual direction and composition.
- The rendering system must not assume all slides use one identical layout.
- Do not add unsupported facts, statistics, interpretations, or promotional claims.

## 3. Output Contract

The top-level JSON object must contain:

- `carousel`: metadata and creative direction.
- `caption`: Instagram caption and hashtags.
- `slides`: ordered slide objects.
- `asset_requirements`: assets needed by the design.
- `validation`: validation status and unresolved issues.

## 4. JSON Schema Example

The following is an illustrative structure. Replace example values with information grounded in the actual input.

{
  "carousel": {
    "topic": "Perkembangan harga properti residensial di Indonesia",
    "main_message": "Harga properti residensial mengalami pertumbuhan terbatas berdasarkan survei Bank Indonesia.",
    "target_audience": [
      "calon pembeli rumah",
      "pemilik properti",
      "pelaku industri properti"
    ],
    "content_approach": "news_explainer",
    "creative_direction": {
      "concept": "Understanding the residential property market",
      "visual_strategy": "Editorial storytelling with supporting property imagery and data visualization",
      "visual_mood": "Informative, clear, contemporary",
      "brand_treatment": "Use Rumah123 brand identity while adapting the composition to the article topic"
    },
    "slide_count": 5,
    "aspect_ratio": "4:5",
    "canvas": {
      "width": 1080,
      "height": 1350,
      "format": "png"
    }
  },
  "caption": {
    "text": "Bagaimana perkembangan harga properti residensial saat ini? Simak hasil survei Bank Indonesia dan sejumlah hal penting yang perlu diketahui dari kondisi pasar properti terkini.",
    "hashtags": [
      "#Rumah123",
      "#BeritaProperti",
      "#PasarProperti",
      "#PropertiIndonesia"
    ],
    "call_to_action": "Bagaimana menurutmu kondisi pasar properti saat ini? Tulis pendapatmu di kolom komentar."
  },
  "slides": [
    {
      "slide_number": 1,
      "purpose": "Introduce the news",
      "headline": "Pertumbuhan harga properti residensial masih terbatas",
      "body": "Bank Indonesia mencatat perkembangan harga properti residensial di pasar primer pada triwulan III 2026.",
      "key_facts": [
        {
          "fact": "Harga properti residensial pasar primer tumbuh terbatas pada triwulan III 2026.",
          "source_reference": "provided_article",
          "qualification": "Based on Bank Indonesia's residential property price survey"
        }
      ],
      "visual": {
        "subject": "Residential property and housing development",
        "type": "photography",
        "description": "Editorial photograph of a residential property development.",
        "asset_status": "to_retrieve_or_generate"
      },
      "layout": {
        "composition": "full_bleed_image_with_overlay",
        "background": "photo_with_brand_overlay",
        "text_alignment": "left",
        "visual_position": "full_background",
        "hierarchy": [
          "headline",
          "supporting_copy",
          "source_context"
        ]
      },
      "brand_elements": {
        "logo": "required",
        "highlight": null,
        "pagination": true
      }
    }
  ],
  "asset_requirements": [
    {
      "asset_type": "logo",
      "asset_name": "Rumah123 logo",
      "status": "required",
      "source": "brand_asset_library"
    },
    {
      "asset_type": "photography",
      "asset_name": "Residential property image",
      "status": "to_retrieve_or_generate",
      "source": null
    }
  ],
  "validation": {
    "factual_accuracy": "pass",
    "caption_consistency": "pass",
    "slide_count": "pass",
    "brand_compliance": "needs_asset_check",
    "mobile_readability": "pending_render",
    "unresolved_issues": []
  }
}

## 5. Field Definitions

### 5.1 Carousel Object

| Field | Type | Description |
|---|---|---|
| `topic` | string | Main topic of the carousel |
| `main_message` | string | Central message |
| `target_audience` | array of strings | Intended audience, if identifiable |
| `content_approach` | string | Selected storytelling approach |
| `creative_direction` | object | Overall art direction |
| `slide_count` | integer | Actual number of planned slides, maximum 6 |
| `aspect_ratio` | string | Normally `4:5` |
| `canvas` | object | Output dimensions and format |

### 5.2 Caption Object

| Field | Type | Description |
|---|---|---|
| `text` | string | Main Instagram caption |
| `hashtags` | array of strings | Relevant hashtags |
| `call_to_action` | string or null | Optional audience engagement prompt |

Caption requirements:
- Generate one caption for the entire carousel.
- Write in natural, engaging Bahasa Indonesia.
- Provide context beyond simply repeating the slide headlines.
- Maintain factual accuracy and consistency with the source article.
- Avoid unsupported claims, exaggerated statements, and misleading clickbait.
- Include a relevant call to action when appropriate.
- Use relevant hashtags without excessive repetition.
- Do not invent source links or promotional links.

### 5.3 Slide Object

| Field | Type | Description |
|---|---|---|
| `slide_number` | integer | Slide order, starting from 1 |
| `purpose` | string | Communication purpose |
| `headline` | string or null | Main slide headline |
| `body` | string or null | Supporting copy |
| `key_facts` | array | Facts used on the slide and their grounding |
| `visual` | object | Visual subject and asset direction |
| `layout` | object | Composition and hierarchy |
| `brand_elements` | object | Logo and optional brand devices |

### 5.4 Asset Status Values

Use clear status values such as:

- `available`
- `to_retrieve`
- `to_generate`
- `required`
- `required_if_available`
- `required_missing`
- `not_needed`

Do not mark an asset as available unless it was supplied or confirmed by the workflow.

## 6. Slide Planning Rules

- The carousel must contain between 1 and 6 slides.
- The first slide should introduce the main news angle and attract attention.
- The following slides should develop the story logically.
- Use the final slide for a relevant takeaway, conclusion, or audience engagement when appropriate.
- Do not force a fixed storytelling structure when the article requires a different approach.
- Do not repeat the same information across multiple slides without a clear purpose.
- Prioritize the most important facts when deciding what to include.
- Each slide must have a clear communication purpose.
- Select the number of slides based on the amount of relevant information, not a predetermined slide count.

## 7. Few-Shot Examples

### Few-Shot 1 — Use a Map When Location Is the Main Story

**Input**

A verified article describes a proposed road connection and identifies the affected districts.

**Expected output decision**

- `visual.type`: `map`
- `layout.composition`: `map_led`
- `asset_requirements`: request a verified map or create a clearly labeled schematic based only on confirmed route information.

**Do not**

Create a precise geographic map from vague place references.

### Few-Shot 2 — Do Not Force a QR Code

**Input**

The carousel explains a housing policy. No campaign landing page or QR destination is supplied.

**Expected output decision**

- The final slide may use a takeaway or a relevant question.
- Do not add a QR asset requirement unless the user specifically requests one.
- Do not fabricate a QR URL.

### Few-Shot 3 — Preserve Uncertainty

**Input**

The article says a project is being considered, but no approval date is provided.

**Expected output decision**

Use wording such as "masih dalam tahap pembahasan" only if supported by the source. Keep the project status qualification in `key_facts` and the slide copy.

**Do not**

Convert it into "proyek akan segera dibangun".

### Few-Shot 4 — Respect the Maximum Slide Count

**Input**

An article contains many facts and developments that could be expanded into 8 slides.

**Expected output decision**

- Select the 6 most relevant slides.
- Consolidate related information where appropriate.
- Preserve the central story and important qualifications.
- Set `carousel.slide_count` to 6.

**Do not**

Generate 7 or more slides.

### Few-Shot 5 — Generate One Caption for the Carousel

**Input**

A carousel explains the latest residential property price survey.

**Expected output decision**

- Generate one caption in `caption.text`.
- Add relevant hashtags in `caption.hashtags`.
- Include a relevant engagement prompt in `caption.call_to_action` when appropriate.

**Do not**

Generate a separate Instagram caption for every slide.

## 8. Output Validation Rules

Before returning the JSON, verify:

1. The output is valid JSON.
2. All required top-level fields are present.
3. `carousel.slide_count` matches the actual number of objects in `slides`.
4. The slide count is at least 1 and does not exceed 6.
5. Slide numbers are sequential, starting from 1.
6. Exactly one caption object is present.
7. Caption text is not empty.
8. Caption claims are consistent with the source article.
9. Every slide has its own visual direction and composition.
10. All key facts are grounded in the provided article.
11. Asset statuses accurately reflect asset availability.
12. No fabricated URLs, asset paths, QR destinations, or source details are included.

Use the following validation status values:

- `pass`
- `fail`
- `pending`
- `needs_asset_check`
- `pending_render`

If a hard constraint fails, do not silently mark the output as valid. Correct the output before returning it. If correction is impossible, report the issue in `validation.unresolved_issues`.

## 9. Rendering Handoff

The output is a design and content plan, not finished HTML.

The rendering workflow should:

1. Read the JSON output.
2. Resolve available assets.
3. Select or assemble HTML/CSS components based on each slide's `layout`.
4. Apply brand tokens from `brand-guidelines.md`.
5. Render each slide to PNG.
6. Return rendered slides for review.
7. Preserve the generated caption separately for the Instagram publishing stage.

The renderer must support multiple composition types. It must not silently replace all requested layouts with one fixed template.

The renderer must produce exactly the number of images specified in `carousel.slide_count`, with a maximum of 6 images.

## 10. Post-Render Validation

After rendering, inspect:

- Text overflow and clipping.
- Safe margins.
- Image cropping.
- Logo contrast and integrity.
- Font availability and fallback.
- Color contrast.
- Chart and map legibility.
- QR scanability if a real QR is included.
- Consistency across the carousel without forcing identical layouts.
- Actual rendered image count does not exceed 6.
- All slide content matches the approved JSON.
- Caption is available separately from the rendered slide images.