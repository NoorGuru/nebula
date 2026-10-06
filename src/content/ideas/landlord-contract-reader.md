---
title: "AqdReader explains Arabic rental contracts to small landlords"
summary: "A chat tool small landlords send photos of Arabic rental contracts to — it returns the deal in plain words and flags the clauses that cost owners money: deposits, renewals, and exit terms."
tags: ["garage", "egypt", "proptech"]
featured: false
publishedAt: 2026-10-06
country: "Egypt"
sector: "proptech"
stage: "idea"
status: "idea"
coreProblem: "Small landlords with one or two flats sign Arabic rental contracts they never fully parse — deposit forfeits, auto-renewals, and vague maintenance duties surface only when a dispute already costs money."
whyNow: "GPT-4o (May 2024) brought flagship-level reading of images and text with sharply better non-English handling, and GPT-4o mini (Jul 2024) put that document reading at ~15¢ per million input tokens."
buildCost: "~$10–15k to first paying landlords: two people assembling a chat front end, a vision-capable model, and a clause checklist — each contract read costs cents in inference."
techStack: "WhatsApp or web chat front end + GPT-4o mini (Arabic document reading) + a fixed checklist of rental clauses every contract is scored against."
firstCustomer: "Cairo landlords renting out one to five flats who sign new contracts a few times a year — they pay per contract read because one flagged deposit clause repays the fee many times over."
howItWorks: "The landlord photographs each page of the Arabic rental contract and sends the photos in chat. The model transcribes the pages, restates the deal in plain words — rent, duration, deposit, who fixes what — and flags risky clauses against a fixed checklist: deposit forfeits, automatic renewal, unclear exit notice, and maintenance duties. The output is a short summary plus a list of questions to put to the tenant before signing."
challenges: "It is not a lawyer and must say so every time — over-trust is the real liability, and one bad reliance story kills the product. Handwritten amendments and stamped pages will misread. And demand is spiky: a landlord needs this a few times a year, so per-read pricing must carry a business with no daily habit."
sources:
  - title: "Hello GPT-4o"
    url: "https://openai.com/index/hello-gpt-4o/"
  - title: "GPT-4o mini: advancing cost-efficient intelligence"
    url: "https://openai.com/index/gpt-4o-mini-advancing-cost-efficient-intelligence/"
summaryAr: "أداة محادثة يرسل إليها الملاك الصغار صور عقود الإيجار العربية فتشرح بنودها بلغة بسيطة وتنبه إلى الشروط المكلفة قبل التوقيع."
---

## The problem

A landlord with two flats signs the same dense Arabic contract every tenant brings. The deposit clause, the renewal clause, and who pays for repairs stay unread until a dispute makes them expensive.

## The build

A chat tool that takes contract photos and returns two things: the deal in plain words (rent, duration, deposit, repair duties) and a flagged list of the clauses that historically cost small owners money — deposit forfeits, auto-renewal, exit notice, maintenance. Each contract is scored against the same fixed checklist, ending with questions to raise before signing.

## Why now

GPT-4o (May 2024) made image-plus-text reading with strongly improved non-English handling a commodity API capability, and GPT-4o mini (July 2024) dropped that document reading to about 15 cents per million input tokens. Reading a ten-page Arabic contract now costs cents — three years ago it took a lawyer's afternoon.

## First customer

Cairo landlords letting one to five flats who sign contracts a few times a year. They pay per contract read, need no legal literacy to use it, and one flagged deposit clause repays the fee many times over — the rare customer who profits before the product is finished.

## Challenges

Over-trust is the liability: the tool must declare it is not a lawyer on every read, because one landlord acting on a misread clause ends the business. Handwritten side-agreements and stamped pages misread most. And usage is spiky by nature — a few reads a year per landlord — so the price per read has to carry the whole business.
