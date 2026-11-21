# Teknisk research R1-A: hosting, domene og kontaktskjema

Hentet 2026-11-21. Alle påstander er lest fra nettet denne dagen. Tillit: høy = primærkilde lest direkte, middels = primærkilde med uklarhet eller sammendrag fra verktøy, lav = sekundærkilde eller usikker. Merk: sidene ble lest via et hentingsverktøy som oppsummerer sider, så ordrett sitat er markert der verktøyet ga det.

## 1. Hosting

1. {Påstand: Vercels vilkår sier ordrett: «You shall only use the Services under a Hobby plan for your personal or non-commercial use.» Hobby er dermed ikke ment for kommersiell drift. Formuleringen er «personal or non-commercial», og det er ikke vurdert hvordan Vercel tolker «eller».}
   Kilde: https://vercel.com/legal/terms | Utgiver: Vercel Inc. | Dato: Last Updated 2026-10-19 | hentet=2026-11-21 | tillit=høy | klasse=vilkår

2. {Påstand: Vercel Pro koster 20 USD per bruker per måned (Developer seat). Viewer-seter er gratis ifølge docs-siden. Priser er oppgitt ekskl. mva.}
   Kilde: https://vercel.com/docs/plans/hobby (bekreftet av https://vercel.com/pricing) | Utgiver: Vercel | Dato: last_updated 2026-11-12 (pricing-siden: ikke oppgitt) | hentet=2026-11-21 | tillit=høy | klasse=pris

3. {Påstand: Hobby inkluderer 100 GB Fast Data Transfer og 1 000 000 CDN-forespørsler per måned. Overskrides grensene, må man vente 30 dager på å bruke funksjonen igjen. Pro har 1 TB Fast Data Transfer ifølge pricing-siden.}
   Kilde: https://vercel.com/docs/plans/hobby ; https://vercel.com/pricing | Utgiver: Vercel | Dato: 2026-11-12 / ikke oppgitt | hentet=2026-11-21 | tillit=høy | klasse=pris

