# Validation Report — PRD: AURA SKIN Klinikk – nettside (versjon 6)

- **PRD:** `prd/prd.md`
- **Rubric:** `.claude/skills/bmad-prd/assets/prd-validation-checklist.md`
- **Run at:** 2026-11-18T13:02:32+01:00
- **Grade:** Fair

## Overall verdict

Dette er en uvanlig ærlig og velfundert PRD: visjonen er konkret (konsultasjon først, ingen selvbetjent booking), avgrensningene er eksplisitte, og de juridiske usikkerhetene er merket i stedet for å glattes over. Det som setter lanseringen 2026-12-15 i fare, er ikke mangel på substans, men tre ting: lanseringskritiske spørsmål er klassifisert som «kan avklares senere», regelverket (forskriften § 7, HIFU som kosmetisk inngrep) kan tømme fase 2–3 (SMS-påminnelser og nyhetsbrev) uten at scope-logikken sier hva som da skjer, og SMS-, timer- og adminkravene (FR-10–FR-20) mangler testbare konsekvenser.
Den adversarielle gjennomgangen skjerper bildet og vurderer PRD-en som «ikke klar til å låse» (3 kritiske funn). Den peker på tre ting rubrikken bare berører: personvernkravene motsier funksjonene (NFR-6 «ingen helseopplysninger» mot behandlingsnavn i skjema og SMS, uten rettsgrunnlag eller STOPP-rutine), omfanget (21 FR + 15 NFR + test + live-sette) er ikke realistisk på rundt fire uker for én person, og NFR-14 («ingen tredjepart») strider mot spam-vern og kart. Karakteren er satt til Fair etter rubrikken (ingen kritiske funn der); med den adversarielle vurderingen alene ville den vært lavere.

## Dimension verdicts
- Decision-readiness — adequate
- Substance over theater — adequate
- Strategic coherence — adequate
- Done-ness clarity — thin
- Scope honesty — strong
- Downstream usability — adequate
- Shape fit — strong

## Findings by severity

### Critical (3)
**[Adversarial]** — K1 Alt som må avklares før publisering står under «Kan avklares senere» (§12 nr. 2, 3, 4, 10, 18, 19, 28)
HIFU-klassifisering, medisinsk ansvarlig, lege, behandlinger og priser kreves av FR-3, NFR-9 og kontroll 9 før publisering, men klinikken har ikke svart og §12 har ingen frister.
Fix: Flytt til «blokkerer publisering» med frist (anbefalt innholdsfrys 2026-12-01) og fallback: uten svar publiseres HIFU uten bilder og resultatpåstander, eller uten HIFU-siden. Slå sammen nr. 3 og 18.

**[Adversarial]** — K2 NFR-6 «ingen helseopplysninger» motsier funksjonene; rettsgrunnlag og STOPP mangler (NFR-6, FR-7, FR-8, FR-10–FR-13)
Fritekst, behandlingsvalg og SMS med «hva timen gjelder» kan avsløre helseforhold. Videresending går over vanlig SMS og en hotmail-adresse. Ingen rettsgrunnlag (art. 6), informasjon til kunden eller STOPP-rutine, og FR-10 validerer ikke nummeret slik at en fremmed kan få SMS med navn og behandling.
Fix: Skriv NFR-6 ærlig, velg og dokumenter rettsgrunnlag, la SMS bare nevne dato, tid og sted, la videresending si «ny melding, se adminpanelet», legg til «ikke send SMS»-flagg og nummervalidering.

**[Adversarial]** — K3 Omfanget rekker ikke på fire uker, og avskjæringen er inkonsistent (§9, §11 (SM-1, kontroll 6), §10)
Kjerne + timer + 15 NFR + test + live-sette på fire uker alene, avhengig av klinikkens innhold, domene og SMS-leverandør. §9 sier nyhetsbrev «hvis tiden rekker», men SM-1 og kontroll 6 krever det.
Fix: Lag en minimumsrelease som eneste definisjon av ferdig (FR-1–5, FR-7–9, FR-18–20), flytt FR-10–16 og FR-21 til etter lansering eller kutt, sett cut-line 2026-12-08 og en testuke, og rett SM-1 og kontroll 6.


