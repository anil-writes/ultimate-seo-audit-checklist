# AI Agents & Future Readiness (AXO) Audit

The web is evolving beyond traditional search engines and human-operated browsing.

AI-powered systems can discover information, retrieve web pages, summarize content, interact with websites, and, in some environments, perform actions on behalf of users.

This creates new considerations for website owners and developers.

An AI-ready website should make its information accessible, understandable, trustworthy, and usable without compromising security, privacy, or human usability.

This audit evaluates website readiness for AI-powered discovery and agent-assisted interactions.

It covers:

1. Agent Experience Optimization (AXO) fundamentals.
2. AI agent access and crawler policies.
3. Machine-readable content and structured information.
4. Semantic HTML and accessibility.
5. Browser automation and interaction compatibility.
6. APIs and controlled integrations.
7. Agent-assisted ecommerce and transactions.
8. Security, privacy, and permission boundaries.
9. Content provenance and data reliability.
10. Monitoring and future readiness.

> **Important:** AXO (Agent Experience Optimization) is an emerging industry term, not a universally standardized SEO framework or an official Google ranking system. This audit is a practical readiness framework, not a guarantee that AI agents will discover, understand, cite, or successfully operate a website.

Not every website needs agent-specific APIs or transaction automation. Implement capabilities according to genuine business requirements and security considerations.

---

## 1. AI Agents & AXO Fundamentals

### Audit objective

Understand how AI-powered systems may discover, interpret, and interact with the website.

### Key concepts

**AI-powered discovery:** Systems retrieve or process website information to answer user questions.

**AI crawlers:** Automated systems that visit pages to discover or process web content.

**AI agents:** Systems that can interpret instructions, use tools, navigate websites, and potentially perform tasks.

**Agent experience:** How reliably an automated agent can understand the website's content, controls, and available actions.

**Machine-readable information:** Structured information that software can interpret more reliably than unstructured presentation alone.

### Checks

- [ ] Identify whether the website contains information that AI systems may need to discover.
- [ ] Identify important pages that should be publicly accessible.
- [ ] Review whether important information is understandable without relying entirely on visual presentation.
- [ ] Check whether page content is available in rendered HTML.
- [ ] Identify important interactive tasks visitors may want an agent to assist with.
- [ ] Determine whether those tasks require APIs or can be completed through ordinary browser interaction.
- [ ] Identify sensitive actions that must remain under human control.
- [ ] Establish whether AI access is beneficial, unnecessary, or undesirable for different sections of the website.

### How to audit

Review the website from three perspectives:

1. A human visitor reading the page.
2. A search or retrieval system accessing the content.
3. An authorized automated agent attempting to understand the interface.

Identify where information, navigation, or interaction becomes difficult for any of these users.

### Recommended approach

Start with accessibility, semantic structure, reliable content, and predictable interactions.

Do not introduce complicated agent infrastructure when ordinary web standards already solve the problem.

---

## 2. AI Crawler Access & Robots.txt Policies

### Audit objective

Understand which automated systems can access the website and whether access policies reflect the website owner's intentions.

AI-related crawlers do not all serve the same purpose. Some support search discovery, while others may be associated with model training or user-triggered page retrieval.

### Important crawler distinctions

| Crawler | Purpose |
|---|---|
| OAI-SearchBot | OpenAI crawler used for ChatGPT search discovery |
| GPTBot | OpenAI crawler that may collect content for model training |
| ChatGPT-User | Visits pages in response to certain user requests |
| Googlebot | Google's crawler for search discovery and indexing |
| Google-Extended | Google control token related to certain AI training and grounding uses |
| Bingbot | Microsoft's search crawler |
| PerplexityBot | Perplexity crawler associated with search discovery |

Crawler names and policies can change. Always check the provider's current documentation before modifying access rules.

### Checks

