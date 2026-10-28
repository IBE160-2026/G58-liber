---
title: "PRD: AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-27
updated: 2026-10-28
---

# PRD: AURA SKIN Klinikk – nettside

## 0. Om dokumentet

Denne PRD-en beskriver hva nettsiden for AURA SKIN Klinikk skal gjøre. Den bygger på produktbriefen (`product-brief/brief.md`), tilleggsmaterialet i `product-brief/addendum.md` og kundeintervjuet med klinikkeieren (`kundeintervju/sporsmal.md`), og gjentar ikke bakgrunnen derfra. Dokumentet er grunnlaget for UX-design, arkitektur og oppdeling i oppgaver.

Begrepene i §3 brukes konsekvent gjennom hele dokumentet. Kravene er nummerert FR-1 til FR-N i §4. Antakelser som må bekreftes med klinikken er merket `[ASSUMPTION]` og samlet i §10. Tekniske valg står i `prd/addendum.md`.

## 1. Visjon

AURA SKIN Klinikk får en egen nettside som presenterer klinikken og behandlerne, forklarer hva behandlingene innebærer og hva de koster, og gjør det enkelt å ta kontakt. Behandlingene starter alltid med en konsultasjon, og mange krever legegodkjenning, så kunden booker ikke selv. I stedet sender kunden en melding fra nettsiden, som kommer frem til behandleren der de allerede svarer kunder: på SMS, Facebook eller Instagram.

Klinikken styrer innholdet selv fra et enkelt adminpanel. Når en time er avtalt, registrerer klinikken den, og kunden får automatisk SMS med bekreftelse og påminnelse. Med nyhetsbrev og push-varsler får klinikken en egen kanal til kundene.

## 2. Målgrupper

### 2.1 Behov som skal dekkes

**Kunden**
- Finne ut raskt hva klinikken tilbyr, hvem behandlerne er, hva en behandling innebærer og hva den koster.
- Ta kontakt for å avtale konsultasjon på en enkel måte, uten å lete etter riktig kanal.
- Bli bekreftet og minnet på timen.
- Få nyheter og tilbud fra klinikken, hvis kunden ønsker det.

**Klinikken** (to ansatte, blant dem en kosmetisk sykepleier)
- Færre gjentatte spørsmål om behandlinger, priser og åpningstider.
- Få henvendelser samlet i kanalene de allerede bruker.
- Slippe å sende bekreftelser og påminnelser for hånd.
- Oppdatere innhold, bilder og priser selv, uten teknisk hjelp.
- Nå kundene direkte med nyhetsbrev og push-varsler.

### 2.2 Ikke målgruppe

- Kunder som vil booke en time selv uten kontakt med klinikken.
- Kunder som vil betale på nettet.

### 2.3 Brukerreiser

**UJ-1. Ida vil prøve HIFU.**
Ida (34) ser et innlegg fra AURA SKIN Klinikk på Instagram og går inn på nettsiden fra mobilen. På behandlingssiden leser hun hva HIFU innebærer, hvor lang tid det tar, hva hun kan forvente, og hva det koster. Hun ser at behandlingen starter med en konsultasjon. Hun trykker «Send melding», fyller inn navn, telefonnummer, velger HIFU og skriver at hun helst vil komme på ettermiddagen. Skjermen bekrefter at meldingen er sendt. Behandleren får meldingen på SMS og Instagram, og ringer Ida tilbake samme dag.
**Kanttilfelle:** Hvis videresendingen til én kanal feiler, kommer meldingen likevel frem på de andre kanalene og vises alltid i adminpanelet.

**UJ-2. Behandleren setter opp timen.**
Etter samtalen med Ida logger behandleren inn i adminpanelet og registrerer en konsultasjon torsdag kl. 16:00. Ida får straks en SMS med tid, sted og hva timen gjelder, og en påminnelse dagen før.

**UJ-3. Klinikken sender ut et tilbud.**
Klinikken har ledige timer neste uke. Behandleren skriver et nyhetsbrev med tilbud og sender et push-varsel til kunder som har slått det på.

## 3. Begreper

- **Behandling:** En tjeneste klinikken tilbyr, med navn, beskrivelse av hva den innebærer, varighet, pris og om den krever legegodkjenning.
- **Pris:** Fast pris («1 200 kr») eller fra-pris («fra 1 200 kr»).
- **Konsultasjon:** Første samtale med en behandler før behandling. Alltid første steg.
- **Legegodkjenning:** Godkjenning fra lege som kreves før enkelte behandlinger. Skjer utenfor nettsiden.
- **Behandler:** En ansatt som utfører behandlinger, presentert under «Om oss».
- **Melding:** En henvendelse kunden sender fra «Send melding»-siden.
- **Videresending:** At en melding automatisk sendes videre til behandleren på SMS, Facebook Messenger og/eller Instagram.
- **Avtalt time:** En time klinikken har avtalt med kunden og registrert i adminpanelet.
- **Bekreftelse:** SMS til kunden når en avtalt time er registrert, flyttet eller avlyst.
- **Påminnelse:** SMS til kunden før en avtalt time.
- **Nyhetsbrev:** E-post klinikken sender til kunder som har meldt seg på.
- **Push-varsel:** Varsel i nettleseren eller på mobilen til kunder som har slått det på.
- **Adminpanel:** Den innloggede delen av nettsiden der klinikken styrer innhold, meldinger, timer og utsendelser.
- **Utvikler:** Rollen som drifter og vedlikeholder nettsiden. Har egen tilgang til adminpanelet.

