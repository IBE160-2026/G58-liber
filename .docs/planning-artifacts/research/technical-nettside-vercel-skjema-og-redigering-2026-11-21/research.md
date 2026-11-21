---
title: 'Teknisk research: hosting, skjema og redigering for Dimmen Dronefoto'
type: 'technical'
topic: 'nettside vercel skjema og redigering'
decision: 'Raskeste trygge tekniske løsning for en liten dronefoto-nettside før 2026-12-15'
source: 'native run (WebFetch, WebSearch), en hovedrunde og en verifiseringsrunde'
status: complete
preset: 'standard'
validation: 'normal'
created: '2026-11-21'
updated: '2026-11-21'
claims_verified: 7
claims_unverified: 2
claims_overturned: 0
---

# Teknisk research: hosting, skjema og redigering

Alle kilder er lest 2026-11-21 via et hentingsverktøy som gjengir sidene (ikke rå HTML), så ordrette sitater er ikke dobbeltsjekket mot originalen. Priser og vilkår endres ofte; «ikke oppgitt» betyr at siden ikke sier selv når den er publisert. Vilkårslesning er ikke juridisk rådgivning.

**Beslutningen forskningen støtter:** hvilken tekniske løsning for hosting, domene, kontaktskjema, innholdsredigering og bilder er raskest å få trygt på plass før 15. desember 2026.

## 1. Sammendrag

**Anbefaling:** bygg siden som ren statisk HTML/CSS/JS som kan hostes hvor som helst, og avgjør produksjonsverten før lansering. Det som er uavklart er hosting, ikke koden.

1. **Vercel Hobby er etter vilkårene bare for «personal or non-commercial use».** Vercel sier ordrett: «You shall only use the Services under a Hobby plan for your personal or non-commercial use» [1]. Vercel definerer ikke «kommersiell», men en bedriftsside som markedsfører en betalt tjeneste er trolig kommersiell. Pro koster 20 USD per bruker per måned [2]. Dette utfordrer antakelsen «Vercel som utgangspunkt» for den ferdige siden. *Tillit: høy for ordlyden, middels for tolkningen.*
2. **Gratis alternativer med kommersiell bruk er uavklart eller begrenset:** Cloudflare Pages har ingen funnet forbudsklausul, men heller ingen eksplisitt tillatelse [4][5]; Netlify er uklart [6]; GitHub Pages forbyr gratis drift av «online business» [7]. *Tillit: middels.*
3. **Enkleste redigeringsløsning er en JSON-fil redigert i GitHubs nettleser-editor.** Decap CMS krever en OAuth-tjener på Vercel eller Cloudflare og skrivetilgang til repoet for alle redaktører [8][9]. Pages CMS er hostet og «100 % free», men at det virker på en ren HTML-side er ikke belagt [10][11]. *Tillit: høy for Decap, lav-middels for Pages CMS.*
4. **Kontaktskjema:** en ekstern tjeneste (Formspree Free: 50 innsendinger per måned [12]) er raskest. En liten funksjon pluss e-posttjenesten Resend (gratis 3 000 e-poster per måned og 100 per dag [13]) gir mer kontroll men krever kode og API-nøkkel. Ingen av dem har belagt EU/EØS-lagring. *Tillit: middels.*
5. **Domene:** `.no` kan holdes av en privatperson fra 18 år med norsk fødselsnummer og norsk adresse, eller av en organisasjon med organisasjonsnummer [14]. Domeneshop oppgir 99 kr per år [15]. *Tillit: høy for reglene, middels for prisen (én registrar).*

**Største forbehold:** Vercel- og Cloudflare-vilkårene er lest i utdrag via et verktøy. Før lansering bør de leses i fulltekst, eller støtte spørres direkte.

## 2. Hosting og kommersiell bruk

