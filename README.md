# CJ Legacy Care — Static Demonstration Prototype

A **static, front-end-only, interactive demonstration** of the CJ Legacy Care caregiving app concept. It uses entirely **fictional demonstration data** (a sample care recipient, "Evelyn Carter," and a sample family) and runs completely in the browser — there is nothing to install and no server to run.

A gold **"Prototype Demonstration — Fictional Data Only"** notice is visible on every screen of the app as a constant reminder of this.

## What this demonstration is NOT

This prototype is **not connected to any real backend**. Specifically, it does not include, require, or transmit data to:
- A real database or permanent storage of any kind
- A real authentication/login service
- A file-storage service
- A messaging service
- An email or text-notification service
- A real healthcare system or medical record system
- The Anthropic API or any other live AI service

**No API key, token, secret, or credential of any kind appears anywhere in this code.** The "Generate Plain-Language Draft" feature does not make a network request — it fills in a clearly labeled, prewritten fictional placeholder (`[Simulated demo output]`) entirely within the browser.

## What is simulated, and how it's labeled

| Feature | What happens | How it's labeled |
|---|---|---|
| Account login / user roles | A local toggle switches the demo view between "Primary Caregiver" and "Family Team" | Profile page states plainly this is not a real login and permissions are not production security controls |
| Family Care Village invitations | Adds a row to the local family list | Form says no real invite email is sent |
| Document uploads | File stays in browser memory for the session only | Upload button says not to upload real documents; nothing is transmitted, analyzed, or stored |
| AI-generated visit summaries | Static placeholder text, no network call | Disclaimer above the button explains the draft is simulated |
| Messaging (group + direct) | Messages are held in browser memory only | Chat tab states messages aren't sent to a real messaging service |
| Notifications ("notify the family team") | Illustrative status text only | Tasks tab states no real emails, texts, or push alerts are sent |
| All data (visits, tasks, meds, notes, messages) | Lives only in this browser tab | Profile page explains refreshing or closing the page erases everything, restoring the original fictional sample automatically |

## Reset Demo

The Profile page (tap the "EC" avatar, top right) includes a **Reset Demo to Sample Data** button that restores the original fictional dataset at any time, with a confirmation prompt first. The same thing happens automatically if you refresh or close the page, since nothing is ever saved.

## Accessibility

- All clickable actions are real `<button>` elements (not `<div>`/`<span>` with only a click handler), so they're reachable and operable by keyboard.
- Form fields have `<label for="...">` associations; icon-only or visually-implicit controls have `aria-label` attributes.
- Visible focus outlines are present on all interactive elements for keyboard navigation.
- Text/background color pairs were checked against WCAG AA (4.5:1 for normal text) and adjusted where needed — this was a values-only fix, not a redesign; the palette, layout, and visual identity are unchanged.

This pass covers the basics above; it is not a full accessibility audit.

## How to run it locally

No build step, no dependencies. Any of these work:
- Double-click `index.html` to open it directly in a browser
- Or serve the folder locally: `python3 -m http.server` from this directory, then visit `http://localhost:8000`

## How to deploy it as a static website

Upload this folder as-is to any static host, with `index.html` as the site root:
- **GitHub Pages** — push to a repo, enable Pages on the branch/folder
- **Netlify / Vercel** — drag-and-drop the folder in their dashboard, or connect a repo
- **Any S3 bucket / static file host** — upload the files and enable static website hosting

The only external resource loaded is Google Fonts (Source Serif 4 / Public Sans). If unavailable, the page falls back to system fonts and still works.

## Files in this package

- `index.html` — the entire application (HTML, CSS, and JavaScript, self-contained)
- `README.md` — this file

## Pre-delivery verification performed

- Opened the app and confirmed all six tabs (Dashboard, Visits, Meds, Family, Tasks, Chat) and all overlays (New Visit, Visit Details, Profile, Log Dose, Add Medication, Invite, New Message, Chat thread) render and navigate correctly
- Walked through the simulated workflows (create a visit, upload a fictional document, generate the simulated draft, approve it, confirm medication changes, create a task, share with the family, log a dose, send messages, add a family note, add a medication, invite a family member, reset the demo)
- Confirmed via search of the source that no `fetch()` call, API endpoint, or credential is present anywhere in the file
- Confirmed every button's `onclick`/`onchange` handler calls a function that actually exists in the script (no dangling references)
- Confirmed the JavaScript parses without syntax errors
- Confirmed refreshing the page and using "Reset Demo" both return the app to the original fictional sample data

## Important notice

This is a **demonstration prototype only**. It is **not secure, not production-ready, not HIPAA-compliant, and must not be used to store, process, or communicate real caregiver, patient, family, or health information.** Use only fictional or sample data when exploring it.

## Turning this into a real product

This prototype's design and workflows are ready to connect to real infrastructure. See the separately provided `backend-architecture-plan.md` for a concrete plan covering real accounts, a database, row-level access control, secure AI integration, and file storage.
