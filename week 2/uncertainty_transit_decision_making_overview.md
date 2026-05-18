# Detailed Overview: *Uncertainty Displays Using Quantile Dotplots or CDFs Improve Transit Decision-Making*

**Article:** Michael Fernandes, Logan Walls, Sean Munson, Jessica Hullman, and Matthew Kay. *Uncertainty Displays Using Quantile Dotplots or CDFs Improve Transit Decision-Making.* CHI 2018 Honourable Mention.

**Core topic:** How different ways of displaying uncertainty in real-time bus arrival predictions affect actual decision-making, not just probability-reading accuracy.

---

## 1. Executive Summary

This article studies whether showing uncertainty in real-time transit predictions helps people make better decisions about when to leave for a bus. Many everyday predictive systems, including transit apps, weather apps, and travel-time tools, usually show a single point prediction such as "the bus arrives in 10 minutes." The authors argue that point estimates hide uncertainty and can lead users to make decisions as if the prediction were exact, even though buses can arrive earlier or later than expected.

The study builds on earlier work showing that people can extract probabilities more precisely from **quantile dotplots** than from traditional uncertainty visualizations. However, the earlier work focused mainly on whether users could read probabilities from a visualization. This paper asks a more practical question: **Do uncertainty displays actually improve the quality of users' decisions?**

To answer this, the authors ran a controlled, incentivized online experiment. Participants repeatedly decided when to arrive at a bus stop based on different uncertainty displays. Their choices were scored using a payoff system that rewarded useful time spent away from the bus stop and penalized waiting too long or missing the bus. The best-performing displays were **quantile dotplots**, especially the 50-dot version, and **cumulative distribution function (CDF) plots**. These displays helped participants make decisions that were closer to the optimal strategy and more consistent over time.

The main finding is that uncertainty visualizations can improve everyday decision-making when they are designed to fit the user's task. In this transit context, **low-density quantile dotplots and CDFs outperformed point estimates, text-only uncertainty, interval plots, and probability density plots**.

---

## 2. Research Problem and Motivation

### 2.1 The problem with point predictions

The paper begins from the observation that everyday predictive systems often simplify uncertain information into a single value. For example, a transit app may say a bus will arrive in 10 minutes, but the true arrival time could vary because of traffic, GPS/location error, schedule disruption, or changing road conditions.

A point prediction is easy to read quickly, but it can create a **false sense of precision**. Users may act as though the value is certain, even when the prediction is only the most likely outcome.

### 2.2 Why transit is a useful test case

Transit prediction is a strong domain for studying uncertainty because riders often make repeated, time-sensitive decisions with real consequences. A rider may need to decide whether to:

- leave immediately or wait a few more minutes;
- continue an activity before walking to the stop;
- risk missing the bus to avoid waiting outside;
- arrive early to guarantee catching the bus;
- accept a higher risk of missing the bus when the destination is less important.

These decisions require balancing **risk**, **waiting time**, and **value of time spent elsewhere**.

### 2.3 Main research gap

Prior work had shown that some uncertainty displays help users estimate probabilities more accurately. This paper argues that accurate probability extraction is not enough. A display is only practically useful if it supports better decisions.

The central question is therefore:

> Do uncertainty displays that help users read probabilities also help them make better real-world decisions?

---

## 3. Main Contributions

The article contributes three main findings to human-computer interaction and uncertainty visualization research.

### 3.1 Evidence that uncertainty improves transit decisions

The authors compare uncertainty displays against a control condition with no uncertainty information. They find that showing uncertainty can improve decision quality in a bus-catching scenario.

### 3.2 Comparison of multiple uncertainty representations

The experiment compares several display types:

- no-uncertainty point-prediction control;
- textual predictive intervals;
- interval plots;
- probability density function (PDF) plots;
- PDF + interval hybrid plots;
- quantile dotplots with 20 dots;
- quantile dotplots with 50 dots;
- complementary cumulative distribution function plots.

This range allows the authors to test whether more expressive visualizations outperform simpler representations such as text or intervals.

### 3.3 Method for evaluating decision quality

The paper adapts an experimental economics approach. Participants are financially incentivized through a simulated coin/reward system. This makes the task closer to real decision-making because users face tradeoffs and consequences, rather than simply answering comprehension questions.

---

## 4. Background: Why Uncertainty Communication Matters

