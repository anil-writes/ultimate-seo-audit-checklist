# Website Performance & Core Web Vitals Audit

Website performance affects how quickly visitors can access content, interact with pages, and complete important tasks.

A website may look visually polished but still provide a frustrating experience if its pages load slowly, respond late, shift unexpectedly, or consume excessive device resources.

This audit evaluates website performance from both technical and user-experience perspectives.

It covers Core Web Vitals, loading performance, responsiveness, visual stability, images, JavaScript, CSS, caching, hosting, third-party scripts, and ongoing monitoring.

> **Important:** Performance results vary by device, network, browser, location, and page complexity. Do not rely on a single Lighthouse score or one laboratory test to represent the complete user experience.

Not every recommendation applies to every website. Evaluate improvements according to actual performance evidence and business requirements.

---

## 1. Performance Fundamentals & Baseline Assessment

### Audit objective

Establish a reliable performance baseline before making optimization changes.

### Checks

- [ ] Identify important page templates that require testing.
- [ ] Test the homepage and important landing pages.
- [ ] Test representative blog, service, category, and product pages where applicable.
- [ ] Evaluate desktop and mobile performance separately.
- [ ] Record laboratory and field performance data where available.
- [ ] Test pages using more than one network condition when practical.
- [ ] Identify pages with unusually large resources or complex interactions.
- [ ] Record current performance problems and their possible causes.
- [ ] Compare similar page templates to identify recurring issues.
- [ ] Establish a baseline before implementing major changes.

### How to audit

Start with these tools:

- Google PageSpeed Insights
- Lighthouse
- Chrome DevTools
- WebPageTest
- Chrome UX Report, where eligible data is available

For each important URL, record:

| Information | What to capture |
|---|---|
| URL | Page being tested |
| Device | Mobile or desktop |
| Test date | Date of measurement |
| LCP | Largest Contentful Paint |
| INP | Interaction to Next Paint |
| CLS | Cumulative Layout Shift |
| TTFB | Time to First Byte |
| Performance score | Laboratory diagnostic score |
| Main issues | Important findings |
| Evidence | Report or screenshot |

### Recommended approach

Do not optimize the entire website based on one homepage test.

Identify representative page templates and investigate recurring problems across the website.

---

## 2. Core Web Vitals Assessment

### Audit objective

Evaluate the three Core Web Vitals used by Google to assess real-world loading performance, interactivity, and visual stability.

Core Web Vitals are evaluated using field data at the 75th percentile of page visits, with mobile and desktop considered separately.

### Current Core Web Vitals thresholds

| Metric | Good | Needs Improvement | Poor |
|---|---:|---:|---:|
| LCP | ≤ 2.5 seconds | 2.5–4 seconds | > 4 seconds |
| INP | ≤ 200 milliseconds | 200–500 milliseconds | > 500 milliseconds |
| CLS | ≤ 0.1 | 0.1–0.25 | > 0.25 |

These thresholds apply to the respective metrics and should be evaluated using the appropriate field-data methodology.

### 2.1 Largest Contentful Paint (LCP)

**What it measures**

LCP measures how quickly the largest visible content element is rendered within the viewport.

This may be a large image, text block, video poster, or other qualifying element.

**Checks**

- [ ] Identify the LCP element on important pages.
- [ ] Check whether the main content image loads efficiently.
- [ ] Ensure important above-the-fold content is not delayed unnecessarily.
- [ ] Review server response time.
- [ ] Check image dimensions and file size.
- [ ] Avoid lazy-loading the primary LCP image when it should load immediately.
- [ ] Use appropriate image prioritization.
- [ ] Review render-blocking CSS and JavaScript.
- [ ] Identify slow fonts or external resources delaying rendering.

**How to audit**

Use PageSpeed Insights or Chrome DevTools to identify the LCP element and investigate its loading timeline.

LCP problems commonly involve:

- Slow server response.
- Large or inefficient images.
- Render-blocking resources.
- Client-side rendering delays.
- Poor resource prioritization.

