---
title: "PRD: AURA SKIN Klinikk – nettside"
status: draft
version: 5
created: 2026-09-27
updated: 2026-11-01
---

# PRD: AURA SKIN Klinikk – nettside

## 0. Om dokumentet

Denne PRD-en beskriver hva nettsiden for AURA SKIN Klinikk skal gjøre, hva som er avklart med klinikken og hva som gjenstår. Den bygger på produktbriefen (`product-brief/brief.md`), kundeintervjuet 2026-10-28 (`kundeintervju/sporsmal.md`) og tilleggsmaterialet i `product-brief/addendum.md` og `prd/addendum.md`, og samler det viktigste fra disse i ett dokument. Versjon 3 legger i tillegg inn funnene fra research av regler og kanaler (2026-10-28, `.docs/planning-artifacts/research/domain-norwegian-clinic-site-rules-and-channels-2026-10-28/research.md`). Versjon 4 (2026-10-29) samkjører PRD-en med produktbrief versjon 2: klinikkens ønske om at meldinger også kan sendes til Messenger og Instagram er ført som et ønske som avgjøres i arkitekturfasen (FR-8, §9, §10), adressen Bøvegen 60, 4260 Salhus (Karmøy) er ført konsekvent, og åpne spørsmål og antakelser er gått gjennom (ingen er lukket, siden klinikken ikke har svart ennå). Versjon 5 (2026-11-01) samkjører PRD-en med designforslaget fra 2026-10-29 (§6): ny sidestruktur og meny (FR-1), egen Send melding-side (FR-7), faste kontaktknapper med infobokser, faktiske kontaktopplysninger og åpningstider med ukedager (FR-4), vanlige spørsmål på forsiden i stedet for egen side (FR-21), «Slik foregår det» flyttet under Behandlinger (FR-5), og push skilt ut av første versjon i FR-15 og FR-17 slik at kravene stemmer med §9. Dokumentet er grunnlaget for UX-design, arkitektur og oppdeling i oppgaver.

- Begrepene i §4 brukes konsekvent. Kravene er nummerert FR-1 til FR-21 (funksjon) og NFR-1 til NFR-13 (kvalitet); numrene er stabile mellom versjoner.
- Antakelser som må bekreftes er merket `[ASSUMPTION]` og samlet i §13. Forslag som ikke er besluttet er merket `[FORSLAG]`.
- Funn fra researchen som ikke er verifisert mot lovtekst eller kildedokumentasjon er merket `[ASSUMPTION]`. Les lovtekst på Lovdata og dmp.no før de brukes som endelige krav.
- Tekniske valg og bakgrunn står i `prd/addendum.md`. Oppsummering av avklart/uklart/forslag står i `prd/prd-grunnlag.md`.
- Klinikkens designeksempel (laget i one.com Website Builder, mottatt 2026-10-29) er lagt inn i §6 og FR-1. Eksempelet er en ferdig mal med malens egne tekster og stockbilder, så det styrer stil og oppbygging, ikke innhold.
- Designforslaget (2026-10-29) er en klikkbar skisse i en privat artefakt og er ikke lagret i repoet. Det viser sider, meny og innholdsplassering, og bruker plassholdere der klinikken ikke har levert innhold. Utenom kontaktopplysningene (FR-4) er alt innhold plassholdere.
- Forrige versjon (versjon 4) finnes i git-historikken, sammen med versjon 3 og 2; versjon 1 (FR-1–FR-20) siste gang i commit `0e38f3a`.

## 1. Visjon

AURA SKIN Klinikk på Karmøy får en egen nettside som presenterer klinikken og behandlerne, forklarer hva behandlingene innebærer og hva de koster, og gjør det enkelt å ta kontakt. Behandlingene starter alltid med en konsultasjon, og mange krever legegodkjenning, så kunden booker ikke selv. I stedet sender kunden en melding fra nettsiden, som kommer frem til behandleren på SMS og e-post. Kunder som heller vil skrive i Messenger eller Instagram, kommer rett dit med en lenke.

Klinikken styrer innholdet selv fra et enkelt adminpanel. Når en time er avtalt, registrerer klinikken den, og kunden får automatisk SMS med bekreftelse og påminnelse. Nyhetsbrev og push-varsler som egen kanal til kundene vurderes, men er begrenset av regelverket og avgjøres i §9.

## 2. Bakgrunn og status

### 2.1 Avklart (intervju 2026-10-28 og senere opplysninger)

| Tema | Avklart |
|---|---|
| Klinikken | To ansatte, blant dem en kosmetisk sykepleier. Bøvegen 60, 4260 Salhus (Karmøy). Har ingen nettside i dag (bekreftet 2026-10-29). |
| Kapasitet | Rundt 3 kunder om dagen, ca. 1 time hver. |
| Åpningstider | Man–fre 10–20, lør–søn 10–18, kun etter avtale (oppgitt 2026-10-29; intervjuet nevnte bare 10–20). Ingen drop-in. |
| Kontakt | Telefon 469 62 914, e-post auraskin.as@hotmail.com og Instagram `instagram.com/Auraskinklinikk` (oppgitt 2026-10-29). Facebook-adressen `facebook.com/auraskinklinikk` og Messenger-navnet `m.me/auraskinklinikk` er antatt, ikke bekreftet. |
| Arbeidsflyt | Konsultasjon alltid først. Mange behandlinger må godkjennes av lege. |
| Booking | Klinikken vil ikke ha kalender eller selvbetjent booking. |
| Kanaler i dag | Facebook, Instagram og telefon. Mange meldinger og bilder på telefonen. Foretrekker private meldinger, men er åpen for å prøve noe nytt. |
| Ønsket innhold | Om oss med bilder, behandlinger med innhold og pris (f.eks. HIFU), åpningstider. |
| Ønsket kontakt | «Send melding»-side som videresendes til behandleren på SMS, Facebook og/eller Instagram, pluss lenker til SMS, Facebook, Instagram og e-post. |
| Ønsket kundekommunikasjon | SMS om avtalte timer, nyhetsbrev, push-varsler. |

### 2.2 Problemene nettsiden løser

- Kunder spør om det samme igjen og igjen: hva behandlingene innebærer, pris, åpningstider og om man kan komme uten avtale.
- Store mengder private meldinger og bilder må besvares manuelt ved siden av behandlingene.
- Bekreftelser og påminnelser sendes for hånd.
- Klinikken har ingen egen kanal til kundene, bare sosiale medier.
- En side på sosiale medier signaliserer mindre etablering enn en egen nettside.

### 2.3 Hvorfor ikke en ferdig bookingplattform

Timma, Fresha, Eazybook, Bookingtjeneste.no, ProClinic og Planfy er bygget rundt selvbetjent booking. Det passer ikke når konsultasjon og legegodkjenning kommer først. En egen nettside gir tilpasning til arbeidsflyten, klinikkens egen merkevare og en egen kanal til kundene. Fra plattformene beholdes det som er bransjestandard: behandlingskatalog med pris, SMS-bekreftelse og -påminnelse, og nyhetsbrev.

