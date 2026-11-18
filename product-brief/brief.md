---
title: "Product Brief: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-13
updated: 2026-11-18
version: 3
---

# Product Brief: AURA SKIN Klinikk – nettside

Versjon 3, 2026-11-18. Erstatter versjon 2 fra 2026-10-29 (historikk i Git). Samkjørt med PRD versjon 8 (`prd/prd.md`).

## Sammendrag

AURA SKIN Klinikk er en hudpleieklinikk på Karmøy (Bøvegen 60, 4260 Salhus) med to ansatte, blant dem en kosmetisk sykepleier. I dag går all kundekontakt gjennom Facebook, Instagram og telefon. Kunder sender meldinger og bilder for å finne ut hva klinikken tilbyr, hva det koster og når den er åpen. Det er tungvint for kundene og tidkrevende for klinikken, som tar imot rundt tre kunder om dagen.

Behandlingene starter alltid med en konsultasjon, og mange behandlinger må godkjennes av lege. Kunden tar derfor kontakt for å avklare konsultasjonen før en time settes opp. Selvbetjent booking passer ikke til denne arbeidsflyten og er ikke en del av løsningen.

Løsningen er en egen nettside med fire sider i menyen, **Hjem**, **Behandlinger**, **Om oss** og **Kontakt oss**, og en egen **Send melding**-side der kunden skriver en melding som automatisk kommer frem til behandlerne på e-post og SMS. Kunder som heller vil skrive i Messenger eller Instagram, kommer rett dit med en lenke. Klinikken oppdaterer innholdet selv i et adminpanel. Nettsiden skal være ferdig 2026-12-15.

## Problemet

- **Mange gjentatte spørsmål.** Kunder spør om det samme igjen og igjen: hva behandlingene innebærer, pris, åpningstider og om man kan komme uten avtale.
- **Mange meldinger og bilder på telefonen.** Klinikken får store mengder private meldinger og bilder som må besvares manuelt ved siden av behandlingene.
- **Uprofesjonelt førsteinntrykk.** En side på sosiale medier signaliserer mindre etablering enn en egen nettside.
- **Manuell oppfølging av timer.** Bekreftelser og påminnelser må sendes for hånd. Dette løses etter første versjon (se Omfang).

## Løsningen

### Nettsiden

- **Om oss:** presentasjon av klinikken og de to behandlerne, med bilde, rolle og kort bakgrunn for hver, slik at kunden vet hvem de møter. Den medisinsk ansvarlige personen navngis med kontaktinformasjon.
- **Behandlinger:** side med alle behandlinger og en egen side per behandling, for eksempel HIFU. For hver behandling står det hva den innebærer (hvordan den foregår, varighet, forventet resultat og eventuell nedetid), hva den koster, risiko og aldersgrense (18 år), og om den krever legegodkjenning. Siden forklarer også hvordan det foregår: kunden tar kontakt, konsultasjon, eventuell legegodkjenning, behandling. Teksten bruker nøytrale behandlingsnavn og viser ikke legemiddelnavn (se Tekniske rammer og regler).
- **Send melding:** kunden skriver navn, mobilnummer, eventuelt hvilken behandling det gjelder, og en melding. Meldingen sendes automatisk til behandlerne på **e-post og SMS**, og vises alltid i adminpanelet. Kunden får en kvittering på skjermen. Fra en behandlingsside er behandlingen forhåndsvalgt. Skjemaet står både på forsiden og på en egen side, er for personer fra 18 år, og ber ikke om bilder eller helseopplysninger.
  - **Direkte lenker** til SMS, e-post, Facebook Messenger og Instagram for kunder som heller vil skrive selv eller sende bilder. Klinikkens ønske om at skjemameldinger også havner i Messenger og Instagram er ikke med i første versjon; lenkene er løsningen.
- **Kontakt oss:** adresse, åpningstider (man–fre 10–20, lør–søn 10–18, kun etter avtale, ingen drop-in), telefon, e-post, parkering og kart. Kartet er et statisk bilde med lenker til Google Maps.
- **Vanlige spørsmål:** en enkel utvidbar liste på forsiden som klinikken redigerer selv.
- **Faste kontaktknapper** for telefon, kart og e-post på alle sider.

### Adminpanelet

Klinikken logger inn og gjør følgende selv:

- legger til, endrer og skjuler behandlinger, med beskrivelse, pris, varighet og krav om legegodkjenning;
- endrer «Om oss»-tekst, behandlerne, bilder, åpningstider og kontaktinformasjon;
- ser alle meldinger fra «Send melding» i en oversikt, med sendestatus og en teller for uleste og feilede, og markerer dem som besvart;
- sletter og eksporterer opplysninger om en kunde når kunden ber om det.

Alle brukere har samme rettigheter. Utvikleren har egen konto under byggingen og overleverer siden til klinikken etterpå. Betaling skjer i klinikken.

### Etter minimumsreleasen

I denne rekkefølgen, så langt tiden rekker før fristen 2026-12-15:

