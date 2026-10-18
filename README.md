# Step 2b - Logo without white box + SEO (search & sharing)

## Install (this order)
1. Supabase -> SQL Editor -> New query -> paste ALL of `seo_m4.sql` -> Run ("Success. No rows returned").
   (Needs pages_m2.sql and menu_m3.sql from earlier steps. It only widens which fields a page may save.)
2. Upload `admin.html`, `cms.js`, `index.html`. Hard refresh (Ctrl+Shift+R).

## Logo
- Logo uploads already keep PNG transparency. A white box almost always means the PNG FILE itself has a white background.
- New button in Brand -> Logo: **Remove white background**. It removes white that touches the picture's edge, softens the edge,
  trims the empty margin, and saves a clean transparent PNG. White INSIDE your logo (letters, dots) is kept.
- If your logo is not clear after one try, upload a PNG exported with a transparent background (best result).
- The logo image on the website now has no background, border or shadow, whatever the file.
- Works on logos hosted in your storage. If it says it cannot read the picture, upload the file again and retry.

## SEO (per website AND per page)
Brand -> "Search and sharing" now has: tab title, search description, **sharing picture**, **canonical address** (optional),
**"don't list this page"**, and live hints (title 30-60 letters, description 70-160, missing picture...).
- On an extra page these fields belong to THAT page (empty picture = the website's picture; canonical is never copied).
- The website adds: description, og:title/description/image/url, twitter card, canonical link, robots noindex when asked.
- Canonical is automatic on your real domain. It is skipped on *.vercel.app / localhost previews.
- A page that does not exist says "Page not found" and asks search engines not to list it.

## Important limit (honest)
Your site builds each page in the browser. Google runs that code, so title/description/canonical work.
WhatsApp, Telegram, Facebook and X do NOT run it, so link previews with the sharing picture will not show for them yet.
Fixing that needs a small server step (Vercel function that pre-fills the tags). That is a good next step. No sitemap.xml yet either.

## Tested
- 67 database checks (+ earlier 64): all pass.
- White-background remover on a synthetic logo (corners, body, inner white dot, soft edge, crop, all-white picture).
- SEO tags on home, page with own SEO + noindex, inherited picture, preview host, missing page.
- Admin: SEO fields, live hints, noindex warning, logo button safe with no logo; earlier pages/menu tests still pass.
- NOT tested: real photos with complex backgrounds, your real Supabase, real browsers.

## Next
Dropdown (nested) menus, Home/section order, then the server step for social previews + sitemap.
