# Handoff — proseguire il lavoro su apps.bigfive.cloud

> Cartella temporanea per lavorare da un'altra postazione. Da rimuovere quando non serve più.
> Ultimo aggiornamento: 3 luglio 2026.

## Obiettivo del progetto

Sito vetrina **apps.bigfive.cloud** per vendere i plugin BigFive. Primo prodotto: **Bot Marley**, chatbot AI self-hosted per WordPress (RAG sui contenuti del sito, WordPress AI Services API, niente costi per conversazione).

Struttura prevista:
- `/` — homepage vetrina
- `/bot-marley/` — landing del plugin
- `/bot-marley/docs/` — documentazione

Checkout: **Freemius**, prodotto **33359**, piani Pro annuali **69 / 129 / 199 €** (1 / 3 / 15 siti), sconto rinnovo 20%.

## Accessi

- **Sito**: https://apps.bigfive.cloud — wp-admin utente `admin` (password nel password manager, NON in questo repo)
- **Server**: Serverplan `89.46.227.10`, porta SSH `10112`, utente `bigapps`. Alias `bigapps` già configurato in `~/.ssh/config` della postazione principale. ⚠️ SSH in attivazione: al 3/7 non ancora funzionante — finora tutto il lavoro è stato fatto da browser (wp-admin).
- **Repo**: `git@github.com:bigfiveagency/big-apps.git` (push funziona via SSH; il token HTTPS salvato risulta senza permessi di scrittura)

## Stato attuale di WordPress

- Nome sito ancora "Bloggers Unite" → **da cambiare**
- Tema attivo: **Quitox** (Theme_Pure, ThemeForest) — scelto dopo aver provato Softec. Gli zip dei temi sono in `temi/` (fuori dal repo, licenza commerciale) e sulla postazione principale in Dropbox.
- Demo importato: **Home 1** con One Click Demo Import, completo (pagine, menu, kit Elementor, campi ACF).
- Plugin attivi: Advanced Custom Fields Pro, Elementor, **Elementor Pro** (licenza collegata da Lorenzo), TP Core, Breadcrumb NavXT, Contact Form 7, Kirki, WP Classic Editor, One Click Demo Import.
- **Permalink**: struttura `/%postname%/` (attivata il 3/7, prima erano "plain").

### Architettura del sito (decisa il 3/7, già applicata)

