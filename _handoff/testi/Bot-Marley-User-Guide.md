# Bot Marley — User Guide

A friendly, step-by-step guide to setting up your Bot Marley AI chatbot and getting the most out of it. No coding required — if you can edit a WordPress page, you can configure Bot Marley.

This guide is written for site owners. Follow it top to bottom the first time, then use it as a reference whenever you want to tweak something.

---

## 1. Welcome to Bot Marley

Bot Marley is a self-hosted AI chatbot that turns your website into a smart assistant. It reads your own pages and posts and answers visitors' questions using only what's actually on your site — so it stays accurate and on-topic.

Because it's self-hosted, your content and conversations stay in your WordPress site, and you connect your own AI provider. There are no per-conversation fees: you only pay your AI provider for what you use.

**What it's great at:** answering "how much does X cost?", "do you ship to…?", "what's your return policy?", guiding shoppers, and capturing leads — 24/7, in the visitor's own language.

---

## 2. What you need before you start

Setting up takes about 10 minutes. Here's the short checklist so nothing blocks you halfway through.

You'll get the smoothest experience if you have these ready before you begin.

- **WordPress 7.0 or newer** (7.1+ unlocks smarter, meaning-based search and document indexing).
- **An AI provider account** — OpenAI, Anthropic (Claude), or Google — with **billing/credit active**. A key without billing is the single most common cause of "the bot won't answer".
- **A Privacy Policy page** on your site (required before the chat can go live — it powers the consent notice).
- **WooCommerce** *(optional)* — only if you run a shop and want the Pro sales features.

> **Good to know:** Bot Marley never stores your API keys. You connect your provider once in WordPress (**Settings → Connectors**) and every compatible plugin shares it safely.

---

## 3. Quick start: go live in 3 steps

If you just want the bot running fast, these are the only three things you must do. Each one has its own detailed section below.

Do them in order — the widget won't switch on until the first two are done.

