# jiyu-labs.com

Company website for JIYU Laboratories, Inc., built with [Jekyll](https://jekyllrb.com/) and hosted on GitHub Pages.

- **Content editors:** see [EDITING.md](EDITING.md) (Japanese guide for editing on github.com, no terminal needed).
- **Live site:** https://jiyu-labs.com

## How it works

The site is a single page. Each section is a Markdown file in `_sections/`, rendered in `order`.

```
_config.yml           Site-wide settings (company name, tagline, SEO, Google verification)
index.html            Loops over _sections (sorted by `order`) and renders each one
_sections/*.md        One file per section. Front matter: order, anchor, nav, label, title,
                      subtitle, background (white|gray), type, hidden
_services/*.md        One file per Services card (title, target, image, button_text, button_url)
_layouts/default.html Page shell: <head>, header nav (built from sections with `nav`), footer
_includes/
  section.html        Section wrapper; picks a renderer by `type`
  services.html       type: services → cards from _services/
  about.html          type: about    → mission + icon items (heart | smile | star)
  contact.html        type: contact  → Google Form button / optional embed
                      type: columns  → body split into columns at `<!-- column -->`
                      (default)      → body rendered as Markdown prose
assets/css/style.css  All styles; design tokens in :root
assets/images/        Images (service cards, OG image, favicon)
reference/            Screenshot of the original STUDIO site (not published)
```

Markdown uses kramdown GFM with `hard_wrap: true`, so single line breaks are kept. Bare URLs must be wrapped in `<...>` to become links.

## Local preview (optional)

Requires Ruby. GitHub Pages builds the site itself, so `Gemfile` is only used for local preview.

```sh
bundle config set --local path vendor/bundle
bundle install
bundle exec jekyll serve      # http://127.0.0.1:4000
```

## Hosting and domain

GitHub Pages deploys from the `main` branch (root folder) on every commit. The custom domain `jiyu-labs.com` is set in Settings → Pages (stored in the `CNAME` file; don't delete it), with HTTPS enforced. DNS is managed in Squarespace Domains and the domain is verified at the organization level.
