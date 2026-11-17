# Appendix B. Barriers and hypotheses

How we got from "weight-loss users churn" to one experiment.

## 1. Framing

1. Users who are on-track stay much longer (Appendix A, section 6). So the job is to make more users on-track.
2. We do not treat price as a cause. "Too expensive" is a symptom: the user does not get the value.
3. To become on-track, a user must change behaviour: eat less or move more. The sensor alone does not change behaviour.
4. Simplification: we look at one user. Couples and families (shared meals, a partner who also loses weight) are out of scope.

## 2. Why users are not on-track: 10 barriers

Weight: how often the barrier comes up in surveys, whether it predicts dropout, and whether it acts in months 1–3.

| # | Barrier | Weight | Evidence | Can the sensor help? |
|---|---|---|---|---|
| 1 | The scale doesn't move; expectations are too high | High | ≤2% loss in month 1 → ~5x more dropout (4 RCTs). 69% quit because results were "too slow" (MyNetDiary survey, n=2,000) | Yes: a daily signal of progress while the scale is flat |
| 2 | Hunger, cravings, tempting food | High | ~4.2 lapses a week; hunger and available tasty food predict lapses (Forman 2017, n=189). Appetite grows ~100 kcal/day per kg lost | Partly: find filling food without sugar dips |
| 3 | Food logging is a burden; users stop | High | Less than half still log by week 10; logging consistency explains 27% of 6-month weight loss (n=124) | Partly: the sensor sees each meal without a log |
| 4 | Stress and emotional eating, poor sleep | Medium-high | 40% overate from stress in the last month (APA) | No |
| 5 | Motivation fades; "all or nothing" after a lapse | Medium | 49% quit after the first lapse (Noom survey) | Weak |
| 6 | Eating out and with others | Medium | Lapses happen more with others and in restaurants (EMA, n=150) | No |
| 7 | No support or accountability | Medium | Remote coaching: −4.6 kg vs −0.8 kg over 24 months (POWER RCT, n=415) | No; needs a coach next to the sensor |
| 8 | Weekends and alcohol | Medium-low | Weight loss stops on weekends (CALERIE, n=48) | Partly: late snacks and alcohol show on the chart |
| 9 | No time to plan and cook | Medium-low | 53% don't plan meals | No |
| 10 | Generic advice | Low-medium | Personal advice beats generic advice for diet quality (Food4Me, n=1,607) | Yes: personal food response |

The sensor helps with barriers 1, 2, 3 and 10. A review of 23 studies (n=1,074) says a CGM changes eating for a short time but rarely meets weight goals without behavioural support. Glucose is not calories: the sensor cannot confirm a calorie deficit.

## 3. How the sensor can help a user lose weight

1. Satiety. A sugar spike after a meal is followed by a dip. The dip brings hunger, and the user snacks. People with big dips eat about 300 kcal more a day (ZOE PREDICT).
2. Fast feedback. Weight changes over weeks; the glucose chart answers in 30 minutes.
3. Meal timing. The sensor sees each meal and late snacks without a log.
4. A cue to move. Light walking after eating lowers post-meal glucose by about 17% (Buffey 2022, meta-analysis of 7 trials).

## 4. Idea pool

| Churn cause | Ideas |
|---|---|
| New knowledge runs out | One experiment per cartridge (e.g. "rice with or without a walk"); a diet test with a personal list of "safe" meals |
| Glucose is not weight | Link sugar and weight ("in weeks with steady sugar you lose X kg"); a weight forecast |
| Price stays, value falls | A discounted 3-month starter bundle; a maintenance mode with 1 cartridge a month; pause instead of cancel |
| The habit lives in the sensor | A sensor-free mode (photo → predicted response); a weekly coach review; a 21-day group challenge |
| Friction and failures | One-click replacement of a broken sensor; setup tips and explanations of odd readings |

## 5. Four hypotheses for the "sugar spike" moment

1. H1. Food swap by photo. The user photographs a meal. If it caused a dip, the app suggests a swap or a fix (add protein, vegetables first, smaller portion).
2. H2. Photo food log, like Cal AI. Food type, protein, rough calories, satiety tips.
3. H3. A meal prompt from the sensor. The sensor sees a rise and asks for a photo. This feeds H1 and H2.
4. H4. Walk after the spike. The sensor sees the rise and sends a push notification: walk for 10 minutes.

We chose H4:

1. It needs almost no engineering: the app already sends glucose alerts.
2. The user does not need to log or photograph anything.
3. The effect shows on the chart at once, before the scale moves (barrier 1).
4. The open question is one link: does a lower spike mean less hunger? The test checks it.

## 6. Rejected ideas

1. Free kitchen scale. Weighing every plate is the first thing users drop.
2. Free smart body scale. Most weight-loss users already own one; weight comes from Apple Health or a manual log.
3. Food swap by photo inside the first test. It is a second idea; it stays as the next step if users walk but weight does not move.