## 4. Funksjoner

### 4.1 Informasjonssider

#### FR-1: Sidestruktur
Kunden kan navigere mellom Forside, Behandlinger, Om oss, Slik foregår det og Send melding.
- Navigasjonen fungerer på alle sider, også på mobil.
- «Send melding» er synlig på alle sider uten å scrolle på mobil.

#### FR-2: Behandlingsside
Kunden kan se alle behandlinger og åpne én for å se detaljer.
- Hver behandling viser hva den innebærer (hvordan den foregår, varighet, forventet resultat, eventuell nedetid), pris og om den krever legegodkjenning.
- Kun behandlinger klinikken har markert som synlige vises.
- Fra hver behandling kan kunden gå til «Send melding» med behandlingen forhåndsvalgt.

#### FR-3: Om oss
Kunden kan lese om klinikken og hver behandler, med bilder av klinikken og behandlerne.

#### FR-4: Praktisk informasjon
Nettsiden viser åpningstider (10–20), at klinikken kun tar imot etter avtale (ingen drop-in), adresse og kart.

#### FR-5: Slik foregår det
Nettsiden forklarer prosessen: ta kontakt → konsultasjon → eventuell legegodkjenning → behandling.

#### FR-6: Lovlig omtale av behandlinger
Behandlinger som bruker reseptpliktige legemidler omtales uten legemiddelnavn eller merkenavn (for eksempel «rynkebehandling» i stedet for «botox»).
- `[ASSUMPTION: klinikken bekrefter hvilke behandlinger dette gjelder og hvilke betegnelser de bruker]`

### 4.2 Send melding

#### FR-7: Sende melding
Kunden kan sende en melding til klinikken ved å oppgi navn, mobilnummer, ønsket behandling (valgfritt) og fritekst.
- Navn, mobilnummer og melding er påkrevd; mobilnummer valideres.
- Kunden må samtykke til at opplysningene brukes til å svare på henvendelsen.
- Skjemaet ber ikke om bilder eller helseopplysninger, og opplyser om at slike ikke skal sendes.
- Etter innsending vises en bekreftelse om at meldingen er sendt og at klinikken tar kontakt.
- Skjemaet er beskyttet mot spam.

#### FR-8: Videresending til behandleren
En innsendt melding videresendes til behandleren på kanalene klinikken har valgt: SMS, Facebook Messenger og/eller Instagram.
- Meldingen inneholder kundens navn, mobilnummer, ønsket behandling og fritekst.
- Feiler én kanal, sendes meldingen likevel på de andre, og den lagres alltid i adminpanelet.
- `[ASSUMPTION: videresending til Messenger/Instagram er teknisk mulig via Metas API; ellers brukes SMS og e-post, se addendum]`

#### FR-9: Direkte kontaktlenker
Kunden kan også kontakte klinikken direkte via lenker som åpner SMS, Facebook Messenger, Instagram eller e-post.

### 4.3 Avtalte timer og SMS

#### FR-10: Registrere avtalt time
Klinikken kan registrere en avtalt time med kundens navn, mobilnummer, behandling (eller konsultasjon), dato og tid.

#### FR-11: SMS-bekreftelse
Kunden får SMS med dato, tid, adresse og hva timen gjelder når timen registreres.

#### FR-12: SMS-påminnelse
Kunden får en påminnelse på SMS før timen.
- `[ASSUMPTION: sendes kl. 12:00 dagen før]`

#### FR-13: Flytte og avlyse
Klinikken kan flytte eller avlyse en avtalt time, og kunden får beskjed på SMS.

#### FR-14: Timeoversikt
Klinikken kan se kommende avtalte timer i en dags- og ukesliste.

### 4.4 Nyhetsbrev og push-varsler

#### FR-15: Påmelding
Kunden kan melde seg på nyhetsbrev med e-post og slå på push-varsler fra nettsiden.
- Påmelding krever aktivt samtykke.
- Hvert nyhetsbrev har en avmeldingslenke; push-varsler kan slås av når som helst.

#### FR-16: Sende nyhetsbrev
Klinikken kan skrive og sende et nyhetsbrev til alle påmeldte fra adminpanelet.

#### FR-17: Sende push-varsel
Klinikken kan skrive og sende et kort push-varsel, med lenke til en side på nettsiden, til alle som har slått det på.

### 4.5 Adminpanel

