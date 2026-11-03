# Advanced Website & Search Visibility Audit

This document provides advanced diagnostic checks for SEO professionals, technical SEO specialists, developers, and website owners managing complex websites.

It builds on the [Complete Audit](COMPLETE-AUDIT.md) and the 12 detailed audit categories in the [`audits/`](audits/) directory.

The purpose is to investigate complex technical problems, validate implementation quality, identify hidden search visibility issues, and build more reliable optimization workflows.

This is not a checklist of mandatory technologies. Apply each investigation according to the website's architecture, business model, scale, and actual risks.

> **Important:** Advanced checks require appropriate access and technical knowledge. Obtain authorization before crawling, testing, or inspecting systems. Never treat a tool warning as proof of a ranking issue or security vulnerability without verification.

---

## 1. Advanced Crawl Analysis

### 1.1 Configure a representative crawl

- [ ] Is the crawler configured to use the preferred user agent?
- [ ] Are crawl limits appropriate for the website and server capacity?
- [ ] Are important subdomains and URL patterns included?
- [ ] Are parameterized URLs handled appropriately?
- [ ] Are JavaScript rendering requirements understood?
- [ ] Are authentication-restricted sections excluded or tested with authorized access?
- [ ] Are crawl results compared with the actual XML sitemap and internal URL inventory?

**How to investigate:**

1. Crawl the website using a suitable crawler such as Screaming Frog or Sitebulb.
2. Export discovered URLs, status codes, titles, canonicals, directives, and internal links.
3. Compare discovered URLs with sitemap URLs.
4. Identify important pages that are missing from the crawl.
5. Investigate unexpected URL patterns and crawl traps.

### 1.2 Analyze crawl depth and internal link structure

- [ ] Are important pages reachable through crawlable internal links?
- [ ] Are commercially important pages unnecessarily deep?
- [ ] Are orphan pages identified?
- [ ] Are important pages supported by relevant contextual links?
- [ ] Are navigation and pagination links implemented correctly?
- [ ] Are internal links pointing to redirected or broken URLs?
- [ ] Are low-value URL patterns consuming excessive crawl resources?

**Fix:** Improve internal linking and remove unnecessary URL generation. Do not assume that every page must be within a universal number of clicks. Evaluate crawl depth in relation to importance, discoverability, and site architecture.

### 1.3 Identify crawl traps

Investigate:

- Infinite calendar or filter combinations.
- Session IDs in URLs.
- Uncontrolled faceted navigation.
- Duplicate parameter combinations.
- Search result pages generating unlimited URLs.
- Infinite pagination or sorting variations.
- Broken redirect chains.
- Unnecessary URL case variations.

**Verification:** Confirm that important content remains discoverable after crawl restrictions or URL changes.

---

## 2. Server Log File Analysis

Server logs can reveal how search engine crawlers actually request website resources.

### 2.1 Obtain and prepare logs

- [ ] Are access logs available?
- [ ] Are the relevant date ranges included?
- [ ] Are timestamps and time zones understood?
- [ ] Are request URLs, status codes, user agents, and response times available?
- [ ] Are internal traffic and irrelevant requests filtered appropriately?
- [ ] Is personal or sensitive information protected during analysis?

### 2.2 Validate crawler identity

- [ ] Are search crawler requests identified correctly?
- [ ] Are claimed Googlebot requests verified using Google's published verification methods?
- [ ] Are other crawler identities verified where possible?
- [ ] Are spoofed user agents excluded from trusted crawler analysis?

Do not classify every request with the text `Googlebot` in its user-agent string as a genuine Google crawler.

### 2.3 Analyze crawler behavior

- [ ] Which important URLs are crawled most frequently?
- [ ] Are important pages being crawled?
- [ ] Are crawlers repeatedly requesting low-value URLs?
- [ ] Are crawlers encountering excessive redirects?
- [ ] Are 4xx and 5xx responses affecting important URLs?
- [ ] Are crawl requests concentrated on outdated URL patterns?
- [ ] Are response times unusually high for crawler requests?

### 2.4 Build a crawl analysis report

Useful dimensions include:

| Dimension | Investigation |
|---|---|
| URL path | Which sections receive crawler requests? |
| Status code | Are errors or redirects common? |
| User agent | Which verified crawlers are visiting? |
| Date and time | Are crawl patterns changing? |
| Response time | Are requests unusually slow? |
| Content type | Are unnecessary resources being requested? |

