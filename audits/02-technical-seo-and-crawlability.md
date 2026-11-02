# 02. Technical SEO & Crawlability Audit

> A practical technical audit framework for checking whether search engines can discover, crawl, render, understand, and index the important pages of a website.

**Audit category:** Technical SEO  
**Difficulty:** Beginner to Advanced  
**Applies to:** Business websites, blogs, portfolios, publishers, ecommerce stores, SaaS platforms, and web applications  
**Priority:** High

---

## 1. Purpose of This Audit

Technical SEO is the process of improving the technical conditions that help search engines access, process, and understand website content.

A website may have excellent content and a professional design but still struggle in organic search if important pages are inaccessible, blocked, incorrectly redirected, duplicated, or difficult to render.

This audit examines the technical foundations of search visibility.

It covers:

- Website accessibility and crawlability
- Indexability and indexing controls
- Robots.txt configuration
- XML sitemaps
- URL structure and normalization
- Canonicalization and duplicate URLs
- HTTP status codes and redirects
- Internal linking and crawl paths
- JavaScript rendering
- Mobile accessibility
- Structured data implementation
- International SEO signals
- Image and media accessibility
- Server errors and crawl efficiency
- AI crawler access and technical discoverability
- Technical monitoring and maintenance

**Important:** Passing a technical audit does not guarantee rankings or indexing. Google decides which pages to crawl, index, and display based on its systems and other signals.

Google's basic technical requirements for eligibility are relatively simple: Googlebot must not be blocked, the page must work successfully, and the page must contain indexable content. Meeting these requirements does not guarantee inclusion in Search.

