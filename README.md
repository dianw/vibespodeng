# VibEsPodeng 🌟

A vibes-driven engineering project that embraces the flow of intuitive coding. This Nuxt.js application is crafted with 100% positive vibes and just the right amount of human guidance. It features Ollama integration for AI chat capabilities, because sometimes the best code comes from good conversations.

> "Code with vibes, debug with peace" - VibEsPodeng Philosophy

## Prerequisites

1. Node.js and npm
2. [Ollama](https://ollama.ai) installed on your machine
3. At least one language model installed in Ollama (e.g., Gemma, Llama, Phi, etc.). You can install models by running:
   ```bash
   # Example models - choose any that fits your needs
   ollama pull gemma2:2b      # Lightweight and fast
   ollama pull llama3.2:3b    # Good balance of speed and capability
   ollama pull phi3:mini      # Microsoft's efficient model
   ollama pull qwen2.5:1.5b   # Compact multilingual model
   ```
4. Ollama service running locally on port 11434

## Setup

1. Install dependencies:
   ```bash
   npm install
   ```

2. Start the development server:
   ```bash
   npm run dev
   ```

3. Open your browser and visit:
   - Home page: http://localhost:3000
   - Chat page: http://localhost:3000/chat

## Using the Chat Interface 💬

1. Navigate to the chat page at http://localhost:3000/chat
2. Select your preferred model from the dropdown (all your installed Ollama models will be available)
3. Type your message and hit "Send Message"
4. Enjoy the conversation with markdown-formatted responses!

## Vibes Features ✨

- Dynamic model selection - choose your AI companion from available Ollama models
- Chill chat interface with markdown support for rich, formatted responses
- Smooth streaming responses that flow like good conversation
- Zen-like UI components built with Nuxt UI
- TypeScript support for those structured vibes
- Clean code vibes maintained by ESLint
- Harmonious 3rd party script management with Nuxt Scripts

## Development Philosophy 🌊

This project embraces:
- Flow-state coding: Let the vibes guide the implementation
- Intuitive architecture: If it feels right, it probably is
- Balanced human-AI collaboration: We're all here to vibe together
- Progressive enhancement: Good vibes get better with time

## Vibe Stack 🚀

- Nuxt 4.0: The next-level framework for next-level vibes
- Vue 3 Composition API: Composing code like a smooth jazz session
- Nuxt UI Library: Beautiful components that spark joy
- TypeScript: Because even good vibes need strong types
- Ollama.js: AI integration that feels natural and flows right
- Marked.js: Markdown parsing for beautifully formatted AI responses

## Production

Build the application for production:

```bash
npm run build
```

Locally preview production build:

```bash
npm run preview
```