**Fix:** Prioritize patterns affecting important content. Log-file activity is evidence of requests, not proof of indexing or ranking.

---

## 3. JavaScript Rendering & Technical SEO

### 3.1 Inspect initial HTML and rendered HTML

- [ ] Is important content present in the initial HTML?
- [ ] Is critical content available after JavaScript rendering?
- [ ] Are internal links rendered as crawlable links?
- [ ] Are titles, descriptions, canonical tags, and robots directives correct after rendering?
- [ ] Are important structured data elements present in the rendered page?
- [ ] Are errors preventing content from loading?
- [ ] Are important pages dependent on user interactions that crawlers may not perform?

### 3.2 Investigate rendering failures

Check for:

- Client-side content that never renders.
- JavaScript exceptions.
- Blocked CSS or JavaScript resources.
- API failures.
- Authentication-dependent content.
- Hydration errors.
- Incorrect canonical tags after rendering.
- Content that appears only after scrolling or interaction.
- Different content served to crawlers and users without a legitimate reason.

### 3.3 Test important templates

Test representative examples of:

- Homepage.
- Category pages.
- Product pages.
- Service pages.
- Blog articles.
- Search or filter pages.
- Location pages.
- Pagination pages.

**How to verify:**

Use browser developer tools, URL Inspection in Google Search Console, and suitable rendering crawlers.

Compare:

1. Raw server response.
2. Browser-rendered DOM.
3. Search engine rendered output where available.

**Fix:** Prefer reliable server-side rendering or static rendering for important content when client-side rendering creates discoverability or performance problems. The correct approach depends on the framework and application architecture.

---

## 4. Advanced Indexation & Canonicalization

### 4.1 Indexation consistency

- [ ] Are indexable pages returning successful HTTP responses?
- [ ] Are non-indexable pages excluded for an intentional reason?
- [ ] Are canonical tags consistent with internal links?
- [ ] Are sitemap URLs indexable and canonical?
- [ ] Are important pages unintentionally marked `noindex`?
- [ ] Are canonicalized URLs handled consistently?
- [ ] Are redirect destinations appropriate?
- [ ] Are conflicting indexing signals investigated?

### 4.2 Advanced canonical issues

Investigate:

- Canonical chains.
- Canonical loops.
- Canonicals pointing to redirected URLs.
- Canonicals pointing to irrelevant pages.
- Canonical conflicts between HTML and HTTP headers.
- Incorrect canonicals on paginated or filtered pages.
- Inconsistent trailing slash or URL case handling.
- Canonical tags generated incorrectly by JavaScript.

**Important:** Canonical tags are signals, not absolute indexing commands. Search engines may select a different canonical URL.

### 4.3 Large-site indexation analysis

- [ ] Are indexed and submitted URL patterns compared?
- [ ] Are important templates disproportionately excluded?
- [ ] Are duplicate or near-duplicate URL patterns identified?
- [ ] Are low-value pages generated at scale?
- [ ] Are discontinued products or obsolete content handled appropriately?
- [ ] Are crawl and indexation issues segmented by page template?

Do not attempt to force every discovered URL into the search index. Focus on pages that deserve search visibility.

---

## 5. Advanced Structured Data & Entity Validation

### 5.1 Structured data implementation

- [ ] Does structured data accurately describe visible page content?
- [ ] Are required properties present for the selected schema type?
- [ ] Are recommended properties added only when accurate?
- [ ] Are entity relationships represented consistently?
- [ ] Are structured data types appropriate for the actual page?
- [ ] Are duplicate or conflicting markup blocks investigated?
- [ ] Is JSON-LD valid and accessible?
- [ ] Are structured data updates tested after template changes?

### 5.2 Validate structured data

Use:

- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)

Check both syntax and eligibility.

A valid schema implementation does not guarantee a rich result. Search engines determine feature eligibility and display.

### 5.3 Entity consistency

- [ ] Is the organization or business identity consistent?
- [ ] Are important people, products, and services represented accurately?
- [ ] Are entity references and identifiers used consistently where appropriate?
- [ ] Are sameAs references genuine and relevant?
- [ ] Are author and publisher details consistent?
- [ ] Are organization details consistent across website templates?

