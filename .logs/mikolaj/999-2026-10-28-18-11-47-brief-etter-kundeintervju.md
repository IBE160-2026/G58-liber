# Brief etter kundeintervju

## 2026-10-28 kl. 18:11 — Mikolaj

### Oppgave
Oppdatere brief, PRD og intervjudokument etter møtet med klinikkeieren. Klinikken vil ikke ha kalender eller booking. Kundene skal ta kontakt via en «Send melding»-side før konsultasjon.

### Plan
- Ført inn intervjunotatene og skrevet om briefen flere ganger etter tilbakemelding fra brukeren.
- Oppdatert product-brief/addendum, prd/prd.md, prd/addendum.md og kundeintervju/sporsmal.md slik at de stemmer med briefen.
- Committet og pushet.

### Resultat
- Briefen: ingen booking. Nettsiden har om oss med bilder, en behandlingsside med hva behandlingene innebærer og pris, åpningstider 10–20 (kun etter avtale) og en «Send melding»-side som videresender til behandleren på SMS, Facebook og/eller Instagram. Siden har også direkte lenker til SMS, Facebook, Instagram og e-post. Adminpanelet dekker innhold, registrering av avtalte timer med automatisk SMS-bekreftelse og påminnelse, nyhetsbrev og push-varsler.
- PRD skrevet om (FR-1–FR-20) og tatt ut av ventestatus.
- Intervjunotatene er ført inn i kundeintervju/sporsmal.md.
- Commit 0e38f3a, pushet til origin/main etter rebase på e16df12.

### Åpne punkter
- Avklare klinikkens sted: den gamle brief-memloggen sier Salhus («Haugesund korrigert»), mens intervjunotatet sier «Haugesund klinikk». Dokumentene sier nå Haugesund.
- Bekrefte at «Hifo» i notatene betyr behandlingen HIFU.
- Undersøke om det går å videresende meldinger til Messenger/Instagram via Metas API, eller om reserveløsningen med SMS/e-post må brukes.
- Åpne spørsmål i PRD §9: reseptpliktige legemidler, Meta-bedriftskonto, mottaker per behandler, hvem som betaler for SMS, domene/hosting og frist.
