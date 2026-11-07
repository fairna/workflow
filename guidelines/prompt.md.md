# Rumah123 Carousel Agent — Master Guidelines

## 1. Project Overview

This project automates the creation of Rumah123 Instagram carousel content from property-related news articles.

The AI Agent is responsible for:
- Analyzing news articles and extracting relevant information.
- Developing accurate and engaging carousel narratives.
- Creating slide-by-slide content.
- Generating an Instagram caption relevant to the carousel content.
- Developing creative visual directions and layouts.
- Producing structured output for carousel rendering.

## 2. Guidelines Directory

All guidelines are stored in the `guidelines/` directory.

| File | Purpose |
|---|---|
| `agent-instructions.md` | Defines the agent's role, objectives, workflow, and execution rules. |
| `content-guidelines.md` | Defines news analysis, information accuracy, storytelling, and copywriting. |
| `brand-guidelines.md` | Defines Rumah123 brand identity, colors, logo usage, and typography direction. |
| `creative-guidelines.md` | Defines art direction, visual concepts, slide composition, and layout decisions. |
| `output-specification.md` | Defines the required JSON structure and validation rules for rendering. |

## 3. Reference Images

Visual reference images are stored in:

`assets/reference-images/`

Use these images to understand the intended visual direction, including:
- Typography hierarchy.
- Color combinations.
- Composition and spacing.
- Visual storytelling.
- Overall design language.

Reference images are visual guidance, not fixed templates. Create layouts that suit each article rather than reproducing the same design for every carousel.

## 4. Guideline Usage

Follow the guidelines according to the current workflow stage:

1. Read `agent-instructions.md` to understand the overall task and workflow.
2. Read `content-guidelines.md` when analyzing news, developing carousel narratives, and generating Instagram captions.
3. Read `brand-guidelines.md` and `creative-guidelines.md` when developing visual concepts and slide layouts.
4. Follow `output-specification.md` when preparing the final structured output.

Do not load every guideline unnecessarily. Use the documents relevant to each stage.

## 5. Instruction Priority

When instructions conflict, follow this priority:

1. Explicit workflow requirements and hard constraints.
2. `agent-instructions.md`.
3. Relevant content, brand, and creative guidelines.
4. `output-specification.md` for output structure and validation.

All generated content must remain factually consistent with the original news article.

## 6. Carousel Constraints

- Generate a maximum of 6 slides per carousel.
- The carousel may contain fewer than 6 slides when the article can be communicated effectively with fewer slides.
- Do not add slides merely to reach the maximum limit.
- Generate one Instagram caption for each carousel.
- The caption must be relevant to the article and carousel narrative, written in accordance with `content-guidelines.md`.

## 7. Design Flexibility

The agent should make creative decisions based on the article topic and available visual references.

Do not assume that every carousel must use the same number of slides, layout, typography arrangement, or visual composition unless explicitly required by the output specification.

The agent must prioritize content clarity, factual accuracy, and visual quality while respecting the maximum slide limit.