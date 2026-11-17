# Appendix C. Prototype brief

The spec I gave Claude Code to build the prototype. It was refined in several rounds; this is the final version.

## 1. Goal

A reviewer opens one link and understands in a minute:

1. what the user sees on the phone;
2. how the experiment runs;
3. which metrics decide and what decision follows;
4. which assumptions drive the expected impact.

## 2. Constraints

1. One self-contained HTML file: HTML, CSS and vanilla JS. No backend, no external libraries or fonts. Works from GitHub Pages.
2. Fictional app brand "Glow". All text in English.
3. All numbers, copy and model defaults in one config object, so they can change in one place.
4. Simulated data is labelled as simulated. Model inputs are labelled as assumptions.
5. Works on desktop and on a phone screen.

## 3. Page layout

1. Header: title, one-line idea, three links (user flow, experiment design, impact model).
2. Demo stage: the phone in the centre, a caption next to it that explains each step, a narrow controls column on the right.
3. Document below the stage: Experiment design, Readout (simulated), Impact model.

## 4. User flow on the phone

1. Home: current glucose, trend arrow, day chart with the 70–140 mg/dL target band, cartridge day 6 of 14. In the test group, a "Sugar spike alerts" card.
2. Value screen before the permission prompt: sugar spike → dip → hunger → snacking; ~300 kcal a day; walking lowers the spike ~17%; up to 0.3 kg of extra fat a week; at most 2 push notifications a day, never at night.
3. iOS-style permission prompt: Allow / Don't Allow.
4. Simulated lunch: the chart animates 2 hours in ~16 seconds. When glucose rises 30+ mg/dL within 30 minutes, the test group gets a push notification with no buttons: "Glucose is rising after lunch. Walk for 10 minutes now. A lower spike means less hunger and less snacking later."
5. The user walks or ignores it. Steps come from Apple Health. With a walk, the curve bends lower (peak 138 vs the usual 162). Without a walk, the dip comes and the app explains that cravings hit now.
6. Week summary: sugar spikes walked off, average spike on walk days, weight trend.

Control group: the standard app. The same trigger fires silently and is logged. The user can still walk or ignore: walking lowers the spike for everyone; the push notification only raises how many users walk.

## 5. Experiment design section

1. Hypothesis and evidence.
2. Who: new weight-loss users without diabetes in their first 14 days.
3. Split: 50/50 at user level; in control the trigger runs silently.
4. Trigger rule: +30 mg/dL within 30 min after a meal; 07:00–22:00; max 2 push notifications a day. "Walked" = 500+ steps within 30 min.
5. Metrics: on-track share at day 28 (decision metric, proxy for M3 retention); funnel; post-meal glucose rise; guardrail – cartridge reorder rate at day 28 must not drop; M3 retention compared at day 90.
6. Decision rule written before launch: ship if on-track goes up 3+ pp and reorders do not drop; iterate if walking is up but on-track is flat; stop if the guardrail is breached.

## 6. Readout (simulated)

Three scenarios with a test funnel, a metric table (control, test, difference, status) and a decision:

1. It works: on-track 35.1% → 39.3%, reorders up → ship.
2. They walk, weight doesn't move → iterate; the next test adds food swaps.
3. Users get annoyed: reorders drop → stop; cut to 1 push notification a day.

## 7. Impact model

Editable inputs (all assumptions): on-track share without the feature 35%; M3 retention of on-track users 55% and of other users 12%; allow notifications 85%; walk regularly with push notifications 35%; walk anyway without them 10%; share of extra walkers who become on-track 31%.

Formulas:

1. extra walkers = walk with push − walk anyway
2. moved = (1 − on-track share) × allow × extra walkers × become on-track
3. on-track in test = on-track share + moved
4. M3 retention = on-track × 55% + others × 12%
5. Sample size for two proportions, 80% power, alpha 0.05.

Expected result: on-track 35.0% → 39.3%; M3 retention 27.1% → 28.9% (+1.8 pp); ~2,000 users per group for on-track, ~9,300 for M3 retention.