- **Front page** = pagina "Home 2" (id **4451**) → home generica vetrina plugin
- **/bot-marley/** = pagina ex "Home 1" (id **4450**, rinominata "Bot Marley") → landing del plugin, contenuti demo ancora da sostituire
- **/about/** = pagina "About" (id **81**) → about essenziale
- **Main Menu** (id 13): Home, Bot Marley, About, Support (→ https://users.freemius.com/, da affinare con l'URL support specifico del prodotto Freemius)
- Bottone header **Contact Us** → `/about/` (impostato via Customizer, setting Kirki `quitox_button_link`)
- **Side info / hamburger desktop disattivato** (Customizer `quitox_side_hide` = false). Su mobile l'hamburger resta (è in un contenitore `d-lg-none`) e apre l'offcanvas col menu.
- Link **Login** dell'header nascosto via CSS: è hardcoded a `login.html` nel template PHP del tema; per ricollegarlo (es. al portale Freemius) serve child theme o edit del tema quando ci sarà SSH.

### Palette BigFive (applicata il 3/7)

Colori brand: nero `#252427`, bianco, viola `#633F98` (primario), sabbia `#e1d2a3`, crema `#f9f6ed`, oro `#ebbe1e` (accento). Applicata su tre livelli:

1. **Opzioni Kirki** (Customizer → colori tema — vincono sul CSS aggiuntivo): theme_color_1 `#633F98`, theme_color_2 `#ebbe1e`, theme_color_3 `#4F327A` (hover), body `#5E5A66`, footer bg `#252427`, breadcrumb bg `#f9f6ed`.
2. **CSS aggiuntivo**: override delle restanti variabili `--tp-*` (pink/sky→sabbia, grey-2→crema, bordi caldi) + testo scuro sui bottoni oro.
3. **Dati Elementor**: sostituiti i colori hardcoded nei widget di home 4451 (12) e About 81 (15); Bot Marley 4450 non ne aveva (i `*_color_b` sono default inerti dei gradienti, ignorarli).

Secondo giro di verifica (audit dei colori computati su tutte le pagine → pulito): footer social e bordo in palette via CSS, testo verticale hero in lavanda, **topbar disattivata** (`quitox_topbar_switch` = false — conteneva telefono e "now hiring" demo; riattivarla solo con contatti veri).

Fuori palette restano le **immagini demo** (blob hero blu/rosa su /bot-marley/, screenshot app, icone SVG): si risolvono sostituendo i contenuti. Anche **logo Quitox** e **titolo sito "Bloggers Unite"** (appare nei breadcrumb) sono ancora da sostituire — serve decisione di Lorenzo sul nome.

### Fix applicate (non toccare)

1. **Customizer → CSS aggiuntivo**:
   - `.wow { visibility: visible !important; }` — l'init di WOW.js nel `main.js` del tema non parte: senza questa regola le sezioni con classe `.wow` (testimonial, accordion, CTA, feature cards) restano invisibili. Bug del tema, non del contenuto.
   - `.tp-header__login { display: none !important; }` — nasconde il Login rotto (vedi sopra).
   - `@media (min-width: 992px) { .tp-menu-bar { display: none !important; } }` — hamburger solo su mobile per tutti gli stili header (lo switch `quitox_side_hide` copre solo alcuni).
   - `.breadcrumb__area { background-image: none !important; }` — via l'immagine demo azzurra dal breadcrumb.
2. **Main Menu** (id 13) ripulito da ~28 voci "(non valido)" residue del vecchio demo Softec, poi ricostruito con le 4 voci definitive.

### Problemi noti / todo tecnici

- I menu del footer (Community, Other Pages, Platform, Usefull Links, What We Do) contengono probabilmente altre voci invalide di Softec — la colonna "Other Pages" nel footer è vuota. Pulire come fatto per il Main Menu (Aspetto → Menu → Selezione multipla).
- 26 pagine nel cestino (residui Softec) da svuotare prima del go-live.
- Il widget testimonial di Quitox non verrà usato: ignorare eventuali suoi problemi, si eliminerà dalla pagina in Elementor.

## Prossimi passi concordati

1. Sostituire i contenuti demo: home generica (4451, vetrina plugin), landing Bot Marley (4450), About (81)
2. Cambiare nome sito, logo, palette
3. Integrare il checkout Freemius (product 33359) nella pagina pricing / landing
4. Pagine legali: Privacy Policy (esiste demo), Terms; necessarie per vendere
5. Pulizia finale (cestino 26 pagine, menu footer con voci invalide Softec, pagine demo inutilizzate: Home 3, Faq, Pricing, Project, Service, Team, ecc.)

Nota Elementor: la landing 4450 è costruita interamente con widget TP Core del tema (tp-banner, services, app-area, tp-integration, tp-cta, tp-fact, tp-accordion-list). Strategia scelta: tenere i widget TP e sostituirne testi/immagini; usare Elementor Pro per Theme Builder/Form dove serve. L'editor Elementor è pilotabile via API JS (`$e`) dal browser.

## Testi pronti

In `_handoff/testi/`:
- `PLUGIN_DESCRIPTION.md` — **descrizione completa e aggiornata** del plugin (v0.7.1): short description, feature Free/Pro, pricing, FAQ, installazione, changelog. È la fonte principale per landing e docs.
- `readme.txt` — readme WordPress.org in formato classico (v0.2.0, più vecchio: usare come riferimento di tono, non di contenuto).

Originali sulla postazione principale: `~/Dropbox/CLAUDE/chatbot/Bot Marley/` (repo git separato del plugin).
