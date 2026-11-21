# Teknisk research runde 2, verifiserer 1

Hentet: 2026-11-21. Alle funn er lest via WebFetch (sideinnhold gjengitt av en liten modell, ikke rå HTML) med mindre annet står. Sitater er slik verktøyet gjengav dem.

## 1. Vercel Hobby og kommersiell bruk

**Svar: Hobby er kun for personlig eller ikke-kommersiell bruk. En bedriftsnettside som markedsfører en betalt tjeneste er svært sannsynlig «kommersiell». Vercel definerer ikke grensen eksplisitt.**

- Vercel Terms of Service, Section 4 (Hobby Plan): «You shall only use the Services under a Hobby plan for your personal or non-commercial use.» Samme seksjon: «We offer a free Hobby plan at our sole discretion.» Kilde: https://vercel.com/legal/terms. Utgiver: Vercel. Dato: Effective/Last Updated 19. oktober 2026. Lest. Tillit: høy (ordlyden); middels (tolkningen av «kommersiell»).
- Terms inneholder ikke uttrykket «fair use» i det hentede innholdet, selv om fair use-siden lenker til `/legal/terms#fair-use`. Det er en uoverensstemmelse jeg ikke fikk avklart.
- Fair use-siden: https://vercel.com/docs/limits/fair-use-guidelines (Vercel, last_updated 2026-11-12, lest). Den handler om bruksmengde (Hobby: 100 GB Fast Data Transfer, 1 000 000 funksjonskall per måned). Seksjonene «Examples of fair use» og «Never fair use» kom tomme i uttrekket, så eksemplene er ikke lest. Siden definerer ikke «kommersiell». Tillit: høy på mengdene, lav på eksemplene.
- Hobby-planen: https://vercel.com/docs/plans/hobby (Vercel, 2026-11-12, lest). Ingen omtale av kommersiell bruk på siden.
- Sammenhengen er tolkning: siden markedsfører en betalt tjeneste og brukes i næringsvirksomhet, så den faller etter vanlig språkbruk utenfor «personal or non-commercial». Ingen Vercel-kilde jeg leste sier uttrykkelig «bedriftsside uten salg på siden er (ikke) kommersiell». Pro koster per bruker: «Developer seats cost $20 per user / month» (Hobby-siden).

## 2. Gratis alternativer for kommersiell bruk

