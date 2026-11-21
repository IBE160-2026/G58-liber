# Digest D-faq-newsletter-push-r1-1

Topic: FAQ page, e-mail newsletter, web push for a small Norwegian skin-care clinic site.
Run date / accessed date: 2026-10-28. Budget used: 16 tool calls (6 searches, 10 fetches).
Method caveat: WebFetch returns a small-model summary of the page, not verbatim text. Quotes below are the summariser's rendering. Where a claim is legally or technically load-bearing, re-read the primary page before putting it in the PRD.

## (a) Findings

### 1. FAQ

F1. Google no longer shows FAQ rich results in Search at all. Changelog entries on the FAQPage doc page: "May 8, 2026: deprecation notice added; this feature will no longer appear in Google Search starting May 7, 2026." "June 15, 2026: FAQ rich result documentation removed; the FAQ rich result feature is no longer shown in Google Search results."
- Source: https://developers.google.com/search/docs/appearance/structured-data/faqpage (changelog section; the page text was 180k chars and only the first 100k were read, the changelog entries were in that part)
- Publisher: Google Search Central. pub_date: entries dated 2026-05-08 and 2026-06-15; page has no own "last updated", newest entry 2026-10-26. accessed 2026-10-28.
- confidence: med-high (primary source, but single fetch via summariser; the search snippet in the same run still showed older "government/health only" text, which is the cached 2023 wording).
- class: platform

F2. Earlier state (superseded by F1): Aug 2023 announcement limited FAQ rich results to well-known, authoritative government and health sites; the doc was updated 2023-09-14 to say so. Search Engine Journal had reported the 2026 removal as ending eligibility for those sites too ("appears to end", not confirmed by Google at the time of the search).
- Source: same Google page changelog (2023-09-14 entry); https://www.searchenginejournal.com/google-drops-faq-rich-results-from-search/ (secondary, only seen as search-result title/snippet, not fetched)
- Publisher: Google Search Central / Search Engine Journal. accessed 2026-10-28. confidence: high for the 2023 limit, low for the SEJ details (snippet only).
- class: platform

F3. Implication stated by Google (via search summary, not directly verified on page): structured data that is not used "does not cause problems" but has no visible effect. So FAQPage markup has no rich-result payoff for a clinic site any more. (Unverified as to exact wording; came from search-engine summary of Google doc.)
- confidence: low-med. class: guidance

F4. LocalBusiness structured data (Google doc): required properties are `address` and `name`; recommended `geo` (5+ decimals), `openingHoursSpecification`, `telephone`, `url`, `priceRange`, `department`. Use the most specific subtype. The page does not mention Google Business Profile at all; it links to "Business details" under Local features. Page last updated 2026-09-08 UTC.
- Source: https://developers.google.com/search/docs/appearance/structured-data/local-business
- Publisher: Google Search Central. pub_date 2026-09-08. accessed 2026-10-28. confidence: med-high (single fetch). class: guidance

### 2. Newsletter - law

N1. Markedsføringsloven § 15 (lovdata): in business, marketing to individuals by individually addressed electronic channels (e-mail, fax, automated voice) is prohibited without the recipient's prior consent (sam­tykke). Phone calls (oral) are excepted. "Electronic mail" includes SMS/MMS (stated in § 15 fourth paragraph). Existing-customer exception (third paragraph): no consent needed for e-mail marketing where the trader got the address in connection with a sale, but only for the trader's own goods/services similar to those the customer relationship is based on, and the customer must be offered a simple, free opt-out when the address is collected and (possibly) with each later message. Ehandelsloven § 9 applies in addition.
- Source: https://lovdata.no/lov/2009-01-09-2/§15
- Publisher: Lovdata (official consolidated law). pub_date: law 2009-01-09 nr. 2; Lovdata page showed the law as last changed by "LOV-2026-05-07-17, effective 2026-07-01" (the summariser said that is the whole-law last change; whether it touched § 15 is unknown). accessed 2026-10-28.
- confidence: med-high (one primary source, paraphrased by summariser; independent second source is below, but it is a 2018 guide).
- class: regulatory