### 4.1 People often misunderstand uncertainty

The paper situates itself in a long line of research on judgment under uncertainty. People may rely on heuristics, misunderstand probability, or treat uncertain forecasts as deterministic. This is especially important in interface design because designers may avoid uncertainty displays out of fear that users will be confused.

### 4.2 But uncertainty can improve decisions

The authors review evidence showing that uncertainty information can help users make better decisions in domains such as weather, driving range estimation for electric vehicles, medical decision-making, and transit planning.

A key argument is that uncertainty can improve trust because it makes the system's limitations more transparent. Rather than pretending the prediction is exact, the interface helps users understand the range of plausible outcomes.

### 4.3 Frequency-based reasoning

The paper draws on prior research showing that people often reason better with **frequencies** than with abstract probabilities. For example, users may understand "8 out of 10 outcomes" more easily than "80%." Quantile dotplots use this idea by representing possible outcomes as dots that users can count or visually estimate.

---

## 5. Interface and Display Design

The study adapts the **OneBusAway** real-time transit application interface. The authors preserve the general look and feel of a familiar transit app while adding uncertainty information to the bus arrival rows.

### 5.1 Modified OneBusAway interface

The authors compare the original OneBusAway-style display with a modified interface containing uncertainty information. The modified interface shows each bus route with a visual representation of the predicted arrival-time distribution.

![Figure 1: Original OneBusAway-style interface and modified dot50 uncertainty interface](uncertainty_transit_overview_assets/figure1_oba_interface_dot50_page4.png)

**Figure 1 overview:** The left phone screen shows a conventional OneBusAway-style list with point predictions such as a bus arriving in a certain number of minutes. The right screen shows the experimental interface with dot-based uncertainty distributions on a timeline.

### 5.2 Content-aware scrolling

Because a mobile display has limited horizontal space, later bus predictions could otherwise fall off the screen. The authors implemented a **content-aware scrolling** technique that shifts the timeline as users scroll so that later predictions remain visible.

### 5.3 Removing “late” annotations

The real OneBusAway app includes indicators such as whether a bus is late relative to its scheduled arrival. The researchers removed these annotations because pilot participants sometimes misused them as uncertainty indicators. Since the predictive distribution already incorporated uncertainty, these annotations risked adding noise to the experimental task.

---

## 6. Predictive Model for Bus Arrival Times

The experiment needed realistic arrival-time uncertainty. The authors used predictive distributions based on prior work by Kay et al. These distributions were generated from Seattle-area bus arrival data and modeled using a **Box-Cox t regression model**.

Each distribution had:

- a most probable arrival time;
- a plausible uncertainty range;
- a minimum mode of 5 minutes from “now”;
- a maximum mode of 25 minutes from “now.”

The goal was not to build a new bus prediction model, but to evaluate how different displays of the same predictive uncertainty affect decisions.

---

## 7. Uncertainty Display Conditions

The experiment tested multiple display types to compare how representation format affects decision quality.

### 7.1 No-uncertainty condition

This condition represents the status quo. Users see a point estimate of arrival time but no distribution or interval information. It serves as the control condition.

### 7.2 Textual predictive intervals

Text displays describe uncertainty using a probability interval in natural language. The study tested three text conditions:

- **text60:** 60% predictive interval;
- **text85:** 85% predictive interval;
- **text99:** 99% predictive interval.

The reason for testing three intervals is that a text display can only communicate one risk threshold at a time. The authors wanted to see whether text performance depended on the specific interval shown.

### 7.3 Interval plots

Interval plots show a range of plausible arrival times. The paper notes that interval plots are common and familiar, but they compress the distribution and do not fully show its shape.

### 7.4 Probability density function plots

PDF plots show the shape of a probability distribution using area. They can be visually appealing and familiar, but estimating exact probabilities from areas is difficult for many users.

### 7.5 Quantile dotplots

Quantile dotplots represent possible outcomes as dots sampled from evenly spaced quantiles of the predictive distribution. Each dot corresponds to an equal portion of probability.

The study tested:

- **dot20:** 20-dot quantile dotplot;
- **dot50:** 50-dot quantile dotplot.

The key advantage is that users can reason in counts. For example, if 5 out of 50 dots occur before a certain time, that region represents about 10% of possible outcomes.

![Figure 2: Example of dot50 display with and without most probable arrival time](uncertainty_transit_overview_assets/figure2_dot50_row_page5.png)