**Recommended fixes**

Optimize the actual LCP element, improve server response where necessary, reduce rendering delays, and prioritize critical resources appropriately.

### 2.2 Interaction to Next Paint (INP)

**What it measures**

INP evaluates responsiveness by observing the latency of interactions throughout a page visit.

It considers interactions such as clicking, tapping, and keyboard input.

**Checks**

- [ ] Test important buttons and interactive controls.
- [ ] Review menus, tabs, accordions, and search interfaces.
- [ ] Identify long-running JavaScript tasks.
- [ ] Check whether event handlers perform excessive work.
- [ ] Review third-party scripts that may interfere with interactions.
- [ ] Check whether the main thread becomes blocked.
- [ ] Test interactions on lower-powered mobile devices where possible.
- [ ] Review delayed visual feedback after user actions.

**How to audit**

Use Chrome DevTools Performance panel and available field diagnostics to identify slow interactions.

Common causes include:

- Excessive JavaScript execution.
- Large event handlers.
- Heavy rendering and layout calculations.
- Long tasks on the main thread.
- Unnecessary third-party scripts.

**Recommended fixes**

Break up long tasks, reduce unnecessary JavaScript, defer non-essential work, and provide prompt visual feedback after user interactions.

### 2.3 Cumulative Layout Shift (CLS)

**What it measures**

CLS measures unexpected visual layout shifts during a page's lifecycle.

Unexpected movement can cause visitors to click the wrong button, lose their reading position, or become frustrated.

**Checks**

- [ ] Images have appropriate width and height attributes or reserved aspect ratios.
- [ ] Video and embedded content have reserved space.
- [ ] Advertisements do not unexpectedly push existing content.
- [ ] Fonts do not cause significant unexpected layout changes.
- [ ] Dynamic content does not insert itself above existing content without preparation.
- [ ] Cookie banners and notifications do not cause disruptive shifts.
- [ ] Lazy-loaded elements reserve sufficient space.
- [ ] Animations avoid properties that trigger unexpected layout changes.

**How to audit**

Use Lighthouse, PageSpeed Insights, and Chrome DevTools layout-shift diagnostics.

Common causes include:

- Images without reserved dimensions.
- Dynamically inserted content.
- Unreserved advertisement space.
- Late-loading fonts.
- Components that change size after rendering.

**Recommended fixes**

Reserve space for media and dynamic elements, use stable layouts, and avoid inserting unexpected content into the visible page.

---

## 3. Server Response & Time to First Byte (TTFB)

### Audit objective

Identify server-side delays that affect the beginning of the page-loading process.

TTFB measures the time between a request being sent and the first byte of the response being received.

It is not itself a Core Web Vital, but it can help diagnose loading performance problems.

### Checks

- [ ] Measure TTFB for important pages.
- [ ] Compare response times across page templates.
- [ ] Check whether dynamic pages respond significantly slower than cached pages.
- [ ] Review server-side processing time.
- [ ] Check database query performance where relevant.
- [ ] Evaluate CDN configuration.
- [ ] Review caching and cache-hit behaviour.
- [ ] Check whether redirects add unnecessary requests.
- [ ] Investigate geographic differences in response time.
- [ ] Review server errors and intermittent response delays.

### How to audit

Use PageSpeed Insights, Chrome DevTools, WebPageTest, and server monitoring tools.

Google's recommended TTFB target for a good user experience is 0.8 seconds or less at the 75th percentile.

This is a diagnostic recommendation, not a universal hosting requirement or a guaranteed ranking threshold.

### Recommended fixes

Depending on the cause:

- Improve application processing.
- Optimize database queries.
- Configure appropriate caching.
- Use a suitable CDN.
- Reduce unnecessary redirects.
- Review hosting resource constraints.
- Investigate slow external dependencies.

Do not upgrade hosting simply because one test reports a high TTFB. Identify the underlying cause first.

---

## 4. Image Optimization & Media Delivery

### Audit objective

