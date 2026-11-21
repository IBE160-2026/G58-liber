---
title: "Kundeintervju: spørsmål til klinikkeier"
status: gjennomført
created: 2026-10-04
updated: 2026-10-28
---

# Kundeintervju: spørsmål til klinikkeier

Spørsmål til AURA SKIN Klinikk som grunnlag for PRD og design av bookingnettsiden. Bygger på produktbriefen (`product-brief/brief.md`) og de åpne avklaringene i addendumet.

Svarene i del 2–4 bekrefter eller justerer forslagene i briefens seksjon **Bookingregler**. Forslaget står i parentes, så det er raskt å si «ja» eller gi et annet tall. Regler som ikke spørres om (f.eks. starttider hvert 15. minutt) settes av utvikleren og kan endres senere.

**Prioriter hvis tiden er knapp:** 1, 3–5, 7–8, 12.

## 1. Behandlinger og priser

1. Stemmer kategoriene ansiktsbehandling, laser, botox/filler, vipper/bryn og kroppsbehandling? Hvilke behandlinger finnes under hver, og hva koster og varer de? (Send gjerne en liste.)
2. Er det behandlinger som krever konsultasjon først, eller som ikke skal kunne bookes direkte, for eksempel botox og filler?

## 2. Åpningstider og kalender

3. Hvilke dager og tider jobber du, og har du faste pauser som lunsj?
4. Trenger du tid til rydding og klargjøring mellom kundene? (Forslag: 15 minutter.)
5. Hvor langt frem i tid skal kundene kunne booke, og hvor kort varsel godtar du? (Forslag: inntil 8 uker frem, minst 2 timer før.)
6. Når du tar fri eller har ferie, er det oftest hele dager eller deler av en dag?

## 3. Booking og avbestilling

7. Skal en booking bekreftes med en gang, eller vil du godkjenne hver forespørsel selv? (Forslag: bekreftes med en gang.)
8. Hvilken frist har du for avbestilling, og er det greit at kunden i første omgang avbestiller ved å kontakte deg? (Forslag: 24 timer før.)
9. Holder det med navn, telefon og e-post fra kunden, eller trenger du noe mer?

## 4. Personvern

10. Hvor lenge trenger du å ta vare på kundens navn og kontaktinfo etter en time? (Forslag: 12 måneder, deretter slettes det automatisk.)

## 5. Adminpanel

11. Kommer du mest til å bruke mobil eller PC, og hva vil du se først når du logger inn?
12. Hvilke av disse er viktigst for deg å kunne gjøre selv?
    - se dagens og ukens timer
    - avlyse eller flytte en booking
    - blokkere tid, for eksempel en ettermiddag eller ferie
    - endre åpningstider
    - endre behandlinger og priser
    - legge inn bookinger du får på telefon eller Facebook

## 6. Innhold og design

13. Har du logo, farger eller en stil du vil at siden skal følge, og hvilket inntrykk vil du gi, for eksempel luksus, trygghet eller personlig preg?
14. Har du bilder som kan brukes på siden? Koden til nettsiden ligger åpent på GitHub. Er det greit at bilder og tekster fra Facebook-siden din ligger der, eller skal det brukes plassholdere til siden er i drift?
15. Hva skal ellers stå på siden: adresse og parkering, en «om meg»-del, lenker til Facebook og Instagram?

## 7. Mål og veien videre

16. Hvor mange bookinger har du omtrent i uken, og hvor mange meldinger handler om booking?
17. Hvordan vil du merke at nettsiden fungerer, og er det en dato du ønsker den klar til?
18. Er bekreftelse på e-post, betaling med Vipps eller eget domenenavn noe du ønsker deg senere?

## Notater fra intervjuet

_Dato:_ 2026-10-28

**Hovedkonklusjon:** Klinikken vil ikke ha kalender eller selvbetjent booking. Kunden må nesten alltid avklare en konsultasjon før behandling, og mange behandlinger må godkjennes av lege. Spørsmålene om bookingregler (del 2–4) er derfor ikke lenger aktuelle.

### Svar

- **Ansatte:** to som jobber i klinikken, blant dem en kosmetisk sykepleier.
- **Kanaler i dag:** Facebook og Instagram i stedet for booking. Får mange meldinger og bilder på telefonen. Foretrekker private meldinger, men er villig til å prøve noe nytt.
- **Arbeidsflyt:** konsultasjon først; behandlinger må være legegodkjent.
- **Kapasitet:** rundt 3 kunder om dagen, ca. 1 time hver.
- **Åpningstider:** 10–20. Ikke drop-in; alle besøk etter avtale med kunden.
- **Klinikk:** Haugesund.
- **Ønsket innhold:** om oss med presentasjon og bilder av klinikken og behandlerne; info om behandlinger (f.eks. HIFU), hva de innebærer og pris; åpningstider.
- **Kontakt:** en «Send melding»-side der meldingen videresendes til behandleren på SMS, Facebook og/eller Instagram, pluss lenker til SMS, Facebook, Instagram og e-post.
- **Kundekommunikasjon:** SMS til kunder om avtalte timer, nyhetsbrev og push-varsler.

## Oppfølging: videresending av meldinger

Avgjør om meldinger fra «Send melding»-siden kan sendes inn i Messenger og Instagram (krever Metas API), eller om SMS brukes. Svar hentet fra intervjunotatene 2026-10-28 der de finnes; resten må spørres om.

| Spørsmål | Svar |
|---|---|
| 1. Er Facebook-siden til klinikken en bedriftsside, eller en privat profil? | Ikke avklart. Klinikken bruker Facebook til kundekontakt i dag. |
| 2. Er Instagram-kontoen en bedrifts-/profesjonell konto, og er den koblet til Facebook-siden? | Ikke avklart. Klinikken bruker Instagram til kundekontakt i dag. |
| 3. Hvem er administrator på Facebook-siden, og kan utvikleren få tilgang til å sette opp en kobling? | Ikke avklart. |
| 4. Hvor svarer dere helst på meldinger: SMS, Messenger eller Instagram? Er det nok at meldingen kommer på SMS? | Delvis: foretrekker private meldinger, i dag på Facebook/Instagram og telefon. Ikke avklart om SMS alene er nok. |
| 5. Skal meldingene gå til ett felles nummer/én konto, eller til hver behandler? | Ikke avklart. Klinikken har to ansatte. |
| 6. Hvilket mobilnummer skal meldingene sendes til? | Ikke avklart. |

**Slik brukes svarene:** Nei på 1 eller 2 → SMS + direkte lenker til Messenger/Instagram. Ja på 1–3 → Meta-løsningen undersøkes i arkitekturfasen. Ja på 4 → SMS velges uansett.