### High (11)
**[Rubrikk – Decision-readiness]** — Lanseringskritiske spørsmål ligger under «Kan avklares senere» (§12 nr. 7, 10, 18, 19)
Domene og hosting (nr. 7), logo/bilder/tekster/priser (nr. 10) og medisinsk ansvarlig/legegjennomgang (nr. 18) er forutsetninger for å gå live (forskriften § 4, FR-3, NFR-9). Nr. 19 avgjør om laser/peeling-sider kan publiseres. Under «Må avklares» står bare 1–5.
Fix: Flytt nr. 7, 10, 18 (og 19 hvis laser/peeling tilbys) til «Må avklares», og sett en dato per spørsmål som er tidligere enn 2026-12-15.

**[Rubrikk – Strategic coherence]** — Lovklemma på fase 2–3 er ikke gjort til scope-beslutning (§5.4, §9, §10, §12 nr. 15 og 28)
Forskriften § 7 forbyr markedsføringshenvendelser om kosmetiske inngrep på e-post og SMS, og HIFU behandles som kosmetisk inngrep. Nyhetsbrevet kan da ikke omtale klinikkens fremste behandlinger, og SMS-påminnelser er bare «trolig tjenestemeldinger». Risikotabellen dekker bare nyhetsbrev.
Fix: Legg inn go/no-go for nyhetsbrev; skriv at SMS bare har tid, sted og «time hos AURA SKIN» som designkrav; legg SMS-påminnelser i risikotabellen med reserveplan.

**[Rubrikk – Done-ness clarity]** — SMS-, timer- og adminkravene har ingen testbare konsekvenser (FR-11–FR-14, FR-16, FR-18, FR-20)
FR-13 «kunden får beskjed på SMS» (innhold? påminnelsen som allerede er planlagt?); FR-12 sier ikke hva som skjer ved time under 24 timer unna; FR-14 sier ikke hvilke felter; FR-18 sier ikke hva som skjer ved glemt passord; FR-20 «besvart» har ingen konsekvens. §11 dekker ikke FR-13 og FR-14.
Fix: Legg til to–tre testbare linjer per krav (inndata, utfall, kanttilfelle) og utvid §11.

**[Adversarial]** — H1 Spam-vern og kart motsier NFR-14 (NFR-14, NFR-4, FR-7, FR-4, §13)
Standard captcha er tredjepartsskript. FR-4 beskriver flisehenting som antakelse mens §13 sier at bildet er lagret som fil.
Fix: Serverside spam-vern uten tredjepart; kartbildet er en egen fil i repoet med ODbL-kildeangivelse.

**[Adversarial]** — H2 Ingen feildeteksjon, retry eller varsling for videresending og påminnelser (FR-7, FR-8, FR-20)
Kunden får «sendt» uavhengig av levering, begge kanaler kan svikte uten at noen vet det, og FR-20 lar klinikken slå av begge kanaler.
Fix: Sendestatus per kanal, retry, tydelig feilstatus og ulest-teller i adminpanelet, og minst én kanal alltid på.

**[Adversarial]** — H3 Databehandler, drift og tilgang er ikke avklart (§7.2, FR-18, §4, §10)
Utvikleren er databehandler uten avtale og har permanent tilgang. Ingen krav til drift etter lansering eller restore-test. SMS-/e-postleverandør ikke vurdert mot EU/EØS.
Fix: Skriv at klinikken er behandlingsansvarlig og utvikleren databehandler med avtale, velg EU/EØS-leverandører, skill utviklerkonto fra de ansattes, og krev restore-test.

**[Adversarial]** — H4 Innsyn og sletting er lovet, men ingen funksjon finnes (NFR-5, NFR-8, FR-19, FR-20)
Ingen funksjon for å slette melding/kunde/påmeldt eller eksportere data. Oppbevaring er bare en antakelse (12 måneder) og dekker ikke samtykkelogg, logger og leverandørlogger. Mulig konflikt med journalkrav (bør verifiseres).
Fix: Legg til FR for sletting og eksport, definer oppbevaring per datatype, og si at siden ikke er journal.

**[Adversarial]** — H5 Nyhetsbrev: samtykkebevis mangler, innholdet kan bli tomt, lovteksten er ulest (FR-15, FR-16, NFR-7, §5.4, UJ-3)
Ingen double opt-in eller samtykkelogg. Markedsføringsloven § 15 er ikke lest ordrett. Innholdsrommet er smalt, og UJ-3-eksempelet kan selv falle under «inngrep i hud og underhud».
Fix: Anbefaling: dropp nyhetsbrev fra første versjon. Ellers double opt-in, samtykkelogg, ett-klikks avmelding og innholdsregel; les § 15 først og skriv om UJ-3.

