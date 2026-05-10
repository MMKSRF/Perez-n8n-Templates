# 🇪🇹 Ethio-Cinematic AI Video Factory

An automated **n8n workflow** that generates spiritual, cinematic videos of Ethiopia using AI.

This system combines:

- **Imagen 3 (Vertex AI)** → image generation
- **Gemini 1.5 Flash** → YouTube metadata generation
- **MediaFX** → video production
- **Telegram Bot** → voice-triggered automation

---

# ✨ Features

- 🎙 **Voice-Triggered Workflow**  
  Generate videos instantly by sending a voice message or audio file to your private Telegram bot.

- ⏱ **Dynamic Video Length**  
  The final video duration automatically matches the length of the uploaded audio.

- 🎨 **500+ Randomized Combinations**  
  Creates unique cinematic outputs using Ethiopian spiritual themes, visual styles, and sacred Ge'ez quotes.

- 🇪🇹 **Authentic Ge'ez & Amharic Support**  
  Automatically includes Amharic text in YouTube titles and descriptions.

- 📱 **Vertical 9:16 Format**  
  Optimized for:
  - YouTube Shorts
  - TikTok
  - Instagram Reels

---

# 🚀 Workflow Overview

```text
Telegram Audio Trigger
        ↓
Randomizer (JavaScript)
        ↓
Imagen 3 (Vertex AI)
        ↓
Gemini 1.5 Flash
        ↓
MediaFX Video Composer
        ↓
YouTube Upload
```

## Step-by-Step Process

### 1. Telegram Trigger
You send an audio message to your Telegram bot.

n8n:
- downloads the audio
- calculates the duration
- passes it through the workflow

---

### 2. Randomizer (JavaScript Node)

The workflow randomly selects:
- a spiritual Ethiopian theme
- a cinematic scene
- an Amharic quote
- a unique generation seed

This ensures every generated video feels different and authentic.

---

### 3. Visual Generation — Imagen 3 (Vertex AI)

**Imagen 3** generates a hyper-realistic cinematic image in **9:16 format**.

Example scene prompt:

```text
A lone Ethiopian priest praying inside the deep blue shadows
of the Lalibela rock-hewn churches, cinematic lighting,
ultra realistic, spiritual atmosphere, 9:16
```

---

### 4. Metadata Generation — Gemini 1.5 Flash

Gemini automatically creates:
- viral YouTube titles
- bilingual descriptions (Amharic + English)
- hashtags and SEO metadata

Example output:

```text
🕯️ የላሊበላ መንፈሳዊ ምሽት | Spiritual Ethiopia ✨
```

---

### 5. Video Production — MediaFX

MediaFX:
- combines the generated image and audio
- creates a cinematic vertical video
- exports the final file

The final video duration exactly matches the original audio length.

---

### 6. YouTube Distribution

The workflow automatically uploads the completed video to your YouTube channel.

---

# 🛠 Requirements

## 1. Google Cloud Platform

Enable the following APIs:

- Vertex AI API
- YouTube Data API v3

### Required Credentials

Create:
- **OAuth 2.0 Client ID**
- or a **Service Account**

Google Cloud Console:

https://console.cloud.google.com/

---

## 2. Telegram

Create a Telegram bot using **BotFather**.

BotFather:

https://t.me/botfather

You will receive:
- Bot Token
- API access for Telegram triggers

---

## 3. n8n

Install the MediaFX community node:

```bash
npm install @sonixnguyen/n8n-nodes-mediafx
```

---

# 📦 Installation

## 1. Export the Workflow

Copy the `workflow.json` file from this repository.

---

## 2. Import into n8n

Inside n8n:

- Create a new workflow
- Press:

```text
CTRL + V
```

to paste the workflow nodes directly.

---

## 3. Configure Credentials

Add credentials for:

- Google YouTube OAuth2
- Google Vertex AI
- Telegram Bot API

---

# 🧠 Core Logic — Randomizer Node

```javascript
const spiritualQuotes = [
  {
    amharic: "እግዚአብሔር ብርሃኔና መድኃኒቴ ነው፤ የሚያስፈራኝ ማን ነው?",
    english: "The Lord is my light and my salvation"
  },
  // ...100+ more quotes
];

const scenes = [
  "A lone priest praying in the deep blue shadows of Lalibela rock churches",
  // ...100+ more scenes
];

// Random selection logic
const selectedQuote =
  spiritualQuotes[Math.floor(Math.random() * spiritualQuotes.length)];

const selectedScene =
  scenes[Math.floor(Math.random() * scenes.length)];
```

---

# ⚠️ Common JSON Error Fix

If you encounter errors such as:

```text
Bad Request
Invalid JSON
```

inside Gemini or Vertex AI nodes, ensure your expressions are wrapped properly.

## ✅ Correct Format

```javascript
{{ { "prompt": $json.prompt } }}
```

This prevents issues with:
- escaped characters
- Amharic text
- malformed JSON payloads

---

# 📁 Recommended Repository Structure

```text
ethio-cinematic-ai/
│
├── README.md
├── workflow.json
├── assets/
│   ├── examples/
│   └── thumbnails/
│
└── prompts/
    ├── quotes.json
    └── scenes.json
```

---

# 🔥 Future Improvements

- Multi-image cinematic transitions
- AI-generated Ethiopian ambient music
- Automatic subtitle generation
- TikTok auto-upload support
- Multi-language support
- AI voice narration

---

# ❤️ Credits

Created for the Ethiopian creative and AI community.

Built with:
- n8n
- Vertex AI
- Gemini
- Telegram
- MediaFX

---

## 📜 License

MIT License

Feel free to fork, modify, and build upon this project.
