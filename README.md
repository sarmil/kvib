# KVIB - Kartverkets interaksjon- og designbibliotek

[KVIB](https://kartverket.github.io/kvib/) er et prosjekt i regi av eiendomsportalen med mål om å samle designguidelines og kode for Kartverkets applikasjoner.

Dokumentasjonen for KVIB hostes med [github-pages](https://pages.github.com/). Sidene generes med [Jekyll](https://jekyllrb.com/).

I tillegg har vi også laget et NPM-bibliotek, KVIB-scss, som inneholder felles-scss for designbiblioteket. Kildekoden til dette ligger i sass-mappen i dette repoet, og det ferdige biblioteket kan lasten ned fra i3-npm repoet på [artifactory](https://artifactory.statkart.no/artifactory/webapp/#/home).

## Kom i gang med github-pages:
1. Installer ruby og jekyll: https://jekyllrb.com/docs/installation/
2. Klon prosjektet fra github: https://github.com/kartverket/kvib
3. Fra prosjektmappa kjør `bundle install`
4. Fra prosjektmappa kjør `bundle exec jekyll serve`
5. De generert sidene er tilgjengelig fra http://localhost:4000/
6. Gjør endringer i filene i docs-mappen for å endre de genererte sidene, disse blir automatisk oppdatert så lenge forrige kommando kjører
7. Endringene blir automatisk publisert når du committer til github.

Her er en fin tutorial for å lære jekyll: https://jekyllrb.com/docs/step-by-step/01-setup/

## Kvib-css:
For å publisere ny versjon av KVIB-css til artifactory:
1. Bytt til sass-mappen (hele KVIB-css biblioteket ligger her i denne mappen)
2. npm config set registry https://artifactory.statkart.no/artifactory/api/npm/i3-npm-release-hfs/
3. npm login, du må oppgi AD-brukernavn og passord, og du må ha tilgang til repoet i3-npm-release-hfs/ (kan fås fra Vegar Andersen, U2)
4. npm version patch, evt se [dokumentasjon hos NPM](https://docs.npmjs.com/cli/version)
5. npm publish --registry https://artifactory.statkart.no/artifactory/api/npm/i3-npm-release-hfs/
6. Husk å commitee og push endringer til github! Npm version lager kode-endringer, så det skal alltid commites når denne er kjørt!

## Rutine ved endringer:
1. Gjør nødvendige endringer i css-filene i css-mappa i src.
2. Sørg for at dokumentasjonen er oppdatert for all ny kode i docs-mappa.
3. Opprett pull-request for endringene dine på github
4. Merg endringene til master når de er godkjent
5. Publiser ny versjon (se steg 1-5 i avsnittet over) av KVIB-css til artifactory
6. Oppdater docs/about.mb med informasjon om ny versjon og hva som er endret, (hent versjonsnummer fra package.json, som ble oppdatert når du kjørte steg 4 i publiseringen)
7. Push commit med nytt versjonsnummer og oppdatert about.md direkte på master
