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
- Plugin attivi: Advanced Custom Fields Pro, Elementor, TP Core, Breadcrumb NavXT, Contact Form 7, Kirki, WP Classic Editor, One Click Demo Import.

### Fix applicate (non toccare)

1. **Customizer → CSS aggiuntivo**: `.wow { visibility: visible !important; }`
   L'init di WOW.js nel `main.js` del tema non parte: senza questa regola le sezioni con classe `.wow` (testimonial, accordion, CTA, feature cards) restano invisibili. Bug del tema, non del contenuto.
2. **Main Menu** (id 13) ripulito da ~28 voci "(non valido)" residue del vecchio demo Softec.

### Problemi noti / todo tecnici

- I menu del footer (Community, Other Pages, Platform, Usefull Links, What We Do) contengono probabilmente altre voci invalide di Softec — la colonna "Other Pages" nel footer è vuota. Pulire come fatto per il Main Menu (Aspetto → Menu → Selezione multipla).
- 26 pagine nel cestino (residui Softec) da svuotare prima del go-live.
- Il widget testimonial di Quitox non verrà usato: ignorare eventuali suoi problemi, si eliminerà dalla pagina in Elementor.

## Prossimi passi concordati

1. Sostituire i contenuti demo con i contenuti Bot Marley (homepage vetrina, poi landing e docs)
2. Cambiare nome sito, logo, palette
3. Integrare il checkout Freemius (product 33359) nella pagina pricing
4. Pulizia finale (cestino, menu footer, pagine demo inutilizzate)

## Testi pronti

In `_handoff/testi/`:
- `PLUGIN_DESCRIPTION.md` — **descrizione completa e aggiornata** del plugin (v0.7.1): short description, feature Free/Pro, pricing, FAQ, installazione, changelog. È la fonte principale per landing e docs.
- `readme.txt` — readme WordPress.org in formato classico (v0.2.0, più vecchio: usare come riferimento di tono, non di contenuto).

Originali sulla postazione principale: `~/Dropbox/CLAUDE/chatbot/Bot Marley/` (repo git separato del plugin).
