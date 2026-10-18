# Step 2c - Dropdown menus

## Install (this order)
1. Supabase -> SQL Editor -> New query -> paste ALL of `dropdown_m5.sql` -> Run ("Success. No rows returned").
   (Needs the earlier SQL files. It adds one column, one safety rule, and widens one view.)
2. Upload `admin.html`, `cms.js`, `index.html`. Hard refresh (Ctrl+Shift+R).

## How to use
Admin -> Pages -> on a page press **Under…** -> type the number of the parent page (0 = normal menu item).
The parent shows a small arrow and opens a dropdown with its sub-pages (hover/keyboard on computers; indented list inside the phone menu).
The parent stays highlighted while you are on one of its sub-pages. Order inside the dropdown follows the ↑ ↓ order.

## Rules (enforced by the database, not only the screen)
- One level only (no dropdown inside a dropdown).
- The parent must be on the SAME website.
- A page cannot be under itself; a page that already has sub-pages cannot go under another page.
- Deleting a parent keeps its sub-pages as normal menu items. If a parent is hidden or unpublished, its sub-pages show normally.
- If you upload the files before the SQL, the menu simply stays flat (nothing breaks).

## Tested
- 80 database checks + earlier 64: all pass.
- Public menu: dropdown, highlight on child page, parent missing, SQL not run yet, loop in data; no list inside list.
- Admin: "Under…" sets/clears the parent; all earlier admin and public tests still pass.
- NOT tested: real phones/browsers (hover vs touch on tablets), your real Supabase.

## Not done yet
Home/section order in the menu, social-app link previews + sitemap (needs a small Vercel function).