Reduce unnecessary image and media payloads without damaging visual quality.

Images often represent a substantial portion of a webpage's transferred data.

### Checks

- [ ] Use appropriately sized images.
- [ ] Avoid serving unnecessarily large images to small screens.
- [ ] Use modern formats such as WebP or AVIF where supported.
- [ ] Compress images while maintaining acceptable visual quality.
- [ ] Use responsive image techniques such as `srcset` and `sizes` where appropriate.
- [ ] Provide explicit image dimensions or aspect ratios.
- [ ] Lazy-load below-the-fold images.
- [ ] Avoid lazy-loading the primary LCP image when it needs high priority.
- [ ] Use descriptive filenames where useful.
- [ ] Review image delivery through a CDN where beneficial.
- [ ] Optimize thumbnails and repeated image assets.
- [ ] Avoid unnecessary autoplay video.
- [ ] Use efficient video formats and delivery methods.

### How to audit

Inspect image requests through Chrome DevTools Network panel.

Look for:

- Large image files.
- Incorrect image dimensions.
- Uncompressed media.
- Duplicate image downloads.
- Unnecessary background images.
- Images that are loaded but never displayed.

### Recommended fixes

Choose image dimensions based on actual display requirements.

For example, a small thumbnail should not require downloading a multi-megabyte original image.

Use responsive delivery and lazy loading where appropriate.

---

## 5. CSS Optimization & Rendering Efficiency

### Audit objective

Reduce unnecessary CSS processing and identify stylesheets that delay rendering or create excessive layout work.

### Checks

- [ ] Identify large CSS files.
- [ ] Remove unused styles where safe.
- [ ] Minimize unnecessary CSS duplication.
- [ ] Review render-blocking stylesheets.
- [ ] Avoid loading page-specific styles across unrelated pages when unnecessary.
- [ ] Use critical CSS techniques where appropriate.
- [ ] Avoid excessive CSS imports.
- [ ] Review complex selectors and expensive layout patterns.
- [ ] Reduce unnecessary animations and transitions.
- [ ] Check whether layout changes cause repeated recalculation.

### How to audit

Use Chrome DevTools Coverage and Performance panels.

Inspect:

- Unused CSS.
- Render-blocking requests.
- Repeated stylesheet downloads.
- Large CSS payloads.
- Layout and rendering activity.

### Recommended fixes

Remove genuinely unused CSS, split styles where beneficial, optimize critical rendering paths, and avoid unnecessary visual effects.

Do not remove CSS simply because it appears unused during one page load. It may be required by interactions, other page states, or responsive layouts.

---

## 6. JavaScript Optimization & Main Thread Performance

### Audit objective

Reduce unnecessary JavaScript execution and improve responsiveness.

### Checks

- [ ] Identify large JavaScript bundles.
- [ ] Remove unused dependencies where practical.
- [ ] Avoid loading unnecessary scripts on every page.
- [ ] Use code splitting where beneficial.
- [ ] Defer non-critical scripts where appropriate.
- [ ] Use asynchronous loading where suitable.
- [ ] Review long tasks.
- [ ] Reduce excessive DOM manipulation.
- [ ] Avoid unnecessary event listeners.
- [ ] Check for memory-intensive components.
- [ ] Review client-side rendering costs.
- [ ] Avoid unnecessary hydration work in applications that use server rendering.
- [ ] Check whether third-party scripts delay important interactions.

### How to audit

Use:

- Chrome DevTools Performance.
- Chrome DevTools Coverage.
- Lighthouse diagnostics.
- JavaScript bundle analyzers appropriate to the framework.

### Recommended fixes

Prioritize reducing work on the main thread, loading only necessary code, and simplifying expensive interactions.

Do not blindly defer every script. Some scripts are essential for navigation, security, analytics, or core functionality.

---

## 7. Font Optimization & Text Rendering

### Audit objective

Improve font delivery and prevent typography from delaying content rendering or causing layout shifts.

### Checks

