---
title: "Addendum: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-13
updated: 2026-10-29
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

## Endringer i versjon 2 (2026-10-29)

- **Omfang snevret inn til kjernen:** Om oss, Behandlinger og Kontakt oss, pluss adminpanel for innhold og meldinger. Brukerens ønske, i tråd med PRD v3 §9.
- **Fase 2:** registrering av avtalte timer med SMS-bekreftelse og påminnelse (var en del av versjon 1 av briefen).
- **Tatt ut av versjon 1:** push-varsler og nyhetsbrev. Researchen 2026-10-28 fant at forskriften om markedsføring av kosmetiske inngrep § 7 trolig forbyr markedsføringshenvendelser om slike inngrep på e-post og SMS, at push på iPhone krever at siden er lagt på hjemskjermen, og at klinikkens volum er lavt.
- **Adresse:** Bøvegen 60, 4260 Salhus (Karmøy), bekreftet av brukeren. Tidligere dokumenter sa Haugesund. Klinikken bekrefter kommunen i spørsmål 23.
- **Kontakt oss:** meldingen sendes på e-post og SMS. Brukeren vil at den også kan sendes på Facebook og Instagram, hvis det lar seg gjøre. Briefen fører det som et ønske som avgjøres i arkitekturfasen, siden researchen tyder på at et skjema ikke kan åpne en samtale (se under).

## Videresending til Facebook og Instagram

Status etter research 2026-10-28 (PRD v3 bygger det ikke; briefen versjon 2 beholder det som ønske, avgjøres i arkitekturfasen): skjemameldinger ser ikke ut til å kunne sendes inn i Messenger eller Instagram. Metas Instagram-API lar en app bare sende melding til en bruker som har skrevet først, og et nettskjema åpner ikke samtalevinduet i Messenger. Løsningen er SMS og e-post til behandlerne, pluss lenker (`m.me`, `ig.me`) som kunden trykker på for å skrive selv. Se `prd/addendum.md`.

## Regler for innhold (fra research 2026-10-28)

- Ikke nevn legemiddelnavn, virkestoff eller kodeord («toksin», «BTX») for reseptpliktige behandlinger. DMP har ilagt en klinikk 5 000 kr per dag i tvangsmulkt for slikt.
- Ingen før/etter-bilder for injeksjoner og fillere, og den medisinsk ansvarlige skal navngis (forskrift om markedsføring av kosmetiske inngrep §§ 4–5).
- Prislister uten påstander om legemidlet er tillatt. Nøytrale behandlingsnavn som «rynkebehandling» ser ut til å være lov, men det er en slutning og ikke bekreftet av DMP.
- Lovtekstene er lest via sammendrag og må leses i fulltekst før tekstene godkjennes. Klinikkens lege bør godkjenne de endelige behandlingstekstene.

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
- Facebook-siden er en bedriftsside (sjekket 2026-10-29). Om Instagram er en profesjonell konto koblet til siden, og hvem som er administrator, er ikke avklart.
- Navn, bakgrunn og bilder av de to behandlerne, og behandlingsliste med priser, leveres av klinikken.
- Om meldinger fra «Kontakt oss» går til ett felles nummer eller til valgt behandler (spørsmål 9 i spørsmålslisten).
- Teknisk plattform avklares i arkitekturfasen.
