# storyTeller
# 🌙 Personalized Bedtime Storyteller

A heartwarming AI application that generates unique, age-appropriate bedtime stories based on dynamic variables like the child's name, a chosen moral lesson, and favourite characters.

![Powered by Claude](https://img.shields.io/badge/Powered%20by-Claude%20AI-7F77DD?style=flat-square) ![Netlify](https://img.shields.io/badge/Deployed%20on-Netlify-00C7B7?style=flat-square)

---

## Demo

> **Input:** Child: Leo, Age: 5. Character: A clumsy astronaut. Theme: Learning that it's okay to make mistakes.
>
> **Output:** A gentle, rhyming tale about Captain Leo dropping his moon-map, getting lost, but discovering a beautiful new galaxy because of his mistake — ending with a soft, sleepy conclusion.

---
## Deployed link - https://poetic-dango-6a931f.netlify.app

## Features

- Personalized stories using child's name, age, and favourite character
- 6 moral lesson themes — mistakes, kindness, bravery, friendship, patience, self-belief
- 3 story lengths — Short (150 words), Medium (300 words), Long (500 words)
- Beautiful starry night animated background with twinkling stars
- Warm italic typography perfect for bedtime reading
- Copy story to clipboard for saving or printing
- Regenerate for a fresh story variation
- Dark immersive UI with purple/gold space theme

---

## Project Structure

```
04-bedtime-storyteller/
├── index.html
├── .gitignore
└── netlify/
    └── functions/
        └── generate.js
```

---

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v18+
- [Netlify CLI](https://docs.netlify.com/cli/get-started/) — `npm install -g netlify-cli`
- An [Anthropic API key](https://console.anthropic.com/)

### Local Development

```bash
git clone https://github.com/yourusername/bedtime-storyteller.git
cd bedtime-storyteller
netlify login
netlify dev
```

Open [http://localhost:8888](http://localhost:8888)

### Environment Variables

```
ANTHROPIC_API_KEY=sk-ant-your-key-here
```

---

## Deployment

```bash
netlify deploy --prod
```

Add `ANTHROPIC_API_KEY` in **Netlify Dashboard → Site configuration → Environment variables**, then redeploy.

---

## How It Works

```
Parent fills in child's name, age, character, theme, and story length
        ↓
index.html builds a personalized prompt → sends to /.netlify/functions/generate
        ↓
generate.js adds API key → forwards to Anthropic
        ↓
Claude generates a warm, age-appropriate story with sensory details
        ↓
Story displayed in italic storybook style with copy button
```

---

## Prompt Template

```
Write a soothing bedtime story for a [Age]-year-old named [Name].
The protagonist is [Character].
The moral of the story is [Theme].
Use simple vocabulary, sensory details, and end with a sleepy, calming conclusion.
Length: [Short / Medium / Long].
```

---

## Temperature Note

This project benefits from a **higher temperature** setting (0.7–0.9) to encourage imaginative, creative storytelling. To set this, add `temperature: 0.8` to the API body in `index.html`:

```js
body: JSON.stringify({
  model: 'claude-sonnet-4-6',
  max_tokens: 1200,
  temperature: 0.8,       // ← add this line
  messages: [...]
})
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| Icons | Tabler Icons |
| AI Model | Claude Sonnet (claude-sonnet-4-6) |
| Backend | Netlify Serverless Functions |
| Hosting | Netlify |

---

## License

MIT