- [ ] Remove unused font families and weights.
- [ ] Avoid loading unnecessary font variants.
- [ ] Prefer efficient font formats such as WOFF2.
- [ ] Review font loading behaviour.
- [ ] Use appropriate font-display settings.
- [ ] Check whether custom fonts delay visible text.
- [ ] Preload only critical fonts when justified.
- [ ] Use suitable fallback fonts.
- [ ] Ensure font changes do not cause disruptive layout shifts.
- [ ] Review external font requests and their dependencies.

### How to audit

Inspect font requests using Chrome DevTools Network and Performance panels.

Check whether text remains readable while custom fonts are loading.

### Recommended fixes

Reduce unnecessary font files, use efficient formats, choose suitable fallback fonts, and preload only genuinely critical resources.

Avoid preloading every font file because unnecessary preloads can compete with more important resources.

---

## 8. Browser Caching & Resource Reuse

### Audit objective

Ensure repeat visitors can reuse suitable resources without downloading everything again.

### Checks

- [ ] Static assets have appropriate cache-control headers.
- [ ] Cache policies are suitable for images, CSS, and JavaScript.
- [ ] Versioned assets can be cached efficiently.
- [ ] Frequently changing content is not cached beyond its intended lifetime.
- [ ] Browser caching behaves correctly after deployment.
- [ ] CDN caching is configured appropriately where used.
- [ ] Cache invalidation works after updates.
- [ ] Compression is enabled where supported.

### How to audit

Inspect response headers through Chrome DevTools Network panel.

Review:

- `Cache-Control`
- `ETag`
- `Last-Modified`
- `Content-Encoding`

### Recommended fixes

Use suitable cache lifetimes for static and dynamic resources.

Version filenames or asset URLs when necessary to ensure updated resources are delivered after deployment.

Avoid applying aggressive caching to sensitive or frequently changing content.

---

## 9. Content Delivery Network (CDN) & Hosting Performance

### Audit objective

Determine whether the website's infrastructure delivers resources efficiently to its intended audience.

### Checks

- [ ] Evaluate whether a CDN would benefit the website.
- [ ] Check whether CDN resources are delivered from suitable locations.
- [ ] Review cache-hit ratios where available.
- [ ] Check whether static assets are unnecessarily served from the origin server.
- [ ] Evaluate server capacity under normal traffic.
- [ ] Review hosting resource usage.
- [ ] Check database and application response times.
- [ ] Investigate server errors and downtime.
- [ ] Review TLS configuration and connection behaviour.
- [ ] Confirm that CDN or caching rules do not break dynamic functionality.

### How to audit

Use available hosting dashboards, CDN analytics, server monitoring, and performance tests from representative locations.

### Recommended fixes

Choose infrastructure based on actual requirements, traffic distribution, application architecture, reliability, and budget.

A CDN is not automatically necessary for every small website, and a more expensive hosting plan does not automatically solve inefficient application code.

---

## 10. Third-Party Scripts & External Dependencies

### Audit objective

Identify external resources that increase loading time, reduce responsiveness, or introduce reliability problems.

### Checks

- [ ] Review analytics scripts.
- [ ] Review advertising scripts.
- [ ] Review chat widgets.
- [ ] Review social media embeds.
- [ ] Review tracking pixels.
- [ ] Review external fonts and libraries.
- [ ] Identify scripts that load on every page unnecessarily.
- [ ] Check whether third-party services block rendering.
- [ ] Review the impact of external scripts on INP.
- [ ] Confirm that important features continue working if a third-party service is unavailable.
- [ ] Remove unused integrations.

### How to audit

Use Chrome DevTools Network panel to group requests by domain and identify the resources consuming the most time and bandwidth.

Compare performance with and without non-essential scripts in a controlled test environment.

### Recommended fixes

Remove unnecessary integrations, load optional services only when needed, use efficient loading strategies, and reduce dependence on external resources.

Do not remove essential functionality or privacy-related controls merely to improve a performance score.

---

## 11. Mobile Performance & Device Constraints

