# VLM Chatbot — Frontend
A modern, production-ready **Next.js** frontend for interacting with the Vision-Language Model (VLM).  
This interface provides a clean chat experience where users can upload satellite imagery, ask questions, and receive VQA responses from the backend.

## Overview
This frontend serves as the user-facing layer of the VLM system.  
It enables:
- Image upload for remote-sensing data  
- Conversational interaction with the AI model  
- Real-time response streaming  
- Image preview and attachment handling  

Built using **Next.js App Router**, **TypeScript**, and **Tailwind**, the project is optimized for speed, modularity, and readability.

## Features 
-  Image upload + preview modal  
-  API proxy for backend communication  
-  Responsive design for mobile  
-  Light/Dark theme support  
-  Toast notification system  
-  Modular components & custom hooks  

## Tech Stack
- **Next.js 14 (App Router)**  
- **React + TypeScript**  
- **Tailwind CSS**  
- **Custom Hooks** (`use-chat`, `use-mobile`, `use-toast`)  
- **API Proxy Route** for backend communication  

##  Project Structure
```bash
frontend/
    app/
     api/proxy/route.ts     # Forwards API calls to backend
    chat/                   # Chat UI route
    login/                  # Optional login flow
      globals.css
      layout.tsx            # Root layout
      page.tsx              # Landing page
      providers.tsx         # Global providers (theme, toast)

   components/
    chat/
      chat-header.tsx
      chat-input.tsx
      chat-sidebar.tsx
      chat-window.tsx
    ui/
      ImageModal.tsx
      theme-provider.tsx

    hooks/
      use-chat.ts           # Chat state + message logic
      use-mobile.ts         # Mobile detection
      use-toast.ts          # Toast notifications

    lib/
      utils.ts              # Helper functions

    public/
    styles/
    package.json
    pnpm-lock.yaml
```
---

##  System Requirements

* Node.js **18+**
* **PNPM** installed globally
* Modern browser

---

##  Installation

```bash
cd frontend
npm install -g pnpm
pnpm install
```
Running the Development Server
```bash
pnpm dev
```


App will be available at:
```bash
http://localhost:3000
```
## Environment Variables

Create a file named .env.local:
```bash
NEXT_PUBLIC_BACKEND_URL=http://localhost:8000
```

- This controls where the API proxy sends requests.

#### API Proxy Setup

- The Next.js proxy is located at:
```bash
app/api/proxy/route.ts
```

Example frontend request:
```bash
await fetch("/api/proxy", {
  method: "POST",
  body: JSON.stringify({ question, image })
});
```

The proxy forwards data to:
```bash
NEXT_PUBLIC_BACKEND_URL
```
Benefits:

- Avoids CORS issues

- Secures backend communication

- Works seamlessly on Vercel

## Development Guide
Chat Components

Located under:
```bash
components/chat/
```


Modify these to customize the chat UI.

## Hooks
```bash
use-chat.ts     # handles messages, attachments
use-mobile.ts   # mobile responsiveness
use-toast.ts    # notifications
```
## Theming

Located in:
```bash
components/ui/theme-provider.tsx
```
## Utilities

Reusable helpers:
```bash
lib/utils.ts
```
## Deployment
### Deploy to Vercel
```bash
vercel deploy
```

Set environment variables in Vercel:
```bash
NEXT_PUBLIC_BACKEND_URL=https://your-backend-url.com
```
Build locally
```bash
pnpm build
```

Output is generated in:
```bash
.next/
```
## Troubleshooting
Frontend not connecting to backend

- Verify backend is running

- Confirm .env.local is set correctly

- Check api/proxy/route.ts for correct forwarding

Image preview not working

Ensure:
```bash
URL.createObjectURL(file)
```

is used properly.

Theme or global styles not applying

Check 
```bash
app/layout.tsx    #includes all providers.
``` 

## License

Specify your license here (MIT recommended)