**Figure 2 overview:** The figure shows a single bus-arrival row in the dot50 condition. The top version includes the most probable arrival time; the bottom version omits it. The study collected both variants but later pooled them because pilot results showed similar performance.

### 7.6 PDF + interval hybrid

This condition combines a probability density plot with a marked interval. The intent is to provide both distribution shape and a simpler interval cue.

### 7.7 Complementary CDF plot

A complementary cumulative distribution function plot shows the probability that the bus has **not yet arrived** by a certain time. This directly matches the rider’s practical question:

> If I arrive at the stop at this time, what chance do I still have of catching the bus?

The authors selected the complementary CDF because it maps better to transit decision-making than a standard CDF.

---

## 8. Online Experiment Design

### 8.1 Overall procedure

The experiment used a between-subjects repeated-measures design. Each participant saw one display type and completed multiple bus-catching decision trials.

The general flow was:

1. The participant reads a bus-catching scenario.
2. The participant sees a bus arrival prediction using their assigned display condition.
3. The participant decides when to arrive at the bus stop.
4. The bus arrival is simulated from the predictive distribution.
5. The participant receives feedback and a reward/penalty based on the outcome.
6. The participant repeats this process across many trials.

![Figure 3: General experimental flow](uncertainty_transit_overview_assets/figure3_experiment_flow_page6.png)

**Figure 3 overview:** The experiment walks users through scenario instructions, prediction display, decision entry, simulated outcome, and reward feedback. This repeated structure allows the researchers to study learning over time.

### 8.2 Decision scenarios

The authors created realistic scenarios in which participants had to balance useful time away from the stop against the risk of missing the bus.

The three scenario types were:

#### Brunch with Friends

Participants are watching TV before leaving to meet friends for brunch. They earn coins for watching TV and for being at brunch, but lose coins for waiting at the bus stop.

#### Sunday Festival

Participants are enjoying a festival before going home. They earn coins for time at the festival and time at home, but lose coins for waiting at the stop.

#### Sunday Museum

Participants are at a museum on a rainy evening and want to return home. This scenario places different values on museum time, home time, and waiting time.

### 8.3 Incentive system

The experiment uses coins as a payoff mechanism. Participants gain or lose coins based on the consequences of their decisions. Coins are then translated into bonus compensation.

This structure matters because it forces realistic tradeoffs. Arriving too early may avoid missing the bus but increases waiting costs. Arriving too late may preserve valuable activity time but increases the risk of missing the bus.

---

## 9. Decision Quality Metrics

The paper evaluates decisions using a formal utility-based metric.

### 9.1 Expected payoff

Expected payoff is the average payoff a participant would receive for a chosen arrival time, weighted across all possible bus arrival outcomes. This is better than using the participant's actual payoff from a single simulated outcome because actual outcomes include random noise.

### 9.2 Optimal payoff

Optimal payoff is the best possible expected payoff for that trial. It is calculated by identifying the response time that would maximize expected value under the known predictive distribution and payoff function.

### 9.3 Expected/optimal payoff ratio

The key decision-quality metric is:

```text
expected payoff / optimal payoff
```

A value closer to 1 means the participant made a more rational decision relative to the optimal strategy. For example:

- 1.00 = optimal decision;
- 0.95 = decision achieves 95% of optimal payoff;
- 0.80 = substantially worse decision.

The authors analyze both the mean of this ratio and its standard deviation. A good display should produce decisions that are both high-quality on average and consistent across users/trials.

---

## 10. Statistical Modeling Approach

The authors use a Bayesian beta regression model because the response variable, expected/optimal payoff, lies between 0 and 1 and tends to bunch near 1.

The model includes:

- display type;
- trial number;
- interaction between display type and trial;
- participant-level random effects;
- scenario-level random effects;
- variation in the beta distribution precision parameter.

This allows the researchers to estimate both:

- whether average decision quality improves over time;
- whether decision consistency improves over time.

The model was pre-registered after pilot testing, strengthening the credibility of the analysis plan.

---

## 11. Participants

The final dataset included **408 participants** from Amazon Mechanical Turk. Participants were Master Turkers in the United States. The final demographic sample with complete information included 385 participants.

Key participant details:

- average completion time: about 10 minutes;
- 45% women;
- median age: 35;
- participants completed up to 40 trials;
- final analysis included those who completed at least 31 trials.

