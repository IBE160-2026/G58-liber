# Digest B-meta-r1-1: Meta messaging from a small-business website (as of 2026-10-28)

Accessed date for all items: 2026-10-28. Tool calls used: ~16 (slightly over budget). Meta docs pages returned no visible "last updated" dates through the fetcher, so pub_date is "not shown" unless stated. Fetcher output is an LLM summary of the page (not raw text), so quotes are second-hand; confidence adjusted accordingly.

## (a) Findings

### Opening a conversation from a website

1. Claim: m.me links (m.me/<PageUsername>, optional ?ref=) open a Messenger thread with the Page; they are still available.
   - Sources: (primary-adjacent) https://developers.facebook.com/documentation/business-messaging/messenger-platform/policy (lists "click m.me or ig.me ref link on an existing thread" as window-opening action; does not itself define the link format). Format/ref details only from third parties: https://trengo.com/blog/facebook-messenger-link-generator, https://sleekflow.io/en-sg/blog/messenger-link, https://u2l.ai/tools/messenger-link-generator.
   - Publisher: Meta (policy page) / vendors (format). pub_date: not shown. confidence: med (format from vendors; Meta's own m.me reference page not retrieved). class: technical.
   - Note: ONLY ONE official source for the existence of m.me as a supported entry point, and it is indirect. Needs a second official page (Meta "m.me links" doc or Business Help).

2. Claim: ig.me links are officially documented: format ig.me/m/<USERNAME>, optional referral tag; redirects to a new or existing thread; a click into an existing conversation counts as customer-initiated contact and opens the standard window; webhook needs `messaging_referral` subscription for referral tracking; NOT supported on Instagram Web.
   - Source: https://developers.facebook.com/documentation/business-messaging/instagram-messaging/features/ig-me-links (seen via search snippet only, page not fetched) ; second corroboration: Messenger policy page above lists "ig.me ref link" among window openers.
   - Publisher: Meta for Developers. pub_date: not shown. confidence: med (snippet only). class: technical.
   - Implication: on desktop browsers (Instagram Web) ig.me may not work; unverified how it behaves for a visitor with no Instagram app. LEAD.

3. Claim: The Messenger/Facebook Chat Plugin (formerly Customer Chat Plugin; embeddable chat bubble on a site) was reported shut down on 9 May 2024; guest mode was disabled earlier (visitors had to log in to Facebook). m.me links remain.
   - Sources (all third party, probably echoing one Meta notice): https://respond.io/help/facebook-messenger/facebook-chat-plugin ; https://chative.io/blog/meta-remove-facebook-messenger-chat-plugin/ ; https://www.tidio.com/blog/facebook-live-chat-integration/ (2026 article; says old guides still describe a plugin-code flow that now does nothing).
   - Publishers: respond.io, Chative, Tidio (vendors). pub_date: 2024 (respond.io/Chative); Tidio 2026 (exact date not shown). confidence: med (several vendors agree but they likely echo one upstream; NO Meta primary confirmation retrieved). class: policy.
   - Meta changelog archive (https://developers.facebook.com/docs/messenger-platform/changelog/archive, fetched) lists only Chat Plugin entries up to 4 Aug 2020 (v8.0 rename to Facebook Chat Plugin) and NO removal entry. The archive appears to stop before 2024, so absence is not evidence either way.
   - Meta web-plugins reference page (https://developers.facebook.com/docs/messenger-platform/reference/web-plugins/) fetched: did NOT cover the chat plugin at all in the extract (only mentioned m.me in the `messaging_referrals` event description).

4. Claim: "Send to Messenger" website widgets were reportedly deprecated on 30 Sep 2024.
   - Source: https://community.manychat.com/product-updates/deprecation-of-send-to-messenger-website-widgets-3988 (snippet only). Publisher: ManyChat (vendor). confidence: low-med. class: policy. Single source.

### Pushing a web form into the Page inbox via API

5. Claim (Instagram): The Instagram Messaging API only allows an app to message an Instagram user AFTER that user has sent the professional account a message: "Only after an Instagram user has sent your app user's Instagram professional account a message can your app send a message to the Instagram user." The Human Agent tag does not change this.
   - Source 1: https://developers.facebook.com/documentation/instagram-platform/instagram-api-with-instagram-login/messaging-api.md (fetched). Source 2 (consistent, via search snippets): https://developers.facebook.com/documentation/business-messaging/messenger-platform/policy and Human Agent Escalation page https://developers.facebook.com/documentation/business-messaging/instagram-messaging/features/human-agent-escalation (snippet only).
   - Publisher: Meta for Developers. pub_date: not shown. confidence: high. class: policy/technical.
   - Consequence: a website form cannot create an Instagram DM to a person who never DMed the account.

6. Claim (Messenger): Messages outside the standard window generally require a message tag, utility messaging, marketing messages or sponsored messages; one-time notification requires the user to have "explicitly requested" a follow-up. The policy page does not state a sentence "you cannot message a user who never contacted the Page", but the window model (window opens only on a user action) implies it.
   - Source: https://developers.facebook.com/documentation/business-messaging/messenger-platform/policy (fetched) + https://developers.facebook.com/docs/messenger-platform/policy/policy-overview/ (fetched; same content). Same publisher/page lineage, so effectively ONE official source for the Messenger case. confidence: med-high. class: policy.
   - Unverified: whether a website-form submission can legitimately be "user action" that opens a window. The listed opening actions are: message sent, CTA click (e.g., Get Started), starting chat through a plugin, clicking an m.me/ig.me ref link on an existing thread, reacting. A form post is not listed. Treat as NOT supported.

7. Claim: Instagram messaging API permissions: `instagram_business_basic` and `instagram_business_manage_messages`. Advanced Access needed "if your app serves Instagram professional accounts you don't own or manage"; Standard Access suffices for accounts you own/manage or have added in the App Dashboard. The fetched extract did not mention App Review or Business Verification (not covered, not "not required"). Human Agent tag requires applying for the Human Agent permission and passing app review (via search snippet of Send API reference; not fetched).
   - Source: https://developers.facebook.com/documentation/instagram-platform/instagram-api-with-instagram-login/messaging-api.md. confidence: med. class: technical.
   - Implication: building any custom integration means a Meta app + tokens + webhook infrastructure for a small clinic; for a single account owned by the developer's client Standard Access might suffice (unverified for production use without review).

### Windows, tags and what remains allowed

8. Claim: Standard messaging window = 24 hours for most user actions; up to 7 days after first message following a Click-to-Messenger or Click-to-Direct ad. Messages within window may include promotional content.
   - Source 1: https://developers.facebook.com/documentation/business-messaging/messenger-platform/policy (fetched). Source 2: https://developers.facebook.com/documentation/instagram-platform/instagram-api-with-instagram-login/messaging-api.md (fetched; states 24h and ad 7 days for IG). Two official pages. confidence: high. class: policy.

9. Claim: Human Agent tag lets a business reply manually to user messages "within a separate 7-day period". Restricted to cases a human must resolve (e.g., after hours support, issues needing more than 24h); automated/unrelated content disallowed; requires the Human Agent permission through app review (permission/review detail from search snippet of Send API reference only).
   - Sources: policy page (fetched) + IG messaging API page (fetched, "separate 7-day Human Agent window"). confidence: high on 7 days; med on the permission/review requirement (snippet). class: policy.
   - Does NOT apply to the clinic replying by hand inside Meta Business Suite inbox: that is a first-party UI, not the API. UNVERIFIED how Business Suite itself enforces the 24h/7-day windows for manual replies (not found). LEAD.

10. Claim: One-time notification: lets a Page ask for one follow-up message after the window; token usable once, expires within 1 year; not available for Instagram. Message tags: "important and personally relevant 1:1 updates" for approved use cases only; misuse may restrict sending. Some tags Messenger-only. Sponsored Messages can be sent outside window and be promotional, not available for IG.
    - Source: policy page (fetched). One official source (the Instagram exclusion also appears in search-snippet of same page). confidence: med-high. class: policy.
    - Recurring notifications: NOT covered in fetched policy page and not found in the changelog archive. Status unverified (my background belief that it was changed/removed is unsupported this run).

11. Claim: Automated bots must respond to user input within 30 seconds; violations unfixed after 7 days may limit sending.
    - Source: policy page (fetched). confidence: med. class: policy. Irrelevant for manual replies; relevant only if bot used.

12. Claim: Marketing Messages for Messenger exist as a way to send outside the window, but the fetched policy page gives no definition, rates or eligibility.
    - Source: policy page (only a link). confidence: low. class: policy/pricing. LEAD.

### Photos

13. Claim: Whether customers can send photos via m.me/ig.me threads and whether the clinic receives them in Business Suite inbox: NOT verified in this run. Only verified: an app can SEND images (png, jpeg; 8 MB), audio, video, PDF (25 MB) via the Instagram API; the fetched doc did not specify attachment types users can send to the app.
    - Source: https://developers.facebook.com/documentation/instagram-platform/instagram-api-with-instagram-login/messaging-api.md. confidence: low for the question asked. class: technical.
    - Meta Business Help inbox article surfaced but not read: https://www.facebook.com/business/help/294426838452244 ("Manage messages with Inbox in Meta Business Suite"). LEAD.

### WhatsApp and pricing

14. Claim: WhatsApp Business PLATFORM (Cloud API) pricing is per delivered message since 1 July 2025; user-to-business messages are free; categories: marketing, utility, authentication (templates), service and Meta Business Agent (non-template). Customer service window = 24h, reset by each user message; outside it only templates. Free entry point window (Click-to-WhatsApp ads, Android/iOS) up to 7 days, messages free.
    - Source 1: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing (fetched). Source 2: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing/non-template-messages (fetched). confidence: high. class: pricing. pub_date: not shown.

15. Claim: From 1 October 2026 service messages become chargeable per message ("have not been charged since November 1, 2024"), with a first 1,000 free service messages per business phone number per month (stated on the main pricing page; the non-template page did not mention the free tier, see contradictions). Utility messages sent within an open service window also become charged from 1 Oct 2026. Businesses without a payment method on file by 30 Sep 2026 will have service messages stopped. Service rates equal utility/authentication rates, vary by market, no volume tiers. Norway sits in the "Rest of Western Europe" region; the actual NOK/EUR/USD rate was NOT retrieved (only in linked CSV/PDF rate cards).
    - Sources: both pages above (fetched). Non-template page includes "as of September 1, 2026" and "September 8, 2026" dates, so its content dates from at least early Sept 2026. confidence: high on dates/structure; rate unknown. class: pricing.
    - Applies to API/Cloud API use. The pages do NOT address the free WhatsApp Business app (manual use on phone); whether the app is free was not established from Meta primary. LEAD.

16. Claim: wa.me click-to-chat links: NOT researched in this run (no source retrieved). Unresolved.

### GDPR/privacy

17. Not found. No Meta requirement on consent/notice for linking to Messenger from a website was retrieved. Only a vendor note (Zenvia) that a notice may appear to the user that the Page can see them when starting a chat via m.me. No claim made. LEAD: Meta Messenger Platform data-use / Developer Policy; Meta Business Tools Terms; Norwegian Datatilsynet on Meta.

## (b) Leads worth chasing

- Meta Business Help article on Inbox (https://www.facebook.com/business/help/294426838452244): what attachments the inbox receives, any 24h/7-day enforcement on manual replies.
- Official m.me doc: https://developers.facebook.com/documentation/business-messaging/messenger-platform/discovery/m-me-links (URL guessed, unverified; search for it).
- ig.me doc fetch in full: https://developers.facebook.com/documentation/business-messaging/instagram-messaging/features/ig-me-links
- Official Meta statement on Chat Plugin end (9 May 2024): search Meta Business Suite help "Facebook chat plugin" or developer community announcement; and ManyChat's Sept 2024 widget notice.
- Meta Business Messaging changelog: https://developers.facebook.com/documentation/business-messaging/instagram-messaging/changelog and https://developers.facebook.com/docs/messenger-platform/changelog/ (newer changelog; not read).
- WhatsApp rate card for Norway (CSV/PDF linked from pricing page), and WhatsApp Business app terms (wa.me, free manual use, broadcast limits).
- Messenger Marketing Messages (eligibility, price) and Human Agent Escalation page for IG.
- Click-to-Messenger/Click-to-Direct ads as an official "form-less" funnel (7-day window).
- Whether Meta Business Suite supports a website-embedded "contact form -> inbox" natively (none found).
- Developer forum thread "Please reconsider removing the free 24-hour service window" (https://developers.facebook.com/community/threads/1328420532772816/): lead only, shows developer reaction to Oct 2026 WhatsApp change.

## (c) Looked for and not found

- Meta primary page confirming Chat Plugin removal and date.
- Official statement that customers can attach photos in m.me/ig.me conversations, size limits for inbound user photos, and display in Business Suite.
- Messenger Platform m.me doc (format, ref, limits).
- wa.me click-to-chat official constraints.
- Marketing message prices for Norway (WhatsApp or Messenger).
- Recurring notifications current status.
- GDPR/consent requirements from Meta for links to Messenger.
- Page dates ("last updated") on any Meta developer doc; the fetcher showed none.
- Whether Business Verification / App Review is required for Instagram messaging with own-account Standard Access.

## (d) Contradictions and caveats

- Free-tier detail: the main WhatsApp pricing page says the first 1,000 service messages per phone number per month are free from 1 Oct 2026; the non-template-messages page extract did not mention any free tier (it said only "Meta will charge on a per-message basis for all service messages"). A search snippet also asserted the 1,000 free tier. Likely an extraction omission; main pricing page treated as authoritative but flag for re-check. Also an older WhatsApp FAQ (per-conversation model, 1,000 free service conversations) is outdated by recency.
- Chat plugin: Meta's changelog archive shows no removal entry and the web-plugins reference page extract did not mention the chat plugin, while vendors uniformly state it ended 9 May 2024. Resolve by recency/publisher quality -> unresolved; vendor consensus plausibly one upstream. Treat as "reported removed, not confirmed from Meta".
- Tidio's phrase that m.me is "the only native option Meta still supports" is a vendor characterization; not adopted.
- Fetcher paraphrase reliability: the WhatsApp non-template page extract speculated ("based on that wording") that person-sent replies are charged service messages from 1 Oct 2026; this applies to Cloud API/Platform, not confirmed for the Business app.
