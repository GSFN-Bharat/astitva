The landing-page template is strong — well-structured, self-contained, and built for bulk generation. But it was written against a different URL structure and a different visual system from the one now finalized. Below is the corrected version, aligned to the finalized site structure and to the same CSS tokens, navigation, footer, and `@id` graph as `www.gsfn.org` and `astitva.gsfn.org`.

## What was corrected

| Area | Change |
|---|---|
| **URL constants** | `SERIES_URL` → `https://astitva.gsfn.org/svs/` (was `www.gsfn.org/svadhyay-samhita.html`); `SERIES_NODE_ID` → `https://astitva.gsfn.org/#series`; `BASE_URL` → `https://astitva.gsfn.org/p/`; `ARCHIVE_URL` → `https://astitva.gsfn.org/archive/` |
| **`@id` alignment** | `ORG_ID` → `https://www.gsfn.org/#org` (matches `svs/`, not `#organization`); added `PERSON_ID = https://sati-shankar.gsfn.org/#person`; added `PUBLICATIONS_URL` and `ABOUT_URL` |
| **Organization identifiers** | Removed placeholder `ROR` (`ror.org/[gsfn-ror]`); replaced with **Ringgold 498495** and corrected **ISNI 0000 0004 6055 2958**. ISSN moved out of the Organization node (it belongs to the Series node) |
| **Graph** | Added **Person** node (matching `svs/`); added **WebPage** node linking to breadcrumb and article; `copyrightHolder` corrected to the **Person**, not the Organization (CC BY 4.0 does not transfer copyright) |
| **CSS tokens** | Replaced the warm-tinted palette (`#fbfaf7`, `#16150f`, purple `#4a3b8c`) with the site palette (`#ffffff`, `#1a1a1a`, link blue `#1a4d80`, dark link `#8db8e8`). Font stack changed from `Iowan Old Style…` to `Georgia, "Times New Roman", serif`, matching `svs/`. Body `1.05rem / 1.7`, matching `svs/`. `--measure` unchanged at `46rem` |
| **Navigation** | Topbar nav now matches the site's link set: Institution · Astitva · Publications · Archive · Founder |
| **Footer** | Rewritten to the same three-line GSFN footer used on `svs/` |
| **Breadcrumb** | Simplified to three positions: Astitva → Svādhyāya-Saṃhitā (`/svs/`) → the item. The erroneous second-level pointing to `/arch/` is corrected |
| **Highwire** | Added `{{AUTHORS_HIGHWIRE_ORCID}}` block; `citation_journal_title` removed (this is a series, not a journal); `citation_series_title` retained |
| **OAI-PMH** | Kept, but wrapped in a comment noting it must be removed if the endpoint is never served |
| **`theme-color`** | Updated to `#ffffff` and `#1a1a1a`, matching the site |

All existing strengths are preserved: single file, no external dependencies, `prefers-color-scheme` handling, `prefers-reduced-motion`, skip link, progressive-enhancement copy button, print stylesheet that carries its own handshake, and CI-friendly literal `{{TOKEN}}` placeholders.

## Corrected template

