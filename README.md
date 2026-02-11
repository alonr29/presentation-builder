# Presentation Agent Builder (Hebrew RTL)

**Presentation Agent Builder** is a 5‑step wizard that helps you create a fully‑formed AI presentation agent in Hebrew: from personal details and persona selection, through context and presentation goal, to a production‑ready prompt you can paste into ChatGPT, Claude, or any other LLM.

The UI is fully RTL, mobile‑friendly, and built with vanilla JavaScript + Tailwind CSS.

---

## Features

### Wizard Flow (5 Steps)

1. **Personal Details** – name & gender (for correct Hebrew addressing).
2. **Persona Selection** – choose the presentation style that fits you.
3. **Professional Context** – role, typical audience, presentation types.
4. **Presentation Topic & Goal** – what the deck is about and what success looks like.
5. **Final Prompt** – a structured, persona‑aware prompt in English (instructions) tailored to your Hebrew use case.

All steps use `localStorage` so data persists across navigation and refreshes.

---

## Personas (8 Total)

The wizard currently supports **8 distinct personas**, each with its own description, tone, and color palette:

- **🧪 Walter White** – presentation scientist, precise and analytical.
- **🥃 Don Draper** – storytelling & nostalgia‑driven marketing master.
- **📎 Michael Scott** – chaotic but lovable creative partner, focused on emotional connection.
- **🦖 Ross Geller** – methodical professor, explains the “why” behind every detail.
- **👔 Sheryl Sandberg** – data‑driven yet empathetic leadership strategist.
- **🚀 Elon Musk** – bold, first‑principles presentation architect.
- **🍎 Steve Jobs** – minimalist storyteller, “one more thing” moments and radical simplicity.
- **💬 Oprah Winfrey** – empathetic, inspirational coach focused on human connection.

The chosen persona influences:

- The **tone and style** of the final prompt.
- The **styling color accents** in the final step.
- The **speaker notes and narrative guidance** requested from the AI.

---

## Dark Mode

The app includes a global **Dark Mode toggle** visible on all pages:

- Floating button in the top‑left corner (desktop & mobile).
- Uses Tailwind’s `dark` mode (`darkMode: 'class'`).
- Key UI elements support light/dark variants (backgrounds, borders, text).
- The current theme is persisted in `localStorage` under `theme` (`light` / `dark`).
- On load, the app reads the saved theme and applies it automatically.

This keeps the wizard comfortable to use in both bright and low‑light environments.

---

## Privacy‑Friendly Analytics

The project includes a **very lightweight, privacy‑friendly analytics layer**:

- Implemented via `fetch` calls to **CountAPI**:
  - One counter per page (home, step1–step5).
  - One counter per persona selection (e.g. `persona-walter_white`, `persona-oprah_winfrey`).
  - One counter tracking successful prompt copies (`prompt-copied`).
- **No personal data** is sent:
  - Only the page name / persona ID and an increment operation.
  - No IPs, no user IDs, no cookies.
- Analytics are **disabled on localhost** to keep local development noise‑free.
- A simple public stats endpoint is linked from step 5:
  - `https://api.countapi.xyz/stats/presentation-builder-alonr29`

This gives a high‑level picture of usage and popular personas without compromising user privacy.

---

## Tech Stack

- **HTML5** – static multi‑page wizard (`index.html`, `step1.html` … `step5.html`).
- **Tailwind CSS (CDN)** – utility‑first styling, with:
  - `darkMode: 'class'` configuration.
  - Heebo font as the default `font-sans`.
  - Responsive grid layout for persona cards (`grid-cols-1 sm:grid-cols-2 lg:grid-cols-4`).
- **Vanilla JavaScript**:
  - Form validation (client‑side, with Hebrew messages).
  - `localStorage` for step data and theme persistence.
  - Persona selection logic & prompt construction.
  - Dark mode toggle across all pages.
  - Lightweight analytics tracking (page views, persona hits, prompt copies).
- **Heebo (Google Fonts)** – modern Hebrew‑friendly typeface.

---

## Running Locally

No build step is required.

1. Clone or download the repository.
2. Open `index.html` directly in your browser **or** serve via a simple static server:

```bash
cd Presentation-Agent-Builder
python -m http.server 8000
# or: npx serve .
```

3. Navigate to `http://localhost:8000/index.html`.

Analytics calls are automatically disabled on `localhost` and `127.0.0.1`.

---

## Future Ideas

- Export final prompt + context as a downloadable `.txt` / `.md` file.
- Add more persona “families” (e.g. educators, product managers, founders).
- Add optional “advanced settings” step for slide count, time limit, or language variations.

