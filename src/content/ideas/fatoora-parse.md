---
title: "Fatoora Parse turns supplier invoices into ZATCA-ready e-invoices"
summary: "A developer API two people could build that reads Arabic paper invoices and supplier PDFs and returns structured line items mapped to Saudi ZATCA Phase 2 e-invoice fields."
tags: ["garage", "saudi arabia", "fintech", "saas"]
featured: false
publishedAt: 2026-10-06
country: "Saudi Arabia"
sector: "fintech"
stage: "idea"
status: "idea"
coreProblem: "Small Saudi businesses receive supplier invoices as paper scans, photos, and mixed Arabic-English PDFs, but ZATCA Phase 2 forces their systems to transmit structured, integrated e-invoices — someone has to bridge the paper pile to the Fatoora platform."
howItWorks: "Shop owner forwards an invoice photo to an endpoint; Mistral OCR extracts ordered text and tables; a small mapping layer assigns buyer, seller, VAT, and line items to ZATCA fields and returns JSON the customer's system posts to Fatoora."
challenges: "ZATCA rejects malformed invoices, so accuracy below ~99% creates support load; Arabic handwriting and stamp-covered scans still defeat OCR; and every accounting suite will eventually ship this as a checkbox feature."
buildCost: "~$10-20k: Mistral OCR at ~$1 per 1,000 pages plus a small model for field mapping, one VPS, and WhatsApp/email intake."
techStack: "Mistral OCR API (mistral-ocr-latest) for extraction, a small LLM for field mapping, ZATCA Fatoora sandbox for validation."
firstCustomer: "Independent Saudi accounting offices onboarding wave-20+ SMEs — they pay per hundred invoices converted because each rejected filing costs them client trust."
whyNow: "Mistral OCR API, Mar 2025 — multilingual document OCR at ~$1 per 1,000 pages; ZATCA 22nd wave (Mar 2025) pulled firms above SAR 1m turnover into Phase 2 with a Dec 2025 deadline."
sources:
  - title: "Mistral OCR announcement (Mistral AI)"
    url: "https://mistral.ai/news/mistral-ocr/"
  - title: "Saudi Arabia announces 22nd wave of Phase 2 e-invoicing integration (EY)"
    url: "https://taxnews.ey.com/news/2025-0759-saudi-arabia-announces-22nd-wave-of-phase-2-e-invoicing-integration"
summaryAr: "واجهة برمجية يبنيها شخصان تحوّل صور الفواتير الورقية العربية إلى بيانات منظمة جاهزة لمنصة فاتورة السعودية."
---

## The problem

Thousands of small Saudi firms must now integrate with ZATCA's Fatoora platform, but their inbound paperwork is still paper: supplier invoices photographed in warehouses, stamped PDFs, mixed Arabic-English line items. Somebody has to turn that pile into structured fields.

## The build

A single API endpoint. Send it an invoice photo or PDF; it returns buyer, seller, VAT number, and line items mapped to ZATCA Phase 2 fields as JSON. Intake over WhatsApp and email for shops with no IT. Two people assemble it from an OCR API, a field-mapping model, and the Fatoora sandbox for validation.

## Why now

In March 2025 Mistral released its OCR API at roughly $1 per 1,000 pages with native multilingual support — Arabic table extraction became a commodity call. The same month, ZATCA's 22nd wave pulled every firm above SAR 1 million turnover into Phase 2 integration, with compliance due by December 2025. Cheap Arabic OCR met a hard regulatory deadline.

## First customer

Independent accounting offices in Riyadh and Jeddah onboarding wave-hit SMEs. They already do this conversion by hand and lose money on every rejected filing — a per-invoice API they can resell to fifty clients is an easy yes before it is finished.

## Challenges

ZATCA rejects malformed invoices, so anything below near-perfect accuracy becomes a support treadmill. Handwritten Arabic and stamp-covered scans still break extraction. And this is a feature, not a company: every accounting suite adds it as a checkbox within two years, so the window is a wedge, not a moat.