---

## 12. Main Results

### 12.1 Uncertainty displays generally improved decisions

Displays with uncertainty usually performed as well as or better than the no-uncertainty control condition. The best displays helped participants make decisions close to the optimal strategy.

### 12.2 Dot50 performed best overall

The **50-dot quantile dotplot** was the strongest condition. Its decisions were:

- approximately **97% of optimal** on average;
- about **5 percentage points better than control**;
- more consistent than control, with lower within-subject standard deviation.

This suggests that quantile dotplots do not merely help people read probabilities; they also help people act on them.

### 12.3 CDFs performed nearly as well

Complementary CDF plots also supported strong decision-making. This is important because CDFs have sometimes been considered difficult for lay users. In this task, however, the complementary CDF matched the decision question well: "What chance do I still have of catching the bus if I arrive at this time?"

### 12.4 Dot20 also performed well

Dot20 performed well, though dot50 was generally better. This suggests that low-density dotplots are useful, but 50 dots may provide a better balance between countability and distribution detail than 20 dots in this task.

### 12.5 Text displays were sensitive to the interval shown

Text displays did not behave consistently. The text99 and text60 conditions performed reasonably well, but text85 performed poorly and resembled the no-uncertainty condition.

This supports one of the paper’s important claims: text can be simple, but it is not flexible. A single text interval may not match the user's current risk tolerance or decision context.

### 12.6 PDFs and intervals were less effective

PDFs, PDF-interval hybrids, and interval plots did not perform as well as dotplots or CDFs. The likely issue is that these displays either require users to estimate probability from area or compress the distribution too much.

---

## 13. Learning Over Time

A major strength of this paper is that it studies repeated decision-making rather than one-time comprehension.

![Figure 4: Learning curves across display conditions](uncertainty_transit_overview_assets/figure4_learning_curves_page9.png)

**Figure 4 overview:** This figure shows model-predicted performance over 40 trials. The top row presents posterior predictive intervals for expected/optimal payoff. The middle row shows uncertainty around mean performance. The bottom row shows uncertainty around the standard deviation of performance. Dot50, CDF, and dot20 show strong learning and become more consistent over time.

Key learning-related findings:

- Most conditions show some learning across trials.
- Dot50, CDF, and dot20 improve most clearly.
- These conditions improve not only in mean decision quality but also in consistency.
- Some conditions, especially no-uncertainty and text85, show flatter learning curves.

This suggests that participants can learn how to use well-designed uncertainty displays through feedback.

---

## 14. Final-Trial Comparisons

![Figure 5: Final-trial differences in mean and standard deviation](uncertainty_transit_overview_assets/figure5_final_trial_comparisons_page10.png)

**Figure 5 overview:** This figure compares each condition against the control condition and against the best-performing dot50 condition. Quantile dotplots and CDFs perform best on average and are the most consistent. Text performance depends heavily on which interval is shown.

Final-trial findings:

- Dot50, CDF, and dot20 outperform most other conditions.
- Dot50 has the strongest combination of high mean performance and low variance.
- Text99 and text60 approach the performance of dot20 in some cases.
- Text85 remains weak, reinforcing the sensitivity of textual uncertainty to the selected probability level.
- Lower standard deviation means that the display helps not only average users but also weaker-performing users.

---

## 15. Interpretation of Why Dotplots and CDFs Worked

### 15.1 Quantile dotplots support frequency reasoning

Dotplots convert probability into countable outcomes. This supports more intuitive reasoning, especially when users can quickly count or estimate dots near a threshold.

For example, in a dot50 display:

- 1 dot = 2% probability;
- 5 dots = 10% probability;
- 25 dots = 50% probability.

This allows users to connect visual evidence to risk tolerance.

### 15.2 CDFs align with the decision task

The complementary CDF directly answers a rider-centered question: "What is the chance the bus has not arrived yet by the time I reach the stop?" Because the display encodes a cumulative probability, users can read the probability of still catching the bus at a chosen arrival time.

### 15.3 Expressive displays adapt to different contexts

The paper emphasizes that different situations require different risk thresholds. A rider going to an important meeting may want a 99% chance of catching the bus, while someone going to a casual event may accept more risk.

Dotplots and CDFs allow users to evaluate many possible thresholds. Text intervals only show one threshold, making them less adaptable.

---

