---
title: "Mawid-Triage cuts clinic no-shows with a WhatsApp receptionist"
summary: "A WhatsApp receptionist for private clinics: it triages incoming appointment requests in Arabic, books them into the doctor's calendar, and chases confirmations the day before so empty slots get refilled."
tags: ["garage", "egypt", "healthtech"]
featured: false
publishedAt: 2026-10-06
country: "Egypt"
sector: "healthtech"
stage: "idea"
status: "idea"
coreProblem: "Private clinics lose real revenue to no-shows — a receptionist books by phone, nobody confirms the day before, and the doctor sits idle while the waiting list never gets called."
howItWorks: "The clinic forwards its booking number to the bot. Patients message in Arabic (text or voice note); a Flash-class model classifies urgency, offers free slots from a shared calendar, and books. The evening before, it messages every booked patient for a yes/no; a 'no' or silence releases the slot to a waitlist automatically. The receptionist sees a one-screen day sheet, not a phone queue."
challenges: "Voice notes in Egyptian dialect are the hard part — misheard symptoms must fail safe into a human callback, never a confident wrong booking. Clinics also guard their patient lists, so the pilot must run on the clinic's own WhatsApp number with a written data promise. One missed urgent case destroys trust, so urgency language must always end with 'confirm with the clinic' rather than a diagnosis."
buildCost: "~$10-15k: WhatsApp Cloud API (non-template replies free inside the 24h customer window), Flash-Lite inference at ~$0.10/1M input tokens, one part-time Arabic speaker to review triage transcripts during the pilot."
techStack: "WhatsApp Cloud API + Gemini 2.5 Flash-Lite via API (Arabic text + voice-note transcription) + a shared calendar (Cal.com or Google Calendar) + a one-screen day-sheet web app."
firstCustomer: "Private dental and dermatology clinics in Cairo and Giza — 3-5 chair practices where one no-show a day is a visible hole in revenue; they prepay a monthly per-chair fee because the bot replaces missed-call losses from week one."
whyNow: "WhatsApp per-message pricing, effective Jul 2025 — non-template replies free inside the 24h window, utility templates free in-window; plus Flash-class Arabic inference at ~$0.10/1M input tokens with a free tier (Google AI pricing, 2026)."
sources:
  - title: "Pricing on the WhatsApp Business Platform"
    url: "https://developers.facebook.com/docs/whatsapp/pricing"
  - title: "Gemini Developer API pricing"
    url: "https://ai.google.dev/pricing"
summaryAr: "موظفة استقبال عبر واتساب للعيادات الخاصة في مصر: تفرز طلبات الحجز بالعربية وتؤكد المواعيد مسبقًا لتقليل الغياب وملء المواعيد الشاغرة."
---

## The problem

A Cairo dental clinic books twenty patients by phone and sees fourteen. Nobody confirms the day before. The receptionist spends her morning answering calls instead of recalling the waiting list. The doctor's idle hour is gone money — and the patients who would have paid for it never hear the slot opened.

## The build

Two people ship a WhatsApp number that acts as the clinic's receptionist. Patients write or send voice notes in Arabic. The model sorts routine bookings from urgent ones, offers open slots from the clinic's calendar, and writes the booking down. The evening before each appointment it asks for a yes or no. A no — or silence — frees the slot and messages the waitlist first-come-first-served. The clinic staff get a single day-sheet screen: who is coming, who cancelled, which slots refilled.

## Why now

Two price drops make this a software assembly job. Since July 2025 Meta charges per template message, but the back-and-forth that matters — patient replies inside the 24-hour window — is free, as are utility confirmations sent in-window. And Flash-class models now read and transcribe Egyptian Arabic at roughly ten cents per million input tokens, with a free tier for the pilot. Three years ago the same bot would have needed a call center and a dialect speech team.

## First customer

Private dental and dermatology clinics in Cairo and Giza with three to five chairs. Their pain is countable: each empty chair-hour has a price, and the owner sees it daily. They prepay a monthly per-chair fee because the bot starts recovering revenue in its first week — one saved no-show covers the month.

## Challenges

Dialect voice notes will be misheard; the design must fail into a human callback, never a confident wrong booking. The bot must never diagnose — urgency wording always ends with confirming at the clinic. And patient lists are sensitive, so the pilot runs on the clinic's own WhatsApp number with a plain written promise about where messages go.