**[Adversarial]** — H6 Påminnelser og timer: ikke testbare og med åpne kanttilfeller (FR-10–FR-14, SM-4)
Time under 24 timer unna, omlegging etter planlagt påminnelse, jobb som ikke kjørte, idempotens, validering av datoer og åpningstider, og SM-4 uten baseline.
Fix: Skriv reglene eksplisitt (under 24 timer: bare bekreftelse; omlegging kansellerer og sender ny; jobb idempotent), legg til valideringer og fjern SM-4 eller legg til «møtte opp».

**[Adversarial]** — H7 Overdrevne sikkerhetsmarkører og interne motsigelser (§10, §2.4, §13, §12 nr. 16, NFR-14, NFR-2)
Meta-påstanden har tre ulike graderinger; § 7 er både «lest på Lovdata» og «lest én gang via sammendrag»; nr. 16 er en jusspåstand ført som beslutning; IP-logging og kontrastberegning for hånd er ikke dekket.
Fix: Én skala for sikkerhet, rett §10 og §13, flytt nr. 16, beskriv IP-logging i personvernerklæringen og gi NFR-2 en målemetode.

**[Adversarial]** — H8 HIFU-håndteringen er delvis (NFR-9, FR-2, FR-19, FR-7)
Bare bilder og nyhetsbrev er kravsatt, mens forskriften § 4 (risiko, under 18) gjelder alt innhold. Ingen felt for risiko/bivirkninger, ingen aldersgrense i skjemaet, og organisasjonsnummer/pris inkl. mva er ikke nevnt (bør verifiseres).
Fix: Obligatoriske felt for risiko og aldersgrense 18 år, organisasjonsnummer i bunnen, og oppdater alle berørte FR i én endring når nr. 28 er svart.


### Medium (21)
**[Rubrikk – Decision-readiness]** — Statusmerkingen stemmer ikke med beslutningene (§9, §7.5, §12)
§9 er merket [FORSLAG] men åpner med «avgjort 2026-11-18»; §7.5 er [FORSLAG] mens NFR-12/13 er krav når siden skal live. «Låses» har ingen kriterium eller dato.
Fix: Fjern [FORSLAG] fra det som er avgjort, og definer hva «låst» betyr.

**[Rubrikk – Substance over theater]** — Endringslogg som brødtekst (§0)
§0 er ett avsnitt på rundt 400 ord som gjenforteller versjon 3–6. Det er git-historikk, og skjuler det en ny leser trenger.
Fix: Erstatt med tre–fire linjer om formål, kilder og status.

**[Rubrikk – Substance over theater]** — Push-rester gjennom hele dokumentet (§3.1, FR-15, FR-17, NFR-7, NFR-11, §10, SM-C1, kontroll 6)
Push er «ikke med i første versjon», men dukker opp i krav, risiko, suksesskriterier og kontroller som om det var på vei inn.
Fix: Samle FR-17 og push-forbeholdene i en kort «Etter lansering»-seksjon og rydd bort resten.

**[Rubrikk – Strategic coherence]** — Suksessmålene måler ikke tesen og kan delvis ikke måles (§11)
Ingen SM for antall meldinger per uke (tilgjengelig i adminpanelet selv uten statistikk). SM-4 har ingen baseline. SM-3 måles i februar 2027 uten eier. SM-1 validerer FR-16 som kanskje ikke bygges.
Fix: Legg til SM «meldinger per uke», gi SM-4 baseline eller flytt den, sett tall på SM-C1, og si hvem som følger opp etter lansering.

**[Rubrikk – Done-ness clarity]** — Feil som ingen ser (FR-8, FR-12, NFR-4)
Hva skjer når begge kanaler feiler, eller når påminnelsesjobben stopper? Ingen vet at en melding ligger der.
Fix: Krev synlig feilstatus i adminpanelet og at feilede utsendelser logges og kan sendes på nytt.

**[Rubrikk – Done-ness clarity]** — Spam- og kostnadsbeskyttelse uten tall (FR-7, NFR-4, §12 nr. 6)
«Rate-limiting» og «tak på utsendelser» er adjektiver, ikke grenser, selv om hver melding koster en SMS.
Fix: Sett startverdier (maks N per IP/time, maks M SMS per døgn) og hva som skjer når taket nås.

