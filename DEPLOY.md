# Deploying the waitlist site to Netlify

This folder (`website/`) is the whole site. One file, no build step, no separate service for email capture (uses Netlify's own free "Forms" feature).

## First-time deploy (drag and drop, ~2 minutes)

1. Go to [app.netlify.com](https://app.netlify.com) and log in to your existing account.
2. On the dashboard, find the box that says **"Want to deploy a new site without connecting to Git?"** and drag the whole `website` folder onto it (drag the folder itself, not just the file inside).
3. Netlify assigns a random URL like `earnest-torvalds-abc123.netlify.app`. The site is live immediately.
4. To use your own domain later: **Site configuration → Domain management → Add a domain**, and follow Netlify's prompts.

## After you have a real domain: fix the social-preview image

`index.html`'s `<head>` has `og:image`/`twitter:image` tags pointing at `assets/og-image.png` as a relative path — that works for the page itself, but social platforms (iMessage, Slack, Twitter/X, etc.) need an absolute URL to fetch the preview image. Once you have a real domain, ask me to update those two tags (and `og:url` if you want one) to the full `https://yourdomain.com/assets/og-image.png` form, otherwise link previews will show no image.

## Confirm the waitlist form is capturing emails

Netlify detects the `<form data-netlify="true">` in `index.html` automatically on deploy — no extra setup.

1. In the Netlify dashboard for this site, go to the **Forms** tab.
2. You should see a form named **"waitlist"** listed. If you don't see it yet, redeploy once (Netlify only registers forms after a real deploy of the HTML, not a preview).
3. Every signup shows up here as a row (email address + timestamp). You can export them as CSV, or connect Netlify's Slack/email notifications (**Forms → Form notifications**) so you get pinged for every new signup instead of checking manually.

## Updating the site later

Whenever you want to change copy or colors: ask me to edit `website/index.html`, then re-drag the `website` folder onto the same Netlify site's deploy page (or connect it to a GitHub repo later for automatic deploys — not necessary for a one-page site like this).

## Retiring the old Beehiiv page

Once this is live and you're happy with it, cancel/redirect the old Beehiiv waitlist page so there's only one place collecting signups. Beehiiv has an export option for any emails already collected there — worth pulling those out before you shut it down so nobody who already signed up gets lost.