**Fix:** Treat structured data as a representation of real page information, not a way to insert unsupported claims.

---

## 6. International SEO & Multilingual Diagnostics

### 6.1 Hreflang validation

- [ ] Are language and regional codes valid?
- [ ] Are alternate URLs accessible?
- [ ] Are return links present where required?
- [ ] Is self-referencing hreflang included?
- [ ] Are canonical and hreflang signals compatible?
- [ ] Are language versions genuinely equivalent?
- [ ] Is the default or `x-default` version used appropriately?

### 6.2 Regional targeting

- [ ] Are country-specific pages useful and distinct?
- [ ] Are currency, shipping, pricing, and contact details appropriate?
- [ ] Are regional URLs consistent?
- [ ] Are users able to switch language or region?
- [ ] Are redirects based on language or location handled carefully?
- [ ] Can search crawlers access alternate versions?

### 6.3 Multilingual content quality

- [ ] Is content translated accurately?
- [ ] Are local search terms researched independently?
- [ ] Are cultural and legal differences considered?
- [ ] Are translated titles and descriptions natural?
- [ ] Are language-specific navigation and internal links correct?

**Fix:** Do not create thin regional pages solely by replacing country names. Each version should provide genuine value to its intended audience.

---

## 7. Advanced Core Web Vitals Diagnostics

### 7.1 Field and laboratory data

- [ ] Are field and lab measurements distinguished?
- [ ] Is the 75th percentile considered when evaluating Core Web Vitals?
- [ ] Are mobile and desktop results analyzed separately?
- [ ] Are representative page templates evaluated?
- [ ] Are real-user performance trends monitored?
- [ ] Are changes tested under realistic network and device conditions?

### 7.2 Diagnose LCP

Largest Contentful Paint measures when the largest visible content element is rendered.

Investigate:

- Slow server response.
- Delayed resource discovery.
- Render-blocking CSS and JavaScript.
- Large hero images.
- Inefficient image delivery.
- Client-side rendering delays.
- Unnecessary resource prioritization.

Target: LCP at or below 2.5 seconds at the 75th percentile.

### 7.3 Diagnose INP

Interaction to Next Paint measures responsiveness to user interactions.

Investigate:

- Long JavaScript tasks.
- Expensive event handlers.
- Excessive DOM updates.
- Main-thread blocking.
- Heavy third-party scripts.
- Unnecessary client-side work.

Target: INP at or below 200 milliseconds at the 75th percentile.

### 7.4 Diagnose CLS

Cumulative Layout Shift measures unexpected visual movement.

Investigate:

- Images without dimensions or reserved space.
- Dynamically injected content.
- Late-loading advertisements.
- Font swaps.
- Layout changes caused by scripts.
- Unstable banners and embeds.

Target: CLS at or below 0.1 at the 75th percentile.

**Important:** These are Google's current good thresholds, not guarantees of rankings or conversions.

### 7.5 Performance investigation tools

