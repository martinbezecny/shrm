# Support site for Simple Heart Rate Monitor

Four files, no build step, no dependencies, no scripts. Static HTML and one
stylesheet.

    index.html      Support page
    privacy.html    Privacy policy
    style.css       Shared stylesheet
    favicon.svg     Icon

## Before you publish

Placeholders. Search for each and replace it everywhere it appears.

    REPLACE_WITH_YOUR_SUPPORT_EMAIL     index.html, privacy.html
    REPLACE_WITH_DATE                   privacy.html
    REPLACE_WITH_HOST                   privacy.html  ("GitHub Pages",
                                        "Cloudflare Pages", etc.)

    grep -rn REPLACE_WITH .

The privacy policy is written to describe version 1.0.1 and says so in
three places. When you ship a version that changes anything it describes,
update the policy and the App Store privacy answers together.

Check the version string at the bottom of `index.html` when you ship an
update, and check the sensor lists occasionally as hardware comes and goes.

## Publishing on GitHub Pages

1. Create a new public repository, for example `shrm-support`.
2. Put these files at the top level of it, not in a subfolder.
3. Push.
4. Repository Settings, Pages. Under Source pick "Deploy from a branch",
   branch `main`, folder `/ (root)`. Save.
5. The URL appears within a minute or two:
   `https://YOURUSERNAME.github.io/shrm-support/`

Cloudflare Pages and Codeberg Pages work the same way if you would rather
not use GitHub.

## In App Store Connect

Both fields are mandatory, and a reviewer will open both.

    Support URL           https://YOURUSERNAME.github.io/shrm-support/
    Privacy Policy URL    https://YOURUSERNAME.github.io/shrm-support/privacy.html

## Custom domain

If you buy a domain, add it under Settings, Pages, Custom domain, and point
a CNAME record at `YOURUSERNAME.github.io`. GitHub issues the TLS
certificate. Doing this also gives you a real support mailbox and solves
the contact address you have to publish for the Digital Services Act.

## Local preview

    python -m http.server 8000

Then open `http://localhost:8000`.

## Notes on what is here

The page loads nothing from a third party: no webfonts, no CDN, no
analytics. That is deliberate. The privacy policy claims the product talks
to nobody, and a policy page that phones Google for a font undercuts its
own argument. It also keeps the site clear of the GDPR question that
embedded Google Fonts raises for EU visitors.

Light and dark are both handled through `prefers-color-scheme`, matching
the app's own System theme setting. Colours are the app's five training
zones, defined once as custom properties at the top of `style.css`.
