---
title: "Addendum: PRD AURA SKIN Klinikk – nettside"
status: draft
created: 2026-09-27
updated: 2026-11-18
---

# Addendum til PRD

Utdypende og tekniske notater som ikke hører hjemme i selve PRD-en, men som er nyttige for arkitektur- og UX-fasen.

## Hvorfor ikke selvbetjent booking

Tidligere utkast la opp til at kunden booker direkte i en kalender. Etter kundeintervjuet (2026-10-28) ble dette forkastet: alle behandlinger starter med en konsultasjon, mange krever legegodkjenning, og kunden må nesten alltid snakke med behandleren først. Klinikken ønsker heller at kunden sender en melding som når behandleren der de allerede svarer. Timen registreres av klinikken etterpå, og SMS-bekreftelse og påminnelse sendes automatisk.

## Videresending til Facebook og Instagram (FR-8, FR-9)

Status etter research 2026-10-28 og brief versjon 2 (2026-10-29): videresending fra skjemaet til Messenger og Instagram er ikke med i første versjon. Klinikken ønsker det, og briefen fører det som et ønske som avgjøres i arkitekturfasen; PRD-en garanterer bare SMS og e-post pluss samtalelenker.

- Metas Instagram Messaging API lar en app sende en melding til en bruker først etter at brukeren har skrevet til kontoen. For Messenger åpnes meldingsvinduet (24 timer, 7 dager etter annonser med «Click-to-Messenger/Direct») av brukerhandlinger. En skjemainnsending står ikke på listen. Slutningen «skjema kan ikke åpne et vindu» er utledet, ikke ordrett bekreftet.
- Et eget Meta-oppsett ville krevd en Meta-app, tillatelsen `instagram_business_manage_messages` og webhook-infrastruktur. Krav til App Review og Business Verification er ikke undersøkt.
- Human Agent-merket gir ytterligere 7 dager for manuelle svar, men krever godkjenning av appen.
- **Valgt løsning:** SMS og e-post til behandleren, og lenker (`m.me/<side>`, `ig.me/m/<brukernavn>`, `sms:`) slik at kunder som vil, skriver selv i Messenger eller Instagram. `ig.me` virker ikke på Instagram Web. Format for `m.me` er bare bekreftet av tredjepartskilder.
- Meta-chat-pluginen (innebygd chatboble) er rapportert fjernet 9. mai 2024. Kun tredjepartskilder; Metas egen endringslogg viser ingen oppføring.
- Åpent: kommer bilder sendt via lenkene frem i Meta Business Suite-innboksen? Test med klinikkens egen side.
- Alternativ ikke valgt: WhatsApp Business. Skybasert API har priser per melding, og tjenestemeldinger er betalte fra 2026-10-01 (de første 1 000 per nummer per måned er gratis). Prisen for Norge er ikke hentet, og klinikken bruker ikke WhatsApp i dag.

## SMS-utsending

- SMS krever en ekstern SMS-tjeneste (norske eksempler: Sveve, Link Mobility, 46elks, Twilio). Prisen ligger typisk på noen titalls øre per melding.
- Brukes til videresending av meldinger, bekreftelse, påminnelse og beskjed om flytting/avlysning.
- Avsendernavn (for eksempel «AURASKIN») støttes av de fleste norske leverandører.

## Nyhetsbrev og push-varsler

- Nyhetsbrev krever en e-posttjeneste med god leveringsrate og støtte for avmelding.
- Gratisplaner (undatert, hentet 2026-10-28): MailerLite 250 abonnenter og 2 500 e-poster per måned; Mailchimp 250 kontakter og 500 utsendelser per måned, uten automatisering og planlegging.
- Åpningsrater fra leverandørenes egne målinger ligger mellom 25 % og 48 %, og er oppblåst av Apples personvernfunksjon for e-post. Det finnes ingen norske tall.
- Push-varsler kan løses med Web Push (fungerer i moderne nettlesere, på iPhone kun når nettsiden er lagt til på hjemskjermen som nettapp). Status for 2026 i EU/EØS er ikke bekreftet.
- Markedsføringsloven § 15 krever forhåndssamtykke for e-post og SMS-markedsføring til privatpersoner. Ekomloven § 3-15 krever samtykke for lagring av og tilgang til data på brukerens enhet; om push faller under den, er ikke avklart.
- Forskriften om markedsføring av kosmetiske inngrep § 7 ser ut til å forby markedsføringshenvendelser om slike inngrep til forbrukere på e-post og SMS. Må leses i fulltekst.
- EasySalon (booking, brukt av en konkurrent) har gratisversjon og betalt fra 199 kr per måned eks. mva. (dato ukjent). Ikke aktuelt for dette prosjektet siden klinikken ikke vil ha selvbetjent booking.

## Designforslaget (2026-10-29)

Klikkbar skisse i en privat artefakt, ikke lagret i repoet. Sider: forside, Behandlinger, Om oss, Kontakt oss, Send melding og tre behandlingssider (HIFU og to plassholdere), alle i versjon for datamaskin og mobil. Lenkene mellom sidene virker bare i spillmodus. Krav som følger av designet står i PRD-ens FR-1 til FR-9 og §6; her står bare detaljer til arkitekturfasen.

