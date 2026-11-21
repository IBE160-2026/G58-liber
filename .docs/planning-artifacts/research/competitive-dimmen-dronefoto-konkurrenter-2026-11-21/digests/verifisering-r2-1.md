# Digest r2-1: prisverifisering, manglende fakta, design fra rå HTML/CSS, dokumentasjon

Hentet 2026-11-21. Rå HTML/CSS via curl, supplert med WebFetch der det er angitt. Publiseringsdato «ikke oppgitt» med mindre noe annet står.

## A) Prisverifisering

**A1. kvadratfoto.no/dronefoto (Bricks/WordPress)**
- pris, høy (rå HTML): pakkene «Liten boligfotopakke» (20-25 bilder) og «Stor» (30-40 bilder) viser prisen «Inkl. mva.»
- pris, høy, **bekreftet**: «Dronebilder 5-7 stk. (1900,-)». Rå HTML har `data-price="1900" data-max="1"`; prisen står i en boks merket «Inkl. mva.», så 1 900 er med stor sannsynlighet inkl. mva. Dronebilder alene er ikke et eget produkt; de er tillegg til en boligfotopakke.
- pris, middels: «3990,- og 2100» = `data-base-price="3990"` og `discount-price` 2100 (liten pakke); stor pakke 4600 og 3500. **Avviker:** sidens inline-JS beregner rabattprisen som `Math.round(total*0.75)` og kjører `updatePrice()` ved lasting, altså 25 % rabatt på totalen. Synlig pris er trolig 2 993 (3990 × 0,75), ikke 2 100; 3 500 passer heller ikke med 4600 × 0,75 = 3 450. HTML-tallene ser ut som utdaterte reserveverdier. Ikke testet i nettleser. Bruk «ordinær 3 990 / 25 % rabatt».
- tilbud, høy: «Vi leverer innen to virkedager». Kjøretillegg: «Nei». Betaling: faktura etter fotografering.

**A2. eiendomsfotografen.no/oslo/priser (Eiendomsfotografen AS)**
- pris, høy, **bekreftet**: «Dronefoto i forbindelse med fotopakke + kr 2 000», «Egen utkjøring kun for dronefoto + kr 3 000», «Alle priser er ekskludert mva» (FAQ: 2 000 kr eks. mva / 3 000 kr eks. mva).
- tilbud, høy, **bekreftet**: «Bilder leveres normalt neste hverdag», ekspress mot tillegg.
- pris, høy: tillegg tomtebilder med grenser +3 500, kveldsfoto +4 500, reisetillegg utenfor byen 600. Pakkene 5 500, 6 500 og 7 500 eks. mva. Avbestilling senest 12 timer før.
- tillit, høy: selskapet er Bergen-basert (adresse Bergen, sidetittel «Eiendomsfotograf Bergen»); Oslo-siden er en lokal landingsside.

**A3. oslodroneogfoto.no (Next.js)**
- pris, høy, **bekreftet**: «Dronefoto – 5-10 bilder fra ulike vinkler – fra 5 000 kr inkl. mva. / 4 000 kr eks. mva.» Seksjonen heter «Veiledende priser». «Totalpris inkludert mva. vises først. Pris ekskludert mva. står under for meglere, bedrifter og andre profesjonelle bestillere.»
- pris, høy: boligfoto (25 bilder) 5 000 inkl., dronevideo 6 000 inkl., Matterport 5 000 inkl., plantegning 3 500 inkl. Endelig pris avhenger av størrelse og lokasjon. Leveringstid ikke funnet.

## B) Manglende fakta

**eiendomsfotografen.no/oslo/dronefoto-bolig** (tillit høy)
- tilbud: «4K bilder + kort video», ferdig redigert til Finn-prospekt og sosiale medier; levering neste hverdag. Antall bilder og flytid ikke oppgitt; bruksrett ikke omtalt.
- tillit: «sertifisert dronefører», «kompetansebevis fra Luftfartstilsynet», «Eget forsikringsbevis for kommersiell droneflyvning», «kan dokumentere både kompetansebevis og ansvarsforsikring» (tekst, ikke vist bevis). Nevner begrenset luftrom i deler av Oslo.
- tilbud: råd om når dronefoto lønner seg (eneboliger med tomt, utsikt, premium over ca. 8 mill.), ikke nødvendig for blokkleiligheter midt i sentrum.

**premani.no** (Lovable/Vite-SPA; priser og FAQ via WebFetch, ikke verifisert i rå HTML; tillit middels)
- /prisindikator: «Typisk prisnivå 6 000–6 000 kr eks. mva.» (trolig skrivefeil). Dronefotografering 4 000 kr (mva ikke oppgitt). «Dette er kun en indikasjon». Ingen leveringstid eller bruksrett.
- /dronetjenester: «Sertifisert dronepilot med A1, A2 og A3 kompetansebevis», bildetekst «Remote Pilot Certificate of Competency». Forsikring og Luftfartstilsyn-registrering ikke nevnt. FAQ viser bare spørsmålsoverskrifter, svarene er ikke tilgjengelige.
- Svartid: «normalt innen 24 timer».