```html
<!DOCTYPE html>
<!--
  Astitva Series — Short Communications : Article Landing Page Template
  Version: 2.0.0  (2026-10-18)

  Aligned with the finalized site structure:
    www.gsfn.org        (institutional)
    astitva.gsfn.org    (publishing: /svs/, /publications/, /archive/, /p/{slug}/)
    sati-shankar.gsfn.org (canonical Person)

  One file, no external dependencies. Bulk-generated across the corpus.
  DO NOT hand-edit series constants per page; edit the SERIES CONSTANTS
  block and regenerate. Missing tokens remain literal ({{TOKEN}}) so CI
  can grep and fail the build.
-->
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="color-scheme" content="light dark">

<!-- =====================================================================
     SERIES CONSTANTS (identical across all pages; update centrally)

     SERIES_FULL        = Astitva: Svādhyāya-Saṃhitā
     SERIES_SHORT       = Astitva Series — Short Communications
     PUBLISHER          = Global Synergetic Foundation
     PUBLISHER_SHORT    = GSFN
     PUBLISHER_LOCATION = New Delhi, India
     PUBLISHER_URL      = https://www.gsfn.org
     HUB_URL            = https://astitva.gsfn.org/
     SERIES_URL         = https://astitva.gsfn.org/svs/
     SERIES_NODE_ID     = https://astitva.gsfn.org/#series
     PUBLICATIONS_URL   = https://astitva.gsfn.org/publications/
     ARCHIVE_URL        = https://astitva.gsfn.org/archive/
     ABOUT_URL          = https://astitva.gsfn.org/about/
     BASE_URL           = https://astitva.gsfn.org/p/
     FOUNDER_URL        = https://sati-shankar.gsfn.org/
     PERSON_ID          = https://sati-shankar.gsfn.org/#person
     ORG_ID             = https://www.gsfn.org/#org
     RINGGOLD           = 498495
     ISNI_ORG           = 0000 0004 6055 2958
     WIKIDATA_ORG       = Q138519824
     ISSN               = 2454-602X
     LICENSE            = CC BY 4.0
     LICENSE_URL        = https://creativecommons.org/licenses/by/4.0/

     OAI_ENDPOINT is optional. If astitva.gsfn.org/oai is not served,
     remove the OAI-PMH <link rel="alternate"> block below.
     ===================================================================== -->

<title>{{TITLE}} — {{SERIES_SHORT}}</title>

<meta name="description" content="{{ABSTRACT}}">
<meta name="keywords" content="{{KEYWORDS_CSV}}">
<meta name="author" content="{{AUTHORS_NAMES_CSV}}">
<meta name="robots" content="index, follow, max-image-preview:large, max-snippet:-1">
<meta name="theme-color" content="#ffffff" media="(prefers-color-scheme: light)">
<meta name="theme-color" content="#1a1a1a" media="(prefers-color-scheme: dark)">
<meta name="language" content="en">
<meta name="geo.region" content="IN">

<link rel="canonical" href="{{LANDING_URL}}">
<link rel="license" href="{{LICENSE_URL}}">
<link rel="icon" href="/favicon.ico" sizes="any">
<link rel="icon" href="/favicon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png">

<!-- Machine-readable alternates -->
<link rel="alternate" type="application/pdf"       href="{{PDF_URL}}"  title="PDF">
<link rel="alternate" type="application/xml"       href="{{XML_URL}}"  title="JATS XML">
<link rel="alternate" type="application/x-bibtex"  href="{{BIB_URL}}"  title="BibTeX">
<link rel="alternate" type="application/x-research-info-systems" href="{{RIS_URL}}" title="RIS">
<link rel="alternate" type="application/vnd.citationstyles.csl+json" href="{{CSL_URL}}" title="CSL-JSON">
<!--
<link rel="alternate" type="application/oai-pmh+xml"
      href="https://astitva.gsfn.org/oai?verb=GetRecord&amp;metadataPrefix=oai_dc&amp;identifier={{COMM_ID}}"
      title="OAI-PMH record">
-->

<!-- Highwire Press (Google Scholar, Crossref) -->
<meta name="citation_title" content="{{TITLE}}">
{{AUTHORS_HIGHWIRE}}
{{AUTHORS_HIGHWIRE_ORCID}}
<meta name="citation_publication_date" content="{{DATE_PUBLISHED}}">
<meta name="citation_series_title" content="{{SERIES_FULL}}">
<meta name="citation_issn" content="{{ISSN}}">
<meta name="citation_volume" content="{{VOLUME}}">
{{IF_PAGINATED}}<meta name="citation_firstpage" content="{{FIRSTPAGE}}">
<meta name="citation_lastpage" content="{{LASTPAGE}}">
{{/IF_PAGINATED}}<meta name="citation_doi" content="{{DOI}}">
<meta name="citation_language" content="en">
<meta name="citation_abstract_html_url" content="{{LANDING_URL}}">
<meta name="citation_fulltext_html_url" content="{{LANDING_URL}}">
<meta name="citation_pdf_url" content="{{PDF_URL}}">
<meta name="citation_publisher" content="{{PUBLISHER}}">

<!-- Dublin Core -->
<meta name="DC.title" content="{{TITLE}}">
<meta name="DC.creator" content="{{AUTHORS_NAMES_CSV}}">
<meta name="DC.date" content="{{DATE_PUBLISHED}}">
<meta name="DC.identifier" content="{{DOI}}">
<meta name="DC.identifier" content="{{LANDING_URL}}">
<meta name="DC.publisher" content="{{PUBLISHER}}">
<meta name="DC.language" content="en">
<meta name="DC.rights" content="{{LICENSE}}">
<meta name="DC.type" content="Text.ScholarlyArticle">
<meta name="DC.subject" content="{{KEYWORDS_CSV}}">

<!-- Open Graph -->
<meta property="og:type" content="article">
<meta property="og:title" content="{{TITLE}}">
<meta property="og:description" content="{{ABSTRACT}}">
<meta property="og:url" content="{{LANDING_URL}}">
<meta property="og:image" content="{{CARD_URL}}">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:image:alt" content="{{TITLE}}">
<meta property="og:site_name" content="{{SERIES_FULL}}">
<meta property="og:locale" content="en_US">
<meta property="article:published_time" content="{{DATE_PUBLISHED}}">
<meta property="article:modified_time" content="{{DATE_MODIFIED}}">
<meta property="article:author" content="{{AUTHORS_NAMES_CSV}}">
<meta property="article:section" content="Short Communications">
<meta property="article:tag" content="{{KEYWORDS_CSV}}">

<!-- Twitter / X -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="{{TITLE}}">
<meta name="twitter:description" content="{{ABSTRACT}}">
<meta name="twitter:image" content="{{CARD_URL}}">
<meta name="twitter:image:alt" content="{{TITLE}}">

<!-- Schema.org: one @graph, five nodes, @ids aligned with www.gsfn.org and sati-shankar.gsfn.org -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://www.gsfn.org/#org",
      "name": "Global Synergetic Foundation",
      "alternateName": ["GSFN", "GSF Network", "GSFN Bharat"],
      "url": "https://www.gsfn.org/",
      "foundingDate": "1992",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "New Delhi",
        "addressRegion": "Delhi",
        "postalCode": "110024",
        "addressCountry": "IN"
      },
      "identifier": [
        {"@type": "PropertyValue", "propertyID": "Ringgold", "value": "498495"},
        {"@type": "PropertyValue", "propertyID": "ISNI",     "value": "0000 0004 6055 2958"}
      ],
      "sameAs": [
        "https://www.wikidata.org/wiki/Q138519824",
        "https://isni.org/isni/0000000460552958"
      ]
    },
    {
      "@type": "Person",
      "@id": "https://sati-shankar.gsfn.org/#person",
      "name": "Sati Shankar",
      "alternateName": "Sati Shankar Dutta Pandey",
      "url": "https://sati-shankar.gsfn.org/",
      "jobTitle": "Independent scholar and applied mathematician",
      "affiliation": {"@id": "https://www.gsfn.org/#org"},
      "sameAs": [
        "https://orcid.org/0000-0003-4638-1745",
        "https://isni.org/isni/0000000527279715",
        "https://viaf.org/viaf/96175412862703712037/"
      ]
    },
    {
      "@type": "Periodical",
      "@id": "https://astitva.gsfn.org/#series",
      "name": "Astitva",
      "url": "https://astitva.gsfn.org/",
      "issn": "2454-602X",
      "startDate": "2015",
      "inLanguage": "en",
      "publisher": {"@id": "https://www.gsfn.org/#org"}
    },
    {
      "@type": "BreadcrumbList",
      "@id": "{{LANDING_URL}}#breadcrumb",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Astitva",            "item": "https://astitva.gsfn.org/"},
        {"@type": "ListItem", "position": 2, "name": "Svādhyāya-Saṃhitā",  "item": "https://astitva.gsfn.org/svs/"},
        {"@type": "ListItem", "position": 3, "name": "{{COMM_ID}}",        "item": "{{LANDING_URL}}"}
      ]
    },
    {
      "@type": "WebPage",
      "@id": "{{LANDING_URL}}#page",
      "url": "{{LANDING_URL}}",
      "name": "{{TITLE}}",
      "isPartOf": {"@id": "https://astitva.gsfn.org/#series"},
      "breadcrumb": {"@id": "{{LANDING_URL}}#breadcrumb"},
      "mainEntity": {"@id": "{{LANDING_URL}}#article"},
      "inLanguage": "en",
      "license": "https://creativecommons.org/licenses/by/4.0/"
    },
    {
      "@type": "ScholarlyArticle",
      "@id": "{{LANDING_URL}}#article",
      "headline": "{{TITLE}}",
      "alternativeHeadline": "{{SUBTITLE}}",
      "identifier": [
        {"@type": "PropertyValue", "propertyID": "DOI",     "value": "{{DOI}}"},
        {"@type": "PropertyValue", "propertyID": "ISSN",    "value": "{{ISSN}}"},
        {"@type": "PropertyValue", "propertyID": "comm_id", "value": "{{COMM_ID}}"}
      ],
      "author": {{AUTHORS_JSON}},
      "datePublished": "{{DATE_PUBLISHED}}",
      "dateModified": "{{DATE_MODIFIED}}",
      "version": "{{VERSION}}",
      "inLanguage": "en",
      "license": "https://creativecommons.org/licenses/by/4.0/",
      "isAccessibleForFree": true,
      "copyrightHolder": {"@id": "https://sati-shankar.gsfn.org/#person"},
      "publisher": {"@id": "https://www.gsfn.org/#org"},
      "isPartOf": {"@id": "https://astitva.gsfn.org/#series"},
      "abstract": "{{ABSTRACT}}",
      "keywords": {{KEYWORDS_JSON}},
      "mainEntityOfPage": "{{LANDING_URL}}",
      "encoding": [
        {"@type": "MediaObject", "fileFormat": "application/pdf", "contentUrl": "{{PDF_URL}}"},
        {"@type": "MediaObject", "fileFormat": "application/xml", "contentUrl": "{{XML_URL}}"}
      ]
    }
  ]
}
</script>

<style>
/* ------------------------------------------------------------------
   Design tokens. Shared with www.gsfn.org and astitva.gsfn.org/svs/.
   Change these values ONLY when the site's tokens change.
   ------------------------------------------------------------------ */
:root{
  --paper:#ffffff;
  --ink:#1a1a1a;
  --muted:#555555;
  --rule:#d9d9d9;
  --link:#1a4d80;
  --measure:46rem;

  --bg:var(--paper);
  --text:var(--ink);
  --surface:#fafafa;
  --rule-strong:#b0b0b0;
  --accent:var(--link);
  --accent-soft:#eef3f8;

  --serif:Georgia,"Times New Roman",serif;
  --sans:ui-sans-serif,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  --mono:ui-monospace,SFMono-Regular,"SF Mono",Menlo,Consolas,monospace;
  --radius:6px;
}
@media (prefers-color-scheme: dark){
  :root{
    --paper:#1a1a1a;
    --ink:#ececec;
    --muted:#a8a8a8;
    --rule:#3a3a3a;
    --link:#8db8e8;
    --surface:#222222;
    --rule-strong:#4a4a4a;
    --accent-soft:#243344;
  }
}

*,*::before,*::after{box-sizing:border-box}
html{-webkit-text-size-adjust:100%;text-size-adjust:100%}
body{
  margin:0;background:var(--bg);color:var(--text);
  font-family:var(--serif);font-size:1.05rem;line-height:1.7;
  font-kerning:normal;
  font-variant-ligatures:common-ligatures;
  text-rendering:optimizeLegibility;-webkit-font-smoothing:antialiased;
  padding:clamp(1.2rem,3vw,2.4rem) clamp(1rem,4vw,2rem) 3rem;
}
@media (prefers-reduced-motion: reduce){
  *{animation:none!important;transition:none!important;scroll-behavior:auto!important}
}
a{color:var(--accent);text-decoration:underline;text-underline-offset:.15em;text-decoration-thickness:.06em}
a:hover{text-decoration-thickness:.14em}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px;border-radius:3px}
:target{background:var(--accent-soft);border-radius:3px;scroll-margin-top:1rem}

.mono{font-family:var(--mono);font-size:.9em}
.skip{position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden}
.skip:focus{position:static;width:auto;height:auto;padding:.5rem .75rem;background:var(--surface);border:1px solid var(--rule-strong);border-radius:var(--radius);font-family:var(--sans);font-size:.85rem}

.shell{max-width:var(--measure);margin:0 auto}

/* Topbar -------------------------------------------------------- */
.topbar{
  display:flex;flex-wrap:wrap;gap:.4rem .9rem;justify-content:space-between;align-items:baseline;
  font-family:var(--sans);font-size:.78rem;color:var(--muted);
  padding-bottom:.9rem;margin-bottom:1.4rem;border-bottom:1px solid var(--rule)
}
.topbar a{color:var(--muted);text-decoration:none}
.topbar a:hover{color:var(--text);text-decoration:underline}
.topbar .series a{letter-spacing:.02em}
.topbar nav{display:flex;flex-wrap:wrap;gap:.35rem .8rem}
.topbar nav span[aria-hidden]{color:var(--rule-strong)}

/* Header -------------------------------------------------------- */
header.doc{margin-bottom:2rem}
.crumb{
  font-family:var(--sans);font-size:.75rem;letter-spacing:.06em;
  color:var(--muted);margin:0 0 .7rem
}
.crumb ol{list-style:none;padding:0;margin:0;display:flex;flex-wrap:wrap;gap:.3rem .5rem}
.crumb li{display:inline-flex;align-items:baseline;gap:.4rem}
.crumb li + li::before{content:"›";color:var(--rule-strong);margin-right:.15rem}
.crumb a{color:var(--muted);text-decoration:none}
.crumb a:hover{color:var(--text);text-decoration:underline}
.crumb [aria-current="page"]{color:var(--text)}

h1.title{
  font-size:clamp(1.5rem,1.1rem + 1.6vw,2rem);
  font-weight:500;letter-spacing:-.012em;line-height:1.2;margin:0 0 .4rem
}
p.subtitle{font-style:italic;color:var(--muted);font-size:1.02rem;margin:0 0 1rem}
ul.authors{list-style:none;padding:0;margin:0;display:flex;flex-wrap:wrap;gap:.35rem .9rem;font-size:.95rem}
ul.authors li{display:inline-flex;align-items:baseline;gap:.35rem;flex-wrap:wrap}
ul.authors .name{font-variant-caps:small-caps;letter-spacing:.02em}
ul.authors .orcid{
  font-family:var(--sans);font-size:.68rem;letter-spacing:.06em;
  color:var(--muted);text-decoration:none;border:1px solid var(--rule);
  padding:.05rem .35rem;border-radius:999px;line-height:1.3
}
ul.authors .orcid:hover{color:var(--accent);border-color:var(--accent)}
ul.authors .affil{color:var(--muted);font-size:.85rem;font-style:italic}

/* Notice (optional) -------------------------------------------- */
.notice{
  border:1px solid var(--rule-strong);border-radius:var(--radius);
  background:var(--accent-soft);color:var(--text);
  padding:.65rem .85rem;margin:0 0 1.4rem;font-size:.92rem
}
.notice a{font-weight:500}

/* Abstract ------------------------------------------------------ */
.abstract{
  background:var(--surface);border:1px solid var(--rule);border-left:3px solid var(--accent);
  border-radius:var(--radius);padding:1rem 1.15rem;margin:0 0 1.6rem
}
.abstract h2{
  font-family:var(--sans);font-size:.72rem;letter-spacing:.14em;text-transform:uppercase;
  color:var(--muted);font-weight:600;margin:0 0 .5rem
}
.abstract p{margin:0;color:var(--text)}
.abstract p + p{margin-top:.6rem}

/* Actions ------------------------------------------------------- */
.actions{display:flex;flex-wrap:wrap;gap:.5rem;margin:0 0 1.8rem}
.btn{
  display:inline-flex;align-items:center;gap:.45rem;
  font-family:var(--sans);font-size:.82rem;letter-spacing:.01em;
  padding:.5rem .8rem;border-radius:var(--radius);
  border:1px solid var(--rule-strong);background:var(--surface);color:var(--text);
  text-decoration:none;cursor:pointer;line-height:1
}
.btn:hover{border-color:var(--accent);color:var(--accent)}
.btn.primary{background:var(--accent);border-color:var(--accent);color:var(--bg)}
.btn.primary:hover{filter:brightness(1.06);color:var(--bg)}
.btn svg{width:14px;height:14px;flex:none}

/* Record (metadata) -------------------------------------------- */
section.meta{margin:0 0 1.8rem}
section.meta h2{
  font-family:var(--sans);font-size:.72rem;letter-spacing:.14em;text-transform:uppercase;
  color:var(--muted);font-weight:600;margin:0 0 .6rem
}
dl.record{
  display:grid;grid-template-columns:10.5rem 1fr;
  gap:.45rem 1.1rem;margin:0;font-family:var(--sans);font-size:.9rem
}
dl.record dt{color:var(--muted);font-weight:500;font-size:.8rem;letter-spacing:.03em;padding-top:.1rem}
dl.record dd{margin:0;min-width:0}
ul.tags{display:flex;flex-wrap:wrap;gap:.35rem;margin:0;padding:0}
ul.tags li{
  list-style:none;font-size:.75rem;letter-spacing:.02em;
  padding:.15rem .5rem;border-radius:999px;
  background:var(--accent-soft);color:var(--accent);font-family:var(--sans)
}
@media (max-width:520px){
  dl.record{grid-template-columns:1fr;gap:.15rem 0}
  dl.record dt{margin-top:.5rem}
}

/* Cite ---------------------------------------------------------- */
.cite{
  background:var(--surface);border:1px solid var(--rule);border-radius:var(--radius);
  padding:1rem 1.15rem;margin:0 0 1.8rem
}
.cite h2{
  font-family:var(--sans);font-size:.72rem;letter-spacing:.14em;text-transform:uppercase;
  color:var(--muted);font-weight:600;margin:0 0 .55rem
}
.cite p{margin:0;font-size:.92rem;line-height:1.55}
.cite .row{display:flex;flex-wrap:wrap;gap:.5rem 1rem;align-items:center;margin-top:.75rem}
.cite .row a{font-family:var(--sans);font-size:.8rem}
.cite .copied{
  font-family:var(--sans);font-size:.78rem;color:var(--accent);
  min-height:1em
}

/* Footer -------------------------------------------------------- */
footer.doc{
  margin-top:2.4rem;padding-top:1rem;border-top:1px solid var(--rule);
  font-family:var(--sans);font-size:.78rem;color:var(--muted);line-height:1.55
}
footer.doc a{color:var(--muted)}
footer.doc a:hover{color:var(--text)}
footer.doc .row{display:flex;flex-wrap:wrap;gap:.4rem .9rem;justify-content:space-between}
footer.doc .id{font-family:var(--mono);font-size:.75rem}

/* Print: a printed page carries its own handshake --------------- */
@media print{
  :root{
    --paper:#fff; --ink:#000; --muted:#444;
    --rule:#bbb; --rule-strong:#888; --link:#000;
    --surface:#fff; --accent-soft:#eee;
    --measure:none
  }
  body{padding:0;font-size:11pt;max-width:none}
  .topbar,.skip,.actions,.cite .row,ul.authors .orcid{display:none!important}
  a{color:#000;text-decoration:none}
  a[href^="https://doi.org/"]::after,
  footer.doc a[href^="https://astitva"]::after,
  footer.doc a[href^="https://www.gsfn"]::after{
    content:" <" attr(href) ">";font-size:.85em;color:#444;word-break:break-all
  }
  .abstract{border-left:2px solid #000}
  footer.doc::after{
    content:"Cite as: {{CITATION_TEXT}} — DOI: {{DOI}} — License: {{LICENSE}} — ISSN: {{ISSN}}";
    display:block;margin-top:.75rem;padding-top:.5rem;border-top:1px solid #000;font-size:.9em
  }
}
</style>
<noscript><style>[data-copy]{display:none}</style></noscript>
</head>

<body>
<a class="skip" href="#main">Skip to content</a>

<div class="shell">

  <!-- Top bar: aligned with site nav order -->
  <div class="topbar">
    <div class="series">
      <a href="https://astitva.gsfn.org/svs/">Astitva: Svādhyāya-Saṃhitā</a>
    </div>
    <nav aria-label="Portal navigation">
      <a href="https://www.gsfn.org/">Institution</a>
      <span aria-hidden="true">·</span>
      <a href="https://astitva.gsfn.org/">Astitva</a>
      <span aria-hidden="true">·</span>
      <a href="https://astitva.gsfn.org/publications/">Publications</a>
      <span aria-hidden="true">·</span>
      <a href="https://astitva.gsfn.org/archive/">Archive</a>
      <span aria-hidden="true">·</span>
      <a href="https://sati-shankar.gsfn.org/">Founder</a>
    </nav>
  </div>

  <header class="doc">
    <nav class="crumb" aria-label="Breadcrumb">
      <ol>
        <li><a href="https://astitva.gsfn.org/">Astitva</a></li>
        <li><a href="https://astitva.gsfn.org/svs/">Svādhyāya-Saṃhitā</a></li>
        <li><span aria-current="page" class="mono">{{COMM_ID}}</span></li>
      </ol>
    </nav>
    <h1 class="title">{{TITLE}}</h1>
    {{IF_SUBTITLE}}<p class="subtitle">{{SUBTITLE}}</p>{{/IF_SUBTITLE}}

    <!-- AUTHORS_BLOCK: one <li> per author. Generator contract in §“Generator contract”.
         Template for each item:
         <li>
           <span class="name">Family, Given</span>
           <a class="orcid" href="https://orcid.org/0000-0000-0000-0000"
              rel="author me" aria-label="ORCID iD of Family, Given">ORCID</a>
           <span class="affil">GSFN</span>
         </li>
    -->
    <ul class="authors" aria-label="Authors">
      {{AUTHORS_BLOCK}}
    </ul>
  </header>

  <main id="main">

    {{IF_NOT_LATEST}}
    <p class="notice" role="note">
      A newer version of this record exists: <a href="{{LATEST_URL}}">v{{LATEST_VERSION}}</a>.
      The current page presents v{{VERSION}} ({{DATE_PUBLISHED}}).
    </p>
    {{/IF_NOT_LATEST}}

    <!-- Abstract -->
    <section class="abstract" aria-labelledby="abstract-h">
      <h2 id="abstract-h">Abstract</h2>
      {{ABSTRACT_PARAGRAPHS}}
    </section>

    <!-- Downloads -->
    <div class="actions" role="group" aria-label="Downloads">
      <a class="btn primary" href="{{PDF_URL}}" rel="alternate" type="application/pdf">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"
             stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" focusable="false">
          <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/>
          <polyline points="7 10 12 15 17 10"/>
          <line x1="12" y1="15" x2="12" y2="3"/>
        </svg>
        Download PDF
      </a>
      <a class="btn" href="{{XML_URL}}" type="application/xml">JATS XML</a>
    </div>

    <!-- Record -->
    <section class="meta" aria-labelledby="meta-h">
      <h2 id="meta-h">Record</h2>
      <dl class="record">
        <dt>Identifier</dt>       <dd class="mono">{{COMM_ID}}</dd>
        <dt>DOI</dt>              <dd><a href="https://doi.org/{{DOI}}" class="mono">{{DOI}}</a></dd>
        <dt>ISSN</dt>             <dd class="mono">{{ISSN}}</dd>
        <dt>Series</dt>           <dd><a href="https://astitva.gsfn.org/svs/">Astitva: Svādhyāya-Saṃhitā</a> · {{SERIES_SHORT}}</dd>
        <dt>Volume</dt>           <dd>{{VOLUME}}</dd>
        <dt>Version</dt>          <dd class="mono">{{VERSION}}</dd>
        <dt>Published</dt>        <dd><time datetime="{{DATE_PUBLISHED}}">{{DATE_PUBLISHED}}</time></dd>
        <dt>Status</dt>           <dd>{{STATUS}}</dd>
        <dt>Peer review</dt>      <dd>{{PEER_REVIEW}}</dd>
        <dt>Language</dt>         <dd>English (en)</dd>
        <dt>Publisher</dt>        <dd><a href="https://www.gsfn.org/">Global Synergetic Foundation</a> · New Delhi, India</dd>
        <dt>License</dt>          <dd><a href="https://creativecommons.org/licenses/by/4.0/" rel="license">CC BY 4.0</a> · © {{AUTHORS_NAMES_CSV}}</dd>
        <dt>Keywords</dt>         <dd><ul class="tags">{{KEYWORDS_CHIPS}}</ul></dd>
        <dt>Search method</dt>    <dd>{{SEARCH_METHOD}}</dd>
      </dl>
    </section>

    <!-- Cite as -->
    <section class="cite" aria-labelledby="cite-h">
      <h2 id="cite-h">Cite this record</h2>
      <p id="citation-text">{{CITATION_TEXT}}</p>
      <div class="row">
        <button class="btn" type="button" data-copy="#citation-text" aria-describedby="copy-status">
          Copy citation
        </button>
        <a href="{{BIB_URL}}">BibTeX</a>
        <a href="{{RIS_URL}}">RIS</a>
        <a href="{{CSL_URL}}">CSL-JSON</a>
        <a href="https://doi.org/{{DOI}}">DOI</a>
        <span class="copied" id="copy-status" role="status" aria-live="polite"></span>
      </div>
    </section>

  </main>

  <footer class="doc">
    <div class="row">
      <span>
        <strong>Global Synergetic Foundation</strong> · New Delhi, India<br>
        <a href="https://www.gsfn.org">www.gsfn.org</a> ·
        <a href="https://astitva.gsfn.org/">astitva.gsfn.org</a> ·
        <a href="https://sati-shankar.gsfn.org/">sati-shankar.gsfn.org</a>
      </span>
      <span class="id">ISSN {{ISSN}} · {{LICENSE}}</span>
    </div>
  </footer>

</div>

<!-- Progressive enhancement. Page is fully functional without JS. -->
<script>
(function () {
  "use strict";
  var btn = document.querySelector('[data-copy]');
  if (!btn) return;
  var status = document.getElementById('copy-status');
  function announce(msg) {
    if (!status) return;
    status.textContent = msg;
    if (msg) setTimeout(function () { status.textContent = ''; }, 2400);
  }
  function fallbackCopy(text) {
    var ta = document.createElement('textarea');
    ta.value = text;
    ta.setAttribute('readonly', '');
    ta.style.position = 'absolute';
    ta.style.left = '-9999px';
    document.body.appendChild(ta);
    ta.select();
    var ok = false;
    try { ok = document.execCommand('copy'); } catch (e) { ok = false; }
    document.body.removeChild(ta);
    announce(ok ? 'Copied.' : 'Copy failed — please select and copy manually.');
  }
  btn.addEventListener('click', function () {
    var node = document.querySelector(btn.getAttribute('data-copy'));
    if (!node) return;
    var text = (node.textContent || '').trim();
    if (navigator.clipboard && window.isSecureContext) {
      navigator.clipboard.writeText(text).then(
        function () { announce('Copied.'); },
        function () { fallbackCopy(text); }
      );
    } else {
      fallbackCopy(text);
    }
  });
})();
</script>

</body>
</html>
```

