# Step 2a - Pages appear in the top menu automatically

## Install (this order)
1. Supabase -> SQL Editor -> New query -> paste ALL of `menu_m3.sql` -> Run ("Success. No rows returned").
   (Needs pages_m2.sql from the previous step. It only adds 2 columns and widens one view.)
2. Upload `admin.html`, `cms.js`, `index.html`. Hard refresh (Ctrl+Shift+R).

If you upload the files first, nothing breaks: the menu simply shows no pages until the SQL is run.

## What you get
- Every PUBLISHED page appears in the top menu by itself: Home, then your pages, then sections/extra links.
- The page you are on is highlighted. Home link appears on every page.
- Pages -> each page now has: "In menu / Not in menu", "Menu name", up/down arrows (order).
- Menu tab shows exactly what visitors get. The admin preview shows the same menu.
- Sites with no pages: menu unchanged. Classic-template sites keep their old items; pages are added after them.

## Tested
- 62 database checks (menu flag, label length, order, visitors, editor/viewer/other-site) + earlier 64: all pass.
- Public menu in a simulated browser: home, sub-page (highlight), real domain, classic site, no pages, database without the new SQL.
- Admin buttons (toggle, move, menu name) and Menu tab: no errors.
- NOT tested: your real Supabase and real phones. Please try it.

## Next
Step 2b: nested (dropdown) menus + custom order of Home/sections, then SEO fields (canonical, Open Graph).