N2. Forbrukertilsynet guidance (veiledning om markedsføring via e-post, SMS o.l., dated 2018-01-01, built on the older wording): valid consent must be voluntary, express (uttrykkelig) and informed; it should cover what type of communication, how often, from whom. Also: Forbrukertilsynet has issued prohibition decisions with tvangsmulkt of NOK 5,000 per unsolicited e-mail/SMS, upheld by Markedsrådet 2024-04-16 (MR-2024-132) against a private individual sender.
- Source: https://www.forbrukertilsynet.no/wp-content/uploads/2018/01/Veiledning-om-markedsføring-via-epost-sms-ol.pdf (seen only as a search result; NOT fetched; content taken from the search-engine summary); enforcement detail from Forbrukertilsynet decision PDFs listed in the same search (not fetched)
- Publisher: Forbrukertilsynet. pub_date 2018-01 (guidance). accessed 2026-10-28.
- confidence: low-med (search summary only; guidance is 8 years old, check for a newer version on forbrukertilsynet.no).
- class: regulatory/guidance

N3. Not obtained: GDPR consent specifics (Datatilsynet), double opt-in as practice, and unsubscribe formatting rules. Not fetched, no claim made.

### 3. Newsletter - tools and benchmarks

N4. MailerLite free plan: 250 subscribers, 2,500 emails/month, campaigns + automations + 1 landing page + signup forms, 2 seats, knowledge-base support only. First paid tier "Comfort" from $12/month per page FAQ (unclear if monthly or annual billing; not shown in grid). No date on page.
- Source: https://www.mailerlite.com/pricing
- Publisher: MailerLite (vendor). pub_date: none shown. accessed 2026-10-28. confidence: med (vendor primary for its own pricing; summariser flagged ambiguity). class: pricing
- Note: the 250-subscriber ceiling is far lower than the 1,000 I would have expected from earlier years. That is a belief from training data, not verified here; do not state it as history.

N5. Mailchimp free plan: 250 contacts, max 500 sends/month or 250/day, 1 seat, 1 audience, popup forms; NOT included: scheduling, removal of Mailchimp branding, automation flows, branded templates. Essentials price could not be read from the page (a displayed EUR 11.75/month for 12 months was a 15% discount tier for 10,000+ contacts, not the base). No date on page except footer (c) 2001-2026. Custom-coded templates can be built but need an upgrade to send.
- Source: https://mailchimp.com/pricing/marketing/
- Publisher: Mailchimp (vendor). pub_date none. accessed 2026-10-28. confidence: med. class: pricing

N6. MailerLite benchmark (median values, Dec 2024-Nov 2025, 3.6M+ campaigns, 181k accounts; published 2025-12-03, dateModified 2026-04-07): Beauty and personal care open 38.40%, click 0.95%, unsub 0.23%. Medical/dental/healthcare open 43.75%, click 2.25%, unsub 0.20%. Health and fitness open 47.81%, click 1.45%, unsub 0.30%. Vendor caveat in the article: Apple Mail Privacy Protection inflates opens. Overall click rate 2.09% (from search snippet). No "skin clinic" row; no Norway-specific data; mostly accounts of MailerLite users (vendor sample, selection bias).
- Source: https://www.mailerlite.com/blog/compare-your-email-performance-metrics-industry-benchmarks
- Publisher: MailerLite (vendor, secondary/marketing). pub_date 2025-12-03. accessed 2026-10-28. confidence: med for the numbers as MailerLite reports them, low as a predictor for a Norwegian clinic. class: benchmark

N7. Other benchmark figures (search snippets only, not fetched, vendor sources, differing methods): Omnisend 2025 Beauty and Fitness open 29.33% (overall 30.22%); NeverBounce 2025 Beauty and Personal Care 34.32% average (Brevo 25.20%); Klaviyo Health and Beauty automated flows 46.73% (flows, not campaigns; URL slug suggests older page).
- Sources: https://www.omnisend.com/blog/email-marketing-benchmarks/ ; https://www.neverbounce.com/blog/2025-email-benchmark-report ; https://klaviyo.com/blog/ecommerce-benchmarks-2021
- Publisher: vendors. accessed 2026-10-28. confidence: low (snippets). class: benchmark
- Spread of open rates across vendors is roughly 25% to 48%, driven by method (MPP inflation, sample). Do not average.

