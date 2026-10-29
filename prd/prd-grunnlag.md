---
title: "PRD-grunnlag: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-10-28
updated: 2026-10-28
---

# PRD-grunnlag: AURA SKIN Klinikk – nettside

Samlet utgangspunkt for å skrive (eller revidere) PRD-en. Dokumentet samler det som er avklart, det som er uklart, hva som bør undersøkes og diskuteres, og hva brukerne trenger. Det erstatter ikke `product-brief/brief.md` eller `prd/prd.md`, men peker til dem.

**Kilder:** `product-brief/brief.md`, `product-brief/addendum.md`, `prd/prd.md`, `prd/addendum.md`, `kundeintervju/sporsmal.md` (notater 2026-10-28), `product-brief/tilbakemelding-product-brief.md`, loggene i `.logs/mikolaj/`.

---

## 1. Det som er avklart

| Tema | Avklart (kilde: intervju 2026-10-28 om ikke annet er sagt) |
|---|---|
| Klinikken | AURA SKIN Klinikk, Bøvegen 60, 4260 Salhus (Karmøy). To ansatte, blant dem en kosmetisk sykepleier. |
| Kapasitet | Rundt 3 kunder om dagen, ca. 1 time hver. |
| Åpningstider | 10–20. Kun etter avtale, ingen drop-in. |
| Arbeidsflyt | Konsultasjon alltid først. Mange behandlinger må godkjennes av lege. |
| Booking | Klinikken vil **ikke** ha kalender eller selvbetjent booking. |
| Kontakt i dag | Facebook, Instagram og telefon. Mange meldinger og bilder på telefonen. Foretrekker private meldinger, men er åpen for å prøve noe nytt. |
| Ønsket innhold | Om oss (presentasjon, bilder av klinikk og behandlere), behandlinger med hva de innebærer og pris (f.eks. HIFU), åpningstider. |
| Kontakt via nettsiden | «Send melding»-side som videresender til behandleren på SMS, Facebook og/eller Instagram, pluss direkte lenker til SMS, Facebook, Instagram og e-post. |
| Kundekommunikasjon | SMS om avtalte timer, nyhetsbrev, push-varsler. |
| Utenfor omfang | Nettbetaling, kundekonto, opplasting av bilder/helseopplysninger, digital legegodkjenning, domene og produksjonshosting. |
| Krav fra veiledning | Lokal kjøring med seed-data og test-admin, uten betalte kontoer. SMS/e-post/push testes uten ekte utsending. Repoet er offentlig: ingen hemmeligheter eller ekte kundedata. |

**Status på dokumentene:** Briefen og PRD-en (FR-1–FR-20, NFR-1–NFR-9) er omskrevet etter intervjuet og ligger i `main`. Delene 1–7 i `kundeintervju/sporsmal.md` er de opprinnelige bookingspørsmålene og er stort sett utdatert; notatene og oppfølgingsdelen nederst er det som gjelder.

---

## 2. Brukerbehov

### Kunden
Slik det står i dag (PRD §2.1) pluss det intervjuet og bransjen tyder på:

| Behov | Dekket i PRD? |
|---|---|
| Forstå hva en behandling innebærer, varighet, nedetid og pris | Ja (FR-2) |
| Vite om behandlingen krever konsultasjon eller legegodkjenning | Ja (FR-2, FR-5) |
| Se hvem behandlerne er, og kunne stole på dem (utdanning, bilder, tilknyttet lege) | Delvis (FR-3). Utdanning/autorisasjon nevnes ikke. |
| Finne åpningstid, adresse, parkering, kart | Delvis (FR-4). Parkering nevnes ikke. |
| Ta kontakt raskt fra mobil, i kanalen man selv foretrekker | Ja (FR-7–FR-9) |
| Få svar på vanlige spørsmål uten å måtte spørre (hvordan forbereder jeg meg, hva skjer etterpå, er det trygt for meg) | **Nei.** Ingen FAQ-side. |
| Bli bekreftet og minnet på timen | Ja (FR-11–FR-13) |
| Vite hva som skjer med opplysningene mine | Ja (NFR-5–NFR-8) |
| Finne klinikken via Google («hudpleie Karmøy») | **Nei.** Ikke omtalt (synlighet i søk). |