- **Vanlige spørsmål** på forsiden.
- **Avtalte timer.** Klinikken registrerer en avtalt time, og kunden får automatisk SMS med bekreftelse og påminnelse før timen. SMS-ene nevner ikke behandlingen.
- **Nyhetsbrev**, hvis klinikken ønsker det og reglene for markedsføring tillater det. Nyhetsbrev kan ikke omtale injeksjoner, fillers eller andre kosmetiske inngrep. Push-varsler er ikke planlagt.

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
3. Åpningstider (man–fre 10–20, lør–søn 10–18), «kun etter avtale» og adressen vises tydelig.
4. En melding sendt via «Kontakt oss» kommer frem til behandlerne på e-post og SMS og vises i adminpanelet; kunden får kvittering på skjermen. Hvis én kanal feiler, sendes meldingen likevel på den andre, og feilen vises i adminpanelet.
5. De direkte lenkene åpner riktig kanal (SMS, e-post, Messenger, Instagram) på mobil.
6. Når klinikken endrer innhold i adminpanelet, vises endringen på nettsiden uten at utvikleren må gjøre noe.
7. Adminpanelet er kun tilgjengelig etter innlogging.
8. Nettsiden fungerer godt på mobilskjerm.
9. Appen kan startes lokalt etter README med seed-data og en test-admin; SMS og e-post kan testes uten ekte utsending.
10. Siden setter ingen sporings-cookies og laster ingen fonter, kart eller skript fra tredjepart, så den trenger ikke samtykkebanner.

### Forretningsmål (følges opp med klinikken etter lansering)

- Klinikken oppdaterer innholdet selv uten teknisk hjelp.
- Færre gjentatte spørsmål om pris, behandlinger og åpningstider.
- Nettsiden oppleves gjennomført og profesjonell.

## Omfang

**Minimumsrelease (kreves 2026-12-15):**
- Nettside med Hjem, Behandlinger (med en side per behandling), Om oss og Kontakt oss, med åpningstider, adresse og kart.
- Send melding med skjema som sendes på e-post og SMS, pluss direkte lenker til SMS, e-post, Messenger og Instagram.
- Adminpanel for innhold, bilder, åpningstider og innkomne meldinger, med sletting og eksport av kundedata.
- Lokal kjøring med seed-data (fiktive behandlinger, test-admin og fiktive testkunder).

**Etter minimumsreleasen, så langt tiden rekker (skjæringspunkt for ny funksjonalitet 2026-12-08):**
- Vanlige spørsmål på forsiden.
- Registrering av avtalte timer med automatisk SMS-bekreftelse og påminnelse.
- Nyhetsbrev, sist og bare hvis reglene tillater det og tiden rekker.

**Utenfor:**
- Kalender og selvbetjent booking: passer ikke klinikkens arbeidsflyt med konsultasjon og legegodkjenning.
- Push-varsler.
- Videresending av skjemameldinger til Messenger og Instagram via Metas API.
- Statistikk og samtykkebanner i første versjon.
- Nettbetaling.
- Kundekonto/innlogging for kunder.
- Opplasting av bilder og innsamling av helseinformasjon fra kunder: ville utløst strengere GDPR-krav (helsedata, art. 9).
- Kjøp og drift av domene og produksjonshosting: klinikkens sak. Nettsiden gjøres klar for klinikkens domene, med en overleveringsguide.

## Tekniske rammer og regler

Konkret stakk velges og begrunnes i arkitekturfasen, innenfor disse rammene:

- **Enkel stakk med én database.** Vanlig, godt dokumentert teknologi.
- **Kjørbar lokalt.** Én kommando (eller noen få steg i README) starter appen med seed-data.
- **Eksterne tjenester bak et grensesnitt.** SMS og e-post sendes via en ekstern leverandør i produksjon, men lokalt brukes en testversjon som logger meldingene i stedet for å sende dem. Ingen betalte kontoer kreves for å kjøre og vurdere løsningen.
- **Messenger og Instagram.** Å sende skjemameldinger inn i Messenger og Instagram er et ønske fra klinikken, men ikke med i første versjon. Metas meldings-API lar en side bare svare brukere som har skrevet først, og et nettskjema ser ikke ut til å kunne åpne en samtale (utledet av Metas dokumentasjon, ikke bekreftet ordrett). Nettsiden lenker derfor direkte til klinikkens Messenger (`m.me`) og Instagram (`ig.me`), og kunden skriver selv der. Det må testes at bilder sendt via lenkene kommer frem i klinikkens innboks, og at adressene stemmer.
- **Regler for innholdet.** Reklame for reseptpliktige legemidler til allmennheten er forbudt, også på klinikkens egen side. Siden bruker derfor ikke legemiddelnavn eller kodeord, viser ikke før/etter-bilder av injeksjons- og fillerbehandlinger, og navngir den medisinsk ansvarlige. Forskriften om markedsføring av kosmetiske inngrep er lest på Lovdata; den forbyr også e-post og SMS-markedsføring om kosmetiske inngrep. Om HIFU regnes som kosmetisk inngrep er uavklart og behandles som om den gjør det inntil videre. Markedsføringsloven § 15 og reglene for laser og peeling er ikke lest ordrett. Se `prd/prd.md` og `.docs/planning-artifacts/research/`.
- **Personvern.** Navn, mobilnummer, e-post (nyhetsbrev) og meldingstekst lagres kun til formålet, og slettes etter 12 måneder. Behandlingsvalg og fritekst kan røpe helseforhold og behandles som sensitive: de sendes ikke i SMS. Klinikken er behandlingsansvarlig og utvikleren databehandler med avtale. Kunden samtykker i skjemaet. Ingen statistikk eller sporing, og fontene hostes selv.
- **Hemmeligheter.** Repoet er offentlig: hemmeligheter ligger i `.env` utenfor Git, med `.env.example` i repoet. Ekte kundedata committes aldri.
- **Bilder.** Bilder av klinikken og de ansatte legges bare i repoet etter samtykke fra klinikken; ellers brukes plassholdere.

## Visjon

Nettsiden kan bli klinikkens hovedkanal for kundekommunikasjon. Videre kan den utvides med SMS-oppfølging av timer, nyhetsbrev og nettbetaling, og den kan bli en gjenbrukbar mal for nettsider til andre små klinikker.