**kvadratfoto.no/megler** (rå tekst, høy)
- kontaktflyt: lead-side for meglere: «Ring, send e-post eller fyll ut skjemaet for å få et godt tilbud». Skjemafelt: Navn, Meglerkontor, E-post, Melding. Viser Google-anmeldelser og «Nyeste annonser». Ingen meglerpriser eller rabatter. Skjemaet viser «Google reCaptcha: Ugyldig nettstedsnøkkel» (ikke verifisert i nettleser).

**Tillitssignaler, oversikt**
- Forsikring: bare eiendomsfotografen.no (påstand om forsikringsbevis, uten vist bevis).
- Luftfartstilsynet: Kvadratfoto sier generelt at man må være registrert operatør; Eiendomsfotografen sier «kompetansebevis fra Luftfartstilsynet».
- A1/A3: bare Premani (tekst, bildetekst nevner sertifikat).
- Ingen viser operatørregistreringsnummer eller forsikring konkret.

## C) Design fra rå HTML/CSS (middels; hex telt fra CSS og er støyete)

| Nettsted | Bygg | Farger / fonter | Animasjon, galleri, mobilmeny |
|---|---|---|---|
| kvadratfoto.no | WordPress + Bricks Builder, FlyingPress-cache | Bricks primary #ffd64f, secondary #fc5778 (kan være default). Hyppige: #fb8e28, #202124, #3b82f6 (plugin-støy). Font: Inter | Splide-karusell, PhotoSwipe-lightbox, Lottie-logo (kun >768px), IntersectionObserver for reveal, hamburger/offcanvas. `prefers-reduced-motion` 2 treff i CSS |
| eiendomsfotografen.no | Next.js (Vercel), Bootstrap + tema | Hoved #4c86e5, aksent #9eb9d7, grå #6c757d. Fonter: Montserrat, Muli, Playfair Display | Egne videoer (`preload="metadata"`, poster), lightGallery, Plyr, hamburger. 3 treff på `prefers-reduced-motion` |
| premani.no | Vite/React fra Lovable, Tailwind (shadcn) | Mørkt tema: bakgrunn ≈ #121218, aksent oransje ≈ #e66a1a. Fonter: Inter og Bodoni Moda (serif) | Hero `<img>` preloadet (`fetchpriority="high"`, webp), `animate-in`/`animate-pulse`, 7 IntersectionObserver- og 1 `prefers-reduced-motion`-treff i JS. Ingen gsap/AOS |
| firmafotografen.no | WordPress + WPBakery + Slider Revolution, tema «wood» | Hex usikre (#869791, #b30000 m.fl.) | jQuery, Owl Carousel, Swiper, masonry/mixitup. Ingen `prefers-reduced-motion` i hentet CSS |

## D) Dokumentasjon (primærkilder, høy)
- **prefers-reduced-motion** — MDN, https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion, sist endret 2026-06-10. Verdier `no-preference` og `reduce`; brukeren ber om grensesnitt som «removes, reduces, or replaces motion». Skalering og panorering av store objekter kan utløse vestibulære plager. Mønster: erstatt (pulse → dissolve via opacity) fremfor å fjerne alt.
- **IntersectionObserver** — MDN, https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API, sist endret 2026-09-02. Asynkron rapportering når element kommer inn/ut av viewport; `root`, `rootMargin`, `threshold`; bruk `unobserve` etter første treff; Baseline «Widely available» siden mars 2019. Scroll-reveal følger av API-et (ikke eksplisitt oppført).
- **Trygt å animere** — web.dev, https://web.dev/articles/animations-guide, dato ikke oppgitt. Bruk `transform` og `opacity`; unngå layout/paint-egenskaper; `will-change` sparsomt.
- **LCP** — web.dev, https://web.dev/articles/optimize-lcp, publisert 2020-04-30, oppdatert 2025-03-31. Hero-bilde i HTML med `fetchpriority="high"`, aldri lazy-load; god LCP ≤ 2,5 s (75. persentil), dårlig > 4,0 s. Omtaler ikke hero-video.
- **CLS** — web.dev, https://web.dev/articles/cls, dato ikke oppgitt. God CLS ≤ 0,1, dårlig > 0,25; årsaker: bilder/video uten dimensjoner, fonter som bytter størrelse, dynamisk innhold; animer med `transform`; respekter `prefers-reduced-motion`.

## Lette etter, fant ikke
1. Rå-HTML-bekreftelse av Premanis priser og FAQ-svar (JS-gjengitt).
2. Faktisk synlig rabattpris på Kvadratfoto etter JS (2 100 eller 2 993). Ikke testet i nettleser.
3. Hva dronefoto-bolig inkluderer av antall bilder, flytid og bruksrett (Eiendomsfotografen).
4. Bruksrett og leveringstid hos Premani; leveringstid hos Oslo Drone og Foto.
5. Konkrete forsikringsbevis eller operatørregistreringsnummer hos noen.
6. Veiledning spesifikt om hero-video og CLS/LCP (bare bildebaserte råd).
7. Verifisert hovedfarge og mobilmeny for firmafotografen.no.
8. Meglerpriser eller rabattavtaler hos Kvadratfoto.