### Klinikken
| Behov | Dekket i PRD? |
|---|---|
| Færre gjentatte spørsmål | Ja, indirekte (FR-2, FR-4). Kan styrkes med FAQ. |
| Meldinger samlet der de allerede svarer | Delvis, avhenger av Meta (FR-8) |
| Slippe manuelle bekreftelser og påminnelser | Ja (FR-10–FR-13) |
| Oppdatere innhold selv | Ja (FR-19) |
| Nå kundene direkte | Ja (FR-15–FR-17) |
| Enkel hverdag: lite ekstra jobb å vedlikeholde siden | Ikke målt. Se §5, punkt om dobbelt føring av timer. |
| Håndtere bilder kunder sender | **Ikke løst.** Siden ber kunder om ikke å sende bilder, men klinikken får dem på Messenger/Instagram i dag. |

---

## 3. Uklare spørsmål

Sortert etter hvor mye svaret påvirker PRD-en.

### Må avklares før PRD-en låses

1. **Messenger/Instagram-videresending (FR-8).** Seks oppfølgingsspørsmål står ubesvart i `kundeintervju/sporsmal.md`: bedriftsside eller privat profil? Instagram-bedriftskonto koblet til siden? Hvem er administrator? Foretrukket mottakskanal, og holder SMS? Felles mottaker eller per behandler? Hvilket nummer?
2. **Hvilke behandlinger finnes, og hva koster de?** Ingen behandlingsliste eller prisliste er mottatt. «HIFU» er eneste navngitte behandling, og «Hifo» i notatene er ikke bekreftet som HIFU.
3. **Hvilke behandlinger krever legegodkjenning**, og hvem er legen (ansatt, ekstern, fast samarbeidspartner)? Skal siden nevne legen?
4. **Reseptpliktige legemidler (FR-6/NFR-9).** Hvilke behandlinger bruker slike, og hvilke betegnelser vil klinikken bruke?
5. **Mottaker per melding.** Én felles mottaker eller den behandleren kunden velger? Skal kunden kunne velge behandler?

### Kan avklares senere, men påvirker kravene

6. **Hvem betaler for SMS** (videresending, bekreftelser, påminnelser)? Hva er forventet volum og budsjett?
7. **Bedriftskontoer** på Facebook og Instagram, og hvem eier dem.
8. **Domene og hosting:** finnes noe i dag, og hvem eier det?
9. **Frist:** når skal nettsiden være ferdig?
10. **Klinikkens sted:** adressen er Bøvegen 60, 4260 Salhus (oppgitt 2026-10-29; tidligere dokumenter sa Haugesund). Bekreft kommunen (Karmøy) med klinikken.
11. **Logo, farger, stil og bilder.** Spørsmål 13–15 fra den opprinnelige lista er ikke besvart i notatene. Kan bilder og tekster fra Facebook ligge i et offentlig repo?
12. **Påminnelsestidspunkt (FR-12):** antatt kl. 12:00 dagen før. Bekreft.
13. **Oppbevaringstid (NFR-8):** antatt 12 måneder. Bekreft.
14. **Nyhetsbrev og push:** hvor ofte, hvem skriver, og er det reelt ønsket eller bare «fint å ha»? Intervjuet nevner det som ønske uten at det er utdypet.

### Svakheter i selve dokumentene
- `kundeintervju/sporsmal.md` har fortsatt ingress og spørsmål om «bookingnettsiden».
- Brief og PRD gir ingen målbar baseline: hvor mange spørsmål og meldinger får klinikken i uka i dag? (Opprinnelig spørsmål 16 er ubesvart, og SM-3 er avhengig av tallet.)
- Ingen språkvalg utover norsk. Bekreft at norsk holder.

---

## 4. Hva bør undersøkes nærmere

