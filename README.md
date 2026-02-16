

# AI Chatbot Template

A modern, customizable AI chatbot built with Next.js, Vercel AI SDK, and Google Gemini. Features include rate limiting, bot protection, and a beautiful UI. Read my learnings from this project at https://rryyqn.com/projects/ai-chatbot

<img width="960" height="540" alt="ai-chatbot" src="https://github.com/user-attachments/assets/d96cc13b-f675-41d6-b955-1335484e1e43" />

## Table of Contents

1. 🚀 [Quick Start](#-quick-start)
2. ⚙️ [Customization](#%EF%B8%8F-customization)
3. 🎨 [UI Customization](#-ui-customization)
4. 🔧 [Technical Details](#-technical-details)
5. 🚀 [Deployment](#-deployment)
6. 🛠️ [Troubleshooting](#-troubleshooting)
7. 📝 [License](#-license)

## 🚀 Quick Start

### 1. Clone and Install

```bash
git clone https://github.com/rryyqn/ai-chatbot.git
cd ai-chatbot-template
pnpm install
```

### 2. Environment Setup

Create a .env.local and add your API keys:

```bash
ARCJET_KEY=
GOOGLE_GENERATIVE_AI_API_KEY=
NEXT_PUBLIC_APP_URL=localhost
```

- `ARCJET_KEY` - Get from [Arcjet Dashboard](https://app.arcjet.com)
- `GOOGLE_GENERATIVE_AI_API_KEY` - Get from [Google AI Studio](https://aistudio.google.com/app/apikey)
- `NEXT_PUBLIC_APP_URL` - Use `localhost` for local development, use deployed url in production (eg. `https://ai-chatbot.vercel.app`)

### 3. Run Development Server

```bash
pnpm dev
```

Visit `http://localhost:3000` to see your chatbot!

## ⚙️ Customization

Edit <code>lib/config.ts</code> to customize your chatbot.

### Basic Information

`name` - Chatbot name

`welcomeMessage` - Initial message in the chat (supports choice and link syntax)

`ui.windowTitle` - Chat window title text

`ui.inputPlaceholder` - Placeholder text for message input

`ui.avatarImage` - AI's avatar image (place in public folder)

`ui.avatarFallback` - Fallback avatar image placeholder

### Rate Limiting

`rateLimit.capacity` - Maximum requests allowed in a burst

`rateLimit.refillRate` - How many tokens are added per interval

`rateLimit.interval` - How often tokens are refilled (in seconds)

### AI SDK API
`api.model` - AI model from Gemini

`api.systemPrompt` - system instruction for AI response (supports choice and link syntax)


### Security Settings

`enableBotDetection` - Block automated bots

`enableShield` - Protect against common attacks

`allowedBots` - Specify which bot categories to allow

### What is the choice/link syntax?

The choice and link syntax renders the interactive buttons at the bottom of AI response. These can be used by the AI for conversation flows, creating quick response suggestions and links to relevant resources. 

Use this in your system prompt:

```
When appropriate, you can these formats to allow users to continue the chat or click a link. Put it at the bottom of the response with no punctuation:
    - {{choice:Option Name}} - Creates clickable choice buttons
    - {{link:https://url.com|Button Text}} - Creates clickable link buttons
```

## 🎨 UI Customization

### Styling

The chatbot uses Tailwind CSS. Key styling files:
- `app/globals.css` - Global styles and theme
- `components/ui/` - Reusable UI components
- `components/Chatbot.tsx` - Direct chatbot styles

## 🔧 Technical Details

### Architecture

- **Frontend**: Next.js 15 with React 19
- **AI**: Vercel AI SDK with Google Gemini
- **Security**: Arcjet for rate limiting and bot protection
- **Styling**: Tailwind CSS with custom design system
- **Animations**: Framer Motion

### Key Features

- ✅ Real-time streaming responses
- ✅ Rate limiting and bot protection
- ✅ Mobile-responsive design
- ✅ Customizable UI and behavior
- ✅ TypeScript support
- ✅ Error handling and retry logic

### File Structure

```
├── app/
│   ├── api/chat/route.ts    # Chat API endpoint
│   ├── page.tsx             # Main page
│   └── globals.css          # Global styles
├── components/
│   ├── ai-elements/         # Chat-specific components
│   ├── ui/                  # Reusable UI components
│   └── Chatbot.tsx          # Main chatbot component
├── lib/
│   ├── config.ts            # Configuration file
│   ├── arcjet.ts            # Security configuration
│   └── utils.ts             # Utility functions
└── public/                  # Static assets (AI avatar image)
```

## 🚀 Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy!

### Other Platforms

The app works on any platform that supports Next.js:
- Netlify
- Railway
- Render
- DigitalOcean App Platform

## 🛠️ Troubleshooting

**Q: I’m getting auth errors from Google AI / Arcjet**

A: Confirm keys are correct and not expired. Verify the correct environment variables are set in your environment/hosting provider.

**Q: I'm getting 403 forbidden errors**

A: Set the `NEXT_PUBLIC_APP_URL` in your `.env` to your deployed URL, eg. `ai-chatbot.vercel.app`


## 📝 License

MIT License - feel free to use this template for your projects!