- [ ] Review the website's robots.txt file.
- [ ] Identify which AI-related crawlers are allowed or blocked.
- [ ] Confirm that important public pages are not unintentionally blocked.
- [ ] Review whether private or sensitive sections are protected independently of robots.txt.
- [ ] Check whether firewall or CDN rules block legitimate crawlers.
- [ ] Identify crawler-specific rules that conflict with broader policies.
- [ ] Review whether important assets are accessible when needed.
- [ ] Check crawler responses in server logs where available.
- [ ] Review whether crawler access decisions align with business and content policies.
- [ ] Document the reason for allowing or blocking each relevant crawler.

### Example robots.txt structure

```text
User-agent: OAI-SearchBot
Allow: /

User-agent: GPTBot
Disallow: /

User-agent: Googlebot
Allow: /

Sitemap: https://example.com/sitemap.xml
```

This is an illustrative example, not a universal recommendation.

The correct configuration depends on the website owner's choices and the provider's current rules.

### Important distinction

Allowing a search crawler does not necessarily mean allowing model-training crawlers.

For example, OpenAI documents OAI-SearchBot and GPTBot as separate controls with different purposes.

### Recommended fixes

Use crawler-specific policies where appropriate, test robots.txt changes, and maintain a documented access strategy.

Do not use robots.txt as a security mechanism. It is a crawler instruction file, not authentication or access control.

### Official documentation

- OpenAI crawler documentation: https://developers.openai.com/api/docs/bots
- Google robots.txt documentation: https://developers.google.com/search/docs/crawling-indexing/robots/intro
- Google-Extended information: https://developers.google.com/search/docs/crawling-indexing/google-common-crawlers
- Bing Webmaster Guidelines: https://www.bing.com/webmasters/help/webmaster-guidelines-30fba23a

---

## 3. Machine-Readable Content & Semantic Structure

### Audit objective

Make important website information understandable through standard web technologies and structured representations.

### Checks

- [ ] Important content has meaningful HTML structure.
- [ ] Page titles describe the actual page.
- [ ] Headings communicate the content hierarchy.
- [ ] Lists use appropriate list elements.
- [ ] Tables use meaningful row and column relationships.
- [ ] Links have descriptive text.
- [ ] Buttons have understandable accessible names.
- [ ] Important business and product information is clearly represented.
- [ ] Structured data is accurate where applicable.
- [ ] Content does not rely entirely on images to communicate essential information.
- [ ] Important details are not available only after inaccessible interactions.
- [ ] Structured information matches the visible page content.

### How to audit

Inspect the rendered HTML and compare it with what a human visitor sees.

Review whether software can identify:

- Page purpose.
- Main heading.
- Important entities.
- Product or service information.
- Prices and availability.
- Business identity.
- Author or publisher information.
- Relevant links and relationships.

### Example

A product page should communicate the following clearly:

```text
Product name: Wireless Headphones
Brand: Example Audio
Price: ₹2,499
Availability: In stock
Warranty: 1 year
```

This information should be accurately represented in the page content and, where appropriate, structured data.

### Recommended fixes

Use semantic HTML, descriptive content, consistent terminology, and valid structured data.

Do not create separate machine-readable information that contradicts the visible website.

---

## 4. JavaScript Rendering & Content Accessibility

### Audit objective

Ensure important website information remains accessible to systems that may not execute JavaScript in the same way as a modern browser.

Different automated systems have different rendering capabilities.

Google Search can render JavaScript, but other crawlers and automated systems may not behave identically.

### Checks

- [ ] Important page content is available in the initial HTML or reliably rendered output.
- [ ] Navigation links use crawlable link elements.
- [ ] Important content does not require unnecessary user interaction to appear.
- [ ] JavaScript failures do not remove essential information.
- [ ] Important pages do not depend entirely on client-side application state.
- [ ] Content is available when scripts load successfully.
- [ ] Server-side rendering or static rendering is considered where useful.
- [ ] Important links are not implemented only as non-semantic click handlers.
- [ ] Error states do not hide essential content.
- [ ] Rendered output is tested using appropriate inspection tools.

### How to audit

Use:

- Chrome DevTools.
- Google Search Console URL Inspection.
- Google's Rich Results Test.
- Browser JavaScript-disabled testing.
- HTML inspection and automated crawlers.

Compare the original HTML with the rendered page.

### Recommended fixes