| Tema | Hva som må undersøkes | Hvorfor |
|---|---|---|
| **Metas API** | Om et nettskjema kan sende en melding inn i klinikkens Messenger- eller Instagram-innboks. | Se §6. Avgjør om FR-8 kan bygges som skrevet. |
| **Reserveløsning for Meta** | Om Meta Business Suite sin samlede innboks (Facebook og Instagram på ett sted) dekker behovet «der de allerede svarer», kombinert med `m.me`/`ig.me`-lenker på siden. | Kan være enklere og mer robust enn et eget API-oppsett. Må verifiseres med klinikken. |
| **SMS-leverandør** | Pris, avsendernavn, norske leverandører (Sveve, Link Mobility, 46elks, Twilio), databehandleravtale, krav til testmodus. | FR-8, FR-11–FR-13. |
| **Misbruk av SMS** | Rate-limiting og bot-beskyttelse. Hvert innsendte skjema kan koste en SMS til behandleren. | Kostnad og spam (FR-7). |
| **Lovverk for markedsføring av kosmetiske behandlinger** | Legemiddelforskriften (reseptpliktig reklame), markedsføringsloven, og om det finnes krav til omtale av injeksjonsbehandlinger og før/etter-bilder. Hos Statens legemiddelverk og Forbrukertilsynet. | NFR-9. Må sjekkes før tekster publiseres, ikke bare antas. |
| **GDPR og tredjeland** | Meldinger via Meta og SMS-leverandør: hvor lagres data, og trengs databehandleravtale? Hva når kundens navn og nummer havner i behandlerens private Messenger/Instagram? | NFR-5–NFR-8. |
| **Samtykke og e-post** | Skjemaet samler mobilnummer, men nyhetsbrev krever e-post. Hvordan skal påmelding til nyhetsbrev og push skilles fra kontaktskjemaet? | FR-15, NFR-7. |
| **Web Push på iPhone** | Fungerer bare når nettsiden er lagt til på hjemskjermen. | Reduserer nytten av FR-17 for mange kunder. |
| **Påminnelsesjobb** | Planlagt jobb (cron) for FR-12 både lokalt og i produksjon. | Teknisk risiko. |
| **Lokal kjøring** | Mock av SMS, e-post, push og Meta som logger i stedet for å sende. | Krav fra veiledningen. |
| **Konkurrent- og referansesider** | Se hvordan 5–10 norske hudpleie- og skjønnhetsklinikker presenterer behandlinger, pris og kontakt. `.docs/research/competition` inneholder bare spørsmålet «hvilke konkurrenter eksisterer?». | Research-grunnlaget er tynt. |

---

## 5. Ideer og funksjoner som bør diskuteres

### Mangler i dag, bør vurderes
- **FAQ / «Vanlige spørsmål».** Treffer problemet «mange gjentatte spørsmål» direkte, og er billig å lage.
- **Forhåndsvalgt behandling i «Send melding»** (allerede i FR-2) – bekreft at det virker godt på mobil.
- **«Bli oppringt»-alternativ** i stedet for kun fritekst, med foretrukket tidspunkt.
- **Hva skal skje med bilder?** Siden sier «send ikke bilder», men klinikken får dem i dag. Avklar en trygg måte (f.eks. at behandleren ber om dem i konsultasjonen).
- **Lokal synlighet:** sidetittel, beskrivelser og Google Business-profil for «hudpleie Karmøy».
- **Anmeldelser/omtaler** som innholdselement (bransjestandard), med forbehold om markedsføringsregler.
- **Behandlervalg** hvis to behandlere har ulik kompetanse.

### Kan være for mye, bør diskuteres
- **Push-varsler.** Begrenset støtte på iPhone, lite volum (3 kunder om dagen), og risiko for avmeldinger. Er det verdt å bygge i første omgang?
- **Nyhetsbrev.** Krever e-postinnsamling, avmelding, leveringsrate og innhold fra klinikken. Hvem skriver, og hvor ofte?
- **Registrering av timer i adminpanelet.** Klinikken registrerer timer et sted fra før (telefon, notatblokk). Dobbeltføring kan bli en hindring; fordelen er SMS-bekreftelse og -påminnelse. Test at flyten tar under ett minutt.
- **Tofaktor** for admin (nevnt i addendum). Nødvendig, eller bare ønskelig?
- **Mer enn én kanal per melding.** Hver ekstra kanal er ekstra feilkilde og kostnad. Kan man starte med SMS og legge til Meta senere?