### 4. Web push

P1. iOS/iPadOS web push exists only for web apps added to the Home Screen, with a manifest `display` of `standalone` or `fullscreen`; permission prompt must follow a direct user gesture; managed per web app in Notifications settings; uses the standard Push API / Notifications API / Service Workers; no Apple Developer membership needed. Introduced with iOS/iPadOS 16.4 beta 1.
- Source: https://webkit.org/blog/13878/web-push-for-web-apps-on-ios-and-ipados/
- Publisher: WebKit (Apple). pub_date 2023-02-16. accessed 2026-10-28. confidence: high for the 2023 mechanism. class: platform

P2. caniuse data (Push API) still marks iOS Safari as partial support with the note "Requires website to first be added to the Home Screen" (latest listed iOS Safari version 27.2); desktop Safari "yes" (macOS 13 Ventura or later; supported in Safari but not WKWebView or SFSafariViewController); Chrome Android 156 yes. Notes also say old-style Safari Push Notifications existed in Safari 7.0-26.3 only.
- Source: https://raw.githubusercontent.com/Fyrd/caniuse/main/features-json/push-api.json
- Publisher: caniuse (community-maintained dataset). pub_date: current main branch, undated. accessed 2026-10-28. confidence: med-high (second independent source for the Home Screen requirement together with P1). class: platform

P3. MDN: Push API is Baseline "Widely available" (since March 2023); page last modified 2025-05-28. The compatibility table did not load, so no per-browser versions from MDN.
- Source: https://developer.mozilla.org/en-US/docs/Web/API/Push_API
- Publisher: MDN. pub_date 2025-05-28. accessed 2026-10-28. confidence: med. class: platform

P4. iOS 26 (and iPadOS 26) change: every site added to the Home Screen via Safari opens as a web app by default unless the user turns "Open as Web App" off. This lowers the barrier for the Home Screen route but does not remove the need for the user to add the site to the Home Screen first.
- Source: https://www.macrumors.com/2025/06/18/safari-changes-on-ios-26/ (seen as search result; summary only, not fetched)
- Publisher: MacRumors (secondary news). pub_date 2025-06-18. accessed 2026-10-28. confidence: low-med. class: platform

P5. EU: In Feb 2024 Apple announced it would drop Home Screen web apps in the EU (iOS 17.4 beta) and then reversed, saying it would continue to offer the existing Home Screen web apps capability in the EU (built on WebKit). Current (2026) EU status of web push could NOT be confirmed. Apple's "DMA and apps in the EU" page says nothing about web apps/web push (it mentions Oct 1, 2026 unified EU terms and iOS/iPadOS 27.2 installation changes for native apps). Norway is EEA, not EU, but Apple's DMA rules apply by EU geography; whether they apply to Norwegian devices is not established here and is probably moot (the Apple DMA changes concern the EU).
- Sources: https://www.macrumors.com/2024/02/15/ios-17-4-web-apps-removed-apple/ ; https://pushalert.co/blog/?p=2608 (both search-result only); https://developer.apple.com/support/dma-and-apps-in-the-eu/ (fetched)
- Publishers: MacRumors, PushAlert (vendor), Apple. pub_date 2024-02; Apple page undated. accessed 2026-10-28. confidence: low for 2026 status; med for the 2024 reversal. class: platform

P6. Legal basis for push in Norway: ekomloven (in force 2025-01-01) § 3-15 prohibits storing or accessing information in the user's terminal equipment without information and GDPR-valid consent; exceptions: transmission only, or strictly necessary to provide an information-society service the user explicitly requested. The text does not mention push notifications. Lovdata text fetched; push is therefore not expressly covered. Whether a push subscription (service worker plus subscription endpoint stored on device) falls under § 3-15, or whether a user-initiated permission prompt counts as the explicit request exception, is NOT settled by any source I read. Marketing content sent via push: whether it is "elektronisk post" under markedsføringsloven § 15 (message "stored until retrieved") is also not established by any source I read. This is my hypothesis only, flagged as unverified: a push marketing message is likely to need prior consent whichever way it is classified, and an explicit opt-in click satisfies the consent-style requirement.
- Source: https://lovdata.no/lov/2024-12-13-76/§3-15
- Publisher: Lovdata. pub_date law 2024-12-13 nr. 76 (in force 2025-01-01 per a search result). accessed 2026-10-28. confidence: med for the § 3-15 text; low for any push-specific conclusion. class: regulatory

