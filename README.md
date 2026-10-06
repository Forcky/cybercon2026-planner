# CyberCon 2026 Planner (unofficial)

> **Unofficial.** An independent attendee tool for CyberCon 2026 (Melbourne, 14–16 October 2026).
> Not affiliated with or endorsed by AISA, CyberCon or MCEC.

**Live:** https://green-bay-0caaeff00.3.azurestaticapps.net · **Feedback:** [open an issue](../../issues/new/choose)

A single-page, offline-capable planner for the conference program:

- **Browse** all sessions with search, day, theme, topic, format, audience and location filters; hide what you're not interested in
- **My plan**: Going / Maybe, clash detection, locks, backup sessions, walking times between rooms, day timelines and calendar (.ics) export
- **Now**: what you're in, what's next, when to leave and how far to walk
- **Venue map**: interactive MCEC floor plans with room pins and routes that follow the corridors
- **Colleagues**: share your plan as a link, compare plans, see sessions in common and free time together
- Installs to your phone's home screen and keeps working without Wi-Fi

Your plan never leaves your browser. There are no accounts and no tracking.

## How it's built

```text
src/planner.html        the app (HTML, CSS and JS in one file) with build-time placeholders
data/program.json       session facts from the official program, plus search keywords
data/program-changes.json  rooms/times/titles that changed after the first snapshot
tools/build.py          builds the site
tools/update_program.py refreshes data/ from the official program
```

```powershell
pip install pillow
python tools/build.py        # -> dist/public (open dist/public/index.html, or serve the folder)
```

### What's deliberately not in this repo

The session abstracts are AISA's text and the floor plans are MCEC's artwork, so neither is published here.
The public site links to the official session pages for abstracts and loads the floor plans from MCEC's own
published guide. A separate private repo holds that content and builds a full personal edition from this code
(`python tools/build.py --private <dir>`). The **Build** workflow runs `tools/build.py --check` on every push and
pull request to make sure none of it ends up here.

### Security

This repo has no secrets and no deploy credentials. Its workflow only builds and checks the public edition with a
read-only token; deployment happens from the private repo. Actions are pinned to commit SHAs.

## Feedback and contributions

Bugs, ideas and map corrections are very welcome: use the **Feedback** links in the planner (they pre-fill the page,
device and version) or [open an issue](../../issues/new/choose). Room positions and walking times are estimates
traced from MCEC's published plans, so corrections from people on site are especially useful.

---

Built by [@UppyAU](https://github.com/UppyAU).
