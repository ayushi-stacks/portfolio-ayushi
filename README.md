# Ayushi M. — Editorial Portfolio

Single-file, self-contained portfolio site (HTML + CSS + vanilla JS). No build step, no dependencies.

## Run it
Open `index.html` in any modern browser (Chrome/Edge/Firefox recommended — the Education roadmap uses CSS `offset-path` for the moving marker, which degrades gracefully to "no marker" on unsupported browsers).

## Flow (three gated stages)
1. **Hero** — locked. Scroll down or click "Learn more" to advance.
2. **Portfolio cover** — slides up over the hero, reveals the italic "Portfolio" wordmark. From here:
   - Scroll down / click "Enter the work" → advances into the page (About section).
   - Scroll up / click "Back to hero" → returns to the hero.
3. **Page** (About onward) — normal scrolling. At the very top, scrolling up returns you to the Portfolio cover.

## Sections
01 About · 02 Education (heading left, animated roadmap right, matched column heights) · 03 Skills (rotating orbit) · 04 What I Offer · 05 Selected Projects · 06 Hall of Fame · 07 Connect · Footer

## Notes for customizing
- **Education roadmap (02)**: two-column CSS Grid (`.ee-grid`) — text on `.ee-left`, graphic on `.ee-right`; grid `align-items:stretch` plus flex-centering keeps both columns the same height. Node content lives in the `.road-node` blocks inside `#eduexp`. The path shape is defined once in the SVG `<path d="...">` and once (identically) on `.road-marker`'s `offset-path` in the CSS, in a 480×720 coordinate space — keep both `d` strings in sync if you reshape the curve, and keep node `top` values inside roughly 120–600px so cards don't clip the top/bottom edges.
- **Projects (05)**: edit the `projects` array near the bottom of the `<script>` tag — name, tagline, description, tags, wireframe layout keys, and swap the `href="#"` placeholders on the "View case study" / "View project" buttons for real links.
- **Hall of Fame (06)**: edit the `.trophy-card` blocks in the `#halloffame` section (icon, competition name, year, position). The list is duplicated once in the markup for a seamless scrolling loop — edit both copies together.
- **Skills orbit (03)**: each skill is an `.orbit-item` with a `--start` angle (evenly spaced at 36° apart for 10 items). Add/remove items and rebalance the angles (360° ÷ count) to keep spacing even.
- Replace the placeholder portrait SVG in the About section with a real photo.
- Fonts: Playfair Display, Inter, Caveat — loaded from Google Fonts.
- Animation is CSS transitions/keyframes + light vanilla JS (no Framer Motion dependency in this static build).
