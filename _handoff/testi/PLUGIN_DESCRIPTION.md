# Bot Marley — AI Chatbot for WordPress

**Version:** 0.7.1
**Requires:** WordPress 7.1+
**License:** GPLv2 or later

---

## Short Description

Bot Marley is a self-hosted AI chatbot plugin that indexes your site content and answers visitor questions using only what's on your website — no hallucinations, no off-topic answers, unlimited conversations.

---

## Description

Bot Marley turns your WordPress site into a smart, always-on assistant. It reads your pages, posts, and attachments, builds a vector knowledge base, and answers visitor questions in real time — grounding every response strictly in your content.

Unlike generic chatbots, Bot Marley never makes things up. If the answer isn't in your site, it says so. If it is, it links directly to the relevant page.

It connects natively to the **WordPress AI Services API** (introduced in WP 7.0), which means it works with any AI provider you already have configured — OpenAI, Anthropic, Google Gemini, Mistral, and more — without storing API keys in a separate plugin.

**No per-conversation fees.** SaaS chatbots charge per conversation or per credit. Bot Marley is self-hosted: you pay a flat license, conversations are unlimited, and your data never leaves your site.

### How it works

1. **Index** — Bot Marley crawls your posts, pages, custom post types, and attachments (PDF, DOC, and more) and stores them as vector embeddings in your WordPress database.
2. **Retrieve** — When a visitor asks a question, the plugin finds the most relevant content chunks using semantic similarity search.
3. **Answer** — The retrieved content is passed to the AI with strict instructions: answer only from what's provided. The visitor gets a grounded, accurate reply — in their own language.

### Features (Free)