Use server-side rendering, static rendering, or appropriate progressive enhancement when it improves reliability and discoverability.

Avoid assuming that every AI crawler can execute JavaScript.

Official documentation:

https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics

---

## 5. Semantic HTML & Accessibility for Agents

### Audit objective

Make website controls and information easier to identify through standard HTML semantics and accessibility features.

Accessible interfaces also tend to be more predictable for browser automation.

### Checks

- [ ] Use appropriate HTML elements for page structure.
- [ ] Use links for navigation.
- [ ] Use buttons for actions.
- [ ] Provide labels for form fields.
- [ ] Use meaningful accessible names for interactive controls.
- [ ] Maintain logical heading hierarchy.
- [ ] Use appropriate ARIA attributes only when necessary.
- [ ] Ensure controls are keyboard accessible.
- [ ] Provide clear error and success messages.
- [ ] Avoid ambiguous labels such as multiple unrelated "Click Here" buttons.
- [ ] Ensure dynamic content changes are communicated appropriately.
- [ ] Avoid using visual styling as a substitute for semantic meaning.

### Example

Prefer:

```html
<a href="/pricing/">View pricing plans</a>

<button type="button">Add to cart</button>

<label for="email">Email address</label>
<input id="email" type="email" name="email">
```

Avoid using generic clickable elements when native HTML controls are more appropriate.

### Recommended fixes

Follow semantic HTML and accessibility standards.

Use ARIA only when native HTML does not provide the required semantics.

Do not add unnecessary ARIA attributes to already accessible elements.

Reference:

https://www.w3.org/WAI/ARIA/apg/

---

## 6. Browser Automation & Agent-Compatible Interactions

### Audit objective

Evaluate whether important website interactions are predictable, understandable, and reliable for authorized browser automation.

### Checks

- [ ] Important navigation links have stable destinations.
- [ ] Buttons perform clearly defined actions.
- [ ] Forms have descriptive labels.
- [ ] Form validation provides understandable feedback.
- [ ] Interactive controls expose their current state.
- [ ] Important actions do not depend only on hover.
- [ ] Menus can be operated through keyboard and pointer interaction.
- [ ] Loading states are detectable.
- [ ] Success and failure states are communicated.
- [ ] Important interactions do not require unnecessary timing precision.
- [ ] Session expiration is handled clearly.
- [ ] Unexpected pop-ups do not block essential tasks.
- [ ] Critical workflows are tested across supported browsers.

### How to audit

Create a list of important user tasks and test them manually.

Example:

1. Open the service page.
2. Locate pricing.
3. Select a plan.
4. Complete the enquiry form.
5. Review the confirmation message.

Record where the interaction becomes ambiguous, unreliable, or impossible.

If the website supports automated testing, use authorized browser automation tools in a controlled environment.

### Recommended fixes

Use standard HTML controls, predictable navigation, explicit feedback, and reliable form handling.

Do not design interactions specifically to manipulate automated agents into unintended actions.

---

## 7. APIs, Integrations & Machine-Accessible Services

### Audit objective

Determine whether structured APIs or integrations would make specific website services more reliable for authorized software and agents.

Not every website needs a public API.

### Checks

- [ ] Identify whether important business operations require programmatic access.
- [ ] Check whether an existing API is documented.
- [ ] Review API authentication requirements.
- [ ] Ensure API responses use consistent data structures.
- [ ] Document required parameters and response formats.
- [ ] Define rate limits and usage restrictions.
- [ ] Review error responses.
- [ ] Ensure sensitive data is not exposed publicly.
- [ ] Use authorization for protected actions.
- [ ] Review API versioning and compatibility.
- [ ] Document whether operations are read-only or can modify data.
- [ ] Monitor API availability and errors.

### Potential use cases

- Checking product availability.
- Retrieving public pricing.
- Searching a product catalogue.
- Checking booking availability.
- Retrieving order status for an authenticated customer.
- Submitting an authorized service enquiry.

### Example API response

```json
{
  "product_id": "P1001",
  "name": "Wireless Headphones",
  "price": 2499,
  "currency": "INR",
  "availability": "in_stock"
}
```

