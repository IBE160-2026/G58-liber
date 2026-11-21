# Research og brainstorming for Dimmen Dronefoto

## 2026-11-21 kl. 16:21 — Mikolaj

### Oppgave
Før PRD-en skrives: kjøre research (regelverk, teknisk løsning, kundenes behov) og en brainstorming om lysshow og visuell stil, innhold og struktur, og navn og merkevare. I tillegg: opprette GitHub-issues for det som gjenstår, og fjerne Andreas' registreringsstatus fra den offentlige repoen.

### Plan
- Opprette sju GitHub-issues (`IBE160-2026/G58-liber`, #1–#7) og gjøre teksten om droneoperatør-registrering nøytral i brief, addendum, memlog, logger og `issues.md`. Commit og push (`789c404`).
- Tre research-kjøringer (`bmad-deep-recon`, standard, seks assistenter i første runde og to verifiseringsassistenter), godkjent plan med bruker.
- Brainstorming (`bmad-brainstorming`, Facilitator): 4 valgte teknikker fra velgersiden, 12 valgt av meg og 4 oppfunnet. Memlog: `.docs/brainstorming/brainstorm-dimmen-dronefoto-nettside-2026-11-21/.memlog.md`.

### Resultat
- **GitHub-issues #1–#7 opprettet** og registreringsstatusen er byttet ut med nøytral ordlyd. Pushet som `789c404`. Teksten ligger fortsatt i tidligere commits i historikken (`5466e70` med flere).
- **Tre research-rapporter** (ikke committet) i `.docs/planning-artifacts/research/`, hver med `digests/`, `.memlog.md` og `research.md`:
  - `domain-regelverk-droneflyging-og-eiendomsfoto-2026-11-21/`
  - `technical-nettside-vercel-skjema-og-redigering-2026-11-21/`
  - `user-voice-meglere-og-boligselgere-om-dronefoto-2026-11-21/`
- Hovedfunn: forsikring er **ikke lovpålagt** for droner under 250 g i åpen kategori (brief og issue #2 antok krav); operatørregistrering kreves, men registreringstype for enkeltperson er uavklart; boligeiere må samtykke til bilder i galleriet (Datatilsynet); **Vercel Hobby er kun for ikke-kommersiell bruk** (Vercel Terms), så produksjonshosting må avgjøres; innhold i `content.json` redigert via GitHub i v1; kontaktskjema via Formspree er raskest; norsk kundestemme finnes nesten ikke offentlig, og «68 % raskere salg» har ingen sporbar kilde. Sitatsjekk og bmad-review er ikke kjørt på de nye rapportene.
- **Brainstorming pågår** (status ikke `complete`): Five Whys (rot: megleren vil slippe oppfølging og bruke tiden på å selge), Future Anthropologist Dig, Three Rounds of Stupid og Steal And Upgrade er kjørt, og Sensory Exploration (lysshow) er halvveis. Ca. 40 ideer er logget. Eksempler: én-knapps bestilling uten telefon og med automatisk bekreftelse, tilbud og tidspunkt automatisk, bilder levert med lenke i mail, gatebilde til naboene i samme bestilling, lydsignal når bestillingen er sendt, hero-video som starter stille og viser pris og løfte, lysshow «som en myk bris, lavt ettermiddagslys».

### Åpne punkter
- Gjenoppta brainstormingen fra `.memlog.md`: neste spørsmål er hvilke farger lysshowet har og hva som skjer med dem mens man blar; så 11 gjenstående valgte teknikker og de 4 oppfunne, konvergering og wrap-up.
- Rette brief («Krav til Andreas») og GitHub-issue #2: ansvarsforsikring er ikke lovpålagt for drone under 250 g i åpen kategori, men er et tillitssignal.
- Spørre Luftfartstilsynet skriftlig hvilken operatørregistreringstype (privat 230 kr, organisasjon 1 500 kr, pilot) en enkeltperson som selger droneflyging skal bruke.
- Skaffe skriftlig samtykke fra boligeierne for bildene i galleriet (eller bruke anonymiserte bilder). Delvis dekket av issue #1.
- Avgjøre produksjonshosting før lansering: Vercel Pro (20 USD/mnd) eller Cloudflare Pages etter at vilkårene er lest i fulltekst. Hold siden vertsuavhengig.
- Kjøre bmad-review og sitatsjekk på de tre nye research-rapportene, og avgjøre om de skal committes.
- Vurdere 2–3 meglerintervjuer for ekte kundestemme.
