# Security, Governance & Website Maintenance Audit

Website security and maintenance are essential for protecting visitors, business data, website availability, and long-term search visibility.

A website may have excellent content, strong backlinks, and good technical SEO, but security vulnerabilities, outdated software, broken integrations, or poor maintenance can put the entire website at risk.

This audit helps website owners and professionals review security controls, software maintenance, access permissions, backups, privacy practices, incident response, and operational reliability.

> **Important:** This checklist is a practical website audit framework, not a penetration-testing procedure or a substitute for a professional security assessment. Do not test systems without proper authorization.

---

## 1. HTTPS & Website Security

### 1.1 HTTPS implementation

- [ ] Does the website use HTTPS across all public pages?
- [ ] Is the SSL/TLS certificate valid and not expired?
- [ ] Does HTTP redirect correctly to HTTPS?
- [ ] Are redirects configured consistently?
- [ ] Are canonical URLs using the preferred HTTPS version?
- [ ] Are internal links and important assets served over HTTPS?
- [ ] Are mixed-content warnings resolved?
- [ ] Are certificate renewal processes monitored?

**How to audit:**

1. Open important website URLs using HTTP and HTTPS.
2. Confirm that HTTP requests redirect to the preferred HTTPS version.
3. Inspect the browser security indicator.
4. Review certificate validity and expiration.
5. Check for mixed-content warnings in browser developer tools.

**Fix:** Correct redirect rules, update internal references, resolve mixed content, and configure certificate renewal monitoring.

### 1.2 Security headers

- [ ] Is an appropriate Content Security Policy (CSP) configured?
- [ ] Is HTTP Strict Transport Security (HSTS) configured where appropriate?
- [ ] Is `X-Content-Type-Options` configured?
- [ ] Is clickjacking protection implemented through suitable CSP directives or other appropriate controls?
- [ ] Is the `Referrer-Policy` appropriate?
- [ ] Are unnecessary or sensitive server-identification headers avoided?

**How to audit:** Inspect HTTP response headers using browser developer tools or a trusted security-header testing tool.

**Important:** Security headers must be configured according to the website's architecture. Incorrect CSP or HSTS settings can break functionality or create deployment problems.

---

## 2. CMS, Software & Dependency Maintenance

### 2.1 CMS and platform updates

- [ ] Is the CMS running a supported version?
- [ ] Are security updates installed promptly?
- [ ] Are themes and plugins updated?
- [ ] Are unsupported or abandoned extensions removed?
- [ ] Are unused themes, plugins, modules, and integrations removed?
- [ ] Are updates tested before production deployment where practical?
- [ ] Is compatibility checked after major upgrades?

This applies to platforms such as:

- WordPress
- Shopify
- Drupal
- Joomla
- Magento / Adobe Commerce
- Custom-built websites
- Other hosted website platforms

### 2.2 Third-party dependencies

- [ ] Are external libraries and frameworks maintained?
- [ ] Are known vulnerable dependencies identified?
- [ ] Are outdated JavaScript packages reviewed?
- [ ] Are package versions and dependency sources documented?
- [ ] Are unnecessary third-party scripts removed?
- [ ] Are dependencies updated through a controlled process?

For custom applications, consider tools such as dependency scanners and automated vulnerability alerts.

**Fix:** Prioritize known exploitable vulnerabilities and unsupported dependencies. Do not blindly update production packages without checking compatibility and testing critical functionality.

### 2.3 Development and deployment practices

- [ ] Is there a separate staging or testing environment where appropriate?
- [ ] Are production changes reviewed before deployment?
- [ ] Are deployment procedures documented?
- [ ] Are rollback procedures available?
- [ ] Are environment variables and secrets managed securely?
- [ ] Are production credentials excluded from public repositories?
- [ ] Are source-code repositories protected with suitable access controls?

**Important:** Never commit API keys, database passwords, private tokens, or other secrets to a public GitHub repository.

---

## 3. User Accounts & Access Control

### 3.1 Administrative access

- [ ] Are administrative accounts limited to authorized people?
- [ ] Are default or unused accounts removed?
- [ ] Are former employees and contractors removed from access lists?
- [ ] Are shared administrator accounts avoided?
- [ ] Are unique user accounts assigned?
- [ ] Are permissions based on actual job responsibilities?
- [ ] Are privileged accounts reviewed periodically?

### 3.2 Authentication

- [ ] Is multi-factor authentication (MFA) enabled for administrators?
- [ ] Are strong authentication methods supported?
- [ ] Are password-reset processes secure?
- [ ] Are login attempts monitored?
- [ ] Is rate limiting or suitable protection against automated login abuse configured?
- [ ] Are session expiration and logout behavior appropriate?
- [ ] Are compromised credentials handled promptly?

### 3.3 Least-privilege access

