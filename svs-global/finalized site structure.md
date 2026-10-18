Your three decisions simplify the structure considerably. Here is the final version, corrected for what they imply.

## What the decisions change

1. **`sati-shankar.gsfn.org` stays canonical.** It already carries the Person `@id` bound to ORCID, ISNI and VIAF, so it must remain its own site. It needs its own repository and its own Cloudflare Pages project — not a folder inside `www.gsfn.org`. It is a single-page site and will stay one.
2. **`/select/` is removed.** There is no curated page on either site. Selected landing pages are linked inline, wherever they are needed: a short list on the founder profile, a short list on `www.gsfn.org/astitva/`, a short list on `astitva.gsfn.org/about/`. These are plain `<ul>` blocks of links, not pages.
3. **Cloudflare Pages + GitHub, three repositories.** Each repository is one Cloudflare Pages project with one custom domain. That is the only arrangement Cloudflare supports cleanly for separate subdomains, and it is also the simplest to manage from anywhere: edit on GitHub (works from a phone), commit, Cloudflare deploys automatically.

## Final structure

### Repository 1 — `gsfn-www` → `https://www.gsfn.org`

Public-facing institutional site. Small, stable, rarely edited.

```
/
├── index.html                 Home
├── about/index.html           About the organisation
├── astitva/index.html         Short public introduction to the series;
│                              one link to astitva.gsfn.org; 3–5 selected
│                              landing-page links inline
├── founder/index.html         Institutional page on the founder;
│                              links to sati-shankar.gsfn.org;
│                              5–10 selected landing-page links inline
├── contact/index.html         Contact
├── legal/
│   ├── terms/index.html
│   ├── privacy/index.html
│   └── licensing/index.html   CC BY 4.0, ISSN / ISBN / DOI policy
├── 404.html
├── _headers                   Security headers (Cloudflare Pages)
├── _redirects                 Path permanence (Cloudflare Pages)
├── robots.txt
├── sitemap.xml
├── favicon.ico
└── assets/
    ├── css/site.css
    └── logo-astitva.png
```

Nav: Home · About · Astitva Series · Founder · Contact, with one styled outbound link “Visit the archive ↗” to `astitva.gsfn.org`.

### Repository 2 — `astitva` → `https://astitva.gsfn.org`

Publishing site. Holds the archive, the series description, the global list, and every landing page. This is the repository that will grow to hundreds of files.

```
/
├── public/                    ← Cloudflare Pages output directory
│   ├── index.html             Home
│   ├── about/index.html       About the series; editorial and identifier
│   │                          policy; how to cite; selected links inline
│   ├── svs/index.html         Astitva: Svādhyāya-Saṁhitā (the page you supplied)
│   ├── publications/index.html  ← GENERATED from data/publications.json
│   ├── archive/index.html     Working notes, drafts, undated material
│   ├── p/                     Landing pages — one folder per publication
│   │   ├── astitva-2019-003/index.html   ← hand-authored
│   │   ├── astitva-2021-007/index.html   ← hand-authored
│   │   ├── note-2021-014/index.html      ← hand-authored
│   │   └── …
│   ├── feed.xml               ← GENERATED (Atom)
│   ├── sitemap.xml            ← GENERATED
│   ├── 404.html
│   ├── _headers
│   ├── _redirects             e.g. /arch/ → /archive/  301
│   ├── robots.txt
│   ├── favicon.ico
│   └── assets/
│       ├── css/astitva.css
│       └── logo-astitva.png
├── data/
│   └── publications.json      Single source of truth for the global list
└── build.py                   Small Python script; Cloudflare runs it on push
```

Nav: Home · About · Svādhyāya-Saṁhitā · Publications · Archive, with one “Institution ↗” link back to `www.gsfn.org`.

**The one workflow that makes this manageable.** Hand-editing a global list of hundreds of entries across three places (visible text, microdata, JSON-LD) will drift. But you also do not want to run a build on your own laptop. So: you type each item once in `data/publications.json`; Cloudflare runs `build.py` on every push; the script writes `publications/index.html`, `feed.xml`, and `sitemap.xml`. You edit `publications.json` on GitHub from wherever you are — phone, tablet, borrowed computer — commit, and the page regenerates and deploys in about a minute. Landing pages themselves remain hand-authored, because the body text is scholarly work and no script should write it.

