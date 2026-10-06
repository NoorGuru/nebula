---
title: "Untether AI puts memory and compute on the same chip for faster AI inference"
summary: "Toronto startup building at-memory AI inference chips — memory and compute elements combined in one chip to kill the data-movement bottleneck of CPUs and GPUs, sold as runAI processors and accelerator cards for cars, machines, and edge devices."
tags: ["frontier", "canada", "semiconductors"]
featured: false
publishedAt: 2025-06-06
company: "Untether AI"
country: "Canada"
sector: "semiconductors"
founded: "2018"
amountRaised: "Over $150M total, incl. $125M round (Jul 2021)"
amountSource: "SiliconANGLE / TechCrunch"
valuationSource: "MISSING"
status: "acquired"
coreProblem: "In traditional servers compute and memory are separate, so running AI models means shuttling data back and forth — a movement bottleneck that costs energy, latency, and performance on every inference."
whyItWorked: "At-memory computation fuses memory and compute elements in the same chip, cutting the electricity needed for data transfers and delivering high-throughput, low-latency inference without sacrificing accuracy — a bet that efficiency, not raw training scale, wins edge and physical-AI workloads."
challenges: "Selling chips against entrenched GPU incumbents; the capital intensity of silicon development across multiple generations; and converting pilot deployments into volume orders — the company ultimately ended its independent run when AMD acqui-hired its engineering team in June 2025."
howItWorks: "Untether AI's runAI processors embed memory alongside compute on-die (at-memory computation) instead of keeping them in separate components. Neural-network weights stay where they are computed, so inference runs with far less data movement. The company packaged the silicon into accelerator cards — a single-server card with four runAI200 units was claimed to manage about 2 quadrillion operations per second — aimed at data-center, automotive, and edge deployments."
painPoints: "Data centers pay a power and latency tax on every AI query because of memory-to-processor transfers; cars, farm machines, and industrial devices need fast on-device inference without data-center power budgets; and buyers want alternatives to scarce, expensive incumbent accelerators."
businessModel: "Fabless semiconductor model — design at-memory inference chips and sell processors plus accelerator cards (runAI devices and tsunAImi-class cards) to automotive, industrial, and data-center customers, with software tooling around them."
hqCity: "Toronto"
usersMetrics: "Single-server accelerator card with four runAI200 units claimed at ~2 quadrillion operations per second with industry-leading power efficiency (company claim, Jul 2021)"
competitors: "Cerebras, Groq, Hailo and other AI-inference chipmakers, plus incumbent GPU vendors"
investors: "Intel Capital, Tracker Capital Management, Radical Ventures, CPP Investments"
sources:
  - title: "Intel co-leads $125M funding round for AI inference chip startup Untether AI"
    url: "https://siliconangle.com/2021/07/20/intel-co-leads-125m-funding-round-ai-inference-chip-startup-untether-ai/"
  - title: "AMD acqui-hires the employees behind Untether AI"
    url: "https://techcrunch.com/2025/06/06/amd-acqui-hires-the-employees-behind-untether-ai/"
summaryAr: "شركة كندية من تورونتو تصمّم رقائق ذكاء اصطناعي تجمع الذاكرة والحوسبة في شريحة واحدة لتسريع الاستدلال وخفض استهلاك الطاقة في السيارات والآلات والأجهزة الطرفية."
---

## The problem

Every AI query on a traditional server pays a movement tax: models live in memory, compute happens in the processor, and the ones and zeros travel back and forth constantly. That shuttling burns energy and adds latency — the exact bottleneck that makes fast, efficient inference hard, especially outside the data center.

## How it works

Untether AI bet on at-memory computation: fuse the memory and computing elements into the same chip so neural-network weights are processed where they sit. Its runAI processors and accelerator cards target inference (running trained models on live data), promising high throughput at a fraction of the data-movement energy — packaged for data centers, cars, and edge machines.

## Pain points

Cloud operators face soaring inference power bills; automakers and industrial buyers need on-device AI that works within tight power and latency budgets; and the market wants credible alternatives to incumbent accelerators on performance-per-watt.

## Business model

Fabless chip company: design the silicon in Toronto, sell processors and accelerator cards to enterprise, automotive, and industrial customers, and support them with inference software and collaborations (including an Arm Automotive Enhanced tie-up for vehicle workloads).

## Challenges

Silicon is brutally capital-intensive across generations; unseating incumbents requires not just better benchmarks but volume supply chains and software ecosystems; and despite real product shipments, Untether AI could not sustain independence — its engineering team joined AMD in 2025.

## Funding

- Raised: over $150M in venture capital total, including an oversubscribed $125M round in July 2021 co-led by Intel Capital and Tracker Capital, with CPP Investments and Radical Ventures participating.
- Valuation: MISSING.

## Latest — July 2021

Untether AI announced the oversubscribed $125M round to deploy its high-performance inference-acceleration chips, built around the runAI200 processor and a four-chip server card claimed at about 2 quadrillion operations per second.

## Latest — October 2024

The company released an AI chip aimed at physical-AI applications in machines — including cars and agricultural devices — pushing its efficiency-first inference story from the data center to the edge.

## Latest — June 2025

Semiconductor giant AMD acqui-hired the team behind Untether AI, as originally reported by CRN; the terms of the deal weren't disclosed, ending Untether AI's run as an independent chipmaker.
