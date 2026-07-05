# Monitoring & alerts: how to get few, trustworthy warnings

Logging your air is step one. The harder problem is turning that stream of numbers into **alerts you actually trust** — a handful of messages a week that each mean "go do something," instead of a firehose of noise you learn to ignore. An alerting system that cries wolf is worse than none: the day it's finally right, you've already muted it.

This page is the calibration playbook behind the main [guide](index.md): how to sample, how to set thresholds that don't false-alarm, how to tune them to your own home, and how to make sure the system tells you when it's the one that's broken. The specific numbers come from one home's monitoring script; **treat them as starting points and calibrate to your own data** — the how-to is the transferable part.

> **Not medical or professional HVAC advice.** This is about instrumentation and alert design. Anything that changes your HVAC airflow or ventilation should be run past a licensed technician; anything health-related, past your doctor.

---

## The one principle: alert only on *actionable* conditions

Before any threshold, adopt the rule that kills most noise: **every alert must map to an action you'd actually take.** "PM2.5 is 6 instead of 4" is not actionable. "Filter efficiency has been below its seasonal floor for two hours — inspect the filter" is. If you can't finish the sentence "…so I will ___," it shouldn't page you. Everything below is machinery in service of that rule.

A second rule makes the first survivable: **fail open and stay quiet under doubt.** When the data is missing, stale, or ambiguous, the system should go silent, not guess. A monitor that invents alarms during its own outages trains you to ignore it.

---

## Sampling interval: why ~5 minutes

Sample roughly **every 5 minutes**. That cadence is the sweet spot for home air:

- **Fine enough to catch real events.** A 5-minute interval resolves cooking spikes, shower humidity bursts, HVAC on/off cycles, and vacuum-induced particle clouds. At 15–30 minutes you smear these into the baseline and lose the very signatures that tell you what's happening.
- **Coarse enough to stay cheap and quiet.** Five minutes is 288 readings a day, ~105,000 a year — trivial for a spreadsheet or a small time-series database, and comfortably inside the request limits of typical consumer sensor APIs (a 5-minute poll is a small fraction of a 120-requests/hour cap). Going to 1-minute quadruples storage and multiplies sensor noise for little diagnostic gain.

The counterintuitive part: **you sample fast but you don't *alert* fast.** Raw 5-minute data is too jittery to threshold directly. Collect at 5 minutes for the diagnostic detail, then compute alerts on short **rolling aggregates** (medians over 30–90 minutes; 6-hour means for slow trends). Fine sampling feeds a calm decision layer — it doesn't drive one alert per reading.

---

## Sustained-vs-instantaneous thresholds (the core noise killer)

The biggest source of false alarms is alerting on a single reading crossing a line. Air is spiky; a lone high sample is almost always noise or a transient (someone walked past with a hot pan). The fix is to require **persistence**, and to **escalate** as persistence grows:

- **Warning after ~30 minutes** above the level.
- **Critical after ~90 minutes** above it.
- **A cooldown** (e.g., 60 minutes per tier) so one noisy patch can't re-page you repeatedly, and independent cooldowns per tier so a warning that's already fired can't suppress the later escalation to critical.

Concretely, a workable indoor-PM2.5 rule: pick an absolute indoor threshold (this home used **5 µg/m³**), then require the **median** of the last 30 minutes above it for a warning and the median of a real 90-minute window above it for critical. Using the median over a window — not the latest point — makes the trigger robust to single-sample outliers. Tuned this way, the system settled to roughly **2–3 alerts a week** — few enough that each one gets read.

### The slope gate: don't alarm on something that's already fixing itself

A spike that's **on its way down** needs no alarm — it's resolving on its own (the classic case: cooking, which spikes then decays over 30–60 minutes). So before firing a warning, check the trend: compare the current 30-minute median to the previous 30-minute median, and **suppress the alert if the signal is decaying** (this home suppressed when the slope was at least −0.5 µg/m³ per 30 min). Only a level that's high *and holding or rising* is worth a message. This single check removes most cooking false-positives while still catching a genuine filtration failure, which rises and *stays* up.

---

## Indoor-spike detection: is it the filter, or is it you?

The most useful routing decision an air monitor can make: **when indoor PM2.5 exceeds outdoor by a margin, the source is inside** — and no amount of filtration or fresh air fixes a source you're actively feeding. Detect it directly: if `indoor − outdoor ≥ ~5 µg/m³`, flag it as an **indoor event**, and treat it differently from a filter problem:

