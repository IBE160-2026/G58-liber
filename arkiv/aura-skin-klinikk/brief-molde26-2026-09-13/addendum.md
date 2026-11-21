---
title: "Addendum: AURA SKIN Klinikk – bookingnettside"
status: draft
created: 2026-09-13
updated: 2026-09-13
---

# Addendum

Utdypende materiale som støtter briefen, men som hører bedre hjemme her enn i selve dokumentet — for bruk i senere faser (arkitektur, PRD).

## Konkurrentlandskap (research)

Norske hudpleie-/skjønnhetsklinikker løser booking i dag typisk med ferdige SaaS-plattformer fremfor egne nettsider:

- **Timma** og **Fresha** er de mest brukte plattformene blant norske klinikker (bl.a. brukt av Oslo Mediq Hudsalong, Hud-Klinikken, Velbehag Klinikk).
- **Eazybook**, **Bookingtjeneste.no**, **ProClinic**, **Planfy** konkurrerer i samme segment. Planfy retter seg også mot helse/medisinsk timebestilling.
- Prismodell er abonnement — Eazybook starter på 249 kr/mnd. De fleste reklamerer med Vipps-støtte som standardfunksjon, ofte brukt til depositum ved booking for å redusere no-show.

Vurdering: en skreddersydd nettside konkurrerer ikke på funksjonsbredde med disse, men på merkevarekontroll, ingen løpende avgift, og at kompleksiteten er tilpasset én behandler i stedet for et multi-ansatt-verktøy.

## Vipps-integrasjon (for v2)

- Dagens produkt er **Vipps Checkout API (v3.0.0)**, som samler Login, ePayment, Recurring og Order Management i én sesjonsbasert flyt.
- Tre integrasjonsveier: ferdig hostet UI ("Flow"), Payment Setup API mot egen UI, eller ren API-integrasjon.
- Støtter engangsbetaling (PAYMENT) og abonnement (SUBSCRIPTION); "Checkout Direct" gir express-betaling for enkeltprodukt uten handlekurv.
- Krever en **Vipps Bedrift**-avtale (merchant agreement) før integrasjon kan settes opp.
- Merk: Vipps/MobilePay Checkout er under overgang til et nytt merkenavn ("Kustom Checkout") — bør verifiseres på nytt når v2 planlegges, siden dette er et bevegelig mål.
- Relevans for AURA SKIN Klinikk: mest naturlige v2-bruk er depositum ved booking (no-show-beskyttelse), ikke nødvendigvis full forhåndsbetaling, siden v1-beslutningen er at kunden betaler i klinikken.

## Personvern / GDPR-vurdering

- Vanlig kontakt-/bookinginformasjon (navn, telefon, e-post) er ordinære personopplysninger og krever et normalt behandlingsgrunnlag (samtykke/avtale) under GDPR, som Norge følger direkte via personopplysningsloven (Datatilsynet er tilsynsmyndighet).
- Dersom klinikken på et senere tidspunkt ønsker å registrere hudtilstand, allergier eller annen helserelatert informasjon knyttet til en behandling, regnes dette som en **særlig kategori personopplysninger** (helsedata, GDPR art. 9) og krever eksplisitt samtykke og strengere håndtering (tilgangskontroll, lagringsbegrensning m.m.).
- Beslutningen i denne omgang er å **ikke** samle slik informasjon i bookingskjemaet — det holder løsningen på et enklere personvernnivå. Dette bør revurderes eksplisitt hvis klinikken senere ønsker et intake-skjema med helseopplysninger.
- Betalingsopplysninger (uansett om det er kontant i dag eller Vipps senere) er underlagt bokføringslovens krav til oppbevaring av regnskapsbilag.

## Bransjestandard-funksjoner (for referanse ved skopevurdering senere)

Sett på tvers av sammenlignbare plattformer: behandlingskatalog med priser, ressursbasert kalender med sanntids ledighet, automatiske SMS/e-post-bekreftelser og påminnelser (markedsført eksplisitt som no-show-reduksjon), depositum/forhåndsbetaling ved booking, håndtering av avbestillings-/ombookingsregler, kundehistorikk/-konto. Før/etter-bildegalleri og anmeldelser forekommer på markedsføringssider, men er mindre universelt i selve bookingmotoren — mer et innholdselement enn en kjernefunksjon.

## Åpne avklaringer (ikke blokkerende for briefen)

- Domenenavn og hosting er ikke valgt.
- Eksakt tekst-, bilde- og prismateriale må hentes manuelt fra Facebook-siden (facebook.com/auraskinklinikk) — kunne ikke hentes automatisk pga. innloggingsvegg.
- Frist oppgitt av oppdragsgiver: briefen skal leveres 2026-09-20. Frist for ferdig nettside er ikke avklart.
- Teknisk plattform/stack er bevisst holdt utenfor denne briefen og avklares i arkitekturfasen.
