# Tilbakemelding på PRD

| | |
|---|---|
| **Gruppe** | G58 – G58-liber |
| **PRD vurdert** | `prd/prd.md` (status: draft, sist endret 2026-10-28, commit 0e38f3a) |
| **Dato** | 2026-11-12 |
| **Type** | Formativ tilbakemelding, ikke karakter |

Jeg har også lest `prd/addendum.md`.

## 1. Samlet inntrykk

PRD-en har en tydelig tese: kunden skal ikke booke selv, men sende en melding som havner der behandleren allerede svarer, og klinikken registrerer timen etterpå. Begrunnelsen står i addendumet, og FR-ene er korte og lette å lese. Risikoen er at mange krav mangler testbare konsekvenser, at omfanget (SMS, Meta-API, nyhetsbrev, push, GDPR) er stort uten tydelig prioritering, og at det ikke står noe om hvordan løsningen kan kjøres og testes uten ekte SMS-, e-post- og Meta-kontoer.

## 2. Dette fungerer godt

1. **Et begrunnet veivalg.** Addendumet («Hvorfor ikke selvbetjent booking») forklarer at kalenderbooking ble forkastet etter kundeintervjuet fordi «alle behandlinger starter med en konsultasjon». Dette er en ekte beslutning med begrunnelse, og FR-1–FR-9 følger av den.
2. **Ærlig om usikkerhet.** FR-8 flagger at Meta-videresending kanskje ikke er mulig, og addendumet gir en reserveløsning (SMS og direktelenker). Det er slik en risiko bør håndteres.
3. **Gode glossar, motmål og avgrensning.** §3 definerer begrepene, §7 begrunner hvorfor kalender er utelatt, og SM-C1 («for mange utsendelser fører til avmeldinger») er en reell motvekt. FR-7 og NFR-6 holder helseopplysninger utenfor.

## 3. Oversikt per dimensjon

| Dimensjon | Vurdering | Kort begrunnelse |
|---|---|---|
| Beslutningsklarhet | god | Hovedvalget er tydelig, men seks åpne spørsmål i §9 har ingen standardløsning eller frist. |
| Substans | god | Innholdet er forankret i klinikkens situasjon. Persona- og NFR-delene er ikke pynt, men NFR-2 og NFR-4 er vage. |
| Strategisk sammenheng | god | Tesen er klar, men SM-1, SM-3 og SM-4 måles etter lansering og kan ikke vurderes i emnet. |
| Testbarhet | svak | Mange FR-er beskriver en funksjon uten verifiserbare konsekvenser (se 4.1). |
| Scope og avgrensning | god | Utelatelser er eksplisitte, men det er ikke skilt mellom kjerne og tillegg. |
| Brukbarhet for neste fase | god | IDer er sammenhengende og glossaret finnes. Mangler brukerreiser for admin-innhold og påmelding. |
| Formtilpasning | god | Kombinasjonen av enkle UJ-er og FR-liste passer en klinikknettside. |

## 4. Viktigste forbedringer

### 4.1 Mange FR-er kan ikke bli testtilfeller
- **Alvorlighet:** høy
- **Hvor:** FR-3, FR-4, FR-5, FR-9, FR-10, FR-11, FR-13, FR-14, FR-16, FR-17; NFR-2 («Sidene laster raskt»)
- **Problem og hvorfor det betyr noe:** Disse FR-ene har én setning eller bare en beskrivelse, uten feilsituasjoner eller målbare utfall. FR-10 sier ikke hva som skjer ved ugyldig nummer, tid i fortiden eller dobbeltbooking av samme behandler. FR-13 sier ikke hva som skjer med påminnelsen når en time flyttes. Stories og tester vil da bygge på gjetning.
- **Forslag:** Gi hvert FR 2–4 kontrollerbare punkter. For eksempel:
  > **FR-10:** Klinikken kan registrere en avtalt time.
  > - Navn, mobilnummer (8 siffer), dato og tid er påkrevd; mangler noe, vises feilmelding og ingenting lagres.
  > - Tid i fortiden avvises.
  > - Overlapper timen en annen avtalt time, vises en advarsel som kan overstyres.
  > - Etter lagring vises timen i timeoversikten (FR-14) og bekreftelsen (FR-11) sendes.

  Erstatt «raskt» i NFR-2 med en grense, for eksempel «forsiden er brukbar innen 3 sekunder på 4G».

### 4.2 Omfanget er stort og mangler prioritering
- **Alvorlighet:** høy
- **Hvor:** §4 (20 FR-er), FR-8, FR-12, FR-15–FR-17
- **Problem og hvorfor det betyr noe:** Dere har fire eksterne integrasjoner (SMS, Meta, e-post, Web Push), en planlagt jobb og en GDPR-sletterutine. Det er mye for ett semester. Det kritiske punktet (Meta-API, FR-8) er en antakelse som ikke er avklart. Hvis den feiler, er det uklart hva som er kjerneleveransen.
- **Forslag:** Del kravene i «Kjerne» og «Tillegg». Et realistisk forslag: Kjerne = FR-1–FR-7, FR-8 kun via SMS, FR-10–FR-14, FR-18–FR-20. Tillegg = Meta-videresending, nyhetsbrev og push (FR-15–FR-17). Skriv avgjørelsen om SMS-reserveløsningen inn i FR-8 selv, ikke bare i addendumet.

