---
title: "DukkanLedger turns receipt photos on WhatsApp into shop books"
summary: "A WhatsApp number small-shop owners send receipt and invoice photos to — it reads each one, logs the expense, and answers plain questions like what the shop spent this week."
tags: ["garage", "egypt", "fintech", "retail-tech"]
featured: false
publishedAt: 2026-10-06
country: "Egypt"
sector: "retail-tech"
stage: "idea"
status: "idea"
coreProblem: "Corner shops and kiosks run on paper receipts stuffed in drawers — the owner has no running picture of spending, stock costs, or who they paid, so margins leak silently."
whyNow: "GPT-4o mini (Jul 2024) reads images plus text for ~15¢ per million input tokens, and WhatsApp replies inside a user-opened chat window cost the business nothing (Meta per-message pricing, Jul 2025)."
buildCost: "~$10–20k to first paying shops: two people assembling the WhatsApp Cloud API, a vision model, and a ledger database — inference runs cents per receipt and in-window chat replies are free."
techStack: "WhatsApp Cloud API + GPT-4o mini vision (Arabic-tolerant tokenizer) + a simple per-shop ledger store with weekly totals."
firstCustomer: "Cairo and Giza kiosk and corner-shop owners who already photograph supplier receipts for their own records — they pay a small monthly fee to stop doing the arithmetic themselves."
howItWorks: "The shop saves the DukkanLedger number and sends photos of purchase receipts and supplier invoices as they arrive. The model extracts amount, date, and supplier from each image — including Arabic handwriting — appends it to the shop's ledger, and replies with a running total. The owner can ask in Arabic how much went to one supplier this month or what the week cost, and gets a plain answer."
challenges: "Messy inputs — crumpled receipts, faded ink, mixed Arabic and numerals — will misread, and every error lands on money, so trust is fragile. WhatsApp template-message rules and spam limits constrain how the bot can re-engage quiet shops. And the glorious-failure trap: the wedge is thin bookkeeping, and graduating from a chat log to figures an accountant or the tax office accepts is a second product entirely."
sources:
  - title: "GPT-4o mini: advancing cost-efficient intelligence"
    url: "https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/"
  - title: "Pricing on the WhatsApp Business Platform"
    url: "https://developers.facebook.com/docs/whatsapp/pricing/"
summaryAr: "رقم واتساب يرسل إليه أصحاب المحلات صور الفواتير فيسجّل المصروفات ويجيب عن أسئلة بسيطة حول إنفاق المتجر."
---

## The problem

A kiosk owner buys stock daily and keeps the proof in a drawer. At month's end nobody knows what the shop spent, which supplier got paid most, or whether the business actually made money.

## The build

One WhatsApp number. The owner sends receipt and invoice photos as they come in; each is read, logged with amount, date, and supplier, and confirmed with a short reply and running total. Questions in Arabic — what did the week cost, what went to the milk supplier — get plain answers from the ledger.

## Why now

Two dated shifts make the unit economics work. GPT-4o mini (July 2024) reads images and text in one call at about 15 cents per million input tokens, with a tokenizer built to handle non-English text cheaply. And Meta's WhatsApp pricing (effective July 2025) charges per template message while replies inside a user-opened 24-hour chat window are free — exactly the shape of a shop sending photos and getting answers.

## First customer

Kiosk and corner-shop owners in Cairo and Giza who already photograph supplier receipts for their own records. They feel the paperwork pain weekly, need no new app, and pay a small monthly fee before the product is polished because it replaces arithmetic they do by hand.

## Challenges

Crumpled paper, faded ink, and handwritten Arabic will misread, and each mistake touches money. WhatsApp's messaging rules limit re-engaging silent shops. And the ledger a chat produces is not yet books an accountant would sign — closing that gap is a second product.
