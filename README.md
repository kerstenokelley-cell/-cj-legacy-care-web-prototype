# CJ Legacy Care — Static Demonstration Prototype

A **static, front-end-only, interactive demonstration** of the CJ Legacy Care caregiving app concept. Entirely fictional demonstration data. No backend, no build step — open `index.html` in a browser and it runs.

A gold **"Prototype Demonstration — Fictional Data Only"** banner is visible on every screen, along with a persistent reminder not to enter real personal, medical, financial, or legal information.

## What's in this version

**Renamed:** "Family Team" is now called **"Family Care Village Member"** everywhere it's shown to the user. The name "Family Care Village" itself is unchanged.

**New sections** (all fictional, all session-only):
- **Cup Check** — a caregiver well-being check-in ("How full is your cup today?") with four levels, a simple visual cup indicator, and a compassionate, non-shaming "Cup Refill" suggestion for whichever level is picked.
- **CareGuide** — type a fictional caregiving question or pick a category (medications, appointment prep, hospital discharge, difficult conversations, caregiver well-being, changing care needs) and get a static, prewritten example response with example resource cards. Clearly states no live AI is used, that it's education/navigation only (not diagnosis, treatment, or emergency advice), and to call 911 in an emergency.
- **Care Hub** — now a fully editable hub, not just a static reference. It opens to a menu of 10 sections (Emergency Quick Reference, Providers, Pharmacy, Insurance, Allergies, Current Medications, Important Documents, Legal & Healthcare Decision-Makers, What Matters Most, and Conditions & Changing Care Needs), each showing an entry count and opening its own list with Add, Edit, and Delete (with a confirmation prompt) for every entry. Multiple entries are supported everywhere it makes sense. **Current Medications is the same live list used by the Medications tab** — there's only one medication array in the app, so edits from either place always match. **Conditions & Changing Care Needs** is a new dated log (date, category, description, current support needed, who recorded it) that always shows the newest update first. Document entries remain demonstrations only — fictional names and descriptions you type, never uploaded, encrypted, or transmitted.
- **Prepare & Transition** — two workflows: "Prepare for a Visit" (reason, concerns, symptoms, medication questions, provider questions, what to bring, attendees) and "Transition of Care" (discharge instructions, medication reconciliation, follow-ups, equipment/home readiness, transportation, meals/support, assigned Family Care Village member, open questions) with a live, session-updatable checklist.

**Navigation:** the bottom nav shows exactly 5 items — **Home**, **Visits**, **Meds**, **Village**, and **More** — kept short so nothing wraps or crowds on mobile. Full page headings ("Dashboard" content, "Medications," "Family Care Village") remain unabbreviated inside each page. **More** contains Tasks, Cup Check, CareGuide, Care Hub, and Prepare & Transition.

**Family Care Village ("Village") is now a hub**, not a flat list — it opens to four compact entry cards (Messages, Village Members, Family Notes, Recent Activity) with short previews, each opening its full view so the landing page stays uncluttered. Group and direct messaging (previously its own "Chat" tab) now live inside Messages here.

**Tasks moved into More**, but stays easy to reach: the Dashboard still shows the open-task count, a "View Tasks →" link right beneath it, and an "Overdue Tasks" section that appears automatically when something's overdue.

## What this demonstration is NOT

Not connected to any real backend, database, authentication service, file-storage service, messaging service, notification service, healthcare system, or AI service. **No API key, token, secret, or credential of any kind appears anywhere in this code**, and no network request is made by any feature. Nothing is described as encrypted, securely stored, or protected by production security controls anywhere in the app — because it isn't.

All data — visits, tasks, medications, messages, notes, Cup Check answers, CareGuide questions, Care Hub info, prep/transition plans — lives only in this browser tab and disappears on refresh. The Profile page has a **Reset Demo** button that restores the original fictional sample data at any time.

## Input handling

Text you type into any field (chat messages, family notes, visit details, CareGuide questions, Prepare & Transition fields, etc.) is escaped before being stored, so it's treated as plain text rather than interpreted as HTML/script when displayed — reducing script-injection risk. **Please don't enter real personal, medical, financial, or legal information into this demo.**

## Accessibility

- All clickable actions are real `<button>` elements.
- Form fields have `<label for="...">` associations or `aria-label`s.
- Visible focus outlines on all interactive elements.
- Text/background colors were checked against WCAG AA contrast and adjusted where needed (values only — no layout or palette redesign).

## How to run it locally

- Double-click `index.html` to open it directly in a browser, or
- `python3 -m http.server` from this directory, then visit `http://localhost:8000`

## How to deploy it as a static website

Upload this folder as-is to any static host with `index.html` as the root — GitHub Pages, Netlify, Vercel, an S3 bucket with static hosting enabled, etc. The only external resource is the Google Fonts CDN (Source Serif 4 / Public Sans); the page falls back to system fonts if it's unavailable.

## Pre-delivery verification performed

- Built an automated Node.js test harness that loads the app's actual JavaScript with stubbed browser APIs and exercises **every** tab, overlay, form, and action function end to end (visit creation → draft simulation → approval → medication confirmation → task creation → sharing; medication add + dose log; family invite + family note; group and direct messaging; Cup Check all four levels; CareGuide free-text and all six categories; Care Hub document buttons; both Prepare & Transition workflows plus the checklist; role switching; Reset Demo) — result: **zero runtime errors**
- Specifically tested script-injection-style input (`<script>`, `onerror=`, quotes, ampersands) in every text field and confirmed the rendered output contains only safely escaped text, with no double-escaping
- Confirmed all empty-field submissions either show a clear validation message or safely no-op — fixed two spots (Family Notes, Transition checklist "Add Item") that previously failed silently, and added a message to CareGuide's Ask button for an empty question
- Added a persistent on-screen reminder not to enter real personal, medical, financial, or legal information (previously this was only in this README)
- Confirmed zero `fetch()` calls, zero network requests, and zero credential-like strings anywhere in the file
- Confirmed no duplicate element IDs and that every `onclick`/`onchange`/`oninput` handler resolves to a real function
- Confirmed zero remaining occurrences of "Family Team" (all renamed to "Family Care Village Member")
- Confirmed both required phrases and the 911/emergency language are present, and that no copy claims real encryption, security, AI, or medical-record access
- Reviewed the mobile layout rules (480px max container width, 380px breakpoint) for the ~375px case

- Ran a dedicated Care Hub test: full add → edit → delete cycle on all 8 reference sections, confirmed medication changes made through the Care Hub immediately appear on the Medications tab (same underlying array, not a duplicate list), confirmed the Conditions & Changing Care Needs log sorts newest-first and auto-records who made each entry, confirmed empty-field validation on every Care Hub form, and confirmed Reset Demo restores all Care Hub data back to the original fictional sample — zero runtime errors

## Important notice

This is a **demonstration prototype only** — not secure, not production-ready, not HIPAA-compliant, and not suitable for storing or communicating real caregiver, patient, family, or health information. Use only fictional or sample data.

## Turning this into a real product

See the separately provided `backend-architecture-plan.md` for a concrete plan covering real accounts, a database, row-level access control, secure AI integration, and file storage.
