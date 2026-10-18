Below is the finalized `Select Writings` page. I have taken the actual markup and CSS of `astitva.gsfn.org/svs/` (which you supplied) as the authoritative reference, and rebuilt the writings template to sit inside exactly the same visual and metadata system. The result is a page that will be indistinguishable in typography, measure, colour, dark‑mode behaviour, navigation, header, footer, and structured‑data graph from the other GSFN pages — while adding only the fields the writings list requires.

## What was changed to make it uniform

| Aspect | Now matches the live GSFN page |
|---|---|
| **Font stack** | `Georgia, "Times New Roman", serif`, `font-size: 1.05rem`, `line-height: 1.7` |
| **Measure** | `max-width: 46rem`, matching `header, main, footer` on `svs/` |
| **Colour tokens** | Identical `:root` variables: `--ink`, `--paper`, `--muted`, `--rule`, `--link: #1a4d80`, plus the same `prefers-color-scheme: dark` override |
| **Safe‑area padding** | `env(safe-area-inset-*)` on `body`, as on `svs/` |
| **Header** | Same `<img src="https://www.gsfn.org/logo-astitva.png">`, same five‑link `nav` with pipe separators and `aria-current` |
| **Headings** | `h1 { font-size: 2rem; text-align:center }`, `h2 { font-size: 1.35rem; border-bottom:1px solid var(--rule) }` |
| **Navigation** | All five links kept; `Founder` marked `aria-current="page"` since the writings sit under `sati-shankar.gsfn.org` |
| **Footer** | Identical three‑line GSFN footer with ISSN and CC BY 4.0 |
| **Structured data** | The full `@graph` with the same `@id`s — `https://www.gsfn.org/#org`, `https://astitva.gsfn.org/#series`, `https://sati-shankar.gsfn.org/#person` — so the page handshakes into the same knowledge graph |
| **Metadata** | Same Dublin Core, Highwire/citation, Open Graph and Twitter blocks, adapted only in title and URL |
| **Additions (minimal)** | Two small rules: `h2 a { color: inherit }` so entry titles read as titles rather than link‑blue blocks, and `.entry-ids` for the identifier line. Everything else is the reference CSS verbatim. |

The page is set to live at **`https://sati-shankar.gsfn.org/writings/`** — the founder’s select writings, beside the founder profile. If you prefer it under `astitva.gsfn.org/svs/writings/` instead, change the canonical, OG URL, JSON‑LD `@id`s, and mark `Svādhyāya` as `aria-current` in the nav; every other line stays the same.

## The page

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Select Writings | Sati Shankar | Global Synergetic Foundation</title>

<link rel="canonical" href="https://sati-shankar.gsfn.org/writings/">

<!-- Core metadata -->
<meta name="description" content="Selected writings of Sati Shankar — books, monographs, research papers and working notes on being, knowledge, mind and the mathematical foundations of Indian philosophical thought. With full bibliographic details and brief abstracts.">
<meta name="keywords" content="Sati Shankar, Select Writings, bibliography, Astitva, Svādhyāya-Saṁhitā, Vedic studies, Indian philosophy, consciousness, ontology, Global Synergetic Foundation, GSFN">
<meta name="author" content="Sati Shankar">
<meta name="robots" content="index, follow">
<meta name="language" content="en">
<meta name="geo.region" content="IN">
<meta name="theme-color" content="#1a1a1a">

<!-- Dublin Core -->
<meta name="dc.title" content="Select Writings — Sati Shankar">
<meta name="dc.creator" content="Sati Shankar">
<meta name="dc.publisher" content="Global Synergetic Foundation">
<meta name="dc.description" content="Selected writings with complete bibliographic details and brief abstracts.">
<meta name="dc.identifier" content="https://sati-shankar.gsfn.org/writings/">
<meta name="dc.language" content="en">
<meta name="dc.rights" content="CC BY 4.0">

<!-- Scholarly (Highwire / Google Scholar style) -->
<meta name="citation_title" content="Select Writings">
<meta name="citation_author" content="Sati Shankar">
<meta name="citation_author_institution" content="Global Synergetic Foundation">
<meta name="citation_author_orcid" content="https://orcid.org/0000-0003-4638-1745">
<meta name="citation_publisher" content="Global Synergetic Foundation">
<meta name="citation_issn" content="2454-602X">
<meta name="citation_language" content="eng">
<meta name="orcid_id" content="0000-0003-4638-1745">