**[Rubrikk – Done-ness clarity]** — Lovkravene i NFR-9 er ikke fullt ut sjekkbare (NFR-9, kontroll 9)
Kontroll 9 dekker ikke «ikke rettet mot under 18» eller «nedtoner ikke risiko», og gjennomgangen av legen har ingen definert prosess.
Fix: Gjør NFR-9 til en sjekkliste per behandlingstekst som legen kan avkrysse.

**[Rubrikk – Scope honesty]** — Ingen definisjon av «klar for lansering» (§9, §11, §7.5)
Innhold levert, legegjennomgang, personvernerklæring, databehandleravtaler, DNS, SPF/DKIM og verifisert sikkerhetskopi står spredt. Tiltaket «Plassholdere og tidlig be om innholdet» har ingen dato.
Fix: Legg til en kort «Lanseringsklar»-liste og avklar hva som skjer 2026-12-15 hvis innhold mangler.

**[Rubrikk – Scope honesty]** — Behandlingsgrunnlag for SMS og timedata er ikke dekket (§7.2, FR-10–FR-13, NFR-8)
NFR-5–8 dekker skjema og nyhetsbrev, ikke at klinikken registrerer en kunde og sender SMS. «Anonymisere» er ikke definert, og utvikleren har permanent tilgang til kundedata (FR-18).
Fix: Legg til grunnlag og informasjon til kunden, definer «anonymisere», og gjør utviklertilgang til et bevisst valg.

**[Rubrikk – Downstream usability]** — NFR-14 er i konflikt med to andre krav (NFR-14, kontroll 12, FR-4, FR-7, NFR-4)
FR-4 sier «kartflisene hentes fra OpenStreetMaps flistjener» mens NFR-14 sier ingen tredjeparts kart. Spam-vern (FR-7/NFR-4) bruker vanligvis tredjeparts captcha som sender IP.
Fix: Si at kartet hentes én gang ved bygging og lagres som fil, og krev selvhostet spam-vern (honeypot, tidsfelt, rate-limit).

**[Adversarial]** — M1 Telefonnummer og SMS-format (FR-7, FR-9, FR-10)
Formater, utenlandske og fasttelefonnumre er ikke spesifisert, og æøå gir flere SMS-segmenter.
Fix: Normaliser til E.164, avvis fasttelefon, sett maks tegn for fritekst.

**[Adversarial]** — M2 Duplikatinnsending og tak uten tall (FR-7, NFR-4, §12 nr. 6)
Ingen beskyttelse mot dobbeltklikk eller dobbelt skjema, ingen tall på tak.
Fix: Idempotens-token, deaktivert knapp, sammenslåing av like meldinger og definerte tak.

**[Adversarial]** — M3 Testbarhet av kvalitetskravene (NFR-1, NFR-3, NFR-4, SM-5)
Ingen testmetode for nettlesere, WCAG eller passordkrav.
Fix: Skriv testmetode og bestått-nivå per NFR, og passordhash, sesjonsutløp og tilbakestilling.

**[Adversarial]** — M4 Innlogging uten roller eller tofaktor med kundedata i panelet (FR-18)
Ingen sesjonsutløp, endringslogg eller kontooversikt.
Fix: Krev sesjonsutløp, sterke passord eller tofaktor og enkel endringslogg.

**[Adversarial]** — M5 FR-20 og «behandleren» er udefinert (FR-8, FR-20, §12 nr. 5)
Ingen regel for hvem som mottar, ferie eller sykdom.
Fix: Ett nummer og én e-postadresse i .env, kanalvalget fjernes fra FR-20.

**[Adversarial]** — M6 SM-kriteriene ligger etter fristen (SM-1–SM-4)
SM-1, SM-3 og SM-4 faller etter 2026-12-15, og SM-3 mangler baseline.
Fix: Skill «før lansering» fra «etter lansering», og bruk en teller i admin som erstatning for statistikk.

**[Adversarial]** — M7 FR-6 går utenfor det siden kan kontrollere (FR-6, kontroll 9)
PRD-en kan ikke kreve noe av Instagram-innlegg, og ordlisten er ikke uttømmende eller håndhevet.
Fix: Begrens til nettsiden og adminpanelet, legg ordlisten som vedlegg og sperr i adminfeltene.

