# Konkurransesjekk Dimmen Dronefoto

## 2026-11-21 kl. 15:10 — Mikolaj

### Oppgave
Kjøre en konkurransesjekk (bmad-deep-recon, type competitive) for Dimmen Dronefoto: verifisere påstanden i briefen om fastpris, og hente struktur- og designinspirasjon (jf. ønsket «lysshow») til senere arbeid med struktur og grafikk.

### Plan
- Plan godkjent før kjøring: competitive + egen designdimensjon, breadth-first med tre assistenter, to runder, norsk resultat.
- Runde 1: Oslo Drone og Foto + Follo, Kvadratfoto + AVIA + Foss, og nye aktører + designteknikk. Runde 2: prisverifisering mot rå HTML, manglende fakta, farger/fonter fra CSS, dokumentasjon (prefers-reduced-motion, IntersectionObserver, LCP/CLS).
- Semantisk sitatsjekk av rapporten i en fersk assistent.

### Resultat
- Rapport: `.docs/planning-artifacts/research/competitive-dimmen-dronefoto-konkurrenter-2026-11-21/research.md` (+ `digests/` og `.memlog.md`). 28 kilder, sitatsjekk ok.
- Hovedfunn: briefens påstand om at de fleste konkurrenter krever kontakt for pris er feil (åpen pris er vanlig). Andreas' 2 000 kr ligger under alle frittstående dronepriser vi fant (3 000–5 000). Tillit (A1/A3, forsikring, registrering) vises sjelden med bevis. 8 anbefalinger bundet til brief, PRD og design, inkludert teknikk for lysshowet (CSS scroll-driven animations + IntersectionObserver, prefers-reduced-motion).
- Kravsporet: 4 verifisert, 7 ubekreftet, 1 avkreftet (briefens påstand). Tidligste ny sjekk 2027-02-21.
- Filene er ikke committet. HTML-briefing og bmad-review-polering av rapporten er ikke kjørt.

### Åpne punkter
- Rette briefen etter funnene: fjerne «de fleste konkurrenter krever kontakt for pris», og bytte differensiatoren til klarhet og tillit.
- Avklare med Andreas hva 2 000 kr dekker og om prisen er inkl. eller eks. mva (prisposisjonen kan ikke vurderes uten).
- Hente skjermbilder av konkurrentene med nettleser-verktøyet før grafikkfasen (design er lest ut av kode og tekst, ikke sett).
- Sjekke Kvadratfotos pakkepris i nettleser (2 100 eller ca. 2 993) og nettleserstøtten for CSS scroll-driven animations mot en støttetabell.
