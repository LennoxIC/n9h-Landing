# n9h — Landing Page

A single-file, production-ready landing page prototype for **n9h**, a multi-agent AI orchestration platform. Built as a static HTML/CSS/JS deliverable — no build step, no dependencies to install. Open the file and it runs.

## Files

```
n9h.html   → the entire site (markup, styles, and scripts in one file)
README.md  → this file
```

## Tech Stack

| Layer       | Choice                          | Why |
|-------------|----------------------------------|-----|
| Structure   | Static HTML5                    | No build step needed for a prototype/demo this size |
| Styling     | Vanilla CSS (custom properties) | Full control over the design token system, zero framework overhead |
| Animation   | [GSAP](https://gsap.com) + ScrollTrigger | Scroll reveals, counters, timeline progress, hero entrance |
| 3D / WebGL  | [Three.js](https://threejs.org) r128 | Hero background node network with mouse parallax |
| Fonts       | Space Grotesk, IBM Plex Sans, IBM Plex Mono (Google Fonts) | Display / body / mono — ties into the "build hash" brand identity |

All libraries load from `cdnjs.cloudflare.com` — an internet connection is required.

## Running it

Just open `n9h.html` in any modern browser. No server, no `npm install`.

For local development with live-reload, any static server works, e.g.:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Design system

- **Color** — single accent (`--amber: #FF9A3C`) on a near-black neutral scale (`--void`, `--void-2`, `--line`, `--bone`, `--muted`). Deliberately one accent color, not a gradient palette.
- **Type** — Space Grotesk (display), IBM Plex Sans (body), IBM Plex Mono (data, status tags, timestamps).
- **Signature motif** — the "build hash" identity: boot sequence on load, persistent status bar with live uptime, and a live log feed in the Command Center section. This is the one consistent idea the whole page is built around.
- **Motion** — respects `prefers-reduced-motion`; all heavy animation (boot sequence, Three.js background) is disabled for users who request it.

## Sections (in order)

1. Boot sequence (load-time only)
2. Nav
3. Hero — headline, CTAs, Three.js network background
4. Product showcase — 3 feature cards
5. Capabilities — 6 capability cards with cursor-glow hover
6. Command Center — live mock dashboard (agents, log feed, graph)
7. Stats — animated counters on scroll
8. Roadmap — 4-phase timeline with scroll-driven progress line
9. Testimonials
10. Waitlist — functional client-side form (no backend wired yet)
11. Footer
12. Status bar (persistent, fixed)

## Known limitations

- The waitlist form only shows a success state client-side — it does not send data anywhere yet. Wire it to an email service (Resend, Mailchimp API, a Supabase table, etc.) before going live.
- All dashboard data (agent status, stats, log lines) is simulated with `Math.random()` — replace with real API data when available.
- This is a static file, not a Next.js project. If you want the TypeScript/Next.js/Shadcn version with a proper component architecture for a real codebase, that's a separate scaffold — let me know and I'll generate it.

## Customizing

- Copy: all section text lives directly in the HTML, easy to find and edit (`<h1>`, `<p>`, card content).
- Colors/fonts: edit the `:root` custom properties at the top of the `<style>` block — everything else references them.
- Stats: update `data-target` attributes on `.num` elements in the Stats section.
- Roadmap phases: edit `.phase` blocks in the Roadmap section; the progress line scales automatically.
