I reviewed the three GSFN pages and reconciled the template against their actual markup, CSS, and metadata conventions. Below is the corrected, finalized version. It now uses **the same typographic system, width, colours, and structural shell** as `www.gsfn.org`, `astitva.gsfn.org`, and `sati-shankar.gsfn.org`.

## What was corrected

| Area | Correction |
|---|---|
| **Fonts** | Replaced the earlier `Source Serif 4` / `Inter` stack with GSFN’s own serif stack: `"Iowan Old Style", "Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif` . |
| **Width** | Container changed from `46rem` to **`620px`**, matching the `.container` rule on all three GSFN pages . |
| **Body padding** | Set to `1.4rem 0.85rem 2.2rem`, exactly as on GSFN . |
| **Line height** | Set to `1.58`, matching GSFN . |
| **Colour tokens** | Aligned to GSFN’s `:root` variables: `--text:#1a1a1a`, `--muted:#555`, `--border:#e0e0e0`, `--soft:#f7f7f7`, `--link:#111`, `--bg:#fff` . |
| **Navigation** | Added GSFN’s three‑link `nav` (Institution · Astitva · Founder) so the page sits inside the existing site architecture . |
| **Header** | Adopted GSFN’s centred header with `h1` at `1.65rem / font-weight:400` and `.subhead` at `0.93rem / colour:var(--muted)` . |
| **Section headings** | `h2` now uses GSFN’s uppercase, letter‑spaced, bordered style (`0.9rem`, `font-weight:600`, `text-transform:uppercase`) . |
| **Links** | Underlined with `text-underline-offset:2px`, colour `var(--link)`, hover `#000` — matching GSFN . |
| **Footer** | Centred, `0.72rem`, muted, bordered top — exactly the GSFN footer treatment . |
| **Responsive rule** | Added GSFN’s `@media (max-width:520px)` adjustment for mobile padding and `h1` size . |
| **Metadata** | Added `citation_author_orcid`, `citation_author_institution`, and `dc.rights` to align with GSFN’s citation metadata . |
| **JSON‑LD** | Switched from a single `CollectionPage` to a **`@graph`** containing `CollectionPage`, `ResearchOrganization`, `PublicationSeries`, and `ScholarlyArticle` entries — consistent with the `@graph` pattern used on `astitva.gsfn.org` . |
| **Missing identifiers** | Added GSFN’s **Ringgold 498495**, **Wikidata Q138519824**, and the founder’s **ISNI 0000 0005 2727 9715** where appropriate . |
| **Author aliases** | Included `also indexed as` note in the header so variant names (S. S. D. Pandey, Sati Pandey) remain discoverable, as on the founder page . |