4. {Påstand: Vercels «Fair Use Guidelines» (docs) lister kun bruksgrenser (100 GB Hobby osv.). Sidens avsnitt «Examples of fair use / Never fair use» kom ikke ut i hentingen (tomme overskrifter), så innholdet er ikke lest. Siden henviser til Terms of Service #fair-use for vilkårene.}
   Kilde: https://vercel.com/docs/limits/fair-use-guidelines | Utgiver: Vercel | Dato: 2026-11-12 | hentet=2026-11-21 | tillit=middels | klasse=vilkår

5. {Påstand: Cloudflare Pages Free: maks 20 000 filer per side, 1 samtidig build, 500 builds per måned, 20 min byggetid. Siden nevner ingen båndbreddegrense og ingen restriksjon på kommersiell bruk (omtaler ikke temaet).}
   Kilde: https://developers.cloudflare.com/pages/platform/limits/ | Utgiver: Cloudflare | Dato: dateModified 2026-11-19 | hentet=2026-11-21 | tillit=middels (fravær av omtale er ikke bevis for tillatelse) | klasse=teknisk

6. {Påstand: Netlify Free har en kredittgrense på 300 kreditter, og båndbredde koster 20 kreditter per GB (ca. 15 GB per måned dersom alt går til båndbredde). Personal 9 USD per måned, Pro 20 USD per måned med ubegrenset antall medlemmer. Prisiden sier ikke noe om kommersiell bruk.}
   Kilde: https://www.netlify.com/pricing/ | Utgiver: Netlify | Dato: ikke oppgitt | hentet=2026-11-21 | tillit=middels | klasse=pris

7. {Påstand: GitHub Pages er ikke ment som gratis webhotell for netthandel/drift av virksomhet. Siden ekskluderer sider «primarily directed at either facilitating commercial transactions or providing commercial software as a service». Grenser: maks 1 GB publisert side, myk båndbreddegrense 100 GB per måned, myk grense 10 builds per time. En ren informasjonsside for en bedrift er ikke eksplisitt omtalt, så grensetilfellet er uavklart.}
   Kilde: https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits | Utgiver: GitHub | Dato: ikke oppgitt | hentet=2026-11-21 | tillit=middels | klasse=vilkår

## 2. Domene

8. {Påstand: .no-domener kan holdes av norske organisasjoner (registrert i Enhetsregisteret, med organisasjonsnummer) og privatpersoner fra 18 år (norsk fødselsnummer/d-nummer, registrert i folkeregisteret). Alle abonnenter trenger postadresse i Norge. Bestilling går via registrar, ikke direkte hos Norid. Siden nevner ingen grense for antall domener.}
   Kilde: https://www.norid.no/en/nytt-domenenavn/hvem-kan-ha-domene/ | Utgiver: Norid | Dato: publisert 2019-03-08, oppdatert 2021-09-15 | hentet=2026-11-21 | tillit=høy (dato eldre, men primærkilde) | klasse=vilkår

9. {Påstand: Abonnenten må signere en egenerklæring (domenet skal ikke stride mot norsk rett). Dette kom fra søkeresultat-sammendrag, ikke fra en fullt lest Norid-side.}
   Kilde: https://teknisk.norid.no/en/administrere-domenenavn/egenerklaering-fra-abonnenten/kravspesifikasjon-for-egenerklaeringen/ (kun treff, ikke åpnet) | Utgiver: Norid | Dato: ikke oppgitt | hentet=2026-11-21 | tillit=lav | klasse=vilkår

10. {Påstand: Domeneshop oppgir .no-domene til 99 kr per år inkl. 25 % mva. En kampanje (nyhet datert 2026-09-14) tilbød .no til 30 kr. Om DNS-hotell er inkludert fremgår ikke av forsiden.}
    Kilde: https://domene.shop/ | Utgiver: Domeneshop | Dato: forsiden viser nyhet 2026-09-14 | hentet=2026-11-21 | tillit=middels | klasse=pris

11. {Påstand: Cloudflare Pages: apex-domene (example.com) krever at domenet er en Cloudflare-sone, dvs. nameservere pekes til Cloudflare, og sonen må ligge på samme konto som prosjektet. Subdomene (f.eks. www) kan peke med CNAME til `<prosjekt>.pages.dev` uten Cloudflare-DNS, men domenet må først legges til i Pages-dashbordet (ellers kan det gi 522-feil). Manglende CAA-poster må tillate Cloudflare å utstede sertifikat. SSL: Pages styrer TLS-versjon/chiffer selv. Om apex med ekstern DNS ikke støttes, er en tolkning av verktøyet, ikke ordrett.}
    Kilde: https://developers.cloudflare.com/pages/configuration/custom-domains/ | Utgiver: Cloudflare | Dato: dateModified 2026-11-11 | hentet=2026-11-21 | tillit=middels | klasse=teknisk

## 3. Kontaktskjema

12. {Påstand: Formspree Free: 50 innsendinger per måned. Grunnleggende spamfilter (Formshield) på alle planer, reCAPTCHA med egen nøkkel på alle planer, egendefinert honeypot kun på Business/Custom. Turnstile ikke nevnt. Betalte planer: Personal 15 USD/mnd (120 USD/år), Professional 30 USD/mnd (240 USD/år), Business 90 USD/mnd (720 USD/år). Free beskrives «For testing and development». EU-lagring/GDPR ikke omtalt på siden.}
    Kilde: https://formspree.io/plans | Utgiver: Formspree | Dato: ikke oppgitt | hentet=2026-11-21 | tillit=middels | klasse=pris

13. {Påstand: Web3Forms Free: 250 innsendinger per måned, Pro 12 USD/mnd med 20 000 innsendinger. Primærsiden ga 403, så tallene stammer fra søkesammendrag og tredjepartssider, ikke lest primærkilde. Ett tredjepartssvar hevder at innsendinger eldre enn 30 dager slettes på gratisplanen.}
    Kilde: https://web3forms.com/pricing (403, ikke lest); sekundære treff via søk | Utgiver: Web3Forms / tredjeparter | Dato: ikke oppgitt | hentet=2026-11-21 | tillit=lav | klasse=pris

14. {Påstand: Resend Free: 100 e-poster per dag og 3 000 per måned, 3 egendefinerte domener. Pro 20 USD/mnd for 50 000 e-poster, kun månedlig fakturering. Alle planer har «multi-region sending» (valg av region), men EU er ikke navngitt på siden. Å bruke Resend krever en serverless-funksjon (egen kode og API-nøkkel), og avsenderdomene må verifiseres.}
    Kilde: https://resend.com/pricing.md | Utgiver: Resend | Dato: ikke oppgitt | hentet=2026-11-21 | tillit=middels | klasse=pris

15. {Påstand: Cloudflare Turnstile Free: 0 USD, opptil 20 widgets per konto, «Unlimited challenges», 10 hostnames per widget, 7 dagers analyse-historikk. Lite arbeid å bruke som spambeskyttelse (widget i skjema pluss verifisering med secret key i backend).}
    Kilde: https://developers.cloudflare.com/turnstile/plans | Utgiver: Cloudflare | Dato: dateModified 2026-08-14 | hentet=2026-11-21 | tillit=høy | klasse=pris

## Vurdering (kun avledet av funn over, ikke ny evidens)

- Vercel Hobby er etter ordlyden i vilkårene (pkt. 1) knyttet til «personal or non-commercial use». Kommersiell side hos næringsdrivende bør derfor enten på Pro (20 USD/mnd) eller på en annen vert. Dette er en lesning av vilkårstekst, ikke juridisk råd.
- Cloudflare Pages er den gratisvertens som ikke har funnet restriksjon i det som er lest, men vilkårene (Self-Serve Subscription Agreement / Service-Specific Terms) er ikke lest.
- Skjema: ingen primærkilde lest om EU/EØS-lagring hos Formspree eller Web3Forms. Resend-løsning gir mest kontroll men mest arbeid (serverless-funksjon). Turnstile er et godt gratis spamvern i begge tilfeller.

## Leads

- Cloudflare Terms: https://www.cloudflare.com/service-specific-terms-application-services/ (Pages-vilkår, kommersiell bruk)
- Netlify Terms of Service og Forms-dokumentasjon (gratisgrense for innsendinger, spamfilter, hvor data lagres): https://docs.netlify.com/
- Vercel Terms #fair-use samt Vercel docs for domener og DNS (apex A-record, www CNAME, automatisk SSL)
- Formspree og Web3Forms personvern/DPA: EU-lagring, databehandleravtale
- Resend: docs om regionvalg (EU, Irland) og personvern/DPA: https://resend.com/docs
- Norid: https://www.norid.no/en/om-domenenavn/regelverk-for-no/ (regelverk), liste over registrare med priser; Domeneshop DNS-dokumentasjon
- Hosting.com/one.com/DNSimple-sider om .no (sekundære) dukket opp i søk

## Lette etter, fant ikke

- Ordrett kommersiell-bruk-klausul for Cloudflare Pages og Netlify Free (sidene lest omtaler ikke temaet).
- Netlify Forms: gratisgrense og EU-lagring.
- Vercel Fair Use-sidens eksempelavsnitt («Never fair use») kom ikke ut av hentingen.
- Pris på .no-domener hos andre norske registrarer enn Domeneshop (kun én registrar lest).
- Vercel/Cloudflare DNS-oppsett for apex og www på Vercel (kun Cloudflare Pages lest).
- Primærkilde for Web3Forms (403) og hCaptcha/reCAPTCHA-vilkår og personvern.
- Dokumentasjon på databehandling i EU/EØS for noen av skjematjenestene.