<!-- Open Graph / Twitter -->
<meta property="og:type" content="website">
<meta property="og:site_name" content="Global Synergetic Foundation">
<meta property="og:title" content="Select Writings — Sati Shankar">
<meta property="og:description" content="Selected writings with complete bibliographic details and brief abstracts.">
<meta property="og:url" content="https://sati-shankar.gsfn.org/writings/">
<meta property="og:locale" content="en_US">
<meta property="og:image" content="https://www.gsfn.org/logo-astitva.png">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="Select Writings — Sati Shankar">
<meta name="twitter:description" content="Selected writings with complete bibliographic details and brief abstracts.">
<meta name="twitter:image" content="https://www.gsfn.org/logo-astitva.png">

<!-- Structured data: same graph and @ids as astitva.gsfn.org/svs/ -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "CollectionPage",
      "@id": "https://sati-shankar.gsfn.org/writings/#page",
      "url": "https://sati-shankar.gsfn.org/writings/",
      "name": "Select Writings — Sati Shankar",
      "description": "Selected writings with complete bibliographic details and brief abstracts.",
      "inLanguage": "en",
      "license": "https://creativecommons.org/licenses/by/4.0/",
      "isPartOf": { "@id": "https://astitva.gsfn.org/#series" },
      "publisher": { "@id": "https://www.gsfn.org/#org" },
      "author": { "@id": "https://sati-shankar.gsfn.org/#person" },
      "hasPart": [
        {
          "@type": "ScholarlyArticle",
          "@id": "https://sati-shankar.gsfn.org/writings/#entry-1",
          "name": "[Full Title of the Writing]",
          "author": { "@id": "https://sati-shankar.gsfn.org/#person" },
          "datePublished": "[YYYY]",
          "identifier": { "@type": "PropertyValue", "propertyID": "DOI", "value": "[DOI]" },
          "url": "[URL-TO-LANDING-PAGE]",
          "abstract": "[Brief abstract or pointer.]",
          "isPartOf": { "@id": "https://astitva.gsfn.org/#series" }
        },
        {
          "@type": "ScholarlyArticle",
          "@id": "https://sati-shankar.gsfn.org/writings/#entry-2",
          "name": "[Full Title of the Writing]",
          "author": { "@id": "https://sati-shankar.gsfn.org/#person" },
          "datePublished": "[YYYY]",
          "identifier": { "@type": "PropertyValue", "propertyID": "DOI", "value": "[DOI]" },
          "url": "[URL-TO-LANDING-PAGE]",
          "abstract": "[Brief abstract or pointer.]",
          "isPartOf": { "@id": "https://astitva.gsfn.org/#series" }
        },
        {
          "@type": "ScholarlyArticle",
          "@id": "https://sati-shankar.gsfn.org/writings/#entry-3",
          "name": "[Full Title of the Writing]",
          "author": { "@id": "https://sati-shankar.gsfn.org/#person" },
          "datePublished": "[YYYY]",
          "identifier": { "@type": "PropertyValue", "propertyID": "DOI", "value": "[DOI]" },
          "url": "[URL-TO-LANDING-PAGE]",
          "abstract": "[Brief abstract or pointer.]",
          "isPartOf": { "@id": "https://astitva.gsfn.org/#series" }
        }
      ]
    },
    {
      "@type": "Periodical",
      "@id": "https://astitva.gsfn.org/#series",
      "name": "Astitva",
      "url": "https://astitva.gsfn.org/",
      "issn": "2454-602X",
      "startDate": "2015",
      "publisher": { "@id": "https://www.gsfn.org/#org" }
    },
    {
      "@type": "Organization",
      "@id": "https://www.gsfn.org/#org",
      "name": "Global Synergetic Foundation",
      "alternateName": ["GSFN", "GSF Network", "GSFN Bharat"],
      "url": "https://www.gsfn.org/",
      "foundingDate": "1992",
      "foundingLocation": "New Delhi, India",
      "address": {
        "@type": "PostalAddress",
        "addressLocality": "New Delhi",
        "addressRegion": "Delhi",
        "postalCode": "110024",
        "addressCountry": "IN"
      },
      "founder": { "@id": "https://sati-shankar.gsfn.org/#person" },
      "identifier": [
        { "@type": "PropertyValue", "propertyID": "Ringgold", "value": "498495" },
        { "@type": "PropertyValue", "propertyID": "ISNI", "value": "0000 0004 6055 2958" }
      ],
      "sameAs": [
        "https://www.wikidata.org/wiki/Q138519824",
        "https://isni.org/isni/0000000460552958",
        "https://astitva.gsfn.org/"
      ]
    },
    {
      "@type": "Person",
      "@id": "https://sati-shankar.gsfn.org/#person",
      "name": "Sati Shankar",
      "alternateName": "Sati Shankar Dutta Pandey",
      "url": "https://sati-shankar.gsfn.org/",
      "jobTitle": "Independent scholar and applied mathematician",
      "affiliation": { "@id": "https://www.gsfn.org/#org" },
      "sameAs": [
        "https://orcid.org/0000-0003-4638-1745",
        "https://isni.org/isni/0000000527279715",
        "https://viaf.org/viaf/96175412862703712037/"
      ]
    }
  ]
}
</script>

