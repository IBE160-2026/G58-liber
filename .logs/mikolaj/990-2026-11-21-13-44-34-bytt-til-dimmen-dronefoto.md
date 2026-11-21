# Bytt til Dimmen Dronefoto

## 2026-11-21 kl. 13:44 — Mikolaj

### Oppgave
Bytte prosjektfokus fra AURA SKIN Klinikk til Dimmen Dronefoto (nettside for nytt dronefoto-firma, Andreas Dimmen), arkivere AURA-materialet, lage en ny product brief og pushe alt til det eksisterende GitHub-repoet (`IBE160-2026/G58-liber`, `main`).

### Plan
- Arkivere AURA-briefen, og kjøre `bmad-product-brief` for Dimmen Dronefoto (hurtigløype, norsk).
- Lage mail til Andreas med spørsmål som bare han kan svare på.
- Skrive utkast til brief med `[ASSUMPTION]`-merker uten å vente på svar.
- Commit og push. Pushen ble avvist fordi remote hadde 70 AURA-commits (PRD v8, brief v3, kundeintervju m.m.), så remote ble slått sammen og alt AURA-relatert arkivert.

### Resultat
- Ny brief (draft): `.docs/planning-artifacts/briefs/brief-dimmen-dronefoto-2026-11-21/` med `brief.md`, `addendum.md` og `.memlog.md`.
- Merge med `origin/main`: konflikter om den gamle briefen løst ved å ta remotes versjon (`product-brief/` v3 erstatter v1-briefen).
- Alt AURA-relatert flyttet til `arkiv/aura-skin-klinikk/`: `product-brief/`, `prd/`, `kundeintervju/`, `overlevering/`, samt `docs/` (prds, research, architecture, research-competition). Forklaring i `arkiv/README.md`. `.logs/`, `CLAUDE.md` og `.claude/` ble stående.
- Commits: `9e882f1` (ny brief og første arkivering), `6ca2a68` (merge), `ff4912e` (arkivering av resten). Pushet til `main`, ikke force.
- Beslutninger: ikke registrert firma ennå, så org.nr., forsikring og registreringsbevis er utenfor første versjon.

### Åpne punkter
- Få svar fra Andreas på mailen (innhold i 2 000 kr, leveringstid, kjørerekkevidde, domene, vedlikehold, bruksrett til tidligere bilder) og oppdatere briefen.
- Avklare frist og krav fra IBE160 (tech stack, innlevering) og hva «lysshow» på Om-siden betyr.
- Kjøre `bmad-review` (struktur og prosa) på Dimmen-briefen før status settes til ferdig.
- Åpne AURA-punkter i denne filen peker på gamle stier (`prd/`, `kundeintervju/` m.m.) som nå ligger i `arkiv/aura-skin-klinikk/`.
