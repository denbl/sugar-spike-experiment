# Appendix C. Prototype brief

The spec we gave Claude Code to build the prototype. After several rounds of edits, we rebuilt the prototype from scratch from this spec with a second model to try a different layout. This is the final version.

## 1. Goal

A reviewer opens one link and understands in a minute:

1. what the user sees on the phone;
2. how the experiment runs;
3. which metrics decide and what decision follows;
4. which assumptions drive the expected impact on retention and money.

## 2. Constraints

1. One self-contained HTML file: HTML, CSS and vanilla JS. No backend, no external libraries or fonts. Works from GitHub Pages.
2. Fictional app brand "Glow". All text in English.
3. All numbers, copy and model defaults in one config object, so they can change in one place.
4. Simulated data is labelled as simulated. Model inputs are labelled as assumptions.
5. Works on desktop and on a phone screen.
6. Less is more: nothing on the page repeats what is already visible on it.

## 3. Page layout

1. Header: title, one-line idea, expected result (on-track share at day 28, M3 retention, LTV per new user), three links (user flow, impact model, experiment design).
2. "On-track users" in the idea is a dotted term. A tap shows the definition: losing 0.5% or more of body weight a week by day 28.
3. Demo stage: the test phone and the control phone side by side, at the same moment of the same day. A short caption for each step on the left.
4. Under the phones, one large button for the next step: Start the experiment, Ask for notifications, Allow and start lunch, Play lunch, Next: week summary, See the impact model.
5. Below the stage: Impact model first, then Experiment design. The formulas are collapsed by default.

## 4. User flow on the phone

1. Home: current glucose, trend arrow, day chart with the 70–140 mg/dL target band, cartridge day 6 of 14. In the test group, a "Sugar spike alerts" card.
2. Value screen before the permission prompt: sugar spike → dip → hunger → snacking; ~300 kcal a day; walking lowers the spike ~17%; up to 0.3 kg of extra fat a week; at most 2 push notifications a day, never at night.
3. iOS-style permission prompt: Allow / Don't Allow.
4. Simulated lunch: the chart animates 2 hours in ~16 seconds. When glucose rises 30+ mg/dL within 30 minutes, the test group gets a push notification with no buttons: "Glucose is rising after lunch. Walk for 10 minutes now. A lower spike means less hunger and less snacking later."
5. Each phone has a Walks / No walk switch. With a walk, steps from Apple Health build up while glucose falls (peak 136 vs the usual 162). Without a walk, the dip comes and the app explains that cravings hit now.
6. Week summary: sugar spikes walked off, average spike on walk days, weight trend.

Control group: the standard app, no push. The same trigger fires silently and is logged. The user can still walk or not: walking lowers the spike for everyone; the push notification only raises how many users walk.

## 5. Experiment design section

1. Hypothesis and evidence.
2. Who: new weight-loss users without diabetes in their first 14 days.
3. Split: 50/50 at user level; in control the trigger runs silently.
4. Trigger rule: +30 mg/dL within 30 min after a meal; 07:00–22:00; max 2 push notifications a day. "Walked" = 500+ steps within 30 min.
5. Metrics: on-track share at day 28 (decision metric, proxy for M3 retention); funnel; post-meal glucose rise; guardrail – cartridge reorder rate at day 28 must not drop; M3 retention compared at day 90.
6. Decision rule written before launch: ship if on-track goes up 3+ pp and reorders do not drop; iterate if walking is up but on-track is flat; stop if the guardrail is breached.

## 6. Impact model

Editable inputs (all assumptions), in funnel order:

1. M3 retention of on-track users: 55%.
2. M3 retention of off-track users: 12%.
3. Share of off-track users in control: 65%.
4. Allow notifications: 85%.
5. Off-track users who walk after meals, control: 10%. Walking regularly = after at least every second spike.
6. Off-track users who walk after meals, test: 35%.
7. New walkers who reach on-track pace: 31%. A walk covers about 70% of the on-track pace, so only users close to the line cross it.

Money (market estimates):

8. Monthly refill, 2 cartridges: $99 (Stelo sells 2 sensors for $99).
9. Gross margin: 50% (Nutrisense).
10. Extra paid months per user kept to M3: 6 (kept users pay to about month 8, Nutrisense average tenure 7–8 months; lost users stop around month 2).

Formulas:

1. new walkers = walkers in test − walkers in control
2. moved to on-track = off-track share × allow × new walkers × reach on-track pace
3. on-track in test = on-track in control + moved
4. M3 retention = on-track × 55% + off-track × 12%
5. LTV per new user = M3 lift × extra paid months × monthly refill × gross margin
6. Sample size for two proportions, 80% power, alpha 0.05.

Expected result: on-track 35.0% → 39.3%; M3 retention 27.1% → 28.9% (+1.8 pp); LTV +$5.5 gross profit per new user (+$11 revenue); per 10,000 new weight-loss users +$109K revenue and +$55K gross profit; ~2,000 users per group for on-track, ~9,300 for M3 retention.
