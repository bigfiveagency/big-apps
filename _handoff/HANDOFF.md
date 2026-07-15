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
2. **Main Menu** (id 13) ripulito da ~28 voci "(non valido)" residue del vecchio demo Softec, poi ricostruito con le 4 voci definitive. Voce **Support** → https://customers.freemius.com/store/17612.
3. **Header sempre fisso viola** (14/7, tutto via CSS aggiuntivo): `#header-sticky` → `position:fixed; background:#633F98; padding:0` (il `padding:0` centra verticalmente il menu: le varie pagine usano stili header diversi — `tp-header__space`/`space-2`/`space-3` — e alcune avevano `padding-top:25px` che scentrava le voci). Testo menu bianco, hamburger bianco su mobile, CONTACT US resta gold. Compensato con `body{padding-top:101px}` (133px con admin-bar). **Breadcrumb eliminata** ovunque (`.breadcrumb__area{display:none}`) — il titolo pagina è dato dal contenuto Elementor.
5. **Header a due livelli** (14/7): 
   - Colori/loghi (ultima versione): **topbar grigia** `#33323a` — logo **BigFive Apps** bianco+oro (`logo-bigfive-apps.svg`) piccolo a sinistra, link **Bot Marley · About · Support** bianchi a destra (hover oro). **Menu bar crema** `#f9f6ed` con logo **Bot Marley** (`logo-bot-marley.svg`), voci scure `#252427` (hover viola), **BUY PRO** pillola viola/bianco (`#header-sticky .tp-btn`).
   - **Larghezza contenuto uguale** per topbar e menu: entrambi max-width 1600px centrato + padding 60 (il tema metteva `padding-left/right:100px` fisso su `#header-sticky` → sostituito con container-fluid max-width 1600).
   - **Topbar** globale con link **About** + **Support** (→ customers.freemius.com/store/17612) allineati a destra. **Si nasconde allo scroll**: lo script footer aggiunge/toglie la classe `body.bf-scrolled` quando `scrollY>60`; il CSS fa `translateY(-100%)` sulla topbar e porta l'header a `top:0` (32px con admin-bar), con transizioni. ⚠️ Il tema NON ha topbar su questi header style né uno slot menu, quindi la topbar è creata via **JS in un widget footer** (Custom HTML `widget-46`, id script `#bf-topbar`): lo script prepende `<div id="bf-topbar">` al body su ogni pagina. Se si edita quel widget footer, non rimuovere lo script. Stile e posizionamento fissi via CSS (`#bf-topbar{position:fixed;top:0;background:#4F327A}`, header spostato a `top:40px`, body `padding-top:140px`; varianti `body.admin-bar` +32).
   - **Main Menu** (id 13) trasformato in **ancore interne** alla landing Bot Marley: Features → /bot-marley/#features, WooCommerce → #woocommerce, Pricing → #pricing, FAQ → #faq (URL assoluti così funzionano da ogni pagina). Rimosse HOME/ABOUT/SUPPORT. Il **logo** linka la home. Sezioni con `_element_id` (features=sez.1, woocommerce=sez.6, pricing, faq) + CSS `.elementor-element[id]{scroll-margin-top:150px}` per l'offset dell'header fisso.

6. **Logo BigFive Apps** (14/7): SVG bianco+oro (`/wp-content/uploads/2026/07/logo-bigfive-apps.svg`) impostato su 3 opzioni Kirki — `logo` (header standard, usato da Home/About), `seconday_logo` (header di Bot Marley, classe `.secondary-logo`) e `quitox_footer_logo`. Nessun filtro sul logo (è già bianco+oro, adatto a viola/nero); sizing CSS `#header-sticky .standard-logo img, #header-sticky .secondary-logo img{height:42px;filter:none}`.

### Problemi noti / todo tecnici

- I menu del footer (Community, Other Pages, Platform, Usefull Links, What We Do) contengono probabilmente altre voci invalide di Softec — la colonna "Other Pages" nel footer è vuota. Pulire come fatto per il Main Menu (Aspetto → Menu → Selezione multipla).
- 26 pagine nel cestino (residui Softec) da svuotare prima del go-live.
- Il widget testimonial di Quitox non verrà usato: ignorare eventuali suoi problemi, si eliminerà dalla pagina in Elementor.

### Landing /bot-marley/ (contenuti veri applicati il 3/7)