#### FR-18: Innlogging
Klinikkens ansatte og utvikleren logger inn med hver sin personlige konto.
- Bare innloggede brukere har tilgang til adminpanelet og kundeopplysninger.

#### FR-19: Innhold
Klinikken kan opprette, endre og skjule behandlinger (beskrivelse, pris, varighet, legegodkjenning), og endre «Om oss», behandlere, bilder, åpningstider og kontaktinformasjon.
- Endringer vises på nettsiden med en gang.

#### FR-20: Meldinger
Klinikken kan se alle innsendte meldinger, markere dem som besvart, og velge hvilke kanaler nye meldinger skal videresendes til.

## 5. Design og tone

- **Visuelt:** Følger klinikkens farger, logo og visuelle uttrykk. Rolig og luftig, få elementer per skjerm.
- **Bilder:** Bilder av klinikken og behandlerne står sentralt og bygger tillit.
- **Tone:** Varm, personlig og faglig trygg. Kort og tydelig språk, uten overdrevne løfter om resultater.
- **Språk:** Norsk (bokmål).
- `[ASSUMPTION: klinikken leverer logo, farger, bilder, tekster og priser]`

## 6. Tverrgående krav

### 6.1 Kvalitet

- **NFR-1 Mobil først:** Alle sider fungerer fra 360 px bredde.
- **NFR-2 Ytelse:** Sidene laster raskt på mobilnett; en kunde kan sende en melding på under 1 minutt.
- **NFR-3 Universell utforming:** WCAG 2.1 nivå AA.
- **NFR-4 Sikkerhet:** HTTPS, passord lagres ikke i klartekst, spam-beskyttelse på skjemaer.

### 6.2 Personvern (GDPR)

- **NFR-5:** Personvernerklæring som forklarer hva som samles inn, hvorfor, hvor lenge og hvordan kunden ber om innsyn eller sletting.
- **NFR-6:** Det samles bare inn navn, mobilnummer, e-post (nyhetsbrev) og meldingstekst. Ingen helseopplysninger eller bilder.
- **NFR-7:** Nyhetsbrev og push-varsler krever eget, aktivt samtykke, adskilt fra kontaktskjemaet.
- **NFR-8:** Meldinger og avtalte timer slettes eller anonymiseres automatisk etter en fastsatt periode. `[ASSUMPTION: 12 måneder]`

### 6.3 Lovlig markedsføring

- **NFR-9:** Nettsiden følger regelverket for markedsføring av kosmetiske behandlinger, inkludert forbudet mot reklame for reseptpliktige legemidler (se FR-6).

## 7. Utenfor omfang

- Kalender og selvbetjent booking: passer ikke klinikkens arbeidsflyt med konsultasjon og legegodkjenning.
- Nettbetaling.
- Kundekonto med innlogging.
- Opplasting av bilder og innsamling av helseopplysninger.
- Digital flyt for legegodkjenning.
- Andre språk enn norsk.

## 8. Suksesskriterier

**Primære**
- **SM-1:** Klinikken oppdaterer innhold, registrerer timer og sender utsendelser selv uten hjelp fra utvikleren. Følges opp de første 4 ukene etter lansering. Validerer FR-10–FR-20.
- **SM-2:** En ny kunde finner pris og innhold for en behandling og sender en melding på mobil på under 2 minutter. Måles med brukertest med 3–5 personer. Validerer FR-1–FR-9.
- **SM-3:** Færre gjentatte spørsmål om pris, behandlinger og åpningstider. Klinikken anslår nivået før lansering og etter 2 måneder.

**Sekundære**
- **SM-4:** Færre uteblitte timer etter innføring av SMS-påminnelser. Validerer FR-12.
- **SM-5:** Nettsiden består en WCAG 2.1 AA-sjekk før lansering. Validerer NFR-3.

**Motvekt**
- **SM-C1:** Antall utsendelser. Nyhetsbrev og push skal være nyttige, ikke hyppige; for mange utsendelser fører til avmeldinger. Motvekt til FR-16–FR-17.

## 9. Åpne spørsmål

1. Hvilke behandlinger bruker reseptpliktige legemidler, og hvilke betegnelser skal brukes? (Klinikken)
2. Har klinikken bedriftskonto på Facebook og Instagram som kan kobles til Metas API? (Klinikken)
3. Skal meldinger gå til én felles mottaker eller til en bestemt behandler? (Klinikken)
4. Hvem betaler for SMS-utsending? (Klinikken)
5. Domene og hosting: hva finnes i dag, og hvem skal eie det? (Klinikken og utvikleren)
6. Når skal nettsiden være ferdig?

## 10. Antakelser

- §4.1 FR-6: Klinikken bekrefter hvilke behandlinger som må omtales uten legemiddelnavn.
- §4.2 FR-8: Videresending til Messenger/Instagram er teknisk mulig.
- §4.3 FR-12: Påminnelsen sendes kl. 12:00 dagen før.
- §5: Klinikken leverer logo, farger, bilder, tekster og priser.
- §6.2 NFR-8: Opplysninger slettes etter 12 måneder.