| Tjeneste | Svar | Belegg |
|---|---|---|
| Cloudflare Pages | **Uklart, ingen forbud funnet** | Self-Serve Subscription Agreement (https://www.cloudflare.com/terms/, Cloudflare, lest) pkt. 2.6: «We may offer free or trial versions of the Services ("Free Services") from time to time.» Ingen ikke-kommersiell begrensning i det som kom tilbake. Developer Platform-vilkårene (https://www.cloudflare.com/service-specific-terms-developer-platform/, oppdatert 28. sept. 2026, lest) omtaler ikke kommersiell bruk. Pkt. 2.2.1(h) forbyr å «process or collect personal or business credit card information on any web property that is receiving Free Services». Tillit: middels (fravær av forbud, ikke eksplisitt tillatelse). |
| Netlify | **Uklart** | Terms of Use (https://www.netlify.com/legal/terms-of-use/, oppdatert 14. okt. 2026, lest) har ingen passasje om kommersiell bruk og viser til Self-Serve Subscription Agreement, som jeg ikke leste. Billing-FAQ for legacy-planer sier bare «Most paid features include a free tier of service for evaluation and smaller projects». Pris-siden nevner ikke kommersiell bruk. Tillit: lav til middels. |
| GitHub Pages | **Nei for bedrifts-/forretningsbruk i streng forstand** | https://docs.github.com/en/pages/getting-started/github-pages-limits (GitHub, lest): tjenesten «is not intended for or allowed to be used as a free web-hosting service to run your online business» (samme setning dekker e-handel). Grenser: 1 GB side, myk grense 100 GB/mnd. En ren informasjonsside uten salg er en gråsone. Tillit: høy på sitatet, middels på anvendelsen. |

Merk: Cloudflare-avtalen kom som kort utdrag av en liten modell. Jeg har ikke lest hele avtalen for en ev. kommersiell klausul.

## 3. CMS på ren HTML

- **Decap CMS** (Decap, lest): https://decapcms.org/docs/install-decap-cms/ beskriver installasjon uten byggesteg: opprett `admin/index.html` som laster `<script src="https://cdn.jsdelivr.net/npm/decap-cms@^3.0.0/dist/decap-cms.js"></script>` og `admin/config.yml`. Støttede backender: Git Gateway, Azure, Bitbucket, Gitea/Forgejo, GitHub, GitLab, Test. Tillit: høy. Det er likevel kun belagt at en `admin`-mappe i publisert side fungerer. Jeg fant ikke et eksplisitt eksempel med ren HTML uten generator, men CDN-skriptet krever ikke bygg.
- **Innlogging utenfor Netlify** (https://decapcms.org/docs/github-backend/, lest): «Because GitHub requires a server for authentication, Netlify facilitates basic GitHub authentication.» Alternativ: «Decap Turbo provides hosted GitHub authentication». Og: «all users must have push access to your content repository». Dvs. en ikke-utvikler trenger en GitHub-konto med skrivetilgang, pluss en OAuth-tjener (egen eller tredjepart) på Vercel/Cloudflare. Selve OAuth-oppsettet står på en annen side jeg ikke leste. Tillit: høy.
- **Pages CMS**:
  - README (https://github.com/pagescms/pagescms, lest): «The easiest way to get started is the hosted version at app.pagescms.org.» MIT-lisens. Tillit: høy.
  - Gratis: nettsiden (https://pagescms.org/, lest) sier «100% free» for online-versjon, Vercel-deploy og selvhosting. Ingen betalte nivåer listet. Tillit: middels (utgivers egen påstand, ingen vilkår lest).
  - Plain HTML: **ikke belagt**. README og forsiden nevner Jekyll, Hugo, Astro osv., ikke ren HTML. Docs-intro: «Add a `.pages.yml` file to the repository» og at verktøyet «does not replace your site generator». Det tyder på at det ikke krever generator, men det står ikke uttrykkelig.
  - Tilganger: kun søkeutdrag (https://pagescms.org/docs/development/github-app): GitHub App med Contents read/write, Metadata read, Administration read/write (guides-siden lister også Actions read/write). Tillit: lav til middels.
  - Ikke-utvikler: https://pagescms.org/docs/configuration/collaborators/ (lest): «Collaborators are invited by email.» «Use them when someone needs to edit content or media but does not have a GitHub account.» Skriving går via GitHub App-tokenet. Siden sier ikke om det virker på den hostede appen eller hvordan de logger inn. Tillit: høy på sitatene, ukjent for hostet bruk.
- Alt som er git-basert committer til repoet, så hostingen er uavhengig av CMS-valget.

## 4. Skjema

- **Netlify Forms** (https://docs.netlify.com/manage/forms/setup/, lest): krever at Netlify bygger/deployer siden, fordi skjemaer oppdages ved deploy. Skjemastørrelse maks 8 MB. Gratisgrense for innsendinger: ikke funnet (billing-FAQ nevner bare «Forms Level 0, which includes 100 form submissions per month» for en betalt tilleggsmodell og advarer mot å lese det som gratisgrense). Lagringsregion/EU: ikke oppgitt. Bruk av Netlify Forms binder dessuten hostingen til Netlify. Tillit: middels.
- **Cloudflare Pages Functions** (https://developers.cloudflare.com/pages/functions/pricing/, Cloudflare, endret 2026-09-08, lest): kall teller mot Workers Free-kvoten, daglig tilbakestilling kl. 00:00 UTC; statiske ressurser er gratis og ubegrenset. Eksakt daglig tak står ikke i uttrekket (eksempel: 100 000 per dag). Lagring: funksjonen lagrer ikke data selv, så EU-spørsmålet gjelder e-posttjenesten.
- **Resend** (https://resend.com/pricing, lest): gratis 3 000 e-poster/mnd, maks 100 per dag, 3 domener. Region: «Configure the region that your emails are sent from», men EU/Irland er ikke navngitt på siden. Tillit: middels.
- **Formspree**: ikke undersøkt i denne runden.
- Vurdering (min tolkning): en liten funksjon + Resend gir full kontroll og EU-region ikke bekreftet, men krever kode, API-nøkkel og spamvern. Om det er enklere enn Formspree er ubelagt, fordi Formspree ikke ble lest.

## Lette etter, fant ikke
- Vercels definisjon av «kommersiell» og innholdet i «Examples of fair use»/«Never fair use».
- Vercel Terms «#fair-use»-seksjon (finnes ikke i hentet tekst).
- Eksplisitt kommersiell-bruk-klausul for Cloudflare Pages og Netlify gratisplan (Netlify Self-Serve Agreement ikke lest).
- Netlify Forms' gratisgrense og datalagringsregion.
- Eksplisitt belegg for Pages CMS på ren HTML, og innloggingsflyt/tilganger for hostet app (kun søkeutdrag).
- Decaps OAuth-oppsett for ikke-Netlify-hosting.
- Cloudflare Pages Functions' eksakte daglige gratistak.
- Resend EU-region og Formspree-vilkår.
