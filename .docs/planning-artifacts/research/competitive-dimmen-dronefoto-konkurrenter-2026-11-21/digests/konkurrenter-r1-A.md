# Digest r1-A: Oslo Drone og Foto, Follo Dronefoto

Hentet 2026-11-21. Kilder er nettstedenes egne sider (primærkilder, utgiver = eier av nettstedet). Publiseringsdato «ikke oppgitt» med mindre noe annet står. WebFetch gir en LLM-oppsummering, så skjemafelt og tekster er sekundærlest. Teknologi og farger er lest direkte fra rå HTML/CSS med curl (høyere tillit).

## 1. Oslo Drone og Foto (oslodroneogfoto.no)
Ikke oppgitt noe sted: org.nr, forsikring, operatørregistrering, A1/A3, erfaring i år, utstyr, leveringstid, bruksrett. Personnavn: bare «Anders» ved kontaktskjemaet.

**Tilbud** (/, /tjenester/*, /om)
- tilbud, høy: dronefoto og film, boligfoto, digital visning (Matterport), bedriftsfoto og video, 2D-plantegning, digital visualisering (/ai-visualisering).
- tilbud, middels: boligfoto = «25 ferdig redigerte bilder»; dronefoto = «5–10 bilder fra ulike vinkler»; dronevideo = «kort, ferdig redigert dronefilm»; Matterport «inntil 100 m²»; plantegning «2D, én etasje» (https://oslodroneogfoto.no/#priser).
- tilbud, middels: dekker Oslo og hele Østlandet; kundetyper: eiendomsmeglere, utviklere, arkitekter, hoteller, etablerte virksomheter.

**Pris** (https://oslodroneogfoto.no/#priser; alle «fra», veiledende, åpent oppgitt; inkl./eks. mva)
- pris, middels: boligfoto fra 5 000 / 4 000 kr; dronefoto fra 5 000 / 4 000 kr; dronevideo fra 6 000 / 4 800 kr; digital visning fra 5 000 / 4 000 kr; plantegning fra 3 500 / 2 800 kr.
- pris, middels: ingen faste pakkepriser; pris «avhenger av størrelse, lokasjon og ønsket leveranse», pakker gir ofte bedre totalpris. Reise, tillegg, avbestilling: ikke oppgitt.

**Tillit**
- tillit, middels (selvpublisert, ikke verifisert): Google 5,0 (antall anmeldelser ikke vist); kundelogoer: Røisland & Co, Scandic, OBOS, Bonava, Nordvik, Sem & Johnsen, Arcasa, Scandinavian Property Group; tre navngitte sitater (megler, 3D-studio, prosjektutvikler); tre prosjektsider (Henie Onstad, Premani, Construction City).

**Kontaktflyt** (/kontakt, /)
- kontaktflyt, middels: skjema med Navn*, E-post*, Telefon (valgfri), «Hva gjelder det?» (nedtrekk med «Hjelp meg å velge»: Boligfoto, Dronefoto, Dronevideo, Digital visning, Plantegning, Bedriftsfoto og video, Digital visualisering, Pakke med flere tjenester, Noe annet), «Hva kan vi hjelpe med?»* (fritekst), skjult honeypot. Knapp «Send melding →».
- kontaktflyt, middels: CTA-er: «Kontakt oss ↗» (meny), «Kontakt oss →», «Se porteføljen →», «Ring 45 85 05 88», «Utforsk tjenesten →». Forhåndsvalgte skjemalenker: /kontakt?service=…. Løfte: «normalt svar i løpet av noen timer», uforpliktende. Telefon og e-post oppgitt, ingen gateadresse.

**Struktur og design**
- design, middels: meny: Tjenester (#anker, undermeny), Priser (#anker), Portefølje, Om oss, Kontakt oss; mobil: «Meny»-knapp. Enkeltside-ankre #tjenester #priser #anmeldelser #arbeid #prosess. Portefølje delt i 5 seksjoner: 01 Drone, 02 Bolig, 03 Næring og film, 04 3D-visning, 05 Plantegning, ca. 14 bilder totalt.
- design, høy (HTML via curl): egen kode, Next.js (19 treff på «_next»), ikke WordPress/Wix.
- design, høy (HTML): hero er bilde («Drone · Foto · Film · 3D», «Hele historien. Fra bakken og opp.»). <video>-tagger (muted, loop, preload="none", poster-bilde) i seksjonen «Film i bevegelse» med klasser «lazyVideo» og «filmShade». Motsier WebFetch-oppsummeringen («ingen video»); curl-HTML veier tyngst.
- design, høy (CSS, https://oslodroneogfoto.no/_next/static/css/index.EUa4TiEP.css): mørkeblå #0a2740 / #10263d / #071f34, lyse flater #f7faf9, aksent blågrønn #bcd9dd / #9fc4ca. Fonter: Georgia (serif, overskrifter) og Inter (brødtekst). Animasjon: @keyframes grain, heroDrift, marquee; klassen «reveal» (scroll-inn); backdrop-filter brukt 40 ganger; smooth scroll.
- design, lav: Matterport lastes først når bruker åpner den. Lightbox/filtrering ikke observert.
- design, lav (assistentens vurdering): proft og ryddig, ro og tydelig prisseksjon. Teknisk avansert (grain, drift, marquee), kan nærme seg overdrevet. Svakhet: tillitsinformasjon som droneoperatører bør vise (forsikring, registrering, org.nr) mangler.

## 2. Follo Dronefoto (follodronefoto.no; Trond Larsen, Vestby)
Ikke oppgitt: leveringstid, betalingsvilkår, forsikring, operatørnummer, A1/A3, org.nr, kundelogoer/referanser/anmeldelser, erfaring i år, utstyr, åpningstider.

**Tilbud** (https://www.follodronefoto.no/)
- tilbud, middels: dronefoto til næringsbygg, eiendom, gårdsbruk, anlegg, byggeprosjekter, landskap, kulturminner; panorama; dronefilm (korte klipp, ferdig redigerte filmer, lengre dokumentasjonsfilmer), normalt 4K, slow motion etter avtale; stillbilder som tillegg; annen fotografering; forhåndsgjennomgang av sted og flyplan.
- tilbud, middels (https://www.follodronefoto.no/tjenester/prisliste/): bruksrett: «Prisene inkluderer normalt bruksrett for kundens egen markedsføring»; videreformidling, videresalg, større kampanjer eller større eksterne produksjoner «avtales særskilt».

**Pris** (/tjenester/prisliste/; åpen prisliste, alle eks. mva)
- pris, middels: Dronefoto Mini 4 500 kr; Standard 6 500 kr; Pluss 8 900 kr (innhold per pakke ikke hentet); dronepanorama fra 1 500; høyoppløselig panorama fra 4 500; storformat/trykk etter avtale.
- pris, middels: dronevideo Enkel fra 4 900; kort ferdig dronefilm fra 8 900; dokumentasjons-/presentasjonsfilm fra 12 500; tillegg: 4K 60 fps fra 1 500, slow motion fra 2 500, avansert fargeprofil fra 2 500.
- pris, middels: stillbilder 5 stk 1 500 kr, 10–15 stk 2 500 kr; råfiler foto fra 1 500, video fra 2 500; ekstra redigering 1 100 kr/time; ekstra lokasjon fra 1 500; kjøring 8 kr/km; hastelevering +30 %; «Kjøring utenfor nærområde avtales på forhånd».

**Tillit**
- tillit, middels (påstand uten bevis): «Vi er registrert droneoperatør og flyr etter gjeldende regelverk for droneflyging» (ingen nummer); beskriver flyplan og forhåndssjekk av hindringer, flyplasser, skoler.
- tillit, middels: om-siden: tjeneste fra et foretak i Vestby; adresse oppgitt; footer «© Copyright 2018».

**Kontaktflyt** (/, /kontakt/)
- kontaktflyt, middels: CTA «Se prisliste», «Send forespørsel», «Uforpliktende forespørsel»; kontaktsiden har lenken «Fyll ut skjema og send inn!» (href #, skjemaet ikke synlig i hentet innhold, felt ukjent); telefon og e-post oppgitt; «Kontakt er alltid uforpliktende!»; Facebook, YouTube, Instagram.

**Struktur og design**
- design, høy: meny START, TJENESTER (undermeny Prisliste), OM, Steder, BILDER og Sånt, GALLERI, KONTAKT; søkeikon; cookie-banner «Greit»; blogglignende innlegg (nyeste 28.07.2026).
- design, høy (HTML via curl): WordPress med Avada-tema, LayerSlider, fusion-flexslider, fusion-mobile-menu (mobilmeny finnes), «fusion-animated»; lightbox = iLightbox.
- design, høy (HTML): hero bilde/slider med «Vakre Son fra luften» og lenke «Se alle bildene!»; <video controls muted> med mp4 i innhold, ikke autoplay-hero. Farger: standard WP-paletter og Avada-variabler (#f9f9f9, #2f576f); fonter: Arial-fallback synlig.
- design, lav (assistentens vurdering): hobby-/lokalpreg, blogg-struktur, få tillitselementer, men svært tydelig åpen prisliste og bruksrettsvilkår.

## Leads
- follodronefoto.no/steder/ og /galleri/ (ikke lest); oslodroneogfoto.no/tjenester/boligfoto og /prosjekter/henie-onstad (ikke lest).
- Pakkeinnhold for Dronefoto Mini/Standard/Pluss hos Follo (antall bilder, redigering) ikke hentet.

## Lette etter, fant ikke
- Begge: org.nr, forsikring, A1/A3 med nummer, erfaring i år, leveringstid, bruksrett (Oslo), betalingsvilkår.
- Oslo: lightbox/filtrering, prosjektbasert prisutregning, avbestilling.
- Follo: skjemafelt, kundelogoer/anmeldelser, fontnavn, hex-paletten utover Avada-standard.
- «Google 5,0» på Oslo-siden er selvrapportert uten antall, ikke verifisert mot Google.
