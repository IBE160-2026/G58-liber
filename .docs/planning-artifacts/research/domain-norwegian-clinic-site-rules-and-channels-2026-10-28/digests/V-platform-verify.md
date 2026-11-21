# V-platform-verify (V4-V7)

Run date: 2026-10-28. Tool budget used: ~10. The fetch tool returns model-processed summaries of pages, not verbatim text; "quotes" below are as returned by the tool and are not guaranteed character-exact.

## V4 - Messaging only after user messages first (24h standard messaging window)
**Verdict: verified (core rule); one nuance.**
- Evidence (Meta policy page, via fetch summary): "For most user actions, it lasts 24 hours." Window is opened by e.g. "User sends a message to the Page", clicking a CTA such as Get Started, reacting to a message, plugin-started conversations, certain m.me/ig.me link clicks. Click-to-Messenger/Direct ads: "may last up to 7 days from that message."
- Outside the window: message tags ("approved use cases"), Sponsored Messages (not on Instagram), One-time notifications (only after the user asks for a follow-up; not on Instagram), private replies (one message, within 7 days of a comment). Utility Messaging and Marketing Messages are linked but not described.
- The page does not state a direct rule for "business messages a user who never messaged first"; that is inferred from the window design. No Meta text found saying a website form submission opens a conversation. A website form is not in the list of window-opening actions (inference, not a quote).
- URL: https://developers.facebook.com/documentation/business-messaging/messenger-platform/policy.md (also https://developers.facebook.com/docs/messenger-platform/send-messages)
- Publisher: Meta for Developers. Date: no last-updated shown on page (changelog entries go to April 2026).
- Correction/nuance: do not say "only after user messaged first, full stop". Exceptions exist (7-day ad window, tags, OTN, private replies, sponsored messages, Marketing/Utility messaging). A website form submission still does not open a window.

## V5 - Messenger customer chat plugin removed May 2024
**Verdict: partly verified - only third-party sources; Meta primary source NOT found. Treat as unverified at primary level.**
- Evidence: Third-party blogs (Chative "meta remove facebook messenger chat plugin" https://chative.io/blog/meta-remove-facebook-messenger-chat-plugin/ ; Tidio https://www.tidio.com/blog/facebook-live-chat-integration/) report discontinuation on May 9, 2024. Tidio (2026) says only the m.me link remains and legacy embed code shows a broken element. Search snippets only; pages not fetched in full.
- Contradiction/gap: Meta's Messenger Platform changelog (https://developers.facebook.com/docs/messenger-platform/changelog/, entries to 2026-04-27, latest version v26.0) has NO entry on chat plugin removal in 2024; last chat plugin entries are 2021-2022. Meta's "Customer Service on Messenger" page (https://developers.facebook.com/products/messenger/customer-care/) still describes the Chat Plugin as current (search-snippet only). Plugchat (WordPress.org) claims a newer Business Suite embed code exists.
- Publisher/date: Chative / Tidio (vendors, date of Tidio guide 2026); Meta changelog (no date stamp).
- Correction: word as "reported by third parties to have been discontinued ~9 May 2024; no Meta changelog entry found; verify in Meta Business Suite before relying on it". Do not state as Meta-confirmed.

## V6 - Google FAQ rich results deprecated (notice 2026-05-08, docs removed 2026-06-15), incl. gov/health
**Verdict: verified.**
- Evidence (Google Search Central changelog via fetch): May 8 [2026]: "Added a deprecation notice to the FAQ rich result documentation." ... "This feature will no longer appear in Google Search starting May 7, 2026." June 15 [2026]: "The FAQ rich result feature is no longer shown in Google Search results," and the FAQ documentation was removed. Earlier (Sept 14, 2023): feature "only shown for well-known, authoritative government and health websites" - so the 2026 removal covers those too.
- Independent corroboration: TechWyse https://www.techwyse.com/news/ai-search/google-faq-rich-results-deprecated-2026 and others (search results only): display ended May 7, 2026 for all sites incl. government/health; Rich Results Test/report dropped June 2026, Search Console API support August 2026. Reports say Google continues to use FAQ structured data for understanding pages (FAQPage markup itself not invalid).
- URL: https://developers.google.com/search/updates (changelog; fetched via https://developers.google.com/search/docs/appearance/structured-data/faqpage). Publisher: Google Search Central. Date: no page stamp; latest entry Oct 26, 2026.
- Correction: the notice is dated 2026-05-08 with feature end 2026-05-07 (the claim's "reported 2026-05-08" is fine). Only the first 100,000 of ~180,000 characters of the page were read; the relevant entries were in that portion.

## V7 - iOS web push only for Home Screen web apps (still true 2026, incl. EU)
**Verdict: verified for 2023 origin; 2026 status UNVERIFIED (no 2026 primary source retrieved).**
- Evidence (WebKit blog, 2023-02-16): "A web app that has been added to the Home Screen can request permission to receive push notifications" (request must come from a user gesture). URL: https://webkit.org/blog/13878/web-push-for-web-apps-on-ios-and-ipados/ Publisher: WebKit. The article does not mention the EU.
- EU: secondary sources (MacRumors forum, vendor blogs) say Apple planned to drop Home Screen web apps in the EU with iOS 17.4 (2024) and then reversed, continuing the capability. One 2026-dated vendor guide (webscraft.org) claims push is unavailable in the EU on iOS 17.4+, contradicting the reversal; judged low reliability. No 2026 Apple/WebKit primary source was retrieved.
- Correction: say "as of the 2023 WebKit announcement; Apple reversed the planned 2024 EU removal per secondary reports; 2026 behaviour not independently confirmed". Also, I did not check whether newer iOS versions (e.g. iOS 17+/26 browser-based push) changed the Home Screen requirement - unverified.
