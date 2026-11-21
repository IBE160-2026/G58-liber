# Teknisk research R1-B: innholdsredigering, bilder og lokal SEO (digest)

Hentet=2026-11-21 for alle påstander. Format: påstand | kilde | utgiver | dato | tillit | klasse. «Lest» = innholdet er hentet og lest i dag (WebFetch gir et sammendrag fra en liten modell, ikke rå HTML; derfor settes tillit til middels der ordlyden ikke er sitert). Kilder lest: 9 (Decap intro, Decap GitHub-backend, Pages CMS intro, Vercel bildegrenser, Vercel fair use, web.dev responsive, web.dev lazy loading, Google LocalBusiness, Google SEO-guide, MDN dialog, sharp resize, GitHub-docs editering). Kilde 13 er et søk (sammendrag), ikke en lest side.

## 1. Innholdsredigering

1. Decap CMS er git-basert og «platform agnostic», innhold lagres i Git-repoet sammen med koden. Oppsett beskrives som «legg til to filer på siden» og velg backend (GitHub, GitLab, Bitbucket, Gitea m.fl.). | https://decapcms.org/docs/intro/ | Decap CMS | ikke oppgitt (footer ©2026; Netlify CMS ble Decap i feb. 2023) | middels | teknisk
2. Intro-siden nevner ikke config.yml, admin-mappe eller rene HTML-sider uten generator; guider finnes for Gatsby, Hugo, Jekyll, Next.js, Nuxt. At Decap fungerer på ren HTML er derfor IKKE bekreftet her (ubekreftet antakelse: to filer, `admin/index.html` + `config.yml`, virker uten bygg, må testes). | samme | Decap CMS | ikke oppgitt | middels | teknisk
3. GitHub-backend krever en server for autentisering. Netlify tilbyr enkel GitHub-auth; alternativt hostet auth via «Decap Turbo» (pris ikke undersøkt). Å bruke det på Vercel krever dermed enten egen OAuth-proxy/OAuth-app eller Decap Turbo. | https://decapcms.org/docs/github-backend/ | Decap CMS | ikke oppgitt | middels | teknisk
4. Alle Decap-brukere «må ha push access» til innholdsrepoet (krever altså GitHub-konto og skrivetilgang for begge redaktører). Konfig: `backend: name: github, repo: eier/repo, branch`. Git LFS støttes ikke av GitHub-backend. | samme | Decap CMS | ikke oppgitt | høy | vilkår
5. Pages CMS: åpen kildekode, redigerer filer direkte i GitHub-repoet uten egen innholdsdatabase; oppsett = legg til `.pages.yml` (content, media, valgfritt components/settings) og logg inn. Erstatter ikke deploy-plattformen. Siden dekker ikke pris, hosted vs. selv-hostet eller hvem som kan logge inn (installasjonsside ga 404; selv-hosting-side 404). | https://pagescms.org/docs/ | Pages CMS | ikke oppgitt | middels | teknisk
6. Ikke undersøkt (ikke belagt): TinaCMS, CloudCannon, Sanity, Contentful, Storyblok, gratisnivåer og priser. Ingen påstander gjøres om dem.
7. GitHubs nettleser-editor: i eget repo redigeres filen direkte og commit-skjemaet lar deg velge gjeldende branch eller ny branch. På standardbranch anbefaler GitHub ny branch + pull request. Er branchen beskyttet, kan man ikke redigere/laste opp via GitHub-nettsiden. I andres repo forkes det automatisk. Docs-siden sier ingenting om opplasting eller filstørrelsesgrense. | https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files | GitHub | ikke oppgitt | middels | teknisk

**Vurdering (min, begrunnet av 3-4 og 7):** Minst arbeid for to redaktører = innhold i én JSON-fil (eller data i HTML) redigert via GitHubs nettleser-editor; ingen OAuth-server, ingen bygg. Krever at eieren har GitHub-konto med skrivetilgang. Decap på Vercel krever ekstra autentiseringsoppsett (punkt 3); Pages CMS er et kandidat-alternativ med `.pages.yml`, men oppsett og tilgangsmodell er ikke verifisert.

## 2. Bilder

