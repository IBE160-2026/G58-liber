---
title: "Product Brief: AURA SKIN Klinikk – bookingnettside"
status: draft
created: 2026-09-13
updated: 2026-09-13
---

# Product Brief: AURA SKIN Klinikk – bookingnettside

## Sammendrag

AURA SKIN Klinikk er en hudpleieklinikk i Salhus som i dag driftes nesten utelukkende gjennom Facebook — kunder må sende meldinger frem og tilbake for å finne ut hva klinikken tilbyr og for å avtale time. Det er tungvint for kundene og tidkrevende for klinikkeieren, som driver alene.

Dette prosjektet er en egen nettside der kunder kan lese om klinikken og behandlingene den tilbyr, se priser, og booke en ledig time selv i en kalender — uten å måtte sende en eneste melding. Klinikkeieren får et adminpanel hvor hun styrer kalender, behandlinger og priser selv. I første versjon betaler kunden i klinikken som normalt; nettbetaling via Vipps er en bevisst utsatt utvidelse.

Prosjektet er en frilansoppgave: [ASSUMPTION] det gjøres som en tjeneste for en bekjent, med et mulig honorar ved ferdigstillelse, og skal samtidig fungere som et referanseprosjekt som gjør utviklerens arbeid attraktivt for fremtidige oppdragsgivere. Den doble målsettingen — en løsning som fungerer godt for en reell, liten enkeltmannsklinikk, og et resultat av høy nok kvalitet til å vises frem — er premisset for hele briefen.

## Problemet

Klinikkeieren driver AURA SKIN Klinikk alene og bruker Facebook som eneste kanal for markedsføring og booking. Det gir flere konkrete problemer:

- **Ingen selvbetjening.** Kunder må sende en melding for å spørre om behandlinger, priser og ledig tid, og vente på svar — i stedet for å se dette selv og booke direkte.
- **Uprofesjonelt førsteinntrykk.** En Facebook-side signaliserer et hobbyprosjekt, ikke en etablert klinikk, noe som kan gjøre det vanskeligere å tiltrekke nye kunder som forventer en ordentlig nettside.
- **Tidsbruk for eieren.** Hver booking krever manuell frem-og-tilbake-kommunikasjon — tid som går fra behandlingstid.
- **Ingen samlet oversikt.** Behandlinger og priser ligger spredt i innlegg og kommentarer på Facebook fremfor på ett sted kunden kan finne selv.

## Løsningen

En dedikert nettside for AURA SKIN Klinikk med tre kjernedeler:

1. **Informasjonsside** — presenterer klinikken og de fem behandlingskategoriene (ansiktsbehandling, laser, botox/filler, vipper/bryn, kroppsbehandling) med beskrivelser og priser, hentet fra eksisterende materiale på klinikkens Facebook-side.
2. **Selvbetjent booking** — kunden velger behandling, ser en kalender med faktisk ledige tider (én behandler, ingen ressursvalg nødvendig) og booker selv. Bookingskjemaet samler kun det som trengs for å gjennomføre timen: navn, telefon, e-post og valgt behandling — ingen helseopplysninger (hudtilstand, allergier) samles i denne versjonen.
3. **Adminpanel** — klinikkeieren administrerer kalender, behandlinger og priser selv. Utvikleren beholder egen tilgang ved siden av, for å kunne bistå med endringer ved behov i en tidlig fase.

Betaling skjer i klinikken som i dag (kontant/kort på stedet); nettsiden endrer ikke betalingsopplevelsen i denne versjonen.

## Hva gjør dette annerledes

De fleste norske hudpleie- og skjønnhetsklinikker løser booking med et abonnement på en ferdig SaaS-plattform (f.eks. Timma, Fresha, Eazybook) fremfor en egen nettside. [ASSUMPTION — basert på research, ikke bekreftet med klinikkeier] Fordelen med en skreddersydd løsning her er:

- **Egen merkevare, ikke en generisk bookingportal.** Nettsiden kan se ut og føles som AURA SKIN Klinikk, ikke som en av mange klinikker inne i en tredjeparts app.
- **Ingen løpende abonnementskostnad** for en klinikk som drives av én person med antagelig begrenset budsjett — engangsutvikling fremfor 200–1000+ kr/mnd i SaaS-avgift.
- **Enkelhet tilpasset faktisk behov.** Klinikken har én behandler; mange SaaS-verktøy er bygget for flere ansatte/ressurser og bærer kompleksitet klinikken ikke trenger.

Dette er ærlig talt ingen teknologisk vollgrav — en ferdig SaaS-løsning kunne løst det samme funksjonelt, kanskje raskere. Fordelen ligger i skreddersøm, merkevarekontroll og at løsningen samtidig er et portefølje-bevis for utvikleren, ikke i unik teknologi.

## Hvem dette er for

**Primær: klinikkeieren.** Driver AURA SKIN Klinikk alene i Salhus. Trenger å bruke mindre tid på booking-kommunikasjon og fremstå mer profesjonelt overfor nye kunder. Suksess for henne = færre meldinger å svare på manuelt, en kalender hun stoler på, og et adminpanel hun faktisk mestrer selv uten teknisk hjelp.

**Primær: klinikkens kunder.** Vil raskt finne ut hva klinikken tilbyr, hva det koster, og booke en ledig time uten å vente på svar. Suksess for dem = booking tar under et par minutter, uten meldingsutveksling.

**Sekundær: utvikleren selv.** [ASSUMPTION] Dette er et frilansprosjekt hvor et vellykket, ryddig sluttresultat skal fungere som referanse overfor fremtidige oppdragsgivere. Dette påvirker kvalitetsbaren på briefen — løsningen skal ikke bare "fungere", den skal se gjennomført og profesjonell ut.

## Suksesskriterier

- Klinikkeieren kan motta og administrere en booking uten å involvere utvikleren i det daglige.
- En ny kunde kan gå fra "vet ikke hva klinikken tilbyr" til "har booket en time" på egen hånd, uten å sende en melding først.
- Antall booking-relaterte meldinger klinikken mottar på Facebook/telefon går ned sammenlignet med i dag. [ASSUMPTION — ingen baseline målt ennå; bør bekreftes med klinikkeier etter lansering]
- Nettsiden er ferdig nok og presentabel nok til at utvikleren selv vil vise den frem som referanseprosjekt overfor potensielle oppdragsgivere.

## Omfang

**Med i første versjon (v1):**
- Informasjonsside om klinikken og de fem behandlingskategoriene, med priser.
- Kalendervisning med faktisk ledige tider for én behandler.
- Selvbetjent booking med enkelt kontaktskjema (navn, telefon, e-post, valgt behandling) — ingen helse-/hudopplysninger.
- Betaling i klinikken (ingen nettbetaling).
- Adminpanel for klinikkeieren til å styre kalender, behandlinger og priser, med parallell tilgang for utvikleren.

**Eksplisitt utenfor v1 (bevisst utsatt, ikke avvist):**
- Nettbetaling / depositum via Vipps — planlagt som neste steg (v2), se Visjon.
- Innsamling av hudtilstand/allergi-informasjon i bookingskjemaet — ville utløst strengere GDPR-krav (helsedata, art. 9); ikke en del av planen nå.
- Flere behandlere / ressursbasert kalender — klinikken har én behandler i dag.
- Valg av teknisk plattform/stack, domene og hosting — dette avklares i en senere fase, ikke i denne briefen.

## Visjon

Neste steg etter en fungerende v1 er å legge til nettbetaling via Vipps — enten for hele beløpet eller som depositum ved booking for å redusere no-shows, som er en vanlig bruksmåte blant sammenlignbare klinikker. Om løsningen fungerer godt for AURA SKIN Klinikk, er det også en åpning for utvikleren: en dokumentert, gjenbrukbar mal for booking-nettsider til andre små enkeltmanns-klinikker — fra ett vellykket kundeprosjekt til et gjentagbart tilbud.
