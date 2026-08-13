# Beit Iran — Storefront

A ready-to-deploy React + Vite + Tailwind site.

## Deploy to Vercel (free, ~10 minutes)

1. Create a free account at https://github.com and https://vercel.com
   (you can sign into Vercel directly with your GitHub account).
2. On github.com, create a new repository (e.g. `beit-iran-store`) and
   upload every file in this folder using the "Add file → Upload files"
   button in the browser — no command line needed.
3. On vercel.com, click "Add New… → Project", choose "Import" and select
   the repository you just created. Leave all settings on their defaults
   (Vercel auto-detects Vite) and click "Deploy".
4. In a minute or two you'll get a free live link like
   `beit-iran-store.vercel.app`.

## Connect the domain beitiran.com

1. Buy the domain from a registrar (Namecheap, GoDaddy, etc.) — usually
   $10–15/year.
2. In your Vercel project, go to Settings → Domains → add `beitiran.com`.
3. Vercel will show you 1–2 DNS records to add at your registrar
   (usually an A record and a CNAME). Add them there — it can take a
   few hours to go live.

## IMPORTANT — order storage after deploying

This site was originally built inside Claude, which provides a special
`window.storage` API for saving orders. That API does **not** exist on a
normal website. The code already falls back to the browser's
`localStorage` automatically — but that only stores orders on the same
device, so the "Store Owner" panel won't see orders customers place on
their own phones.

To receive real orders reliably after deploying:

1. Sign up for a free account at https://formspree.io (2 minutes, no code).
2. Create a form and copy your endpoint URL (looks like
   `https://formspree.io/f/xxxxxxx`).
3. Open `src/App.jsx`, find the line:
   ```js
   const ORDER_NOTIFY_ENDPOINT = "";
   ```
   and paste your endpoint URL between the quotes.
4. Redeploy (push the change to GitHub — Vercel redeploys automatically).

Every order placed on the live site will then also be emailed to you,
regardless of which device the customer used.

## Admin panel passcode

The "Store Owner" link in the footer is protected by a passcode set in
`src/App.jsx` (search for `adminPasscode !==`). This is a basic
deterrent, not real security — anyone who views the site's source code
could find it. Treat it as a placeholder until a proper login system is
added.