- Route indoor-source spikes as **advisory** (informational), not as filter warnings. They're expected and usually self-clearing — the wrong thing to escalate.
- Make the *advice* conditional on outdoor air: if outdoor is clean (say ≤ 25 µg/m³), boosting ventilation will clear the spike faster; if outdoor is dirty, more fresh air imports particles, so the right move is a portable HEPA unit or simply waiting it out.
- Hand off cleanly at the boundary: when outdoor air is itself high (this home used ≥ 10 µg/m³), **stop running the indoor-source check** and let the outdoor-AQI logic own that regime, so you don't get two alerts for one situation.

This is also why filter-efficiency alerts must exclude indoor-source moments (see next section) — measuring your filter mid-cook measures your stove.

---

## Reliability-gate your efficiency alerts

The [filter-efficiency method](filter-efficiency.md) only produces a trustworthy number under specific conditions, and your *alerting* must enforce them, not just your dashboard. Before computing an efficiency alert, keep only readings where:

1. **Outdoor PM2.5 is above the seasonal floor** (below it, the efficiency formula divides by near-zero and screams false failures — the critical caveat from the efficiency page), and
2. **Indoor ≤ outdoor** (drops the cooking/indoor-source moments that would otherwise read as negative efficiency).

Require a **minimum number of qualifying readings** (this home needed at least ~5 in the window) before alerting at all — if too few readings qualify, the honest state is "can't assess right now," not a number. Then alert on the **median** of the qualifying readings crossing a threshold (this home used **75% for a warning, 65% for critical**). Median, not mean, because a couple of outliers shouldn't move the call.

---

## Calibrate thresholds to your *own* history, by season

Hand-picked thresholds are guesses. Your home has the data to do better. Two moves make thresholds fit reality:

**1. Seasonal minimum-outdoor floors.** "Clean enough to skip" and "dirty enough to measure against" both shift with the seasons. A single fixed floor either throws away every summer reading or trusts unreliable winter noise. Split it:

| Season | Minimum outdoor PM2.5 to trust efficiency |
|---|---|
| Winter (dirtier air) | ~10 µg/m³ |
| Summer (cleaner air) | ~5 µg/m³ |
| Spring / Fall | ~7 µg/m³ |

**2. Learn the alert thresholds from your own lower tail.** Rather than declaring "75% = warning" a priori, take each season's history of *valid* efficiency readings and set the warning at, say, the **10th percentile** and critical at the **5th percentile** of that season's distribution. Now an alert means "unusually bad *for this home, this season*," which is exactly what you want. Re-run the calibration periodically (monthly is plenty) as seasons and conditions change, and require a decent sample (e.g., ≥ 500 readings per season) before trusting the fit. Calibrated this way, one home's numbers landed near **winter 74%/62%, summer 77%/63%, spring-fall 70%/59%** (warning/critical) — close to the hand-picked defaults, but *earned* from the data and self-adjusting.

### Adaptive baselines beat global thresholds

For metrics with strong seasonal or daily swings (CO₂ especially), a single global threshold misfires both ways: a winter-normal reading looks alarming against the annual average, and a genuine summer anomaly hides beneath it. A locally-adaptive baseline fixes this. One lightweight approach: fit a **LOWESS** smoother (local regression) through the series, then flag points whose residual exceeds ~**1.5× the residual standard deviation**. Resample to a coarse grid first (6-hour means work well) so you're detecting real excursions, not sensor jitter. The anomaly threshold now floats with the local trend — a 900 ppm CO₂ reading can be normal in winter and anomalous in summer, and the system judges each correctly.

---

## Outdoor-AQI-driven control, with hysteresis

If you automate (or semi-automate) ventilation based on outdoor air, build in **hysteresis** so it doesn't flap on and off at the boundary. Use two different thresholds with a gap between them and a small state machine:

- Outdoor PM2.5 (1-hour average) rises to **~35 µg/m³** → recommend/turn ventilation (ERV, whole-house fan) **off**, seal up.
- It falls back to **~15 µg/m³** and stays there → **all-clear**, resume fresh air.