## Finalized HTML template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">

  <!-- ============================================================
       PAGE TITLE & DESCRIPTION
       Replace [Your Name] with the preferred scholarly name.
       ============================================================ -->
  <title>Select Writings — [Your Name] | Global Synergetic Foundation</title>

  <meta name="description" content="Selected writings of [Your Name], with complete bibliographic details and brief abstracts. Published through the Astitva: Svādhyāya-Saṁhitā series, Global Synergetic Foundation.">
  <meta name="keywords" content="[Your Name], Select Writings, Astitva, Svādhyāya-Saṁhitā, Vedic studies, Indian philosophy, philosophy of science, Global Synergetic Foundation">
  <meta name="author" content="[Your Name]">
  <meta name="robots" content="index, follow">
  <meta name="theme-color" content="#1a1a1a">
  <meta name="language" content="en">
  <meta name="geo.region" content="IN">

  <!-- Canonical & licence -->
  <link rel="canonical" href="https://[your-domain]/select-writings.html">
  <link rel="icon" href="/favicon.ico">
  <link rel="license" href="https://creativecommons.org/licenses/by/4.0/">

  <!-- Open Graph -->
  <meta property="og:type" content="website">
  <meta property="og:title" content="Select Writings — [Your Name]">
  <meta property="og:description" content="Selected writings with complete bibliographic details and abstracts, published through the Astitva: Svādhyāya-Saṁhitā series.">
  <meta property="og:url" content="https://[your-domain]/select-writings.html">
  <meta property="og:site_name" content="Global Synergetic Foundation">
  <meta property="og:locale" content="en_US">

  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary">
  <meta name="twitter:title" content="Select Writings — [Your Name]">
  <meta name="twitter:description" content="Selected writings with complete bibliographic details and abstracts.">

  <!-- Dublin Core -->
  <meta name="dc.title" content="Select Writings — [Your Name]">
  <meta name="dc.creator" content="[Your Name]">
  <meta name="dc.description" content="Selected writings of [Your Name], with complete bibliographic details and brief abstracts.">
  <meta name="dc.publisher" content="Global Synergetic Foundation">
  <meta name="dc.date" content="[YYYY]">
  <meta name="dc.type" content="Text.Collection">
  <meta name="dc.format" content="text/html">
  <meta name="dc.identifier" content="https://[your-domain]/select-writings.html">
  <meta name="dc.language" content="en">
  <meta name="dc.rights" content="CC BY 4.0">

  <!-- Highwire / citation metadata (aligned with GSFN practice) -->
  <meta name="citation_title" content="Select Writings — [Your Name]">
  <meta name="citation_author" content="[Your Name]">
  <meta name="citation_author_orcid" content="https://orcid.org/[ORCID]">
  <meta name="citation_author_institution" content="Global Synergetic Foundation">
  <meta name="citation_publication_date" content="[YYYY]">
  <meta name="citation_publisher" content="Global Synergetic Foundation">
  <meta name="citation_series_title" content="Astitva: Svādhyāya-Saṁhitā">
  <meta name="citation_issn" content="2454-602X">
  <meta name="citation_language" content="eng">

  <!-- ============================================================
       GSFN-COMPATIBLE STYLES
       Do not change these values if uniformity with www.gsfn.org,
       astitva.gsfn.org and sati-shankar.gsfn.org is required.
       ============================================================ -->
  <style>
    :root {
      --text: #1a1a1a;
      --muted: #555;
      --border: #e0e0e0;
      --soft: #f7f7f7;
      --link: #111;
      --bg: #fff;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: "Iowan Old Style", "Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif;
      line-height: 1.58;
      text-rendering: optimizeLegibility;
      -webkit-font-smoothing: antialiased;
      padding: 1.4rem 0.85rem 2.2rem;
    }

    .container {
      max-width: 620px;
      margin: 0 auto;
    }

    /* —— Navigation —— */
    nav {
      font-size: 0.78rem;
      letter-spacing: 0.02em;
      color: var(--muted);
      text-align: center;
      margin-bottom: 1.75rem;
    }
    nav a {
      color: var(--muted);
      text-decoration: none;
      margin: 0 0.4rem;
    }
    nav a:hover, nav a:focus {
      color: var(--text);
      text-decoration: underline;
    }

    /* —— Header —— */
    header {
      text-align: center;
      margin-bottom: 1.6rem;
      padding-bottom: 1.35rem;
      border-bottom: 1px solid var(--border);
    }
    h1 {
      font-size: 1.65rem;
      font-weight: 400;
      letter-spacing: -0.015em;
      margin-bottom: 0.35rem;
    }
    .subhead {
      font-size: 0.93rem;
      color: var(--muted);
      margin-bottom: 0.15rem;
    }
    .indexed-name {
      font-size: 0.76rem;
      color: #777;
      margin-top: 0.55rem;
      line-height: 1.45;
    }

    /* —— Sections & entries —— */
    section {
      margin-bottom: 1.55rem;
    }
    h2 {
      font-size: 0.9rem;
      font-weight: 600;
      letter-spacing: 0.045em;
      text-transform: uppercase;
      color: #2a2a2a;
      margin-bottom: 0.5rem;
      padding-bottom: 0.22rem;
      border-bottom: 1px solid var(--border);
    }

    article {
      margin-bottom: 1.55rem;
      padding-bottom: 1.55rem;
      border-bottom: 1px solid #eee;
    }
    article:last-of-type {
      border-bottom: none;
      padding-bottom: 0;
    }

    .entry-title {
      font-size: 1.05rem;
      font-weight: 600;
      line-height: 1.35;
      margin-bottom: 0.35rem;
    }
    .entry-title a {
      color: var(--text);
      text-decoration: none;
    }
    .entry-title a:hover {
      color: var(--link);
      text-decoration: underline;
      text-underline-offset: 2px;
    }

    .bibliography {
      font-size: 0.85rem;
      color: var(--muted);
      line-height: 1.5;
      margin-bottom: 0.65rem;
    }
    .bibliography span + span::before {
      content: " · ";
    }

    .abstract {
      font-size: 0.94rem;
      margin-bottom: 0.55rem;
    }
    .abstract strong {
      font-weight: 600;
    }

    .identifiers {
      font-size: 0.78rem;
      color: var(--muted);
      line-height: 1.5;
    }
    .identifiers a {
      color: var(--muted);
      text-decoration: none;
      border-bottom: 1px solid transparent;
    }
    .identifiers a:hover {
      color: var(--text);
      border-bottom-color: var(--text);
    }

    /* —— Footer —— */
    footer {
      margin-top: 2rem;
      padding-top: 1rem;
      border-top: 1px solid var(--border);
      font-size: 0.72rem;
      line-height: 1.5;
      color: var(--muted);
      text-align: center;
    }
    footer a {
      color: var(--muted);
    }
    footer a:hover {
      color: var(--text);
    }

    /* —— Responsive —— */
    @media (max-width: 520px) {
      body { padding: 1.1rem 0.7rem 1.8rem; }
      h1 { font-size: 1.4rem; }
    }

    /* —— Print —— */
    @media print {
      body { padding: 0; }
      article { break-inside: avoid; }
      nav, footer { display: none; }
    }
  </style>