### Fasering som kan avtales
1. Informasjonssider + «Send melding» med SMS/e-post + direkte lenker + adminpanel for innhold og meldinger.
2. Registrering av timer med SMS-bekreftelse og påminnelse.
3. Nyhetsbrev, deretter push.
4. Videresending til Messenger/Instagram hvis Meta tillater det.

Dette er kun et forslag til diskusjon, ikke et vedtak.

---

## 6. Lignende løsninger å lære av

| Løsning | Hva den gjør | Hva vi kan lære |
|---|---|---|
| **Timma, Fresha, Eazybook, Bookingtjeneste.no, ProClinic, Planfy** | Ferdige bookingplattformer med behandlingskatalog, SMS-påminnelser, kampanjer. Abonnement (Eazybook fra 249 kr/mnd). | Behandlingskatalog med pris og beskrivelse og SMS-påminnelser er forventet standard. Selvbetjent booking passer ikke her. |
| **Klinikknettsider med «Be om konsultasjon»-skjema** | Kunden sender en forespørsel, klinikken ringer opp. Vanlig for estetisk medisin og kosmetiske inngrep. | Samme arbeidsflyt som AURA SKIN. Se på hvor lite skjemaet kan være, og hvordan bekreftelsen formuleres. (Eksempler bør innhentes, se §4.) |
| **Meta Business Suite (samlet innboks) + `m.me`/`ig.me`-lenker** | Facebook- og Instagram-meldinger på ett sted; lenker som åpner en samtale i appen. | Mest sannsynlige måte å oppfylle «der de allerede svarer». Meta sin Messenger-chat-plugin er faset ut (2024), og `m.me`-lenker omtales som den støttede veien. |
| **Messenger Platform / Instagram Messaging API** | Meta sitt offisielle API for å svare kunder. | Gir kontroll, men krever bedriftskonto, godkjent app, og er bygget for at *kunden skriver først*. |
| **SMS-tjenester (Sveve, 46elks m.fl.)** | Sender SMS via API med avsendernavn. | Enkelt å bygge og enkelt å teste med mock. |

**Om Meta (verifiser mot Metas egen dokumentasjon):** søk viste at 24-timersvinduet åpnes av at brukeren skriver til siden, trykker en knapp, klikker på en annonse eller bruker en `m.me`-lenke. Å sende en melding fra et nettskjema inn i klinikkens egen innboks er ikke et standard bruksområde, og jeg fant ikke bekreftelse på at det er mulig. Dette er kilder fra tredjepart og Metas policyside, ikke en endelig avklaring.

---

## 7. Områder der vi trenger mer informasjon før beslutning

| Beslutning | Mangler | Hvem kan svare |
|---|---|---|
| Hvilken videresendingsløsning (FR-8) | Svar på seks Meta-spørsmål, test av hva Meta tillater | Klinikken + utvikler |
| Omfang av nyhetsbrev og push | Er det reelt ønsket, hvor ofte, hvem skriver | Klinikken |
| Hvor mye adminpanelet skal gjøre | Hvordan klinikken følger opp timer i dag | Klinikken |
| Innhold og struktur på behandlingssiden | Behandlingsliste, priser, hva som krever lege | Klinikken |
| Formulering av behandlinger | Hvilke betegnelser lovverket tillater | Klinikken + Legemiddelverket/Forbrukertilsynet |
| SMS-løsning og kostnad | Leverandør, volum, hvem betaler | Klinikken + utvikler |
| Design | Logo, farger, bilder, samtykke til bilder i offentlig repo | Klinikken |
| Teknisk stakk | Alt over, pluss lokal kjøring og planlagt jobb | Utvikler (arkitekturfasen) |
| Suksessmål | Baseline: antall henvendelser og gjentatte spørsmål i uka | Klinikken |
| Tidsplan | Frist | Klinikken + veileder |

---

## 8. Forslag til rekkefølge videre

1. Send klinikken en kort samlet spørreliste med punktene i §3 («må avklares før PRD-en låses»).
2. Test hva Meta tillater (eller konkluder med reserveløsningen) og oppdater FR-8.
3. Beslutt omfang for nyhetsbrev og push (diskuter §5).
4. Oppdater PRD-en med svar, fjern utdaterte antakelser i §10, og legg til FAQ-siden hvis den vedtas.
5. Gå videre til UX-design og arkitektur.
