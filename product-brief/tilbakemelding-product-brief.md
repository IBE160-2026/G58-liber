# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G58 – G58-liber |
| **Product brief** | `product-brief/brief.md` (commit `529cc0a`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

Jeg har også lest `addendum.md` i samme mappe og spørsmålene i `kundeintervju/sporsmal.md`.

## Samlet vurdering

- **Godt utgangspunkt med justeringer.** Gruppen kan gå videre og innarbeide punktene under.

**Det som er bra:**

1. Problemet er ekte og konkret: en enkeltmannsklinikk som i dag tar all booking via meldinger på Facebook. Det er lett å se for seg både klinikkeieren og kunden, og de tre kjernedelene (informasjonsside, selvbetjent booking, adminpanel) svarer direkte på problemene.
2. Avgrensningen er klok og godt begrunnet: én behandler, betaling i klinikken, ingen helseopplysninger i bookingskjemaet (med henvisning til GDPR art. 9) og Vipps utsatt til v2.
3. «Hva gjør dette annerledes» er ærlig: dere sier rett ut at Timma, Fresha og Eazybook kunne dekket det meste, og at fordelen er merkevare, ingen abonnementskostnad og tilpasning til én behandler. Planen om å intervjue klinikkeieren er også et godt grep for å forankre kravene.

**De viktigste endringene:**

1. Bookingreglene er ikke beskrevet. Hva er en «ledig tid»? Avklar åpningstider, varighet per behandling, pauser mellom timer, hvor langt fram man kan booke, og hva som skjer ved avbestilling. Dette er kjernen i appen og det som må testes.
2. Suksesskriteriene blander funksjonelle krav og forretningsmål. «Antall meldinger går ned» og «fremstår profesjonell» kan ikke måles i emnet. Legg til konkrete kriterier som «en kunde kan booke en ledig time, og tiden forsvinner fra kalenderen» og «to kunder kan ikke booke samme tid».
3. Planlegg hvordan sensor kan kjøre appen lokalt: med eksempelbehandlinger, en testkalender og en test-admin, uten tilgang til klinikkens eller deres egen hosting.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Middels**

**Sammenlignbart med:** Mellom 6) To-do-liste med smarte etiketter (enkel) og 2) AI CV- og søknadsassistent (middels). Appen har ingen KI-funksjon, men bookinglogikk med ledighet, to brukerroller (kunde og admin med innlogging) og personopplysninger løfter den over et rent CRUD-prosjekt. Jeg plasserer den i nedre del av middels.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels | Ledige tider ut fra åpningstid, behandlingsvarighet og eksisterende bookinger, og hindring av dobbeltbooking. Reglene er ikke beskrevet ennå. |
| Datamodell – antall entiteter og relasjoner mellom dem | Lav–middels | Behandlingskategori, behandling (pris, varighet), tidsluke/åpningstid, booking og admin-bruker. Overkommelig. |
| Brukere, roller og innlogging | Middels | Kunder uten konto og admin med innlogging (klinikkeier og utvikler). Admin-innloggingen må være sikker. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Lav | Ingen KI i appen. KI brukes i utviklingen. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Lav | Ingen i v1 (Vipps er utsatt). Bekreftelse på e-post er ikke nevnt; vurder om den trengs. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Middels | To kunder kan forsøke å booke samme tid samtidig. Det må håndteres i databasen. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Lav | Eventuelt bilder av behandlinger. Ikke sentralt. |
| Sikkerhet og personvern | Middels | Navn, telefon og e-post til kunder. Godt at helseopplysninger er holdt utenfor. Beskriv sletting av gamle bookinger. |

**Hva vanskelighetsgraden betyr for dere:**

- _Middels:_ Et godt balansert valg. Pass på at kjerneflyten (velg behandling → se ledige tider → book → booking vises i adminpanelet) blir ferdig og stabil før dere legger til mer. Som soloprosjekt er det lurt å holde adminpanelet enkelt i første runde.

### Gjennomførbarhet med BMAD og Claude Code

