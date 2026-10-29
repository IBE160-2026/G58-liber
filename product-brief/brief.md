---
title: "Product Brief: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-13
updated: 2026-10-29
version: 2
---

# Product Brief: AURA SKIN Klinikk – nettside

Versjon 2, 2026-10-29. Erstatter versjon 1 fra 2026-10-28 (historikk i Git).

## Sammendrag

AURA SKIN Klinikk er en hudpleieklinikk på Karmøy (Bøvegen 60, 4260 Salhus) med to ansatte, blant dem en kosmetisk sykepleier. I dag går all kundekontakt gjennom Facebook, Instagram og telefon. Kunder sender meldinger og bilder for å finne ut hva klinikken tilbyr, hva det koster og når den er åpen. Det er tungvint for kundene og tidkrevende for klinikken, som tar imot rundt tre kunder om dagen.

Behandlingene starter alltid med en konsultasjon, og mange behandlinger må godkjennes av lege. Kunden tar derfor kontakt for å avklare konsultasjonen før en time settes opp. Selvbetjent booking passer ikke til denne arbeidsflyten og er ikke en del av løsningen.

Løsningen er en egen nettside med tre hoveddeler: **Om oss**, der de to behandlerne presenteres, **Behandlinger**, der hver behandling forklares med pris, og **Kontakt oss**, der kunden sender en melding som automatisk kommer frem til behandlerne på e-post og SMS, og om mulig også i Facebook Messenger og Instagram. Klinikken oppdaterer innholdet selv i et adminpanel.

## Problemet

- **Mange gjentatte spørsmål.** Kunder spør om det samme igjen og igjen: hva behandlingene innebærer, pris, åpningstider og om man kan komme uten avtale.
- **Mange meldinger og bilder på telefonen.** Klinikken får store mengder private meldinger og bilder som må besvares manuelt ved siden av behandlingene.
- **Uprofesjonelt førsteinntrykk.** En side på sosiale medier signaliserer mindre etablering enn en egen nettside.
- **Manuell oppfølging av timer.** Bekreftelser og påminnelser må sendes for hånd. Dette løses i fase 2.

## Løsningen

### Nettsiden

- **Om oss:** presentasjon av klinikken og de to behandlerne, med bilde, rolle og kort bakgrunn for hver, slik at kunden vet hvem de møter. Den medisinsk ansvarlige personen navngis.
- **Behandlinger:** egen side med alle behandlinger, for eksempel HIFU. For hver behandling står det hva den innebærer (hvordan den foregår, varighet, forventet resultat og eventuell nedetid), hva den koster, og om den krever legegodkjenning. Teksten bruker nøytrale behandlingsnavn og viser ikke legemiddelnavn (se Rammer).
- **Kontakt oss:** her avklarer kunden konsultasjon med behandlerne.
  - **Meldingsskjema:** kunden skriver navn, mobilnummer, eventuelt hvilken behandling det gjelder, og en melding, og trykker «Send melding». Meldingen sendes automatisk til behandlerne på **e-post og SMS**. Klinikken ønsker at den også kan sendes til **Facebook Messenger og Instagram**, slik at behandlerne får den der de allerede svarer. Om det lar seg gjøre, avgjøres i arkitekturfasen (se Rammer). Kunden får en bekreftelse på skjermen om at meldingen er sendt og at klinikken tar kontakt.
  - **Direkte lenker** til SMS, e-post, Facebook Messenger og Instagram for kunder som heller vil skrive selv. Lenkene er også reserveløsningen hvis skjemameldinger ikke kan sendes inn i Messenger og Instagram.
  - Skjemaet ber ikke om bilder eller helseopplysninger. Bilder tas i konsultasjonen eller i Messenger og Instagram.
- **Slik foregår det:** kunden tar kontakt og avtaler konsultasjon, deretter eventuell legegodkjenning og behandling.
- **Praktisk info:** åpningstider 10–20, kun etter avtale (ingen drop-in), adresse Bøvegen 60, 4260 Salhus.

### Adminpanelet

Klinikken logger inn og gjør følgende selv:

- legger til, endrer og skjuler behandlinger, med beskrivelse, pris, varighet og krav om legegodkjenning;
- endrer «Om oss»-tekst, behandlerne, bilder, åpningstider og kontaktinformasjon;
- ser alle meldinger fra «Kontakt oss» i en oversikt, markerer dem som besvart og velger hvem som mottar dem og på hvilke kanaler (e-post, SMS og eventuelt Messenger og Instagram).

Utvikleren beholder egen admin-tilgang for å kunne bistå ved behov. Betaling skjer i klinikken.

### Senere faser

- **Fase 2: avtalte timer.** Klinikken registrerer en avtalt time, og kunden får automatisk SMS med bekreftelse og påminnelse før timen.
- **Etter det:** nyhetsbrev, hvis klinikken ønsker det og reglene for markedsføring er avklart. Push-varsler er ikke planlagt.

## Hva gjør dette annerledes

Mange klinikker bruker en ferdig bookingplattform (f.eks. Timma, Fresha, Eazybook). For AURA SKIN Klinikk passer ikke det: behandlingene krever konsultasjon og legegodkjenning før time kan settes, så automatisk booking ville skapt flere avklaringer, ikke færre. Fordelen med en skreddersydd nettside er:

- **Tilpasset klinikkens arbeidsflyt:** kunden blir informert før kontakt, og timen settes av klinikken.
- **Meldinger som havner der behandlerne svarer:** SMS og e-post i stedet for en innboks de må sjekke.
- **Egen merkevare:** nettsiden ser ut og føles som AURA SKIN Klinikk.