This is an illustrative data format, not a required schema.

### Recommended fixes

Provide APIs only when they solve a real integration or automation requirement.

Use appropriate authentication, permissions, rate limits, validation, and monitoring.

Never expose private customer information or privileged business operations through unauthenticated endpoints.

---

## 8. Agent-Assisted Ecommerce & Transactions

### Audit objective

Evaluate whether an ecommerce website can support safe and understandable agent-assisted shopping journeys.

### Checks

- [ ] Product information is accurate and consistent.
- [ ] Product availability is current.
- [ ] Pricing and currency are clearly represented.
- [ ] Product variants are distinguishable.
- [ ] Shipping costs and delivery conditions are accessible.
- [ ] Return and cancellation policies are easy to find.
- [ ] Cart contents can be reviewed clearly.
- [ ] Payment methods and checkout steps are understandable.
- [ ] Important purchase details are confirmed before payment.
- [ ] Authentication and authorization are enforced.
- [ ] High-impact actions require appropriate user confirmation.
- [ ] Order status is communicated accurately.
- [ ] Transaction failures are handled safely.

### Human approval and control

Agents should not be allowed to perform high-impact actions without appropriate authorization.

Examples include:

- Making a purchase.
- Sending money.
- Cancelling an order.
- Changing account details.
- Booking a non-refundable service.
- Submitting sensitive personal information.

The website should make the action, cost, consequences, and confirmation process clear.

### Recommended fixes

Use clear transaction states, explicit confirmation steps, secure payment systems, and appropriate permission controls.

Do not assume that making a website automatable means allowing unrestricted purchases or account modifications.

---

## 9. AI Content Retrieval, Citations & Provenance

### Audit objective

Make important information easier to verify and understand while maintaining content accuracy and source transparency.

### Checks

- [ ] Important claims are supported by reliable evidence.
- [ ] Content distinguishes facts from opinions.
- [ ] Authors and publishers are identifiable where appropriate.
- [ ] Publication and update dates are accurate.
- [ ] External sources are cited when necessary.
- [ ] Statistics include context and source information.
- [ ] Product and service claims are verifiable.
- [ ] Content avoids misleading or unsupported statements.
- [ ] Important information is organized into understandable sections.
- [ ] Definitions and terminology are used consistently.
- [ ] Original research explains its methodology.
- [ ] Corrections are handled transparently.

### How to audit

Select important pages and evaluate whether a reader or automated system can identify:

- Who published the information.
- What the main claim is.
- What evidence supports it.
- When the information was published or updated.
- Which sources support the claim.
- Whether the content is factual, interpretive, or promotional.

### Recommended fixes

Improve sourcing, explain methodology, identify authors, and keep important information accurate.

Do not add citations merely to make a page appear authoritative. Sources should genuinely support the claims being made.

---

## 10. AI-Specific Discovery Files & Emerging Conventions

### Audit objective

Evaluate emerging files and conventions that may help automated systems understand a website.

### Checks

- [ ] Review whether an XML sitemap is maintained.
- [ ] Check whether important content has clear canonical URLs.
- [ ] Review robots.txt policies.
- [ ] Evaluate whether a public documentation index is useful.
- [ ] Check whether an llms.txt file exists and whether it provides accurate information.
- [ ] Review any machine-readable service documentation.
- [ ] Ensure supplementary files do not contradict the main website.
- [ ] Document the purpose and maintenance responsibility of each file.

### About llms.txt

`llms.txt` is a proposed convention intended to provide AI systems with a curated overview of a website and links to useful resources.

It is not a universal requirement, and it is not an established Google ranking factor.

Creating the file does not guarantee that AI systems will read or use it.

### Example illustrative structure

```text
# Example Website

> Official website for Example Company.

## Main Resources

- [About](https://example.com/about/)
- [Services](https://example.com/services/)
- [Documentation](https://example.com/docs/)
- [Contact](https://example.com/contact/)
```

Only include accurate, useful, publicly accessible resources.

### Recommended approach

Prioritize standard web infrastructure, accessible content, and reliable structured information.