### 2.4 Rammer fra research (2026-10-28)

Funnene under styrer kravene i §5, §7, §9 og §10. Kildene og graden av sikkerhet står i research-rapporten. «Verifisert» betyr at et uavhengig kildested bekreftet funnet; resten er `[ASSUMPTION]` til lovteksten er lest.

| Tema | Funn | Sikkerhet |
|---|---|---|
| Omtale av legemidler | Å navngi botox, botulinumtoksin, virkestoff eller kodeord («toksin», «BTX») på klinikkens nettside og sosiale medier regnes som forbudt reklame for reseptpliktig legemiddel (Direktoratet for medisinske produkter, tidl. Legemiddelverket; vedtak 2025-04-23, tvangsmulkt 5 000 kr per dag). Nøytrale betegnelser som «rynkebehandling» ser ut til å være tillatt, men er en slutning fra veilederen, ikke et godkjent ordvalg. | `[ASSUMPTION]`, lest via sammendrag |
| Prislister | Prislister er tillatt så lenge de ikke inneholder påstander om legemiddelet. Kilder er uenige om merkenavn kan stå i prislister. | `[ASSUMPTION]` |
| Markedsføring av kosmetiske inngrep | Forskrift FOR-2005-07-01-749: ingen før- og etter-bilder (§ 5), medisinsk ansvarlig skal navngis med kontaktinformasjon (§ 4), ikke rettet mot under 18 (§ 4). Gjelder også injeksjoner og fillers. | Verifisert (Lovdata) |
| Utøvere | Kosmetiske injeksjoner kan bare utføres av helsepersonell (helsepersonelloven § 4 a), og ikke på under 18 år uten medisinsk begrunnelse (§ 4 b). | Verifisert |
| Direkte markedsføring | Forskriften § 7 ser ut til å forby markedsføringshenvendelser om kosmetiske inngrep til forbrukere på e-post og SMS. Markedsføringsloven § 15 krever forhåndssamtykke for e-post og SMS-markedsføring. | `[ASSUMPTION]` (§ 7 lest én gang via sammendrag) |
| Meta | Et nettskjema kan ikke legge en melding i klinikkens Messenger- eller Instagram-innboks. Meta åpner meldingsvinduet (24 timer) bare når kunden skriver først. `m.me`- og `ig.me`-lenker er den støttede veien inn. | Verifisert (med forbehold: «ikke mulig» er utledet av vindusreglene) |
| Meta: bilder og chat-plugin | Om bilder sendt via `m.me`/`ig.me` kommer frem i klinikkens innboks er ikke sjekket. Chat-pluginen er rapportert fjernet i mai 2024, bare bekreftet av tredjepart. | Uverifisert |
| FAQ | Google fjernet FAQ-rike resultater i 2026. Ingen kilde viste at en FAQ-side reduserer henvendelser eller hjelper søkerangering. | Verifisert (Google), ellers ingen belegg |
| Push på iPhone | Krever at nettsiden er lagt til på hjemskjermen (WebKit 2023, caniuse). Status for 2026 og EU/EØS er ikke bekreftet. | Delvis verifisert |
| Konkurrenter (fire klinikker i **Molde-området**, ikke Karmøy) | Bare Skin Clinic Molde viser priser åpent. To av fire har FAQ. Én har resultatside med bilder (se før/etter-forbudet). Ingen viste nyhetsbrev, Messenger eller kontaktskjema. Undersøkelsen ble satt opp for feil sted. Funnene gir et bilde av hva klinikker i bransjen viser på nettsiden, men er ikke en konkurrentanalyse for Karmøy. | Lav (n = 4, feil område) |

## 3. Målgrupper

### 3.1 Behov som skal dekkes

**Kunden** (fra mobil, oftest)
- Finne ut raskt hva klinikken tilbyr, hvem behandlerne er, hva en behandling innebærer og hva den koster.
- Vite om en behandling krever konsultasjon eller legegodkjenning.
- Ta kontakt for å avtale konsultasjon på en enkel måte, uten å lete etter riktig kanal.
- Få svar på vanlige spørsmål uten å måtte spørre (FR-21).
- Bli bekreftet og minnet på timen.
- Få nyheter og tilbud, hvis kunden ønsker det.
- Vite hva som skjer med opplysningene sine.

**Klinikken** (to ansatte, blant dem en kosmetisk sykepleier)
- Færre gjentatte spørsmål om behandlinger, priser og åpningstider.
- Få henvendelser samlet i kanalene de allerede bruker.
- Slippe å sende bekreftelser og påminnelser for hånd.
- Oppdatere innhold, bilder og priser selv, uten teknisk hjelp.
- Nå kundene direkte med nyhetsbrev og push-varsler.
- Kunne følge opp timer uten mye ekstra arbeid ved siden av behandlingene.

### 3.2 Ikke målgruppe

- Kunder som vil booke en time selv uten kontakt med klinikken.
- Kunder som vil betale på nettet.

### 3.3 Brukerreiser

**UJ-1. Ida vil prøve HIFU.**
Ida (34) ser et innlegg fra AURA SKIN Klinikk på Instagram og går inn på nettsiden fra mobilen. På behandlingssiden leser hun hva HIFU innebærer, hvor lang tid det tar, hva hun kan forvente, og hva det koster. Hun ser at behandlingen starter med en konsultasjon. Hun trykker «Send melding», fyller inn navn og telefonnummer, velger HIFU og skriver at hun helst vil komme på ettermiddagen. Skjermen bekrefter at meldingen er sendt. Behandleren får meldingen på SMS og e-post, og ringer Ida tilbake samme dag.
**Kanttilfelle:** Hvis videresendingen til én kanal feiler, kommer meldingen likevel frem på den andre kanalen og vises alltid i adminpanelet.

**UJ-2. Behandleren setter opp timen.**
Etter samtalen med Ida logger behandleren inn i adminpanelet og registrerer en konsultasjon torsdag kl. 16:00. Ida får straks en SMS med tid, sted og hva timen gjelder, og en påminnelse dagen før.

**UJ-3. Klinikken sender ut nyheter.** `[FORSLAG]`
Klinikken har en ny hudpleiebehandling å fortelle om. Behandleren skriver et nyhetsbrev og sender det til kunder som har meldt seg på. Eksempelet er under forbehold: en utsendelse kan ikke omtale injeksjons- eller fillerbehandlinger, og kan ikke være et tilbud på botulinumtoksin (se §5.4 og §2.4). Push-varsel er ikke med i første versjon.

**UJ-4. Kunden har bare et spørsmål.**
Mia lurer på hvor lenge hun må vente før hun kan trene etter en behandling. Hun finner svaret under «Vanlige spørsmål» på forsiden uten å sende melding. Klinikken slipper å svare på spørsmålet enda en gang.

## 4. Begreper