- **Kart:** statisk bilde fra OpenStreetMap (flis, zoom 16) med nål og kildeangivelsen «© OpenStreetMap-bidragsytere». Nålen ligger på 59.371629, 5.288586, der OpenStreetMap plasserer «Bøvegen 60, 4260». Lenker til Google Maps bruker koordinater, ikke adressetekst:
  - Åpne: `https://www.google.com/maps/search/?api=1&query=59.371629,5.288586`
  - Veibeskrivelse: `https://www.google.com/maps/dir/?api=1&destination=59.371629,5.288586`
  - Begge åpnes i ny fane.
- **Kontaktlenker:** `tel:+4746962914`, `sms:+4746962914`, `mailto:auraskin.as@hotmail.com`, `https://m.me/auraskinklinikk` (antatt navn), `https://www.instagram.com/Auraskinklinikk` (profil, sporingsparametere fjernet), `https://www.facebook.com/auraskinklinikk` (antatt adresse). Facebook, Messenger og Instagram åpnes i ny fane.
- **Kontaktknapper:** tre faste knapper (telefon, kart, e-post). På datamaskin langs høyre kant, på mobil i en fast linje nederst sammen med «Send melding». Hver åpner en infoboks som lukkes med en egen knapp. Infoboksene må kunne brukes med tastatur og skjermleser (NFR-3).
- **Fonter:** designforslaget laster Dancing Script og Montserrat fra Google Fonts. Det sender besøkendes IP-adresse til Google. Fontene hostes selv i den ferdige siden (avgjort 2026-11-18, NFR-14).
- **Menyvalg:** Hjem, Behandlinger, Om oss, Kontakt oss og knappen Send melding. Sidene «Slik foregår det» og «Besøk oss» fra tidligere utkast finnes ikke lenger; Besøk oss er slått sammen med Kontakt oss.
- **Cookies:** ingen statistikk eller sporing i første versjon, og kartet er et eget bilde, så samtykkebanner trengs ikke (NFR-14, avgjort 2026-11-18).
- **Instagram:** knappen bruker `https://ig.me/m/Auraskinklinikk` (brukernavnet må bekreftes). Designforslaget går til profilen og må oppdateres, det samme gjelder forhåndsvalgt behandling i skjemaet.

## Tekniske hensyn for arkitekturfasen

- **Eksterne tjenester bak et grensesnitt:** SMS, e-post og push implementeres slik at en testversjon som logger meldinger kan brukes lokalt.
- **Tidssone:** All tid lagres og vises i norsk tid (Europe/Oslo).
- **Påminnelser (FR-12):** Krever en planlagt jobb.
- **Spam (FR-7):** Rate-limiting og enkel bot-beskyttelse på skjemaet.
- **Innlogging (FR-18):** Minst tre kontoer (to ansatte og utvikler). Tofaktor vurderes.
- **Databehandleravtaler:** Leverandører av hosting, SMS, e-post og push krever databehandleravtale under GDPR.

## Markedsføring av reseptpliktige legemidler

Legemiddelforskriften § 13-4 forbyr reklame for reseptpliktige legemidler rettet mot allmennheten. Botulinumtoksin («botox») er reseptpliktig. Direktoratet for medisinske produkter (DMP, tidligere Statens legemiddelverk) fører tilsyn.

- DMPs veileder for estetiske klinikker (oppdatert 2025-11-11) sier at forbudet gjelder handelsnavn, virkestoff, kodebetegnelser og bilder som viser legemiddelet, på klinikkens egne nettsider og sosiale medier. Kodeord som «toksin», «BTX» og «bot.tox» er ulovlige. Kampanjer og rabatter på behandlingen er forbudt, og det samme gjelder å fortelle eksisterende kunder uoppfordret hvilket legemiddel klinikken bruker.
- Tillatt etter samme veileder: prislister uten påstander om legemiddelet, og lenker til pakningsvedlegg for den som selv leter. Veilederen sier at reglene ikke regulerer markedsføring av behandlinger i seg selv, med mindre markedsføringen tydelig viser hvilke legemidler som brukes. Den gir ingen eksempler på ordlyd, og DMP kan veilede men ikke forhåndsgodkjenne.
- Eksempel på bruk i praksis: en klinikkside bruker «Rynkebehandling» med teksten «Grunnet legemiddelforskriften har vi ikke lov å markedsføre reseptpliktige legemidler mot allmennheten.» Det er bare ett eksempel verifisert.
- Håndhevelse: DMP har offentliggjort omtrent 14 vedtak om botulinumtoksin siden september 2022. Vedtaket mot Lead Partner AS (2025-04-23) ga tvangsmulkt på 5 000 kr per dag; ulovlig innhold var positive utsagn om legemiddelet, klinikklister og priser på botox.
- Fillers regnes som medisinsk utstyr, ikke legemiddel. Reglene om markedsføring av kosmetiske inngrep gjelder likevel (ett sammendrag som eneste kilde for resten av fillers-reglene).
- Se research-rapporten for lenker og sikkerhetsgrad per påstand.