Treat emerging conventions as optional experiments until there is clear evidence of practical value and adoption.

---

## 11. Security, Privacy & Agent Permission Boundaries

### Audit objective

Ensure that automation and AI integrations cannot bypass normal security or privacy protections.

### Checks

- [ ] Sensitive pages require proper authentication.
- [ ] Authorization is enforced on the server.
- [ ] Private APIs do not expose confidential information.
- [ ] API keys and credentials are not embedded in public frontend code.
- [ ] Session tokens are protected.
- [ ] Form submissions are validated server-side.
- [ ] Rate limits protect important endpoints.
- [ ] Destructive actions require appropriate confirmation.
- [ ] Payment operations use secure payment infrastructure.
- [ ] User data is collected only for legitimate purposes.
- [ ] Data retention and deletion policies are documented.
- [ ] Automated traffic is monitored for abuse.
- [ ] Third-party integrations are reviewed for security implications.

### Agent-specific risks

AI agents may misinterpret instructions, follow malicious page content, or attempt actions that the user did not intend.

Websites should not assume that an agent's request is automatically trustworthy.

### Recommended fixes

Apply established security principles:

- Least privilege.
- Authentication.
- Authorization.
- Input validation.
- Output encoding.
- Rate limiting.
- Audit logging.
- Human confirmation for sensitive actions.

Do not rely on hidden buttons, robots.txt, or user-agent detection as security controls.

### Official references

- OWASP Top 10: https://owasp.org/www-project-top-ten/
- OWASP API Security: https://owasp.org/www-project-api-security/
- OWASP Web Security Testing Guide: https://owasp.org/www-project-web-security-testing-guide/

---

## 12. Agent Testing & Compatibility Evaluation

### Audit objective

Determine whether an authorized agent or automation system can reliably complete clearly defined website tasks.

### Checks

- [ ] Identify important tasks suitable for automation.
- [ ] Define expected task outcomes.
- [ ] Test navigation and page discovery.
- [ ] Test form interactions in a safe environment.
- [ ] Test error handling.
- [ ] Test browser compatibility.
- [ ] Verify that agents cannot access restricted information.
- [ ] Confirm that high-impact actions require authorization.
- [ ] Record unsuccessful tasks and their causes.
- [ ] Retest after major interface or API changes.

### Example test scenarios

| Task | Expected outcome |
|---|---|
| Find a service | Correct service page is discovered |
| Retrieve pricing | Current pricing is returned |
| Search products | Relevant products are identified |
| Submit an enquiry | Form validates and confirms submission |
| Access private account data | Authentication is required |
| Make a purchase | Appropriate authorization and confirmation are required |

### How to audit

Use test accounts, sandbox environments, and authorized automation tools.

Do not test real payments, customer accounts, or destructive operations without explicit authorization.

### Recommended fixes

Improve unclear navigation, inaccessible controls, inconsistent data, and unreliable workflows.

Measure task completion and error rates rather than simply declaring a website "AI compatible."

---

## 13. Monitoring, Governance & Future Readiness

### Audit objective

Maintain a responsible approach to emerging AI technologies without repeatedly adopting unproven techniques.

### Checks

- [ ] Assign responsibility for AI-related website policies.
- [ ] Document crawler access decisions.
- [ ] Review crawler traffic and server logs where useful.
- [ ] Monitor API usage and errors.
- [ ] Review security and permission policies periodically.
- [ ] Track changes in major search and AI platform documentation.
- [ ] Review emerging technical conventions before adopting them.
- [ ] Document automation capabilities and limitations.
- [ ] Maintain testing procedures for important agent workflows.
- [ ] Review privacy and legal requirements in target markets.
- [ ] Record significant changes to website architecture and integrations.

### Recommended approach

Review relevant platform documentation periodically rather than reacting to every new acronym or industry trend.

Adopt a new technology only when it provides a clear benefit and can be maintained safely.

---

## 14. AXO Audit Issue Prioritization & Reporting

### Audit objective

Convert agent-readiness findings into actionable development and governance tasks.

### Suggested priority levels