</head>
<body>
  <div class="container">

    <!-- ============================================================
         GSFN NAVIGATION — keep exactly as on other GSFN pages
         ============================================================ -->
    <nav aria-label="Primary links">
      <a href="https://www.gsfn.org/">Institution</a>
      <span aria-hidden="true">·</span>
      <a href="https://astitva.gsfn.org/">Astitva</a>
      <span aria-hidden="true">·</span>
      <a href="https://sati-shankar.gsfn.org/">Founder</a>
    </nav>

    <!-- ============================================================
         HEADER
         ============================================================ -->
    <header>
      <h1>Select Writings</h1>
      <div class="subhead">
        <strong>[Your Name]</strong>
      </div>
      <div class="subhead">
        Published through <a href="https://astitva.gsfn.org/">Astitva: Svādhyāya-Saṁhitā</a>,
        Global Synergetic Foundation · ISSN 2454-602X
      </div>
      <div class="indexed-name">
        Also indexed as: [Variant Name 1] · [Variant Name 2] · [Initials]
      </div>
    </header>

    <main>

      <!-- ==========================================================
           ENTRY 1
           Duplicate this <article> block for each writing.
           ========================================================== -->
      <article
        itemscope
        itemtype="https://schema.org/ScholarlyArticle">

        <div class="entry-title" itemprop="name">
          <a href="[URL-TO-PUBLICATION-LANDING-PAGE]" itemprop="url">
            [Full Title of the Writing]
          </a>
        </div>

        <div class="bibliography">
          <span itemprop="author" itemscope itemtype="https://schema.org/Person">
            <span itemprop="name">[Your Name]</span>
          </span>
          <span itemprop="isPartOf" itemscope itemtype="https://schema.org/PublicationSeries">
            <span itemprop="name">Astitva: Svādhyāya-Saṁhitā</span>
          </span>
          <span itemprop="publisher" itemscope itemtype="https://schema.org/Organization">
            <span itemprop="name">Global Synergetic Foundation</span>
          </span>
          <span itemprop="datePublished">[YYYY]</span>
          <span itemprop="identifier" itemscope itemtype="https://schema.org/PropertyValue">
            <meta itemprop="propertyID" content="DOI">
            <span itemprop="value">[DOI or ISBN]</span>
          </span>
        </div>

        <p class="abstract" itemprop="abstract">
          <strong>Abstract / pointer.</strong>
          [1–3 sentences: what the piece is, the central question it addresses,
          and the kind of reader it is written for.]
        </p>

        <div class="identifiers">
          <span>DOI: <a href="https://doi.org/[DOI]" itemprop="sameAs">[DOI]</a></span>
          <span>ORCID: <a href="https://orcid.org/[ORCID]">[ORCID]</a></span>
          <span>Series: <a href="https://astitva.gsfn.org/">Astitva Archive</a></span>
        </div>
      </article>

      <!-- ==========================================================
           ENTRY 2 — copy and fill
           ========================================================== -->
      <article
        itemscope
        itemtype="https://schema.org/ScholarlyArticle">

        <div class="entry-title" itemprop="name">
          <a href="[URL-TO-PUBLICATION-LANDING-PAGE]" itemprop="url">
            [Full Title of the Writing]
          </a>
        </div>

        <div class="bibliography">
          <span itemprop="author" itemscope itemtype="https://schema.org/Person">
            <span itemprop="name">[Your Name]</span>
          </span>
          <span itemprop="isPartOf" itemscope itemtype="https://schema.org/PublicationSeries">
            <span itemprop="name">Astitva: Svādhyāya-Saṁhitā</span>
          </span>
          <span itemprop="publisher" itemscope itemtype="https://schema.org/Organization">
            <span itemprop="name">Global Synergetic Foundation</span>
          </span>
          <span itemprop="datePublished">[YYYY]</span>
          <span itemprop="identifier" itemscope itemtype="https://schema.org/PropertyValue">
            <meta itemprop="propertyID" content="DOI">
            <span itemprop="value">[DOI or ISBN]</span>
          </span>
        </div>

        <p class="abstract" itemprop="abstract">
          <strong>Abstract / pointer.</strong>
          [Brief abstract or pointer.]
        </p>

        <div class="identifiers">
          <span>DOI: <a href="https://doi.org/[DOI]" itemprop="sameAs">[DOI]</a></span>
          <span>ORCID: <a href="https://orcid.org/[ORCID]">[ORCID]</a></span>
          <span>Series: <a href="https://astitva.gsfn.org/">Astitva Archive</a></span>
        </div>
      </article>

      <!-- Add further <article> blocks as needed. -->

    </main>

    <!-- ============================================================
         FOOTER — matches GSFN footer structure
         ============================================================ -->
    <footer>
      <p>
        [Your Name] · ORCID <a href="https://orcid.org/[ORCID]">[ORCID]</a><br>
        Global Synergetic Foundation · New Delhi, India<br>
        <a href="https://www.gsfn.org">www.gsfn.org</a> ·
        <a href="https://astitva.gsfn.org/">astitva.gsfn.org</a>
      </p>
    </footer>

  </div>

  <!-- ============================================================
       STRUCTURED DATA — @graph pattern consistent with GSFN
       Replace bracketed values. Add one ScholarlyArticle object
       per entry in hasPart.
       ============================================================ -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@graph": [
      {
        "@type": "ResearchOrganization",
        "@id": "https://www.gsfn.org/#organization",
        "name": "Global Synergetic Foundation",
        "alternateName": ["GSFN", "GSF Network", "GSFN Bharat"],
        "url": "https://www.gsfn.org",
        "foundingDate": "1992",
        "identifier": [
          {
            "@type": "PropertyValue",
            "propertyID": "Ringgold",
            "value": "498495"
          },
          {
            "@type": "PropertyValue",
            "propertyID": "ISNI",
            "value": "0000 0004 6055 2958"
          },
          {
            "@type": "PropertyValue",
            "propertyID": "Wikidata",
            "value": "Q138519824"
          }
        ]
      },
      {
        "@type": "PublicationSeries",
        "@id": "https://astitva.gsfn.org/#series",
        "name": "Astitva: Svādhyāya-Saṁhitā",
        "issn": "2454-602X",
        "url": "https://astitva.gsfn.org/",
        "publisher": { "@id": "https://www.gsfn.org/#organization" }
      },
      {
        "@type": "CollectionPage",
        "@id": "https://[your-domain]/select-writings.html#page",
        "name": "Select Writings — [Your Name]",
        "description": "Selected writings with complete bibliographic details and abstracts, published through the Astitva: Svādhyāya-Saṁhitā series.",
        "url": "https://[your-domain]/select-writings.html",
        "isPartOf": { "@id": "https://astitva.gsfn.org/#series" },
        "author": {
          "@type": "Person",
          "name": "[Your Name]",
          "identifier": "https://orcid.org/[ORCID]"
        },
        "publisher": { "@id": "https://www.gsfn.org/#organization" },
        "hasPart": [
          {
            "@type": "ScholarlyArticle",
            "name": "[Full Title of the Writing]",
            "author": {
              "@type": "Person",
              "name": "[Your Name]"
            },
            "datePublished": "[YYYY]",
            "identifier": {
              "@type": "PropertyValue",
              "propertyID": "DOI",
              "value": "[DOI]"
            },
            "url": "[URL-TO-PUBLICATION-LANDING-PAGE]",
            "abstract": "[Brief abstract or pointer.]",
            "isPartOf": { "@id": "https://astitva.gsfn.org/#series" }
          }
        ]
      }
    ]
  }
  </script>

