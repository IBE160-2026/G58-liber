# Research: regler og kanaler for nettsiden

## 2026-10-28 kl. 19:58 — Mikolaj

### Oppgave
Kjøre `bmad-deep-recon` (Run) for å få dekning for de uverifiserte punktene i PRD-en: regler for omtale av reseptpliktige behandlinger, om et nettskjema kan sende meldinger til Messenger/Instagram, lokale konkurrenter, og om FAQ, nyhetsbrev og push-varsler hører hjemme i PRD-en. Brukeren svarte «Run» og deretter «go and run all».

### Plan
- Plan-gate: fire dimensjoner (A norske regler, B Meta-meldinger, C konkurrenter, D FAQ/nyhetsbrev/push), preset `standard`, validering `normal`, bred fan-out med én assistent per dimensjon, bare nettsøk.
- A, B og C parallelt; D startet da C var ferdig (grense på tre samtidige).
- Verifisering av bærende påstander med to uavhengige verifikatorer (regler; Meta/Google/iOS-push), uten tilgang til prosjektfiler.
- Syntese til `research.md`, sitatsjekk og staleness-kart.
- `uv` er ikke installert; skriptene ble kjørt med Python 3.14 i stedet.

### Resultat
Alt ligger i `.docs/planning-artifacts/research/domain-norwegian-clinic-site-rules-and-channels-2026-10-28/` (ikke committet, ligger som ikke-sporet mappe): `research.md` (status complete), `digests/` (A, B, C, D og to verifikasjonsfiler), `.memlog.md`. Skriptene kjørte med `python`, og sitatsjekken er ren (ingen hengende markører eller foreldreløse rader). Frontmatter viser 4 verifiserte og 6 uverifiserte påstander.

Hovedfunn:
- Å navngi botox, botulinumtoksin eller kodeord («toksin», «BTX») på klinikkens egen nettside og sosiale medier regnes som forbudt legemiddelreklame (DMP, veileder oppdatert 2025-11-11; vedtak mot Lead Partner AS 2025-04-23, tvangsmulkt 5 000 kr/dag). Nøytrale behandlingsnavn som «rynkebehandling» er en slutning fra DMPs formulering, ikke et godkjent ordvalg.
- Forskrift om markedsføring av kosmetiske inngrep (FOR-2005-07-01-749): ingen før/etter-bilder (§ 5), medisinsk ansvarlig skal navngis (§ 4), ikke rettet mot under 18. § 7 ser ut til å forby markedsføringshenvendelser om kosmetiske inngrep til forbrukere på e-post/SMS. Dette er lest kun én gang via sammendrag og ikke verifisert.
- Helsepersonelloven §§ 4 a/4 b verifisert (i kraft 2022-07-01).
- Meta: et nettskjema kan ikke legge en samtale i klinikkens innboks (Instagram-API tillater bare svar etter at brukeren har skrevet først). `m.me`/`ig.me`-lenker er veien inn. Chat-pluginen er rapportert fjernet 2024-05-09, men bare vendor-kilder sier det. Det er uverifisert om bilder sendt via lenkene kommer fram i Business Suite.
- Google avviklet FAQ-rikt resultat i 2026 (verifisert). Push på iPhone krever Hjem-skjerm-app. Ingen kilde viste at en FAQ-side reduserer henvendelser.
- Konkurrenter (fire lest førstehånds): bare Skin Clinic Molde viser priser åpent; Velbehag har FAQ og resultatside med bilder; ingen viste nyhetsbrev, Messenger eller kontaktskjema.
- Anbefalinger i `research.md`: regel mot legemiddelnavn, nøytrale behandlingsnavn, ingen før/etter-bilder, `m.me`/`ig.me`-knapper i stedet for videresending, FAQ som liten infoside, nyhetsbrev utsatt, push utelatt fra v1.
- Ikke kjørt: red-team, andre runde (depth 2) og `bmad-review` på rapporten. Hullene står som åpne spørsmål i rapporten.
- Ingen endringer i `prd/` eller `product-brief/`.

### Åpne punkter
- Lese kilden for forskrift § 7 (markedsføringshenvendelser om kosmetiske inngrep til forbrukere) og markedsføringsloven § 15 på Lovdata, og avgjøre om § 7 også gjelder SMS-påminnelser.
- Finne ut hva lovendringen LOV-2026-06-19-42 (i kraft 2026-07-01) endrer i helsepersonelloven.
- Spørre DMP om merkenavn i prislister (kilder er uenige), og la klinikkens lege godkjenne endelige behandlingstekster.
- Teste med klinikkens egen Facebook-side at bilder fra `m.me`/`ig.me` kommer fram i Business Suite.
- Utføre manuelt Google-søk fra Molde («hudpleie Molde») og lese anmeldelser av konkurrentene.
- Oppdatere PRD (v2) med funnene: ordvalgsregel, før/etter-forbud, `m.me`/`ig.me` i stedet for videresending (FR-8), FAQ-omfang, nyhetsbrev og push.