- [ ] Do users receive only the permissions they need?
- [ ] Are hosting, domain, CMS, DNS, and analytics permissions reviewed separately?
- [ ] Are external agencies and developers given controlled access?
- [ ] Are sensitive actions logged where possible?
- [ ] Is access revoked when a project or contract ends?

**Fix:** Maintain an access register that identifies the account owner, role, permission level, and review date. Avoid sharing passwords through email, public documents, or chat messages.

---

## 4. Hosting, Server & Infrastructure Security

### 4.1 Hosting environment

- [ ] Is the hosting provider actively maintaining its infrastructure?
- [ ] Is the server environment supported?
- [ ] Are unnecessary services and ports disabled?
- [ ] Are server permissions configured appropriately?
- [ ] Is database access restricted?
- [ ] Are administrative interfaces protected?
- [ ] Are server logs available?
- [ ] Are security updates applied to managed infrastructure?

### 4.2 DNS and domain security

- [ ] Is domain ownership registered under the correct account?
- [ ] Is domain auto-renewal configured where appropriate?
- [ ] Is the domain expiration date monitored?
- [ ] Is registrar account MFA enabled?
- [ ] Are DNS records reviewed periodically?
- [ ] Are unnecessary or outdated DNS records removed?
- [ ] Is DNSSEC considered where supported and appropriate?
- [ ] Are domain transfer protections enabled where available?

### 4.3 Server configuration

- [ ] Are directory listings disabled unless explicitly required?
- [ ] Are sensitive configuration files inaccessible publicly?
- [ ] Are database backups protected?
- [ ] Are error messages prevented from exposing sensitive technical details?
- [ ] Are file permissions appropriate?
- [ ] Are administrative tools restricted?
- [ ] Are server-side logs monitored for suspicious activity?

**Fix:** Ask the hosting provider or infrastructure administrator to investigate issues that require server-level access. Do not change production server settings without understanding their impact.

---

## 5. Malware, Vulnerability & Threat Monitoring

### 5.1 Malware and suspicious activity

- [ ] Is the website monitored for malware?
- [ ] Are unexpected file modifications investigated?
- [ ] Are suspicious administrator accounts reviewed?
- [ ] Are unusual login patterns monitored?
- [ ] Are unexpected redirects investigated?
- [ ] Are injected links or spam pages checked?
- [ ] Are unauthorized scripts identified?
- [ ] Are security alerts reviewed promptly?

### 5.2 Vulnerability management

- [ ] Are security advisories monitored for the CMS and major dependencies?
- [ ] Are known vulnerabilities assessed?
- [ ] Are critical issues prioritized by severity and exposure?
- [ ] Are remediation actions documented?
- [ ] Are fixes validated after deployment?
- [ ] Are unresolved vulnerabilities tracked?

### 5.3 Security incident indicators

Investigate unexpected occurrences such as:

- Sudden redirects to unfamiliar websites.
- Unknown administrator accounts.
- Unexpected files or scripts.
- Spam pages appearing in search results.
- Unusual outbound links.
- Browser malware warnings.
- Unexpected server resource consumption.
- Unexplained changes to website content.
- Suspicious traffic or authentication activity.

**Important:** A security warning or unusual metric is a signal to investigate, not automatic proof of compromise.

---

## 6. Backup & Disaster Recovery

### 6.1 Backup strategy

- [ ] Are website files backed up?
- [ ] Are databases backed up?
- [ ] Are important configuration files included?
- [ ] Are backups stored separately from the production environment?
- [ ] Are backups protected against unauthorized access?
- [ ] Is backup frequency appropriate for the website's update and transaction volume?
- [ ] Are backup retention periods documented?
- [ ] Are backup failures monitored?

### 6.2 Backup restoration testing

- [ ] Has a backup been restored successfully in a test environment?
- [ ] Are restoration instructions documented?
- [ ] Are restored files and databases validated?
- [ ] Are important integrations checked after restoration?
- [ ] Are backup integrity and completeness verified?

**Important:** A backup that has never been tested is not a proven recovery solution.

### 6.3 Recovery planning

- [ ] Is there a documented recovery procedure?
- [ ] Are recovery responsibilities assigned?
- [ ] Is the expected recovery time understood?
- [ ] Is acceptable data loss defined?
- [ ] Are domain, DNS, hosting, and database recovery steps documented?
- [ ] Are critical third-party dependencies identified?
- [ ] Is the recovery plan reviewed periodically?

Understand these two concepts:

- **RTO (Recovery Time Objective):** The target time within which a service should be restored.
- **RPO (Recovery Point Objective):** The acceptable amount of data loss measured in time.

These targets should reflect the website's business importance and operational requirements.

---

## 7. Privacy, Data Protection & User Trust

### 7.1 Privacy documentation

