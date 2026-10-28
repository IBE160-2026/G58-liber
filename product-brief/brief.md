---
title: "Product Brief: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-13
updated: 2026-10-28
---

# Product Brief: AURA SKIN Klinikk – nettside

## Sammendrag

AURA SKIN Klinikk er en hudpleieklinikk i Haugesund med to ansatte, blant dem en kosmetisk sykepleier. I dag går all kundekontakt gjennom Facebook, Instagram og telefon. Kunder sender meldinger og bilder for å finne ut hva klinikken tilbyr, hva det koster og når den er åpen. Det er tungvint for kundene og tidkrevende for klinikken, som tar imot rundt tre kunder om dagen.

Behandlingene starter alltid med en konsultasjon, og mange behandlinger må godkjennes av lege. Kunden tar derfor kontakt med klinikken for å avtale konsultasjon før en time settes opp. Selvbetjent booking passer ikke til denne arbeidsflyten og er ikke en del av løsningen.

Dette prosjektet er en egen nettside som presenterer klinikken og behandlerne med bilder, forklarer behandlingene og prisene, og gjør det enkelt å kontakte en behandler via SMS, Facebook, Instagram eller e-post. Klinikken får et adminpanel der de oppdaterer innholdet selv, registrerer avtalte timer slik at kunden automatisk får SMS om timen, og når kundene sine med nyhetsbrev og push-varsler.

## Problemet

- **Mange gjentatte spørsmål.** Kunder spør om det samme igjen og igjen: hva behandlingene innebærer, pris, åpningstider og om man kan komme uten avtale.
- **Mange meldinger og bilder på telefonen.** Klinikken får store mengder private meldinger og bilder som må besvares manuelt ved siden av behandlingene.
- **Manuell oppfølging av timer.** Bekreftelser og påminnelser om avtalte timer må sendes for hånd.
- **Ingen egen kanal til kundene.** Klinikken når kundene bare gjennom sosiale medier, uten nyhetsbrev eller varsler den selv styrer.
- **Uprofesjonelt førsteinntrykk.** En side på sosiale medier signaliserer mindre etablering enn en egen nettside.

## Løsningen

### Nettsiden

- **Om oss:** presentasjon av klinikken og behandlerne, med bilder av klinikken og de ansatte.
- **Behandlinger:** egen side med alle behandlinger, for eksempel HIFU. For hver behandling står det hva den innebærer (hvordan den foregår, varighet, forventet resultat og eventuell nedetid), hva den koster, og om den krever legegodkjenning.
- **Slik foregår det:** kunden tar kontakt og avtaler konsultasjon, deretter eventuell legegodkjenning og behandling.
- **Praktisk info:** åpningstider 10–20, kun etter avtale (ingen drop-in), adresse i Haugesund.
- **Send melding (kontakt og timeavtale):** en egen side der kunden skriver navn, telefonnummer, hvilken behandling det gjelder og en melding, og trykker «Send melding». Meldingen videresendes til behandleren på SMS, Facebook Messenger og/eller Instagram, slik at behandleren får den der de allerede svarer kunder. Behandleren tar så kontakt og avtaler konsultasjon eller time. Siden har i tillegg direkte lenker til SMS, Facebook, Instagram og e-post for kunder som heller vil skrive selv.
- **Påmelding:** kunden kan melde seg på nyhetsbrev og slå på push-varsler.

### Adminpanelet

Klinikken logger inn og gjør følgende selv:

- legger til, endrer og skjuler behandlinger, med beskrivelse, pris, varighet og krav om legegodkjenning;
- endrer åpningstider, kontaktinformasjon, «Om oss»-tekst og bilder;
- velger hvilke kanaler meldinger fra «Send melding» skal videresendes til (SMS, Facebook, Instagram), og ser alle mottatte meldinger i en oversikt;
- registrerer en avtalt time (kunde, telefonnummer, behandling, tidspunkt), og kunden får automatisk en SMS med bekreftelse og påminnelse før timen;
- skriver og sender nyhetsbrev til påmeldte kunder;
- sender push-varsler, for eksempel om tilbud eller ledige timer.

Utvikleren beholder egen admin-tilgang for å kunne bistå ved behov. Betaling skjer i klinikken.

## Hva gjør dette annerledes

Mange klinikker bruker en ferdig bookingplattform (f.eks. Timma, Fresha, Eazybook). For AURA SKIN Klinikk passer ikke det: behandlingene krever konsultasjon og legegodkjenning før time kan settes, så automatisk booking ville skapt flere avklaringer, ikke færre. Fordelen med en skreddersydd nettside er:

- **Tilpasset klinikkens arbeidsflyt:** kunden blir informert før kontakt, og timen settes av klinikken, som så får automatisk SMS-oppfølging.
- **Egen kanal til kundene:** nyhetsbrev og push-varsler som klinikken styrer selv.
- **Egen merkevare:** nettsiden ser ut og føles som AURA SKIN Klinikk.