### Audit objective

Ensure that performance remains acceptable on real mobile devices and constrained networks.

### Checks

- [ ] Test important pages on mobile devices.
- [ ] Review mobile Core Web Vitals separately from desktop.
- [ ] Check performance on slower network connections.
- [ ] Evaluate JavaScript execution on lower-powered devices.
- [ ] Avoid unnecessarily large mobile downloads.
- [ ] Optimize images for mobile display.
- [ ] Review mobile-specific scripts and components.
- [ ] Check whether animations create performance problems.
- [ ] Ensure interactive elements respond without excessive delay.
- [ ] Test important journeys on real devices where possible.

### How to audit

Use real devices when available, alongside Chrome DevTools network and CPU throttling.

Remember that simulated device testing does not perfectly reproduce every real-world mobile environment.

### Recommended fixes

Reduce unnecessary resource downloads, optimize images, simplify expensive interactions, and avoid heavy client-side processing.

---

## 12. Page Weight, Network Requests & Resource Prioritization

### Audit objective

Understand how much data a page downloads and whether important resources are requested in the correct order.

### Checks

- [ ] Review total transferred page size.
- [ ] Count network requests.
- [ ] Identify unusually large resources.
- [ ] Check duplicate requests.
- [ ] Review unnecessary redirects.
- [ ] Identify resources loaded but not used.
- [ ] Prioritize critical visual resources appropriately.
- [ ] Avoid excessive preloading.
- [ ] Review font, image, script, and stylesheet request order.
- [ ] Check whether important content waits for non-essential resources.

### How to audit

Use the Network panel in Chrome DevTools.

Review:

- Total requests.
- Transferred size.
- Resource types.
- Request duration.
- Initiator.
- Priority.
- Failed requests.

### Recommended fixes

Remove unnecessary requests, reduce payload sizes, prioritize critical resources, and avoid downloading assets that are not needed for the current page.

There is no universal ideal request count or page-weight limit for every website. Evaluate the actual impact on users.

---

## 13. Performance Monitoring & Regression Prevention

### Audit objective

Maintain performance after improvements and detect problems introduced by future updates.

### Checks

- [ ] Monitor Core Web Vitals using available field data.
- [ ] Review Google Search Console Core Web Vitals reports.
- [ ] Track important page templates over time.
- [ ] Repeat laboratory tests after major changes.
- [ ] Monitor server response and availability.
- [ ] Review performance after theme or plugin updates.
- [ ] Test performance after adding third-party integrations.
- [ ] Establish performance budgets where practical.
- [ ] Monitor unexpected increases in page weight.
- [ ] Document optimization changes and their measured impact.

### Recommended tools

- Google Search Console
- PageSpeed Insights
- Lighthouse CI
- Chrome User Experience Report
- WebPageTest
- Chrome DevTools
- Hosting and CDN monitoring tools

### Recommended approach

Use field data to understand real user experience and laboratory tests to diagnose specific problems.

Do not treat one Lighthouse score as a complete performance report.

---

## 14. Performance Issue Prioritization & Reporting

### Audit objective

Convert performance measurements into practical development tasks.

### Suggested priority levels

| Priority | Meaning | Example |
|---|---|---|
| Critical | Major failure affecting essential page functionality | Important pages fail to load |
| High | Significant performance problem affecting important journeys | Poor LCP on primary landing pages |
| Medium | Noticeable inefficiency with measurable impact | Oversized images on multiple templates |
| Low | Minor optimization opportunity | Unnecessary small resource requests |

Priority should reflect actual impact, affected users, business importance, and implementation effort.

### Performance audit report template

| Field | Description |
|---|---|
| Issue ID | Unique reference |
| URL or template | Affected page |
| Device | Mobile or desktop |
| Metric or resource | LCP, INP, CLS, TTFB, image, script, etc. |
| Current result | Measured value or observation |
| Target or reference | Relevant threshold or intended behaviour |
| Evidence | Test report or screenshot |
| Root cause | Identified technical cause |
| User impact | Effect on loading, interaction, or stability |
| Recommended fix | Proposed change |
| Priority | Critical, High, Medium, or Low |
| Verification | How the improvement will be confirmed |
| Status | Open, In Progress, or Resolved |

