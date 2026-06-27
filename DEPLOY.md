# Deploying the Lev Trade Partners site (Cloudflare Pages)

Static site, no build step. The whole folder is the deployable site.

```
(this folder)
  index.html        Lev Trade Partners (the flagship, for levtradepartners.com)
  group.html        "Our group" page (energy live, media/equipment in development)
  assets/           photography, logo.svg, favicon.svg
  _headers          Cloudflare Pages security headers + asset caching
  robots.txt
  sitemap.xml
  netlify.toml      (only used if you ever deploy to Netlify, harmless on Cloudflare)
```

The folder on disk is named `lev-energies` from the first draft. That name is internal only and does not affect the live site.

## Step 1: Put it on GitHub (easiest path for Cloudflare)
- Create a new repo (private is fine), e.g. `lev-trade-partners`.
- Upload the contents of this folder to the repo root (so `index.html` is at the top level of the repo).
- If you prefer no GitHub: Cloudflare Pages also supports "Direct Upload", just drag this folder in the dashboard.

## Step 2: Create the Cloudflare Pages project
- Cloudflare dashboard -> Workers & Pages -> Create -> Pages.
- Connect the GitHub repo (or choose Direct Upload).
- Build settings: Framework preset = None. Build command = leave empty. Build output directory = `/` (the root).
- Deploy. It goes live on a `*.pages.dev` URL in under a minute.

## Step 3: Connect the domain
- Buy `levtradepartners.com` (about $10/yr). Since you are on Cloudflare, the cleanest path is to register or transfer the domain into Cloudflare Registrar, then DNS is automatic.
- In the Pages project: Custom domains -> Set up a domain -> `levtradepartners.com` (and `www`).
- HTTPS is automatic.

## Step 4: Turn on the contact form (Formspree, free)
Cloudflare Pages has no built-in form handler, so the form posts to Formspree.
1. Go to https://formspree.io, sign up, create a new form. Set the destination to your inbox.
2. Copy the form endpoint, it looks like `https://formspree.io/f/abcdwxyz`.
3. In `index.html`, find `action="https://formspree.io/f/YOUR_FORM_ID"` and replace `YOUR_FORM_ID` with your real ID (the part after `/f/`).
4. Redeploy. Submissions now arrive by email, pre-qualified with product, grade, port, volume, Incoterms, payment instrument, licence status, and buyer type.

Free Formspree allows 50 submissions/month. Alternatives that work the same way on Cloudflare: Web3Forms (instant access key, no account) or Getform. Until you set this up, prospects can still reach you via the email and WhatsApp links in the contact section.

## Before you send a single outreach email
- Replace the placeholder WhatsApp number (`+971 50 000 0000`, in two `wa.me/971500000000` links).
- Confirm the head office line ("Dubai") matches where the company is actually registered and banked.
- Replace or remove the placeholder stat numbers (4 / 15+ / 3).
- Set up the `hello@levtradepartners.com` inbox once the domain is live.
