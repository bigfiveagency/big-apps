# Big Apps — apps.bigfive.cloud

Sito vetrina per la vendita dei plugin BigFive. Primo prodotto: **Bot Marley**, chatbot AI self-hosted per WordPress.

## Stack

- WordPress su Serverplan (`89.46.227.10`, porta SSH 10112, utente `bigapps` — alias SSH `bigapps`)
- Tema: **Quitox** (Theme_Pure, ThemeForest) con Elementor + TP Core + ACF Pro
- Demo importato: Home 1, via One Click Demo Import
- Checkout: Freemius (prodotto 33359, piani 69 / 129 / 199 €)

## Struttura del sito

- `/` — homepage vetrina
- `/bot-marley/` — landing del plugin
- `/bot-marley/docs/` — documentazione

## Note operative

- I temi ThemeForest sono in `temi/` (esclusa dal repo: licenza commerciale).
- Fix attiva nel Customizer → CSS aggiuntivo: `.wow { visibility: visible !important; }` — l'init di WOW.js del tema non parte e senza questa regola diverse sezioni restano invisibili. Non rimuoverla.
- Descrizione del prodotto: `Bot Marley/PLUGIN_DESCRIPTION.md` nel progetto `chatbot`.