### Example finding

**Issue:** Main banner image is delaying LCP.

**Location:** Homepage.

**Device:** Mobile.

**Evidence:** PageSpeed Insights identifies the large hero image as the LCP element.

**User impact:** The primary visual content appears later than expected.

**Possible root cause:** Image is oversized and not prioritized appropriately.

**Recommended fix:** Serve an appropriately sized modern image format and review loading priority.

**Verification:** Repeat field and laboratory assessments after deployment.

---

## 15. Common Performance Optimization Mistakes

Avoid these common mistakes:

- Treating a Lighthouse score of 100 as the only goal.
- Optimizing a single URL while ignoring other important templates.
- Lazy-loading the primary LCP image.
- Preloading every image, font, or script.
- Removing essential JavaScript to improve a score.
- Using aggressive caching without considering content updates.
- Installing multiple optimization plugins without understanding their overlap.
- Compressing images so heavily that quality becomes unacceptable.
- Upgrading hosting without identifying the actual bottleneck.
- Treating TTFB as a Core Web Vital.
- Assuming desktop performance represents mobile performance.
- Treating laboratory results as equivalent to real-user field data.
- Making performance changes without retesting functionality.
- Claiming ranking improvements solely because a performance score increased.

---

## 16. Performance Audit Completion Checklist

A performance audit can be considered complete when:

- [ ] Important page templates have been tested.
- [ ] Mobile and desktop results have been evaluated.
- [ ] Core Web Vitals have been reviewed.
- [ ] LCP elements and their loading behaviour have been inspected.
- [ ] INP-related interaction problems have been investigated.
- [ ] CLS-related layout shifts have been checked.
- [ ] Server response and TTFB have been evaluated.
- [ ] Images and media have been reviewed.
- [ ] CSS and JavaScript have been inspected.
- [ ] Font loading has been reviewed.
- [ ] Caching and CDN behaviour have been checked where relevant.
- [ ] Third-party scripts have been evaluated.
- [ ] Important findings include evidence.
- [ ] Fixes have been prioritized.
- [ ] Performance has been retested after implementation.
- [ ] Monitoring has been planned.

---

## 17. Official Documentation & Further Reading

Use official documentation for accurate definitions, thresholds, and implementation guidance.

### Google Search & Core Web Vitals

- [Core Web Vitals](https://web.dev/articles/vitals)
- [Web Vitals](https://web.dev/articles/vitals)
- [Largest Contentful Paint](https://web.dev/articles/lcp)
- [Interaction to Next Paint](https://web.dev/articles/inp)
- [Cumulative Layout Shift](https://web.dev/articles/cls)
- [Google Search Console Core Web Vitals Report](https://support.google.com/webmasters/answer/9205520)
- [PageSpeed Insights](https://pagespeed.web.dev/)

### Performance Diagnostics

- [Lighthouse Documentation](https://developer.chrome.com/docs/lighthouse/)
- [Chrome DevTools Performance](https://developer.chrome.com/docs/devtools/performance/)
- [Chrome DevTools Network](https://developer.chrome.com/docs/devtools/network/)
- [WebPageTest](https://www.webpagetest.org/)

### Web Platform Guidance

- [MDN Web Performance](https://developer.mozilla.org/en-US/docs/Web/Performance)
- [web.dev Performance](https://web.dev/explore/learn-core-web-vitals)

---

## Final Audit Principle

Website performance is not about chasing perfect scores or applying every available optimization technique.

It is about making important content load reliably, keeping interactions responsive, preventing unexpected layout movement, and delivering a consistent experience across devices and network conditions.

Measure first, identify the real bottleneck, implement targeted improvements, and verify the result using both laboratory diagnostics and real-user data where available.