Pagina 4450 ristrutturata via Elementor con i testi da `_handoff/testi/PLUGIN_DESCRIPTION.md` (inglese):
hero → 6 feature card (repeater `tp_service_list` del widget services) → sezione screenshot placeholder → "Index. Retrieve. Answer." → accordion "Your content, your rules" → integrazioni → **pricing** (sezione `tp-pricing` copiata dalla pagina demo Pricing 4455, anchor `#pricing`: Pro 1/3/15 siti a 69/129/199€) → CTA "Try Bot Marley on your site" → stats (15 lingue, 24/7, 30 giorni) → FAQ (5 domande dal readme).

Sotto i prezzi c'è una sezione **"Support & Customer Portal"** (heading + text + button Elementor nativi) con bottone viola "Go to the customer portal" → https://customers.freemius.com/store/17612 (aggiunta il 14/7).

**Griglia feature "Everything you need"** (widget `services` id `7d931f5`, sezione 1): 8 card a **4 per riga** (CSS `@media(min-width:992px){.elementor-element-7d931f5 [class*=col-xl-4]{flex:0 0 25%;max-width:25%}}` nel Customizer). Card: No hallucinations, Self-hosted & private, Any AI provider (con "unlimited conversations" mergiata dentro), Fully customizable, Behaviour & languages, Lead capture, Auto-sync knowledge, Works everywhere. Icone ancora demo.

**Sezione WooCommerce** (widget `html`, id `a09b82c`, prefisso `.bmwoo`, card viola con badge "WooCommerce · Pro"): claim "Turn conversations into revenue" + 3 vantaggi (push prodotti, coupon contestuali, statistiche ricavi). Inserita **prima del confronto** (indice 6).

**Blocco confronto "Other chatbots vs Bot Marley"** (14/7): sezione con un widget `html` (id `a608c3e`, tabella comparativa in HTML+CSS inline, prefisso classi `.bmcmp`, palette brand — colonna Bot Marley viola con ✓ oro, "other chatbots" spenta con ✕). Inserita **prima della sezione pricing** (indice 7). 8 righe: privacy, GDPR/compliance, pricing, AI provider, accuratezza, WordPress nativo, setup, lingue. Per editarla: editor Elementor → widget HTML.

⚠️ **Compliance framing** (corretto il 14/7 dopo dubbio di Lorenzo): NON affermare "i dati non lasciano la UE / nothing leaves your site" — falso, perché contenuti+query vanno al provider AI (spesso USA) per embedding e risposte. Le claim vere: storage locale (DB WordPress), nessun intermediario SaaS, e compliance *ottenibile scegliendo un provider EU + DPA diretto*. Vale per il blocco confronto E la card "Self-hosted & private".

Da completare sulla landing:
- **Screenshot**: sezione "See Bot Marley in action" ha 3 widget immagine vuoti da riempire (Lorenzo) + le immagini demo di hero/accordion/app-area sono ulteriori slot naturali.
- **Bottoni "Get Pro"**: puntano a `#` — da collegare al checkout Freemius (prodotto 33359, servono gli URL/plan-id dal dashboard Freemius).
- Icone card pricing e icone integrazioni = ancora demo.
- Quirk widget scoperti: il counter `tp-fact` non renderizza il numero "0"; il bottone del widget `tp-cta` (layout-1) non renderizza mai — il bottone è stato messo come `<a class="tp-btn-blue">` dentro la descrizione. Il typo del tema `tp_accordion_content_desctiption` è la chiave giusta dei repeater accordion.

### Homepage / front page (4451 "Home 2") — contenuti applicati il 14/7

