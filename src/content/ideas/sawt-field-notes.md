---
title: "Sawt Field Notes turns reps' voice notes into job records"
summary: "A WhatsApp number two people would wire to speech and structuring APIs: field sales reps dictate a 30-second voice note in Saudi dialect after each visit, and it files a visit record, restock order, or complaint ticket — no app to install, no forms to type."
tags: ["garage", "ksa", "saas", "ai"]
featured: false
publishedAt: 2026-10-06
country: "Saudi Arabia"
sector: "saas"
stage: "idea"
status: "idea"
coreProblem: "Van salesmen and field reps visit 20-30 shops a day and report nothing — end-of-day paperwork never happens, so distributors can't see which shelves are empty or which shop asked for what."
howItWorks: "The distributor gives reps one WhatsApp number. After each visit the rep sends a voice note ('Al-Othaim branch 4, milk running low, wants 20 cartons Thursday'). The service transcribes it with Saudi-dialect speech recognition, structures it into a visit record/order/complaint via a language model, and drops it into a shared sheet or simple dashboard; the rep gets a one-line confirmation back. Managers see visits, orders, and gaps the same day."
buildCost: "~$8-15k to first paying distributor: API usage, WhatsApp Business number, and ~6-8 weeks of two builders' time; no mobile app, no model training."
techStack: "WhatsApp Business Platform for capture; Azure Speech ar-SA transcription (or Chat Completions audio input, Oct 2024) for async voice notes; a language model for structuring; Postgres + a minimal dashboard."
firstCustomer: "FMCG and building-materials distributors in Riyadh/Jeddah running 5-50 van salesmen — the sales manager already begs for visit reports on WhatsApp and will prepay per-rep monthly to get them structured."
whyNow: "Audio input/output in OpenAI's Chat Completions API, Oct 2024 — async voice-note transcription and structuring in one request/response call, no realtime session needed; plus Azure Speech shipping Saudi Arabic (ar-SA) recognition and neural voices."
challenges: "Saudi dialect + product brand names + van-engine background noise is the hardest transcription setting — needs per-distributor vocabulary lists (brand names, shop names) to be usable; reps must actually send the notes, so the confirmation reply has to be instant and useful or the habit dies in week two; and WhatsApp template-message rules mean outbound nudges outside the service window cost per message."
sources:
  - title: "OpenAI — Introducing the Realtime API (notes Oct 17, 2024: audio in Chat Completions API)"
    url: "https://openai.com/index/introducing-the-realtime-api/"
  - title: "OpenAI docs — Realtime API guide (speech-to-speech, tool use, session model)"
    url: "https://developers.openai.com/api/docs/guides/realtime"
  - title: "Microsoft Learn — Azure Speech language support (ar-SA recognition + neural voices)"
    url: "https://learn.microsoft.com/en-us/azure/ai-services/speech-service/language-support?tabs=stt"
  - title: "Meta docs — WhatsApp Business Platform pricing (per-message since Jul 1, 2025; in-window replies free)"
    url: "https://developers.facebook.com/docs/whatsapp/pricing/"
summaryAr: "رقم واتساب يحوّل الرسائل الصوتية لمندوبي المبيعات باللهجة السعودية إلى سجلات زيارات وطلبات بضاعة دون أي تطبيق أو نماذج ورقية."
---

## The problem

A Jeddah food distributor's vans visit hundreds of baqalas a week and management learns about stock-outs when the shop calls angry. Reps won't fill CRM forms on their phones between stops — the data simply never gets captured, and the distributor flies blind on its own shelves.

## The build

No app, no training, no hardware: one WhatsApp number, transcription tuned with the distributor's brand and shop names, a structuring prompt that outputs visit/order/complaint records, and a dashboard the sales manager already checks. The rep's whole job is a 30-second voice note per stop — the lowest-friction reporting interface that exists, because it is the app they already live in. Two people build it from APIs in under two months.

## Why now

Three years ago dialect speech recognition meant either MSA-only models that mangled Saudi speech or a custom data-collection project. Audio input in the Chat Completions API (Oct 2024) made async voice-note understanding a single call, and Azure ships Saudi Arabic (ar-SA) recognition plus neural voices for the confirmation replies — so the whole loop is bought infrastructure.

## First customer

A Riyadh or Jeddah FMCG/building-materials distributor with 5-50 van salesmen: the sales manager is a named payer with a daily reporting headache, reps already use WhatsApp voice notes socially, and per-rep-per-month pricing is trivially below one lost shelf-week. Pilot: one 10-rep team, prepaid, measured on % of visits reported.

## Challenges

Transcription accuracy on brand names shouted over a van engine is make-or-break — launch with a per-customer vocabulary list, not generic models. Adoption is behavioral: if the confirmation reply is slow or useless, reps stop sending notes within days. And unit economics need discipline: outbound reminders outside WhatsApp's service window are charged per template message, so nudges must ride inside free reply windows or the margin leaks.