**Widget**
- Floating chat launcher — customizable position, margins, and colors
- Two launcher icon styles: BotMarley (branded) and Classic (monochrome, takes your brand color)
- Bot name, welcome message, and footer text
- Widget language selector — 15 languages for all fixed widget texts (the AI always replies in the visitor's language)
- Show/hide on mobile, tablet, and desktop independently
- Mobile full-screen chat experience
- Privacy consent banner with configurable Privacy Policy link
- Source citations — show which pages were used to compose the answer
- Session-persistent conversation history
- Lead capture form with privacy checkbox
- Preview mode — test the widget on the live site before enabling it

**Knowledge**
- Index any post type (pages, posts, custom post types)
- Auto-sync — changed content is re-indexed automatically every hour
- Excluded URLs — prevent specific pages from being indexed or cited
- Contact information injected into the AI system prompt (email, phone, address) — authoritative, overrides anything found in the site content
- Important information pages: contact, booking, FAQ, Privacy Policy, Terms and Conditions URLs the AI can link naturally in answers

**Behaviour**
- Four personality tones: Professional, Neutral, Friendly, Witty
- Mandatory rules (built-in, always on): no legal/medical/financial advice, no sensitive personal data requests, never mention competitors, never negotiate prices
- Customizable objectives: what the bot should and shouldn't do
- Fallback message for when no relevant content is found
- Message limit per session and configurable max message length

**Settings**
- Compatible with the WordPress AI Services API (WP 7.0+)
- Configurable AI parameters: temperature, top-K retrieval chunks
- Test connection button to verify the AI provider is working
- Proxy/CDN-aware rate limiting (Cloudflare and similar)
- Automatic cache purge (WP Rocket, LiteSpeed, W3TC, SiteGround, and 8 more) when widget settings change

**Compatibility**
- WPML-ready: widget strings and page URLs are language-aware
- Works with any page builder (Elementor, Divi, Bricks, …)

---

### Features (Pro)

**WooCommerce AI** — the deepest e-commerce integration of any self-hosted WordPress chatbot:
- **Cart awareness** — the AI sees the visitor's live cart and helps complete the purchase ("what's in my cart?", "how much for free shipping?")
- **Order tracking** — logged-in customers can ask about their recent orders and shipping status
- **Product cards** — rich product previews with image, price, and Add to Cart button right in the chat
- **Coupon rules** — suggest the right coupon based on cart conditions (cart total, specific products, categories), with a 5-level "push" slider from discreet to proactive; expired coupons are skipped automatically
- **Product suggestions** — control which products or categories the AI promotes more, promotes less, or never mentions
- **WooCommerce objectives** — dedicated sales goals: guide purchases, reduce cart abandonment, upsell, explain shipping and returns

**Advanced Knowledge**
- Additional Knowledge files — add PDF and documents from the Media Library to the knowledge base, each with a custom note
- Attachment indexing — index PDF, DOC, and other media files automatically (WordPress 7.1+)
- WooCommerce product indexing — products, variations, and descriptions fully indexed and searchable
- ACF / custom fields indexing

**Analytics & Logs**
- Conversation log: see every question asked and every answer given
- Unanswered questions report — what visitors ask that your site doesn't cover
- Lead capture log with export

**Support**
- Priority email support
- 30-day money-back guarantee

### Pricing (Pro, billed annually)

| | 1 site | 3 sites | 15 sites |
|---|---|---|---|
| **Pro** | €69 / $69 | €129 / $129 | €199 / $199 |

Unlimited conversations on every plan — you only pay your own AI provider (or nothing, using the WordPress AI Services API credits). 20% renewal discount. Need more sites? Contact us.

---

## Installation

1. Upload the plugin to `/wp-content/plugins/bot-marley/` or install it from the WordPress plugin directory.
2. Activate the plugin through the **Plugins** menu in WordPress.
3. Go to **Bot Marley → Settings** and verify that an AI provider is configured via the WordPress AI Services API.
4. Go to **Bot Marley → Knowledge** and click **Reindex All Content** to build the knowledge base.
5. Go to **Bot Marley → Widget** and enable the widget. Adjust colors, position, and icon to match your brand.
6. Visit your site — the chat launcher should appear in the corner.

---

## Frequently Asked Questions

**Does it require an API key?**
Bot Marley uses the WordPress AI Services API (WP 7.0+), which manages API keys centrally. Configure your provider once in WordPress and all compatible plugins share it.

**How much do conversations cost?**
Nothing — conversations are unlimited on every plan, including Free. You only pay your own AI provider's API usage, typically a few euros per month even on busy sites. Compare that with SaaS chatbots charging per conversation or per credit.

**Does it hallucinate?**
No. Every response is strictly grounded in your indexed content. If the answer isn't in your site, the bot says it doesn't have that information rather than inventing one.

**Does it work in multiple languages?**
Yes. The bot detects the visitor's language from their question and responds accordingly. The widget interface is available in 15 languages, and WPML is fully supported.

**Where is the data stored?**
All vector embeddings and conversation data are stored in your own WordPress database. Nothing is sent to external servers except the AI API call (question + retrieved content chunks).

**What happens when I add new content?**
New posts and pages are indexed automatically when published or updated (hourly auto-sync). You can also trigger a full reindex manually from the Knowledge page at any time.

**Is it compatible with page builders?**
Yes. Bot Marley reads the final rendered content of your pages, so it works with Elementor, Divi, Beaver Builder, Bricks, and any other page builder.

**What happens if I don't renew my Pro license?**
Pro features keep working — you only lose updates and support. No lock-in.

---

## Changelog

### 0.7.1
- Attachment indexing (PDF, DOC, and more) — requires WordPress 7.1+ (Pro)
- Additional Knowledge files: add Media Library files to the knowledge base with a custom note (Pro)
- WooCommerce AI suite: cart awareness, order tracking, product cards, coupon rules with push level, product suggestions (Pro)
- Widget language selector with 15 languages
- Hourly auto-sync of changed content
- Universal cache purge on widget settings save
- Preview mode for admins
- Mobile full-screen chat panel
- Proxy/CDN-aware rate limiting
- FAQ, Privacy Policy and Terms and Conditions page URLs in Knowledge

### 0.2.x
- Submenu pages: Settings, Widget, Knowledge, Behaviour
- Hide widget on mobile/tablet/desktop
- Lead capture form with privacy checkbox
- Source citations
- WPML compatibility
- Session-persistent conversation history

---

## About

Bot Marley is built by [BigFive Agency](https://bigfive.it) — a web agency specializing in WordPress, AI integrations, and digital strategy.

Pro licenses and support: [plugins.bigfive.cloud](https://plugins.bigfive.cloud)
