---
title: "Product Brief: Dimmen Dronefoto – nettside"
status: draft
created: 2026-11-21
updated: 2026-11-21
---

# Product Brief: Dimmen Dronefoto – nettside

## Sammendrag

Dimmen Dronefoto er et nytt, lite dronefoto-firma som Andreas Dimmen vil starte. Firmaet skal levere dronefoto og -video, først og fremst av eiendom i Oslo og omegn. Andreas har over fire års erfaring som droneoperatør (kurs og eksamen A1/A3) og har levert foto og video til eiendomssalg. Som firma starter han uten logo, nettside og sosiale medier.

Dette prosjektet er en enkel, stilren nettside som blir selve starten på firmaet. Den skal gjøre én ting godt: la en eiendomsmegler eller boligselger raskt se hva som tilbys, hva det koster og hvordan man bestiller, og gi nok tillit til at de tar kontakt med en helt ukjent aktør.

Prosjektet bygges av ML (utvikleren) som et eget prosjekt for en bekjent, og nettsiden skal leveres inn i IBE160 innen **15. desember 2026**. [ASSUMPTION] Prosjektet fungerer samtidig som referanseprosjekt. Det som står på spill er at Andreas får en troverdig nettside han kan bruke til å skaffe de første kundene sine.

## Problemet

Andreas har ingen digital tilstedeværelse. En megler eller privatperson som hører om ham, finner ingenting: ingen priser, ingen eksempler på arbeid, ingen enkel måte å bestille på. [ASSUMPTION] For en tjeneste som bestilles raskt under et boligsalg, kan det bety tapte oppdrag.

For kunden er dronefoto i dag noe man må spørre om. Det er uklart hva det koster, hva man får og hvor lang tid det tar, og nettopp det må en ny aktør uten omdømme gjøre enkelt for å bli valgt.

## Løsningen

En liten nettside på 5 sider: **Om | Tjenester | Prosess | Galleri | Kontakt**.

- **Om:** kort tekst om hva som tilbys, kontaktinfo nederst og et animert «lysshow» som beveger seg mens besøkende blar nedover siden. Andreas ønsker lysshowet og gir fri hånd på utformingen. [ASSUMPTION] Det gjøres subtilt og skal ikke gå utover lastetid eller lesbarhet på mobil.
- **Tjenester:** boligfoto med drone til fast pris (2 000 kr per oppdrag, vist åpent). Alt er inkludert, megler kan bruke bildene fritt, og levering skjer innen 2–3 dager. Dekker Oslo, Asker, Drammen og Lillestrøm. [ASSUMPTION] Ingen reisetillegg, siden reise er inkludert. Dessuten dronevideo og tomt/næringsbygg «etter avtale» med «Be om tilbud»-knapp.
- **Prosess:** [ASSUMPTION] 3–4 enkle steg fra kontakt til levering (ta kontakt, avtal tid og pris, flyging, levering), slik at kunden vet hva som skjer etter at de har tatt kontakt.
- **Galleri:** utvalgte bilder fra tidligere oppdrag, lastet ned fra Google Drive. [ASSUMPTION] Bilder først; video kommer senere via embed når Andreas får en YouTube-kanal.
- **Kontakt:** kontaktskjema som sendes til e-post, i tillegg til telefon og e-post.

Siden gjøres klar for å koble på Instagram, Facebook og YouTube senere, uten at kontoene må finnes ved lansering. Utvikleren har frie hender på logo og farger: stilrent og enkelt, med svart og grått kombinert med lysere farger.

## Hva gjør dette annerledes

Dette er ikke en ny idé; flere etablerte aktører i Oslo-området har tilsvarende nettsider. Forskjellen ligger i hva siden vektlegger:

- **Alt samlet på ett sted:** fastpris, hva som er inkludert, leveringstid, bruksrett og trygghet (forsikring). Åpen pris er vanlig hos konkurrentene, men få viser samtidig hva som er inkludert, leveringstid og bruksrett (konkurranseanalysen i `.docs/planning-artifacts/research/competitive-dimmen-dronefoto-konkurrenter-2026-11-21/research.md`). 2 000 kr ligger under konkurrentenes frittstående dronepriser (3 000–5 000 kr), så det må stå tydelig at alt er inkludert.
- **Rett tone for en nystartet aktør:** proff, men ikke overdrevet. Andreas' egen favoritt (oslodroneogfoto.no) er «litt for proff» for ham; målet er troverdig og ærlig, ikke å late som om firmaet er større enn det er.

