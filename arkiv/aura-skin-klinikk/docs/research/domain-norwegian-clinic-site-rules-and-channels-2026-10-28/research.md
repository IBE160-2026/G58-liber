---
title: 'domain research: Rules and channels for the AURA SKIN Klinikk website (Norway)'
type: 'domain'
topic: 'Rules and channels for the AURA SKIN Klinikk website (Norway)'
decision: 'What the PRD can commit to on: prescription-treatment wording, Meta messaging from the site, local competitors, and FAQ/newsletter/push scope'
source: 'native run'
status: complete
preset: 'standard'
validation: 'normal'
claims_verified: 4
claims_unverified: 6
created: '2026-10-28'
updated: '2026-10-28'
---

# Domain research: rules and channels for the AURA SKIN Klinikk website (Norway)

**Decision this research serves:** what the PRD can commit to on four points: wording for prescription-only treatments, Meta (Messenger/Instagram) contact from the site, the local competitor picture, and the scope of FAQ, newsletter and push.

## Executive summary

**What to do.** Treat the site as a *neutral-wording, inbound-contact* site. Do not name botox or any code word. Do not show before/after images. Do not plan any outbound promotion about injectables. Link out to Messenger/Instagram instead of trying to feed them. Drop push and newsletter from v1, and keep the FAQ only as a small information page.

**Findings that drive this**

1. **Naming the drug is illegal advertising, even on the clinic's own site and social media.** The medicines regulator (DMP, formerly Legemiddelverket) says that trade names, active substances and code words such as "toksin" or "BTX" are covered, and it has fined a clinic NOK 5,000 per day [1][2]. "Rynkebehandling"-style names are not regulated as such unless they clearly reveal the drug [1], but DMP gives no approved wording, so this is an inference (confidence: medium).
2. **Cosmetic-procedure marketing has its own hard rules.** No before/after images, the medically responsible person must be named, and marketing may not be aimed at under-18s [6]. A separate provision appears to forbid directing marketing about such procedures to consumers by e-mail or SMS [6]. If that holds, it removes most of the point of a newsletter about injectables. This provision was read once through a summary and not independently verified.
3. **A web form cannot create a conversation in the clinic's Messenger/Instagram inbox.** Meta's windows open on a user action, and the Instagram API only lets an app message someone who has messaged first [10][11]. A `m.me` / `ig.me` link that the customer clicks is the supported route [10][12].
4. **Google ended FAQ rich results in 2026** (notice 2026-05-08, removed 2026-06-15) [17], and no source showed that an FAQ page cuts enquiries. Push on iPhone only works for sites installed to the Home Screen [24][25].

**Biggest caveat.** The fetch tool returned model summaries, not verbatim law text. Every regulatory claim below must be re-read on Lovdata or dmp.no before it is written into a PRD requirement. Photos sent through `m.me`/`ig.me` and the 2026 amendment to helsepersonelloven were not checked at all.

## A. Norwegian rules for treatment wording and marketing

**Medicines advertising (botulinum toxin and other prescription-only drugs).**
- Advertising prescription-only medicines to the public is banned (legemiddelforskriften § 13-4) [2]. DMP's guide for aesthetic clinics (updated 2025-11-11) says the ban covers trade names, active substances, code words and images of the drug, on websites and social media, and that "toksin", "BTX" and "bot.tox" are unlawful code words [1]. Campaigns and discounts on botulinum toxin treatment, and telling existing customers which drug the clinic uses, are also covered [1]. (Confidence: high on the DMP text; the guide's body was read through a summary, so status of the code-word list is *unverified* in the ledger.)
- Enforcement is real: DMP's 2025-04-23 decision against Lead Partner AS ordered a stop and set tvangsmulkt of NOK 5,000 per day; the content that was unlawful included positive statements about the drug, lists of clinics offering it and prices for it [2]. About 14 botulinum-toxin decisions have been listed since September 2022 (titles only, one read in full) [3].
- What is allowed: price lists "så lenge de ikke inneholder påstander om legemiddelet", and links to leaflets that only someone who actively searches would find [1]. DMP also writes that the medicines rules "regulerer ikke markedsføring av behandlinger i seg selv, med mindre markedsføringen tydelig viser hvilke legemidler som brukes" [1]. A neutral name such as "rynkebehandling" therefore looks permissible, but it is an inference (medium). One real clinic page uses it and adds the disclaimer "Grunnet legemiddelforskriften har vi ikke lov å markedsføre reseptpliktige legemidler mot allmennheten" [9].
- **Disputed:** one source (a NORFEM memo, reported by the verifier) says brand names are allowed in price lists, while DMP's text says price lists must make no claims about the drug. Follow DMP; ask DMP before using any drug name in a price list.