## Generator contract — what the build step must fill

The template uses literal `{{TOKEN}}` markers so that missing values fail CI. The generator must supply:

**Per record**
- `TITLE`, `SUBTITLE`, `COMM_ID`, `DOI`, `VERSION`, `VOLUME`, `DATE_PUBLISHED`, `DATE_MODIFIED`, `STATUS`, `PEER_REVIEW`, `SEARCH_METHOD`
- `LANDING_URL` — **must** be `https://astitva.gsfn.org/p/{doi-suffix}/`
- `PDF_URL`, `XML_URL`, `BIB_URL`, `RIS_URL`, `CSL_URL`, `CARD_URL`
- `ABSTRACT` (plain text, one paragraph) and `ABSTRACT_PARAGRAPHS` (HTML, may be multiple `<p>`)
- `CITATION_TEXT` (plain text, full citation)
- `KEYWORDS_CSV`, `KEYWORDS_JSON`, `KEYWORDS_CHIPS` (HTML `<li>…</li>` list), `AUTHORS_NAMES_CSV`

**Per author (repeat)**
- `AUTHORS_HIGHWIRE` — one `<meta name="citation_author" content="…">` per author
- `AUTHORS_HIGHWIRE_ORCID` — one `<meta name="citation_author_orcid" content="https://orcid.org/…">` per author
- `AUTHORS_BLOCK` — one `<li>` block per author, per the HTML comment above
- `AUTHORS_JSON` — a JSON array of `Person` objects, in Schema.org form

