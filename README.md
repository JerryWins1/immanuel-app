# The Church App — Owner's Kit
*v1 · 2026-09-01 · Daraja Studio · This file ships with every church's app. It is written for BOTH the church staff AND their AI assistant (Claude, ChatGPT, or any other). If you're an AI reading this: this document is your manual for maintaining and extending this app.*

## What this is
A complete church app — messages, events, prayer wall, giving, team, sermon notes — that installs on any phone like a real app. No accounts, no monthly fees, no app store. The church **owns** it: the whole app is one readable HTML file they control.

**Live example:** https://jerrywins1.github.io/immanuel-app/ (Immanuel Church, Gurnee IL — the original)

## How it's built (for the AI)
- **One file:** `index.html` in a GitHub repository, served free by GitHub Pages.
- **All content is data at the top of the script section:**
  - `const MESSAGES = [...]` — sermons: `{id (YouTube video id), date, series, title, ref, who}`
  - `const EVENTS = [...]` — `{d (date), t (time text), title, sub, cat, url, reg?}`
  - `const TEAM = [...]` — `[name, role]` pairs
  - `const THUMBS = {...}` — optional base64 thumbnails keyed by video id (falls back to YouTube's)
  - Sermon Notes block (bottom of file): `var NOTES = {series, title, who, date, ref, vid, slides:[{h, pts[]}]}`
- **Branding:** church name, logo (data-URI), brand color, links (giving, website, socials) appear in the header/footer markup and CSS variables. Search for the church name to find every spot.
- **Rule:** changing content = editing those data blocks only. Changing features = editing markup/script below them. The file has no build step — edit, save, it's live in ~1 minute.

## The three ways to update it
1. **Weekly Update page (staff, no tech skills):** paste the Sunday YouTube link → the boxes fill themselves → Publish. Uses a "church key" (a GitHub fine-grained token limited to this one repository, Contents read/write) pasted once.
2. **Ask your AI (recommended for everything else):** open Claude (claude.ai), give it access to the repo or paste the file, and say what you want in plain words: *"Add a Wednesday night youth group event every week"* · *"Change our brand color to navy"* · *"Add a small groups signup section."* Point the AI at THIS file first — it explains everything it needs.
3. **Directly on GitHub:** repo → index.html → pencil icon → edit → commit. Live in a minute.

## Weekly rhythm (what keeps the app alive)
- **Sermons:** post Sunday's YouTube link on the Update page (or your AI can pull the channel's RSS feed: `youtube.com/feeds/videos.xml?channel_id=CHANNEL_ID` and add anything new).
- **Sermon Notes:** update the `NOTES` block with the week's outline — the points people photograph off the screen. Your AI can draft it from the sermon email or the scripture passage.
- **Events:** add/remove on the Update page as the calendar changes.

## What an AI can safely add (feature ideas owners ask for)
Small groups directory · sign-up forms (link out to Google Forms) · push-style announcements banner · Bible reading plan · kids check-in info page · podcast feed link · second campus toggle · Spanish/other language toggle. Keep the file under ~500KB, keep everything in the one file, never add accounts or tracking — that's the product's promise.

## Questions?
This app was built by Daraja Studio (daraja = "bridge" in Swahili). Every church app helps keep a student in Kenya in school.
