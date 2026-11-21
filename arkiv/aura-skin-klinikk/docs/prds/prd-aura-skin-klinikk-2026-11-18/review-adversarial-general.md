# Adversarial review: PRD AURA SKIN Klinikk – nettside (versjon 6)

Gjennomgått: `prd/prd.md` (versjon 6, 2026-11-18) og `prd/addendum.md`. Ingen PRD-filer er endret.
Metode: kryssjekk av FR/NFR mot §9, §8, §11, §12 og §13; vurdering av bygbarhet innen 2026-12-15 med én utvikler; jus- og personverngjennomgang; feil- og kanttilfeller. Sitater er hentet ordrett fra PRD-en. Jusspåstander som ikke er lest i lovtekst i denne gjennomgangen er merket «bør verifiseres».

## Konklusjon

**Ikke klar til å låse som grunnlag for «live 2026-12-15».** Kravene i kjernen er rimelig konkrete, men PRD-en har tre grunnleggende svakheter:

1. Alt som må være avklart før publisering (HIFU-klassifisering, medisinsk ansvarlig, lege, behandlinger og priser) står under «Kan avklares senere», og klinikken har ikke svart på noe ennå.
2. Personvernkravene motsier funksjonene. NFR-6 sier «ingen helseopplysninger», men SMS, skjema og timeregistrering bærer behandlingsnavn og fritekst. Retting, sletting og feilhåndtering er lovet i prosa, men ikke kravsatt.
3. Omfanget (21 FR, 15 NFR, test, live-sette) er ikke realistisk på rundt fire uker for én person, og avskjæringen er uklar. §11 og §9 er også uenige om hva som kreves for å regnes som ferdig.

Antall funn: **3 kritiske, 8 høye, 11 middels, 6 lave** (totalt 28).

---

## KRITISKE

### K1. Alt som må avklares før publisering står under «Kan avklares senere»

- **Funn:** §12 «Må avklares før PRD-en låses» har bare nr. 1–5. Under «Kan avklares senere» ligger nr. 18 (medisinsk ansvarlig), nr. 19 (laser/peeling), nr. 28 (HIFU som kosmetisk inngrep), nr. 15 (markedsføringsloven § 15, SMS-påminnelser) og nr. 10 (bilder og tekster). Likevel krever FR-3 at siden «oppgir hvem som er medisinsk ansvarlig» (forskriften § 4), og NFR-9 krever at «klinikkens lege eller medisinsk ansvarlige» gjennomgår tekstene før publisering. Funksjonell kontroll 9 (§11) sier at «medisinsk ansvarlig er oppgitt». Siden skal gå live 2026-12-15, men klinikken har «ikke svart ennå» (§0), og §12 har ingen frister for klinikken.
- **Hvorfor kritisk:** Nr. 28 gjelder klinikkens «fremste eksempel» (§10, HIFU). Svaret avgjør før/etter-bilder, nyhetsbrev, hvilke tekster som kan stå på siden og om forskriften § 4 (risiko, under 18) gjelder fullt ut. Nr. 3/18 og nr. 4 er duplikater eller overlapper, og de står i ulike tabeller.
- **Fiks:** Flytt nr. 2, 3, 4, 18, 28 og 10 til «blokkerer publisering». Gi hver en frist og en eier. Anbefalt: innholdsfrys 2026-12-01. Legg inn en fallback i PRD-en: uten svar publiseres HIFU uten bilder og uten resultatpåstander, eller siden publiseres uten HIFU-siden. Slå sammen nr. 3 og 18.

### K2. NFR-6 («ingen helseopplysninger») motsier funksjonene; rettsgrunnlag og avmelding for SMS til kunder er ikke behandlet

