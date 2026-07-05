# Home Air Quality for Asthma & Allergy Sufferers

A practical, evidence-based guide to understanding and improving the air in your home — written by someone who lives with reactive airways and got tired of guessing. This is distilled from a real DIY monitoring project, boiled down to reusable knowledge.

> **Not medical advice.** This is an educational guide, not a substitute for professional care. Air quality is one lever among many. If you have asthma, allergies, or any respiratory condition, work with your doctor, and consult a licensed HVAC or radon professional before making changes to your home's systems. Nothing here should override a treatment plan.

---

## Why this exists

If you have asthma or allergies, your home is where you spend most of your time — and indoor air is often *dirtier* than the air outside. The good news: home air is also the air you have the most control over. You can't fix the whole outdoors, but you can make one room, or a whole house, dramatically better to breathe in.

The trap is that air quality is **invisible**. You can't see PM2.5. You can't smell CO₂. You feel the *consequences* — a tight chest at 2 a.m., a stuffy headache in a closed bedroom, a flare that seems to come from nowhere — but not the cause. So people guess, buy gadgets, and never find out whether any of it helped.

The fix is to **measure, interpret, and improve** — in that order, on a loop. This guide walks through each step with concrete numbers and thresholds, and it's honest about the trade-offs (fresh air is good for CO₂ but can be bad for particles; a "failing" filter reading is often just clean outdoor air fooling you).

---

## TL;DR / Quick start

If you do nothing else, do these:

1. **Get one indoor monitor that reads PM2.5, CO₂, temperature, and humidity.** Add a **radon** monitor if you haven't tested (radon is a separate, long-term risk). Get an **outdoor** PM2.5 number too — a nearby public AQI station works.
2. **Source control first.** No indoor smoking, ever. Run the range hood *every* time you cook. Cut obvious VOC sources. Vacuum with a HEPA machine.
3. **Upgrade your HVAC filter to MERV 13** *if your system can handle it* (see the airflow caveat below), and run the system fan for circulation, not just when heating/cooling.
4. **Add a portable HEPA purifier** sized to your most-used room — especially the bedroom. Match the purifier's **CADR** to the room (rule of thumb below).
5. **Keep relative humidity at 30–50%** to starve mold and dust mites.
6. **On smoky / high-pollen / high-AQI days: seal up.** Close windows, run purifiers, and lean on filtration. On *clean* days, open up to flush CO₂.
7. **Judge your HVAC filter by efficiency, not by age** — and *only* when outdoor air is dirty enough to measure against (this is the single most useful and most misunderstood insight in this guide; see below).

Target numbers at a glance:

| Metric | Good | Act when… |
|---|---|---|
| PM2.5 (indoor) | < 5 µg/m³ | > 15 µg/m³ sustained; > 35 = clearly unhealthy |
| CO₂ | < 800 ppm | > 1000 ppm (ventilate); > 1400 = poor |
| Relative humidity | 30–50% | < 30% (dry) or > 50% (mold/mite risk) |
| Radon | < 100 Bq/m³ (≈2.7 pCi/L) | ≥ 148 Bq/m³ (4 pCi/L) → mitigate |
| VOCs | low / stable | sustained spikes above your own baseline |
| Temperature | comfort (≈20–22 °C / 68–72 °F) | comfort-driven |

---

## What to measure, and why it matters

You don't need every sensor. But knowing *what each metric tells you* is what turns a number into an action.

### PM2.5 — fine particulate matter (the big one for asthma)

PM2.5 is airborne particles 2.5 micrometers across or smaller — small enough to get deep into your lungs and, for the finest fraction, into your bloodstream. For asthma and allergies, **this is the metric that matters most.** Sources include outdoor pollution that leaks in, wildfire smoke, cooking (especially frying and searing), candles, wood stoves, and resuspended dust.

The World Health Organization's air-quality guideline levels:
- **24-hour mean: 15 µg/m³**
- **Annual mean: 5 µg/m³**

Those are ceilings for *healthy* populations; if you're sensitive, aim lower indoors. A well-filtered home can sit under 5 µg/m³ almost all the time. **The single most useful habit is tracking indoor vs. outdoor PM2.5 side by side** — it tells you how much of your indoor particle load is leaking in from outside versus being generated inside, and it's the basis of the filter-efficiency method below.

