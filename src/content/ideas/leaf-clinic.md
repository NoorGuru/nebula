---
title: "Leaf-Clinic diagnoses sick crops from a phone photo over WhatsApp"
summary: "A WhatsApp bot for Egyptian smallholders: the farmer sends a photo of a diseased leaf, a vision model identifies the disease and replies in Arabic with the treatment, dose, and when to spray."
tags: ["garage", "egypt", "agritech"]
featured: false
publishedAt: 2026-10-06
country: "Egypt"
sector: "agritech"
stage: "idea"
status: "idea"
coreProblem: "Egyptian smallholders lose a share of each harvest to misdiagnosed crop disease — the nearest agronomist is a bus ride away, pesticide dealers guess, and wrong sprays waste money while the disease spreads."
howItWorks: "Farmer sends a leaf photo to a WhatsApp number. A Flash-class vision model classifies the disease against public crop-disease references, then replies in Egyptian Arabic with the diagnosis, the treatment and dose, and spray timing. Uncertain cases escalate to a human agronomist queue. No app install, no account, no typing — just a photo."
challenges: "Vision misdiagnosis is the existential risk — a wrong pesticide recommendation costs a farmer real money and kills trust, so confidence thresholds and human escalation must be conservative. Scope must stay narrow (a few crops first). Pesticide labels change by market, so treatment advice needs a per-country label table, not model memory."
buildCost: "~$10-20k: WhatsApp Cloud API (farmer-initiated replies free in-window), vision inference at ~fractions of a cent per photo, one Arabic-speaking agronomist for the escalation queue and label table."
techStack: "WhatsApp Cloud API + Flash-class multimodal model via API + public crop-disease references (e.g. PlantVillage library) + a small per-market treatment table."
firstCustomer: "Tomato and wheat smallholders in the Nile Delta via agricultural input shops — dealers prepay seasonal diagnosis bundles because every correct diagnosis sells the right pesticide from their shelf."
whyNow: "Flash-class vision inference at ~$0.75/1M input tokens with a free tier (Google AI pricing, 2026) + WhatsApp non-template replies free inside the 24h customer window (Meta per-message pricing, effective Jul 2025)."
sources:
  - title: "Gemini Developer API pricing"
    url: "https://ai.google.dev/pricing"
  - title: "Pricing on the WhatsApp Business Platform"
    url: "https://developers.facebook.com/docs/whatsapp/pricing"
  - title: "PlantVillage — smallholder crop-health library and AI"
    url: "https://plantvillage.psu.edu/"
summaryAr: "خدمة واتساب للمزارع المصري: يرسل صورة لورقة مريضة فيصله التشخيص والعلاج بالعربية دون الحاجة إلى مهندس زراعي."
---

## The problem

A Delta tomato farmer spots yellow spots on Monday, asks the pesticide dealer on Tuesday, and sprays the wrong thing on Wednesday. The disease was early blight; the spray was for whitefly. By the time an agronomist sees the field, a fifth of the plot is gone. Extension agronomists exist but never at the right village on the right day.

## The build

Two people ship a WhatsApp number, not an app. The farmer photographs the sick leaf and sends it. A vision model returns: the likely disease, a confidence level, the registered treatment with dose per feddan, and whether to spray now or wait for cooler evening hours. Low-confidence photos route to a human agronomist who answers within hours. Launch scope is deliberately tiny: tomato and wheat, two governorates, one Arabic dialect.

## Why now

Two price curves crossed. Flash-class multimodal inference now costs on the order of $1 per million input tokens with a free tier — each photo diagnosis costs a fraction of a cent. And since July 2025, Meta's per-message WhatsApp pricing leaves farmer-initiated conversations effectively free: the photo comes in, the diagnosis goes back inside the 24-hour window, no per-message charge. Three years ago the same bot would have needed a custom-trained classifier and per-message fees that ate the margin.

## First customer

Nile Delta input dealers, not farmers directly. A dealer in Kafr El-Sheikh prepays a seasonal bundle of diagnoses and hands the WhatsApp number to every customer who walks in — because a correct diagnosis converts directly into the right product off his shelf. The farmer pays nothing; the dealer pays for footfall and fewer angry returns.

## Challenges

Trust is one bad recommendation away from zero, so the bot must say "I don't know, asking an agronomist" more often than its builders would like. Treatment tables must track Egyptian-registered pesticides only — model-hallucinated brand names are the failure mode. And dealers will push the bot toward recommending whatever they overstocked, so the escalation agronomist, not the dealer, must own the label table.