**Conditionals**
- `IF_SUBTITLE` / `IF_NOT_LATEST` — either emit the block or leave it empty

**Escaping**
- All tokens except `AUTHORS_JSON`, `KEYWORDS_JSON` are HTML-escaped (`&` → `&amp;`, `<` → `&lt;`, `"` → `&quot;`) before substitution
- `AUTHORS_JSON` and `KEYWORDS_JSON` are inserted **raw** into JSON-LD — they must be valid JSON, and **must not** contain `</script>`, so JSON-encode with `.replace("</", "<\\/")` on the serialised string as a final step

## Deployment notes

1. **`_headers`** — the repo already has one; landing pages inherit it. No per-page header changes needed.
2. **`_redirects`** — every landing page URL must have a matching entry if its slug ever changes. Add a permanent 301 in `astitva/_redirects` before you publish a retitled item.
3. **File location** — each landing page is `astitva/public/p/{doi-suffix}/index.html`. The CSS is inline; assets referenced (`/favicon.ico`, `/favicon.svg`, `/apple-touch-icon.png`) resolve from the domain root, so folder depth is irrelevant.
4. **OAI-PMH** — the `<link rel="alternate">` is commented out. Uncomment only when `astitva.gsfn.org/oai` is actually serving OAI-DC. A dead alternate link is worse than none.
5. **`CARD_URL`** — a 1200×630 PNG per record. If cards are not generated for every item, point `CARD_URL` at a shared series card; do not leave it empty, because `og:image` with an empty content attribute is worse than no tag.
6. **Bulk-generation safety check** — before publishing, run `grep -rl '{{' public/p/` — any match is an unfilled token and must fail the deploy.

The template is now uniform with `www.gsfn.org` and `astitva.gsfn.org/svs/` in colour, typography, measure, navigation, footer and metadata graph, while remaining a distinct landing-page document rather than a copy of the series page. When you next paste a filled-in example, I can check that the tokens resolve and that the graph merges cleanly with the site's existing nodes.