- **Funn:**
  - NFR-6: «Ingen helseopplysninger eller bilder (GDPR art. 9)». Men FR-7 har fritekstfelt og behandlingsvalg. FR-11 sender SMS med «hva timen gjelder». FR-10 lagrer navn, mobilnummer og behandling. FR-2 viser «om legegodkjenning kreves». Hvem som har time til HIFU, peeling eller andre behandlinger, og som trenger legegodkjenning, er opplysninger om helse eller i grenseland til det. «Skjemaet … opplyser om at slike ikke skal sendes» (FR-7) er ingen kontroll, siden kunder skriver symptomer i fritekst uansett.
  - Meldingen videresendes til behandleren på vanlig SMS og e-post (FR-8). Det er ukrypterte kanaler, og mottakeradressen er en `hotmail.com`-adresse (§2.1). Det er en forbrukertjeneste uten databehandleravtale.
  - FR-10–FR-13: Kunden registreres av klinikken, ikke av kunden selv. PRD-en nevner ikke rettsgrunnlag (GDPR art. 6), informasjon til kunden (art. 13/14) eller hvordan en kunde som svarer «STOPP» eller ber om å slippe SMS blir håndtert. NFR-7 dekker bare nyhetsbrev og push.
  - Ingen krav om validering eller bekreftelse av mobilnummer i FR-10. Feil nummer betyr at en fremmed får SMS med navn, tid og behandling («hva timen gjelder»).
- **Fiks:**
  - (a) Endre NFR-6 til å være ærlig: «Siden behandler opplysninger som kan avsløre helseforhold (behandlingstype, fritekst)». Velg et rettsgrunnlag og dokumenter det, for eksempel art. 6 (1)(b) for timer og art. 6 (1)(a) for skjemaet. Vurder art. 9 (2)(a) eksplisitt samtykke for fritekst, og få klinikkens personvernrådgiver eller en jurist til å bekrefte.
  - (b) Reduser innholdet i SMS: bekreftelse og påminnelse nevner dato, tid, sted og «time hos AURA SKIN», ikke behandlingsnavn. Videresendingen til behandleren inneholder bare navn, nummer og «ny melding, se adminpanelet» (innholdet leses i panelet).
  - (c) Legg til krav om informasjon til kunden når klinikken registrerer en time, og om hvordan kunden ber om at SMS stoppes (manuell «ikke send SMS»-flagg i FR-10).
  - (d) Valider norsk mobilnummer i FR-10 (se M1).

### K3. Omfanget rekker ikke på fire uker, og avskjæringen er ikke testbar eller konsistent

- **Funn:**
  - §9 pkt. 1 «Kjerne» omfatter FR-1–FR-9, FR-18–FR-21, pluss NFR-1–NFR-9, NFR-11–NFR-15. Det er innholdsstyring, innlogging, skjema med spam-vern, SMS og e-post med feilhåndtering, databehandleravtaler, WCAG 2.1 AA, sletting etter 12 måneder, daglig backup, miljøvariabler og overleveringsguide, i tillegg til hosting, domene og DNS (§7.5). Pkt. 2 (FR-10–FR-14) kommer i tillegg, med planlagt jobb.
  - Det er ingen estimat, ingen rekkefølge innen kjernen, og ingen grense for hva som kuttes først. Kravet om at siden skal «kjøres live hos klinikken etter tester» (§9) har ingen definisjon av «tester», og ingen tid til dem. SM-2 krever brukertest med 3–5 personer og SM-5 en WCAG-sjekk før lansering.
  - Avhengighetene er utenfor utviklerens kontroll: klinikkens innhold (nr. 2, 10, 18), domene og hosting (nr. 7), SMS-leverandør og -avtale, e-postleverandør.
  - Intern uenighet: §9 pkt. 3 sier nyhetsbrev bygges «bare hvis tiden rekker», og §10 sier «Nyhetsbrev utsettes uten at kjernen påvirkes». Men SM-1 (§11) validerer «FR-10–FR-16», og funksjonell kontroll 6 krever at «Kunder kan melde seg på og av nyhetsbrev, og klinikken kan sende». Suksesskriteriene er altså ikke oppnåelige hvis planen følges.
  - SM-1 følges opp «de første 4 ukene etter lansering», altså etter fristen, uten at det står hvem som er ansvarlig for oppfølgingen og hvem som drifter siden da (se H3).
- **Fiks:** Lag en «minimumsrelease» som er den eneste definisjonen av ferdig 2026-12-15: FR-1–FR-5, FR-7–FR-9, FR-18–FR-20 med enklest mulig FR-19. Flytt FR-21, FR-10–FR-14 og FR-15–FR-16 til «etter lansering» (eller bare FR-10–FR-12 hvis de skal med). Fjern FR-14 og FR-13 fra første versjon (klinikken ser timene i telefonen, og avlysning kan være en ny registrering). Oppdater SM-1 og kontroll 6 slik at de bare gjelder det som faktisk bygges. Sett inn en testuke og en fast cut-line (for eksempel 2026-12-08). Skriv inn avhengighetene med datoer.