## Hvem dette er for

**Primær: klinikken.** To ansatte, blant dem en kosmetisk sykepleier. Suksess = færre gjentatte spørsmål, og innhold de oppdaterer selv uten teknisk hjelp.

**Primær: klinikkens kunder.** Vil raskt finne ut hva klinikken tilbyr, hvem behandlerne er, hva det koster og hvordan de tar kontakt, som oftest fra mobilen.

## Suksesskriterier

### Funksjonelle kriterier

1. Behandlingssiden viser hver synlige behandling med hva den innebærer og hva den koster.
2. «Om oss» viser presentasjon og bilder av klinikken og begge behandlerne.
3. Åpningstider (10–20), «kun etter avtale» og adressen vises tydelig.
4. En melding sendt via «Kontakt oss» kommer frem til behandlerne på e-post og SMS og vises i adminpanelet; kunden får bekreftelse på skjermen. Hvis én kanal feiler, sendes meldingen likevel på de andre. Hvis videresending til Messenger og Instagram er mulig, kommer meldingen også dit.
5. De direkte lenkene åpner riktig kanal (SMS, e-post, Messenger, Instagram) på mobil.
6. Når klinikken endrer innhold i adminpanelet, vises endringen på nettsiden uten at utvikleren må gjøre noe.
7. Adminpanelet er kun tilgjengelig etter innlogging.
8. Nettsiden fungerer godt på mobilskjerm.
9. Appen kan startes lokalt etter README med seed-data og en test-admin; SMS og e-post kan testes uten ekte utsending.

### Forretningsmål (følges opp med klinikken etter lansering)

- Klinikken oppdaterer innholdet selv uten teknisk hjelp.
- Færre gjentatte spørsmål om pris, behandlinger og åpningstider.
- Nettsiden oppleves gjennomført og profesjonell.

## Omfang

**Versjon 1:**
- Nettside med om oss (de to behandlerne), behandlinger med priser, slik foregår det, åpningstider og kontakt.
- «Kontakt oss» med meldingsskjema som sendes på e-post og SMS, og på Messenger og Instagram hvis Meta tillater det, pluss direkte lenker til SMS, e-post, Messenger og Instagram.
- Adminpanel for innhold, bilder, åpningstider og innkomne meldinger.
- Lokal kjøring med seed-data (fiktive behandlinger, test-admin og fiktive testkunder).

**Fase 2:**
- Registrering av avtalte timer med automatisk SMS-bekreftelse og påminnelse.

**Utenfor:**
- Kalender og selvbetjent booking: passer ikke klinikkens arbeidsflyt med konsultasjon og legegodkjenning.
- Push-varsler.
- Nyhetsbrev i versjon 1.
- Nettbetaling.
- Kundekonto/innlogging for kunder.
- Opplasting av bilder og innsamling av helseinformasjon fra kunder: ville utløst strengere GDPR-krav (helsedata, art. 9).
- Domene og produksjonshosting: klinikkens sak.

## Tekniske rammer og regler

Konkret stakk velges og begrunnes i arkitekturfasen, innenfor disse rammene:

- **Enkel stakk med én database.** Vanlig, godt dokumentert teknologi.
- **Kjørbar lokalt.** Én kommando (eller noen få steg i README) starter appen med seed-data.
- **Eksterne tjenester bak et grensesnitt.** SMS og e-post sendes via en ekstern leverandør i produksjon, men lokalt brukes en testversjon som logger meldingene i stedet for å sende dem. Ingen betalte kontoer kreves for å kjøre og vurdere løsningen.
- **Messenger og Instagram.** Å sende skjemameldinger inn i Messenger og Instagram er et ønske, men uavklart. Metas meldings-API lar en side bare svare brukere som har skrevet først, og et nettskjema ser ikke ut til å kunne åpne en samtale (utledet av Metas dokumentasjon, ikke bekreftet ordrett). Det krever dessuten bedriftskonto og godkjenning fra Meta. Arkitekturfasen undersøker om det lar seg gjøre, med en prøve mot klinikkens egen side. E-post og SMS er det som er garantert. Hvis Meta-løsningen ikke går, lenker nettsiden direkte til klinikkens Messenger (`m.me`) og Instagram (`ig.me`), og kunden skriver selv der. Det må også testes om bilder sendt via lenkene kommer frem i innboksen.
- **Regler for innholdet.** Reklame for reseptpliktige legemidler til allmennheten er forbudt, også på klinikkens egen side. Siden bruker derfor ikke legemiddelnavn eller kodeord, viser ikke før/etter-bilder av injeksjons- og fillerbehandlinger, og navngir den medisinsk ansvarlige. Reglene er lest via sammendrag og må kontrolleres på Lovdata og dmp.no før tekstene godkjennes. Se `prd/prd.md` og `.docs/planning-artifacts/research/`.
- **Personvern.** Telefonnummer og e-post lagres kun til formålet (svar på henvendelsen, senere timeavtaler). Kunden samtykker i skjemaet.
- **Hemmeligheter.** Repoet er offentlig: hemmeligheter ligger i `.env` utenfor Git, med `.env.example` i repoet. Ekte kundedata committes aldri.
- **Bilder.** Bilder av klinikken og de ansatte legges bare i repoet etter samtykke fra klinikken; ellers brukes plassholdere.

## Visjon

Nettsiden kan bli klinikkens hovedkanal for kundekommunikasjon. Videre kan den utvides med SMS-oppfølging av timer, nyhetsbrev og nettbetaling, og den kan bli en gjenbrukbar mal for nettsider til andre små klinikker.
