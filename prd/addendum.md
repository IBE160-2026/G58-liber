---
title: "Addendum: PRD AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-27
updated: 2026-10-28
---

# Addendum til PRD

Utdypende og tekniske notater som ikke hører hjemme i selve PRD-en, men som er nyttige for arkitektur- og UX-fasen.

## Hvorfor ikke selvbetjent booking

Tidligere utkast la opp til at kunden booker direkte i en kalender. Etter kundeintervjuet (2026-10-28) ble dette forkastet: alle behandlinger starter med en konsultasjon, mange krever legegodkjenning, og kunden må nesten alltid snakke med behandleren først. Klinikken ønsker heller at kunden sender en melding som når behandleren der de allerede svarer. Timen registreres av klinikken etterpå, og SMS-bekreftelse og påminnelse sendes automatisk.

## Videresending til Facebook og Instagram (FR-8)

- Å sende meldinger inn i Messenger og Instagram krever Metas Messenger Platform / Instagram Messaging API, en Facebook-side og en Instagram-bedriftskonto koblet sammen, og en app som er godkjent av Meta.
- Meta tillater i utgangspunktet bare at en side svarer brukere som har skrevet først (24-timersvindu). Å sende en melding *til klinikkens egen innboks* fra et nettskjema er ikke et standard bruksområde og må undersøkes.
- **Reserveløsning:** Meldingen videresendes på SMS (og eventuelt e-post) til behandleren, og nettsiden har direkte lenker (`m.me/…`, `ig.me/m/…`, `sms:`) slik at kunder som vil, skriver direkte i Messenger eller Instagram.
- Avgjøres tidlig i arkitekturfasen.

## SMS-utsending

- SMS krever en ekstern SMS-tjeneste (norske eksempler: Sveve, Link Mobility, 46elks, Twilio). Prisen ligger typisk på noen titalls øre per melding.
- Brukes til videresending av meldinger, bekreftelse, påminnelse og beskjed om flytting/avlysning.
- Avsendernavn (for eksempel «AURASKIN») støttes av de fleste norske leverandører.

## Nyhetsbrev og push-varsler

- Nyhetsbrev krever en e-posttjeneste med god leveringsrate og støtte for avmelding.
- Push-varsler kan løses med Web Push (fungerer i moderne nettlesere, på iPhone kun når nettsiden er lagt til på hjemskjermen).
- Markedsføringsloven krever forhåndssamtykke for elektronisk markedsføring til privatpersoner.

## Tekniske hensyn for arkitekturfasen

- **Eksterne tjenester bak et grensesnitt:** SMS, e-post og push implementeres slik at en testversjon som logger meldinger kan brukes lokalt.
- **Tidssone:** All tid lagres og vises i norsk tid (Europe/Oslo).
- **Påminnelser (FR-12):** Krever en planlagt jobb.
- **Spam (FR-7):** Rate-limiting og enkel bot-beskyttelse på skjemaet.
- **Innlogging (FR-18):** Minst tre kontoer (to ansatte og utvikler). Tofaktor vurderes.
- **Databehandleravtaler:** Leverandører av hosting, SMS, e-post og push krever databehandleravtale under GDPR.

## Markedsføring av reseptpliktige legemidler

Legemiddelforskriften forbyr reklame for reseptpliktige legemidler rettet mot allmennheten. Botulinumtoksin («botox») er reseptpliktig, og norske klinikker omtaler derfor behandlingen typisk som «rynkebehandling» eller «injeksjonsbehandling». Statens legemiddelverk fører tilsyn. Bør verifiseres med klinikken før tekstene publiseres.
