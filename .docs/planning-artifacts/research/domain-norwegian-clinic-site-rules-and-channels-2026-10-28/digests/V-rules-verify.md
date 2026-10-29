# V-rules-verify: independent verification of V1-V3

Run date: 2026-10-28. Budget of 10 tool calls used.

**Method caveat.** WebFetch and WebSearch return model-written summaries, not verbatim page text. Quotes below are what the tool reported as text, so treat them as near-verbatim and re-check against the live page before putting them in a PRD. The two DMP guidance pages (the clinic guide and the cosmetic-procedures guide) were fetched, but the tool returned only site navigation and truncated before the body. Statements from them come from search-result summaries only. The Helsedirektoratet PDF came back as unreadable binary, so its conclusion was not read.

**Agency name.** The regulator is now shown as **Direktoratet for medisinske produkter (DMP)**, domain dmp.no. Legemiddelverket documents are hosted there. Documents may need citing as "Statens legemiddelverk / DMP". The fetched page headers show only the DMP name. Whether and when the rename happened was not verified.

---

## V1. Ban on naming Botox/botulinumtoksin (or code words) on a clinic's own website or social media

**Verdict: verified at summary level. The primary guide text was not read, so the quotes below are unverified.**

- Evidence (search summary of DMP's "Veileder for estetiske klinikker i regelverket for legemiddelreklame"): the ban applies whether a clinic uses a trade name, the active substance, a code or pictures. The guide reportedly lists "toksin" and "BTX" as illegal code words. Discount campaigns are prohibited. Price lists are allowed only if they make no claims about the drug.
- The DMP decisions in the same search cite legemiddelforskriften § 13-4 (ban on advertising prescription-only medicines to the public) and treat clinic content on websites, Facebook, Instagram and TikTok as advertising. Decisions found:
  - Klinikk Birkeland, 2022-10-01.
  - Lead Partner AS, 2025, with a daily fine of NOK 5,000.
  - A 2023 botulinum-toxin decision, reported in the search summary as a NOK 700,000 fine.
- Annual report 2022 (as summarised): 14 decisions and 175 tips, most about botulinum toxin.
- URLs:
  - https://www.dmp.no/tilvirkning-import-og-salg/reklame-for-legemidler/informasjon-for-klinikker/veileder-for-estetiske-klinikker (publisher DMP; date not retrieved)
  - https://www.dmp.no/globalassets/documents/tilvirkning-import-og-salg/reklame/brudd-pa-reklamereglene/vedtak-om-stans-av-ulovlig-reklame-og-tvangsmulkt-011022_klinikk-birkeland.pdf (DMP, 2022-10-01)
  - https://www.dmp.no/globalassets/documents/tilvirkning-import-og-salg/reklame/brudd-pa-reklamereglene/23_09256-19-vedtak-om-stans-av-ulovlig-reklame-for-botulinum-toksin-beriktigelse-of-37762309_25733902_0-2.pdf (DMP, 2023-06-23)
  - https://www.dmp.no/globalassets/documents/tilvirkning-import-og-salg/reklame/brudd-pa-reklamereglene/2025/25_07558-4-vedtak-om-stans-av-ulovlig-reklame-og-tvangsmulkt.pdf (DMP, 2025)
- Corrections and nuance:
  - A secondary source, a NORFEM clinic-association memo, says brand names may appear in price lists together with units/vials and price. This was reported only via search summary and conflicts in detail with the DMP summary ("no claims about the drug"). Treat price-list wording as **unresolved**. Safest design is no product names at all.
  - The ban comes from legemiddelforskriften § 13-4. The exact wording of § 13-4 was not retrieved. Verify on Lovdata before quoting the section number.

## V2. Marketing rules for cosmetic procedures

**Verdict: verified (via a Lovdata fetch summary). Correct title and scope below. The 2025-26 amendment check is inconclusive.**

- Correct title: **Forskrift om markedsføring av kosmetiske inngrep**, FOR-2005-07-01-749, issued by Helse- og omsorgsdepartementet. In force 2005-07-01. Last amendment shown: FOR-2022-12-21-2445, in force **2023-03-21**.
- § 5, as reported: "Markedsføring av kosmetiske inngrep skal ikke inneholde pre- og postoperative bilder." Verified.
- § 4, as reported: "Det skal fremgå av markedsføringen hvem som er medisinsk ansvarlig for de kosmetiske inngrepene" (plus contact details). Verified.
- Under 18: also in § 4 (paragraph added by the 2023 amendment). Reported text begins "Markedsføringen skal ikke utformes slik at den kan oppfattes av barn under 18 år". The rule is that marketing must not be designed so it can be perceived as aimed at under-18s. It also covers body pressure on children. This is slightly narrower than a general ban on marketing "aimed at" under-18s. Do not paraphrase it as an absolute ban.
- Scope: § 3 defines "kosmetiske inngrep" as plastic surgery and procedures in skin and subcutis, including injections and fillers/medicines, where cosmetic or aesthetic considerations are decisive. It begins "Med kosmetiske inngrep menes plastikkirurgiske inngrep og inngrep i hud og underhud". So the before/after ban applies to **all** procedures in that definition, including injectable treatments. It is not limited to surgery. Whether non-injection skin treatments (peels, laser, facials) fall inside the definition was not confirmed. Check § 3 in full.
- After-only images: Helsedirektoratet issued "Tolkningsuttalelse - bruk av etterbilder av kosmetiske inngrep" (PDF metadata date 2023-06-14). The conclusion was **not read** (unreadable PDF). Do not assume after-only images are allowed. The PRD should avoid all result images until this is read.
  - https://www.helsetilsynet.no/globalassets/opplastinger/presse/2023_tolkningsuttalelse_bruk_etterbilder_kosmetiske_inngrep.pdf
- Amendments in 2025-2026: the Lovdata summary showed no amendment after 2023-03-21, but the fetch may be cached or summarised, so this is **unverified**. Re-check the "Endringer" list on Lovdata.
- URL: https://lovdata.no/dokument/SF/forskrift/2005-07-01-749 (publisher Lovdata / Helse- og omsorgsdepartementet; retrieved 2026-10-28). Related guidance on dmp.no was not read: https://www.dmp.no/medisinsk-utstyr/omsetning/reklame-for-medisinsk-utstyr/veiledning-om-markedsforing-av-kosmetiske-inngrep
- Note: the regulation is made under helsepersonelloven and supervised by Statens helsetilsyn. Legemiddelverket/DMP covers medicine advertising. Forbrukertilsynet covers the marketing act. Three regimes can apply at once.

## V3. Helsepersonelloven § 4 a and § 4 b

**Verdict: verified, with scope corrections.**

- Evidence (Lovdata, reported text):
  - § 4 a, first paragraph: "Kosmetiske inngrep, injeksjoner og behandling som kan påføre pasienten alvorlig skade, sykdom, komplikasjon eller bivirkning, kan bare utføres av helsepersonell."
  - § 4 b, first paragraph: such procedures "uten medisinsk eller odontologisk begrunnelse skal ikke foretas på pasienter under 18 år."
  - Entry into force: "tilføyd ved lov 1. april 2022 nr. 18 og trådte i kraft 1. juli 2022". The page shows no later amendments to §§ 4 a or 4 b.
- URL: https://lovdata.no/dokument/NL/lov/1999-07-02-64/KAPITTEL_1-2 (Lovdata; retrieved 2026-10-28). Only the first 100,000 of 129,637 characters of the page were read. This covered §§ 4 a and 4 b.
- Corrections:
  - § 4 a is not a blanket restriction on all cosmetic injections. It covers those that **can cause serious harm, disease, complication or side effect**. A regulation-making power for the ministry sits in the second paragraph.
  - § 4 b applies to treatments done by health personnel as well. Lower-risk cosmetic treatments such as skin care ("typisk hudpleie") done by non-health personnel have no 18-year limit.
  - The exemption for medical justification covers corrective treatment and treatment of malformation, injury or disease (§ 4 b third paragraph).

---

## Open items
1. Read the body of the DMP clinic guide (page text exceeds 100,000 characters; fetch with offset 100000) for verbatim code-word and price-list wording and its last-updated date.
2. Read the Helsedirektoratet after-only interpretation (2023-06-14).
3. Retrieve legemiddelforskriften § 13-4 text from Lovdata.
4. Re-check the Lovdata change list for FOR-2005-07-01-749 for any 2024-2026 amendments.