- [ ] Is a privacy policy available?
- [ ] Does it accurately describe data collection and usage?
- [ ] Are third-party services and integrations disclosed where required?
- [ ] Is the privacy policy easy to find?
- [ ] Is contact information available for relevant privacy requests?
- [ ] Are outdated policy statements reviewed?

### 7.2 Forms and personal information

- [ ] Do forms collect only necessary information?
- [ ] Are sensitive fields protected?
- [ ] Are form submissions transmitted securely?
- [ ] Is access to submitted information restricted?
- [ ] Are data retention practices documented?
- [ ] Are spam and abusive submissions managed?
- [ ] Are personal details prevented from appearing in URLs or analytics events?

### 7.3 Cookies and consent

- [ ] Are cookies and tracking technologies reviewed?
- [ ] Is consent implemented where legally required?
- [ ] Are non-essential technologies handled according to applicable consent requirements?
- [ ] Are consent preferences respected?
- [ ] Can users access relevant privacy choices?
- [ ] Are consent configurations tested after changes?

**Important:** Legal obligations vary by jurisdiction, website audience, business type, and data processing activity. Use qualified legal guidance when necessary.

### 7.4 Website trust

- [ ] Are contact details accurate?
- [ ] Are business identity and ownership details clear where relevant?
- [ ] Are terms and conditions available where appropriate?
- [ ] Are refund, cancellation, and delivery policies clear for ecommerce websites?
- [ ] Are payment methods and checkout processes trustworthy?
- [ ] Are commercial disclosures and affiliate relationships transparent?
- [ ] Are misleading claims and deceptive interface patterns avoided?

---

## 8. Website Availability & Operational Monitoring

### 8.1 Uptime monitoring

- [ ] Is website availability monitored?
- [ ] Are important pages included in monitoring?
- [ ] Are downtime alerts configured?
- [ ] Are server errors investigated?
- [ ] Are DNS and certificate problems monitored?
- [ ] Are maintenance windows documented?
- [ ] Are uptime reports reviewed?

### 8.2 Error and log monitoring

- [ ] Are recurring 4xx errors investigated?
- [ ] Are 5xx errors monitored?
- [ ] Are application errors logged?
- [ ] Are failed API requests reviewed?
- [ ] Are payment and checkout failures investigated?
- [ ] Are suspicious patterns escalated?
- [ ] Are log retention and access controls appropriate?

### 8.3 Critical functionality checks

- [ ] Do important forms work?
- [ ] Do checkout and payment flows work?
- [ ] Do login and registration functions work?
- [ ] Do booking or enquiry workflows work?
- [ ] Do important integrations work?
- [ ] Are email notifications delivered?
- [ ] Are important user journeys tested after major updates?

**Fix:** Create a small set of repeatable operational checks for the website's most important user journeys.

---

## 9. Website Maintenance & Technical Hygiene

### 9.1 Regular maintenance

- [ ] Are outdated pages reviewed?
- [ ] Are broken internal links corrected?
- [ ] Are unnecessary redirects removed?
- [ ] Are unused plugins and scripts removed?
- [ ] Are obsolete files and temporary assets cleaned up?
- [ ] Are important integrations reviewed?
- [ ] Are contact details and business information updated?
- [ ] Are important forms and interactive elements tested?

### 9.2 Content and SEO maintenance

- [ ] Are important content pages reviewed for accuracy?
- [ ] Are outdated claims and statistics updated?
- [ ] Are discontinued products and services handled appropriately?
- [ ] Are obsolete URLs redirected when a suitable replacement exists?
- [ ] Are important internal links maintained?
- [ ] Are structured data and metadata reviewed after template changes?
- [ ] Are sitemaps and robots directives checked after major changes?

### 9.3 Performance maintenance

- [ ] Are Core Web Vitals monitored periodically?
- [ ] Are large images and unnecessary assets reviewed?
- [ ] Are caching rules still appropriate?
- [ ] Are third-party scripts reviewed?
- [ ] Are database and server performance issues monitored?
- [ ] Are performance regressions investigated after deployments?

**Fix:** Maintenance should be planned according to risk and business impact. Avoid changing working production systems simply to keep everything constantly updated without testing.

---

## 10. Change Management & Website Governance

### 10.1 Change management

- [ ] Are important website changes documented?
- [ ] Are changes reviewed before release?
- [ ] Are affected pages and systems identified?
- [ ] Are SEO implications considered before URL or template changes?
- [ ] Are backups or rollback options available before risky deployments?
- [ ] Are post-release checks performed?
- [ ] Are stakeholders informed about significant changes?

### 10.2 Roles and responsibilities

- [ ] Is there a clear website owner?
- [ ] Are technical responsibilities assigned?
- [ ] Are content approval responsibilities defined?
- [ ] Are hosting and domain responsibilities documented?
- [ ] Are security escalation contacts identified?
- [ ] Are third-party vendor responsibilities understood?