**Who may do the treatments.**
- Cosmetic injections and treatments can only be performed by health personnel (helsepersonelloven § 4 a), and not on under-18s without medical justification (§ 4 b); both in force since 2022-07-01 [5]. Verified, with the nuance that § 4 a covers only procedures that can cause serious harm [5]. Only a doctor can prescribe botulinum toxin; a nurse injects as the doctor's assistant [4].

**Marketing of cosmetic procedures** (*Forskrift om markedsføring av kosmetiske inngrep*, FOR-2005-07-01-749, last amended 2023-03-21) [6]. Verified on Lovdata:
- § 3: covers procedures in skin and subcutaneous tissue, including injections and fillers.
- § 4: must name the medically responsible person and how to contact the business; must not downplay risk; must not be designed so it can be perceived as aimed at under-18s (a duty, not an absolute ban).
- § 5: no pre- and post-operative images. Whether after-only images are allowed was not established.
- § 6: no credit offers. § 9: Statsforvalteren and Statens helsetilsyn supervise.
- § 7 (*unverified, read once via summary*): forbids directing marketing enquiries about cosmetic procedures to consumers through individual channels such as e-mail and SMS.

**Fillers** are medical devices, so the medicines ban does not apply, but the cosmetic-procedures forskrift does. A single search summary says advertising is allowed if claims are documented and follow the manufacturer's instructions [7][8] (low confidence).

**Not covered:** lasers and chemical peels, Forbrukertilsynet and Helsetilsynet enforcement, and what the helsepersonelloven amendment in force 2026-07-01 changes.

## B. Contacting the clinic through Meta

- **Link-based entry works; a form-to-inbox push does not.** `m.me/<page>` and `ig.me/m/<handle>` open a thread with the Page [10][12]; the link format itself comes from vendor pages only [13]. `ig.me` does not work on Instagram Web [12]. The Instagram Messaging API lets an app send to a user only after that user has messaged the account [11] (high). For Messenger, the policy page says the window opens on a user action and does not list a form submission [10]; "form cannot push" is therefore an inference from the window rule (verified with that nuance).
- **Windows.** 24 hours as standard, 7 days after a click-to-message ad [10][11]. A Human Agent tag adds 7 days for manual replies but needs app review [10][11]. These rules govern the API. How Meta Business Suite enforces them for a clinic replying by hand was not established.
- **Chat plugin.** The embeddable Messenger chat plugin is *reported* removed on 2024-05-09 [14], but only vendor blogs say so and Meta's changelog shows no removal entry. Do not build on it (unverified).
- **WhatsApp as an alternative.** Cloud API billing is per message since 2025-07-01. From 2026-10-01 service messages are chargeable, with the first 1,000 per number per month free (stated on the main pricing page only) [15][16]. Norway's rate was not retrieved. Whether the free WhatsApp Business app is affected, and the terms of `wa.me` links, were not checked.
- **Gaps that matter for the PRD:** whether customers can send photos through `m.me`/`ig.me` and whether those reach the Business Suite inbox, App Review / Business Verification requirements, and any Meta consent notice are all unverified.

## C. Local competitors and what they show

> **Scope error:** this dimension was run for the Molde / Romsdal area. The clinic is at Bøvegen 60, 4260 Salhus (Karmøy), not in Haugesund as earlier notes said. The findings show what clinics in the industry publish on their sites, but they are not a competitor analysis for the clinic's market. Dimensions A, B and D are Norway-wide and unaffected. Redo C for Karmøy before using it for positioning (recommendation 7).