1. **Connect your AI** in **Settings → Connectors** (see [Section 4](#connect)).
2. **Build the knowledge base** — pick what to index and run the first indexing (see [Section 5](#knowledge)).
3. **Turn on the widget** and match it to your brand (see [Section 6](#widget)).

That's it — open your site and the chat launcher appears in the corner.

---

<a id="connect"></a>
## 4. Step 1 — Connect your AI

Bot Marley doesn't come with its own AI; it uses the provider you choose. This keeps you in control of costs, data location, and which model answers your visitors.

You only do this once. After it's connected, everything else in Bot Marley just works.

**How to connect:**

1. Go to **Settings → Connectors** in WordPress.
2. Choose a provider (OpenAI, Anthropic, or Google) and paste a valid **API key**.
3. Make sure that account has **active billing or prepaid credit** — most providers won't answer a single request without it.

Back in **Bot Marley → Settings**, the **Status** line confirms the connection is detected. You can optionally pin a specific provider there, or leave it on **Site default** and let WordPress decide.

> **Tip:** Prefer to keep data in a specific region (for example the EU)? Choose a provider that offers it — you control which one Bot Marley talks to.

---

<a id="knowledge"></a>
## 5. Step 2 — Build your knowledge base

The knowledge base is everything the bot is allowed to know. Bot Marley reads the content you select and uses **only** that to answer — so a good knowledge base means good answers.

Spend a couple of minutes here and you'll dramatically cut the questions that reach your inbox. This is all on the **Bot Marley → Knowledge** page.

### Choose what to index

Pick which content feeds the bot. Posts and pages are included by default; add custom post types, and — on WP 7.1+ — uploaded PDFs and documents.

- **Auto-sync content changes** — keep this **ON** so new and edited pages are picked up automatically (checked hourly). Set it and forget it.
- **Reindex All Content** — run this after big changes to rebuild everything from scratch.
- **Reviews and comments are never indexed** — on purpose, for your safety, since anyone could post text there to trick the bot.

### Add your contact details

Fill in your **email, phone, and address** here. When set, these **override anything found in your content**, so the bot always shares the right, up-to-date contacts and never an old number buried in an old post.

### Point to your important pages

Tell the bot where your **Contact, Booking, Cart, FAQ, Return Policy, Terms, and Privacy Policy** pages live. A handy "pick page" button lets you select them instead of typing URLs.

The **Privacy Policy** is special: it's required, and it's the link shown in the consent notice above the chat.

---

<a id="widget"></a>
## 6. Step 3 — Turn on and style the widget

The widget is the chat bubble your visitors see. Here you switch it on and make it feel like part of your brand. Everything is on the **Bot Marley → Widget** page.

Take a minute to match your colours and welcome message — a personalised widget gets far more use than a generic one.

### Switch it on

- **Show on frontend** — the master on/off. (It needs your Privacy Policy URL first.)
- **Preview on site** — opens your site with the widget forced on, so you can test before going live.
- **Hide on device** — show or hide it independently on mobile, tablet, and desktop.
- **Open automatically** — pop the chat open after a few seconds, if you like.

### Make it yours

- **Position & margins** — bottom-right or bottom-left, with pixel-perfect spacing.
- **Bot name & welcome message** — the first thing visitors read. Leave the welcome empty to use a ready-made one in the widget's language.
- **Theme colours** — a primary colour (header, buttons, launcher) and a secondary colour for text on top of it.
- **Launcher icon** — the friendly Bot Marley face or a classic chat bubble.
- **Footer text** — a small line under the input (supports bold, italics, links).

### Control where it appears

- **Show sources** — display the pages each answer came from, so visitors can double-check.
- **Hide on URLs / post types** — keep the widget off specific pages (like checkout) or entire content types.

---

## 7. Shaping how the bot talks (Behaviour)

The Behaviour page sets your bot's personality and its do's and don'ts. It's how you make the assistant sound like *your* brand while staying accurate.

Whatever tone you pick, the golden rule never changes: the bot answers only from your content and never makes things up. Find it under **Bot Marley → Behaviour**.

- **Personality** — choose **Professional, Neutral, Friendly, or Witty**.
- **Objectives** — a simple grid where you mark goals **green (do this)**, **red (never do this)**, or **grey (no instruction)** — for example "encourage newsletter sign-ups" or "never discuss competitors".
- **Fallback message** — what the bot says when the answer genuinely isn't on your site. Leave it empty for a polished default that invites the visitor to get in touch.

---

## 8. Capturing leads

Bot Marley can turn a conversation into a contact. When the bot suggests getting in touch, a short form appears right inside the chat — no extra plugin needed.

Every submission is emailed to you with the conversation, so you have full context to follow up. You configure this on the **Widget** page.

- **Lead capture** — switch the in-chat form on.
- **Show form after** — wait for a couple of messages before offering it, so it never feels pushy.
- **Notification email** — where new leads land (defaults to your admin email).
- **Form fields** — decide which of name, company, email, and phone are **required, optional, or off**.
- **Title & thank-you message** — personalise both, with per-language versions if you serve multiple languages.

---

## 9. Speaking your visitors' language

Bot Marley is multilingual out of the box. The AI always replies in the language the visitor writes in, and the widget's fixed texts (buttons, consent notice) can follow your site language automatically.

If you run a multilingual site with WPML, Polylang, TranslatePress, or Weglot, this all happens without extra work.

- Set **Widget language** to **Site language (auto-detect)** to follow your site, or pin one specific language.
- **15 languages** are supported for the interface: English, Italian, Spanish, French, German, Portuguese, Dutch, Polish, Russian, Turkish, Arabic, Chinese, Japanese, Korean, and Greek.
- Want different wording per language? Next to the welcome, fallback, and lead-form texts there's an **Edit translations** link where you can fine-tune each language. Any language you don't customise falls back to its own clean default — never to another language.

---

## 10. Selling with WooCommerce (Pro)

If you run a shop, the Pro WooCommerce integration turns Bot Marley into a sales assistant that actually helps close the sale. It's the deepest shop integration of any self-hosted WordPress chatbot.

Everything below lives under **Bot Marley → WooCommerce** and needs WooCommerce plus a Pro licence.

- **Cart awareness** — the bot sees the live cart and can help finish the order ("how much more for free shipping?").
- **Order tracking** — logged-in customers can ask "where's my order?" and get the status of their recent orders.
- **Product cards** — when the bot mentions a product, it shows a card with image, price, and an **Add to Cart** button.
- **Smart coupons** — offer the right coupon based on the cart (total, specific products, or categories), with a 1–5 "push" level from discreet to proactive. Expired coupons are never suggested.
- **Product suggestions** — tell the bot which products or categories to promote **more, less, or never**.
- **Sales objectives** — dedicated goals like "reduce cart abandonment" or "upsell related products", using the same green/red/grey grid as the Behaviour page.

---

## 11. Fine-tuning answers & limits (Settings)

Most sites never need to touch these, but a few knobs let you balance answer quality against cost. They're on the **Bot Marley → Settings** page.

Start with the defaults — they're sensible — and adjust only if you have a reason to.

| Setting | What it does | Suggested |
|---|---|---|
| **Retrieved chunks (top-k)** | How much of your content the bot reads per question. Higher = more thorough, but costs more. | Default **5** |
| **Temperature** | How creative the wording is. Lower = more factual and on-brand. | Default **0.2** |
| **Max messages per session** | Caps messages per visitor to prevent abuse. **0 = unlimited.** | Set a limit on busy sites |
| **Max message length** | Longest single message a visitor can send. | Default **280** |

> **Watching costs?** Lower **top-k**, set a **max messages per session**, and keep **temperature** low. These three together keep your AI bill predictable.

---

## 12. Measuring results (Statistics, Pro)

The Statistics dashboard shows how your chatbot is performing, so you can see what's working and where visitors get stuck. It's available with a Pro licence under **Bot Marley → Statistics**.

Use it to spot the questions you should answer better on your site — and, if you run a shop, to see what the bot earned.

- **Key numbers** — total conversations, how often the chat is opened, engagement rate, and how often the bot had no answer (fallback rate).
- **Trends** — activity by day and by hour, so you know when your visitors chat.
- **Top pages** — where conversations start most often.
- **Shop impact** *(WooCommerce)* — leads captured, products suggested, coupons used, and orders the chat helped along.

---

## 13. Your data & privacy

Bot Marley is built to keep you in control of your data. Your knowledge base and chat history stay in your own WordPress database — there's no third-party chatbot company holding your information.

The only thing sent outside your site is the AI request itself (the visitor's question plus the relevant snippets of your content), which goes to the AI provider **you** chose and control.

- **Your keys stay in WordPress**, never in the plugin.
- **Answers are grounded in your content** — the bot won't wander off into outside knowledge.
- **Visitors are informed** — a consent notice (linking your Privacy Policy) tells them they're chatting with an AI.
- **Choose a compliant provider** — for stricter needs (e.g. EU data residency), pick an AI provider that offers it and sign your agreement with them directly.

---

## 14. Troubleshooting (self-help)

Before you contact support, check here — the vast majority of setup hiccups are one of these, and each has a quick fix.

Work through the symptom that matches, and you'll usually be back up and running in under a minute.

**"The AI Client is not available."**
You're either below WordPress 7.0 or haven't connected a provider yet. Add a valid key under **Settings → Connectors**.

**The bot gives empty answers or always uses the fallback.**
Two usual causes: indexing hasn't run (open **Knowledge** and check there's a content count), or your AI account has no active billing/credit. Fix both and re-test.

**The widget won't switch on.**
Set a **Privacy Policy URL** on the Knowledge page — it's required before the chat can go live.

**I updated a page but the bot doesn't know.**
Turn on **Auto-sync content changes**, or click **Reindex All Content** after major edits.

**The bot gave an old phone number or email.**
Fill in the **Contact Information** fields on the Knowledge page — they override anything in your content.

**My AI bill is higher than expected.**
Lower **top-k**, set a **max messages per session**, and keep **temperature** low (see [Section 11](#11-fine-tuning-answers--limits-settings)).

---

*Still stuck after all this? That's exactly what support is for — reach out from your customer portal and we'll help.*
