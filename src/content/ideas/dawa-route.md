---
title: "Dawa-Route sends prescription refills to the cheapest nearby pharmacy"
summary: "A WhatsApp refill router for chronic patients: the patient photographs the prescription, a vision model reads what needs refilling, and the order goes to the cheapest nearby pharmacy with stock — delivery or pickup, no price-hunting phone calls."
tags: ["garage", "saudi arabia", "healthtech"]
featured: false
publishedAt: 2026-10-06
country: "Saudi Arabia"
sector: "healthtech"
stage: "idea"
status: "idea"
coreProblem: "Chronic patients in Riyadh refill the same drugs every month but prices and stock vary pharmacy to pharmacy — so families call around, overpay, or skip doses when a drug is 'out of stock' two streets away."
howItWorks: "The patient (or a family member) sends a photo of the prescription or the empty box to a WhatsApp number. A Flash-class vision model extracts the drug names, doses, and quantities, then matches them against a small per-pharmacy stock-and-price table for the patient's district. The order routes to the cheapest pharmacy that has everything in stock; the patient confirms with one reply, and the pharmacy delivers or holds for pickup. Repeat refills re-trigger monthly with a single confirmation."
challenges: "Drug names are safety-critical — a misread dose routes the wrong medicine, so every extraction needs a pharmacist confirmation step before the pilot scales, and controlled drugs stay out of scope entirely. Pharmacy stock tables go stale fast; the build must make updating stock a 30-second daily habit for the pharmacist, not a dashboard they ignore. Price data also needs a per-city table, not model memory."
buildCost: "~$12-18k: WhatsApp Cloud API (confirmations free inside the 24h window), Flash vision at ~$0.30/1M input tokens for prescription photos, Maps-grounded pharmacy lookup (500 free requests/day, then ~$25/1,000), one pharmacist reviewer for the pilot's extraction queue."
techStack: "WhatsApp Cloud API + Gemini 2.5 Flash vision via API (prescription photo reading) + Gemini Grounding with Google Maps (nearby pharmacy lookup) + a per-district pharmacy stock-and-price table + a pharmacist review queue."
firstCustomer: "Independent pharmacies in Riyadh residential districts — they pay a monthly fee per confirmed refill routed to them because each routed chronic patient is a repeat buyer for years, cheaper than any ads they currently run."
whyNow: "Flash vision reads printed prescriptions at ~$0.30/1M input tokens with a free tier (Google AI pricing, 2026) + Maps grounding for nearby-pharmacy lookup with 500 free requests/day (2025); WhatsApp confirmations inside the 24h window are free (Meta per-message pricing, effective Jul 2025)."
sources:
  - title: "Gemini Developer API pricing"
    url: "https://ai.google.dev/pricing"
  - title: "Pricing on the WhatsApp Business Platform"
    url: "https://developers.facebook.com/docs/whatsapp/pricing"
summaryAr: "خدمة واتساب لمرضى الأمراض المزمنة في السعودية: يرسل المريض صورة الوصفة فيوجه الطلب إلى أقرب صيدلية متوفر فيها الدواء بأرخص سعر."
---

## The problem

A hypertension patient in Riyadh takes the same three drugs every month. This month one box costs more at the usual pharmacy; another is out of stock. The family calls four pharmacies, or just pays extra, or the dose gets skipped for a week. The information exists — stock and price per pharmacy — but nobody aggregates it, so every refill is a small scavenger hunt.

## The build

Two people ship a WhatsApp number for refills. The patient sends a photo of the prescription or the empty box. A vision model reads the drug names, doses, and quantities, checks a stock-and-price table for pharmacies in the patient's district, and proposes the cheapest one with everything in stock. One reply confirms; the pharmacy delivers or holds the bag for pickup. Next month the same refill re-triggers with a single confirmation message — no new photo needed.

## Why now

Reading a prescription photo used to need a custom OCR pipeline and a pharmacy IT integration. Now a Flash-class vision model does the extraction at roughly thirty cents per million input tokens with a free tier, Maps grounding finds nearby pharmacies with hundreds of free lookups a day, and the confirmation chat back-and-forth on WhatsApp costs nothing inside the 24-hour window. The whole product is three APIs and one table.

## First customer

Independent pharmacies in Riyadh residential districts. A routed chronic patient refills monthly for years — lifetime value no flyer campaign can match. They pay a monthly fee per confirmed refill because the economics are legible from the first order, and the pilot starts with the five pharmacies around one clinic cluster.

## Challenges

A misread drug name is a safety failure, not a typo — every extraction passes a pharmacist review step until accuracy is proven, and controlled substances are excluded by policy from day one. Stock tables rot within days, so the pharmacist-facing update step must take thirty seconds or it dies. And prices differ by city and supplier, so the table is per-district truth, never model memory.