Observed first-hand on 2026-10-28 (fetch-based; absences mean "not found in page text", not proven absence). Sample is four sites.

| Clinic | Prices on site | Booking | FAQ | Results / before-after | Newsletter | Contact seen |
|---|---|---|---|---|---|---|
| Skin Clinic Molde/Kristiansund [27] | Yes, homepage and /priser (e.g. filler 1 ml 4 500 kr, wrinkle treatment 3 areas 4 850 kr) | bestille.no | Not found | Not found | Not found | Phone, e-mail |
| SE Hudklinikk Molde [28] | No | EasySalon | Not found | Not found | Not found | Phone, e-mail, Instagram |
| Velbehag (chain; Molde presence unverified) [29] | Not on homepage | Own page | Yes (10 Q) | Yes (/resultater, photos) | Not found | Phone, e-mail |
| Medderma (Oslo + Molde) [30] | Separate price list | Consultation page | Yes (8 Q) | Not found | Not found | Contact page |

- Only one of four shows prices openly. Skin Clinic's from-prices name no drug, which fits DMP's price-list allowance in section A.
- No site showed a contact form or a Messenger link on fetched text; the fetcher may miss chat widgets.
- Velbehag's results page uses photos. That is the pattern section A says to avoid for injectables, and the same name (Velbehag Frogner AS) appears in a 2025-05-09 DMP "ulovlig reklame" decision listed by title only [3]. Do not copy it.
- EasySalon is free, with paid plans from kr 199/month excluding VAT [31] (price date unknown). Bookis and Timma pricing could not be retrieved.
- **Not answered:** Google rankings for "hudpleie Molde" (the search tool returns summaries, not result pages), public review wording, Norwegian data on Messenger vs forms, and any clinic in Åndalsnes or Fræna/Elnesvågen.

## D. FAQ, newsletter, push

