# Search-aware Next.js applications

Define the public search surface separately from authenticated product routes. A customer's account history belongs behind access controls; useful category and editorial pages may belong in search. Rendering configuration should follow that distinction rather than exposing private content to obtain more indexed URLs.

## Validate output, not framework labels

Inspect server HTML and browser-rendered content for the relevant title, heading, navigation and primary information. Public links should lead to meaningful URLs. A Server Component is not proof that every content dependency succeeds; exercise slow, missing and failed records.

Use the Metadata API to manage titles, descriptions, canonical URLs and Open Graph information deliberately. Set the production base URL and test dynamic records and translations. The [metadata guide](https://nextjs.org/docs/app/getting-started/metadata-and-og-images) documents current framework behaviour. Social preview metadata and search snippets are different outputs, neither with guaranteed presentation.

## Catalogue and publishing decisions

Keep product URLs stable and define variant/filter rules. Structured data should describe the visible product and current offer; server generation reduces some coordination risks but does not ensure factual accuracy. Document stock freshness, discontinued products and empty categories. Avoid successful responses with an error message in place of the requested record.

Sitemap and robots metadata must describe the agreed public surface. Canonicals, internal navigation, redirects and language alternatives should agree. Do not use a robots disallow rule as the protection for private data or assume it ensures removal from search. During migration, preserve a meaningful redirect map and inspect deployed status codes.

## Acceptance sample

Test one editorial page, category, product variant, missing record and language alternative. Confirm that mobile navigation retains the useful paths and important content. Measure performance against representative tasks and check content shifts, heavy client scripts and slow data dependencies.

Google can render JavaScript, but fragile client-only content adds dependencies to delivery. Choose server or static output where it fits the content and deployment. Consult [Google's JavaScript SEO guidance](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics) alongside framework documentation. No rendering strategy guarantees indexing or ranking. This repository provides educational guidance and does not request Search Console access or submissions.
