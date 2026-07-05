# Deep dive: HVAC filter efficiency (do it right)

This page expands on the core insight from the main [the guide](index.md): **judge an HVAC filter by how well it removes particles, not by how old it is** — and only measure it when outdoor air is dirty enough to give you signal.

> **Not medical or professional HVAC advice.** Changing filters or altering airflow can affect your equipment. If in doubt, ask a licensed HVAC technician what your specific system can handle.

---

## Why "filter life" prediction fails

The appealing idea is to predict when a filter is spent, either by:

- **Elapsed time** — "replace every 90 days." But loading rate depends on how dirty *your* air is, how many hours the system runs, the season, cooking, pets, and smoke events. A 90-day filter in clean, low-runtime conditions is barely used; the same filter through wildfire season is finished in weeks. A calendar can't know the difference.
- **Accumulated load** — trying to estimate how much dust the filter has trapped. This is very hard to measure accurately at home, and even a good estimate of *load* doesn't directly tell you what you care about: **is the filter still cleaning the air?**

Both proxies drift away from the thing that matters. So measure the thing that matters directly.

---

## The efficiency method

You already have two numbers if you're monitoring: **outdoor PM2.5** and **indoor PM2.5**. The filter's job is to keep indoor particles low relative to outdoor. So:

```
filter efficiency = (outdoor PM2.5 − indoor PM2.5) / outdoor PM2.5
```

Expressed as a percentage, this is the fraction of the outdoor particle load that *isn't* making it to your indoor air. Conditions for a meaningful reading:

1. **The system fan is running** (air must move through the filter — no airflow, no filtration, and efficiency reads artificially low).
2. **No large indoor PM2.5 source is active** — don't measure mid-cook or while vacuuming; you'll be measuring your stove, not your filter.
3. **Outdoor air is dirty enough** (the critical caveat, below).

Interpretation:

- **High efficiency (large outdoor-indoor gap):** filter + airflow are doing their job.
- **Falling efficiency over time (comparing like conditions):** the filter is loading up, airflow has dropped, or air is bypassing the filter. Time to inspect/replace.

Because the metric is a *ratio against current outdoor conditions*, it automatically accounts for run time, season, and how dirty your air is — the exact things the calendar and load methods can't.

---

## The critical caveat: clean outdoor air breaks the math

Look at the denominator. When **outdoor PM2.5 is very low**, it's tiny — and dividing by a tiny number makes the result wildly sensitive to noise.

Worked example:

| Outdoor PM2.5 | Indoor PM2.5 | Computed "efficiency" | Reality |
|---|---|---|---|
| 80 | 6 | 92% | Filter clearly working |
| 40 | 4 | 90% | Filter clearly working |
| 10 | 3 | 70% | Marginal signal — treat with caution |
| 5 | 3 | 40% | **Noise — do not trust** |
| 3 | 2 | 33% | **Meaningless — nothing to filter** |

In the bottom rows the air is *already clean* — indoor 2–3 µg/m³ is excellent. But the formula screams "failing filter!" purely because the denominator collapsed. Act on that and you'll replace a perfectly good filter and distrust a working system.

### The fix: a seasonal minimum outdoor threshold

**Refuse to compute efficiency when outdoor PM2.5 is below a minimum.** Below it, report "**can't assess — outdoor air too clean to measure against**," not a number. Because what counts as "clean" varies by place and season, make the floor seasonal:

- **Clean-air seasons/regions: require outdoor PM2.5 ≳ 5 µg/m³.**
- **Dirtier seasons/regions: require ≳ 10 µg/m³.**

You lose nothing by skipping clean days: if outdoor air is that clean, your indoor air is fine regardless of the filter. You only *need* the filter to be working when outdoor air is dirty — which is exactly when the measurement is valid. The threshold turns this method from a false-alarm generator into a dependable check.

### Practical logging pattern

- Sample outdoor and indoor PM2.5 on the same cadence, with the fan running.
- **Gate every efficiency value on the outdoor threshold**; drop (don't record) values computed below it.
- Compare efficiency across days *of similar outdoor level* to spot a real downward trend, rather than comparing a smoky day to a hazy one.
- Trigger "inspect the filter" on a sustained drop across valid readings — not on any single number, and never on a below-threshold day.

---

## MERV and the airflow trade-off

MERV (Minimum Efficiency Reporting Value) rates capture efficiency by particle size; higher = finer.

- **MERV 13** captures the large majority of PM2.5 and is the widely recommended practical target for fine particles and smoke.
- **Finer filters restrict airflow more.** A denser medium raises **static pressure** across the blower. An undersized or older system may not move enough air through a high-MERV filter — which *reduces* comfort and total particle removal (less air moved means less air cleaned) and can strain the equipment.

Ways to get MERV 13 filtration without choking the system:

- **Use a thicker (4–5") pleated MERV 13.** More pleat surface area = lower pressure drop at the same rating.
- **Drop one MERV step** if airflow is clearly suffering, and make up the difference with portable HEPA.
- **Offload particle removal to standalone HEPA purifiers**, letting the HVAC filter be gentler.
- **Ask an HVAC professional** what static pressure and filter depth your blower is rated for.

The goal is the best filtration your system can sustain *with healthy airflow* — a high-MERV filter that starves the blower is a net loss.

---

## Quick checklist

- [ ] Sample indoor and outdoor PM2.5 together, fan running, no active indoor source.
- [ ] Compute efficiency = (outdoor − indoor) / outdoor.
- [ ] **Gate on outdoor ≳ 5 µg/m³ (clean season) / ≳ 10 (dirty season);** below that, "can't assess."
- [ ] Trend valid readings over time, comparing similar outdoor levels.
- [ ] Replace on a sustained efficiency drop — not on the calendar, not on one noisy reading.
- [ ] Filter target: MERV 13 if the blower supports the airflow; otherwise thicker-pleat MERV 13, a step down, or offload to HEPA.