8. Vercel Image Optimization, Hobby inkludert: 5 000 transformasjoner, 300 000 cache-reads, 100 000 cache-writes per måned. Gratis innen grensene. | https://vercel.com/docs/image-optimization/limits-and-pricing | Vercel | last_updated 2026-11-12 | høy | pris
9. Over grensen på Hobby: nye bilder feiler med 402-feil (alt-tekst vises); allerede cachede bilder fortsetter å virke; ingen belastning. | samme | Vercel | 2026-11-12 | høy | vilkår
10. Tekniske grenser: transformert bilde maks 10 MB; kildebilde maks 8192 px bredde/høyde; kun jpeg/png/webp/avif optimaliseres, andre formater serveres uendret. En 48 MP-original (typisk ca. 8000x6000 eller større; ukontrollert) kan altså ligge på/over grensen og bør nedskaleres FØR opplasting. | samme | Vercel | 2026-11-12 | høy | teknisk
11. Fair use-tabell for Hobby: Fast Data Transfer første 100 GB, samme bildetall som over. Siden viser at Hobby-grenser finnes; om Hobby er begrenset til ikke-kommersiell bruk er IKKE verifisert (sidens «examples of fair use» kom ikke med). | https://vercel.com/docs/limits/fair-use-guidelines | Vercel | last_updated 2026-11-12 | middels | vilkår
12. Ikke bekreftet: at Vercels bildeoptimalisering fungerer for ren statisk HTML uten Next.js (dokumentasjonen jeg leste viser Next-eksempler). Enklere og uavhengig: forhåndsgenerer størrelser og WebP/AVIF selv.
13. sharp (Node): `sharp(input).resize({ width: 100 })` skalerer med auto-høyde; `withoutEnlargement` (standard false) hindrer oppskalering; `fit` standard cover. Siste utgivelse på changelog-menyen: v0.35.5 (27. sept. 2026). | https://sharp.pixelplumbing.com/api-resize | sharp (Lovell Fuller m.fl.) | 2026-09-27 (versjonsdato) | middels | versjon
14. srcset gir nettleseren kandidatkilder for ett `<img>`; `sizes` forteller hvordan bildet vises, så nettleseren velger mest effektive; `<picture>` gir eksplisitt kontroll (art direction, formatstøtte-fallback). Eksempelkode, bredde-deskriptorer og anbefalte størrelser stod ikke i utdraget. | https://web.dev/learn/images/responsive-images | Google (web.dev) | ikke oppgitt | middels | teknisk
15. Lazy loading: bruk ikke `loading="lazy"` på bilder som sannsynligvis er i viewport ved lasting, særlig LCP-bildet; sett `width` og `height` på alle `<img>` for å unngå layoutskift (CLS); `fetchpriority="high"` for viktig LCP-bilde. Støtte: Chrome 77, Edge 79, Firefox 75, Safari 15.4. | https://web.dev/articles/browser-level-image-lazy-loading | Google (web.dev) | ikke oppgitt | høy | teknisk
16. Lightbox uten avhengighet: native `<dialog>`; `showModal()` gjør resten av siden inert, lukker på Esc som standard, `::backdrop` kan stiles, fokus settes på første fokuserbare element (bruk `autofocus` på lukkeknapp), og `closedby="any"` gir klikk-utenfor-lukking. Baseline «widely available» siden mars 2022. Eksempel på ca. 10 linjer JS finnes. | https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog | MDN | sist endret 2026-11-10 | høy | teknisk
17. Squoosh: ikke undersøkt (ingen kilde lest). AVIF vs. WebP-størrelsesforskjeller, anbefalte pikselbredder og kvalitetsverdier: ikke belagt.

## 3. Lokal SEO

18. Google LocalBusiness-strukturerte data: påkrevd `name` og `address` (PostalAddress, så mange felt som mulig). Anbefalt: `geo` (min. 5 desimaler), `openingHoursSpecification`, `telephone` (med landskode), `url`, `priceRange`. Bruk mest spesifikke undertype; flere typer som array (`additionalType` støttes ikke). LocalBusiness er underklasse av Organization. | https://developers.google.com/search/docs/appearance/structured-data/local-business | Google Search Central | ikke oppgitt | høy | teknisk
19. Om «ProfessionalService» er riktig undertype og hvordan et tjenesteområde (areaServed) markeres: ikke belagt (schema.org ikke lest).
20. Google SEO-guide: unike, klare og korte titler per side; meta description kort og unik (Google bruker ofte sidetekst i stedet); sitemap er IKKE påkrevd; alt-tekst er viktig for bilder; strukturert data gir kvalifisering til spesialresultater. Guiden dekker ikke Business Profile. | https://developers.google.com/search/docs/fundamentals/seo-starter-guide | Google Search Central | ikke oppgitt | høy | teknisk
21. Google Business Profile (kun fra søkesammendrag, side ikke åpnet): virksomhet uten publikumsadresse bør registreres som tjenesteområde-virksomhet (opptil 20 områder, ca. 2 timers kjøretid fra base) og adressen skjules; verifisering skjer ofte via videoopptak (min. 30 s, uredigert, fra mobil, viser sted, utstyr og drift); metoden velges av Google; rent nettbaserte virksomheter er ikke kvalifisert. | https://support.google.com/business/answer/9157481 og https://support.google.com/business/answer/14271705 | Google Business Profile Help | ikke oppgitt | lav (kun søkeutdrag) | vilkår

## Leads
- Decap på Vercel: leter etter «decap-cms-oauth-provider» / Decap Turbo-priser og vilkår (https://decapcms.org/turbo/ og Decaps «external OAuth clients»-side).
- Pages CMS: https://pagescms.org/docs/ (undersider: Configuration, Media, Collaborators, GitHub App) og om hosted instans finnes og er gratis.
- Vercel Hobby og kommersiell bruk: https://vercel.com/docs/plans/hobby og https://vercel.com/legal/terms#fair-use.
- Vercel Image Optimization for statiske sider (`/_vercel/image`): https://vercel.com/docs/image-optimization.
- web.dev «learn/images» sider om srcset/sizes, formater (AVIF/WebP) og kompresjon; https://squoosh.app / GoogleChromeLabs/squoosh.
- schema.org/ProfessionalService og areaServed; Google Help-sider for GBP direkte (9157481, 14271705, 3038177).

## Lette etter, fant ikke
- Dokumentasjon som eksplisitt bekrefter Decap CMS på ren HTML/JS-side uten generator.
- Gratisnivå/oppsettkrav for TinaCMS, CloudCannon, Sanity, Contentful, Storyblok.
- Anbefalte bildestørrelser/kvalitetsinnstillinger, Squoosh-dokumentasjon, AVIF vs. WebP-sammenligning.
- GitHub-docs om filstørrelsesgrense for opplasting i nettleser.
- Om Vercel Hobby tillater kommersiell bruk (ordlyd ikke hentet).
- Norsk-spesifikk lokal SEO-kilde (f.eks. Brønnøysund, Gule Sider, norske kataloger).