Reference: [Google Search Technical Requirements](https://developers.google.com/search/docs/essentials/technical)

---

## 2. Establish the Technical Audit Baseline

Before changing anything, understand the website's current technical condition.

### 2.1 Identify the website environment

- [ ] Confirm the primary website domain.
- [ ] Identify the CMS or development framework.
- [ ] Identify the hosting provider and server environment.
- [ ] Confirm whether the website uses WordPress, Shopify, Wix, Webflow, a custom CMS, or another platform.
- [ ] Identify whether the website uses server-side rendering, static generation, client-side rendering, or a combination.
- [ ] Identify CDN, caching, firewall, and security services.
- [ ] Check whether staging, development, or test environments are publicly accessible.
- [ ] Identify the main website languages and target countries.
- [ ] Identify important page types: homepage, service pages, category pages, product pages, articles, landing pages, and other templates.

**Why it matters:** Technical recommendations depend on the website's architecture. A WordPress blog, Shopify store, and JavaScript web application will not have identical technical requirements.

**How to check:**

Use browser inspection, CMS administration, hosting documentation, developer tools, and technology detection tools.

Possible tools:

- [Wappalyzer](https://www.wappalyzer.com/)
- [BuiltWith](https://builtwith.com/)
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)

### 2.2 Create a URL inventory

- [ ] Identify all important public URLs.
- [ ] Identify important page templates.
- [ ] Separate indexable pages from utility pages.
- [ ] Identify pages that should not appear in search results.
- [ ] Identify old, redirected, discontinued, and duplicate URLs.
- [ ] Record the canonical URL for important pages.
- [ ] Compare the website's URL inventory with its XML sitemap and Search Console data.

Maintain a spreadsheet containing:

| Field | What to record |
|---|---|
| URL | Full page URL |
| Page type | Homepage, service, product, article, etc. |
| HTTP status | 200, 301, 404, 500, etc. |
| Indexability | Indexable or non-indexable |
| Canonical | Preferred URL |
| Sitemap | Included or excluded |
| Internal links | Important incoming links |
| Priority | High, medium, or low |
| Notes | Errors and recommended fixes |

Do not assume every URL discovered by a crawler deserves indexing. Filter out duplicate, utility, low-value, and intentionally excluded URLs.

---

## 3. Website Accessibility & Crawlability

### 3.1 Confirm that important pages are publicly accessible

- [ ] Important pages load without requiring authentication.
- [ ] Search engines can access the intended page content.
- [ ] No unexpected firewall or security rule blocks legitimate search crawlers.
- [ ] Important pages do not return access-denied responses.
- [ ] CDN or hosting security settings do not accidentally block crawlers.
- [ ] Important content is not available only to logged-in users.
- [ ] Website pages work consistently across supported browsers.

**Why it matters:** A search engine cannot properly process a page that it cannot access.

**How to check:**

1. Open important URLs in an incognito browser window.
2. Check their HTTP response codes.
3. Use Google Search Console's URL Inspection tool.
4. Review server or CDN logs when crawler access appears inconsistent.
5. Investigate unexpected 403, 429, or 5xx responses.

**Fix:** Correct access restrictions, firewall rules, authentication settings, or server errors without weakening legitimate security protections.

**Verify:** Test the affected URL again and inspect the result in Search Console.

### 3.2 Understand crawling, rendering, and indexing

These are related but different stages.

| Stage | Meaning |
|---|---|
| Crawling | A search engine discovers and requests a URL. |
| Rendering | It processes the page, including supported JavaScript execution. |
| Indexing | It analyzes and may store the page in its search index. |
| Serving | It may display the page for relevant searches. |

A page can be crawled without being indexed. It can also be discovered but not rendered as expected.

**Audit checks:**

- [ ] Important URLs are discoverable through internal links or sitemaps.
- [ ] Important pages return the correct response.
- [ ] Main content is available to crawlers.
- [ ] Rendering does not remove important text or links.
- [ ] Search Console does not report unexpected indexing exclusions.
- [ ] Important pages are not accidentally blocked by multiple technical controls.

Reference: [How Google Search Works](https://developers.google.com/search/docs/fundamentals/how-search-works)

### 3.3 Check crawl depth and orphan pages

An orphan page is a page that has no meaningful internal links pointing to it.

- [ ] Important pages are reachable through the website's navigation or contextual links.
- [ ] Important pages are not buried unnecessarily deep in the website structure.
- [ ] Important pages have relevant incoming internal links.
- [ ] No valuable page depends exclusively on being present in an XML sitemap.
- [ ] Important pages are accessible through ordinary HTML links.

**Why it matters:** Internal links help users and search engines discover related content and understand the website's structure.

**How to check:**

Use a website crawler to identify:

- Pages with zero internal inlinks
- Pages with excessive click depth
- Broken internal links
- Pages reachable only through redirects
- Pages missing from navigation or contextual linking

**Fix:** Add relevant links from suitable parent pages, category pages, articles, or navigation elements.

Do not add irrelevant links simply to increase the number of internal links.

Reference: [Google Link Best Practices](https://developers.google.com/search/docs/crawling-indexing/links-crawlable)

---

## 4. Robots.txt Configuration

### 4.1 Check whether robots.txt exists

- [ ] Open `https://example.com/robots.txt`.
- [ ] Confirm that the file is accessible.
- [ ] Check whether the rules are intentional.
- [ ] Confirm that important public pages and resources are not unintentionally blocked.
- [ ] Check whether the file contains outdated or conflicting directives.
- [ ] Confirm that the correct sitemap location is declared when appropriate.

Replace `example.com` with the actual website domain.

### 4.2 Review crawler-specific rules

Example:

```txt
User-agent: *
Disallow: /admin/
Disallow: /private/

Sitemap: https://example.com/sitemap.xml
```

This is only an illustration. Do not copy it blindly. The correct rules depend on the website's structure.

- [ ] Review `User-agent` rules.
- [ ] Review `Disallow` rules.
- [ ] Review `Allow` rules where needed.
- [ ] Check whether different crawler groups receive different instructions.
- [ ] Confirm that important CSS and JavaScript resources are accessible when required for rendering.
- [ ] Check for accidental site-wide blocking.

**Critical distinction:**

`robots.txt` controls crawling instructions. It is not a reliable method for keeping a page out of search results or protecting private information.

If a URL is blocked from crawling, a search engine may still discover its URL through external links and potentially show limited information about it.

For pages that should not appear in search results, use an appropriate indexing control such as `noindex`, while allowing the crawler to access the page so it can read that directive.

For confidential content, use proper authentication and access controls.

**Common mistake:**

```txt
User-agent: *
Disallow: /
```

This blocks crawling across the entire website for matching crawlers. It is generally inappropriate for a public website intended to appear in search.

**Verify:**

Use:

- [Google Search Console](https://search.google.com/search-console/)
- [Robots.txt documentation](https://developers.google.com/search/docs/crawling-indexing/robots/intro)

### 4.3 Check staging and development environments

- [ ] Staging websites are not accidentally exposed as public production content.
- [ ] Development URLs are not included in production sitemaps.
- [ ] Test pages do not compete with production pages.
- [ ] Authentication or access controls protect private environments.
- [ ] Temporary indexing restrictions are removed from production after deployment.

Do not rely on `robots.txt` alone to protect a private staging environment.

---

## 5. Indexability & Indexing Controls

### 5.1 Review meta robots directives

Check important pages for indexing instructions.

Examples:

```html
<meta name="robots" content="index, follow">
```

```html
<meta name="robots" content="noindex, follow">
```

- [ ] Important pages do not contain accidental `noindex` directives.
- [ ] Utility pages are handled according to their intended search visibility.
- [ ] Robots meta tags are consistent with the page's purpose.
- [ ] JavaScript does not unexpectedly change indexing directives.
- [ ] Page templates do not apply the same indexing rule to every page without considering page type.

**Important:** `index, follow` is generally the default behavior, so explicitly writing it on every page is not necessary.

### 5.2 Check X-Robots-Tag HTTP headers

Search engines can receive indexing instructions through HTTP response headers as well as HTML meta tags.

Example:

```http
X-Robots-Tag: noindex
```

- [ ] Check whether important HTML pages receive unexpected `X-Robots-Tag` headers.
- [ ] Check PDF and other non-HTML resources where indexing controls are relevant.
- [ ] Confirm that server-level rules do not unintentionally apply `noindex` across the website.

Use browser developer tools, command-line HTTP requests, or a crawler to inspect response headers.

### 5.3 Review Google Search Console indexing reports

- [ ] Verify the correct website property in Search Console.
- [ ] Review the Page Indexing report.
- [ ] Identify important pages that are not indexed.
- [ ] Investigate unexpected `noindex` exclusions.
- [ ] Investigate pages blocked by robots.txt.
- [ ] Review redirects and server errors.
- [ ] Review duplicate and canonical-related exclusions.
- [ ] Compare reported issues with actual business priorities.

Common report classifications include:

- Crawled - currently not indexed
- Discovered - currently not indexed
- Duplicate without user-selected canonical
- Duplicate, Google chose different canonical than user
- Alternate page with proper canonical tag
- Excluded by `noindex`
- Blocked by robots.txt
- Not found (404)
- Page with redirect
- Server error (5xx)

These classifications require investigation, not automatic fixes. Some exclusions are intentional.

**Fix:** Prioritize valuable pages that should be indexed. Review content quality, internal links, technical accessibility, canonical signals, and response behavior before requesting another crawl.

**Important:** Submitting a URL for indexing does not guarantee that Google will index it.

Reference: [Google Search Console Help](https://support.google.com/webmasters/)

---

## 6. XML Sitemap Audit

### 6.1 Check sitemap availability

Common sitemap locations include:

```text
https://example.com/sitemap.xml
https://example.com/sitemap_index.xml
```

- [ ] Confirm whether an XML sitemap exists.
- [ ] Check whether the sitemap returns a successful response.
- [ ] Confirm that the sitemap is valid XML.
- [ ] Check whether it can be accessed by search engines.
- [ ] Confirm that the sitemap index points to valid child sitemaps where applicable.
- [ ] Confirm that the sitemap is submitted in Search Console.

The actual sitemap location depends on the CMS or website configuration.

### 6.2 Review sitemap URL quality

- [ ] Include preferred canonical URLs.
- [ ] Include only URLs intended for indexing.
- [ ] Exclude redirected URLs.
- [ ] Exclude URLs returning 404 or server errors.
- [ ] Exclude URLs blocked from crawling.
- [ ] Exclude duplicate URL variants.
- [ ] Exclude private, utility, and irrelevant pages.
- [ ] Use the correct protocol and hostname.
- [ ] Keep sitemap entries updated when pages are added, removed, or changed.

**Why it matters:** Sitemaps help search engines discover important URLs and understand when content has been updated.

A sitemap is not a guarantee of crawling, indexing, or ranking.

### 6.3 Review lastmod values

Example:

```xml
<url>
  <loc>https://example.com/technical-seo/</loc>
  <lastmod>2026-10-20</lastmod>
</url>
```

- [ ] Check whether `lastmod` reflects meaningful page updates.
- [ ] Avoid changing every URL's modification date on every automated sitemap refresh.
- [ ] Update dates when the primary content has genuinely changed.
- [ ] Do not use fake modification dates to encourage crawling.

### 6.4 Review sitemap size and structure

- [ ] Check the sitemap protocol limits.
- [ ] Split large sitemaps into smaller files when appropriate.
- [ ] Use a sitemap index for multiple sitemap files.
- [ ] Organize large websites by content type when useful.
- [ ] Confirm that child sitemap URLs are accessible.

For standard XML sitemaps, each sitemap is limited to 50,000 URLs or 50 MB uncompressed. Larger websites should use multiple sitemap files and a sitemap index.

Reference: [Build and Submit a Sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)

---

## 7. URL Structure & Normalization

### 7.1 Review URL readability

- [ ] URLs are understandable and descriptive.
- [ ] URL paths reflect the website's content organization where useful.
- [ ] Unnecessary parameters are avoided.
- [ ] URLs do not contain excessive random identifiers.
- [ ] Words are separated consistently, preferably with hyphens.
- [ ] URLs do not change unnecessarily.
- [ ] The website uses a consistent URL naming convention.

Example:

Good:

```text
https://example.com/services/technical-seo/
```

Less descriptive:

```text
https://example.com/page?id=82736&cat=4
```

Readable URLs improve clarity for users, but there is no need to force keywords into every URL.

### 7.2 Check URL variants

Review whether the website responds consistently across these versions:

```text
http://example.com
https://example.com
http://www.example.com
https://www.example.com
```

- [ ] Select the preferred HTTPS hostname.
- [ ] Redirect alternative versions to the preferred version.
- [ ] Avoid having multiple versions of the same page independently accessible.
- [ ] Check trailing slash consistency.
- [ ] Review uppercase and lowercase URL behavior.
- [ ] Review unnecessary query parameters.
- [ ] Check whether URL parameters create duplicate page variations.

**Fix:** Establish one consistent URL version and use redirects and canonical signals appropriately.

### 7.3 Avoid unnecessary URL changes

- [ ] Existing URLs are retained when they work well.
- [ ] URL changes have a clear business or structural reason.
- [ ] Old URLs redirect to their closest relevant replacements.
- [ ] Internal links are updated after URL changes.
- [ ] Sitemaps and canonical tags are updated.
- [ ] External backlinks are considered before removing important URLs.

Do not redesign URL structures only to make them look shorter or more keyword-rich.

Reference: [URL Structure Best Practices](https://developers.google.com/search/docs/crawling-indexing/url-structure)

---

## 8. Canonicalization & Duplicate Content

### 8.1 Review canonical tags

Example:

```html
<link rel="canonical" href="https://example.com/technical-seo/" />
```

- [ ] Important indexable pages have an appropriate canonical strategy.
- [ ] Canonical URLs point to the preferred version of the content.
- [ ] Canonical URLs return successful responses.
- [ ] Canonical URLs are not blocked by robots.txt.
- [ ] Canonical URLs are not redirected to unrelated pages.
- [ ] Canonical URLs use the preferred HTTPS hostname.
- [ ] Canonical tags are consistent with internal links and sitemap entries.
- [ ] Canonical tags are not accidentally pointing every page to the homepage.

A self-referencing canonical is often a useful implementation choice for indexable pages, but the correct strategy depends on the page and its alternatives.

### 8.2 Identify duplicate URL variations

Check for duplicates created by:

- HTTP and HTTPS versions
- WWW and non-WWW versions
- URL parameters
- Sorting and filtering
- Session identifiers
- Tracking parameters
- Printer-friendly versions
- Duplicate category or archive pages
- Similar product URLs
- CMS-generated alternative URLs

**Fix:** Decide whether each variation should be consolidated, canonicalized, redirected, or intentionally kept separate.

Do not canonicalize genuinely different pages to one another merely because they share a template or topic.

### 8.3 Understand canonical signals

Google considers multiple signals when selecting a canonical URL, including:

- Redirects
- `rel="canonical"` annotations
- Sitemap inclusion
- HTTPS and other URL signals

A canonical tag is a signal, not an absolute command. Google may select a different canonical URL.

**Verify:** Compare the declared canonical with Google's selected canonical in URL Inspection.

Reference: [How to Specify a Canonical URL](https://developers.google.com/search/docs/crawling-indexing/canonicalization)

---

## 9. HTTP Status Codes & Redirect Management

### 9.1 Audit important HTTP status codes

| Status | Meaning | Audit action |
|---|---|---|
| 200 | Successful response | Confirm page content is correct |
| 301 | Permanent redirect | Check destination and relevance |
| 302 | Temporary redirect | Confirm temporary intent |
| 307 | Temporary redirect | Confirm temporary intent |
| 308 | Permanent redirect | Confirm permanent intent |
| 401 | Authentication required | Check whether access is intentional |
| 403 | Access forbidden | Investigate accidental crawler blocks |
| 404 | Page not found | Check whether removal is intentional |
| 410 | Resource gone | Confirm permanent removal |
| 429 | Too many requests | Investigate rate limiting |
| 500 | Internal server error | Investigate application/server failure |
| 502 | Bad gateway | Check upstream server or proxy |
| 503 | Service unavailable | Check temporary outages |
| 504 | Gateway timeout | Investigate server response delays |

### 9.2 Review redirect implementation

- [ ] Permanent moves use appropriate permanent redirects.
- [ ] Temporary redirects are used only when the move is temporary.
- [ ] Redirects point to relevant destinations.
- [ ] Redirect chains are minimized.
- [ ] Redirect loops are eliminated.
- [ ] Internal links point directly to final destinations.
- [ ] Redirected URLs are removed from the sitemap.
- [ ] Important backlinks and old URLs are considered during migrations.

Example of an unnecessary redirect chain:

```text
/page-a/ → /page-b/ → /page-c/
```

Preferred:

```text
/page-a/ → /page-c/
```

Avoid redirecting every deleted page to the homepage. If a relevant replacement does not exist, the appropriate response may be a genuine 404 or 410.

### 9.3 Review custom 404 pages

- [ ] Non-existent pages return a genuine 404 status.
- [ ] The 404 page explains that the requested content was not found.
- [ ] Users can navigate to useful sections.
- [ ] Important replacement pages are linked where relevant.
- [ ] Soft 404 behavior is avoided.

A visually designed error page that returns HTTP 200 may be treated as a soft 404.

Reference: [Redirects and Google Search](https://developers.google.com/search/docs/crawling-indexing/301-redirects)

---

## 10. Internal Linking & Site Architecture

### 10.1 Check HTML link crawlability

A standard crawlable link generally uses an anchor element with an `href` attribute.

Recommended:

```html
<a href="/services/technical-seo/">
  Technical SEO Services
</a>
```

Avoid relying exclusively on JavaScript click handlers or non-link elements for important navigation.

- [ ] Important links use valid destinations.
- [ ] Navigation links work without unusual interaction requirements.
- [ ] Important links are not hidden behind inaccessible controls.
- [ ] Anchor text describes the destination.
- [ ] Internal links do not point unnecessarily through redirects.
- [ ] Broken internal links are fixed.

### 10.2 Review site hierarchy

- [ ] Main navigation reflects important website sections.
- [ ] Related pages are grouped logically.
- [ ] Important pages can be reached without excessive navigation.
- [ ] Category and subcategory relationships are understandable.
- [ ] Breadcrumb navigation is implemented where useful.
- [ ] Internal links connect related content naturally.
- [ ] Important pages are not orphaned.

### 10.3 Review breadcrumbs

Example:

```text
Home > SEO Guides > Technical SEO
```

- [ ] Breadcrumbs accurately represent the page hierarchy.
- [ ] Breadcrumb links work.
- [ ] Breadcrumb labels are understandable.
- [ ] Structured data matches the visible breadcrumb content when implemented.
- [ ] Breadcrumbs do not create misleading navigation paths.

Do not assume that adding breadcrumb structured data guarantees a breadcrumb display in search results.

Reference: [Google Link Best Practices](https://developers.google.com/search/docs/crawling-indexing/links-crawlable)

---

## 11. JavaScript SEO & Rendering

JavaScript can power modern websites, but important content and navigation must remain discoverable and understandable to search engines and other automated systems.

### 11.1 Check initial HTML content

- [ ] Important page content is available in the initial HTML where practical.
- [ ] Main headings and primary content are not missing before JavaScript executes.
- [ ] Important internal links are represented as crawlable links.
- [ ] Page titles and metadata are correct.
- [ ] Canonical information is consistent.
- [ ] Important content does not depend on fragile client-side interactions.

### 11.2 Test rendered content

- [ ] Important content appears after rendering.
- [ ] JavaScript errors do not prevent page content from loading.
- [ ] Navigation links remain available after rendering.
- [ ] Lazy-loaded content works as expected.
- [ ] Content is not hidden behind user actions that automated systems cannot perform.
- [ ] Important images and media load correctly.
- [ ] The rendered page matches the intended user experience.

**How to check:**

1. Inspect the raw HTML response.
2. Compare it with the rendered page.
3. Use Search Console URL Inspection.
4. Review rendered HTML and screenshots where available.
5. Test pages with browser JavaScript disabled as an additional diagnostic, not as the only SEO test.
6. Review browser console errors.

### 11.3 Review client-side routing

For single-page applications:

- [ ] Important content has its own meaningful URL.
- [ ] Navigation uses browser-compatible URL handling.
- [ ] Page transitions update the URL correctly.
- [ ] Direct visits to deep URLs work.
- [ ] Refreshing a deep URL does not return an error.
- [ ] History navigation works correctly.
- [ ] Important pages do not depend on URL fragments to represent separate indexable content.

Use the History API for client-side navigation rather than relying on hash fragments to represent separate search pages.

### 11.4 Evaluate rendering architecture

Depending on the website, consider:

- Server-side rendering (SSR)
- Static site generation (SSG)
- Dynamic rendering only where appropriate
- Hybrid rendering approaches

Server-side or pre-rendered HTML can improve accessibility for users and automated systems, but a framework does not automatically guarantee better SEO.

Choose the rendering strategy based on content requirements, performance, maintenance, and technical capability.

Reference: [JavaScript SEO Basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)

---

## 12. Mobile Accessibility & Responsive Technical Setup

### 12.1 Check responsive behavior

- [ ] Pages adapt to common mobile screen sizes.
- [ ] Text remains readable without unnecessary zooming.
- [ ] Navigation is usable on mobile.
- [ ] Buttons and links are accessible.
- [ ] Important content is not removed from mobile versions.
- [ ] Images do not overflow the viewport.
- [ ] Forms and interactive components work correctly.
- [ ] Mobile and desktop versions provide equivalent important content.

### 12.2 Check viewport configuration

A common viewport declaration is:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

- [ ] A suitable viewport declaration is present.
- [ ] Layout does not require horizontal scrolling for ordinary content.
- [ ] Responsive CSS works correctly.
- [ ] Important content is not hidden at mobile breakpoints.

### 12.3 Check mobile-first indexing readiness

Google primarily uses the mobile version of a website's content for indexing.

- [ ] Important text is present on mobile.
- [ ] Important structured data is available on mobile.
- [ ] Main navigation and internal links are accessible.
- [ ] Metadata is consistent across mobile and desktop.
- [ ] Image alt text and important media are not lost.
- [ ] Mobile pages do not unintentionally block important resources.

Reference: [Mobile-first Indexing Best Practices](https://developers.google.com/search/docs/crawling-indexing/mobile/mobile-sites-mobile-first-indexing)

---

## 13. Structured Data & Schema Markup

Structured data helps search engines understand the meaning and context of supported content. It may also make eligible pages qualify for enhanced search appearances.

It does not guarantee rich results or higher rankings.

### 13.1 Identify relevant schema types

Choose structured data based on the actual page content and Google's current supported features.

Potential types include:

- Organization
- LocalBusiness
- Article
- Product
- BreadcrumbList
- Event
- Recipe
- VideoObject
- JobPosting
- Course
- SoftwareApplication
- ProfilePage
- Other supported types where genuinely applicable

Do not add every schema type to every page.

### 13.2 Review schema accuracy

- [ ] Structured data represents visible page content.
- [ ] Business details are accurate.
- [ ] Product information matches the actual product page.
- [ ] Ratings and reviews are genuine and eligible.
- [ ] Author and publisher information is correct.
- [ ] Breadcrumb data reflects the actual hierarchy.
- [ ] Required properties are present for the selected feature.
- [ ] Structured data does not contain misleading claims.
- [ ] Schema is updated when the underlying content changes.

### 13.3 Validate structured data

Use:

- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)
- [Google Search Console Enhancements reports](https://search.google.com/search-console/)

Understand the difference:

- A syntax-valid schema is not automatically eligible for a Google rich result.
- Eligibility does not guarantee that a rich result will appear.
- Not every Schema.org type is supported as a Google rich result.

### 13.4 Review JSON-LD implementation

Example:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Example Company",
  "url": "https://example.com/"
}
</script>
```

This is a basic illustration, not a complete schema template for every business.

- [ ] JSON-LD syntax is valid.
- [ ] The entity represented is accurate.
- [ ] URLs and identifiers are correct.
- [ ] Duplicate or conflicting schema is avoided.
- [ ] Schema does not describe information that users cannot verify on the page.

Reference: [Google Structured Data Guidelines](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)

---

## 14. International SEO & Language Targeting

This section applies to websites targeting multiple countries or languages.

### 14.1 Check language and regional versions

- [ ] Each language or regional version has a clear URL.
- [ ] Pages use the correct language.
- [ ] Important translations are complete and useful.
- [ ] Navigation and internal links lead to the appropriate language version.
- [ ] Users can discover alternate language versions.
- [ ] Country-specific content is not accidentally duplicated without a clear purpose.

### 14.2 Review hreflang annotations

Example:

```html
<link rel="alternate"
      hreflang="en-in"
      href="https://example.com/in/" />

<link rel="alternate"
      hreflang="en-us"
      href="https://example.com/us/" />

<link rel="alternate"
      hreflang="x-default"
      href="https://example.com/" />
```

- [ ] Language and region codes are valid.
- [ ] Each alternate page references the other relevant versions.
- [ ] Return links are present.
- [ ] URLs are absolute and accessible.
- [ ] Each language version has an appropriate canonical strategy.
- [ ] Hreflang references do not point to broken or redirected URLs.
- [ ] The `x-default` value is used only when appropriate.

Do not use hreflang simply because two pages have similar layouts. There must be a genuine language or regional relationship.

### 14.3 Check language consistency

- [ ] Page language matches the intended audience.
- [ ] Translated pages contain meaningful localized content.
- [ ] Currency, address, phone number, and regional details are appropriate.
- [ ] Internal links do not unexpectedly switch users between languages.
- [ ] Browser language redirects do not prevent users or crawlers from accessing alternate versions.

Reference: [Managing Multi-Regional and Multilingual Sites](https://developers.google.com/search/docs/specialty/international/localized-versions)

---

## 15. Image, Video & Other Media Technical SEO

### 15.1 Image accessibility and discoverability

- [ ] Important images use accessible HTML image elements where appropriate.
- [ ] Image URLs are accessible.
- [ ] Relevant images have descriptive alt text.
- [ ] Decorative images use appropriate empty alt attributes.
- [ ] Image filenames are understandable where practical.
- [ ] Image dimensions are specified where appropriate to reduce layout shifts.
- [ ] Responsive image delivery is configured correctly.
- [ ] Important images are not unintentionally blocked.
- [ ] Image-heavy pages are tested for loading problems.

### 15.2 Review lazy loading

- [ ] Below-the-fold images use appropriate lazy loading where useful.
- [ ] Important above-the-fold images are not unnecessarily delayed.
- [ ] The primary page content is not dependent on an unreliable lazy-loading implementation.
- [ ] Lazy-loaded images become available when needed.
- [ ] Search engines can access the actual image URLs.

Do not lazy-load the main hero image by default if doing so delays its discovery and loading.

### 15.3 Review video and media pages

Where relevant:

- [ ] Video content has a descriptive title.
- [ ] Video information is accessible.
- [ ] Relevant thumbnails are available.
- [ ] Video metadata accurately describes the content.
- [ ] Video structured data is valid when implemented.
- [ ] Important media pages are internally linked.
- [ ] Embedded media does not prevent the main page from rendering.

Reference: [Google Image SEO Best Practices](https://developers.google.com/search/docs/appearance/google-images)

---

## 16. Website Security & HTTPS

### 16.1 Verify HTTPS configuration

- [ ] The production website uses HTTPS.
- [ ] The SSL/TLS certificate is valid.
- [ ] The certificate covers the correct hostname.
- [ ] HTTP URLs redirect appropriately to HTTPS.
- [ ] Internal resources do not create mixed-content warnings.
- [ ] Canonical URLs use the preferred HTTPS version.
- [ ] Sitemap URLs use HTTPS.
- [ ] Important external integrations work correctly after HTTPS configuration.

### 16.2 Review security fundamentals

- [ ] CMS, themes, plugins, and dependencies are maintained.
- [ ] Unused plugins and extensions are removed where safe.
- [ ] Administrator access is protected.
- [ ] Strong authentication practices are used.
- [ ] Backups are maintained and tested.
- [ ] Security headers are reviewed where appropriate.
- [ ] Vulnerable dependencies are investigated.
- [ ] Website security incidents are monitored.
- [ ] Malware and unauthorized page injections are investigated.

**Important:** Security is not a substitute for content quality or a guaranteed ranking advantage. It is essential for user protection, reliability, and website integrity.

### 16.3 Review unwanted indexed content

- [ ] Spam pages are not being generated.
- [ ] Hacked URLs are investigated.
- [ ] Unauthorized redirects are checked.
- [ ] Unexpected subdomains are reviewed.
- [ ] Search Console security issues are monitored.
- [ ] Removed malicious content is handled correctly.

Reference: [Google Search Essentials](https://developers.google.com/search/docs/essentials)

---

## 17. Crawl Efficiency & Large Website Considerations

Crawl budget optimization is not necessary for every website.

For a small business website or a blog with a limited number of regularly updated pages, a clean sitemap, good internal linking, and routine Search Console monitoring are usually more relevant than advanced crawl-budget engineering.

This section is particularly important for large ecommerce websites, marketplaces, publishers, and websites with rapidly changing or very large URL inventories.

### 17.1 Identify crawl waste

- [ ] Excessive URL parameters are reviewed.
- [ ] Duplicate filter and sort URLs are assessed.
- [ ] Session-based URLs are reviewed.
- [ ] Infinite URL combinations are controlled.
- [ ] Low-value search result pages are assessed.
- [ ] Redirect chains and unnecessary redirects are reduced.
- [ ] Internal links do not generate endless URL variations.
- [ ] Important pages remain discoverable.

### 17.2 Review faceted navigation

Ecommerce websites may generate many URL variations through filters such as:

- Colour
- Size
- Brand
- Price
- Availability
- Sorting
- Multiple filter combinations

Decide which filtered pages genuinely provide unique value and deserve to be crawlable or indexable.

- [ ] Valuable filter combinations have a deliberate URL and indexing strategy.
- [ ] Unnecessary combinations do not create unlimited crawl paths.
- [ ] Canonical and indexing signals are consistent.
- [ ] Internal links do not expose endless low-value URL variations.
- [ ] Important category and product pages remain accessible.

Do not block all filtered URLs automatically. Some filtered pages may serve valuable search demand.

### 17.3 Use server logs for advanced diagnosis

For larger websites, review server logs to understand:

- Which URLs search crawlers request
- Crawl frequency
- Response codes
- Response times
- Repeated requests to low-value URLs
- Unexpected crawler errors
- Whether important pages are being discovered

Verify crawler identity using reliable methods rather than trusting a user-agent string alone.

Reference: [Google Crawl Budget Guide](https://developers.google.com/crawling/docs/crawl-budget)

---

## 18. AI Crawler Access & Technical Discoverability

AI search and answer platforms may use different crawlers, retrieval systems, or content access methods. Their behavior and policies vary.

This section is about technical access and content discoverability, not a guaranteed method for earning AI citations.

### 18.1 Identify relevant crawler policies

- [ ] Understand which AI-related crawlers are relevant to the website's goals.
- [ ] Review their published documentation and user-agent information.
- [ ] Check whether robots.txt intentionally allows or disallows them.
- [ ] Review CDN, firewall, and bot-protection settings.
- [ ] Confirm that the website's content access policy is deliberate.
- [ ] Revisit crawler rules when the website's business or privacy policy changes.

Examples of crawler names that website owners may encounter include:

- `OAI-SearchBot`
- `GPTBot`
- `Google-Extended`
- Other crawlers documented by individual providers

Do not assume that every crawler has the same purpose or that allowing one automatically allows every service from that provider.

### 18.2 Make important content technically accessible

- [ ] Important public information is available without unnecessary login barriers.
- [ ] Main page content is present in crawlable HTML or rendered output.
- [ ] Important pages have descriptive titles and headings.
- [ ] Internal links connect related information.
- [ ] Pages return correct HTTP responses.
- [ ] Content is not unintentionally blocked by bot protection.
- [ ] Public content is distinguishable from private or restricted information.

### 18.3 Understand `llms.txt` correctly

Some websites publish an `llms.txt` file to provide a structured guide to their content for AI-related tools.

However:

- It is not a universally adopted web standard.
- It is not a confirmed Google ranking requirement.
- Publishing it does not guarantee AI crawling, indexing, or citations.
- It should not replace robots.txt, XML sitemaps, accessible HTML, or normal website architecture.

If implemented, keep it accurate and useful rather than treating it as a mandatory SEO task.

### 18.4 Review technical consistency across AI discovery channels

- [ ] Important facts are consistent across public website pages.
- [ ] Organization and contact information are accurate.
- [ ] Product and service details are accessible.
- [ ] Structured data reflects visible content.
- [ ] Important resources are linked clearly.
- [ ] Outdated pages do not contradict current information.

AI visibility depends on multiple factors beyond technical crawlability. Content usefulness, accuracy, authority, source selection, and platform-specific systems also matter.

---

## 19. Technical Monitoring & Maintenance

Technical SEO is an ongoing process. A website can become technically unhealthy after a redesign, plugin update, migration, deployment, or hosting change.

### 19.1 Establish regular monitoring

- [ ] Monitor Search Console indexing reports.
- [ ] Review crawl and server errors.
- [ ] Check sitemap availability.
- [ ] Monitor important URL status codes.
- [ ] Review accidental noindex or robots.txt changes.
- [ ] Monitor canonical inconsistencies.
- [ ] Check broken internal links.
- [ ] Review redirect behavior.
- [ ] Monitor security issues.
- [ ] Re-test important page templates after major updates.

### 19.2 Create an update schedule

| Frequency | Suggested checks |
|---|---|
| After every major deployment | Test important URLs, redirects, indexing controls, and rendering |
| Weekly | Review critical Search Console errors and sitemap issues |
| Monthly | Run a technical crawl and review broken links, canonicals, and indexability |
| Quarterly | Review architecture, URL strategy, crawler policies, and technical documentation |
| During migrations | Run a full pre-migration and post-migration audit |

This is a practical starting schedule, not a universal requirement. Adjust it to website size, update frequency, and business risk.

### 19.3 Maintain a technical change log

Record:

- Date of change
- Affected URLs or templates
- Description of change
- Reason for change
- Person responsible
- Expected outcome
- Validation method
- Observed result
- Follow-up actions

This helps identify technical problems introduced by recent changes.

---

## 20. Recommended Technical SEO Tools

Use tools according to the problem being investigated. No single tool provides a complete technical audit.

| Tool | Primary use |
|---|---|
| [Google Search Console](https://search.google.com/search-console/) | Indexing, URL inspection, sitemap and search diagnostics |
| [Screaming Frog SEO Spider](https://www.screamingfrog.co.uk/seo-spider/) | Crawling, status codes, metadata, links, canonicals |
| [Sitebulb](https://sitebulb.com/) | Technical audits and visualization |
| [Bing Webmaster Tools](https://www.bing.com/webmasters/) | Bing crawling and indexing diagnostics |
| [PageSpeed Insights](https://pagespeed.web.dev/) | Performance diagnostics |
| [Chrome DevTools](https://developer.chrome.com/docs/devtools/) | Browser inspection, network requests, rendering errors |
| [Rich Results Test](https://search.google.com/test/rich-results) | Google rich result structured data testing |
| [Schema Markup Validator](https://validator.schema.org/) | Schema.org validation |
| [WebPageTest](https://www.webpagetest.org/) | Advanced loading and performance diagnostics |
| [HTTPStatus.io](https://httpstatus.io/) | HTTP response and redirect checking |
| [Redirect Path](https://redirectpath.com/) | Browser-based redirect inspection |

**Tool selection guidance:**

- Beginners can start with Search Console, browser developer tools, and a small crawl.
- Freelancers can add Screaming Frog or Sitebulb for client audits.
- Developers can use browser network tools, command-line requests, server logs, and automated tests.
- Large websites may require log analysis and crawl management workflows.

---

## 21. Technical Audit Prioritization

Not every technical issue has the same impact.

Prioritize issues based on their effect on important pages, user access, search visibility, and business outcomes.

| Priority | Examples | Recommended action |
|---|---|---|
| Critical | Important pages blocked, site-wide noindex, major server failure | Investigate immediately |
| High | Incorrect canonicals, important pages returning errors, broken redirects | Fix as soon as practical |
| Medium | Orphan pages, sitemap inconsistencies, unnecessary URL duplication | Plan and resolve |
| Low | Minor URL formatting inconsistencies, non-critical technical cleanup | Address during maintenance |

### Suggested priority scoring

Use a simple internal assessment:

- **Impact:** How much does the issue affect important pages or users?
- **Reach:** How many pages or templates are affected?
- **Confidence:** How certain are we that the issue is real?
- **Effort:** How much time or technical work is needed?

A useful planning formula is:

```text
Opportunity Score =
Impact × Reach × Confidence ÷ Effort
```

This is an internal prioritization method, not a Google ranking formula.

Do not delay a critical security or accessibility fix merely because it has a low estimated SEO score.

---

## 22. Technical SEO Audit Report Template

Use this template to document findings for a website or client.

### Website Information

| Field | Details |
|---|---|
| Website URL | |
| Audit date | |
| CMS / Framework | |
| Hosting / CDN | |
| Website type | |
| Approximate URL count | |
| Target market | |
| Auditor | |

### Findings

| Issue | Affected URLs | Priority | Evidence | Recommended fix | Status |
|---|---|---|---|---|---|
| Example: Incorrect canonical | `/page-a/` | High | Crawl report | Correct canonical target | Open |
| | | | | | |

### Technical health summary

- Crawlability:
- Indexability:
- Sitemap:
- Robots.txt:
- Canonicalization:
- Redirects:
- Internal linking:
- JavaScript rendering:
- Mobile accessibility:
- Structured data:
- Security:
- AI crawler access:

### Final recommendations

1. List critical technical blockers.
2. List high-impact fixes.
3. Identify issues requiring developer support.
4. Separate confirmed problems from observations that need further testing.
5. Define a verification method for every major fix.
6. Schedule a follow-up audit.

---

## 23. Common Technical SEO Mistakes

Avoid these common mistakes:

1. Blocking important pages through robots.txt.
2. Using `noindex` on pages that should appear in search.
3. Assuming sitemap submission guarantees indexing.
4. Redirecting every deleted URL to the homepage.
5. Pointing all canonical tags to the homepage.
6. Including redirected and non-canonical URLs in XML sitemaps.
7. Ignoring JavaScript rendering problems.
8. Depending exclusively on JavaScript click handlers for important navigation.
9. Changing URLs without a redirect and migration plan.
10. Treating every Search Console exclusion as an error.
11. Optimizing crawl budget on a small website without evidence of a crawl problem.
12. Blocking all ecommerce filter URLs without checking their value.
13. Adding irrelevant structured data to every page.
14. Treating a valid schema test as a guarantee of rich results.
15. Treating `robots.txt` as a security mechanism.
16. Assuming that allowing an AI crawler guarantees citations or visibility.
17. Making large technical changes without recording a baseline.
18. Fixing tool warnings without verifying whether they affect real users or important pages.

---

## 24. Completion Criteria

This audit can be marked complete when:

- [ ] Important public pages are accessible.
- [ ] Critical crawlability and indexability problems are identified.
- [ ] Robots.txt rules are reviewed.
- [ ] XML sitemap quality is checked.
- [ ] Important pages have an appropriate canonical strategy.
- [ ] URL variations and duplicate pages are assessed.
- [ ] HTTP status codes and redirects are reviewed.
- [ ] Important internal links are crawlable.
- [ ] JavaScript rendering is tested where relevant.
- [ ] Mobile content and navigation are accessible.
- [ ] Structured data is reviewed where applicable.
- [ ] International SEO signals are reviewed where applicable.
- [ ] Security and HTTPS configuration are checked.
- [ ] AI crawler policies are reviewed where relevant.
- [ ] Findings are supported by evidence.
- [ ] Issues are prioritized and assigned.
- [ ] Fixes have a verification plan.

**Audit principle:** Do not mark a technical issue as fixed merely because a setting was changed. Re-test the affected URL, template, or system and confirm the expected result.

---

## 25. Official Documentation & Further Reading

The following resources should be treated as primary references for Google-specific technical SEO practices.

1. [Google Search Technical Requirements](https://developers.google.com/search/docs/essentials/technical)
2. [Google Crawling and Indexing Documentation](https://developers.google.com/search/docs/crawling-indexing)
3. [How Google Search Works](https://developers.google.com/search/docs/fundamentals/how-search-works)
4. [Robots.txt Introduction](https://developers.google.com/search/docs/crawling-indexing/robots/intro)
5. [Build and Submit a Sitemap](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)
6. [Canonicalization](https://developers.google.com/search/docs/crawling-indexing/canonicalization)
7. [URL Structure Best Practices](https://developers.google.com/search/docs/crawling-indexing/url-structure)
8. [Redirects and Google Search](https://developers.google.com/search/docs/crawling-indexing/301-redirects)
9. [JavaScript SEO Basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
10. [Google Link Best Practices](https://developers.google.com/search/docs/crawling-indexing/links-crawlable)
11. [Structured Data Guidelines](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
12. [Mobile-first Indexing](https://developers.google.com/search/docs/crawling-indexing/mobile/mobile-sites-mobile-first-indexing)
13. [International and Multilingual Sites](https://developers.google.com/search/docs/specialty/international/localized-versions)
14. [Google Crawl Budget Guide](https://developers.google.com/crawling/docs/crawl-budget)

For crawler-specific AI policies, consult the relevant provider's official documentation and review it periodically because policies and crawler behavior can change.

---

## 26. Next Audit

After completing the technical foundation, move to:

**[03. Content Quality & Information Architecture](03-content-quality-and-information-architecture.md)**

This next audit will examine content usefulness, topical coverage, information architecture, originality, content structure, and how website information is organized for people and search systems.

---

**Part of the Search Visibility & Website Experience Audit Framework.**

*An evidence-based audit resource. Recommendations should be adapted to each website's architecture, audience, goals, and technical environment.*