- **Behandling:** En tjeneste klinikken tilbyr, med navn, beskrivelse av hva den innebærer, varighet, pris og om den krever legegodkjenning.
- **Pris:** Fast pris («1 200 kr») eller fra-pris («fra 1 200 kr»).
- **Konsultasjon:** Første samtale med en behandler før behandling. Alltid første steg.
- **Legegodkjenning:** Godkjenning fra lege som kreves før enkelte behandlinger. Skjer utenfor nettsiden.
- **Behandler:** En ansatt som utfører behandlinger, presentert under «Om oss».
- **Melding:** En henvendelse kunden sender fra «Send melding»-siden.
- **Videresending:** At en melding automatisk sendes videre til behandleren på SMS og e-post.
- **Samtalelenke:** En lenke (`m.me` for Messenger, `ig.me` for Instagram) som åpner en samtale med klinikken der kunden skriver først.
- **Medisinsk ansvarlig:** Personen som er faglig ansvarlig for behandlingene og som skal oppgis på nettsiden.
- **Avtalt time:** En time klinikken har avtalt med kunden og registrert i adminpanelet.
- **Bekreftelse:** SMS til kunden når en avtalt time er registrert, flyttet eller avlyst.
- **Påminnelse:** SMS til kunden før en avtalt time.
- **Nyhetsbrev:** E-post klinikken sender til kunder som har meldt seg på.
- **Push-varsel:** Varsel i nettleseren eller på mobilen til kunder som har slått det på.
- **Adminpanel:** Den innloggede delen av nettsiden der klinikken styrer innhold, meldinger, timer og utsendelser.
- **Utvikler:** Rollen som drifter og vedlikeholder nettsiden. Har egen tilgang til adminpanelet.

## 5. Funksjoner

### 5.1 Informasjonssider

#### FR-1: Sidestruktur
Kunden kan navigere mellom Forside, Behandlinger (med en egen side per behandling, FR-2), Om oss, Kontakt oss og Send melding.
- Menyen er Hjem, Behandlinger, Om oss og Kontakt oss, pluss knappen «Send melding». På mobil åpnes menyen med en hamburgerknapp. Menyen har ikke «Kjøp» eller handlekurv (nettbetaling er utenfor omfanget, §8).
- Vanlige spørsmål (FR-21) ligger på forsiden, ikke som egen side eller menyvalg. «Slik foregår det» er ikke en egen side (FR-5).
- Navigasjonen fungerer på alle sider, også på mobil.
- «Send melding» er synlig på alle sider uten å scrolle på mobil: knappen ligger i menyen på datamaskin og i en fast linje nederst på skjermen på mobil.
- Faste kontaktknapper for telefon, kart og e-post ligger på alle sider, langs høyre kant på datamaskin og i den faste linjen nederst på mobil, slik klinikken viser i designeksempelet (§6). Hver knapp åpner en infoboks: telefon viser nummeret og «Ring nå», kart viser adresse, åpningstider, «Åpne i Google Maps» og «Veibeskrivelse», e-post viser adressen og «Send e-post».
- Bunnen på alle sider viser adresse, åpningstider, ikoner for Facebook og Instagram (åpnes i ny fane) og lenke til personvernerklæringen (NFR-5).
- `[ASSUMPTION: menynavnene kommer fra designforslaget og avtales med klinikken. Klinikkens eget eksempel bruker Hjem, Vårt team, Tjenester og Kontakt (§6). Om menylenkene skal åpne i ny fane er uavklart (§12 nr. 24)]`

#### FR-2: Behandlingsside
Kunden kan se alle behandlinger og åpne én for å se detaljer.
- Hver behandling viser hva den innebærer (hvordan den foregår, varighet, forventet resultat, eventuell nedetid), pris og om den krever legegodkjenning.
- Kun behandlinger klinikken har markert som synlige vises.
- Behandlinger-siden viser alle synlige behandlinger som kort med lenke til behandlingens egen side. Forsiden viser et utdrag.
- Hver behandlingsside har bilde, overskrift, kort beskrivelse, en faktaboks (varighet, pris, om legegodkjenning kreves), «Om behandlingen» og lenker til de andre behandlingene. Den sier at alle behandlinger starter med en konsultasjon.
- Fra hver behandling kan kunden gå til «Send melding» («Send melding om HIFU»). `[ASSUMPTION: behandlingen er forhåndsvalgt i skjemaet. Designforslaget viser ikke dette; avgjøres i §12 nr. 25]`
- Behandlingssider viser ikke før- og etter-bilder for injeksjons- eller fillerbehandlinger (se NFR-9).
- Priser vises uten påstander om legemiddelet (se FR-6).

#### FR-3: Om oss
Kunden kan lese om klinikken og hver behandler, med bilder av klinikken og behandlerne.
- Siden viser to behandlere, hver med portrett, navn og rolle, og en kort tekst om klinikken. Navn, roller, bilder og samtykke til å vise dem kommer fra klinikken.
- Siden oppgir hvem som er medisinsk ansvarlig og hvordan klinikken kan kontaktes (forskrift om markedsføring av kosmetiske inngrep § 4, verifisert på Lovdata).
- `[ASSUMPTION: klinikken oppgir utdanning/autorisasjon og eventuell tilknyttet lege, hvis de ønsker det vist]`

#### FR-4: Praktisk informasjon
Nettsiden viser åpningstider, at klinikken kun tar imot etter avtale (ingen drop-in), adresse, telefon, e-post, kart og parkering.
- Åpningstider (oppgitt 2026-10-29): man–fre 10–20, lør–søn 10–18, kun etter avtale. Adresse: Bøvegen 60, 4260 Salhus, Karmøy. Telefon: 469 62 914. E-post: auraskin.as@hotmail.com.
- Kontakt oss-siden viser adresse, åpningstider, telefon, e-post og parkering med små ikoner, kartet og knappene «Åpne i Google Maps» og «Veibeskrivelse». Nederst på forsiden vises fire kort for adresse, telefon, e-post og åpningstider. Samme opplysninger står i infoboksene til kontaktknappene (FR-1) og i bunnen.
- Kartet er et statisk kartbilde fra OpenStreetMap, med nål og kildeangivelsen «© OpenStreetMap-bidragsytere», som lenker til Google Maps. Lenkene bruker koordinater (59.371629, 5.288586), fordi adressen som tekst kan gi treff på Salhus ved Bergen. Et innebygd Google-kart kan sette cookies og ville krevd samtykkebanner. `[FORSLAG: statisk kartbilde med lenke]`
- Parkering: innhold fra klinikken (plassholder i designforslaget).
- `[ASSUMPTION: kartnålen ved Bøvegen 60 er plassert av OpenStreetMap og må bekreftes av klinikken (§12 nr. 23)]`