---

## HØYE

### H1. Spam-beskyttelse og kart motsier NFR-14 («ingen ressurser fra tredjepart»)

- **Funn:** NFR-14: «laster ingen ressurser fra tredjepart som sender besøkendes IP-adresse dit … Siden trenger da ikke samtykkebanner». Kontroll 12: «laster ingen fonter, kart eller skript fra tredjepart». NFR-4 og FR-7 krever «spam-beskyttelse» og «enkel bot-beskyttelse». Standardløsningene (reCAPTCHA, hCaptcha, Turnstile) er tredjepartsskript som setter eller leser data og sender IP. PRD-en sier ikke hvilken løsning som er tillatt. FR-4 beskriver samtidig kartbildet som en antakelse: «kartflisene hentes fra OpenStreetMaps flistjener … bildet lagres heller som egen fil». §13 sier «Kartbildet lagres som egen fil» som om det var avgjort, mens bruksvilkårene for fliser «ikke er lest».
- **Fiks:** Skriv at spam-vern er serverside (honeypot, tidsfelle, rate-limit per IP og per nummer, utsendelsestak) uten tredjepartsskript. Kartbildet skal være en egen fil i repoet (avgjort, ikke antakelse), med kildeangivelse etter ODbL. Fjern det motstridende forbeholdet i FR-4.

### H2. Videresending (FR-8) og påminnelser: ingen feildeteksjon, retry eller varsling

- **Funn:**
  - FR-8: «Feiler én kanal, sendes meldingen likevel på den andre, og den lagres alltid i adminpanelet». Det står ingenting om hva som skjer hvis begge feiler, eller hvordan en feil oppdages. En SMS-leverandør som godtar kallet har ikke levert meldingen, og hotmail slipper ofte e-post fra ny avsender i søppelpost, spesielt før SPF og DKIM er satt opp (§7.5, «Demo før domene»).
  - Skjermen bekrefter «at meldingen er sendt» (FR-7) uavhengig av om noen faktisk fikk den. UJ-1 lover «ringer Ida tilbake samme dag».
  - Admin er eneste sikkerhetsnett, men det finnes ingen ulest-markering, varsling eller krav til at noen sjekker. FR-20 lar klinikken «velge hvilke kanaler nye meldinger skal videresendes til». Dermed kan begge kanaler slås av uten at det synes (strider mot FR-8 «videresendes til … SMS og e-post»).
  - Ingen kø, retry, tidsavbrudd, feillogg eller leveringskvittering. Ingen test for feil (kontroll 2 tester bare at alt virker).
- **Fiks:** Legg til krav: sendestatus per kanal lagres (sendt, levert, feilet), automatisk retry (for eksempel 3 forsøk), og feilstatus vises tydelig i adminpanelet med teller for uleste og feilede. Låse minst én kanal på («kan ikke slå av begge»). Bekreftelsesteksten til kunden skal ikke love svar innen en tid. Legg til testtilfelle: leverandør nede, ugyldig mottaker, e-post i søppelpost.

### H3. Databehandler, drift og tilgang er ikke avklart

- **Funn:** NFR-5–NFR-8 og §7.2 sier at «Leverandører av hosting, SMS, e-post og push krever databehandleravtale». Utvikleren selv er ikke nevnt, men har egen konto i adminpanelet (FR-18) og «drifter og vedlikeholder» siden (§4). Utvikleren er dermed databehandler for klinikken og trenger avtale. Klinikken er behandlingsansvarlig, og det står ingen steder. FR-18: «Alle brukere har samme rettigheter», så utvikleren ser alle kundeopplysninger permanent. Ingen krav til hvem som drifter siden etter 2026-12-15 (sikkerhetsoppdateringer, nedetid, backup-restore, hva som skjer hvis utvikleren slutter). NFR-15 sier backup tas, men ingen krav om restore-test. §10 sier «Avklar i arkitekturfasen» om tredjelandsoverføring til Meta og SMS-leverandør, men hosting «i EU/EØS» er bare nevnt i §7.5. SMS-leverandørene i addendumet (Twilio er amerikansk) og e-posttjenestene (Mailchimp, MailerLite) er ikke vurdert mot dette.
- **Fiks:** Legg inn et eget krav: «Klinikken er behandlingsansvarlig; utvikleren er databehandler med skriftlig avtale». Velg SMS- og e-postleverandør med EU/EØS-behandling og avtale før bygging. Skill utviklerkontoen fra de ansattes (eller deaktiver den etter overlevering). Skriv inn drift: hvem svarer ved feil, svartid, hvem betaler, og en restore-test før lansering.