**Landing-page URL rule.** Derive the path from the DOI suffix, never from the title, so a retitled work never needs a new URL and a registered DOI never breaks:

```
https://astitva.gsfn.org/p/{doi-suffix}/
https://astitva.gsfn.org/p/note-{year}-{seq}/     (items without a DOI yet)
```

Each landing page is a self-contained `index.html` referencing `/assets/…` by absolute path, so folder depth never matters. This is the slot for the landing-page HTML you will paste — I will align it to the same shared CSS and the same `@id` graph as the rest of the site.

### Repository 3 — `sati-shankar` → `https://sati-shankar.gsfn.org`

Founder profile. One page, stable, its own Cloudflare project.

```
/
├── index.html                 Profile: biography, research summary,
│                              ORCID · ISNI · VIAF, selected writings
│                              inline (5–10 landing-page links)
├── 404.html
├── _headers
├── _redirects
├── robots.txt
├── sitemap.xml
├── favicon.ico
└── assets/
    ├── css/profile.css
    └── logo-astitva.png
```

Nav: Home · Selected writings (an anchor on the same page) · Institution ↗ · Astitva ↗.

## Cloudflare Pages settings, project by project

| Project | Source repo | Build command | Output directory | Custom domain |
|---|---|---|---|---|
| `gsfn-www` | `gsfn-www` | *(none)* | `/` | `www.gsfn.org` |
| `astitva` | `astitva` | `python build.py` | `public` | `astitva.gsfn.org` |
| `sati-shankar` | `sati-shankar` | *(none)* | `/` | `sati-shankar.gsfn.org` |

Two static projects need no build. Only `astitva` runs a build, because only `astitva` has a list that grows. Python 3 is available in Cloudflare’s build environment; `build.py` needs no third-party libraries — the standard library is enough.

`_headers` in all three repos, identical content:

```
/*
  X-Content-Type-Options: nosniff
  X-Frame-Options: DENY
  Referrer-Policy: strict-origin-when-cross-origin
  Permissions-Policy: geolocation=(), microphone=(), camera=()
```

`_redirects` in `astitva` for legacy paths (`/arch/ → /archive/ 301`, and any old landing-page slugs as they arise). `_redirects` in `gsfn-www` reserved for future moves. Keep this file under version control from day one; retrofitting redirects after URLs have been cited is painful.

## Managing from wherever you are

- **Edits.** GitHub web and mobile web both work. Edit `publications.json` on the phone, commit, Cloudflare deploys. No local tools, no terminal.
- **New landing page.** Create `public/p/{slug}/index.html` on GitHub, paste the landing-page HTML, commit. Add the record to `publications.json` in the same commit or the next; the list regenerates.
- **Moving pages.** Edit `_redirects`, commit. Done.
- **Rollbacks.** Cloudflare keeps every deployment; any version can be made live in one click.
- **No dependencies.** No framework, no package manager, no local build. Nothing to reinstall when you change machines.

## Build order

1. Freeze the `@id` table (unchanged from the earlier discussion) and the `/p/{doi-suffix}/` URL rule. These are the only things that are hard to change later.
2. Create the three repos and three Cloudflare Pages projects; point custom domains; confirm HTTPS on each.
3. Build `gsfn-www` — five pages plus legal. Small and anchors the graph.
4. Move `svs/` into `astitva` unchanged; add `about/`, `archive/`, and the home page.
5. Create `data/publications.json` with the first ten entries; write `build.py`; confirm Cloudflare generates `publications/index.html`, `feed.xml`, `sitemap.xml` on push.
6. Paste in the landing-page HTML; align it to `astitva.css` and the graph.
7. Add `_redirects`, `_headers`, `robots.txt`, `404.html`, sitemaps to each repo.
8. Submit the three sitemaps to search consoles; confirm the `@id` references resolve across domains.

When you paste the landing-page HTML, I will align it to the same shared stylesheet and the same `@id` conventions as the rest, so the landing pages and the section pages are indistinguishable in typography, measure and metadata. Nothing else in the structure above depends on that step.