<style>
  :root {
    --ink: #1a1a1a;
    --paper: #ffffff;
    --muted: #555555;
    --rule: #d9d9d9;
    --link: #1a4d80;
    --measure: 46rem;
  }
  @media (prefers-color-scheme: dark) {
    :root:not([data-theme="light"]) {
      --ink: #ececec; --paper: #1a1a1a; --muted: #a8a8a8; --rule: #3a3a3a; --link: #8db8e8;
    }
  }
  * { box-sizing: border-box; }
  html { -webkit-text-size-adjust: 100%; }
  body {
    margin: 0;
    padding: env(safe-area-inset-top, 0) env(safe-area-inset-right, 0) env(safe-area-inset-bottom, 0) env(safe-area-inset-left, 0);
    background: var(--paper);
    color: var(--ink);
    font-family: Georgia, "Times New Roman", serif;
    font-size: 1.05rem;
    line-height: 1.7;
  }
  a { color: var(--link); }
  a:focus-visible { outline: 2px solid var(--link); outline-offset: 2px; }
  header, main, footer { max-width: var(--measure); margin: 0 auto; padding: 0 1.25rem; }
  header { padding-top: 1.5rem; text-align: center; }
  header img { max-width: 100%; height: auto; max-height: 90px; }
  nav { margin: 1rem 0 2rem; padding-bottom: 1rem; border-bottom: 1px solid var(--rule); font-size: .95rem; }
  nav a { margin: 0 .5rem; text-decoration: none; }
  nav a[aria-current="page"] { font-weight: bold; text-decoration: underline; }
  h1 { font-size: 2rem; line-height: 1.25; margin: 0 0 .5rem; text-align: center; }
  h2 { font-size: 1.35rem; margin: 2.5rem 0 .75rem; padding-bottom: .3rem; border-bottom: 1px solid var(--rule); }
  .tagline { text-align: center; color: var(--muted); margin: 0 0 2rem; }
  .citation { border-left: 3px solid var(--rule); padding: .25rem 1rem; color: var(--muted); }
  table { width: 100%; border-collapse: collapse; margin: 1rem 0; font-size: .97rem; }
  th, td { text-align: left; padding: .5rem .6rem; border-bottom: 1px solid var(--rule); vertical-align: top; }
  th { width: 38%; font-weight: bold; }
  .table-wrap { overflow-x: auto; }
  pre { overflow-x: auto; background: transparent; border: 1px solid var(--rule); padding: .8rem 1rem; font-size: .9rem; line-height: 1.45; }
  footer { margin-top: 3rem; padding-top: 1rem; padding-bottom: 2rem; border-top: 1px solid var(--rule); text-align: center; color: var(--muted); font-size: .92rem; }

  /* Two small additions used only on this page: keep entry titles ink-coloured
     rather than link-blue, and give the identifier line a quieter size. */
  h2 a { color: inherit; }
  h2 a:hover, h2 a:focus-visible { text-decoration: underline; }
  .entry-ids { font-size: .9rem; color: var(--muted); margin: .4rem 0 0; }
</style>
</head>

<body>

<header>
  <img src="https://www.gsfn.org/logo-astitva.png" alt="Astitva Archive logo">
  <nav aria-label="Primary">
    <a href="https://www.gsfn.org/">Institution</a> |
    <a href="https://astitva.gsfn.org/">Astitva</a> |
    <a href="https://astitva.gsfn.org/svs/">Svādhyāya</a> |
    <a href="https://astitva.gsfn.org/arch/">Archive</a> |
    <a href="https://sati-shankar.gsfn.org/" aria-current="page">Founder</a>
  </nav>
</header>