### H4. Innsyn og sletting er lovet, men ingen funksjon finnes; oppbevaring er antakelse

- **Funn:** NFR-5 skal forklare «hvordan kunden ber om innsyn eller sletting». FR-19 og FR-20 har ingen funksjon for å slette en melding, en kunde eller en påmeldt, eller eksportere data. NFR-8: «Meldinger og avtalte timer slettes … `[ASSUMPTION: 12 måneder]`» er verken regnet fra innsending eller fra timen. Den gjelder ikke nyhetsbrev-adresser, samtykkelogg, adminkontoer, access-logger, rate-limit-data (IP) eller leverandørenes loggfiler (SMS-innhold lagres ofte hos leverandøren). NFR-15 (30 dagers backup) er ikke koblet til «slett nå»-forespørsler. Samtidig krever personvernerklæringen (NFR-5) «hvor lenge», og det er ennå en antakelse. Hvis klinikken bruker timeregisteret som erstatning for journal, kan sletting etter 12 måneder bryte journalkrav (helsepersonelloven, «bør verifiseres»).
- **Fiks:** Legg til FR: «Klinikken kan slette en melding, en kunde og en påmeldt, og eksportere en kundes data». Definer oppbevaring per datatype og tidspunkt (for eksempel 12 måneder etter siste kontakt, nyhetsbrevadresse til avmelding pluss samtykkelogg i tre år). Si eksplisitt at nettsiden ikke er journal, og at klinikkens journalsystem er separat. Gjør 12 måneder til en beslutning før bygging, siden NFR-5 ikke kan skrives uten den.

### H5. Nyhetsbrev: samtykkebevis mangler, innholdet kan bli tomt, og lovteksten er ulest

- **Funn:**
  - FR-15 krever «aktivt samtykke, adskilt fra kontaktskjemaet», men ingen bekreftelse på e-post (double opt-in) og ingen samtykkelogg. Hvem som helst kan melde en annens adresse på. Beviset for samtykke ligger hos klinikken, som selger (markedsføringsloven § 15, «bør verifiseres»).
  - Markedsføringsloven § 15 er «ikke hentet ordrett» (§0, §5.4, §13) og bygger likevel kravene i NFR-7 og FR-15. §9 pkt. 3 sier at loven «skal leses ordrett før bygging», altså er en bygget funksjon avhengig av et ulest dokument.
  - §5.4 og NFR-9: nyhetsbrev kan ikke omtale injeksjoner, fillers eller «inngrep i hud og underhud», og HIFU er utelatt «til det er avklart». Da er det uklart hva klinikken kan skrive i et nyhetsbrev. UJ-3 foreslår et brev om «en ny hudpleiebehandling», og selve eksempelet kan falle under «inngrep i hud og underhud» (forskriften § 3).
  - §12 nr. 11: «Ønsker klinikken nyhetsbrev og push, hvor ofte, og hvem skriver innholdet?» er ubesvart, mens §2.1 sier at klinikken ønsker det.
- **Fiks:** Anbefaling: dropp FR-15–FR-16 fra første versjon (se K3). Hvis de beholdes: double opt-in, samtykkelogg med tidspunkt og kilde, avmelding med ett klikk, og en innholdsregel («bare åpningstider, ferie, nyheter om klinikken, ikke behandlinger»). Les markedsføringsloven § 15 før kravene skrives som endelige. Skriv om UJ-3.

### H6. Påminnelser og timer (FR-10–FR-14): ikke testbare og med åpne kanttilfeller

