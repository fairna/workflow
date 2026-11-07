# Instagram News Automation

An automated workflow built with **n8n Cloud** to transform property news articles into Instagram carousel content

The workflow discovers property news, extracts article content, generates carousel content and design specifications using Google Gemini, and creates slide images using Gemini Image Generation.

## Features

- **News Discovery:** Collects property news articles through Google News RSS.
- **Article Extraction:** Resolves article URLs and extracts full article content from ANTARA.
- **Content Planning:** Uses Google Gemini to analyze news and create an Instagram carousel content plan.
- **AI Design Generation:** Generates slide headlines, body text, visual concepts, and layouts based on project guidelines.
- **Image Prompt Generation:** Uses an AI Agent to transform structured slide design JSON into detailed image-generation prompts.
- **AI Image Generation:** Uses Gemini Image Generation to generate carousel visuals based on the generated prompts.
- **Carousel Output:** Produces a maximum of 6 slides with one caption for the entire carousel.

## Repository Structure

```text
workflow/
│
├── assets/
│   └── reference-images/
│
├── guidelines/
│   ├── prompt.md
│   ├── agent-instructions.md
│   ├── content-guidelines.md
│   ├── brand-guidelines.md
│   ├── creative-guidelines.md
│   └── output-specification.md
│
├── workflows/
│   └── rumah123-instagram-automation.json
│
└── README.md
```

## Requirements

- n8n Cloud account.
- Google Gemini API key with access to the required text and image generation models.
- GitHub repository access for retrieving project guidelines.

## Setup

### 1. Import the Workflow

1. Open your n8n Cloud workspace.
2. Create a new workflow.
3. Select **Import from File**.
4. Upload `rumah123-instagram-automation.json`.
5. Save the imported workflow.

### 2. Configure Google Gemini

1. Obtain a Google Gemini API key.
2. Configure Google Gemini credentials in n8n.
3. Select the credentials in the Gemini Chat Model and Gemini Image Generation nodes.
4. Ensure the selected models support the required operations.

### 3. Configure GitHub Guidelines

The workflow retrieves project guidelines from:

```text
https://raw.githubusercontent.com/fairna/workflow/main/
```

Required files:

- `guidelines/agent-instructions.md`
- `guidelines/content-guidelines.md`
- `guidelines/brand-guidelines.md`
- `guidelines/creative-guidelines.md`
- `guidelines/output-specification.md`

## How to Run

### 1. Execute the Workflow

Open the workflow in n8n and click **Execute Workflow** to start the automation.

### 2. News Discovery and Extraction

The workflow searches for property-related news through Google News RSS, filters ANTARA articles, resolves article URLs, and extracts article information.

### 3. AI Content Planning

Google Gemini analyzes the extracted article and generates:

- Main news angle.
- Key facts and supporting information.
- Important statistics.
- Carousel narrative.
- Instagram caption and hashtags.

### 4. Carousel Design Generation

An AI Agent generates structured JSON containing:

- Carousel metadata.
- One caption for the entire carousel.
- Slide headlines and body text.
- Visual descriptions.
- Layout and composition instructions.

The carousel contains a maximum of 6 slides.

### 5. Image Prompt Generation

An AI Agent receives the parsed slide design JSON and generates detailed image prompts based on:

- Slide content.
- Visual descriptions.
- Layout instructions.
- Brand guidelines.
- Creative guidelines.

### 6. Gemini Image Generation

Gemini Image Generation uses the generated prompts to create the carousel slide visuals.

### 7. Review the Output

Review the generated images and caption before publication.

Check:
- Accuracy of news information.
- Text and statistical consistency.
- Visual quality and brand consistency.
- Slide order and readability.
- Caption relevance.

## Important Notes

- Gemini model availability and API quotas depend on the selected model and Google AI plan.
- AI-generated content must be reviewed before publication.
- Never upload API keys or private credentials to GitHub.
- Keep project guidelines updated when brand or content requirements change.

## License

This project is intended for portfolio and educational purposes. Refer to the applicable terms of service and content usage permissions of external services and news sources.
