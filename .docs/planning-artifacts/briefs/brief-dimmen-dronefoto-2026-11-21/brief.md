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
- **Tjenester:** boligfoto med drone til fast pris (2 000 kr per oppdrag, vist åpent), samt dronevideo og tomt/næringsbygg «etter avtale» med «Be om tilbud»-knapp.
- **Prosess:** [ASSUMPTION] 3–4 enkle steg fra kontakt til levering (ta kontakt, avtal tid og pris, flyging, levering), slik at kunden vet hva som skjer etter at de har tatt kontakt.
- **Galleri:** utvalgte bilder fra tidligere oppdrag, lastet ned fra Google Drive. [ASSUMPTION] Bilder først; video kommer senere via embed når Andreas får en YouTube-kanal.
- **Kontakt:** kontaktskjema som sendes til e-post, i tillegg til telefon og e-post.

Siden gjøres klar for å koble på Instagram, Facebook og YouTube senere, uten at kontoene må finnes ved lansering. Utvikleren har frie hender på logo og farger: stilrent og enkelt, med svart og grått kombinert med lysere farger.

## Hva gjør dette annerledes

Dette er ikke en ny idé; flere etablerte aktører i Oslo-området har tilsvarende nettsider. Forskjellen ligger i hva siden vektlegger:

- **Tydelig fastpris synlig på siden** for den vanligste tjenesten og lav terskel for å bestille, mens de fleste konkurrenter krever kontakt for pris. [ASSUMPTION] Ikke verifisert mot konkurrentenes sider; sjekkes mot referansesidene i addendumet.
- **Rett tone for en nystartet aktør:** proff, men ikke overdrevet. Andreas' egen favoritt (oslodroneogfoto.no) er «litt for proff» for ham; målet er troverdig og ærlig, ikke å late som om firmaet er større enn det er.

## Hvem dette er for

**Hovedkunder:** eiendomsmeglere og privatpersoner som selger bolig i Oslo og omegn. Meglere kjøper jevnlig og vil ha rask, forutsigbar levering til en klar pris. Privatpersoner kjøper én gang og trenger trygghet og enkelhet. [ASSUMPTION] Meglere er den viktigste gruppen på sikt fordi de gir gjentakende oppdrag.

**Andreas** er den andre brukeren: han skal kunne stå inne for siden som firmaets ansikt utad. [ASSUMPTION] Han endrer ikke innhold selv i første versjon; ML gjør endringer.

## Suksesskriterier

- Besøkende forstår hva som tilbys, hva boligfoto koster og hvordan de bestiller, uten å måtte spørre om noe.
- Andreas får henvendelser via kontaktskjema eller telefon.
- [ASSUMPTION] Mål for de første månedene: de første betalende oppdragene kommer via siden. Konkret tall avklares med Andreas.
- Siden laster raskt og fungerer godt på mobil. [ASSUMPTION] Det er sannsynligvis her de fleste meglere ser den.

## Omfang

**Frist:** 15. desember 2026.

**Rammer:** arbeidet følger BMAD-metoden, siden bygges med HTML, CSS og JavaScript, og hosting er Vercel som utgangspunkt.

**Krav til Andreas:** droneoperatør-registrering og forsikring må være på plass før han tar betalte oppdrag, uavhengig av firmaregistrering.

**Med i første versjon:** alt under Løsningen, pluss logo, fargepalett og enkel visuell identitet. Siden er på norsk.

**Utenfor første versjon:**
- Booking med kalender og betaling på nett
- Innlogging og adminpanel
- Blogg, kundeanmeldelser og referanser (finnes ikke ennå)
- Aktive sosiale medier
- Organisasjonsnummer, forsikring og registreringsbevis på siden. Andreas har ikke registrert firma ennå.

## Åpne spørsmål

**Andreas**
- Hva dekker 2 000 kr (antall bilder, redigering, reisekostnad, bruksrett), og hva er leveringstiden?
- Hvor langt kjører han, og er det tillegg utenfor Oslo?
- Har han lov til å vise bildene fra tidligere oppdrag offentlig? De viser andres boliger.
- Har han et domene, og hvem endrer innhold etter lansering?
- Svarene må komme tidlig. Det som ikke er avklart innen utgangen av november, løses med en enkel standardløsning i stedet for å vente.

**ML**
- Hva skal leveres inn i IBE160 ved fristen: kun nettsiden, eller også dokumentasjon fra BMAD-arbeidet?

**Arkitektur**
- Hvordan sender kontaktskjemaet e-post fra en HTML/JS-side på Vercel: ekstern tjeneste som Formspree, eller en liten serverless-funksjon?

## Visjon

Hvis dette går bra, blir siden det sentrale stedet for Dimmen Dronefoto: et sted som viser arbeidet, samler henvendelser og etter hvert også video, anmeldelser og aktive sosiale medier. Neste steg kan være nettbooking og enkel oppdragsstyring, men først må de første kundene være på plass.