- **Funn:**
  - FR-12 «sendes kl. 12:00 dagen før» er en antakelse. Ikke definert: time bestilt mindre enn 24 timer før (da blir påminnelsen aldri sendt, eller sendes umiddelbart?), omlegging eller avlysning etter at påminnelsen er planlagt (FR-13 sier bare at «kunden får beskjed på SMS»), eller jobb som ikke kjørte (nedetid, gratis hosting som sover, sommertid). «Påminnelser … krever en planlagt jobb» (addendum) uten krav om at den er idempotent, slik at en kunde ikke får to eller null SMS.
  - FR-10 har ingen validering mot datoer i fortiden, dobbeltbooking, lukkede dager eller tider utenfor åpningstid (§2.1). FR-14 viser en liste, men ingen regel for utløpte eller avlyste timer.
  - SM-4 «Færre uteblitte timer» har ingen baseline (§12 nr. 12 gjelder bare gjentatte spørsmål), og systemet registrerer ikke uteblitte timer. Målet kan ikke måles.
  - «Mål: under ett minutt» (FR-10) har ingen testprosedyre.
  - Avsender: alfanumerisk avsendernavn (addendum) kan ikke besvares, og det står ikke hvordan kunden avlyser eller flytter (ring?).
- **Fiks:** Skriv regler: «Er det under 24 timer til timen, sendes bare bekreftelsen»; «flytting og avlysning kansellerer planlagt påminnelse og sender ny»; «jobb kjører hvert 5. minutt og markerer sendt (idempotent)»; SMS-teksten angir telefonnummer for avlysning. Legg til valideringsregler i FR-10. Fjern SM-4 eller legg til felt «møtte opp» og en baseline.

### H7. Overdrevne sikkerhetsmarkører og interne motsigelser om hva som er verifisert

- **Funn:**
  - §10 rad 1: «(Inntruffet: researchen bekrefter at det ikke er mulig.)». FR-8, §2.4 og §13 sier at det er «utledet … ingen Meta-side sier ordrett at en skjemainnsending ikke kan åpne et vindu». §2.4 merker det «Verifisert (med forbehold)». Tre ulike graderinger for samme påstand.
  - §13 punkt 7: forskriften § 7 er «lest én gang via sammendrag», mens §0, §2.4, §5.4 og §12 nr. 15 sier den er «lest på Lovdata 2026-11-18». §2.4 sier samtidig at bare første del av setningen er ordrett.
  - §12 nr. 16 er listet som «Avgjort … utviklerens beslutninger», men er en jusspåstand («gir ingen nye krav til nettsiden»), ikke en beslutning.
  - Alle «Avgjort»-radene i §12 (inkludert nr. 6, SMS-kostnad bæres av klinikken, og live hos klinikken) er utviklerens beslutninger, ikke klinikkens. §9 og §7.5 bruker dem som om de var avtalt.
  - NFR-14: «Siden trenger da ikke samtykkebanner». Server- og rate-limit-logger som lagrer IP-adresser er også behandling av personopplysninger og må stå i personvernerklæringen (NFR-5), selv uten banner.
  - §6 «Beregnet kontrast … for hånd» brukes som grunnlag for AA-krav, men er ikke målt.
  - NFR-2 «brukbare på under 3 sekunder … 4G» er et mål uten måleverktøy («velges i arkitekturfasen»).
- **Fiks:** Bruk én skala for sikkerhet i hele dokumentet (lest ordrett, lest sammendrag, utledet, antatt). Rett §10 rad 1 og §13 punkt 7. Flytt nr. 16 til «Kilde, ikke beslutning» og merk «Avgjort av utvikler, ikke bekreftet av klinikken» der klinikken påvirkes. Bytt NFR-14s påstand til «trenger ikke samtykkebanner for cookies, men IP-logging beskrives i personvernerklæringen». Gi NFR-2 en målemetode (Lighthouse mobil, throttling) og et bestått-nivå.

### H8. HIFU-håndteringen er delvis: risiko, «forventet resultat» og alder er ikke kravsatt