| Tjeneste | Gratis for kommersiell bruk? | Grenser | Merknad | Kilde |
|---|---|---|---|---|
| Vercel Hobby | **Nei, ifølge vilkårene** («personal or non-commercial use»). Vercel gir Hobby «at our sole discretion». | 100 GB trafikk og 1 000 000 CDN-forespørsler per måned | Pro 20 USD/bruker/måned. Fair use-siden gir bare bruksgrenser; eksempelavsnittene kom tomme. | [1][2][3] |
| Cloudflare Pages Free | **Uklart, ingen forbud funnet** | 20 000 filer, 500 builds/måned; ingen båndbreddegrense nevnt | Fravær av forbud er ikke tillatelse. Pkt. 2.2.1(h) forbyr å samle betalingskortinformasjon på sider med gratistjeneste. | [4][5] |
| Netlify Free | **Uklart** | 300 kreditter; båndbredde 20 kreditter per GB (ca. 15 GB) | Kommersiell bruk er ikke omtalt i vilkårene som er lest; Self-Serve-avtalen er ikke lest. | [6] |
| GitHub Pages | **Nei for «online business»** | 1 GB side, myk grense 100 GB/måned | En ren informasjonsside uten salg er en gråsone. | [7] |

**Hva dette betyr for prosjektet**
- Selve leveransen til IBE160 er en skole-oppgave og trenger ikke betalt hosting. Men Andreas skal bruke siden kommersielt, og da er Vercel Hobby uegnet etter ordlyden.
- Hold siden vertsuavhengig: ren statisk HTML/CSS/JS uten Vercel-spesifikke funksjoner. Da kan den flyttes uten omarbeiding.
- Avgjør produksjonsverten før lansering: Vercel Pro (20 USD/mnd), eller Cloudflare Pages dersom full lesing av vilkårene eller en henvendelse til Cloudflare bekrefter at kommersiell bruk er tillatt.

## 3. Domene

