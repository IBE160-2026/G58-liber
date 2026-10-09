---
title: "Product Brief: AURA SKIN Klinikk – bookingnettside"
status: draft
created: 2026-09-13
updated: 2026-10-09
---

# Product Brief: AURA SKIN Klinikk – bookingnettside

## Sammendrag

AURA SKIN Klinikk er en hudpleieklinikk i Salhus som i dag driftes nesten utelukkende gjennom Facebook — kunder må sende meldinger frem og tilbake for å finne ut hva klinikken tilbyr og for å avtale time. Det er tungvint for kundene og tidkrevende for klinikkeieren, som driver alene.

Dette prosjektet er en egen nettside der kunder kan lese om klinikken og behandlingene den tilbyr, se priser, og booke en ledig time selv i en kalender — uten å måtte sende en eneste melding. Klinikkeieren får et adminpanel hvor hun styrer kalender, behandlinger og priser selv. I første versjon betaler kunden i klinikken som normalt; nettbetaling via Vipps er en bevisst utsatt utvidelse.

Løsningen er skreddersydd for en liten enkeltmannsklinikk: enkel å bruke, uten løpende abonnementskostnad, og med klinikkens egen merkevare i sentrum.

## Problemet

Klinikkeieren driver AURA SKIN Klinikk alene og bruker Facebook som eneste kanal for markedsføring og booking. Det gir flere konkrete problemer:

- **Ingen selvbetjening.** Kunder må sende en melding for å spørre om behandlinger, priser og ledig tid, og vente på svar — i stedet for å se dette selv og booke direkte.
- **Uprofesjonelt førsteinntrykk.** En Facebook-side signaliserer et hobbyprosjekt, ikke en etablert klinikk, noe som kan gjøre det vanskeligere å tiltrekke nye kunder som forventer en ordentlig nettside.
- **Tidsbruk for eieren.** Hver booking krever manuell frem-og-tilbake-kommunikasjon — tid som går fra behandlingstid.
- **Ingen samlet oversikt.** Behandlinger og priser ligger spredt i innlegg og kommentarer på Facebook fremfor på ett sted kunden kan finne selv.

## Løsningen

En dedikert nettside for AURA SKIN Klinikk med tre kjernedeler:

1. **Informasjonsside** — presenterer klinikken og de fem behandlingskategoriene (ansiktsbehandling, laser, botox/filler, vipper/bryn, kroppsbehandling) med beskrivelser, varighet og priser, hentet fra eksisterende materiale på klinikkens Facebook-side.
2. **Selvbetjent booking** — kunden velger behandling, ser en kalender med faktisk ledige tider (én behandler, ingen ressursvalg nødvendig) og booker selv. Bookingskjemaet samler kun det som trengs for å gjennomføre timen: navn, telefon, e-post og valgt behandling — ingen helseopplysninger (hudtilstand, allergier) samles i denne versjonen. Kunden får en bekreftelse på skjermen med tid, behandling og pris.
3. **Adminpanel** — klinikkeieren logger inn og gjør det daglige arbeidet selv:
   - ser dagens og ukens timer i en oversikt, med kundens navn og kontaktinfo;
   - avlyser eller flytter en booking (f.eks. etter en telefon fra kunden);
   - blokkerer tid — en ettermiddag, en dag eller en ferieperiode — slik at den ikke kan bookes;
   - endrer faste åpningstider per ukedag;
   - legger til, endrer og skjuler behandlinger, med pris og varighet.

   Utvikleren beholder egen admin-tilgang ved siden av, for å kunne bistå med endringer ved behov.

Betaling skjer i klinikken som i dag (kontant/kort på stedet); nettsiden endrer ikke betalingsopplevelsen i denne versjonen.

Kjerneflyten som må være ferdig og stabil før noe annet bygges: **velg behandling → se ledige tider → book → bookingen vises i adminpanelet og tiden er ikke lenger ledig.**

## Bookingregler

Reglene under avgjør hva en «ledig tid» er, og er grunnlaget for testene. Verdiene er et forslag som bekreftes eller justeres i kundeintervjuet med klinikkeieren (se `kundeintervju/sporsmal.md`); alle tallverdier er innstillinger i adminpanelet eller konfigurasjonen, ikke hardkodet.