- **Funn:** NFR-9 behandler HIFU som kosmetisk inngrep bare for to ting: før/etter-bilder og nyhetsbrev. Men forskriften § 4 (som PRD-en selv siterer: «skal ikke nedtone risiko», «ikke rettet mot personer under 18 år») gjelder alt innhold hvis HIFU er kosmetisk inngrep. FR-2 krever at hver behandling viser «forventet resultat» og «eventuell nedetid», men ingen risiko- eller bivirkningsseksjon. FR-19 har ikke felt for risiko. UJ-1 beskriver HIFU-siden med «hva du kan forvente». Ingen mekanisme sikrer at kundene ikke er under 18 (FR-7 tar ingen alder, og skjemaet kan ikke avvise). Kundeomtaler (§6) er begrenset til «ingenting om resultat», men HIFU-omtaler kan likevel bryte regelen. Prisen skal oppgis (FR-2, «Pris»), men PRD-en sier ikke at prisen er inkl. mva (bør verifiseres mot markedsførings- og prisopplysningsreglene). Ehandelsloven § 8 (bør verifiseres) krever tjenesteyterinformasjon (organisasjonsnummer m.m.) på nettsiden; det står ikke i bunnteksten (FR-1).
- **Fiks:** Legg til obligatoriske felt i FR-19/FR-2: «Risiko og bivirkninger» og «Aldersgrense 18 år», og krev at begge vises på behandlingssiden. Legg inn «ikke for under 18 år» i skjema og tekst. Legg organisasjonsnummer, firmanavn og pris inkl. mva i bunnen og prisvisning. Når HIFU-svaret kommer (nr. 28), oppdater alle berørte FR i én endring i stedet for å spre forbeholdene.

---

## MIDDELS

### M1. Telefonnummer og SMS-format
- FR-7: «mobilnummer valideres», FR-10 har ingen validering, FR-9 hardkoder `sms:+4746962914`. Ikke spesifisert: norsk 8-sifret nummer (starter på 4 eller 9) eller utenlandsk (studenter, turister), mellomrom og `+47` eller `0047`, fasttelefon (kan ikke motta SMS).
- SMS-lengde: fritekst med æøå gir UCS-2 (70 tegn per segment i stedet for 160) og flere segmenter, altså høyere kostnad. FR-8 sier «fritekst» skal videresendes uten lengdebegrensning.
- **Fiks:** Spesifiser tillatte formater og normalisering til E.164, avvis fasttelefon, sett maks tegn for fritekst (for eksempel 500) og kutt eller henvis til adminpanelet i SMS.

### M2. Duplikatinnsending
- FR-7 har ingen beskyttelse mot dobbeltklikk, tilbake-knapp og ny innsending, eller innsending fra to skjemaer (forsiden og egen side, FR-7). Hver innsending kan koste en SMS (FR-7: «hver melding kan koste en SMS»).
- Rate-limiting og «tak på utsendelser mot misbruk» (§12 nr. 6, NFR-4) har ingen tall og ingen oppførsel ved nådd tak (får ekte kunder avvist?).
- **Fiks:** Idempotens-token per skjema, deaktiver knapp etter klikk, slå sammen like meldinger (samme nummer og tekst innen 10 min) og definer tall (for eksempel 3 per nummer per time, 200 SMS per døgn) og feilmelding til kunden.

### M3. Testbarhet av kvalitetskravene
- NFR-1 «de to siste versjonene av Safari (iOS), Chrome og Samsung Internet» krever testutstyr som ikke er nevnt. NFR-3 (WCAG 2.1 AA) og SM-5 har ingen metode (automatisk verktøy, manuell sjekk med skjermleser). Infobokser med tastaturfelle og fast bunnlinje (FR-1) er risikoområder. NFR-4 «passord lagres ikke i klartekst» er en lav terskel uten krav til hashing-algoritme, passordregler eller tilbakestilling.
- **Fiks:** Skriv testmetode og bestått-nivå per NFR (for eksempel axe + manuell tastaturtest på 5 sider, BrowserStack eller to egne enheter). Legg til krav om passordhash (argon2/bcrypt), lengde, låsing etter feil, og tilbakestilling.

### M4. Innlogging uten roller og uten tofaktor mens kundedata ligger i panelet
- FR-18: «Alle brukere har samme rettigheter», «tofaktor … ikke et krav». Panelet inneholder navn, telefon og fritekst om hud og helse (K2). Ingen sesjonsutløp, ingen kontooversikt, ingen logg over hvem som så eller endret hva.
- **Fiks:** Krev sesjonsutløp, tofaktor eller sterke passord for admin, og en enkel endringslogg. Eller flytt utviklerkontoen ut av produksjon (H3).

