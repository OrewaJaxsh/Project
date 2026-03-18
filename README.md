# 🧠 IQ Challenge — Mobile-First Viral Quiz Website

> *"Only 2% can pass this test 😳"*  
> A lightweight, single-file IQ + Personality quiz web app built for maximum engagement, retention, and shareability — optimised for Indian mobile users with Tamil + English mixed content.

---

## 📁 File Structure

```
iq-test.html     ← Entire app (HTML + CSS + JS, single file)
README.md        ← This file
```

No build tools. No dependencies. No framework. Just open the HTML file and it works.

---

## ✨ Features

### User Flow
| Step | Screen | Description |
|------|--------|-------------|
| 1 | Landing | Hook headline, live user count badge, stats |
| 2 | Details | Name input + age group pill selector |
| 3 | Questions | 5 IQ questions, one at a time, 30s timer each |
| 4 | Share Gate | Share to 3 friends to unlock results |
| 5 | Loading | Animated "Calculating IQ..." screen |
| 6 | Result | Personalised IQ score + outcome |
| 7 | Personality Test | Bonus 5-question test to retain users |
| 8 | Personality Result | Type reveal with share + retry options |

### Engagement Mechanics
- **Viral share gate** — users must share to WhatsApp, Instagram, or Telegram before seeing results
- **30-second countdown timer** per question creates urgency
- **Live badge** showing "2,847 people testing now" for social proof
- **Confetti animation** on good scores (Above Average / Genius)
- **Personality Test** immediately after results to prevent drop-off
- **"Compare with Friends"** WhatsApp deep link for organic spread

### IQ Result Tiers
| Score | Result | Label |
|-------|--------|-------|
| 5 / 5 | 🔥 Genius! | IQ 138–152 |
| 3–4 / 5 | 😏 Above Average! | IQ 118–132 |
| 1–2 / 5 | 😳 Hidden Talent! | IQ 98–112 |
| 0 / 5 | 😅 Keep Practising! | IQ 88–102 |

### Personality Types
| Type | Emoji | Trait |
|------|-------|-------|
| The Leader | 🔥 | Bold, decisive, inspires others |
| The Visionary | 🌊 | Creative, imaginative, forward-thinking |
| The Empath | 💛 | Deeply feeling, connective, warm |
| The Analyst | 🧠 | Logical, detail-oriented, problem-solver |

---

## 🌐 Deployment

### Option 1 — Direct (Fastest)
Just upload `iq-test.html` to any static host:

```
Netlify Drop   →  drag & drop at netlify.com/drop
GitHub Pages   →  push to repo, enable Pages in Settings
Vercel         →  vercel --prod
Cloudflare Pages → connect repo or drag & drop
```

### Option 2 — Rename to index.html
```bash
cp iq-test.html index.html
```
Then host anywhere that serves static files.

### Option 3 — Local Preview
```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```
Then open `http://localhost:8080/iq-test.html`

---

## 🎨 Design System

| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#0a0a0f` | Page background |
| `--surface` | `#13131f` | Cards, inputs |
| `--accent` | `#7c3aed` | Primary purple |
| `--accent2` | `#a855f7` | Gradients, highlights |
| `--gold` | `#f59e0b` | Result titles, CTAs |
| `--green` | `#10b981` | Correct answers |
| `--red` | `#ef4444` | Wrong answers |

**Font:** Space Grotesk (display) + Noto Sans Tamil (Tamil script) — loaded from Google Fonts.

---

## ✏️ Customisation

### Change Questions
Find the `questions` array in the `<script>` block:
```js
const questions = [
  {
    text: "Your question here",
    tamil: "Tamil translation or hint here",
    options: ["Option A", "Option B", "Option C", "Option D"],
    correct: 0   // index of correct answer (0–3)
  },
  // ...
];
```

### Change Personality Questions
Find the `personalityQ` array and edit similarly. No correct answer needed — just 4 options per question.

### Update Share Text
Search for `shareText` in the JS and update the message template:
```js
const shareText = `Your custom message here ${window.location.href}`;
```

### Change Branding / Colors
Edit the `:root` CSS variables at the top of the `<style>` block.

### Add More Result Tiers
In the `showResult()` function, adjust the `if/else if` score thresholds and outcome objects.

---

## 📱 Mobile Optimisation

- `max-width: 480px` centered layout — feels native on phones
- `font-size: 16px` on inputs — prevents iOS zoom on focus
- `touch-action` friendly — no hover-dependent interactions
- Minimal network requests — only Google Fonts CDN call
- No images — all visuals use emoji + CSS
- Total page weight: **~18KB** (excluding fonts)

---

## 🔒 Share Gate Logic

The share gate tracks clicks on the three share buttons and fills progress dots:

```
Button clicked → shareCount++
shareCount reaches 3 → auto-advance to Loading screen
```

> **Note:** The gate counts *button clicks*, not actual shares. This is intentional — requiring verified shares would need a backend. For a stricter gate, you can integrate the Web Share API or a URL shortener with click tracking.

---

## 🚀 Ideas to Extend

- **Backend score storage** — save results to Firebase / Supabase for leaderboards
- **More tests** — Luck Test, Memory Test, Reflex Test, Emotional IQ
- **AdSense integration** — add a banner after the result screen
- **PWA support** — add a manifest + service worker to make it installable
- **Analytics** — drop in Google Analytics or Plausible for funnel tracking
- **Localisation** — add more Indian languages (Hindi, Telugu, Kannada)

---

## 📄 License

Free to use, modify, and deploy for personal or commercial projects.  
Attribution appreciated but not required.

---

*Built as a single HTML file — fast, shareable, and zero-dependency.*