## 16. Discussion and Implications

### 16.1 Uncertainty should not be hidden by default

The study provides evidence against the assumption that uncertainty will necessarily confuse users. In this experiment, uncertainty displays improved decision-making when designed appropriately.

### 16.2 Display design should match the decision structure

The best displays are not merely visually attractive; they support the user’s decision task. In this case, the task is choosing an arrival time while balancing waiting cost against missing-bus risk.

### 16.3 Simpler is not always better

Text and intervals are simpler than dotplots or CDFs, but they may be too limited. The article shows that lower-fidelity uncertainty displays can underperform more expressive visualizations.

### 16.4 Consistency matters

A display that improves the average decision but produces highly variable results may still fail many users. The paper therefore values both mean decision quality and variance reduction. Dot50 is especially strong because it improves both.

### 16.5 Generalization to other domains

The authors argue that these findings may generalize to other everyday decisions where:

- users must choose a threshold;
- uncertainty matters for decision quality;
- no single probability interval is universally optimal;
- users benefit from adapting risk tolerance to context.

Possible domains include weather decisions, travel planning, arrival-time estimation, delivery tracking, medical risk displays, or energy/range prediction.

---

## 17. Limitations

The authors acknowledge several limitations.

### 17.1 Simulated decision environment

The experiment used realistic scenarios and incentives, but it was still an online simulation. Real bus riders may behave differently while walking, multitasking, stressed, or exposed to weather.

### 17.2 Shared utility function

The experiment used the same payoff structure for participants within scenarios. In real life, people have personal preferences and changing priorities.

### 17.3 Need for field studies

The authors call for longitudinal real-world deployment studies. Such studies could examine not only decision quality but also trust, blame, satisfaction, and whether users feel responsible when uncertainty information leads them to take a risk.

### 17.4 Possible emotional effects

Earlier work suggested that some users may dislike uncertainty displays because they shift responsibility from the app to the user. For example, if a rider misses a bus after seeing uncertainty, they may feel complicit in the bad outcome rather than simply blaming the app.

---

## 18. Key Takeaways

1. **Point predictions can mislead users** by hiding uncertainty and creating false precision.
2. **Uncertainty displays can improve everyday decisions** when they are designed around the user’s actual task.
3. **Quantile dotplots and complementary CDFs performed best** in this transit decision-making experiment.
4. **Dot50 was the strongest overall display**, achieving high average decision quality and low variance.
5. **Text uncertainty is fragile** because its usefulness depends on which probability interval is communicated.
6. **Users can learn to use uncertainty displays over time**, especially when feedback is available.
7. **Decision quality should be evaluated directly**, not inferred only from probability-comprehension tasks.
8. **Expressive uncertainty displays are valuable** when users need to adapt risk tolerance across different situations.

---

## 19. Conceptual Comparison Table

| Display Type | What It Shows | Strengths | Weaknesses | Study Outcome |
|---|---|---|---|---|
| No uncertainty | Point prediction only | Fast and familiar | Hides uncertainty; false precision | Worst or near-worst performance |
| Text interval | One probability threshold in words/numbers | Compact and easy to read | Not flexible; sensitive to chosen interval | Mixed; text85 weak, text60/text99 better |
| Interval plot | Plausible range of outcomes | Familiar and simple | Compresses distribution; limited threshold flexibility | Weaker than dotplots/CDFs |
| PDF plot | Distribution shape by area | Visually familiar/appealing | Probability estimation from area is difficult | Moderate, below dotplots/CDFs |
| PDF + interval | Density shape plus interval cue | More information than interval alone | Still may not support threshold decisions well | Moderate |
| Dot20 | 20 countable outcomes | Simple frequency reasoning | Less distribution detail | Strong |
| Dot50 | 50 countable outcomes | Good balance of detail and countability | More visually complex than text | Best overall |
| Complementary CDF | Probability bus has not arrived by a time | Directly maps to catching-bus probability | May be unfamiliar at first | Nearly best overall |

---

## 20. Plain-Language Bottom Line

The article shows that uncertainty should not be treated as extra information that only experts can use. When uncertainty is displayed in a way that matches the decision people are trying to make, non-experts can use it effectively. For bus arrival predictions, a dotplot or complementary CDF helps people decide when to leave more rationally than a simple point prediction. The best displays helped users avoid both unnecessary waiting and excessive risk of missing the bus.