- **Hvem kan eie `.no`:** norske organisasjoner med organisasjonsnummer, og privatpersoner fra 18 år med norsk fødselsnummer eller d-nummer, begge med postadresse i Norge. Bestilling skjer via en registrar, ikke direkte hos Norid [14]. *Tillit: høy (primærkilde, men siden er oppdatert 2021-09-15).*
- **Pris:** Domeneshop oppgir 99 kr per år inkl. 25 % mva, og viser en kampanje til 30 kr datert 2026-09-14 [15]. Bare én registrar er lest. *Tillit: middels.*
- **Eier:** hvem som står som innehaver har betydning for kontroll og fremtidig foretak. Anbefaling: Andreas som innehaver og ML som teknisk kontakt, siden domenet er firmaets. Dette er en slutning, ikke en kildebelagt påstand, og eier er allerede et åpent spørsmål (issue #3).
- **DNS og SSL:** Cloudflare Pages krever at apex-domene (`dimmendronefoto.no`) ligger som Cloudflare-sone, altså nameservere hos Cloudflare, mens `www` kan peke med CNAME [5][16]. Vercels DNS-oppsett er ikke lest.

## 4. Kontaktskjema

| Alternativ | Gratis | Spamvern | Arbeid | Forbehold | Kilde |
|---|---|---|---|---|---|
| Formspree Free | 50 innsendinger/måned | Formshield og egen reCAPTCHA-nøkkel på alle planer; egen honeypot kun på Business | lavt | Free beskrives «for testing and development»; EU-lagring ikke omtalt | [12] |
| Web3Forms Free | 250/måned (kun sekundære kilder) | ikke lest | lavt | primærsiden ga 403 | – |
| Netlify Forms | gratisgrense ikke funnet | – | lavt | krever Netlify-deploy | [6][17] |
| Cloudflare Pages Function + Resend | Resend 3 000 e-poster/måned, 100/dag | Turnstile (gratis, ubegrenset) | middels | kode, API-nøkkel og verifisert avsenderdomene; EU-region ikke navngitt | [13][18][19] |

- **Anbefaling:** for 3 uker og en student som utvikler, er Formspree (eller tilsvarende) raskest. Hold avsender og mottaker generisk så tjenesten kan byttes. Gratisgrensen på 50 innsendinger er sannsynligvis nok for en ny aktør, men bør sjekkes mot vilkårene før lansering.
- **Spamvern uten cookies:** reCAPTCHA setter cookies og laster tredjepartsskript, og kan derfor utløse samtykkekrav (slutning, ikke belagt). Turnstile er et alternativ, men cookiebruken er ikke undersøkt. Honeypot-felt og tidsjekk i JS er billige og uten tredjepart.
- **Personvern:** ingen kilde belegger EU/EØS-lagring hos Formspree, Web3Forms eller Resend. Hvis skjemaet samler navn, e-post og adresse, må tjenesten kunne dokumenteres som databehandler før lansering.
- **Test ved lansering:** konkurrentene hadde defekte skjema (se konkurranseanalysen). Test hele flyten Gmail → mottak, inkludert spam-mappen.

## 5. Innholdsredigering for to redaktører

| Alternativ | Oppsett | Innlogging for eier | Forbehold | Kilde |
|---|---|---|---|---|
| **JSON/Markdown i repoet + GitHubs nettleser-editor** | ingen | GitHub-konto med skrivetilgang | GitHub anbefaler ny branch + pull request på standardbranch; beskyttet branch kan ikke redigeres i nettleseren | [20] |
| **Decap CMS** | `admin/index.html` + `config.yml`, laster skript fra CDN, ingen bygg | GitHub-konto med push-tilgang **og** OAuth-tjener (Netlify, Decap Turbo eller egen) | fungerer ikke på Vercel uten ekstra OAuth-oppsett; ren HTML uten generator er ikke eksplisitt eksemplifisert | [8][9] |
| **Pages CMS** | `.pages.yml` i repoet; hostet app | e-postinvitasjon («collaborators») uten GitHub-konto, ifølge docs | om invitasjon virker i hostet app og om ren HTML støttes, er ikke bekreftet; GitHub App-tilganger kun fra søkeutdrag | [10][11] |

- **Anbefaling v1:** innholdet ligger i én `content.json` (tekst, priser, bildelister). ML redigerer; Andreas kan redigere via GitHubs nettleser hvis han får en GitHub-konto med skrivetilgang. Dette dekker brief-beslutningen («ML gjør endringer i første versjon, løsning avtales senere») uten ekstra infrastruktur.
- **Test etterpå:** Pages CMS som mulig enkel løsning for Andreas. En kort test (en times arbeid) bør avgjøre om det virker på siden uten generator og om invitasjon uten GitHub-konto fungerer.
- **Arkitekturvalg som følger:** innhold i JSON betyr at HTML må enten hente JSON med JavaScript (påvirker første innlasting og søkemotorer) eller bygges ved deploy med et lite skript. Dette er en slutning fra funnene og ikke belagt i kildene; det er et åpent arkitekturspørsmål.
- Ikke undersøkt: TinaCMS, CloudCannon, Sanity, Contentful, Storyblok.

## 6. Bilder, ytelse og lightbox

- **Vercel Image Optimization på Hobby:** 5 000 transformasjoner, 300 000 cache-reads og 100 000 cache-writes per måned; over grensen feiler nye bilder med 402, mens cachede fortsetter [21]. Kildebilde maks 8192 px bredde/høyde og transformert bilde maks 10 MB [21]. Om funksjonen virker på ren HTML uten Next.js er ikke bekreftet.
- **Anbefaling:** forhåndsgenerer størrelser og formater (WebP, eventuelt AVIF) og skaler ned 48 MP-originaler **før** opplasting. Verktøy: sharp (`resize({ width })`, `withoutEnlargement`), siste utgivelse v0.35.5 (27.09.2026) [22]. Squoosh er ikke undersøkt. Anbefalte størrelser og kvalitetsverdier er ikke belagt.
- **Responsive bilder:** `srcset` og `sizes` på `<img>`, eller `<picture>` for formatfallback [23].
- **LCP og CLS:** hero-bildet skal ligge i HTML med `fetchpriority="high"` og **ikke** `loading="lazy"`; alle `<img>` får `width` og `height` [24]. God LCP er ≤ 2,5 s og god CLS ≤ 0,1 (se konkurranseanalysen).
- **Lightbox uten bibliotek:** native `<dialog>` med `showModal()` gjør resten av siden inert, lukker med Esc og kan stiles med `::backdrop`; Baseline «widely available» siden mars 2022 [25]. Sidens eksempel er ca. 10 linjer JS.
- **Animasjon:** `prefers-reduced-motion`, IntersectionObserver og `transform`/`opacity` er dekket i konkurranseanalysen.

## 7. Lokal SEO

- Google krever bare `name` og `address` for LocalBusiness-markup; `geo`, `telephone`, `url`, `openingHoursSpecification` og `priceRange` er anbefalt [26]. Om «ProfessionalService» er riktig undertype og hvordan `areaServed` markeres, er ikke belagt.
- Unike, korte titler og meta descriptions per side, og alt-tekst på bilder. Sitemap er **ikke** påkrevd [27].
- **Google Business Profile (kun søkeutdrag):** virksomheter uten publikumsadresse kan registreres som tjenesteområde-virksomhet (opptil 20 områder) med skjult adresse, og verifisering skjer ofte via videoopptak [28]. *Tillit: lav.*
- **Personvernkonflikt:** LocalBusiness-markup krever adresse, men Andreas har ikke registrert firma ennå og kan ikke ønske å vise privatadressen. Uavklart. Til Andreas har foretak og adresse kan markup utelates.

## 8. Anbefalinger

| # | Anbefaling | Støtte |
|---|---|---|
| 1 | **Bygg siden vertsuavhengig** (ren statisk HTML/CSS/JS). Avgjør produksjonsvert før lansering: Vercel Pro, eller Cloudflare Pages etter at vilkårene er lest i fulltekst eller bekreftet. | [1][2][4][5] |
| 2 | **Bruk Formspree (eller tilsvarende) til kontaktskjema** i v1, med honeypot og tidsjekk i stedet for reCAPTCHA. Dokumenter databehandler og EU-lagring før lansering. | [12][13] |
| 3 | **Legg innholdet i én `content.json`** i v1. Test Pages CMS senere (en time) før avtale med Andreas om redigering. | [10][11][20] |
| 4 | **Registrer `dimmendronefoto.no` hos Domeneshop** (99 kr/år) med Andreas som innehaver når han kan stå som det. | [14][15] |
| 5 | **Forhåndsgenerer bildestørrelser med sharp** (WebP, srcset) og skaler ned 48 MP-bilder før opplasting. Hero med `fetchpriority="high"`, ingen lazy. | [21][22][24] |
| 6 | **Bruk native `<dialog>` til lightbox** (ingen biblioteker). | [25] |
| 7 | **Hopp over LocalBusiness-markup** inntil Andreas har foretak og adresse; skriv unike titler og alt-tekst. | [26][27] |

## 9. Åpne spørsmål

- Tillater Cloudflare Pages og Netlify kommersiell bruk på gratisplan (fulltekst av vilkårene)?
- Hvor lagrer Formspree, Web3Forms og Resend data (EU/EØS), og tilbyr de databehandleravtale?
- Fungerer Pages CMS på en ren HTML-side, og kan Andreas logge inn uten GitHub-konto?
- Skal innhold i JSON hentes med JavaScript eller bygges til HTML ved deploy?
- Hva er den daglige gratisgrensen for Cloudflare Pages Functions?

## 10. Kilder

Alle hentet 2026-11-21.

| # | Kilde | Utgiver | Dato | Tillit |
|---|---|---|---|---|
| 1 | https://vercel.com/legal/terms | Vercel | oppdatert 2026-10-19 | høy |
| 2 | https://vercel.com/docs/plans/hobby (pris: https://vercel.com/pricing) | Vercel | 2026-11-12 | høy |
| 3 | https://vercel.com/docs/limits/fair-use-guidelines | Vercel | 2026-11-12 | middels |
| 4 | https://www.cloudflare.com/terms/ og https://www.cloudflare.com/service-specific-terms-developer-platform/ | Cloudflare | 2026-09-28 (vilkår for utviklerplattform) | middels |
| 5 | https://developers.cloudflare.com/pages/platform/limits/ og https://developers.cloudflare.com/pages/configuration/custom-domains/ | Cloudflare | 2026-11-19 / 2026-11-11 | middels |
| 6 | https://www.netlify.com/pricing/ og https://www.netlify.com/legal/terms-of-use/ | Netlify | 2026-10-14 (vilkår) | lav–middels |
| 7 | https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits | GitHub | ikke oppgitt | høy (sitat) |
| 8 | https://decapcms.org/docs/install-decap-cms/ | Decap CMS | ikke oppgitt | høy |
| 9 | https://decapcms.org/docs/github-backend/ | Decap CMS | ikke oppgitt | høy |
| 10 | https://pagescms.org/ og https://github.com/pagescms/pagescms | Pages CMS | ikke oppgitt | middels |
| 11 | https://pagescms.org/docs/configuration/collaborators/ | Pages CMS | ikke oppgitt | høy (sitat) |
| 12 | https://formspree.io/plans | Formspree | ikke oppgitt | middels |
| 13 | https://resend.com/pricing | Resend | ikke oppgitt | middels |
| 14 | https://www.norid.no/en/nytt-domenenavn/hvem-kan-ha-domene/ | Norid | oppdatert 2021-09-15 | høy |
| 15 | https://domene.shop/ | Domeneshop | nyhet 2026-09-14 | middels |
| 16 | https://developers.cloudflare.com/pages/configuration/custom-domains/ | Cloudflare | 2026-11-11 | middels |
| 17 | https://docs.netlify.com/manage/forms/setup/ | Netlify | ikke oppgitt | middels |
| 18 | https://developers.cloudflare.com/pages/functions/pricing/ | Cloudflare | 2026-09-08 | middels |
| 19 | https://developers.cloudflare.com/turnstile/plans | Cloudflare | 2026-08-14 | høy |
| 20 | https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files | GitHub | ikke oppgitt | middels |
| 21 | https://vercel.com/docs/image-optimization/limits-and-pricing | Vercel | 2026-11-12 | høy |
| 22 | https://sharp.pixelplumbing.com/api-resize | sharp | 2026-09-27 (versjon) | middels |
| 23 | https://web.dev/learn/images/responsive-images | Google (web.dev) | ikke oppgitt | middels |
| 24 | https://web.dev/articles/browser-level-image-lazy-loading | Google (web.dev) | ikke oppgitt | høy |
| 25 | https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog | MDN | 2026-11-10 | høy |
| 26 | https://developers.google.com/search/docs/appearance/structured-data/local-business | Google Search Central | ikke oppgitt | høy |
| 27 | https://developers.google.com/search/docs/fundamentals/seo-starter-guide | Google Search Central | ikke oppgitt | høy |
| 28 | https://support.google.com/business/answer/9157481 (kun søkeutdrag) | Google Business Profile Help | ikke oppgitt | lav |

## 11. Metode og forbehold

Fire digester ligger i `digests/` (to i første runde, en verifiseringsrunde). Kildene er hentet via et verktøy som gjengir sidene, ikke rå HTML. Priser og vilkår kan ha endret seg siden hentedatoen. Web3Forms ble ikke lest (403), så tallene for den er utelatt fra anbefalingene. Alt som er kun søkeutdrag er merket.