Dere skal planlegge med BMAD (product brief → PRD → arkitektur → epics og stories) og implementere med Claude Code. Vurderingen under tar hensyn til at det må være tid til hele denne flyten, og til testing, retting og README til slutt.

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | OK | Tre kjernedeler for én person er realistisk, så lenge bookingreglene holdes enkle. Det finnes ennå ingen PRD. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Risiko | Strukturen er tydelig, men bookingreglene og hva adminpanelet konkret skal kunne (blokkere tid, endre åpningstider, avlyse) mangler. Kundeintervjuet kan gi svarene. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | En bookingnettside med database og admin-innlogging er et vanlig mønster som Claude Code håndterer godt. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | OK | Ledighet og dobbeltbooking kan kontrolleres for hånd med noen konkrete eksempler. Lag dem på forhånd. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | Risiko | Når reglene er skrevet ned, blir de gode testtilfeller (f.eks. «en 60-minutters behandling kan ikke bookes kl. 16.30 hvis klinikken stenger kl. 17»). I dag mangler de. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | Risiko | Briefen handler om en ekte nettside for klinikken, med hosting og domene. Sørg for at appen også kan kjøres lokalt med seed-data og en test-admin. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | OK | Ingen betalte API-er i v1. Hosting og domene er klinikkens sak og ikke nødvendig for emnet. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart som beskrevet.**

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Skriv ned bookingreglene konkret (åpningstider, varighet per behandling, buffer, hvor langt fram, avbestilling), gjerne etter kundeintervjuet, og ta dem inn i briefen eller i PRD.
2. Vurder én utvidelse som gir mer å vise i funksjonalitet og testing når kjernen virker, f.eks. bekreftelse på e-post eller at kunden kan avbestille via en lenke. Legg den som et tydelig andre trinn.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Tydelig: en egen nettside med informasjon, priser, selvbetjent booking og adminpanel for en klinikk som i dag bruker Facebook. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Fire konkrete problemer (ingen selvbetjening, uprofesjonelt inntrykk, tidsbruk, ingen samlet oversikt). |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | Juster | Beskriver opplevelsen godt, men adminpanelet er bare «styrer kalender, behandlinger og priser». Beskriv hva eieren konkret gjør der, f.eks. legger inn ferie, blokkerer en ettermiddag eller ser dagens timer. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig og konkret om SaaS-alternativene og hvorfor en skreddersydd løsning likevel er valgt. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | OK | Klinikkeier og kunder er tydelige, med konkrete suksessmål for hver. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | To av fire kriterier er forretningsmål (færre meldinger, profesjonelt inntrykk). Legg til funksjonelle, testbare kriterier for booking, ledighet, dobbeltbooking og admin. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | OK | Tydelig delt i v1 og «bevisst utsatt». |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Vipps-depositum og gjenbrukbar mal er tydelig plassert etter v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Historikken viser at briefen er bearbeidet flere ganger (bl.a. omskrevet fra frilansramme til skoleprosjekt), og kundeintervjuet er forberedt. Bra. Gjennomfør intervjuet, dokumenter svarene, og bruk dem i PRD. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | OK | Tydelig kjerneflyt med nok innhold for én person. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Bookingreglene og funksjonelle suksesskriterier må på plass før de kan bli testtilfeller. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | OK | To tydelige brukergrupper og et ønske om klinikkens egen merkevare. Skisser bookingflyten på mobil og adminpanelets oversikt. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | Juster | Teknologi er bevisst utsatt til arkitekturen. Velg en enkel stakk med én database, og begrunn valget. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Juster | Planlegg lokal kjøring med seed-data og test-admin, uavhengig av klinikkens hosting. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Repoet er offentlig: ekte kundedata og admin-passord må aldri committes. Bruk fiktive testkunder og legg hemmeligheter i `.env` utenfor Git. Avklar også med klinikken om bilder og tekster fra Facebook kan ligge i et offentlig repo. |

## 3. Neste steg for gruppen

1. Gjennomfør kundeintervjuet og skriv bookingreglene og admin-funksjonene konkret inn i briefen eller i et addendum.
2. Legg til funksjonelle, testbare suksesskriterier (booking, ledighet, dobbeltbooking, admin-endringer), og flytt forretningsmålene til et eget avsnitt.
3. Gå videre til PRD og arkitektur, og ta med lokal kjøring med seed-data som et eksplisitt krav.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