| Regel | Forslag v1 |
|---|---|
| Åpningstider | Faste tider per ukedag (f.eks. tirsdag–fredag 10–17, lørdag 10–14). Stengte dager har ingen ledige tider. |
| Varighet | Hver behandling har en fast varighet (f.eks. 30, 60 eller 90 min) satt av eieren. |
| Buffer | 15 min mellom timer til rydding og klargjøring. |
| Tidsluker | Starttider tilbys hvert 15. minutt. |
| Ledig tid | En starttid er ledig når hele behandlingen *pluss buffer* får plass innenfor åpningstiden, uten overlapp med en annen booking eller blokkert tid. Eksempel: en 60-minutters behandling kan ikke bookes kl. 16.30 når klinikken stenger kl. 17. |
| Korteste varsel | Tidligst 2 timer frem i tid; tider tidligere samme dag vises ikke. |
| Lengste horisont | Inntil 8 uker frem i tid. |
| Dobbeltbooking | To bookinger kan aldri overlappe. Sjekken skjer i databasen ved lagring, slik at to kunder som booker samme tid samtidig ikke begge får bekreftelse — den siste får beskjed om at tiden er tatt. |
| Avbestilling | I v1 avbestiller kunden ved å kontakte klinikken; eieren avlyser i adminpanelet og tiden blir ledig igjen umiddelbart. Avbestillingsfrist (f.eks. 24 timer) vises som tekst på nettsiden. |
| Sletting av data | Kundeopplysninger på gjennomførte eller avlyste bookinger slettes/anonymiseres automatisk etter en fast periode (forslag: 12 måneder). |

## Hva gjør dette annerledes

De fleste norske hudpleie- og skjønnhetsklinikker løser booking med et abonnement på en ferdig SaaS-plattform (f.eks. Timma, Fresha, Eazybook) fremfor en egen nettside (basert på egen research, ikke bekreftet med klinikkeier). Fordelen med en skreddersydd løsning her er:

- **Egen merkevare, ikke en generisk bookingportal.** Nettsiden kan se ut og føles som AURA SKIN Klinikk, ikke som en av mange klinikker inne i en tredjeparts app.
- **Ingen løpende abonnementskostnad** for en klinikk som drives av én person med begrenset budsjett — engangsutvikling fremfor 200–1000+ kr/mnd i SaaS-avgift.
- **Enkelhet tilpasset faktisk behov.** Klinikken har én behandler; mange SaaS-verktøy er bygget for flere ansatte/ressurser og bærer kompleksitet klinikken ikke trenger.

En ferdig SaaS-løsning kunne dekket mye av det samme funksjonelt. Fordelen her ligger ikke i unik teknologi, men i skreddersøm, merkevarekontroll og en løsning som er dimensjonert for klinikkens faktiske behov.

## Hvem dette er for

**Primær: klinikkeieren.** Driver AURA SKIN Klinikk alene i Salhus. Trenger å bruke mindre tid på booking-kommunikasjon og fremstå mer profesjonelt overfor nye kunder. Suksess for henne = færre meldinger å svare på manuelt, en kalender hun stoler på, og et adminpanel hun faktisk mestrer selv uten teknisk hjelp.

**Primær: klinikkens kunder.** Vil raskt finne ut hva klinikken tilbyr, hva det koster, og booke en ledig time uten å vente på svar — som oftest fra mobilen. Suksess for dem = booking tar under et par minutter, uten meldingsutveksling.

## Suksesskriterier

### Funksjonelle kriterier (testbare i v1)