### M5. FR-20 og «behandleren» er udefinert
- FR-20: «velge hvilke kanaler nye meldinger skal videresendes til», og FR-8: «videresendes til behandleren». Spørsmål 5 («én felles mottaker eller en bestemt behandler? Hvilket mobilnummer?») er ubesvart under «Må avklares». To ansatte, men ingen regel for hvem som mottar, hva som skjer ved ferie eller sykdom, eller om «besvart» er per person.
- **Fiks:** Bestem at alle meldinger går til ett nummer og én e-postadresse som settes i `.env` og kan endres i panelet. Skriv det i FR-8 og fjern kanalvalget fra FR-20 (H2).

### M6. Rekkefølge og SM-kriterier etter fristen
- SM-1 (4 uker etter lansering), SM-3 (baseline før lansering og etter 2 måneder, uten statistikk jf. NFR-14) og SM-4 ligger etter 2026-12-15. SM-3 krever baseline fra §12 nr. 12, som står under «Kan avklares senere». SM-2 (brukertest 3–5 personer) har ingen plassering i planen. Uten statistikk (NFR-14) finnes ingen måling av skjemaets bruk.
- **Fiks:** Skill «før lansering» (SM-2, SM-5) fra «etter lansering» (SM-1, SM-3, SM-4). Flytt nr. 12 til «blokkerer» (kort telling i to uker). Vurder teller i admin (antall meldinger per uke) som erstatning for statistikk.

### M7. FR-6 går utenfor det siden kan kontrollere, og er ikke testbar
- FR-6 gjelder også «klinikkens egne innlegg som lenker til siden». PRD-en kan ikke kreve noe av Instagram- og Facebook-innlegg, bare av nettsiden. Kontroll 9 «Ingen side bruker legemiddelnavn, kodeord» er ikke testbar uten en ordliste. Eksempelordene (botox, toksin, BTX) er ikke uttømmende (merkenavn, «bot.tox», bilder av legemiddelet, jf. addendum). Adminpanelet «viser en påminnelse» (ikke blokkering). §12 nr. 17 (merkenavn i prisliste) er uavklart, men FR-6 forbyr allerede merkenavn.
- **Fiks:** Begrens FR-6 til nettsiden og adminpanelet. Legg ordlisten som vedlegg og implementer en enkel sperre i adminfeltene (advarsel som må kvitteres, eller blokk). Skriv kontroll 9 som en søketest mot ordlisten.

### M8. FR-21 (vanlige spørsmål) er helsefaglig innhold uten gjennomgang
- FR-21 inkluderer «forberedelse, etterpå» (UJ-4: «hvor lenge må jeg vente før jeg kan trene»). Det er medisinsk råd. NFR-9 krever lege-gjennomgang av «behandlingstekstene», men nevner ikke FAQ eksplisitt. §13 har fortsatt FR-21 som antakelse, mens §12 nr. 13 sier «avgjort … uten å vente på klinikken».
- **Fiks:** Skriv at FAQ-svar om etterbehandling godkjennes av medisinsk ansvarlig, eller kutt FR-21 fra første versjon (K3).

### M9. Demoversjon og seed-data kan bli en sikkerhetsrisiko
- §7.5 «Demo før domene» kjører en offentlig demo på hostingtjenestens gratisadresse. NFR-11 krever «seed-data … og en test-admin». En offentlig demo med standard test-admin er et åpent adminpanel. Gratisplaner sover ofte, noe som bryter påminnelsesjobben (H6). Demoadressen kan indekseres av søkemotorer med fiktive behandlinger og priser. Repoet er offentlig (§7.4) og viser hele koden, inkludert rate-limit-logikk.
- **Fiks:** Krev at seed og test-admin aldri kjøres i produksjon (miljøsjekk), `noindex` og passordbeskyttelse (basic auth) på demo, og at produksjon bruker egne hemmeligheter. Velg hosting som ikke sover for produksjon.

### M10. Hardkodede verdier mot NFR-12
- NFR-12 sier «Ingen adresser er hardkodet». FR-9 lister `sms:+4746962914`, FR-4 koordinater og adresse, og FR-1 gjentar adresse og åpningstider i bunn, infobokser og fire kort. `LocalBusiness`-markering (NFR-10) bruker samme data. FR-19 lar klinikken endre «åpningstider, kontaktinformasjon».
- **Fiks:** Én kilde for kontaktdata (konfig eller database), brukt av alle visninger, lenker og markering. Koordinater som konfig. Skriv det som krav i FR-4.