### CO₂ — your ventilation proxy

Carbon dioxide itself isn't a major asthma trigger at household levels, but it's an excellent **stand-in for how stuffy and under-ventilated a space is.** You and everyone else exhale CO₂; if it's building up, so is everything else that isn't being flushed out (odors, VOCs, humidity, exhaled aerosols).

- Outdoor air is roughly **420 ppm**.
- **Below ~800 ppm:** well ventilated.
- **Above ~1000 ppm:** poor ventilation — noticeable stuffiness, and measurable effects on concentration and sleep quality.
- **1400+ ppm:** a closed bedroom overnight with the door shut can easily hit this. Crack a door or add fresh air.

CO₂ is the metric that tells you *when to ventilate* — which matters because ventilation is a trade-off (see the fresh-air dilemma below).

### VOCs — volatile organic compounds

VOCs are gases that off-gas from new furniture, paint, flooring, air "fresheners," cleaning products, and cooking. Some are irritants or asthma triggers; many are simply things you don't want to be breathing. Consumer VOC sensors report a **relative** index (often "TVOC," total VOCs) rather than a lab-grade concentration — so **treat them as a trend and a spike detector, not an absolute truth.** What's useful is watching the number jump when you spray a cleaner, open a new piece of furniture, or paint — and watching how long it takes to clear (that's your ventilation working).

### Radon — the slow, invisible one

Radon is a naturally occurring radioactive gas that seeps up from soil and rock into homes, especially basements and ground floors. It has **nothing to do with day-to-day asthma symptoms** — it's a long-term **lung-cancer risk** (the leading cause of lung cancer in non-smokers). It's included here because it's invisible, common, cheap to test for, and fixable, and because anyone building an air-monitoring setup should test for it once.

- **WHO reference level: 100 Bq/m³**
- **US EPA action level: 148 Bq/m³ (4 pCi/L)**

**Units differ by region** — Europe and most of the world use becquerels per cubic meter (Bq/m³); the US uses picocuries per liter (pCi/L). The conversion: **1 pCi/L ≈ 37 Bq/m³.** If your reading is at or above the action level, this is a call-a-professional situation — radon mitigation (typically a sub-slab depressurization system) is a well-established, effective fix.

### Temperature & humidity — comfort *and* biology

Beyond comfort, **relative humidity is a real health lever:**
- **Below 30%:** dry air irritates airways and can worsen asthma and eczema.
- **Above 50%:** you're feeding **mold** and **dust mites**, two of the most common allergy and asthma triggers.
- **Target: 30–50% RH.** Aim for the lower half of that range if dust mites or mold are your triggers.

Humidity also interacts with temperature (warm air holds more moisture) and with your PM2.5 sensor — many low-cost optical sensors read high in very humid air because they see swollen, water-coated particles. Keep that in mind when a reading spikes on a muggy day.

### Barometric pressure — mostly context

Barometric pressure won't hurt your lungs, but it's worth logging for two reasons. First, it's **context** for other readings (weather fronts move pollutants around). Second, **some people are genuinely barometric-pressure sensitive** — rapid pressure drops before storms correlate with headaches, migraines, and joint pain for a subset of people. If that's you, having the data lets you connect a bad day to a front instead of blaming your air.

---

## The measure → interpret → improve loop

### Step 1 — Measure

You need, at minimum:
- **One indoor monitor** covering PM2.5, CO₂, temperature, and humidity. Place it at breathing height, away from windows, doors, and the kitchen, in a room you actually use (the bedroom is the highest-value spot — you spend a third of your life there).
- **An outdoor PM2.5 reference.** Either a small outdoor sensor or a nearby public air-quality station. You *need* the outdoor number to interpret the indoor one.
- **A radon test**, at least once, ideally a long-term measurement (radon swings day to day and season to season).

Then **log the readings over time.** A single snapshot tells you almost nothing; a week of data tells you when your CO₂ peaks, whether cooking spikes PM2.5, and whether your filter is keeping up. A spreadsheet is fine to start. A small time-series database is nicer if you want dashboards, but don't let tooling ambition stop you — even hourly manual notes reveal patterns. Once you're logging continuously, [monitoring-and-alerts.md](monitoring-and-alerts.md) covers how to turn that stream into a few trustworthy alerts instead of noise.

### Step 2 — Interpret

Use the thresholds table from the TL;DR. A few interpretation habits that matter:

- **Compare indoor to outdoor, always.** Indoor PM2.5 of 12 µg/m³ means very different things when outdoor is 80 (your envelope and filter are doing great) versus when outdoor is 6 (something *inside* is generating particles — cooking, a candle, vacuuming). Concretely: outdoor 80 / indoor 12 is a filter removing 85% of the load — excellent; outdoor 6 / indoor 12 is an *indoor* source, and no filter will fix a problem you keep making.
- **Watch changes, not just absolute values,** for VOCs especially. Your baseline is your baseline; the spike is the signal.
- **Correlate spikes with activities.** Tag your log: "cooked dinner," "vacuumed," "windows open," "storm." Patterns jump out fast.

### Step 3 — Improve

Covered in depth in the next two sections.

---

## The HVAC filter insight: measure efficiency, not life

This is the hard-won centerpiece of the project this guide came from, and it corrects a mistake almost everyone makes.

### The wrong way: predicting filter "life"

The intuitive approach is to guess when a filter is spent by **elapsed time** ("replace every 90 days") or by **accumulated load** (some notion of how much dust it's caught). In practice this **fails.** Filter loading depends on how dirty your specific air is, how much you run the system, the season, whether you cooked a lot that month, whether there were fires. A calendar can't know any of that, and "load" is nearly impossible to measure well at home. You end up replacing good filters early (waste) or running clogged ones too long (worse airflow, worse air).

### The right way: measure efficiency directly

A filter's whole job is to **remove particles.** So measure that, directly, using the two numbers you already have:

```
filter efficiency = (outdoor PM2.5 − indoor PM2.5) / outdoor PM2.5
```

A healthy filter, with the system circulating air, removes most of the outdoor particle load — you'll see high efficiency (a large gap between outdoor and indoor). As a filter degrades, or if airflow drops, or the filter is bypassed, that gap shrinks and efficiency falls. **You're measuring the thing you actually care about — clean air — instead of a proxy for it.**

This also naturally accounts for everything the calendar can't: run time, season, how dirty your air is. If the filter is keeping indoor air clean relative to outdoor, it's doing its job, regardless of its age.

### The critical caveat: clean outdoor air breaks the math

Here's the part almost everyone gets wrong, and it's essential:

> **The efficiency measurement is only meaningful when outdoor air is dirty enough.**

Look at the formula. When **outdoor PM2.5 is very low** — a crisp, clean-air day — the denominator is tiny, and any small indoor reading (a bit of cooking, sensor noise, a speck of dust) makes efficiency look terrible. Outdoor 3, indoor 2 → "33% efficiency, the filter is failing!" — when in reality the air is *fine* and there's simply nothing to filter. You'll chase a phantom problem and maybe replace a perfectly good filter.

**The fix: apply a minimum outdoor PM2.5 threshold, and refuse to compute efficiency below it.** Below the threshold, the honest answer is *"can't assess right now — outdoor air is too clean to measure against."* Make it seasonal, because "clean" varies:

- **Clean-air seasons/regions: require outdoor PM2.5 ≳ 5 µg/m³** before trusting the number.
- **Dirtier seasons/regions: require ≳ 10 µg/m³.**

Only assess your filter on days when outdoor air actually gives you signal. On clean days, the filter question is simply moot — the air is already good. This one rule turns filter efficiency from a source of false alarms into a genuinely reliable health check.

### MERV ratings and the airflow trade-off

MERV (Minimum Efficiency Reporting Value) rates how well a filter captures particles; higher = finer filtration.

- **MERV 13 captures the large majority of PM2.5** and is the sweet spot for most homes wanting real particle control. Many public-health bodies recommend MERV 13 as the practical target for filtering fine particles and smoke.
- **But there's a trade-off: finer filters restrict airflow more.** A denser filter raises **static pressure** on your blower. Some HVAC systems — especially older or undersized ones — can't push enough air through a MERV 13, which hurts both comfort and, ironically, filtration (less air moved = less air cleaned) and can strain the equipment.
- **Balance filtration against airflow.** If MERV 13 chokes your system, options include a thicker (4–5") pleated MERV 13 with more surface area (lower pressure drop for the same rating), a slightly lower MERV, or offloading particle removal to standalone HEPA purifiers. When in doubt, ask an HVAC pro what your blower can handle.

More depth on the method and the airflow math lives in [filter-efficiency.md](filter-efficiency.md).

---

## How to actually improve your air

Work in this order — it's roughly the order of cost-effectiveness.

### 1. Source control first (cheapest, biggest wins)

You can't filter your way out of a problem you keep creating. Remove the sources:

- **No indoor smoking or vaping. Ever.** Nothing else on this list competes with this.
- **Run the range hood every time you cook** — and make sure it vents *outside*, not just recirculates. Cooking, especially frying, searing, and high heat, is one of the largest indoor PM2.5 sources in most homes. Use back burners (better hood capture) and give it a few extra minutes after you finish.
- **Cut VOC sources.** Skip plug-in "air fresheners" and scented sprays (they add chemicals, they don't clean air). Choose low-VOC paints and finishes. Let new furniture, mattresses, and rugs off-gas in a ventilated space before heavy use.
- **Dust and vacuum with a HEPA-filtered vacuum.** A non-HEPA vacuum resuspends the fine dust it picks up. Damp-dust hard surfaces so you capture rather than scatter.
- **Deal with allergen reservoirs:** wash bedding hot weekly, minimize wall-to-wall carpet if dust mites are a trigger, and manage pet dander at the source.

### 2. Filtration (steady, reliable improvement)

- **Upgrade the HVAC filter to MERV 13** if your system supports it (see airflow caveat above), and **run the system fan continuously or on a circulation schedule** — filtration only happens when air is moving through the filter. Many thermostats have a "circulate" mode for exactly this.
- **Add portable HEPA air purifiers** in the rooms you use most, sized to the room. True HEPA captures ≥99.97% of 0.3 µm particles — more than enough for PM2.5 and smoke.

**Sizing a purifier — CADR:** CADR (Clean Air Delivery Rate) tells you how much clean air a purifier produces, in CFM or m³/h. A common rule of thumb: **for smoke/fine particles, pick a CADR (in CFM) at least ⅔ of your room's floor area in square feet** — e.g., a 150 ft² bedroom wants a smoke CADR around 100 CFM for solid turnover. If you want aggressive cleaning (asthma, smoke season), size up so the unit can do **4–5 air changes per hour**. Bigger room or worse air → more CADR, or run it higher. A DIY box-fan-plus-filter unit is a legitimate, cheap high-CADR option in a pinch.

### 3. Ventilation — and the fresh-air dilemma

Ventilation flushes CO₂, VOCs, and humidity. But here's the trade-off that trips people up:

> **Fresh air lowers CO₂ but can *raise* indoor PM2.5.**

Opening a window — or running an ERV (Energy Recovery Ventilator) — brings in outdoor air. On a clean day that's pure upside: CO₂ drops, staleness clears. But on a **smoky, dusty, or high-pollen day, you're importing exactly the particles you're trying to keep out.** More fresh air = more outdoor PM2.5 indoors.

So ventilation isn't "always good" — it's **conditional:**

- **On clean-air days (low outdoor PM2.5, low pollen): ventilate freely.** Open windows, run the ERV, flush that CO₂ down below 800 ppm.
- **On bad-air days (smoke, high AQI, peak pollen): seal up and lean on filtration.** Close windows, pause or minimize fresh-air intake, run your purifiers hard. Yes, CO₂ will creep up — that's the acceptable cost of keeping particles out. Manage it by not over-occupying sealed rooms, and open up again the moment outdoor air improves.

An **ERV** is worth mentioning specifically: it swaps stale indoor air for fresh outdoor air while recovering heat/coolth, so you ventilate without wrecking your heating bill. But an ERV **still brings outdoor particles inside** (many include only a modest filter), so on smoke days its fresh-air function is a liability, not an asset — know how to reduce or bypass it, or pair it with strong downstream filtration. **Let your outdoor PM2.5 reading decide** whether today is a ventilate day or a seal-up day. That's exactly why you measure outdoor air.

### 4. Humidity control

Keep RH in the **30–50%** band:
- **Too humid (>50%):** run a dehumidifier or your AC; fix leaks and moisture sources; use bathroom exhaust fans. This starves mold and dust mites.
- **Too dry (<30%):** a humidifier helps, but **clean it religiously** — a dirty humidifier is a mold and bacteria aerosolizer, which is worse than dry air. Distilled or demineralized water reduces white dust.

### 5. Wildfire smoke & high-AQI days

Smoke events are the extreme case, and they're becoming more common. When outdoor AQI spikes:

- **Seal the house.** Close windows and doors; shut off or minimize any fresh-air intake and ERV/whole-house fan.
- **Run every purifier you have**, on high.
- **Create one "clean room."** Pick a room (ideally the bedroom), close it off, run a well-sized HEPA purifier, and make it the space where the most vulnerable person sleeps and spends time. You don't have to win the whole house — you have to win one room.
- **Set your HVAC fan to recirculate** (not fresh-air) with the best filter your system tolerates; a portable HEPA unit covers the gap if your filter is modest.
- **Watch your own indoor PM2.5** to confirm it's actually working, and **wait for the outdoor number to drop** before you re-open to ventilate.

There's a fuller playbook in [wildfire-smoke.md](wildfire-smoke.md).

---

## Sensors: what to get (vendor-neutral)

This guide names **categories, not brands** — the market changes fast and the principles don't.

- **Consumer indoor air-quality monitors** typically bundle **PM2.5, CO₂, VOC (TVOC), temperature, humidity, and barometric pressure** in one unit. A single good multi-sensor is the easiest start.
- **Low-cost PM2.5 sensors** (optical/laser scattering) are inexpensive and good enough for trends and indoor/outdoor comparison. Know their limits: they estimate mass from light scattering, can read high in high humidity, and aren't reference-grade — but for *relative* indoor-vs-outdoor and trend work, they're excellent.
- **CO₂ sensors:** insist on **true NDIR** sensors. Cheap "eCO₂" sensors *estimate* CO₂ from VOCs and are not trustworthy for real ventilation decisions.
- **Radon monitors:** consumer continuous radon monitors give you a running readout and trends; a professional or lab test kit gives you an official measurement. Radon fluctuates a lot, so **longer measurement windows are more meaningful.**
- **Outdoor data:** either a dedicated outdoor sensor at your home or a **nearby public AQI monitoring station.** You need this reference to interpret indoor numbers and to make the ventilate-vs-seal-up call.

**Whatever you pick, log it over time.** A spreadsheet, a home-automation dashboard, or a small database — the tool matters far less than actually capturing the history. Trends are where the insight lives: the cooking spike you never noticed, the bedroom CO₂ that climbs every night, the filter efficiency that's quietly slipping. A snapshot lies; a time series tells the truth. For the patterns worth hunting in your own history — overnight CO₂, indoor-vs-outdoor coupling, the ERV trade-off with numbers — see [what-a-year-of-data-taught-me.md](what-a-year-of-data-taught-me.md).

---

## FAQ

**Do I really need to measure, or can I just buy a purifier and be done?**
A purifier without measurement is a guess. It might be undersized, in the wrong room, or off when you need it. Measuring tells you whether it's actually working and where to put your effort. Start with one monitor.

**What's the single highest-value thing to buy first?**
One indoor monitor with PM2.5 + CO₂, placed in your bedroom. It covers your two most actionable metrics in the room where you spend the most time.

**My indoor PM2.5 is higher than outdoor. What's wrong?**
Something inside is making particles — most often cooking, candles, a fireplace, or vacuuming without HEPA. On a clean-outdoor day it's normal for a brief cooking spike to exceed outdoor levels. Ventilate the spike (hood, cracked window if outdoor air is clean) and it should clear.

**My filter-efficiency number looks terrible today. New filter time?**
Check the outdoor PM2.5 first. If outdoor air is very clean (below ~5–10 µg/m³ depending on season), **the efficiency number is meaningless** — there's nothing to filter, so a tiny indoor reading looks like failure. Only judge the filter on days with dirty enough outdoor air. This is the most common mistake with this method.

**Is MERV 13 always the right filter?**
It's the target if your system can move enough air through it. An over-restrictive filter raises static pressure and can starve your blower — hurting airflow, comfort, and even filtration, and straining the equipment. Use a high-surface-area (thick) MERV 13, drop a step, or offload to portable HEPA if your system struggles. Ask an HVAC pro about your blower.

**Should I open windows for fresh air or keep them closed?**
It depends entirely on the outdoor air. Clean day: open up and flush CO₂. Smoky/high-pollen/high-AQI day: keep them closed and run filtration, accepting some CO₂ buildup as the lesser evil. Let your outdoor PM2.5 number decide.

**Is CO₂ actually dangerous at home levels?**
Not acutely dangerous, but high CO₂ (>1000 ppm) signals poor ventilation, causes stuffiness and worse sleep and focus, and means other pollutants aren't being flushed either. Treat it as your ventilation gauge.

**Do I need to worry about radon if I don't have symptoms?**
Radon causes no symptoms — that's the danger. It's a long-term lung-cancer risk, not an asthma trigger. Test once (long-term is best); if you're at/above 148 Bq/m³ (4 pCi/L), get professional mitigation. It's a common and very fixable problem.

**Humidifier or dehumidifier?**
Whichever pulls you toward 30–50% RH. Above 50%, dehumidify (mold/mites). Below 30%, humidify — but keep the humidifier scrupulously clean, or it becomes a mold sprayer.

**Are cheap PM2.5 sensors accurate enough?**
For trends and indoor-vs-outdoor comparison, yes. They're not reference instruments and can read high in humid air, but they're more than good enough to drive the decisions in this guide.

---

## Putting it together

The whole system is a loop:

1. **Measure** — indoor PM2.5/CO₂/temp/humidity, an outdoor PM2.5 reference, radon once, and *log it over time.*
2. **Interpret** — compare indoor vs. outdoor, watch trends and spikes, use the thresholds table.
3. **Improve** — source control → filtration → conditional ventilation → humidity → smoke-day sealing.
4. **Verify** — watch the numbers move. Judge your HVAC filter by *efficiency*, only when outdoor air is dirty enough to measure against.
5. Repeat. Your air, your triggers, and the seasons all change — a standing loop keeps up; a one-time fix doesn't.

You don't have to do all of it at once. One monitor in the bedroom and a right-sized HEPA purifier will already change how you sleep. Build from there.

Breathe easier.

---

## Further reading & standards referenced

### Companion pages in this guide

- [what-a-year-of-data-taught-me.md](what-a-year-of-data-taught-me.md) — real patterns from months of continuous logging, framed as things to look for in your own data.
- [monitoring-and-alerts.md](monitoring-and-alerts.md) — how to build and calibrate alerts that stay few and trustworthy.
- [filter-efficiency.md](filter-efficiency.md) — the efficiency method in depth, with the clean-air caveat and MERV/airflow trade-off.
- [wildfire-smoke.md](wildfire-smoke.md) — the seal-up / clean-room playbook for smoke and high-AQI days.

### Standards

- **WHO Global Air Quality Guidelines** — PM2.5 24-hour (15 µg/m³) and annual (5 µg/m³) guideline levels; radon reference level (100 Bq/m³).
- **US EPA** — radon action level (148 Bq/m³ / 4 pCi/L); Air Quality Index (AQI); guidance on wildfire smoke and creating a clean room; MERV 13 recommendations for smoke.
- **ASHRAE** — ventilation and filtration standards; MERV rating system.
- Consult local public-health and building authorities for region-specific guidance and units (Bq/m³ vs. pCi/L).

## License

Released under the [MIT License](https://github.com/minghsuy/home-air-quality/blob/main/LICENSE). Educational content, provided as-is; see the disclaimer at the top. Contributions welcome.