#### FR-5: Slik foregår det (under Behandlinger)
Nettsiden forklarer at alle behandlinger starter med en konsultasjon, og hva som skjer videre: ta kontakt → konsultasjon → eventuell legegodkjenning → behandling.
- Forklaringen står under Behandlinger og på behandlingssidene (FR-2), ikke på en egen side og ikke i menyen.
- `[ASSUMPTION: de fire stegene vises i en eller annen form under Behandlinger. Designforslaget har ikke stegene lenger; teksten skrives senere]`

#### FR-6: Lovlig omtale av behandlinger
Behandlinger som bruker reseptpliktige legemidler omtales uten legemiddelnavn, virkestoff, merkenavn eller kodeord. Det gjelder på hele nettsiden, i adminpanelets tekstfelt og i klinikkens egne innlegg som lenker til siden.
- Eksempler på ord som ikke brukes: «botox», «botulinumtoksin», «toksin», «BTX». Nøytrale betegnelser som «rynkebehandling» brukes i stedet.
- Prislister viser behandlingsnavn og pris, uten påstander om legemiddelet og uten rabatter eller kampanjer på behandlingen.
- Adminpanelet (FR-19) viser en påminnelse om ordlisten når klinikken skriver behandlingstekster.
- `[ASSUMPTION: nøytrale betegnelser er tillatt. DMPs veileder sier at reglene ikke regulerer markedsføring av behandlinger i seg selv, med mindre markedsføringen tydelig viser hvilke legemidler som brukes. Det finnes ingen godkjent ordlyd å vise til; DMP forhåndsgodkjenner ikke tekster]`
- `[ASSUMPTION: klinikken bekrefter hvilke behandlinger dette gjelder og hvilke betegnelser de bruker]`

#### FR-21: Vanlige spørsmål `[FORSLAG]`
Kunden kan lese svar på vanlige spørsmål om behandlinger, forberedelse, etterpå, åpningstider, avbestilling og hvem som utfører behandlingene. Klinikken redigerer spørsmål og svar i adminpanelet.
- Spørsmålene vises som en enkel utvidbar liste på forsiden. Det er ingen egen side, ingen egen widget og ikke noe menyvalg, og de står ikke på Kontakt oss-siden.
- Treffer problemet med gjentatte spørsmål direkte, men ingen kilde i researchen viser at en FAQ-liste faktisk reduserer henvendelser. Effekten måles med SM-3.
- Listen holdes liten og enkel. Den skal ikke bygges for søkemotorer: Google viser ikke lenger FAQ-rike resultater, så ingen FAQ-markering (`FAQPage`) trengs.
- Svarene følger FR-6 og NFR-9 som all annen tekst.
- `[ASSUMPTION: klinikken ønsker vanlige spørsmål på forsiden; avgjøres sammen med omfanget i §9]`

### 5.2 Send melding

#### FR-7: Sende melding
Kunden kan sende en melding til klinikken ved å oppgi navn, mobilnummer, ønsket behandling (valgfritt) og fritekst.
- Skjemaet ligger både på forsiden og på en egen Send melding-side, med de samme feltene. Knappen «Send melding» i menyen går til skjemaet på forsiden når kunden står der, og ellers til Send melding-siden. Knappene «Send melding om …» på behandlingssidene åpner Send melding-siden.
- Navn, mobilnummer og melding er påkrevd; mobilnummer valideres. «Ønsket behandling» er en nedtrekksliste med «Vet ikke ennå» og klinikkens behandlinger.
- Kunden må samtykke til at opplysningene brukes til å svare på henvendelsen, med lenke til personvernerklæringen.
- Skjemaet ber ikke om bilder eller helseopplysninger, og opplyser om at slike ikke skal sendes. `[ASSUMPTION: behandleren ber om bilder i konsultasjonen, på en måte klinikken velger]`
- Kunder som ønsker å sende bilder kan bruke samtalelenkene (FR-9). `[ASSUMPTION: bilder sendt via m.me og ig.me kommer frem i klinikkens innboks; ikke sjekket i researchen, må testes med klinikkens egen side]`
- Etter innsending vises en bekreftelse om at meldingen er sendt og at klinikken tar kontakt.
- Skjemaet er beskyttet mot spam og misbruk (hver melding kan koste en SMS).

#### FR-8: Videresending til behandleren
En innsendt melding videresendes til behandleren på SMS og e-post.
- Meldingen inneholder kundens navn, mobilnummer, ønsket behandling og fritekst.
- Feiler én kanal, sendes meldingen likevel på den andre, og den lagres alltid i adminpanelet.
- Videresending til Messenger eller Instagram er ikke et krav i første versjon. Klinikken ønsker det, og briefen (versjon 2) fører det som et ønske som avgjøres i arkitekturfasen; SMS og e-post er garantert, og samtalelenkene (FR-9) er reserveløsningen. Metas meldings-API lar en side bare svare brukere som har skrevet først, og et nettskjema er ikke en handling som åpner meldingsvinduet. `[ASSUMPTION: utledet av Metas vindusregler og API-dokumentasjon; ingen Meta-side sier ordrett at en skjemainnsending ikke kan åpne et vindu]`

#### FR-9: Direkte kontaktlenker
Kunden kan også kontakte klinikken direkte via lenker som åpner SMS (`sms:+4746962914`), Facebook Messenger (`m.me/auraskinklinikk`), Instagram eller e-post.
- Lenkene ligger ved siden av skjemaet, på forsiden og på Send melding-siden, under teksten «Vil du heller skrive i en app, eller sende bilder?».
- Instagram-knappen i designforslaget går til klinikkens profil (`instagram.com/Auraskinklinikk`). En `ig.me`-lenke åpner i stedet en samtale der kunden skriver først, og er det researchen og FR-8 bygger på. `[ASSUMPTION: profil-lenken brukes til klinikken har bestemt seg; valget står i §12 nr. 27]`
- `ig.me` virker ikke på Instagram Web; siden viser da et alternativ.
- Chat-pluginen fra Meta (innebygd chatboble) brukes ikke. Den er rapportert fjernet i 2024. `[ASSUMPTION: bekreftet bare av tredjepartskilder]`

### 5.3 Avtalte timer og SMS

#### FR-10: Registrere avtalt time
Klinikken kan registrere en avtalt time med kundens navn, mobilnummer, behandling (eller konsultasjon), dato og tid.
- Registreringen skal gå raskt (mål: under ett minutt), siden klinikken allerede følger opp timer et annet sted.

#### FR-11: SMS-bekreftelse
Kunden får SMS med dato, tid, adresse og hva timen gjelder når timen registreres.

#### FR-12: SMS-påminnelse
Kunden får en påminnelse på SMS før timen.
- `[ASSUMPTION: sendes kl. 12:00 dagen før]`

#### FR-13: Flytte og avlyse
Klinikken kan flytte eller avlyse en avtalt time, og kunden får beskjed på SMS.

#### FR-14: Timeoversikt
Klinikken kan se kommende avtalte timer i en dags- og ukesliste.

### 5.4 Nyhetsbrev og push-varsler

Omfanget av denne delen avgjøres i §9: det er uavklart om klinikken vil ha begge. Researchen gir tre begrensninger:

- **Innhold:** Forskriften om markedsføring av kosmetiske inngrep § 7 ser ut til å forby markedsføringshenvendelser om slike inngrep til forbrukere på e-post og SMS. Nyhetsbrev kan derfor ikke omtale injeksjons- eller fillerbehandlinger. Tilbud og kampanjer på botulinumtoksin er uansett forbudt (FR-6). `[ASSUMPTION: § 7 er lest én gang via sammendrag og må leses i fulltekst på Lovdata. Om forbudet også gjelder SMS-påminnelser om avtalte timer er uavklart; påminnelser er trolig tjenestemeldinger, ikke markedsføring]`
- **Samtykke:** Markedsføringsloven § 15 krever forhåndssamtykke for e-post og SMS-markedsføring. Unntaket for eksisterende kunder gjelder bare egne, tilsvarende tjenester og krever enkel, gratis avmelding. `[ASSUMPTION: lest via sammendrag]`
- **Push:** På iPhone fungerer push bare for en nettside som er lagt til på hjemskjermen. Om push faller under ekomloven § 3-15 eller markedsføringsloven § 15 er ikke avklart. Det finnes ingen data på hvor mange som slår på push. Forslag: utelat push fra første versjon.

#### FR-15: Påmelding
Kunden kan melde seg på nyhetsbrev med e-post. Push-varsler (FR-17) er ikke med i første versjon (§9); hvis klinikken ber om dem senere, kan kunden også slå dem på fra nettsiden.
- Påmelding krever aktivt samtykke, adskilt fra kontaktskjemaet.
- Hvert nyhetsbrev har en avmeldingslenke; hvis push tas med, kan varslene slås av når som helst.

#### FR-16: Sende nyhetsbrev
Klinikken kan skrive og sende et nyhetsbrev til alle påmeldte fra adminpanelet.

#### FR-17: Sende push-varsel `[FORSLAG]`
Klinikken kan skrive og sende et kort push-varsel, med lenke til en side på nettsiden, til alle som har slått det på.
- Ikke med i første versjon (§9). Kravet står her for det tilfellet at klinikken ber om push etter lansering.

### 5.5 Adminpanel

#### FR-18: Innlogging
Klinikkens ansatte og utvikleren logger inn med hver sin personlige konto.
- Bare innloggede brukere har tilgang til adminpanelet og kundeopplysninger.
- `[ASSUMPTION: tofaktor vurderes, men er ikke et krav i første versjon]`

#### FR-19: Innhold
Klinikken kan opprette, endre og skjule behandlinger (beskrivelse, pris, varighet, legegodkjenning), og endre «Om oss», behandlere, bilder, åpningstider, kontaktinformasjon og vanlige spørsmål.
- Endringer vises på nettsiden med en gang.

#### FR-20: Meldinger
Klinikken kan se alle innsendte meldinger, markere dem som besvart, og velge hvilke kanaler nye meldinger skal videresendes til.

## 6. Design og tone

Klinikken har laget et designeksempel i one.com Website Builder. Det viser stilen de ønsker. Designforslaget fra 2026-10-29 (en klikkbar skisse, ikke lagret i repoet) viser oppbyggingen av nettsiden i stilen fra eksempelet: sider og meny i FR-1, kontaktknapper i FR-1, behandlingssider i FR-2 og Send melding i FR-7.