- [PageSpeed Insights](https://pagespeed.web.dev/)
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)
- [Chrome UX Report](https://developer.chrome.com/docs/crux/)
- [web.dev Learn Performance](https://web.dev/learn/performance/)

---

## 8. Advanced URL Architecture & Faceted Navigation

### 8.1 URL pattern analysis

- [ ] Are URL patterns documented?
- [ ] Are unnecessary parameters identified?
- [ ] Are case and trailing slash variations normalized?
- [ ] Are session identifiers excluded from indexable URLs?
- [ ] Are pagination URLs handled consistently?
- [ ] Are internal search URLs controlled?
- [ ] Are duplicate URL combinations identified?

### 8.2 Ecommerce facets and filters

- [ ] Are crawlable filter combinations limited to useful pages?
- [ ] Are indexable category and subcategory pages defined intentionally?
- [ ] Are canonical, robots, and internal linking strategies consistent?
- [ ] Are filter combinations creating duplicate content?
- [ ] Are sorting and tracking parameters handled appropriately?
- [ ] Are important filtered landing pages supported by unique value?

**Fix:** Decide which filtered URLs deserve search visibility. Avoid allowing unlimited combinations to generate crawlable, low-value pages.

---

## 9. Advanced Internal Linking & Information Architecture

- [ ] Are important pages supported by contextual internal links?
- [ ] Are orphan URLs identified using crawl and analytics data?
- [ ] Are internal links relevant to the destination?
- [ ] Are anchor texts descriptive without being artificially repetitive?
- [ ] Are important pages linked from authoritative sections of the website?
- [ ] Are breadcrumb structures consistent?
- [ ] Are links to redirected and broken URLs removed?
- [ ] Are large-site navigation structures scalable?

### Advanced analysis

Compare internal link counts with:

- Organic landing-page traffic.
- Business importance.
- Crawl depth.
- Conversion contribution.
- Content relevance.

Do not assume that increasing the number of internal links automatically improves rankings. Improve navigation and discoverability first.

---

## 10. Advanced AI Search & Answer Engine Testing

AI search visibility is evolving. Different systems retrieve, select, summarize, and cite information differently.

No checklist can guarantee inclusion in AI-generated answers.

### 10.1 Crawler access

- [ ] Are relevant search crawlers identified?
- [ ] Are robots.txt rules reviewed?
- [ ] Are CDN and firewall restrictions reviewed?
- [ ] Are crawler-specific access policies documented?
- [ ] Are crawler requests monitored where logs are available?
- [ ] Are user-triggered retrieval crawlers distinguished from training crawlers?

Review official documentation for crawler identities and their purposes. Do not assume that allowing one crawler automatically allows every AI-related service.

### 10.2 Content retrieval and answer quality

- [ ] Are important facts stated clearly?
- [ ] Are claims supported by trustworthy sources?
- [ ] Are definitions and explanations unambiguous?
- [ ] Are important pages structured around meaningful user questions?
- [ ] Are original research and first-hand experience clearly presented?
- [ ] Are dates and changing facts maintained?
- [ ] Are authorship and business identity transparent?

### 10.3 Test AI search discoverability

- [ ] Are representative questions documented?
- [ ] Are brand and non-brand questions tested?
- [ ] Are answers checked for factual accuracy?
- [ ] Are citations and source URLs recorded?
- [ ] Are incorrect brand associations documented?
- [ ] Are results compared across platforms and dates?
- [ ] Are tests repeatable?

Example test categories:

- Brand identity.
- Product or service comparisons.
- Expert explanations.
- Industry questions.
- Local business discovery.
- Frequently asked customer questions.

### 10.4 Evaluate AI visibility carefully

Record:

- Platform and test date.
- Exact query.
- Whether the brand appeared.
- Whether a source citation appeared.
- Cited page URL.
- Accuracy of the generated answer.
- Competitor mentions.
- Follow-up action.

AI answer outputs vary by user, location, context, model, and time. Manual observations are not a universal visibility measurement.

---

## 11. Automation & Technical Monitoring

### 11.1 Automated SEO checks

Where useful, automate checks for:

- Broken URLs.
- Unexpected status-code changes.
- Missing titles or descriptions.
- Canonical changes.
- Noindex changes.
- Sitemap errors.
- Missing structured data.
- Important page availability.
- Core Web Vitals regressions.
- Unexpected robots.txt changes.

### 11.2 Deployment validation

- [ ] Are critical SEO checks included in release workflows?
- [ ] Are important URL patterns tested?
- [ ] Are metadata and canonical rules validated?
- [ ] Are structured data templates tested?
- [ ] Are robots and sitemap files checked?
- [ ] Are critical user journeys tested?
- [ ] Is rollback possible if a release causes serious issues?

### 11.3 Alert quality

- [ ] Are alerts based on meaningful thresholds?
- [ ] Are false positives reduced?
- [ ] Are alert owners assigned?
- [ ] Are critical failures escalated?
- [ ] Are alerts reviewed after major changes?

**Fix:** Automate repeatable checks, but retain human review for context-dependent decisions such as content quality, search intent, and business impact.

---

## 12. Advanced Ecommerce & Large-Scale Website Checks

### Ecommerce

- [ ] Are product variants represented consistently?
- [ ] Are discontinued products handled appropriately?
- [ ] Are out-of-stock products handled according to business policy?
- [ ] Are product structured data and merchant feeds consistent?
- [ ] Are price and availability values accurate?
- [ ] Are faceted navigation patterns controlled?
- [ ] Are category and product templates unique and useful?
- [ ] Are checkout and payment failures monitored?

### Large websites and publishers

- [ ] Are page templates reviewed at scale?
- [ ] Are duplicate and thin page patterns identified?
- [ ] Are crawl budgets evaluated using actual evidence?
- [ ] Are internal linking patterns scalable?
- [ ] Are content updates and removals governed?
- [ ] Are important page groups monitored independently?
- [ ] Are automated publishing workflows validated?

### SaaS and web applications

- [ ] Are public marketing pages separated from private application areas?
- [ ] Are account-specific pages protected?
- [ ] Are public documentation pages crawlable?
- [ ] Are dynamically generated routes tested?
- [ ] Are authentication and indexing boundaries correct?
- [ ] Are API-generated content dependencies reliable?

---

## 13. Advanced Audit Prioritization

Advanced audits can uncover many issues. Not every issue deserves immediate implementation.

Evaluate each finding using:

| Factor | Question |
|---|---|
| Search impact | Could this affect crawling, indexing, or visibility? |
| Business impact | Could it affect leads, sales, or customer experience? |
| Scope | How many important pages or users are affected? |
| Severity | How serious is the problem? |
| Confidence | Is there sufficient evidence? |
| Effort | How difficult is the fix? |
| Risk | Could the proposed fix create other problems? |

### Suggested priority levels

- **Critical:** Security compromise, major outage, or severe issue affecting essential website functionality.
- **High:** Significant problem affecting important pages, indexing, conversions, or site reliability.
- **Medium:** Meaningful technical or experience improvement with limited immediate impact.
- **Low:** Minor refinement or optimization opportunity.

Document evidence and dependencies before assigning a priority.

---

## 14. Advanced Audit Finding Template

Use this structure for each investigation.

### Finding ID: ADV-001

**Audit category:**  
Technical SEO / Rendering / Security / Performance / AI Search

**Affected URL or template:**  
List exact URLs or representative examples.

**Observed behavior:**  
Describe what happened.

**Expected behavior:**  
Explain what should happen.

**Evidence:**  
Logs, crawl exports, screenshots, HTTP responses, test results, or analytics.

**Impact:**  
Explain the potential effect on search visibility, user experience, business outcomes, or security.

**Root cause:**  
Document the confirmed cause. If uncertain, state the hypothesis.

**Priority:**  
Critical / High / Medium / Low.

**Recommended fix:**  
Provide a practical implementation recommendation.

**Verification method:**  
Explain how the result will be tested.

**Owner and status:**  
Assign responsibility and track progress.

---

## 15. Advanced Audit Completion Criteria

An advanced audit can be considered complete when:

- [ ] Representative crawl analysis has been performed.
- [ ] Important crawl and URL patterns are understood.
- [ ] Server logs have been reviewed where available and justified.
- [ ] JavaScript rendering has been validated for important templates.
- [ ] Canonical and indexation signals have been checked.
- [ ] Structured data has been validated.
- [ ] International SEO signals have been checked where relevant.
- [ ] Core Web Vitals diagnostics have been completed for representative pages.
- [ ] AI search access and visibility have been evaluated appropriately.
- [ ] Automation and monitoring opportunities have been documented.
- [ ] Findings include evidence, impact, and verification steps.
- [ ] High-risk issues have clear owners and remediation plans.

---

## 16. Official Documentation & Advanced Resources

### Search engines and crawling

- [Google Search Central](https://developers.google.com/search)
- [Google Search Crawling and Indexing](https://developers.google.com/search/docs/crawling-indexing)
- [Google JavaScript SEO Basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [Bing Webmaster Guidelines](https://www.bing.com/webmasters/help/webmaster-guidelines-30fba23a)

### Structured data

- [Google Structured Data Documentation](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
- [Schema.org](https://schema.org/)

### Performance

- [web.dev](https://web.dev/)
- [PageSpeed Insights](https://pagespeed.web.dev/)
- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)

### Security

- [OWASP](https://owasp.org/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

### AI search

- [OpenAI Crawlers and User Agents](https://platform.openai.com/docs/bots)
- [OpenAI Publisher FAQ](https://help.openai.com/en/articles/12627856-publishers-and-developers-faq)
- [Google AI Features and Your Website](https://developers.google.com/search/docs/appearance/ai-features)

---

**Final principle:** Advanced SEO is not about using the most tools or implementing the most complicated technology. It is about identifying real problems, collecting reliable evidence, understanding their impact, and validating solutions.