## Hvem dette er for

**Primær: klinikken.** To ansatte, blant dem en kosmetisk sykepleier. Suksess = færre gjentatte spørsmål, mindre manuell oppfølging av timer, og innhold de oppdaterer selv uten teknisk hjelp.

**Primær: klinikkens kunder.** Vil raskt finne ut hva klinikken tilbyr, hvem behandlerne er, hva det koster og hvordan de tar kontakt, som oftest fra mobilen.

## Suksesskriterier

### Funksjonelle kriterier

1. Behandlingssiden viser hver synlige behandling med hva den innebærer og hva den koster.
2. «Om oss» viser presentasjon og bilder av klinikken og behandlerne.
3. Åpningstider (10–20) og «kun etter avtale» vises tydelig.
4. En melding sendt via «Send melding» kommer frem til behandleren på de valgte kanalene og vises i adminpanelet; kunden får bekreftelse på skjermen om at meldingen er sendt.
   Direkte lenker åpner riktig kanal (SMS, Facebook, Instagram, e-post) på mobil.
5. Når klinikken endrer innhold i adminpanelet, vises endringen på nettsiden uten at utvikleren må gjøre noe.
6. Når klinikken registrerer en time, sendes en SMS-bekreftelse til kunden, og en påminnelse før timen.
7. Kunder kan melde seg på og av nyhetsbrev og push-varsler; klinikken kan sende til de påmeldte.
8. Adminpanelet er kun tilgjengelig etter innlogging.
9. Nettsiden fungerer godt på mobilskjerm.
10. Appen kan startes lokalt etter README med seed-data og en test-admin; SMS, e-post og push kan testes uten ekte utsending.

### Forretningsmål (følges opp med klinikken etter lansering)

- Klinikken oppdaterer innholdet og registrerer timer selv uten teknisk hjelp.
- Færre gjentatte spørsmål om pris, behandlinger og åpningstider.
- Færre uteblitte timer takket være SMS-påminnelser.
- Nettsiden oppleves gjennomført og profesjonell.

## Omfang

**Med:**
- Nettside med om oss, bilder av klinikken og behandlerne, behandlinger med priser, slik foregår det, åpningstider og kontakt.
- «Send melding»-side som videresender kundens melding til behandleren på SMS, Facebook og/eller Instagram, pluss direkte kontaktlenker.
- Adminpanel for innhold, bilder og åpningstider.
- Registrering av avtalte timer med automatisk SMS-bekreftelse og påminnelse.
- Nyhetsbrev med på- og avmelding.
- Push-varsler med på- og avmelding.
- Lokal kjøring med seed-data (fiktive behandlinger, test-admin og fiktive testkunder).

**Utenfor:**
- Kalender og selvbetjent booking: passer ikke klinikkens arbeidsflyt med konsultasjon og legegodkjenning.
- Nettbetaling.
- Kundekonto/innlogging for kunder.
- Opplasting av bilder og innsamling av helseinformasjon fra kunder: ville utløst strengere GDPR-krav (helsedata, art. 9).
- Domene og produksjonshosting: klinikkens sak.

## Tekniske rammer

Konkret stakk velges og begrunnes i arkitekturfasen, innenfor disse rammene:

- **Enkel stakk med én database.** Vanlig, godt dokumentert teknologi.
- **Kjørbar lokalt.** Én kommando (eller noen få steg i README) starter appen med seed-data.
- **Eksterne tjenester bak et grensesnitt.** SMS, e-post og push sendes via en ekstern leverandør i produksjon, men lokalt brukes en testversjon som logger meldingene i stedet for å sende dem. Ingen betalte kontoer kreves for å kjøre og vurdere løsningen.
- **Videresending til Facebook og Instagram.** SMS-videresending er enkelt å få til. Å sende meldinger inn i Messenger eller Instagram krever Metas API med bedriftskonto og godkjenning, så det avklares i arkitekturfasen. Om det ikke lar seg gjøre, sendes meldingen på SMS (og eventuelt e-post), og nettsiden lenker direkte til klinikkens Messenger og Instagram.
- **Personvern.** Telefonnummer og e-post lagres kun til formålet (timeavtaler, nyhetsbrev, varsler). Nyhetsbrev og push krever aktivt samtykke, og kunden kan melde seg av når som helst.
- **Hemmeligheter.** Repoet er offentlig: hemmeligheter ligger i `.env` utenfor Git, med `.env.example` i repoet. Ekte kundedata committes aldri.
- **Bilder.** Bilder av klinikken og de ansatte legges bare i repoet etter samtykke fra klinikken; ellers brukes plassholdere.

## Visjon

Nettsiden kan bli klinikkens hovedkanal for kundekommunikasjon. Videre kan den utvides med nettbetaling, og den kan bli en gjenbrukbar mal for nettsider til andre små klinikker.