The gap between 35 (shut) and 15 (reopen) is deliberate: a single threshold would toggle every time the reading wobbled across it. Only the *edges* fire an alert, and the system remembers its current state between checks. Note this ~35 is the **hard automated cutoff** — in practice you'd start *dialing back* fresh air manually earlier, around the ~20 µg/m³ mark from [the ERV dilemma](what-a-year-of-data-taught-me.md), well before the automatic seal-up trips. This is the automated version of the ventilate-vs-seal-up decision in the [wildfire playbook](wildfire-smoke.md).

---

## Time-based tracking for what efficiency can't see

Not every filter sits in the measured air path. Small in-room or zone filters protect individual blowers but don't move the indoor-vs-outdoor PM2.5 differential, so **efficiency monitoring is blind to them.** For those, fall back to honest **time-based reminders** — but make them well-behaved:

- Track "installed on" dates and a target interval (e.g., 90 days).
- Fire an **overdue** warning once it's past due, but **throttle to once per day** so it doesn't nag every hour.
- Give **advance notice at discrete milestones** (e.g., 14 / 7 / 3 / 1 days out), each firing exactly once as it's crossed — enough lead time to buy the filter, without a running countdown.

The dividing line is worth stating plainly: **measure what's measurable, schedule what isn't** — and don't pretend a calendar reminder is a performance measurement.

---

## Data-gap detection: catch the monitor going blind

The failure mode that quietly defeats every alerting system: **the data stops and nobody notices.** A silent sensor produces no high readings, so a naive alerter reports "all clear" forever. Guard against it explicitly:

- **Know each sensor's expected cadence** and alert when it goes quiet past a tolerance — a 5-minute sensor missing for an hour is a problem; a battery-powered hourly sensor needs a looser window (say 3 hours) before you worry.
- **Check by time-since-last-reading, not by row count.** A row-count window can't tell a multi-day outage from a busy hour.
- **Iterate the sensors you *expect*, not the ones you *see*.** This is the subtle bug: if you only loop over sensors present in recent data, a sensor that stopped days ago simply vanishes from the loop and is never flagged. Loop over the expected roster so an absent sensor is conspicuous.
- **Alert on both stop and recovery.** A "sensor stopped" critical when it goes silent, and a "sensor resumed" note when it comes back, so you know the gap's boundaries.

Treat a monitoring outage as a first-class alert, at least as important as a bad reading — because a blind monitor is the one failure that hides all the others.

---

## Optional: pressure-change alerts for the weather-sensitive

If someone in the home is barometric-pressure sensitive (migraines, joint pain — a real effect for a subset of people), the same infrastructure can give a heads-up. Pull barometric pressure from a public weather API and watch for **rapid drops**: e.g., a fall of **≥ 6 hPa over 6 hours** as a realized-change warning, and a forecast drop of similar size over the next 12 hours as a preventive heads-up. This is comfort/quality-of-life, not an air-quality alarm — keep it clearly separated from your particle and CO₂ alerts so it never dilutes them.

The engineering lesson here generalizes to any external-API input: **fail open with a short-lived cache.** On a fetch error, serve the last good value (up to some max age, e.g., 24 hours) but **never re-fire alerts from stale data** — degrade to silence, don't degrade to noise.

---

## Calibration checklist

- [ ] Sample ~5 min; compute alerts on rolling medians (30–90 min), not raw points.
- [ ] Require **sustained** exceedance (e.g., 30-min warning / 90-min critical) with per-tier cooldowns.
- [ ] Add a **slope gate**: suppress alerts on a signal that's already decaying.
- [ ] Detect **indoor-source spikes** (indoor − outdoor ≥ ~5 µg/m³) and route them as advisory, not filter alarms.
- [ ] **Reliability-gate** efficiency alerts: outdoor above the seasonal floor, indoor ≤ outdoor, enough samples, use the median.
- [ ] **Calibrate seasonally** from your own history (learn thresholds from each season's lower tail); re-run monthly.
- [ ] Use **adaptive baselines** (e.g., LOWESS residuals) for metrics with big seasonal/daily swings.
- [ ] Add **hysteresis** to any on/off control (shut and reopen at *different* levels).
- [ ] **Time-based reminders** for filters efficiency can't measure — throttled, with milestone lead time.
- [ ] **Data-gap detection** by time-since-last-reading, iterating the *expected* sensor roster; alert on stop and resume.
- [ ] **Fail open**: under missing/stale/ambiguous data, go quiet — never invent an alarm.

Every item above trades a little more logic for a lot less noise. That trade is the whole game: the goal isn't more alerts, it's alerts you'll still believe on the day one of them saves you a bad night's sleep.