### 10.3 Documentation

Maintain documentation for:

- Website architecture.
- Hosting and domain ownership.
- DNS configuration.
- CMS and important dependencies.
- Backup and restoration procedures.
- Analytics and tracking configuration.
- Deployment and rollback procedures.
- Security contacts and escalation processes.
- Important third-party integrations.

Do not store passwords, private keys, or secrets in publicly accessible documentation.

---

## 11. AI-Generated Code & Third-Party Integration Governance

AI coding tools and external integrations can accelerate website development, but generated code and unfamiliar scripts still require review.

- [ ] Is AI-generated code reviewed before production use?
- [ ] Are dependencies checked before installation?
- [ ] Are external scripts obtained from trusted sources?
- [ ] Are API permissions limited to required functionality?
- [ ] Are third-party integrations reviewed periodically?
- [ ] Are scripts checked for unexpected data collection?
- [ ] Are automated deployments protected?
- [ ] Are generated configurations tested for security and compatibility?

**Fix:** Treat AI-generated code like code from any other source. Review, test, and validate it before deployment.

---

## 12. Security & Maintenance Audit Evidence

Use a consistent format to document findings.

| Field | What to document |
|---|---|
| Audit area | Security, backup, access control, etc. |
| Issue | What is wrong or missing? |
| Evidence | Screenshot, log, URL, configuration, or test result |
| Risk | Potential security or operational impact |
| Priority | Critical, High, Medium, or Low |
| Recommended action | What needs to be fixed? |
| Owner | Responsible person or team |
| Status | Open, In Progress, Fixed, or Verified |
| Validation | How the fix will be tested |
| Review date | Next review date |

### Example finding

**Issue:** Website administrator accounts do not have multi-factor authentication enabled.

**Evidence:** Administrative account security settings show password-only authentication.

**Risk:** Compromised credentials could allow unauthorized website access.

**Priority:** High.

**Recommended action:** Enable MFA for administrative accounts and review other privileged access.

**Verification:** Confirm that authorized administrators can authenticate using the configured additional factor.

---

## 13. Common Security & Maintenance Mistakes

Avoid these practices:

- Treating HTTPS as complete website security.
- Using outdated or unsupported CMS software.
- Installing plugins and scripts without reviewing their source.
- Sharing administrator credentials.
- Keeping unused accounts active.
- Storing API keys or passwords in public repositories.
- Assuming hosting backups are always sufficient.
- Never testing backup restoration.
- Ignoring domain and DNS ownership.
- Exposing sensitive configuration files.
- Ignoring security and server logs.
- Collecting unnecessary personal information.
- Treating privacy policies as generic templates that never need review.
- Making risky production changes without rollback plans.
- Ignoring website functionality after major updates.
- Assuming AI-generated code is secure without review.

---

## 14. Recommended Tools & Resources

### Security testing and monitoring

- [Google Safe Browsing](https://transparencyreport.google.com/safe-browsing/search)
- [VirusTotal](https://www.virustotal.com/)
- [Security Headers](https://securityheaders.com/)
- [Mozilla Observatory](https://observatory.mozilla.org/)
- [OWASP](https://owasp.org/)

### WordPress and CMS security

- [WordPress Security](https://wordpress.org/about/security/)
- [WordPress Hardening Guide](https://developer.wordpress.org/advanced-administration/security/hardening/)
- [WordPress Site Health](https://wordpress.org/documentation/article/site-health-screen/)

### Security standards and guidance

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [Mozilla Web Security Guidelines](https://infosec.mozilla.org/guidelines/web_security)

### Monitoring and maintenance

- [UptimeRobot](https://uptimerobot.com/)
- [Google Search Console](https://search.google.com/search-console/)
- [Google PageSpeed Insights](https://pagespeed.web.dev/)

Tool capabilities and pricing may change. Review official documentation before selecting or implementing a tool.

---

## 15. Audit Completion Criteria

This audit can be considered complete when:

- [ ] HTTPS and certificate configuration are verified.
- [ ] Important security headers are reviewed.
- [ ] CMS, themes, plugins, and dependencies are maintained.
- [ ] Administrative access and MFA are reviewed.
- [ ] Hosting, server, and DNS security are assessed.
- [ ] Malware and vulnerability monitoring are considered.
- [ ] Backup and restoration procedures are documented and tested.
- [ ] Privacy and consent practices are reviewed.
- [ ] Website availability and critical functionality are monitored.
- [ ] Maintenance responsibilities are assigned.
- [ ] Change management and rollback procedures are documented.
- [ ] Security findings are prioritized and assigned.
- [ ] Critical fixes are validated with evidence.

**Final principle:** Website security and maintenance are continuous responsibilities. A secure, well-maintained website protects users, supports business continuity, and provides a more reliable foundation for search visibility and website growth.
