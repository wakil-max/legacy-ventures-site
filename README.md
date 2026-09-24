# Legacy Ventures website

Static site for legacyventures.global. One page (`index.html`) with client-side routing, plus `assets/`.

## Deploy on Vercel
1. Push this folder to a GitHub repository (or upload the files through GitHub's web interface).
2. In Vercel: Add New > Project > import the repository. Framework preset: **Other**. No build command, output directory: leave empty.
3. Deploy. Then add the domain `legacyventures.global` under Project > Settings > Domains and point the domain's DNS at Vercel as instructed there.

Routes like `/about` and `/accelerator` are rewritten to `index.html` by `vercel.json`, so shared links work.

## Login (Firebase Authentication)
Log in, Sign up, Google sign-in and password reset run on Firebase Authentication, project `legacy-ventures-51b72` (Wakil's Google account, console.firebase.google.com).
- Providers enabled: Email/Password and Google. Manage under Authentication > Sign-in method.
- Authorized domains: legacyventures.global, www.legacyventures.global, legacy-ventures-site.vercel.app. Add any new domain under Authentication > Settings > Authorized domains or Google sign-in will refuse it.
- Users appear under Authentication > Users. The web config is in `index.html` (`FIREBASE_CONFIG`); the apiKey there is a public identifier, not a secret.
- Verification and reset emails come from noreply@legacy-ventures-51b72.firebaseapp.com; customise them under Authentication > Templates.

## Forms
The waitlist and newsletter forms currently show a thank-you message only. Connect them to a form backend (Formspree, Tally, a Supabase table, or Google Sheets via n8n) when ready: see `wireForm()` in `index.html`.

## Photos
`assets/people/` holds mentor and team photos (600x600 JPEG). Add or replace files there and update the `mentors` / `team` arrays in `index.html`.
