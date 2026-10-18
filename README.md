# Milestone 1 hardening: how to apply

Order matters. Do these in this order:

1. Supabase -> SQL Editor: run `patch_m1.sql` (safe to repeat, deletes nothing).
   It marks your older sites with `classic='1'` so they keep their template.
2. Upload `cms.js`, `admin.html`, `index.html` (only change: `cms.js?v=8` -> `?v=9`). Keep `classic.html` and `setup.sql` as they are.
3. Hard-refresh the admin and open each site once to confirm it looks the same.

If you upload `cms.js` BEFORE step 1, older sites lose the classic template until you run the SQL.

## What changed
- classic template shows only when `classic = '1'` (it can no longer come back by accident).
- `?site=` works only on preview addresses (vercel.app / localhost), never on a real domain.
- Contact and subscribe forms: length and email checks.
- Domain verification tokens are now random UUIDs.
- Activity log accepts only clean short action names.

## Test it yourself (needs Postgres, no Supabase)
`bash run.sh` builds a stub database from `setup.sql` + this patch, then
`psql -d t -f tests.sql` runs 64 checks across 2+ websites. Result: all pass.
This tests the SQL rules. It does NOT test Supabase email/phone/Google provider settings.

## Still on you (cannot be done from code)
- Supabase -> Auth -> Providers: enable Phone + an SMS provider (Twilio etc.) for +880 login. Enable Google if wanted.
- Auth -> URL Configuration: add your admin URL to Redirect URLs (needed for password reset).
- Auth -> Email: set up SMTP (default Supabase mail is rate-limited, not for business).
- Add each domain in your host (Vercel), then set DNS: CNAME/A to the host + the TXT record shown in Domains.
- Open signups: anyone can create an account (they see no websites, so no data), and invitations are accepted when the invited person signs up. If you turn signups off, create new users from the Supabase dashboard instead.