### 4.3 Lokal kjøring, testmodus og kostnad mangler som krav
- **Alvorlighet:** høy
- **Hvor:** §6 (ingen krav om dette); addendum «Eksterne tjenester bak et grensesnitt»; §9 spørsmål 4 («Hvem betaler for SMS-utsending?»)
- **Problem og hvorfor det betyr noe:** Tilbakemeldingen på briefen ba om lokal kjøring med seed-data og test-admin. Addendumet nevner en «testversjon som logger meldinger», men det står ikke som krav. Repoet er offentlig, så nøkler til SMS og Meta kan ikke ligge der, og sensor har ikke tilgang til dere sine kontoer.
- **Forslag:** Legg til et NFR, for eksempel: «**NFR-10:** Løsningen kan kjøres lokalt uten eksterne kontoer. SMS, e-post og push logges i stedet for å sendes, og eksempelbehandlinger og en testbruker følger med. Nøkler ligger i `.env` utenfor Git.» Da kan hvert FR som sender noe (FR-8, FR-11, FR-12, FR-13) testes mot loggen.

### 4.4 Åpne spørsmål uten standardsvar
- **Alvorlighet:** medium
- **Hvor:** §9 spørsmål 2, 3, 6; §10
- **Problem og hvorfor det betyr noe:** Spørsmål 3 («én felles mottaker eller en bestemt behandler?») påvirker FR-8 og FR-20 direkte. Spørsmål 6 («Når skal nettsiden være ferdig?») har ingen dato, mens emnet har en kjent frist. Spørsmål 1 dupliserer antakelsen i FR-6.
- **Forslag:** Skriv en foreløpig standard bak hvert spørsmål, for eksempel «Antar én felles mottaker til klinikken svarer». Sett en dato for når spørsmålene senest må være avklart, og slå sammen spørsmål 1 med FR-6-antakelsen.

### 4.5 Suksesskriterier og brukerreiser dekker ikke hele løsningen
- **Alvorlighet:** medium
- **Hvor:** SM-1, SM-3, SM-4; UJ-2 og UJ-3
- **Problem og hvorfor det betyr noe:** SM-3 («Færre gjentatte spørsmål») og SM-4 («Færre uteblitte timer») har ingen tall og kan ikke måles før semesterslutt. UJ-2 og UJ-3 har bare «behandleren» som aktør, og det finnes ingen reise for kundens påmelding til nyhetsbrev eller for klinikkens innholdsendring (FR-19).
- **Forslag:** Legg til et SM som kan testes før levering, for eksempel «Fra registrering av en time til SMS-bekreftelse (i testmodus) tar under 10 sekunder». Gi UJ-2 og UJ-3 et navn og en kort feilsituasjon, og legg til en UJ for påmelding med samtykke.

## 5. Mekaniske funn

- §0 sier «FR-1 til FR-N»; skriv «FR-1 til FR-20».
- FR-, NFR-, UJ- og SM-IDer er sammenhengende, og alle fem `[ASSUMPTION]` står i §10. Bra.
- Glossar: «Utsendelse» (SM-1, SM-C1) står ikke i §3. «Behandleren» og «klinikken» brukes om hverandre som aktør i UJ-2 og FR-10. «Beskjed» (FR-13) bør være «bekreftelse».
- NFR-9 henviser til FR-6, men sier ikke hvem som godkjenner teksten før publisering.

## 6. Før dere går videre

**Må avklares før UX, arkitektur og epics:**
- Hvilke krav er kjerne og hvilke er tillegg (4.2), og hva som er reserveløsningen for FR-8.
- Mottaker for meldinger (spørsmål 3) og hvem som betaler for SMS (spørsmål 4).
- Krav om lokal kjøring og testmodus (4.3).

**Kan vente:** domene og hosting (spørsmål 5), eksakt påminnelsestidspunkt (FR-12), tofaktor for innlogging.

**Oppfølging av briefen: delvis.** Kundeintervjuet er gjennomført og brukt, og bookingreglene er borte siden booking er forkastet. Det er positivt. Funksjonelle, testbare mål (4.1) og lokal kjøring (4.3) fra briefen er ikke fulgt opp ennå. Oppdater også `brief.md` slik at den ikke fortsatt beskriver selvbetjent booking.

## 7. Refleksjonsspørsmål

1. Veivalget bort fra kalenderbooking kom etter kundeintervjuet. Hvilke deler av det tidligere KI-utkastet kunne dere ha godtatt uten intervjuet, og hvordan oppdaget dere at de var feil?
2. FR-8 bygger på at Meta-API fungerer. Hvordan kontrollerte dere dette, og hva ville dere gjort hvis KI-assistenten hadde svart at det «bare er å koble til»?

_Vurdert mot kvalitetsrubrikken i bmad-prd. Dette er veiledning, ikke sensur._
