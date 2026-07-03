=== Bot Marley ===
Contributors: bigfive
Tags: ai, chatbot, chat, rag, assistant
Requires at least: 7.1
Tested up to: 7.1
Requires PHP: 8.0
Stable tag: 0.2.0
License: GPLv2 or later
License URI: https://www.gnu.org/licenses/gpl-2.0.html

Self-hosted AI chatbot that answers visitor questions grounded strictly on your own site content, powered by the native WordPress AI Client.

== Description ==

Bot Marley indexes your WordPress content into a local knowledge base and lets visitors ask questions in natural language. Answers are generated **only** from your indexed content — if the answer isn't there, the bot says so instead of inventing one.

It uses the **native WordPress AI Client** (WordPress 7.1+): you connect your AI provider (OpenAI, Anthropic, Google) and API key once under **Settings → Connectors**, and Bot Marley uses it for both indexing (embeddings) and answers. The plugin itself never stores any API key. Your content and your costs stay yours.

**Features (free):**

* Native WordPress AI Client integration — provider keys managed in Settings → Connectors
* Automatic indexing on publish/update/trash, in the background (never blocks the editor)
* Bulk reindex of all published content
* Selectable post types (posts, pages, public custom post types)
* Gutenberg + Classic editor content extraction
* Strict grounding: answers only from indexed content, with a configurable fallback
* Custom persona/rules and a self-hosted chat widget (no external scripts)
* Source citations under each answer

**Pro (planned):**

* WooCommerce products and product fields
* Hand-written FAQ knowledge (dedicated post type)
* Multi-format ingestion (DOCX, TXT, Markdown) and OCR for scanned PDFs
* Advanced widget customization, conversation logs/analytics, multilanguage

== Installation ==

1. Make sure you are on WordPress 7.1+ and have connected an AI provider under **Settings → Connectors**.
2. Upload the `bot-marley` folder to `/wp-content/plugins/` and activate it.
3. Go to **Bot Marley** in the admin menu and confirm the AI Client status is green.
4. Select the post types to index and **Save**.
5. Click **Reindex All Content** for the initial indexing.

== Frequently Asked Questions ==

= Where is my API key stored? =
Not in this plugin. API keys are managed centrally by WordPress under Settings → Connectors and injected by the AI Client at call time.

= Does the bot make things up? =
No. It is instructed to answer only from the retrieved site content and to say it doesn't know otherwise.

= Do I need an external service? =
No backend of ours. The only outbound calls are made by the WordPress AI Client to the provider you connected.

== Changelog ==

= 0.2.0 =
* Switched to the native WordPress AI Client (WP 7.1+) for text generation and embeddings; removed in-plugin API key handling (keys now live in Settings → Connectors).

= 0.1.0 =
* Initial scaffold: provider abstraction, MySQL vector store, content extractor, background indexer, grounded chat engine, REST endpoint, self-hosted widget, settings page.