## Hvem dette er for

**Hovedkunder:** eiendomsmeglere og privatpersoner som selger bolig i Oslo og omegn. Meglere kjøper jevnlig og vil ha rask, forutsigbar levering til en klar pris. Privatpersoner kjøper én gang og trenger trygghet og enkelhet. [ASSUMPTION] Meglere er den viktigste gruppen på sikt fordi de gir gjentakende oppdrag.

**Andreas** er den andre brukeren: han skal kunne stå inne for siden som firmaets ansikt utad. I første versjon gjør ML endringer, og hvordan Andreas selv kan redigere avtales senere. Begge bør ha tilgang til å endre tekst.

## Suksesskriterier

- Besøkende forstår hva som tilbys, hva boligfoto koster og hvordan de bestiller, uten å måtte spørre om noe.
- Andreas får henvendelser via kontaktskjema eller telefon.
- [ASSUMPTION] Mål for de første månedene: de første betalende oppdragene kommer via siden. Konkret tall avklares med Andreas.
- Siden laster raskt og fungerer godt på mobil. [ASSUMPTION] Det er sannsynligvis her de fleste meglere ser den.

## Omfang

**Frist og innlevering:** 15. desember 2026. Alt skal leveres inn i IBE160: nettsiden og dokumentasjonen fra BMAD-arbeidet er begge en del av prosjektet.

**Rammer:** arbeidet følger BMAD-metoden, siden bygges med HTML, CSS og JavaScript, og hosting er Vercel som utgangspunkt.

**Krav til Andreas:** han har ansvarsforsikring for droneflyging. Gyldig droneoperatør-registrering må være dokumentert før han tar betalte oppdrag, uavhengig av firmaregistrering, og siden nevner den først når beviset foreligger.

**Med i første versjon:** alt under Løsningen, pluss logo, fargepalett og enkel visuell identitet. Siden er på norsk.

**Utenfor første versjon:**
- Booking med kalender og betaling på nett
- Innlogging og eget adminpanel. Andreas redigerer ikke selv i første versjon; ML gjør endringer, og redigeringsløsning avtales etter prosjektet.
- Blogg, kundeanmeldelser og referanser (finnes ikke ennå)
- Aktive sosiale medier
- Organisasjonsnummer og registreringsbevis på siden. Andreas har ikke registrert firma ennå. Forsikringen kan nevnes.

## Åpne spørsmål

**Andreas**
- Er 2 000 kr inkl. eller eks. mva? (2 000 kr dekker alt, men mva-status er ikke oppgitt.)
- Kan han sende kopi av forsikringsbeviset og dokumentasjon på droneoperatør-registreringen?
- Har kundene eller meglerne gitt lov til å vise bildene fra tidligere oppdrag offentlig? De viser andres boliger. (Andreas sier vi kan bruke bildene han har sendt.)
- Er det reisetillegg til Asker, Drammen og Lillestrøm? Han kjører dit, og reise er inkludert i prisen, men tillegg er ikke bekreftet.

**ML**
- Domenet `dimmendronefoto.no`: Andreas ba ML ordne det. Hvem skal stå som eier, og hvem betaler?

**Arkitektur**
- Tekst, priser og bilder bør ligge samlet (for eksempel i en egen innholdsfil) slik at både ML og Andreas kan ha tilgang til å endre dem uten å røre koden. Redigeringsløsning for Andreas (enkel CMS eller filredigering) avtales etter at prosjektet er ferdig.
- Hvordan sender kontaktskjemaet e-post fra en HTML/JS-side på Vercel: ekstern tjeneste som Formspree, eller en liten serverless-funksjon?

## Visjon

Hvis dette går bra, blir siden det sentrale stedet for Dimmen Dronefoto: et sted som viser arbeidet, samler henvendelser og etter hvert også video, anmeldelser og aktive sosiale medier. Neste steg kan være nettbooking og enkel oppdragsstyring, men først må de første kundene være på plass.