## (b) Leads worth chasing

1. Datatilsynet page on newsletter / e-mail marketing and GDPR consent, plus Forbrukertilsynet's current (post-2018) page on "markedsføring via e-post" and whether it says anything about double opt-in or proof of consent.
2. Nkom or Datatilsynet guidance on § 3-15 and "lignende teknologier"; any note on push notifications and service workers.
3. Google Search Central blog or "Search Central documentation updates" post confirming the FAQ rich result removal (the changelog dates are 2026-05-08 and 2026-06-15); also any John Mueller statement on whether FAQ content still helps rankings and AI-answer surfaces.
4. WebKit blog for Declarative Web Push (iOS 18.4 era, believed from training data, unverified) and Safari 26/27 release notes on web push; Apple developer forums on EU Home Screen web apps in iOS 26/27.
5. Push opt-in rate sources with named methodology (Airship, OneSignal, Pushwoosh are vendors; look for an independent study).
6. SMS reminder rules in Norway (markedsføringsloven § 15 fourth paragraph says SMS marketing is covered; appointment reminders are service messages, not marketing; confirm in Forbrukertilsynet guidance) and SMS gateway costs in Norway.
7. Whether the 2026-07-01 change to markedsføringsloven (LOV-2026-05-07-17) touched § 15 or enforcement.
8. Datatilsynet/NAV-style health-data angle: skin clinics may be special-category data processing; a newsletter list that infers treatments may need care (not researched).
9. Booking-system built-in reminder/newsletter features (not researched).

## (c) Looked for and could not find

- Any evidence that an FAQ page reduces repeat enquiries for small service businesses (no study retrieved). Also no direct evidence of SEO value for plain FAQ content apart from the observation that the rich result is gone.
- Google Business Profile guidance from a primary source (Google's local-business structured-data page does not mention it; nothing else was fetched).
- Norwegian-specific newsletter benchmarks or evidence about value at very low subscriber counts (a few hundred). Only generic vendor benchmarks, plus free-tier limits of 250 contacts, which is a cost-side fact.
- Double opt-in as a legal requirement or recommended practice in Norway.
- Push opt-in rates and any push-specific Norwegian rule (see P6).
- Confirmation from Apple/WebKit of EU web push status in iOS 26/27.
- A fetched (not snippet) copy of the Forbrukertilsynet guidance.
- Mailchimp Essentials base price.

## (d) Contradictions and quality flags

- Google FAQ: the search-engine summary of the Google doc said eligibility is still "government and health", while the changelog on the same page says the feature was removed in May-June 2026. Resolve in favour of the changelog (newer, primary); the 'government and health' text is the 2023 wording and probably a cached or search-snippet artefact. SEJ headline claims removal; consistent with the changelog.
- Open-rate benchmarks conflict by vendor (25% to 48%); different definitions and MPP inflation. Not averaged.
- Vendor pricing pages carry no date; treat free-tier limits as "as of 2026-10-28 fetch" only. The MailerLite 250-subscriber and 2,500-email limits and the Mailchimp 250/500 limits were each seen on one page only.
- Cookie/consent sources via search mixed old § 2-7b with new § 3-15; the lovdata fetch confirms § 3-15 for the current law. One snippet claimed consent can be given through browser settings; contradicted by § 3-15 text (GDPR-valid consent required). Resolve for the lovdata text.
- Legal claims with only one independent source: N1 (lovdata only; Forbrukertilsynet 2018 guide is search-snippet and predates the current wording), P6 (single source, and silent on push). Platform claims with two sources: P1/P2 (Home Screen requirement for iOS web push). EU status single/old sources only.
- Aggregator/echo: lawinsider.com mirrors the Forbrukertilsynet guidance (not independent). Numerous vendor blogs on push and benchmarks are marketing-register; none relied on.
- Tool-reliability flag: this run's WebFetch outputs are model summaries; one search result displayed a header date of "August 11, 2026" on an article that was in fact from 2024 (iclarified), so page-header dates from aggregators are unreliable.
