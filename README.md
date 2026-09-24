# Legacy Ventures website

Static site for legacyventures.global. One page (`index.html`) with client-side routing, plus `assets/`.

## Deploy on Vercel
1. Push this folder to a GitHub repository (or upload the files through GitHub's web interface).
2. In Vercel: Add New > Project > import the repository. Framework preset: **Other**. No build command, output directory: leave empty.
3. Deploy. Then add the domain `legacyventures.global` under Project > Settings > Domains and point the domain's DNS at Vercel as instructed there.

Routes like `/about` and `/accelerator` are rewritten to `index.html` by `vercel.json`, so shared links work.

## Turn on real login (Supabase, free tier)
The Log in / Sign up / Reset password pages are wired for Supabase Auth. Until keys are added they run in waitlist mode.
1. Create a project at supabase.com. In Authentication > Providers, enable Email.
2. In Project Settings > API copy the Project URL and the anon public key.
3. In `index.html` find `const LV_AUTH = { supabaseUrl: "", supabaseAnonKey: "" };` and paste both values.
4. In Supabase Authentication > URL Configuration set Site URL to `https://www.legacyventures.global` and add `https://www.legacyventures.global/#login` to Redirect URLs.
5. Redeploy. Sign-up sends a confirmation email; log-in shows the account page.

## Forms
The waitlist and newsletter forms currently show a thank-you message only. Connect them to a form backend (Formspree, Tally, a Supabase table, or Google Sheets via n8n) when ready: see `wireForm()` in `index.html`.

## Photos
`assets/people/` holds mentor and team photos (600x600 JPEG). Add or replace files there and update the `mentors` / `team` arrays in `index.html`.
