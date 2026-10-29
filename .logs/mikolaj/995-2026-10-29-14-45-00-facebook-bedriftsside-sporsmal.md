# Facebook-bedriftsside og spørsmål til klinikken

## 2026-10-29 kl. 14:45 — Mikolaj

### Oppgave
Klinikkeieren forsto ikke spørsmålet om privat profil kontra bedriftsside (Meta Business) på Facebook, som gjaldt om kundene kan skrive til klinikken i Facebook/Messenger. Brukeren ba om en enkel forklaring og enklere spørsmål, og la senere til at Facebook-siden ser ut som en bedriftsside.

### Plan
- Lese spørsmål 6–7 i `kundeintervju/sporsmal-oppfolging.md` og relevant research (`prd/addendum.md`) for å se hvorfor spørsmålet betyr noe.
- Skrive en forklaring og en melding brukeren kan sende klinikkeieren.
- Etter at brukeren bekreftet at siden er en bedriftsside: skrive om spørsmål 6–7 og lage ny PDF.

### Resultat
- Meldingsutkast med forskjellen mellom privat profil, Facebook-side og Meta Business Suite (verktøy, ikke sidetype), pluss tre enkle spørsmål. Gitt i chat, ikke lagret i repoet.
- Viktig begrunnelse: etter researchen 2026-10-28 bygger vi ikke videresending fra skjema til Messenger. Spørsmålet gjelder bare at `m.me`/`ig.me`-lenkene må peke til en side.
- `kundeintervju/sporsmal-oppfolging.md`: spørsmål 6 sier at Facebook-siden er en bedriftsside (brukerens observasjon: «Følg»-knapp, ikke «Legg til venn») og spør om Instagram er profesjonell og koblet til. Spørsmål 7 er forenklet til «hvem logger inn», uten passord. `updated` satt til 2026-10-29.
- `kundeintervju/sporsmal-oppfolging.pdf` laget på nytt med ReportLab (2 sider, uten intern PRD-tabell). Scriptet lå i scratchpad og er ikke lagret i repoet. Innholdet er kontrollert ved å dekode PDF-strømmen; siden er ikke åpnet visuelt (ingen PDF-renderer installert).
- Endringene i spørsmålsfilene er ikke committet. Ingenting er pushet.

### Åpne punkter
- Sende oppdatert melding eller PDF til klinikkeieren og få svar på om Instagram er en profesjonell konto koblet til siden, og hvem som er administrator (spørsmål 6–7).
- Ordlyden «Bytt til personlig konto» (Instagram-innstillinger) er ikke verifisert mot norsk grensesnitt. Sjekk den, og åpne PDF-en visuelt, før den sendes.

## 2026-10-29 kl. 15:10 — Mikolaj

### Oppgave
Brukeren ba meg huske at klinikken er i Haugesund, Salhus, og ga senere adressen Bøvegen 60, Salhus, 4260. Brukeren bestemte å beholde adressen etter at jeg pekte på at 4260 ikke passer Haugesund.

### Plan
- Sjekke adressen på nett, og melde fra om avviket.
- Rette dokumentene som beskriver klinikken, når brukeren hadde bestemt seg.

### Resultat
- Nettsøk fant ikke adressen. Salhus har postnummer 5107 og ligger i Bergen. 4260 hører etter min kunnskap til Torvastad i Karmøy (ikke verifisert). Brukeren mente Karmøy høres riktig ut.
- Rettet fra Haugesund til Bøvegen 60, 4260 Salhus (Karmøy) i `product-brief/brief.md`, `prd/prd.md` (inkl. søketermen «hudpleie Karmøy»), `prd/prd-grunnlag.md`, spørsmål 23 i `kundeintervju/sporsmal-oppfolging.md` og scope-notatet i research.md. Gamle logger, memlogger og `kundeintervju/sporsmal.md` (intervjunotater) er ikke endret.
- PDF-en `kundeintervju/sporsmal-oppfolging.pdf` laget på nytt med den nye ordlyden i spørsmål 23.
- `issues.md`: punktet «Salhus eller Haugesund» lukket, konkurrentpunktet endret til Karmøy.
- Endringene i prosjektfilene er ikke committet og ikke pushet. `prd/` hadde allerede ukommitterte endringer fra før.

### Åpne punkter
- Klinikken må bekrefte kommunen (Karmøy) i spørsmål 23.
- Konkurrentdelen i researchen må gjøres om for Karmøy (allerede i `issues.md`).