- **Farger:** Dempet lys rosa (ca. #FFD6CC) som bakgrunn i de fargede seksjonene, hvit mellom dem, mørk rød (ca. #9B2C2C) på knapper og aksenter, mørk brun-grå (#3B2A2A) brødtekst. Fargekodene er anslått fra skjermbilder av klinikkens eksempel, og designforslaget bruker dem. `[ASSUMPTION: klinikken oppgir endelige fargekoder og logo]`
- **Typografi:** Overskrifter i en håndskrevet skriftfont, brødtekst i en ren, rund sans-serif. Designforslaget bruker Dancing Script (vekt 600) og Montserrat. Beregnet kontrast: mørk rød mot lys rosa 5,6:1, brødtekst mot lys rosa 10,2:1, hvit tekst på mørk rød 7,5:1 (WCAG AA krever 4,5:1 for vanlig tekst; beregnet for hånd fra fargekodene, ikke målt med verktøy). Tynnere skriftvekt enn i forslaget må kontrastsjekkes på nytt mot NFR-3.
- **Former:** Avrundede kort, runde knapper og ovale bildeutsnitt. Rolig og luftig, få elementer per skjerm.
- **Forsiden, i eksempelets rekkefølge:** hero med overskrift, kort tekst, hovedknapp og stort portrettbilde; en fremhevet behandling med bilde; «Vår ekspertise» med «Les mer»; tre fordelskort; kundeomtaler.
- **Forsiden i designforslaget:** hero, et utdrag av behandlinger (tre kort med «Les mer»), Send melding (skjema og kontaktlenker, FR-7 og FR-9), Vanlige spørsmål (FR-21) og Kontakt oss (fire kort, FR-4). Forslaget har ikke seksjonene for fordelskort og kundeomtaler fra klinikkens eksempel.
- **Hovedknapp:** Eksempelet har «Bestill tid». Siden har ingen booking (§8), så knappen heter «Send melding» (slik den heter i designforslaget; «Ta kontakt» er et alternativ) og går til FR-7.
- **Kundeomtaler** `[FORSLAG]`: Seksjonen tas bare med hvis klinikken har ekte omtaler med samtykke fra de som er sitert. Malens fiktive omtaler brukes ikke. Omtalene følger FR-6 og NFR-9, så de sier ingenting om resultat av injeksjons- eller fillerbehandlinger.
- **Påstander:** Malens formuleringer («avansert teknologi», «skreddersydde», «naturlige resultater», laserterapi og IPL) er plassholdere. Klinikken bekrefter hva de kan stå inne for. Laser og IPL er ikke undersøkt (NFR-9).
- **Bilder:** Bilder av klinikken og behandlerne står sentralt og bygger tillit. Malens stockbilder erstattes av klinikkens egne (§7.4).
- **Tone:** Varm, personlig og faglig trygg. Kort og tydelig språk, uten overdrevne løfter om resultater.
- **Språk:** Norsk (bokmål).
- `[ASSUMPTION: klinikken leverer logo, farger, bilder, tekster og priser]`

## 7. Tverrgående krav

### 7.1 Kvalitet

- **NFR-1 Mobil først:** Alle sider fungerer fra 360 px bredde.
- **NFR-2 Ytelse:** Sidene laster raskt på mobilnett; en kunde kan sende en melding på under 1 minutt.
- **NFR-3 Universell utforming:** WCAG 2.1 nivå AA.
- **NFR-4 Sikkerhet:** HTTPS, passord lagres ikke i klartekst, spam-beskyttelse og rate-limiting på skjemaer.
- **NFR-10 Søkesynlighet:** Sidene har beskrivende titler og tekster slik at klinikken kan bli funnet på søk som «hudpleie Karmøy». Nettsiden har `LocalBusiness`-markering (navn, adresse, åpningstider, telefon), og klinikken oppfordres til å ha en verifisert Google-bedriftsprofil. Det brukes ikke `FAQPage`-markering. `[FORSLAG]`
  - Det er ikke undersøkt hvilke nettsider som rangerer for «hudpleie Karmøy», eller om dette trenger mer enn grunnleggende tiltak.
- **NFR-11 Lokal kjøring:** Appen kan startes lokalt etter README med seed-data (fiktive behandlinger, fiktive kunder) og en test-admin. SMS, e-post og eventuelt push bruker en testversjon som logger i stedet for å sende, så ingen betalte kontoer kreves.

### 7.2 Personvern (GDPR)

- **NFR-5:** Personvernerklæring som forklarer hva som samles inn, hvorfor, hvor lenge og hvordan kunden ber om innsyn eller sletting.
- **NFR-6:** Det samles bare inn navn, mobilnummer, e-post (nyhetsbrev) og meldingstekst. Ingen helseopplysninger eller bilder (GDPR art. 9).
- **NFR-7:** Nyhetsbrev og push-varsler krever eget, aktivt samtykke, adskilt fra kontaktskjemaet (markedsføringsloven § 15). Innholdet følger i tillegg NFR-9. `[ASSUMPTION: se §5.4 for forbehold om forskriften § 7 og push]`
- **NFR-8:** Meldinger og avtalte timer slettes eller anonymiseres automatisk etter en fastsatt periode. `[ASSUMPTION: 12 måneder]`
- Leverandører av hosting, SMS, e-post og push krever databehandleravtale.

### 7.3 Lovlig markedsføring

- **NFR-9:** Nettsiden følger regelverket for markedsføring av kosmetiske behandlinger, inkludert forbudet mot reklame for reseptpliktige legemidler (se FR-6). Konkret:
  - Ingen før- og etter-bilder i markedsføring av kosmetiske inngrep, inkludert injeksjoner og fillers (forskriften § 5, verifisert).
  - Medisinsk ansvarlig og kontaktinformasjon er oppgitt (forskriften § 4, verifisert; se FR-3).
  - Markedsføringen er ikke rettet mot personer under 18 år og skal ikke nedtone risiko (forskriften § 4, verifisert). Behandlinger uten medisinsk begrunnelse utføres ikke på under 18 år (helsepersonelloven § 4 b, verifisert).
  - Ingen tilbud om forbrukerlån (forskriften § 6).
  - Tilsyn føres av Statsforvalteren og Statens helsetilsyn (forskriften § 9) og av DMP for legemidler og medisinsk utstyr.
  - Før publisering gjennomgås behandlingstekstene av klinikkens lege eller medisinsk ansvarlige. `[ASSUMPTION: gjennomgangen er klinikkens ansvar]`
  - Laserbehandling og kjemisk peeling er ikke undersøkt, og kan ha egne krav. `[ASSUMPTION]`

### 7.4 Repoet

Repoet er offentlig. Hemmeligheter ligger i `.env` utenfor Git, med `.env.example` i repoet. Ekte kundedata committes aldri. Bilder av klinikken og de ansatte legges bare i repoet etter samtykke fra klinikken; ellers brukes plassholdere.

### 7.5 Domene, hosting og overlevering `[FORSLAG]`

Nettsiden skal kunne legges på klinikkens eget domene (for eksempel `auraskin.no`) uten endringer i koden.

- **NFR-12 Domeneuavhengig:** Adresse til nettsiden, avsender-e-post og andre miljøavhengige verdier ligger i miljøvariabler (`.env.example`). Ingen adresser er hardkodet.
- **NFR-13 Overleveringsguide:** README beskriver stegene for å gå live: velge hosting, legge inn domenet hos hostingtjenesten, sette DNS-oppføringene hos registraren, sette miljøvariabler og verifisere avsenderdomenet for e-post og SMS.
- **Eierskap:** Domenet registreres av klinikken i eget navn, hos en registrar klinikken velger. Produksjonshosting og tilhørende kontoer eies av klinikken, eller overføres til klinikken ved overlevering.
- **E-post:** Hvis klinikken har e-post på domenet fra før, endres ikke MX-oppføringene. Utsending fra nettsiden krever at SPF og DKIM legges til for e-posttjenesten.
- **Hosting:** Nettsiden har admin, database og utsending, og krever hosting som kan kjøre en applikasjon, ikke ren statisk hosting. Hosting og database velges i EU/EØS (se §7.2).
- **HTTPS:** Sertifikat utstedes automatisk av hostingtjenesten når DNS peker riktig (NFR-4).
- **Demo før domene:** Før klinikken har domene og hosting på plass, kjøres en demoversjon på gratisadressen hostingtjenesten gir, slik at hele flyten (bygg, publisering, miljøvariabler) er prøvd før overlevering.

## 8. Utenfor omfang

- Kalender og selvbetjent booking: passer ikke klinikkens arbeidsflyt med konsultasjon og legegodkjenning.
- Nettbetaling.
- Kundekonto med innlogging.
- Opplasting av bilder og innsamling av helseopplysninger.
- Digital flyt for legegodkjenning.
- Andre språk enn norsk.
- Kjøp og drift av domene og produksjonshosting (klinikkens ansvar). Å gjøre nettsiden klar for klinikkens domene og levere en overleveringsguide er med (§7.5).

## 9. Omfang og fasering `[FORSLAG]`

Forslag til rekkefølge, som avtales når omfanget for nyhetsbrev og push er avklart:

1. **Kjerne:** informasjonssider (FR-1–FR-6, FR-21), Send melding med SMS og e-post (FR-7–FR-8), samtalelenker til Messenger og Instagram (FR-9), adminpanel for innhold og meldinger (FR-18–FR-20).
2. **Timer:** registrering av avtalte timer med SMS-bekreftelse og -påminnelse (FR-10–FR-14).
3. **Nyhetsbrev:** FR-15–FR-16, begrenset til innhold som ikke omtaler injeksjons- eller fillerbehandlinger, og først etter at forskriften § 7 og markedsføringsloven § 15 er lest i fulltekst og avklart.
4. **Push (FR-17):** ikke med i første versjon. Vurderes bare hvis klinikken ber om det etter lansering.

Videresending til Messenger og Instagram via Metas API er ikke med i første versjon. Klinikkens ønske om det avgjøres i arkitekturfasen, etter at klinikken har svart om Facebook-siden og Instagram-kontoen (spørsmål 1) og Meta-reglene er testet (FR-8, §10).

## 10. Risikoer

| Risiko | Konsekvens | Tiltak |
|---|---|---|
| Meta tillater ikke at et nettskjema sender meldinger inn i klinikkens innboks. Meta er bygget for at kunden skriver først. (Inntruffet: researchen bekrefter at det ikke er mulig.) | Klinikkens ønske om videresending til Messenger og Instagram oppfylles ikke. | FR-8 er endret til SMS og e-post pluss `m.me`- og `ig.me`-lenker (FR-9). Ønsket står i briefen og avgjøres i arkitekturfasen. Test at bilder via lenkene kommer frem i klinikkens innboks. |
| Bilder fra kunder kommer ikke frem via `m.me`/`ig.me`. | Klinikken får bildene på en annen måte enn i dag. | Test med klinikkens egen side før lansering; ellers avtal bildeopplasting i konsultasjonen (spørsmål 14). |
| Nyhetsbrev om kosmetiske inngrep er forbudt (forskriften § 7). | FR-15–FR-16 kan ikke brukes til tilbud på injeksjoner og fillers. | Begrens innholdet; les § 7 og markedsføringsloven § 15 i fulltekst og avklar med klinikkens lege eller DMP før bygging. |
| SMS-misbruk eller spam på skjemaet. | Kostnad og støy. | Rate-limiting, bot-beskyttelse, tak på utsending (NFR-4). |
| Dobbeltføring av timer gjør at klinikken slutter å bruke registreringen. | SMS-påminnelser uteblir, SM-4 oppnås ikke. | Hurtig registrering (FR-10), test med klinikken. |
| Push virker dårlig på iPhone. | Lav nytte av FR-17. | Vurder å droppe eller utsette push (§9). |
| Ulovlig omtale av reseptpliktige behandlinger. | Brudd på legemiddelforskriften. DMP har ilagt tvangsmulkt på 5 000 kr per dag (2025). | Ingen legemiddelnavn eller kodeord (FR-6), gjennomgang av tekster med klinikkens lege før publisering (NFR-9), spørsmål til DMP om uklare tilfeller. |
| Bilder eller tekster fra konkurrenter eller klinikkens egne kanaler bryter før/etter-forbudet. | Brudd på forskriften § 5. | Ikke kopier resultatsider med bilder; se NFR-9. |
| Personopplysninger sendes via Meta og SMS-leverandør. | GDPR-krav om databehandleravtale, mulig tredjelandsoverføring. | Avklar i arkitekturfasen (NFR-5–NFR-8). |
| Klinikken leverer ikke innhold (tekster, bilder, priser) i tide. | Nettsiden kan ikke publiseres. | Plassholdere og tidlig be om innholdet. |
| Malens tekster, stockbilder og fiktive kundeomtaler fra designeksempelet publiseres uendret. | Uriktige påstander, ugyldige omtaler og uavklart bildelisens. | Bruk eksempelet bare som stil (§6). Alt innhold byttes mot klinikkens eget og gjennomgås etter NFR-9. |

## 11. Suksesskriterier

**Primære**
- **SM-1:** Klinikken oppdaterer innhold, registrerer timer og sender utsendelser selv uten hjelp fra utvikleren. Følges opp de første 4 ukene etter lansering. Validerer FR-10–FR-16 og FR-18–FR-20 (FR-17 bare hvis push tas med, §9).
- **SM-2:** En ny kunde finner pris og innhold for en behandling og sender en melding på mobil på under 2 minutter. Måles med brukertest med 3–5 personer. Validerer FR-1–FR-9.
- **SM-3:** Færre gjentatte spørsmål om pris, behandlinger og åpningstider. Klinikken anslår antall henvendelser og gjentatte spørsmål per uke før lansering og etter 2 måneder.

**Sekundære**
- **SM-4:** Færre uteblitte timer etter innføring av SMS-påminnelser. Validerer FR-12.
- **SM-5:** Nettsiden består en WCAG 2.1 AA-sjekk før lansering. Validerer NFR-3.

**Motvekt**
- **SM-C1:** Antall utsendelser. Nyhetsbrev og push skal være nyttige, ikke hyppige; for mange utsendelser fører til avmeldinger. Motvekt til FR-16–FR-17.

**Funksjonelle kontroller (testbare)**
1. Behandlingssiden viser hver synlige behandling med innhold og pris.
2. En innsendt melding vises i adminpanelet og kommer frem på SMS og e-post; kunden får bekreftelse på skjermen.
3. Direkte lenker (SMS, `m.me`, Instagram, e-post) åpner riktig kanal på mobil.
4. Når klinikken endrer innhold, vises endringen på nettsiden uten at utvikleren gjør noe.
5. Når klinikken registrerer en time, sendes SMS-bekreftelse og senere påminnelse.
6. Kunder kan melde seg på og av nyhetsbrev, og klinikken kan sende til de påmeldte (push avgjøres i §9).
7. Adminpanelet er kun tilgjengelig etter innlogging.
8. Appen kan startes lokalt etter README med seed-data (NFR-11).
9. Ingen side bruker legemiddelnavn, kodeord eller før- og etter-bilder av injeksjons- eller fillerbehandlinger, og medisinsk ansvarlig er oppgitt (FR-3, FR-6, NFR-9).
10. Kontaktknappene (telefon, kart, e-post) ligger på alle sider, også på mobil, og hver åpner riktig infoboks med riktig lenke. Google Maps-lenkene lander ved Bøvegen 60 på Karmøy (FR-1, FR-4).
11. Menyvalgene og lenkene mellom Forside, Behandlinger, behandlingssidene, Om oss, Kontakt oss og Send melding fører til riktig side (FR-1).

## 12. Åpne spørsmål

**Må avklares før PRD-en låses**

| # | Spørsmål | Hvem |
|---|---|---|
| 1 | Facebook-siden er bekreftet som en bedriftsside, og Instagram-kontoen er en profesjonell konto koblet til den (2026-10-29). Hvem er administrator? Holder det med SMS og e-post som mottakskanal, med `m.me`/`ig.me`-lenker for de som vil skrive i Messenger eller Instagram, eller vil klinikken fortsatt ha forsøk på videresending til Meta (§2.4, FR-8)? (Spørsmål 6–7 i `kundeintervju/sporsmal-oppfolging.md`.) | Klinikken |
| 2 | Hvilke behandlinger finnes, hva koster de, og hvilke krever legegodkjenning? «Hifo» er bekreftet som HIFU (2026-10-29). | Klinikken |
| 3 | Hvem er legen (ansatt, ekstern, samarbeidspartner), og skal siden nevne legen? | Klinikken |
| 4 | Hvilke behandlinger bruker reseptpliktige legemidler, og hvilke betegnelser skal brukes? | Klinikken |
| 5 | Skal meldinger gå til én felles mottaker eller til en bestemt behandler? Hvilket mobilnummer? | Klinikken |

**Kan avklares senere**

| # | Spørsmål | Hvem |
|---|---|---|
| 6 | Hvem betaler for SMS-utsending, og hva er forventet volum? | Klinikken |
| 7 | Klinikken har ingen nettside i dag (bekreftet 2026-10-29). Domene og hosting: har klinikken et domene eller e-post på eget domene, hvem eier og administrerer det, og hvilken e-postløsning brukes på det? Forslag i §7.5: klinikken eier domene og hosting, utvikleren leverer en overleveringsguide. Designeksempelet er laget i one.com Website Builder, trolig på en gratisplan; det er ikke bekreftet at klinikken har et domene eller webhotell hos one.com. Hvis de har webhotell der, må det sjekkes om det kan kjøre en applikasjon (§7.5). | Klinikken og utvikleren |
| 8 | Når skal nettsiden være ferdig? | Klinikken |
| 9 | Adresse: Bøvegen 60, 4260 Salhus (oppgitt 2026-10-29). Kommunen (Karmøy) er ikke bekreftet av klinikken (spørsmål 23 i `kundeintervju/sporsmal-oppfolging.md`). | Klinikken |
| 10 | Logo, endelige farger, stil og bilder. Designeksempelet bruker malens stockbilder og tekster; hvilke egne bilder og tekster skal erstatte dem? Kan bilder og tekster fra Facebook ligge i et offentlig repo? | Klinikken |
| 11 | Ønsker klinikken nyhetsbrev og push, hvor ofte, og hvem skriver innholdet? | Klinikken |
| 12 | Hva er antall henvendelser og gjentatte spørsmål per uke i dag (baseline for SM-3)? | Klinikken |
| 13 | Skal forsiden ha en liste med vanlige spørsmål (FR-21)? | Klinikken og utvikleren |
| 14 | Hvordan skal bilder fra kunder håndteres i konsultasjonen, siden nettsiden ikke tar imot dem? Kommer bilder sendt via `m.me`/`ig.me` frem i klinikkens innboks? (Test med klinikkens egen side.) | Klinikken og utvikleren |
| 15 | Forskriften § 7 (FOR-2005-07-01-749) og markedsføringsloven § 15: forbyr de nyhetsbrev om kosmetiske inngrep, og gjelder det SMS-påminnelser? Les lovteksten på Lovdata og avklar med klinikkens lege eller Statens helsetilsyn. | Utvikleren |
| 16 | Hva endrer lovendringen LOV-2026-06-19-42 (i kraft 2026-07-01) i helsepersonelloven? | Utvikleren |
| 17 | Kan merkenavn stå i en prisliste? Kilder er uenige. Spør DMP. | Utvikleren |
| 18 | Hvem er medisinsk ansvarlig, og hvem hos klinikken gjennomgår behandlingstekstene før publisering? | Klinikken |
| 19 | Hvilke regler gjelder for laserbehandling og kjemisk peeling (hvem kan utføre dem, hva kan sies)? Ikke undersøkt. | Utvikleren |
| 20 | Hvilke nettsider rangerer for «hudpleie Karmøy», og hva har de felles? Krever manuelt Google-søk fra stedet. Konkurrentoversikten er laget for Molde-området, ikke Karmøy. | Utvikleren |
| 21 | Skal siden ha kundeomtaler (§6)? Har klinikken ekte omtaler, og samtykke fra de som er sitert? | Klinikken |
| 22 | Hovedknappen i eksempelet heter «Bestill tid». Er «Send melding» (som i designforslaget) eller «Ta kontakt» greit, siden klinikken ikke vil ha booking? Er menyen i designforslaget (Hjem, Behandlinger, Om oss, Kontakt oss og knappen Send melding) greit, i stedet for eksempelets (Hjem, Vårt team, Tjenester, Kontakt)? | Klinikken |
| 23 | Stemmer Facebook-adressen (`facebook.com/auraskinklinikk`), Messenger-navnet (`m.me/auraskinklinikk`) og kartnålen ved Bøvegen 60 (FR-4, FR-9)? | Klinikken |
| 24 | Skal menylenkene åpne i ny fane (FR-1)? Ønsket er nevnt, men ikke presisert. | Utvikleren |
| 25 | Skal behandlingen være forhåndsvalgt i skjemaet når kunden kommer fra en behandlingsside (FR-2, FR-7)? Designforslaget viser det ikke. | Utvikleren |
| 26 | Kartløsning på den ferdige siden: statisk kartbilde med lenke til Google Maps (som i forslaget) eller innebygd Google-kart? Innebygd kart kan sette cookies og krever samtykkebanner (FR-4). | Utvikleren |
| 27 | Skal Instagram-knappen åpne klinikkens profil (som i designforslaget) eller en samtale via `ig.me` (FR-9)? | Klinikken og utvikleren |

## 13. Antakelser

- §5.1 FR-3: Klinikken oppgir utdanning/autorisasjon og eventuell tilknyttet lege, hvis de ønsker det vist.
- §5.1 FR-6: Klinikken bekrefter hvilke behandlinger som må omtales uten legemiddelnavn. Nøytrale betegnelser som «rynkebehandling» er tillatt (slutning fra DMPs veileder, ikke en godkjent ordlyd).
- §5.1 FR-21: Klinikken ønsker vanlige spørsmål på forsiden.
- §5.2 FR-7: Behandleren ber om bilder i konsultasjonen, og bilder sendt via `m.me`/`ig.me` kommer frem i klinikkens innboks.
- §5.2 FR-8: Meta tillater ikke videresending fra nettskjema (utledet av vindusreglene).
- §5.2 FR-9: Meta-chat-pluginen er fjernet (bare tredjepartskilder).
- §5.4: Forskriften § 7 forbyr e-post- og SMS-markedsføring om kosmetiske inngrep til forbrukere (lest én gang via sammendrag). Push faller under samme samtykkekrav (ikke avklart).
- §2.4: Konkurrentoversikten fra Molde-området sier noe om bransjen, men ikke om konkurransen på Karmøy.
- §7.3 NFR-9: Klinikkens lege eller medisinsk ansvarlige gjennomgår behandlingstekstene. Laser og kjemisk peeling har ikke vært undersøkt.
- §5.3 FR-12: Påminnelsen sendes kl. 12:00 dagen før.
- §5.5 FR-18: Tofaktor er ikke et krav i første versjon.
- §6: Klinikken leverer logo, farger, bilder, tekster og priser. Fargekodene i §6 er anslått fra skjermbilder av designeksempelet.
- §5.1 FR-1: Menynavnene (fra designforslaget) er ikke endelige, og det er uavklart om menylenkene åpner i ny fane.
- §5.1 FR-2: Behandlingen er forhåndsvalgt i skjemaet når kunden kommer fra en behandlingsside (ikke vist i designforslaget).
- §5.1 FR-4: Kartnålen ved Bøvegen 60 er riktig, og et statisk kartbilde med lenke til Google Maps er løsningen (ikke bekreftet av klinikken).
- §5.1 FR-5: De fire stegene (ta kontakt, konsultasjon, eventuell legegodkjenning, behandling) vises i en eller annen form under Behandlinger.
- §5.2 FR-9: Facebook-adressen og Messenger-navnet (`auraskinklinikk`) er antatt, ikke bekreftet. Instagram-knappen går til profilen til klinikken har valgt.
- §7.2 NFR-8: Opplysninger slettes etter 12 måneder.
