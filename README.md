# Open Studio AI

Free, unlimited AI assistant — chat, image generation, image editing, and voice — built as a mobile-first Progressive Web App (PWA). No API key, no backend, no subscription. Powered by Puter.js (free keyless AI access).

Developed by **Hasnain Sheikh**.

---

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The entire app (UI + logic) |
| `manifest.json` | Makes the site installable as an app (PWA) |
| `sw.js` | Service worker — enables offline use and instant updates |
| `icon-192.png` / `icon-512.png` | App icons (you add these — see below) |

---

## How to deploy (GitHub Pages, mobile-only)

1. Open your GitHub repo in Chrome.
2. Delete/replace your old `index.html`, `manifest.json`, and `sw.js` with these new files.
3. Commit the changes directly on GitHub (Add file → Upload files, or edit each file and commit).
4. Wait 30–60 seconds for GitHub Pages to rebuild.
5. Open your live link (e.g. `https://yourusername.github.io/your-repo/`) in a **fresh tab** to test.

### App icons
Add two square PNG images named exactly `icon-192.png` (192×192px) and `icon-512.png` (512×512px) to the same folder as `index.html`. You can make these free at canva.com or similar, mobile-friendly.

---

## What was fixed this time

Your previous version failed on every image-related action. The root cause: Puter.js requires the AI **provider** to be explicitly stated when you send an image along with a prompt (image editing) — otherwise the request fails silently with no useful error. This version:

- Explicitly sets `provider: 'gemini'` for image editing
- Explicitly sets `provider: 'openai-image-generation'` for image generation
- Shows the **real error message** on screen if anything fails, instead of just going silent — so if something ever breaks again, you'll immediately see why
- Removed the old email-gate and unused cloud-logging code that added risk without any benefit
- Service worker now uses a "network-first" strategy — meaning every time you open the app with internet, it fetches the newest version first. No more stuck-on-old-version problems. (Old cached version is only used if you're fully offline.)

---

## Features

- **Chat** — full conversational AI, remembers context within a conversation
- **Image generation** — tap the image icon, describe what you want
- **Image editing** — tap the paperclip/gallery icon, attach a photo, describe the edit
- **Voice input** — tap the mic icon and speak (uses your device's built-in speech recognition)
- **Voice output** — tap "read aloud" under any AI reply, or turn on auto-read in Settings → Appearance
- **Multiple conversations** — sidebar keeps a history of every chat, switch anytime
- **Settings (ChatGPT-style)**:
  - **Account** — set a display name, sign in/out with a free Puter account (optional — guest use works fully too)
  - **Appearance** — dark/light theme, auto-read toggle
  - **Data controls** — see how many conversations are stored, clear them all
  - **About** — app info

---

## Notes

- Conversations are stored only on your device (local storage), so they stay private but won't sync across devices unless you add cloud storage later.
- Signing in with Puter is optional — it doesn't cost anything and doesn't require a card, but the app works fully without it too.
- Everything runs client-side; there is no server to maintain or pay for.

---

Open Studio AI — Developed by Hasnain Sheikh
