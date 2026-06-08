---
name: resume-builder
description: >
  Resume Builder — launches an interactive web app pre-loaded with Sandeep Goyal's resume data.
  Features a live two-panel interface: left editor (Header, Experience, Sidebar, Tips tabs) and
  right live preview matching his exact two-column navy/blue design. Includes one-click PDF export,
  auto metric highlighting (numbers/$/%  get blue pill badges), company logo badges (Intuit blue,
  Oracle red), LinkedIn/GitHub/Gmail clickable links in the header, executive stat chips, and a
  five-nines availability ticker in the profile. Use this skill whenever someone says: "open resume
  builder", "edit my resume", "launch resume app", "update my resume", "export my resume as PDF",
  "show resume builder", or any request to view, edit, or improve Sandeep's resume interactively.
---

# Resume Builder Skill

Launches the interactive resume builder web app at `http://localhost:7799` and opens it in the
browser. The app is a self-contained HTML file pre-loaded with Sandeep Goyal's full resume data.

---

## How to Launch

```bash
# Start the server (idempotent — safe to run if already running)
cd /Users/sgoyal11/Projects/resume-builder
python3 -m http.server 7799 &>/tmp/resume-server.log &
sleep 1
open http://localhost:7799
```

Then confirm the server is up and tell the user the app is live at `http://localhost:7799`.

---

## App File

```
/Users/sgoyal11/Projects/resume-builder/index.html
```

Photo asset: `/Users/sgoyal11/Projects/resume-builder/photo.jpg`

---

## App Features

### Editor Panel (left)
- **Header tab** — name, tagline, email, website, LinkedIn, GitHub, phone, location, executive profile text
- **Experience tab** — all 7 positions with editable title, company, period, location, and bullet points
- **Sidebar tab** — impact cards, education, certifications, tools & platforms, core competencies
- **Tips tab** — saved improvement suggestions; new notes can be added and persist

All edits update the live preview instantly. Changes persist via `localStorage` on Save.

### Resume Preview (right)
Matches the original two-column PDF layout:
- **Navy gradient header** with name, tagline, two-row contact strip (website/LinkedIn/GitHub on line 1; email/phone/location on line 2), and professional headshot
- **Executive Profile** — 3-sentence summary + 7 stat chips ($200M+, 24,000+, 50%, $7M+, 5,000+, 1,000+, 99.999%)
- **Experience section** — jobs with company logo badges (Intuit = blue, Oracle = red, Tavant = teal), left accent borders, auto metric pills
- **Sidebar** — Executive Impact cards, Education, Certifications, Tools & Platforms, Core Competencies

### Export
Click **⬇ Export PDF** — uses `html2pdf.js` to download `SandeepGoyal_Resume.pdf` directly (no print dialog).

---

## Improvement Suggestions Log

All accepted changes from past sessions are captured here for continuity:

| # | Change | Session |
|---|--------|---------|
| 1 | Added LinkedIn + GitHub fields to header contact row | Session 1 |
| 2 | Changed color scheme from pink/purple → navy blue throughout | Session 1 |
| 3 | Added blue metric pill highlights for numbers/$/%  in bullets and profile | Session 1 |
| 4 | Replaced SG placeholder with real headshot (sandeep photo.png from Desktop) | Session 1 |
| 5 | Increased photo size 1.5x (72px → 108px) | Session 1 |
| 6 | Scaled all resume font sizes 1.25x | Session 1 |
| 7 | Split contact row into 2 lines: web profiles / personal contact | Session 1 |
| 8 | Name color → deep navy (#0a3161) | Session 1 |
| 9 | Visual upgrade: gradient header, section title pills, job left-border accent, impact card styling | Session 1 |
| 10 | Executive Profile → 2-sentence summary + 7 stat chips row | Session 1 |
| 11 | Company logo badges: inline SVGs for Intuit (blue), Oracle (red), Tavant (teal) | Session 1 |
| 12 | Removed duplicate company name next to logo SVG | Session 1 |
| 13 | LinkedIn/GitHub/email → clickable hyperlinks in header | Session 1 |
| 14 | Added Gmail, LinkedIn, GitHub SVG icons to contact row | Session 1 |
| 15 | Added five-nines (99.999%) stat chip to profile metrics row | Session 1 |
| 16 | Added operational excellence bullet to Kubernetes role | Session 1 |
| 17 | Export PDF via html2pdf.js (replaces window.print()) | Session 1 |

---

## When Iterating

After launching the app, apply any user prompts as edits to:
```
/Users/sgoyal11/Projects/resume-builder/index.html
```

Then reload the preview with:
```javascript
window.location.reload()
```

Save accepted improvements to the **Improvement Suggestions Log** above so future sessions
have continuity and don't repeat already-applied changes.

---

## Port & Server Notes

- Default port: **7799**
- If port busy: `kill $(lsof -ti :7799)` then restart
- Server config in: `/Users/sgoyal11/.claude/launch.json` (entry: `resume-builder`)
