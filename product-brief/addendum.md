---
title: "Addendum: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-13
updated: 2026-10-28
---

# Addendum

Utdypende materiale som støtter briefen, men som hører bedre hjemme her enn i selve dokumentet, for bruk i senere faser (arkitektur, PRD).

## Funn fra kundeintervjuet (2026-10-28)

- Klinikken har to ansatte, blant dem en kosmetisk sykepleier.
- Kundekontakt skjer i dag via Facebook, Instagram og telefon; klinikken får mange meldinger og bilder på telefonen.
- Behandlinger starter alltid med konsultasjon, og mange må godkjennes av lege.
- Klinikken vil **ikke** ha kalender eller selvbetjent booking, fordi kunden nesten alltid må avklare konsultasjonen først. I stedet ønskes en «Send melding»-side som videresender meldingen til behandleren på SMS, Facebook og/eller Instagram.
- Klinikken foretrekker private meldinger.
- Åpningstider 10–20, kun etter avtale (ingen drop-in). Rundt 3 kunder om dagen, ca. 1 time hver.
- Ønsket innhold: om oss med presentasjon og bilder av klinikken og behandlerne, behandlinger med hva de innebærer og pris (f.eks. HIFU).
- Ønsket kundekommunikasjon: SMS om avtalte timer, nyhetsbrev og push-varsler.

## Konkurrentlandskap (research)

Norske hudpleie-/skjønnhetsklinikker bruker typisk ferdige SaaS-plattformer:

- **Timma** og **Fresha** er mest brukt (bl.a. hos Oslo Mediq Hudsalong, Hud-Klinikken, Velbehag Klinikk).
- **Eazybook**, **Bookingtjeneste.no**, **ProClinic**, **Planfy** konkurrerer i samme segment.
- Prismodellen er abonnementsbasert; Eazybook starter på 249 kr/mnd.

Vurdering: disse plattformene er bygget rundt selvbetjent booking, som ikke passer en klinikk der konsultasjon og legegodkjenning kommer først. En skreddersydd nettside konkurrerer på tilpasning til arbeidsflyten, merkevarekontroll og en egen kanal til kundene.

## Videresending til Facebook og Instagram

Å sende meldinger inn i Messenger og Instagram krever Metas API, bedriftskontoer og godkjenning fra Meta. Reserveløsningen er videresending på SMS/e-post og direkte lenker til Messenger og Instagram. Se `prd/addendum.md`.

## Personvern / GDPR-vurdering

- Navn, telefon og e-post er ordinære personopplysninger og krever et normalt behandlingsgrunnlag. Norge følger GDPR via personopplysningsloven, med Datatilsynet som tilsyn.
- Nyhetsbrev og push-varsler er elektronisk markedsføring og krever forhåndssamtykke (markedsføringsloven), med enkel avmelding.
- Kunder sender i dag bilder av huden sin på telefonen. Slike bilder og opplysninger om hudtilstand er helseopplysninger (GDPR art. 9). Nettsiden skal derfor **ikke** ta imot bilder eller helseopplysninger, og skjemaet bør si tydelig fra om dette.

## Bransjestandard-funksjoner (referanse)

- Behandlingskatalog med priser
- Automatiske SMS/e-post-bekreftelser og påminnelser (markedsført som no-show-reduksjon)
- Nyhetsbrev og kampanjer
- Før/etter-bilder og anmeldelser som innholdselementer

## Åpne avklaringer

- Domenenavn og hosting er ikke valgt.
- Tekster, bilder og priser leveres av klinikken.
- Om klinikken har bedriftskontoer på Facebook og Instagram som kan kobles til Metas API.
- Teknisk plattform avklares i arkitekturfasen.
