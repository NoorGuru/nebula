---
title: "Sawt Receptionist answers clinic phones in Egyptian Arabic"
summary: "A dialect-fluent voice receptionist two people would assemble from speech APIs: it answers a clinic's phone and WhatsApp voice notes in Egyptian Arabic, books and reschedules appointments, and logs every call — so a small practice never misses a booking again."
tags: ["garage", "egypt", "healthtech", "ai"]
featured: false
publishedAt: 2026-10-06
country: "Egypt"
sector: "saas"
stage: "idea"
status: "idea"
coreProblem: "Small Egyptian clinics lose bookings because the phone rings while the doctor is with a patient and there is no receptionist — callers hang up and book elsewhere."
howItWorks: "One business phone number (PSTN via a SIP provider, plus a WhatsApp Business number) fronts the clinic. Inbound calls go to a speech-to-speech voice agent prompted with the clinic's schedule, services, and prices; it speaks Egyptian Arabic, offers free slots, confirms bookings by SMS/WhatsApp, and writes everything to a shared calendar. WhatsApp voice notes get transcribed and answered the same way, in text."
buildCost: "~$10-20k to first paying clinic: API usage, two phone numbers, and ~2 months of two builders' time; no model training, only API assembly."
techStack: "OpenAI Realtime API (speech-to-speech) or Chat Completions audio input for WhatsApp voice notes; Azure Speech ar-EG voices as fallback; SIP trunk + WhatsApp Business Platform; hosted calendar (e.g. Cal.com/Calendly API or Google Calendar)."
firstCustomer: "Private dental and dermatology clinics in Cairo/Giza with 1-2 chairs and no full-time receptionist — they already lose ~5-15 calls a day and can prepay a monthly answering fee before the product is finished."
whyNow: "OpenAI Realtime API public beta, Oct 2024 (GA Aug 2025) — natural speech-to-speech from a single API call, no stitched ASR/LLM/TTS pipeline; plus Azure Speech shipping Egyptian Arabic (ar-EG) neural voices."
challenges: "Egyptian dialect + clinic noise still mistranscribes names and drug terms — needs a confirmation loop ('press 1 to confirm'); doctors must trust it with their schedule, so the first version needs human review of every booking; and call quality on Egyptian mobile networks can break real-time audio latency budgets."
sources:
  - title: "OpenAI — Introducing the Realtime API (public beta, Oct 1, 2024; GA Aug 28, 2025)"
    url: "https://openai.com/index/introducing-the-realtime-api/"
  - title: "Microsoft Learn — Azure Speech language support (ar-EG Salma/Shakir neural voices)"
    url: "https://learn.microsoft.com/en-us/azure/ai-services/speech-service/language-support?tabs=stt"
  - title: "Meta docs — WhatsApp Business Platform pricing (per-message since Jul 1, 2025; in-window replies free)"
    url: "https://developers.facebook.com/docs/whatsapp/pricing/"
summaryAr: "موظفة استقبال صوتية تتحدث العامية المصرية ترد على هواتف العيادات ورسائل واتساب الصوتية وتحجز المواعيد حتى لا يضيع أي حجز."
---

## The problem

A two-chair dental clinic in Cairo misses most calls between 6 and 10pm — exactly when working patients call to book. Hiring a full-time receptionist costs more than the missed bookings feel worth, so the phone just rings out and the patient books the clinic across the street.

## The build

Two people assemble it, they don't invent it: a SIP number for the clinic's published phone line, a WhatsApp Business number for voice notes, a speech-to-speech agent primed with the doctor's slots and price list, and a shared calendar as the source of truth. The agent answers in Egyptian Arabic, negotiates a time, sends a WhatsApp confirmation, and flags uncertain bookings for the doctor to glance at each morning. Nothing is trained — it is prompting, call routing, and calendar glue.

## Why now

Three years ago this needed a custom Arabic-dialect ASR pipeline, a dialogue manager, and a TTS voice nobody had — a research project. The Realtime API's public beta (Oct 2024, GA Aug 2025) collapsed that into one API call, and Azure now ships Egyptian Arabic neural voices (ar-EG) off the shelf, so the dialect half is bought, not built.

## First customer

Private dental and derma clinics in Greater Cairo: visible missed-call pain, a named payer (the doctor-owner), and a fee smaller than one receptionist salary. Offer: we answer every call for a flat monthly fee, starting with one pilot clinic that prepays month one.

## Challenges

Dialect transcription of proper names under street noise will be wrong sometimes — the confirmation loop is the product, not a detail. Latency on real mobile calls can make the agent feel drunk; the pilot must be measured on real lines, not demos. And trust: one double-booked root canal undoes ten perfect weeks, so every booking stays human-glanceable until the error rate earns autonomy.
