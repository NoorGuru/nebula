---
title: "Saqi-Schedule tells each field when to irrigate, over WhatsApp"
summary: "A WhatsApp scheduler for Jordanian farmers: it pulls free reference-evapotranspiration and soil-moisture data for the farm's coordinates and texts exactly how long to run the drip lines each day."
tags: ["garage", "jordan", "climatetech"]
featured: false
publishedAt: 2026-10-06
country: "Jordan"
sector: "climatetech"
stage: "idea"
status: "idea"
coreProblem: "Jordanian farmers irrigate by habit and feel — overwatering wastes pumped groundwater they pay for by the cubic meter, underwatering stresses high-value vegetables, and nobody computes actual daily crop water need."
howItWorks: "Farmer shares a WhatsApp location pin once plus crop and drip-flow rate. A nightly job fetches reference evapotranspiration (ET0), soil moisture, and rain forecast for those coordinates from a free weather API, multiplies by the crop coefficient, and sends a morning message: run line A for 47 minutes, skip tomorrow, rain expected Thursday. No sensors, no hardware, no app."
challenges: "ET0 math is only as good as the crop coefficients, which vary by growth stage — wrong coefficients mean confident-sounding wrong advice. Farmers who flood-irrigate can't act on minute-level schedules, so the wedge must start with drip-irrigated plots. Groundwater pumping costs differ by well, so savings estimates must stay per-farm, never advertised as averages."
buildCost: "~$8-15k: weather data free up to 10k calls/day, WhatsApp farmer-initiated replies free in-window, one part-time irrigation agronomist to set crop coefficients."
techStack: "WhatsApp Cloud API + Open-Meteo free forecast API (ET0, soil moisture, precipitation) + nightly scheduler + crop-coefficient table per crop and growth stage."
firstCustomer: "Greenhouse and open-field vegetable growers in the Jordan Valley on metered wells — they pay per cubic meter pumped, so a seasonal subscription pays for itself the first month it trims pumping hours."
whyNow: "Open-Meteo serves reference evapotranspiration (ET0), soil moisture, and forecasts free at ~10k calls/day with no key (pricing page, 2026) + WhatsApp non-template replies free inside the 24h window (Meta per-message pricing, effective Jul 2025)."
sources:
  - title: "Open-Meteo Weather Forecast API docs (ET0, soil moisture)"
    url: "https://open-meteo.com/en/docs"
  - title: "Open-Meteo pricing (free tier limits)"
    url: "https://open-meteo.com/en/pricing"
  - title: "Pricing on the WhatsApp Business Platform"
    url: "https://developers.facebook.com/docs/whatsapp/pricing"
summaryAr: "جدولة ري عبر واتساب للمزارع الأردني: تحسب حاجة الحقل اليومية من بيانات الطقس المجانية وترسل مدة تشغيل التنقيط كل صباح."
---

## The problem

Water is Jordan's binding constraint and irrigation runs on vibes. A Valley farmer runs his drip lines two hours every morning because his neighbor does. On cool cloudy weeks he is pumping expensive groundwater straight past the root zone; on heatwave weeks the peppers stress before noon. The agronomy to fix this — daily crop water need from weather data — has existed for decades but never reached a farmer without a sensor salesman attached.

## The build

Two people ship a scheduler, not a sensor. Onboarding is one WhatsApp location pin, the crop, and the drip flow rate. Every night a job pulls the farm's reference evapotranspiration, soil moisture, and rain forecast, applies the crop's coefficient for its growth stage, and sends a morning message in Arabic: run 47 minutes today, skip tomorrow, rain Thursday. The farmer replies "done" or "skipped" and the schedule adjusts. The free weather API tier covers roughly ten thousand farm-days of calls per day — the whole pilot runs on zero data cost.

## Why now

The missing input — per-field daily ET0 and soil moisture — recently became a free API call instead of a weather station. Open-Meteo exposes reference evapotranspiration, multi-layer soil moisture, and precipitation forecasts free up to 10,000 calls a day. Delivery rides the same July-2025 WhatsApp pricing shift: the farmer's morning question opens a window and the schedule lands free. Three years ago this needed hardware in the soil; now it needs a location pin.

## First customer

Jordan Valley vegetable growers pumping metered groundwater. They feel every wasted cubic meter in dinars, they mostly already run drip, and a single season of trimmed pumping hours covers a subscription several times over. Sell through well-driller and drip-equipment shops that already visit these farms monthly.

## Challenges

A schedule is a promise, and soil is not uniform — one farm's loam holds water two days longer than the neighbor's sand, so the bot must learn per-farm corrections from "too dry / too wet" replies instead of defending its math. Flood irrigators are out of scope until a version speaks in irrigation turns, not minutes. And in a drought year, telling a farmer to water less when his well is failing reads as blame — the message must frame savings as stretched supply, not lectures.
