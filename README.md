# Step 1 - Pages (multi-page websites)

## Install (in this order)
1. Supabase -> SQL Editor -> New query -> paste ALL of `pages_m2.sql` -> Run. Expect "Success. No rows returned".
   (It only ADDS two tables, a view and two functions. Your home page and data are not touched.)
2. Upload `admin.html`, `cms.js`, `index.html` (cms.js is now `?v=10`). Hard refresh (Ctrl+Shift+R).
3. Open the admin -> Pages & Content -> **Pages**.

If you upload the files before the SQL, the Pages screen just says "run pages_m2.sql". Nothing else breaks.

## How it works
- **Home** stays exactly as before (same builder, same publish).
- **New page** creates a draft with its own address: `index.html?page=about`.
- Each page has its own draft (autosave), Publish, Unpublish, Duplicate, Delete (admins only), search, and version history (last 25 publishes; "Restore as draft").
- Visitors only see PUBLISHED pages. Drafts are never readable by visitors (database rule, tested).
- Brand, colours and menu are shared by the whole website. If you change them while editing a page, Publish warns you and does not save them from the page.

## Tested
- 51 database checks (2 websites, owner/admin/editor/viewer/stranger/visitor): all pass. The earlier 64 checks still pass.
- Admin screen (list, search, open, publish, create) and public pages (home, page, missing page, bad address) tested in a simulated browser: no errors.
- NOT tested: your real Supabase project and real browsers. Please try: create a page, add a section, Publish, open the link.

## Known limits (next steps)
- The top menu on an extra page only lists that page's sections. Add a "Home" link in Menu & header for now. A real menu builder is Step 2.
- No canonical/Open Graph/social image yet, no templates, no scheduled publish (Steps 2 and 4).
- Clean addresses like /about need a host rewrite; `?page=about` works everywhere today.