### M11. Alder og samtykke i skjemaet
- NFR-9 og forskriften § 4: ikke rettet mot under 18. Skjemaet (FR-7) kan sendes av ungdom, og samtykket (GDPR art. 8, aldersgrense for samtykke i Norge, bør verifiseres) er ikke aldersvurdert. Ingen avvisningsrutine for henvendelser fra mindreårige.
- **Fiks:** Legg inn «Du må være 18 år eller eldre» ved skjemaet og en rutine for behandleren.

---

## LAVE

### L1. Navn og nummerering
- Kravene står i filen i rekkefølgen FR-21 etter FR-6, og NFR-10, NFR-14, NFR-15 foran NFR-11. «Numrene er stabile» er ivaretatt, men leseren må lete. §12 mangler synlig nr. 6, 8, 13, 16, 24–27 i de åpne tabellene (de står under «Avgjort»), noe som ser ut som hull.
- **Fiks:** Sorter, eller legg en kort indeks over FR/NFR med status (bygges i v1 / senere).

### L2. Prosjektstatus og kilder
- §0 viser til `prd/prd-grunnlag.md` (finnes) og `product-brief/brief.md`, men designforslaget er «en privat artefakt … ikke lagret i repoet». Flere krav (FR-1, FR-4, FR-7, §6) refererer til det som kilde.
- **Fiks:** Lagre en eksport (skjermbilder eller HTML) i repoet, uten klinikkens innhold hvis det er sensitivt.

### L3. Kontaktlenker som kan feile
- `m.me`- og `ig.me`-navnene er antatt (§12 nr. 23). `sms:` virker ikke på datamaskin. `ig.me` virker ikke på Instagram Web (FR-9, ok), og i appnettlesere kan lenker oppføre seg ulikt. Kontroll 3 «åpner riktig kanal på mobil» krever klinikkens kontoer og telefon.
- **Fiks:** Skriv en fallback per enhet (på datamaskin vis nummer og e-post som tekst). Legg lenketesting inn i testplanen før lansering.

### L4. Fast bunnlinje på mobil
- FR-1 plasserer «Send melding» og tre kontaktknapper i én fast linje på 360 px (NFR-1). Det kan dekke innhold, skjemafelt (tastaturet) og bunnteksten.
- **Fiks:** Test på 360 px med tastatur åpent, og tillat at linjen skjules mens skjemaet fylles ut.

### L5. Dobbeltskjema og menyoppførsel
- FR-7: «Knappen «Send melding» i menyen går til skjemaet på forsiden når kunden står der, og ellers til Send melding-siden». Kontekstavhengig oppførsel er dyrere å bygge og teste enn én konsistent regel.
- **Fiks:** La knappen alltid gå til Send melding-siden, og la forsiden ha en kort lenke dit.

### L6. Faktiske kilder og kostnader
- Addendum bruker «gratisplaner (undatert)» og «prisen ligger typisk på noen titalls øre per melding» uten kilde eller leverandørvalg. Kostnad til SMS er «klinikkens» (§12 nr. 6), men ingen anslag per måned.
- **Fiks:** Legg inn et budsjettanslag (3 kunder per dag, bekreftelse, påminnelse og videresending) og la klinikken godkjenne det.

---

## Oppsummert etter alvorlighet

| Alvorlighet | Antall | Funn |
|---|---|---|
| Kritisk | 3 | K1–K3 |
| Høy | 8 | H1–H8 |
| Middels | 11 | M1–M11 |
| Lav | 6 | L1–L6 |

## Anbefalt rekkefølge for oppfølging

1. K1 og K3: lås innholdsfrys, minimumsrelease og avhengighetsdatoer.
2. K2, H3, H4: personvernpakken (rettsgrunnlag, SMS-innhold, databehandleravtaler, sletting, oppbevaring).
3. H2, H6, H1: feilhåndtering og retry for SMS, e-post og påminnelser, og serverside spam-vern.
4. H5, H7, H8: nyhetsbrev (kutt eller double opt-in), ensartet sikkerhetsgradering, og HIFU-risiko og alder i FR-2/FR-19.
