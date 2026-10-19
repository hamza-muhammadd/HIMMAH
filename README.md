# Step 2d - Look & feel polish (no SQL this time)

## Install
Upload `admin.html` and `index.html` (`cms.js` is unchanged but included). Hard refresh (Ctrl+Shift+R). No Supabase step.

## Public menu / dropdown
- Dropdown fades and slides in (0.16s), has padding, rounded hover rows, an active row, and a rotating arrow.
- Keyboard: Tab opens it, Escape closes it. Clear focus outline.
- Touch tablets (wider than 900px): first tap opens the dropdown, second tap opens the page.
- Phone: sub-pages are grouped under the parent with a guide line and calmer text; the menu scrolls if it is long.
- The dropdown opens from the right edge for the last two items so it never goes off screen.
- Respects "reduce motion".

## Admin -> Pages
- One row = title, status, small chips (In menu / Under X / Unpublished changes) + only Edit, View and a "..." menu.
- "..." menu: Publish/Unpublish, Duplicate, Version history, Remove from menu, Menu name, Put under a page, Move up/down, Delete.
- Sub-pages are indented under their parent. Header shows "5 pages, 4 published". Better empty state.
- The "..." menu closes on click-outside/Escape and opens upward when there is no room below.
- Move up/down now moves a page among its siblings (top-level among top-level, sub-pages inside their parent).

## Checked
Rendered in a real Chromium (desktop 1280px and phone 390px) - see /screenshots. Fonts in the screenshots are fallbacks
(web fonts are blocked in my test), your real fonts will look a little different.
All earlier tests still pass (80 + 64 database checks, public and admin tests).