Vetrina rifatta con focus Bot Marley + BigFive in generale, riprendendo tono e contenuti da bigfive.it/en/services e /en/about-us. Struttura finale (6 sezioni, ridotta da 10):
1. **Hero** (tp-banner) — "Premium WordPress plugins, built by BigFive ✨" + sottotitolo con link "Discover Bot Marley →". Rimossi i badge App Store/Google Play demo (svuotato `list_2`) e cambiato `tp_des`.
2. **Brand strip** (tp-brand) — tagline "From 2012 · 9 international awards · 100+ websites live". ⚠️ i loghi (Spotify/Slack/Zoom/Dropbox) sono ancora demo.
3. **Bot Marley spotlight** (tp-cta) — "Meet Bot Marley" + bottone "Explore Bot Marley" → /bot-marley/.
4. **What we build** (features, 3 card) — Custom WordPress plugins / Websites & e-commerce / AI & digital solutions. Section id `services` (ancora `#services` dall'hero btn2, ora non più usato). ⚠️ icone card ancora demo.
5. **About BigFive** (about) — "A lightweight agency, big results" + 4 punti chiave in HTML nella descrizione + bottone "About BigFive" → /about/.
6. **Final CTA** (tp-cta, widget `e8c0a14`, sezione `cb4d84d`) — "Let's build something together" + "Get in touch" → /about/. Restylata il 14/7 via CSS scoped: sfondo **giallo** (`.tp-cta__wrapper-2`), titolo **viola**, testo **nero**, bottone **grigio scuro #252427 testo bianco** (`.tp-btn-sky`), + `margin-bottom:90px` per staccarla dal footer.

Header: il bottone Kirki è ora **BUY PRO** (`quitox_button_text`) → `/bot-marley/#pricing` (`quitox_button_link`).

Rimosse dalla home: pricing, app-badge area, testimonial, FAQ (non pertinenti/senza contenuti reali).

Quirk confermati: il bottone nativo dei widget `tp-cta` e la lista/badge del widget `about` non renderizzano nel layout usato → bottoni messi come `<a class="tp-btn-blue">` e punti chiave come HTML dentro le descrizioni (i campi description del tema accettano HTML).

⚠️ **Footer ancora demo** (appare su tutte le pagine): colonne Services/What We Do/Other Pages con link Customization/Design/…, blocco "Ready To Download" con badge app-store, logo Quitox. Da ripulire (widget/opzioni footer del tema).

### Pagina /about/ (81) — contenuti applicati il 14/7

Rifatta con focus su BigFive agenzia + tutti i servizi (contenuti da bigfive.it/en/about-us e /en/services). Struttura finale (4 sezioni, ridotta da 6):
1. **Intro** (widget `about`, layout-3) — "A lightweight agency, big results", badge "14 Years of projects", storia BigFive (dal 2012, Monza, team full-remote, Lorenzo creative director), checklist (One partner / Zero templates / 9 awards / 100+ siti), bottone "Our services" → #services. ⚠️ Mapping campi layout-3 non intuitivo: titolo=`tp_ex_title`, badge grande=`experience_title`, corpo=`tp_ex_des`, label=`experience_subtitle`, checklist=`tp_list_list`.
2. **Servizi** (widget `features`) — griglia con **tutti i 15 servizi** BigFive. Reso griglia cambiando `tp_design_style` da `layout-3` (slider) a `layout-1` (grid statica). Section id `services`. ⚠️ icone tutte uguali (demo, clonate dal template).
3. **Stats** (tp-fact) — 14 anni / 9 awards / 100+ siti / 15 servizi.
4. **FAQ + CTA finale** (accordion + tp-cta) — 5 FAQ agenzia + "Let's talk about your project" con bottone "Get in touch" → https://bigfive.it/en/ (in attesa di una pagina contatti dedicata).
Rimosse: pricing, team (senza dati/foto reali).

### Footer — pulito il 14/7

Il footer è fatto con **widget classici** in "Footer Style 2 : 1-4" (Aspetto → Widget). Ora:
- **Col1 "Product"** (widget-45, nav_menu id 16 "What We Do" ripurposato): Bot Marley, Support → users.freemius.com. Sotto, un Custom HTML (widget-46) con frase BigFive (prima erano i badge App Store/Google Play demo).
- **Col2 "Company"** (widget-47, nav_menu id 14 "Other Pages" ripurposato): Home, About.
- Rimossi i widget nav_menu extra (48, 49) e il blocco "Ready To Download".
- ⚠️ Restano demo: **logo "Quitox"** (header+footer, serve file logo BigFive) e **icone social** che puntano a `#` (servono URL reali). I menu WordPress "What We Do"(16) e "Other Pages"(14) sono stati riusati come Product/Company: se servono altrove, ricordarlo.

### Pagina Documentation (/documentation/, id 4637)

Guida utente pubblica per chi usa il plugin. **Ricostruita in Elementor** (14/7) con blocchi editabili — così è modificabile visivamente in Elementor.
- Contenuto = **nuova guida utente** (taglio da guida, per orientare l'utente ed evitare ticket di supporto), non più la doc interna. Sorgente: `_handoff/testi/Bot-Marley-User-Guide.md` (e `chatbot/Documentation/Bot-Marley-User-Guide.md`).
- Struttura: sezione titolo + sezione a 2 colonne → **col sinistra (30%) sticky con widget "Table of Contents" di Elementor Pro** (indice auto-generato dagli H2) + **col destra (70%) con Heading (H2) + Text Editor per ogni sezione**.
- Stile via CSS scopato per **ID pagina** (`.page-id-4637 ...`) — NB: i `_css_classes` impostati via API su sezioni/colonne NON si applicano, quindi usare page-id. Titoli macro **viola**, resto **grigio**, tabelle/blockquote stilizzati.
- Anchor offset per l'header fisso: `.page-id-4637 [id^=elementor-toc__heading-anchor]{scroll-margin-top:150px}`. Aggiunto anche `html{scroll-behavior:auto}` globale (lo smooth-scroll del tema bloccava lo scroll programmatico).
- In menu come ultima voce **Documentation** → /documentation/.
- Ancore con **slug parlanti** (ID leggibili sui widget Heading, usati anche dall'indice): `#welcome #requirements #quick-start #connect-ai #knowledge #widget #behaviour #leads #languages #woocommerce #settings #statistics #privacy #troubleshooting` — linkabili nei ticket (es. `/documentation/#knowledge`). I titoli non hanno più il numero (lo mette l'indice) per evitare la doppia numerazione.

## Prossimi passi concordati

1. Sostituire i contenuti demo: ~~home generica (4451)~~ ✔, ~~landing Bot Marley (4450)~~ ✔, ~~About (81)~~ ✔ (v. sotto)
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

- **FAQ Bot Marley (4450, widget tp-accordion-list #f7aa94b, repeater `accordions`)**: 14/7 ampliata da 5 a 13 domande. Nuove: provider AI, free plan, tempo setup, performance, privacy (framing corretto), PDF/documenti, lead, WooCommerce. Ordine tematico, "renew Pro" resta ultima.

- **About (81) — FAQ + CTA (15/7)**: FAQ (widget tp-accordion-list #e748eb6) ampliata da 5 a 11 domande (durata progetto, costo, supporto post-lancio, presa in carico progetti esistenti, design/branding, AI). Il vecchio CTA "Get in touch" (#17d14d6, era layout-4 con <a> dentro la descrizione) sistemato: convertito a **layout-3 giallo** come il blocco home, **spostato in una sezione full-width propria (a7bf8e1) sotto le FAQ** (prima era nella stessa colonna e si accavallava). Bottone nativo Get in touch -> https://bigfive.it/en/ (nuova scheda). Colori via Customizer CSS scoped `.elementor-element-17d14d6` (sfondo #ebbe1e, titolo #633F98, testo/bottone #252427, marker `/* about-cta-yellow */`).

- **About (81) — immagini servizi (15/7)**: sostituite le icone demo dei 15 servizi (widget features #ee127a4, campo `tp_box_icon_image`, type `image`) con le foto reali di ogni servizio prese da bigfive.it/servizi. Scaricate e caricate nella media library (ID 4674-4688, file `bigfive-<slug>.jpg/webp/svg` in uploads/2026/07). Upload fatto via REST (`wp.apiFetch` POST /wp/v2/media) con fetch CORS diretto da bigfive.it (il file_upload del browser accetta solo file allegati dallutente; scratchpad e cartella progetto non sono whitelisted). Website Development usa `siti-web.svg` (SVG abilitato sul sito), gli altri 14 foto. Mappatura per titolo servizio.

- **About (81) — immagini servizi full-width (15/7)**: le foto servizio non stanno più nel piccolo slot-icona (88px) ma sono bande full-width in cima a ogni card. CSS Customizer scoped `.elementor-element-ee127a4` (marker `/* about-services-images */`): `.tp-feature__icon` con `margin:-40px -55px 28px` (bleed che annulla il padding 40/55 della card, la card ha `overflow:hidden`+radius 10 → angoli arrotondati automatici), img `width:100 0.000000e+00ight:200px object-fit:cover`. SVG website in `object-fit:contain` su fondo sabbia #f4efe3 con padding 45 (via selettore `img[src$=".svg"]`).