| Priority | Meaning | Example |
|---|---|---|
| Critical | Security, privacy, or transaction risk | Unauthorized API access to customer data |
| High | Important discovery or task failure | Main service content unavailable to intended crawlers |
| Medium | Reliability or compatibility problem | Important form controls difficult to automate |
| Low | Optional improvement | Additional documentation index |

### AXO audit report template

| Field | Description |
|---|---|
| Issue ID | Unique reference |
| Page or endpoint | Affected URL or API |
| System tested | Browser, crawler, or agent |
| Finding | What is wrong |
| Evidence | Logs, screenshots, or test output |
| User impact | Effect on visitors |
| Security impact | Potential risk |
| Recommended fix | Proposed change |
| Priority | Critical, High, Medium, or Low |
| Verification | How the fix will be tested |
| Status | Open, In Progress, or Resolved |

### Example finding

**Issue:** Important service information is generated only after a client-side interaction.

**Location:** Service detail page.

**Evidence:** Initial HTML does not contain the main service description.

**User impact:** Some automated systems may not access the complete information.

**Recommended fix:** Make essential content available through reliable rendered HTML.

**Verification:** Compare initial and rendered HTML and test using the relevant inspection tools.

---

## 15. Common AXO & AI Readiness Mistakes

Avoid these mistakes:

- Treating AXO as an officially established Google ranking factor.
- Assuming all AI crawlers have identical purposes.
- Blocking all automated systems without considering business requirements.
- Allowing all crawlers without reviewing content and privacy policies.
- Treating robots.txt as a security mechanism.
- Assuming every AI system can execute JavaScript.
- Adding structured data that contradicts visible content.
- Creating an llms.txt file and expecting guaranteed AI citations.
- Building unnecessary public APIs.
- Exposing private information through machine-readable endpoints.
- Allowing automated agents to perform sensitive actions without authorization.
- Treating user-agent strings as proof of crawler identity.
- Optimizing interfaces for agents while making them harder for humans.
- Adopting experimental standards without checking their status and practical value.

---

## 16. AXO Audit Completion Checklist

An AXO readiness audit can be considered complete when:

- [ ] AI and automation use cases have been identified.
- [ ] Relevant crawler policies have been reviewed.
- [ ] Important content is accessible in rendered output.
- [ ] Semantic HTML and accessibility have been evaluated.
- [ ] Structured data has been reviewed where applicable.
- [ ] Important browser interactions have been tested.
- [ ] API requirements have been evaluated.
- [ ] Sensitive actions have appropriate permission controls.
- [ ] Security and privacy risks have been reviewed.
- [ ] Content accuracy and provenance have been evaluated.
- [ ] Emerging conventions have been assessed without assuming they are mandatory.
- [ ] Important tasks have been tested in a controlled environment.
- [ ] Findings include supporting evidence.
- [ ] Issues have been prioritized.
- [ ] Monitoring and governance responsibilities have been defined.

---

## 17. Official Documentation & Further Reading

### OpenAI

- [Overview of OpenAI Crawlers](https://developers.openai.com/api/docs/bots)
- [Publishers and Developers FAQ](https://help.openai.com/en/articles/12627856-publishers-and-developers-faq)

### Google

- [JavaScript SEO Basics](https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics)
- [Google Crawlers and Fetchers](https://developers.google.com/search/docs/crawling-indexing/google-common-crawlers)
- [Structured Data Guidelines](https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data)
- [Robots.txt Introduction](https://developers.google.com/search/docs/crawling-indexing/robots/intro)

### Web Standards & Accessibility

- [W3C Web Accessibility Initiative](https://www.w3.org/WAI/)
- [WAI-ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/)
- [MDN HTML Documentation](https://developer.mozilla.org/en-US/docs/Web/HTML)

### Security

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP API Security](https://owasp.org/www-project-api-security/)

---

## Final Audit Principle

AI readiness is not about adding as many AI-specific files, scripts, or integrations as possible.

It is about building a website that is accessible, understandable, secure, reliable, and useful to both people and authorized software systems.

Start with strong web fundamentals, apply machine-readable structure where it adds value, define clear permission boundaries, and test real tasks before claiming agent compatibility.