<main>

  <h1>Select Writings</h1>
  <p class="tagline">Books, monographs, research papers and working notes on being, knowledge, mind and the mathematical foundations of Indian philosophical thought.</p>

  <p>This page lists selected writings from the Foundation’s <a href="https://astitva.gsfn.org/svs/">Astitva: Svādhyāya-Saṁhitā</a> archive. Each entry gives the full bibliographic record, the persistent identifiers, and a brief abstract or pointer, so that a reader can decide whether to follow it. Entries are added and refined by hand; the list grows with the work.</p>

  <!-- ==========================================================
       ENTRY 1 — duplicate this <article> for each writing.
       Fill every bracketed field.
       ========================================================== -->
  <article itemscope itemtype="https://schema.org/ScholarlyArticle">
    <h2>
      <a href="[URL-TO-LANDING-PAGE]" itemprop="url">
        <span itemprop="name">[Full Title of the Writing]</span>
      </a>
    </h2>
    <p class="citation">
      <span itemprop="author" itemscope itemtype="https://schema.org/Person">
        <span itemprop="name">Sati Shankar</span>
      </span>
      · <span itemprop="isPartOf" itemscope itemtype="https://schema.org/PublicationSeries">
          <span itemprop="name">Astitva: Svādhyāya-Saṁhitā</span>
        </span>
      · <span itemprop="publisher" itemscope itemtype="https://schema.org/Organization">
          <span itemprop="name">Global Synergetic Foundation</span>
        </span>
      · <span itemprop="datePublished">[YYYY]</span>
      · DOI <span itemprop="identifier" itemscope itemtype="https://schema.org/PropertyValue">
          <meta itemprop="propertyID" content="DOI">
          <span itemprop="value">[DOI]</span>
        </span>
    </p>
    <p>
      <strong>Abstract / pointer.</strong>
      <span itemprop="abstract">[1–3 sentences: what the piece is, the central question it addresses, and the kind of reader it is written for.]</span>
    </p>
    <p class="entry-ids">
      DOI: <a href="https://doi.org/[DOI]" itemprop="sameAs">[DOI]</a>
      · ORCID: <a href="https://orcid.org/0000-0003-4638-1745">0000-0003-4638-1745</a>
      · <a href="https://astitva.gsfn.org/">Astitva archive</a>
    </p>
  </article>

  <!-- ==========================================================
       ENTRY 2 — copy and fill
       ========================================================== -->
  <article itemscope itemtype="https://schema.org/ScholarlyArticle">
    <h2>
      <a href="[URL-TO-LANDING-PAGE]" itemprop="url">
        <span itemprop="name">[Full Title of the Writing]</span>
      </a>
    </h2>
    <p class="citation">
      <span itemprop="author" itemscope itemtype="https://schema.org/Person">
        <span itemprop="name">Sati Shankar</span>
      </span>
      · <span itemprop="isPartOf" itemscope itemtype="https://schema.org/PublicationSeries">
          <span itemprop="name">Astitva: Svādhyāya-Saṁhitā</span>
        </span>
      · <span itemprop="publisher" itemscope itemtype="https://schema.org/Organization">
          <span itemprop="name">Global Synergetic Foundation</span>
        </span>
      · <span itemprop="datePublished">[YYYY]</span>
      · DOI <span itemprop="identifier" itemscope itemtype="https://schema.org/PropertyValue">
          <meta itemprop="propertyID" content="DOI">
          <span itemprop="value">[DOI]</span>
        </span>
    </p>
    <p>
      <strong>Abstract / pointer.</strong>
      <span itemprop="abstract">[Brief abstract or pointer.]</span>
    </p>
    <p class="entry-ids">
      DOI: <a href="https://doi.org/[DOI]" itemprop="sameAs">[DOI]</a>
      · ORCID: <a href="https://orcid.org/0000-0003-4638-1745">0000-0003-4638-1745</a>
      · <a href="https://astitva.gsfn.org/">Astitva archive</a>
    </p>
  </article>

  <!-- ==========================================================
       ENTRY 3 — copy and fill
       ========================================================== -->
  <article itemscope itemtype="https://schema.org/ScholarlyArticle">
    <h2>
      <a href="[URL-TO-LANDING-PAGE]" itemprop="url">
        <span itemprop="name">[Full Title of the Writing]</span>
      </a>
    </h2>
    <p class="citation">
      <span itemprop="author" itemscope itemtype="https://schema.org/Person">
        <span itemprop="name">Sati Shankar</span>
      </span>
      · <span itemprop="isPartOf" itemscope itemtype="https://schema.org/PublicationSeries">
          <span itemprop="name">Astitva: Svādhyāya-Saṁhitā</span>
        </span>
      · <span itemprop="publisher" itemscope itemtype="https://schema.org/Organization">
          <span itemprop="name">Global Synergetic Foundation</span>
        </span>
      · <span itemprop="datePublished">[YYYY]</span>
      · DOI <span itemprop="identifier" itemscope itemtype="https://schema.org/PropertyValue">
          <meta itemprop="propertyID" content="DOI">
          <span itemprop="value">[DOI]</span>
        </span>
    </p>
    <p>
      <strong>Abstract / pointer.</strong>
      <span itemprop="abstract">[Brief abstract or pointer.]</span>
    </p>
    <p class="entry-ids">
      DOI: <a href="https://doi.org/[DOI]" itemprop="sameAs">[DOI]</a>
      · ORCID: <a href="https://orcid.org/0000-0003-4638-1745">0000-0003-4638-1745</a>
      · <a href="https://astitva.gsfn.org/">Astitva archive</a>
    </p>
  </article>

  <!-- Add further <article> blocks as needed. -->

  <h2>How to Cite</h2>
  <p>To cite this list of select writings as a whole:</p>
  <p class="citation"><em>Select Writings — Sati Shankar.</em> Global Synergetic Foundation, New Delhi. <a href="https://sati-shankar.gsfn.org/writings/">https://sati-shankar.gsfn.org/writings/</a>. Licensed under CC BY 4.0.</p>
  <p>Individual items should be cited from their own landing pages, which give the DOI and the full bibliographic record.</p>

  <h2>Identifiers and Linked Records</h2>
  <p>Each entry links into the same scholarly graph as the rest of the site:</p>