</body>
</html>
```

## Notes for filling and maintaining the template

1. **Uniformity** — The typeface, measure (620 px), colour tokens, navigation bar, and footer are now identical in structure and style to the three live GSFN pages. No additional CSS is required for the page to sit visually alongside them.

2. **Header variants** — If you wish to include the founder’s full legal name and aliases (as on `sati-shankar.gsfn.org`), add them inside `.indexed-name`. If the page is for the founder specifically, replace `[Your Name]` with **Sati Shankar** and set the ORCID to **0000-0003-4638-1745** .

3. **DOI and ISBN** — For items in the Astitva series, use the DOI. For print‑on‑demand monographs, use the ISBN India Agency–registered ISBN. The microdata `identifier` block accepts either; change `propertyID` from `DOI` to `ISBN` where appropriate.

4. **JSON‑LD `hasPart`** — Add one `ScholarlyArticle` object per entry. The `@id` of the series is already defined in the graph, so each article can reference it with `"isPartOf": { "@id": "https://astitva.gsfn.org/#series" }`, keeping the graph compact.

5. **Canonical URL** — Replace `https://[your-domain]/select-writings.html` in the `<link rel="canonical">`, Open Graph, Dublin Core, and JSON‑LD sections with the actual URL where the file will be hosted.

6. **Print** — The print stylesheet hides navigation and footer and prevents entries from breaking across pages, so the page can double as a clean printed reading list.

7. **Validation** — The microdata and JSON‑LD can be checked with Google’s Rich Results Test or the Schema.org validator. The `ScholarlyArticle` type is appropriate for journal‑style articles; for monographs you may use `Book` instead, but `ScholarlyArticle` remains acceptable for book chapters and research communications within a series.

This is the finalized template: corrected, aligned to GSFN’s visual and structural system, and ready for manual entry.
