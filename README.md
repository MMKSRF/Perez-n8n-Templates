```python
markdown_content = """# 🇪🇹 Ethio-Cinematic AI Video Factory

An automated n8n workflow that generates spiritual, high-quality cinematic videos of Ethiopia. This system uses **Imagen 3 (Vertex AI)** for visuals, **Gemini 1.5 Flash** for metadata, and **MediaFX** for video production, triggered directly by your voice via **Telegram**.

## ✨ Features
* **On-Demand Creation:** Trigger video generation by sending a voice message or audio file to your private Telegram bot.
* **Dynamic Video Length:** The generated video length automatically matches the duration of your audio message.
* **Deep Variety:** Over 500+ random combinations of Ethiopian spiritual themes, artistic styles, and sacred Ge'ez quotes.
* **Authentic Ge'ez Support:** Automatically integrates Amharic text into YouTube titles and descriptions.
* **9:16 Optimized:** Perfectly formatted for YouTube Shorts and TikTok.

## 🚀 How It Works
1.  **Telegram Trigger:** You send an audio message. n8n calculates the duration.
2.  **Randomizer (JS):** Selects a spiritual theme, a visual scene, and a random Amharic quote.
3.  **Visual Engine (Vertex AI):** **Imagen 3** generates a hyper-realistic 9:16 image.
4.  **Metadata Engine (Gemini):** Creates a viral YouTube Title and a dual-language (Amharic/English) description.
5.  **Production (MediaFX):** Concatentates the image and audio into a final video matching your audio length.
6.  **Distribution (YouTube):** Automatically uploads the video to your channel.

## 🛠 Setup & APIs
To run this workflow, you will need the following API credentials:

### 1. Google Cloud Platform
* **Vertex AI API:** For image generation.
* **YouTube Data API v3:** For video uploads.
* **Credentials:** Create an **OAuth 2.0 Client ID**.
    * *Where to get it:* [Google Cloud Console](https://console.cloud.google.com/)

### 2. Telegram
* **Telegram Bot Token:** To send your audio triggers.
    * *Where to get it:* [@BotFather](https://t.me/botfather)

### 3. n8n
* **MediaFX Node:** Requires the `@sonixnguyen/n8n-nodes-mediafx` community node installed in your n8n instance.

## 📦 Installation
1.  Copy the `workflow.json` code from this repository.
2.  In n8n, create a new workflow and press **CTRL+V** to paste the nodes.
3.  Configure your credentials for:
    * Google YouTube OAuth2
    * Google Vertex AI (Service Account or OAuth)
    * Telegram Bot API

## 📝 The "Brain" (JavaScript Node)
The core logic resides in the `Randomizer` node. It ensures your prompts are diverse and spiritually resonant:

```javascript
const spiritualQuotes = [
  { amharic: "እግዚአብሔር ብርሃኔና መድኃኒቴ ነው፤ የሚያስፈራኝ ማን ነው?", english: "The Lord is my light and my salvation" },
  // ... 100+ more quotes
];

const scenes = [
  "A lone priest praying in the deep blue shadows of Lalibela rock churches",
  // ... 100+ more scenes
];

// Logic picks random elements and a unique seed for every run

```

## ⚠️ Important Note on JSON Errors

If you encounter a `Bad Request` or `Invalid JSON` error in the Gemini/Vertex nodes, ensure your prompt expressions are wrapped correctly to escape Amharic characters:
`{{ { "prompt": $json.prompt } }}`

---

*Created with ❤️ for the Ethiopian Creative Community.*
"""

with open("README.md", "w", encoding="utf-8") as f:
f.write(markdown_content)

```
Your README.md file is ready for GitHub.

[file-tag: code-generated-file-0-1778407012250269389]

I have organized this file specifically for your project. It includes:
* **The "Audio-Driven" logic:** Mentioning how the Telegram voice message sets the video duration.
* **API Guide:** Exactly which Google APIs to enable (Vertex and YouTube).
* **A "Pro-Tip" section:** Explaining how to avoid those JSON "Bad Request" errors we fixed with the escaped expressions.

You can now upload this to your repository along with your exported n8n JSON file!

```
