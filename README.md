# Super Helper App — Career Day Demo

**Live site:** https://super-helper-app.vercel.app

A small, polished, offline web app for an elementary school Career Day presentation. Built to help kids understand what software engineers do by showing — live — how an app takes an input, follows instructions, and gives back an output.

---

## How to Run

1. Download or clone this folder to your laptop.
2. Open `index.html` in any browser (Chrome, Edge, Firefox, Safari).
3. Put the browser in full-screen mode — press **F11** on Windows or **Cmd+Ctrl+F** on Mac.
4. Click every button at least once to make sure everything works before you walk in.

No internet required. No install required. Just open the file.

---

## How to Present

See `presenter-guide.md` for full scripts in three lengths:

| Session length | What you cover |
|---|---|
| 10 minutes | Input → Code → Output, one bug demo |
| 20–25 minutes | Full demo + live feature builder |
| 40–45 minutes | Full demo + paper activity sheets |

The short version of the demo sequence:
1. Click a category button (the class votes).
2. Read the output.
3. Click **Show code** — explain the instruction.
4. Click **Make a bug** — show what goes wrong.
5. Click **Fix bug** — show the fix.
6. Click **Mystery feature** — ask for ideas.
7. Type the class idea into the Feature Builder → **Add feature**.
8. Let a student press the new button.

---

## Files Included

| File | What it is |
|---|---|
| `index.html` | The app — open this to run the demo |
| `printable-cards.html` | Concept cards (INPUT, CODE, OUTPUT, BUG, FIX) + activity sheet — print before the event |
| `presenter-guide.md` | Full scripts, suggested questions, backup plan |
| `buildspec.md` | Original product specification |
| `README.md` | This file |

---

## Printing the Cards

1. Open `printable-cards.html` in a browser.
2. Press **Ctrl+P** (Windows) or **Cmd+P** (Mac).
3. Turn off "Print background graphics" if your printer asks.
4. Each card prints on its own page.
5. The last page is the **Design Your Own App** activity sheet — print one per student for the 40-minute session.

---

## Privacy Note

This app does **not**:
- Collect student names, photos, audio, or location data.
- Store anything in cookies, localStorage, or a database.
- Make any network requests.
- send any data anywhere, ever.

Everything resets when the page refreshes.

During the demo, do not type student names into the Feature Builder or app name field.

---

## Troubleshooting

**Browser opens but the app looks blank.**
Try a different browser. Chrome or Edge are the most reliable for local HTML files.

**Buttons are not responding.**
Make sure JavaScript is enabled. On most browsers it is on by default.

**Text looks too small on the projector.**
Press **Ctrl++** (or **Cmd++** on Mac) a few times to zoom in. The layout will reflow cleanly.

**No projector / the laptop dies.**
Use the printed concept cards and run the backup plan from the presenter guide. Hold up each card and narrate the demo manually — it works great with kids.

**The feature builder button is missing.**
Scroll down on the page. The feature builder is below the main app grid.