- **FAQ.** FAQ rich results no longer appear in Google, including for government and health sites [17] (verified against Google's changelog). No study was found showing that an FAQ page reduces repeat enquiries or helps ranking. Google's LocalBusiness structured-data page (updated 2026-09-08) requires name and address and does not mention Google Business Profile [18]. Two of four competitors have an FAQ [29][30].
- **Newsletter, law.** Markedsføringsloven § 15 requires prior consent for marketing e-mail and SMS to individuals. The existing-customer exception covers only the trader's own similar goods and needs a free opt-out [19] (single primary source, via summary). Forbrukertilsynet's guidance found is from 2018 and was seen only as a search snippet [20]. Combined with § 7 of the cosmetic-procedures forskrift (section A, unverified), a newsletter promoting injectables looks non-compliant.
- **Newsletter, cost and benchmarks.** MailerLite free: 250 subscribers and 2,500 e-mails a month [21]. Mailchimp free: 250 contacts and 500 sends a month, no automation or scheduling [22]. Both pages are undated. MailerLite's own benchmark gives beauty and personal care 38.4% opens and 0.95% clicks [23]; this is a vendor sample inflated by Apple Mail Privacy Protection. No Norwegian data.
- **Push.** On iOS/iPadOS, web push only works for a site added to the Home Screen as a web app, per WebKit (2023) and caniuse [24][25]. Apple's 2026 EU position is unverified [32]. Ekomloven § 3-15 requires GDPR-valid consent for storing or accessing data on a device but does not mention push, and no source settles whether § 3-15 or § 15 governs push messages [26]. No push opt-in rate data was found.

## Cross-dimension insights

1. **The rules push the whole site toward inbound contact.** The medicines ban, the cosmetic-marketing rules (including § 7, if confirmed) and Meta's user-first messaging window all restrict clinic-initiated promotion. The compliant default is the customer starting the contact, through a booking or request form, a phone number, or an `m.me`/`ig.me` link.
2. **Competitor patterns collide with the rules.** The trust features the stronger competitor shows (a results page with photos) fall under the before/after ban for injectables. What can be copied safely is the price page without drug names, an FAQ, and a named responsible doctor.
3. **Low volume weakens the extras.** A newsletter capped at 250 free subscribers, push that needs a Home Screen install, and an FAQ with no rich-result payoff all cost build effort for little evidenced return at this clinic's size.

## Contrary evidence

The red-team pass was not run (`red_team = off`, validation `normal`). The strongest counter-argument to the main recommendation is DMP's own scoping sentence: if "rynkebehandling" does not clearly reveal the drug, neutral treatment names may be fine and even a modest newsletter about *non-injectable* skincare may be lawful. That is why the newsletter recommendation below is "defer", not "never".

## Recommendations

Bound to the PRD (`prd/prd.md`, v2) and its open questions. Confidence in brackets.

1. **Wording rule for the PRD (NFR/content rule).** Ban drug names, active substances and code words anywhere on the site and in the clinic's social posts; use neutral treatment names; show prices without claims about the drug; state the medically responsible person and contact details; no before/after images for any injection or filler treatment. [high on the ban, medium on neutral names]. Before launch, ask DMP or have the clinic's doctor sign off the final treatment texts.
2. **Contact channel (replaces any "forward form to Messenger" idea).** Provide `m.me` and `ig.me` buttons plus a normal request form/e-mail/phone; do not promise that form submissions appear in the Meta inbox. Test with the clinic's real Page that photos can be sent and received before relying on this for photo enquiries. [high that form push is unsupported; photo support unknown]
3. **FR-21 (FAQ).** Keep as a small, plain information page (who performs treatments, cancellation, what to expect), not for SEO. Drop FAQPage markup. [medium]
4. **Newsletter.** Defer from v1. If it comes back, limit it to non-injectable skincare and opt-in with a free unsubscribe, after § 7 of the forskrift and § 15 are re-read in full. [medium; rests on unverified claims]
5. **Push.** Drop from v1. Use SMS and e-mail booking confirmations and reminders (service messages), which were not researched for rules and cost. [medium]
6. **NFR-10 (search visibility).** Add LocalBusiness structured data (name, address, opening hours, phone) and a verified Google Business Profile; do not count on FAQ rich results. [medium]
7. **Competitive positioning.** Open price display like Skin Clinic Molde is a differentiator against three of four competitors, if the clinic agrees to publish prices. [low-medium, n=4]

## Open questions

| Question | What would answer it |
|---|---|
| Is § 7 of FOR-2005-07-01-749 as read, and does it also cover SMS booking reminders? | Read Lovdata text; ask Helsetilsynet or the clinic's doctor |
| What does the 2026-07-01 helsepersonelloven amendment (LOV-2026-06-19-42) change? | Lovdata change history; regjeringen.no |
| Is the NORFEM / DMP conflict on brand names in price lists settled? | Ask DMP directly (it advises but does not pre-approve) |
| Do lasers and chemical peels fall under § 4 a, and who may perform them? | Separate domain run; Strålevernet rules for lasers |
| Do photos sent via `m.me`/`ig.me` reach the Business Suite inbox? Is Business Verification needed? | Test with the clinic's Page; Meta Business Help inbox article |
| Is the chat plugin truly gone? | Meta Messenger changelog or Business Help |
| What does Norway pay per WhatsApp message, and is the free Business app affected? | Meta rate card CSV; WhatsApp Business terms |
| Which Molde clinics rank for "hudpleie Molde", and what do reviews say? | Manual incognito Google check from Molde; Google Maps reviews |
| Does iOS web push work in the EEA in 2026? | WebKit / Apple developer documentation |
| Is push marketing governed by ekomloven § 3-15 or markedsføringsloven § 15? | Nkom or Datatilsynet guidance |

## Source appendix

| # | Supports | Publisher | Pub date | Accessed | Confidence |
|---|---|---|---|---|---|
| 1 | DMP guide for aesthetic clinics: drug-name ban, code words, price lists, scoping sentence | [DMP](https://www.dmp.no/tilvirkning-import-og-salg/reklame-for-legemidler/informasjon-for-klinikker/veileder-for-estetiske-klinikker) | 2025-11-11 | 2026-10-28 | high (summary read) |
| 2 | Lead Partner AS decision, § 13-4, NOK 5,000/day | [DMP](https://www.dmp.no/globalassets/documents/tilvirkning-import-og-salg/reklame/brudd-pa-reklamereglene/2025/25_07558-4-vedtak-om-stans-av-ulovlig-reklame-og-tvangsmulkt.pdf) | 2025-04-23 | 2026-10-28 | high |
| 3 | List of DMP advertising decisions (titles only) | [DMP](https://www.dmp.no/tilvirkning-import-og-salg/reklame-for-legemidler/tilsyn-og-sanksjonsmuligheter/vedtak-om-brudd-pa-reklameregelverket) | latest 2025-06-03 | 2026-10-28 | medium |
| 4 | Only doctors prescribe botulinum toxin; nurse as assistant | [Helsedirektoratet](https://www.helsedirektoratet.no/lov-og-forskrift/helsepersonelloven/rekvirering-og-bruk-av-botulinumtoksin-botox) | 2022-07-05 | 2026-10-28 | high |
| 5 | Helsepersonelloven §§ 4 a, 4 b, in force 2022-07-01 | [Lovdata](https://lovdata.no/dokument/NL/lov/1999-07-02-64) | 2022-07-01 | 2026-10-28 | high |
| 6 | Forskrift om markedsføring av kosmetiske inngrep §§ 3–9 | [Lovdata](https://lovdata.no/dokument/SF/forskrift/2005-07-01-749) | 2023-03-21 | 2026-10-28 | high (§ 7 unverified) |
| 7 | DMP guidance on marketing of cosmetic procedures (drugs and devices) | [DMP](https://www.dmp.no/medisinsk-utstyr/omsetning/reklame-for-medisinsk-utstyr/veiledning-om-markedsforing-av-kosmetiske-inngrep) | 2023-09-08 | 2026-10-28 | medium-high |
| 8 | Fillers as devices, advertising allowed with documented claims | [DMP](https://www.dmp.no/medisinsk-utstyr/omsetning/reklame-for-medisinsk-utstyr/veiledning-om-reklame-for-fillere) | unknown | 2026-10-28 | low (search summary only) |
| 9 | Example clinic wording and disclaimer | [Sommerro booking page](https://vestkantbadet.try.be/items/671662b9c9fc8199f8003a8f/rynkebehandling-june) | undated | 2026-10-28 | high that the wording exists |
| 10 | Messenger policy: 24h window, tags, window openers | [Meta for Developers](https://developers.facebook.com/documentation/business-messaging/messenger-platform/policy) | not shown | 2026-10-28 | medium-high |
| 11 | Instagram Messaging API: user must message first; windows; permissions | [Meta for Developers](https://developers.facebook.com/documentation/instagram-platform/instagram-api-with-instagram-login/messaging-api.md) | not shown | 2026-10-28 | high |
| 12 | `ig.me` links, not on Instagram Web | [Meta for Developers](https://developers.facebook.com/documentation/business-messaging/instagram-messaging/features/ig-me-links) | not shown | 2026-10-28 | medium (snippet) |
| 13 | `m.me` link format (vendors) | [Trengo](https://trengo.com/blog/facebook-messenger-link-generator) | undated | 2026-10-28 | medium |
| 14 | Chat plugin reported removed 2024-05-09 | [Chative](https://chative.io/blog/meta-remove-facebook-messenger-chat-plugin/) | 2024 | 2026-10-28 | low (vendor, no Meta confirmation) |
| 15 | WhatsApp Cloud API per-message pricing; service messages chargeable from 2026-10-01 | [Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing) | not shown | 2026-10-28 | high on dates, rate unknown |
| 16 | WhatsApp non-template message pricing | [Meta for Developers](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing/non-template-messages) | 2026-09-08 | 2026-10-28 | high on structure |
| 17 | Google FAQ rich results deprecated and removed | [Google Search Central](https://developers.google.com/search/docs/appearance/structured-data/faqpage) | 2026-06-15 | 2026-10-28 | high |
| 18 | LocalBusiness structured data requirements | [Google Search Central](https://developers.google.com/search/docs/appearance/structured-data/local-business) | 2026-09-08 | 2026-10-28 | medium-high |
| 19 | Markedsføringsloven § 15, consent and existing-customer exception | [Lovdata](https://lovdata.no/lov/2009-01-09-2/§15) | 2009-01-09 | 2026-10-28 | medium-high (summary) |
| 20 | Forbrukertilsynet guidance on e-mail/SMS marketing | [Forbrukertilsynet](https://www.forbrukertilsynet.no/wp-content/uploads/2018/01/Veiledning-om-markedsføring-via-epost-sms-ol.pdf) | 2018-01 | 2026-10-28 | low (snippet) |
| 21 | MailerLite free plan limits | [MailerLite](https://www.mailerlite.com/pricing) | undated | 2026-10-28 | medium |
| 22 | Mailchimp free plan limits | [Mailchimp](https://mailchimp.com/pricing/marketing/) | undated | 2026-10-28 | medium |
| 23 | Email benchmarks (beauty, medical) | [MailerLite](https://www.mailerlite.com/blog/compare-your-email-performance-metrics-industry-benchmarks) | 2025-12-03 | 2026-10-28 | medium as reported, low as predictor |
| 24 | iOS web push requires Home Screen web app | [WebKit](https://webkit.org/blog/13878/web-push-for-web-apps-on-ios-and-ipados/) | 2023-02-16 | 2026-10-28 | high for 2023 mechanism |
| 25 | caniuse Push API: iOS partial, Home Screen needed | [caniuse](https://raw.githubusercontent.com/Fyrd/caniuse/main/features-json/push-api.json) | undated | 2026-10-28 | medium-high |
| 26 | Ekomloven § 3-15 consent for device access | [Lovdata](https://lovdata.no/lov/2024-12-13-76/§3-15) | 2024-12-13 | 2026-10-28 | medium (text), low for push |
| 27 | Skin Clinic Molde: prices, booking, contact | [skin-clinic.no](https://skin-clinic.no/) | undated | 2026-10-28 | high |
| 28 | SE Hudklinikk Molde | [sehudklinikk.no](https://www.sehudklinikk.no/) | undated | 2026-10-28 | high |
| 29 | Velbehag: FAQ, results page, trust features | [Velbehag](https://velbehagklinikk.no/) | undated | 2026-10-28 | high for presence |
| 30 | Medderma: consultation-first, FAQ, price list | [Medderma](https://medderma.no/behandlinger) | undated | 2026-10-28 | medium-high |
| 31 | EasySalon pricing | [EasySalon](https://www.easysalon.no/priser) | undated | 2026-10-28 | medium |
| 32 | Apple EU web app status | [Apple](https://developer.apple.com/support/dma-and-apps-in-the-eu/) | undated | 2026-10-28 | low (silent on web push) |

Verification files: `digests/V-rules-verify.md` and `digests/V-platform-verify.md` hold the independent checks behind the verified statuses above.

## Staleness map

Computed with `recon_kit.py staleness`. The tool measures from publication date; for regulatory and policy claims the pack requires "verify current on every load-bearing claim", so those windows run from the access date, 2026-10-28.

| Claim class | Window | Re-check by |
|---|---|---|
| Meta messaging policy (24h window, user-first rule) | 1 month | 2026-11-28 |
| Chat plugin status (unverified) | 1 month | 2026-11-28 |
| Google FAQ rich results | 6 months | 2026-12-15 |
| iOS web push (unverified) | 6 months | 2027-04-28 |
| Regulatory claims (DMP guide, forskrift, helsepersonelloven, markedsføringsloven) | 6 months, from access date | 2027-04-28 |
| WhatsApp pricing | 6 months | 2027-03-08 |
| Vendor pricing (MailerLite, Mailchimp, EasySalon) | 6 months | 2027-04-28 |
| Competitor landscape | 18 months | 2028-04-28 |
| Email benchmarks | 24 months | 2027-12-03 |

**Earliest re-check: 2026-11-28 (Meta messaging policy).** The unverified regulatory claims (§ 7, § 15, DMP code words) should be resolved before launch rather than waiting for the re-check date.