**[Adversarial]** — M8 FAQ med helsefaglig innhold uten gjennomgang (FR-21, NFR-9, §13)
«Forberedelse, etterpå» er medisinsk råd uten eksplisitt legegjennomgang.
Fix: Krev godkjenning av medisinsk ansvarlig, eller kutt FR-21 fra første versjon.

**[Adversarial]** — M9 Demo og seed-data kan bli en sikkerhetsrisiko (§7.5, NFR-11)
Offentlig demo med test-admin og gratisplan som sover.
Fix: Aldri seed i produksjon, noindex og basic auth på demo, produksjonshosting som ikke sover.

**[Adversarial]** — M10 Hardkodede verdier mot NFR-12 (FR-9, FR-4, FR-1, FR-19)
Telefon, adresse og koordinater står flere steder.
Fix: Én kilde for kontaktdata brukt av alle visninger og markering.

**[Adversarial]** — M11 Alder og samtykke i skjemaet (FR-7, NFR-9)
Ingen aldersbekreftelse eller rutine for mindreårige.
Fix: «Du må være 18 år eller eldre» og en rutine for behandleren.


### Low (6)
**[Rubrikk – Substance over theater]** — Implementasjonsdetaljer dupliseres i PRD og addendum (§6, FR-4, FR-9, addendum)
Koordinater, lenkeformater og Instagram-beslutningen står to steder: risiko for drift.
Fix: La én kilde eie hver verdi (anbefalt addendum).

**[Rubrikk – Done-ness clarity]** — Mindre uferdige mål (NFR-2, SM-5, FR-7)
Ingen metrikk for «under 3 sekunder», ingen metode for WCAG-sjekk, ingen definert telefonformat.
Fix: Velg metrikk, verktøy og aksepterte nummerformat.

**[Rubrikk – Scope honesty]** — Støy i antakelsesmerkingen (§13)
Mange [ASSUMPTION] er leveranser fra klinikken, ikke antakelser som kan vise seg feil.
Fix: Skill avhengigheter fra risikable antakelser.

**[Rubrikk – Downstream usability]** — Brukerreisene dekker få flyter (§3.3)
UJ-2 og UJ-3 mangler navngitt protagonist; ingen reise for adminpanelet, flytting/avlysning eller påmelding.
Fix: Navngi behandleren og legg til én admin-reise og én flytte/avlys-reise.

**[Rubrikk – Downstream usability]** — Ordlistedrift (§4, FR-1, FR-7)
«Bekreftelse» brukes om både SMS og skjermkvittering, «Forside»/«Hjem» om samme side, og «Kosmetisk inngrep» mangler i ordlisten.
Fix: Definer «Kosmetisk inngrep» med forskriftens ordlyd og rydd termene.

**[Adversarial]** — L1–L6 Mindre punkter (§12, §0, FR-9, FR-1, FR-7, addendum)
Rekkefølge på FR/NFR og hull i §12-numrene som ser ut som feil; designforslaget ligger ikke i repoet; kontaktlenker mangler fallback per enhet; fast bunnlinje kan dekke innhold med tastatur åpent; kontekstavhengig «Send melding»-knapp; SMS-kostnad uten budsjettanslag.
Fix: Sorter eller indekser, lagre en eksport av designet, skriv fallbacks, test på 360 px, la knappen alltid gå til Send melding-siden og legg inn budsjettanslag.

## Mechanical notes
- §0 refererer til «versjon 4» som forrige versjon; skal være versjon 5.
- NFR-ene står i rekkefølgen 1–4, 10, 14, 15, 11, 5–9, 12, 13, og FR-21 står mellom FR-6 og FR-7. ID-ene er komplette og unike.
- Innebygde [ASSUMPTION] som mangler i §13: NFR-7, prislisteraden i §2.4 og FR-6s andre antakelse. §13 sier «Push faller under samme samtykkekrav» mens §5.4 sier «ikke avklart».
- §13 sier «Kartbildet lagres som egen fil», mens FR-4 beskriver flisehenting (se Downstream usability).
- UJ-2 og UJ-3 mangler navngitt protagonist. `prd/prd-grunnlag.md` bør sjekkes mot v6.

## Reviewer files
- `review-rubric.md`
- `review-adversarial-general.md`
