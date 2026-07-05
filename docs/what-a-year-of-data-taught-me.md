# What a year of data taught me

The main [guide](index.md) is built on a simple loop: measure, interpret, improve. This page is about the *interpret* step — the patterns that only show up once you've logged your home's air continuously for months instead of glancing at a number now and then.

Everything here comes from roughly nine months of continuous logging in a single home (indoor and outdoor PM2.5, CO₂, VOCs, radon, temperature, humidity, sampled every few minutes). **None of it is a universal constant.** One home is not a study. Treat every number below as *"here's what I saw — go check whether your own data does the same thing."* The value isn't my specific figures; it's knowing which relationships to look for in yours.

> **Not medical advice.** This is an educational summary of measurement patterns, not health guidance. Where sleep or symptoms are mentioned, effect sizes in the research are genuinely debated — treat the physiology as motivation to ventilate and filter, not as a diagnosis. Work with your doctor on anything respiratory.

---

## 1. A closed bedroom fills up with CO₂ overnight — more than you'd guess

The main guide notes that a closed bedroom can pass 1400 ppm overnight. In practice it can be much worse: an occupied bedroom with the door shut climbed from the ~420 ppm outdoor baseline to **2,000–3,000 ppm by morning** in a tight room. The absolute number matters less than what it represents: for eight hours, the room was barely exchanging air with anywhere else, so *everything* the occupants exhaled or off-gassed accumulated alongside the CO₂.

**The reusable move:** put a CO₂ monitor on the nightstand and look at it at 6 a.m., before you open the door. That single reading converts "ventilation" from an abstraction into a number you can feel. If it's high, the fixes are cheap: crack the door, add a transfer grille or a quiet fan for cross-flow, or bump up mechanical fresh-air overnight.

## 2. CO₂ and VOCs can rise together — a cheap monitor may double as a VOC proxy

In this home, indoor CO₂ and indoor VOCs tracked each other closely (Spearman ρ ≈ 0.65). Both climbed whenever fresh-air flow was low. The reason is specific to the house: most of its VOCs are *occupant- and activity-generated* (cooking, breathing, cleaning), so the same poor ventilation that traps CO₂ traps them too. That makes an ~$80 NDIR CO₂ monitor a reasonable stand-in for "are my occupant-sourced VOCs building up?"

**But this relationship is conditional, and that's the lesson.** In a home with heavy *material* off-gassing — new furniture, fresh paint, new flooring — VOCs are produced independently of how many people are breathing, and the CO₂↔VOC pairing breaks down. So don't assume it; *test* it. Plot your own CO₂ and VOC index on the same timeline for a couple of weeks. If they move together, one cheap sensor covers both. If they don't, you have a material source that ventilation alone won't fix, and you need to find it.

## 3. Indoor readings are mostly a filtered echo of outdoors — with a lag

Most of the time, indoor PM2.5 is just outdoor PM2.5 with the peaks shaved off by your envelope and filter. When outdoor air is dirty and indoor stays low, that gap *is* your filtration working (the basis of the [filter-efficiency method](filter-efficiency.md)). Two patterns worth watching for in your own data:

- **Weather couples pollutants that have nothing to do with each other.** Outdoor PM2.5 and *indoor radon* rose together (ρ ≈ 0.59) despite having completely different sources. The common cause is atmospheric stagnation: a temperature inversion with no wind means outdoor particles can't disperse *and* soil radon can't ventilate out of the house, so both climb at once. In the data this shows up as multi-day bands of elevated readings, mostly in winter. If you see two unrelated metrics spike together for days, suspect the weather, not a new indoor source.
- **Expect a seasonal baseline shift, not a flat line.** Winter ran higher across the board — higher outdoor and indoor CO₂ (inversions plus a sealed house), higher radon, higher outdoor PM2.5. Summer ran cleaner on all of those, with the exception that wildfire smoke can erase the advantage overnight. A "normal" reading in July is an anomaly in January; judge today against the same season, not an annual average.

## 4. When indoor exceeds outdoor, *you* are the source

The single most useful spike-diagnosis rule: **if indoor PM2.5 is meaningfully higher than outdoor, the particles are being made inside.** No filter fixes a source you keep feeding. Cooking is the usual culprit — a sensor near the kitchen jumped from ~3 µg/m³ to **80+ µg/m³** during cooking, then decayed back over **30–60 minutes**. That signature — a sharp rise above the outdoor level, then a slow ~half-hour decay — is what an indoor event looks like.

**The reusable move:** keep a rough activity log for your first few weeks ("cooked dinner," "vacuumed," "lit a candle," "windows open"). The spikes will line up with the tags fast, and you'll learn which of your own habits move the needle. Two practical consequences fall out of this:

- A brief cooking spike that clears in half an hour is normal; run the range hood and move on. A *sustained* elevation is a filter or ventilation problem.
- It also means the efficiency math only works when no indoor source is active — measuring your filter mid-cook measures your stove.

## 5. The ERV dilemma, with numbers

The main guide explains *why* fresh air is a trade-off (lower CO₂, higher particles). The data lets me put rough thresholds on the decision. Ventilation flow moves CO₂/VOCs and PM2.5 in opposite directions, so the outdoor particle level decides which way to lean:

- **Outdoor PM2.5 below ~15 µg/m³ (and outdoor VOC/NOₓ low):** favor more ventilation. The CO₂ and VOC you flush out are worth the small particle load you let in.
- **Outdoor PM2.5 above ~20 µg/m³ (smoke, high-pollution days), or elevated outdoor VOC/NOₓ from nearby traffic:** cut ventilation and lean on recirculating filtration. Accept some CO₂ creep as the price of keeping particles out.

The band between 15 and 20 is a judgment call. The point is that "should I ventilate right now?" has a *measured* answer that changes hour to hour — which is exactly why the outdoor number earns its keep. (An energy-recovery ventilator still imports outdoor particles; on smoke days its fresh-air function is a liability. See the [wildfire playbook](wildfire-smoke.md).)

## 6. "MERV 13" is a rating, not a performance guarantee

This one surprised me most. Over about six weeks, a filter was swapped for a *different* model carrying the **same MERV 13 rating** — same home, same HVAC, same outdoor air, same sensors, only the filter changed. Measured ambient-PM2.5 removal efficiency:

- Original filter: ~95% median
- Same-rated replacement: **~69% median, with bad days down to 35–50%**
- Swapping the original back: ~95% again, on day one

Two filters wearing the same label differed by **~20 percentage points** in real-world performance in the same slot. A MERV rating comes from a standardized test with a *minimum* capture threshold at each particle size — a filter that barely passes and one that comfortably exceeds can both print "MERV 13," and media quality, pleat density, and housing fit all vary underneath the label. **The only way to know which one you actually installed is to measure it** (see [filter-efficiency.md](filter-efficiency.md) for how). The cheapest same-rated filter is not a saving if it quietly lets 20% more of the outdoor load through.

## 7. Filter age barely predicts filter health

Across nine months, monitoring caught exactly **one** genuine filter failure — efficiency fell from a ~95% baseline to **~49%** over about eight hours before replacement, then snapped back to baseline within an hour of the new filter going in. The degradation was even noticeable by smell before anyone read the numbers. Meanwhile, a filter running at nearly **twice** its manufacturer's rated life was still removing ~87% of particles.

The takeaway isn't a specific interval — it's that **elapsed time and "accumulated load" are weak predictors of whether a filter is still doing its job.** Loading depends on how dirty your specific air is, how many hours the system runs, the season, cooking, pets, and smoke events — none of which a calendar knows. Watch efficiency (on dirty-enough days) and replace on a sustained drop. For most homes that means *fewer* replacements than the label schedule, plus a real alarm when something actually fails. Full method and the clean-air caveat are in [filter-efficiency.md](filter-efficiency.md).

## 8. Know what a "0" means on your sensor

A subtle data-quality trap that cost me a wrong conclusion: a low-cost PM2.5 sensor that **rounds to whole numbers** reports `0` whenever true indoor PM is below ~0.5 µg/m³. Feed that into the efficiency formula and it pegs at a flawless-looking **100%** — not because filtration is perfect, but because the sensor ran out of resolution. Whole stretches of "100% efficiency" were really "indoor PM below what this device can see."

**The reusable move:** before you compute anything on sensor data, learn each channel's resolution and detection floor. A `0` on a coarse sensor is not zero — it's "below my resolution," and arithmetic on it produces confident, meaningless numbers. If indoor precision matters to you, pick a sensor with sub-integer PM2.5 reporting.

---

## How to find these in your own data

None of this required fancy tooling — just history and a habit of comparing the right things:

1. **Log continuously and keep the history.** A snapshot lies; a time series tells the truth. The patterns above are invisible in any single reading.
2. **Always pair indoor with outdoor.** Half of these findings are a *relationship between two series*, not a single value.
3. **Compare like with like.** Judge a reading against the same season and similar outdoor conditions, not an annual average.
4. **Tag your activities early.** A couple of weeks of "cooked / vacuumed / windows open" notes turns mystery spikes into a labeled map of your own home.
5. **Look for correlations, then question them.** Two metrics moving together is a lead, not a conclusion — figure out the common cause (often the weather or your ventilation) before you act.

Your home, your climate, and your habits are different from mine. The findings won't transfer — but the *method of looking* will.