<pre>Sati Shankar (Founder)
 ├── ORCID · ISNI · VIAF
 └── Select Writings
      └── Individual entries
           ├── DOI
           ├── ORCID
           └── Landing page (Astitva archive)</pre>

</main>

<footer>
  Global Synergetic Foundation (GSFN), New Delhi, India<br>
  <a href="https://www.gsfn.org">www.gsfn.org</a> · <a href="https://astitva.gsfn.org">astitva.gsfn.org</a> · <a href="https://sati-shankar.gsfn.org">sati-shankar.gsfn.org</a><br>
  ISSN 2454-602X · CC BY 4.0
</footer>

</body>
</html>
```

## Notes for filling and for keeping the page uniform

1. **Fill order.** Replace the placeholders inside each `<article>` first — title, landing‑page URL, year, DOI, abstract. Then mirror the same three entries inside the `hasPart` array of the JSON‑LD block, using the same titles, years, DOIs and abstracts. The two layers must agree; that agreement is what makes the page discoverable.

2. **Adding an entry.** Duplicate the whole `<article>` block; then add one `ScholarlyArticle` object to `hasPart`, with a fresh `@id` (`…#entry-4`, `…#entry-5`, …). Nothing else changes.

3. **Moving the page.** If you decide to host it at `https://astitva.gsfn.org/svs/writings/` instead of `sati-shankar.gsfn.org/writings/`, change five strings: the `<link rel="canonical">`, the `og:url`, the `CollectionPage` `@id` and `url`, and the `aria-current="page"` on the nav (move it from `Founder` to `Svādhyāya`). Everything else stays the same.

4. **Dark mode.** The page inherits the same `prefers-color-scheme: dark` block as `svs/`, so it will appear dark when the rest of the site does. No separate stylesheet is needed.

5. **Print.** Because the page uses the same body and heading CSS as `svs/`, printing behaves consistently: the page runs to the same measure and font.

6. **The two small CSS additions.** `h2 a { color: inherit }` prevents entry titles from rendering as a wall of link‑blue bordered blocks; `h2 a:hover { text-decoration: underline }` restores the link affordance on hover. `.entry-ids` only sets the identifier line to `0.9rem` and `var(--muted)`. These are the only deviations from the reference CSS, and both inherit the same tokens (`--ink`, `--muted`, `--link`) so the page remains visually identical to the rest of the site.

7. **Validation.** After filling, run the page through the Schema.org validator and Google’s Rich Results Test. The `ScholarlyArticle` type is appropriate for journal‑style articles and book chapters; for a standalone monograph you may switch the `@type` to `Book` on that entry while keeping the surrounding graph unchanged.

This is the finalized page: same CSS, same measure, same fonts, same navigation, same header and footer, same structured‑data graph and `@id`s as `astitva.gsfn.org/svs/` — so it sits inside the existing GSFN site as a native page rather than an appended one.