1. En kunde kan velge en behandling, se ledige tider og booke en time; etter bookingen er tiden ikke lenger ledig i kalenderen.
2. Ledige tider følger bookingreglene: ingen tider utenfor åpningstid, ingen tider der behandling + buffer går over stengetid, ingen tider i blokkert periode, og ingen tider utenfor korteste varsel / lengste horisont.
3. To kunder kan ikke booke overlappende tider — heller ikke når de sender bookingen samtidig.
4. En ny booking vises i adminpanelets oversikt med tid, behandling og kundens kontaktinfo.
5. Når eieren avlyser en booking eller fjerner en blokkering, blir tiden ledig igjen for kundene.
6. Når eieren endrer pris, varighet eller åpningstider, gjenspeiles endringen på informasjonssiden og i ledige tider uten at utvikleren må gjøre noe.
7. Adminpanelet er kun tilgjengelig etter innlogging; kunder ser aldri andres bookinger.
8. Bookingflyten kan fullføres på en mobilskjerm.
9. Appen kan startes lokalt etter README med eksempelbehandlinger, en testkalender og en test-admin — uten tilgang til klinikkens hosting eller andre private nøkler.

### Forretningsmål (følges opp med klinikkeieren etter lansering)

- Klinikkeieren håndterer bookinger i det daglige uten teknisk hjelp.
- Antall bookingrelaterte meldinger på Facebook/telefon går ned sammenlignet med i dag (ingen baseline er målt ennå).
- Nettsiden oppleves gjennomført og profesjonell, på nivå med det kunder forventer av en etablert klinikk.

## Omfang

**Med i første versjon (v1):**
- Informasjonsside om klinikken og de fem behandlingskategoriene, med priser og varighet.
- Kalendervisning med faktisk ledige tider for én behandler, etter bookingreglene over.
- Selvbetjent booking med enkelt kontaktskjema (navn, telefon, e-post, valgt behandling) — ingen helse-/hudopplysninger.
- Beskyttelse mot dobbeltbooking i databasen.
- Betaling i klinikken (ingen nettbetaling).
- Adminpanel med innlogging: oversikt over timer, avlyse/flytte booking, blokkere tid, åpningstider og behandlinger/priser. Egen tilgang for utvikleren.
- Lokal kjøring med seed-data (fiktive behandlinger, testkalender, test-admin og fiktive testkunder).

**Trinn 2 (når kjerneflyten er ferdig og stabil):**
- Bekreftelse på e-post ved booking, med en lenke kunden kan bruke til å avbestille selv innenfor avbestillingsfristen.

**Eksplisitt utenfor v1 (bevisst utsatt, ikke avvist):**
- Nettbetaling / depositum via Vipps — planlagt som v2, se Visjon.
- SMS-påminnelser.
- Kundekonto/innlogging for kunder.
- Innsamling av hudtilstand/allergi-informasjon i bookingskjemaet — ville utløst strengere GDPR-krav (helsedata, art. 9); ikke en del av planen nå.
- Flere behandlere / ressursbasert kalender — klinikken har én behandler i dag.
- Domene og produksjonshosting — klinikkens sak, og ikke nødvendig for at løsningen kan kjøres og vurderes lokalt.

## Tekniske rammer

Konkret stakk velges og begrunnes i arkitekturfasen, innenfor disse rammene:

- **Enkel stakk med én database.** Velg vanlig, godt dokumentert teknologi; ingen mer kompleksitet enn en bookingnettside for én behandler trenger.
- **Kjørbar lokalt.** Én kommando (eller noen få steg i README) starter appen med seed-data. Ingen betalte API-er eller eksterne kontoer kreves i v1.
- **Hemmeligheter og data.** Repoet er offentlig: admin-passord og andre hemmeligheter ligger i `.env` utenfor Git (med en `.env.example` i repoet), og kun fiktive testkunder brukes i utvikling og testing — ekte kundedata committes aldri.
- **Innhold fra Facebook.** Bilder og tekster fra klinikkens Facebook-side legges bare i repoet etter avklaring med klinikkeieren; ellers brukes plassholdere.

## Visjon

Neste steg etter en fungerende v1 er å legge til nettbetaling via Vipps — enten for hele beløpet eller som depositum ved booking for å redusere no-shows — en vanlig praksis blant sammenlignbare klinikker. Om løsningen fungerer godt for AURA SKIN Klinikk, kan den også bli en dokumentert, gjenbrukbar mal for bookingnettsider til andre små enkeltmannsklinikker.
