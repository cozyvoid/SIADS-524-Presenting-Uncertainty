# Detailed Overview: “When (ish) is My Bus? User-centered Visualizations of Uncertainty in Everyday, Mobile Predictive Systems”

**Article:** Matthew Kay, Tara Kola, Jessica R. Hullman, and Sean A. Munson. *When (ish) is My Bus? User-centered Visualizations of Uncertainty in Everyday, Mobile Predictive Systems*. CHI 2016.  
**Topic area:** Human-computer interaction, mobile visualization, uncertainty visualization, transit prediction, user-centered design.  
**Core contribution:** The authors design and evaluate mobile visualizations that communicate uncertainty in real-time bus arrival predictions, introducing **quantile dotplots** as a compact discrete-outcome visualization for small screens.

---

## 1. Big-picture purpose of the article

The article addresses a common problem in everyday predictive systems: users often see a single predicted value, such as “bus arrives in 5 minutes,” even though the actual outcome is uncertain. The authors argue that this can create **false precision**, leading users to make decisions as if the prediction were exact.

The motivating example is a commuter who sees that her bus is predicted to arrive in five minutes, decides to get coffee, but misses the bus when it arrives earlier than expected. The point estimate was technically useful, but it did not communicate the range of plausible arrival times.

The authors focus on **real-time transit prediction** because it is:

- Everyday and familiar to non-expert users.
- Time-sensitive: users make quick decisions while walking, waiting, or planning.
- Space-constrained: predictions are often viewed on mobile phones.
- Naturally uncertain: buses may arrive earlier or later than predicted.

The article’s central question is: **How can a mobile interface communicate uncertainty in bus arrival predictions in a way that ordinary users can understand quickly and use for real decisions?**

---

## 2. Main research goals

The authors identify three major goals:

1. **Understand user needs** around uncertainty in transit prediction.
2. **Design mobile visualizations** that communicate prediction uncertainty without overwhelming users.
3. **Evaluate which visualizations help users estimate probabilities most accurately, precisely, and confidently.**

They combine literature review, user survey, iterative design, and a controlled experiment.

---

## 3. Key contributions

The paper makes three major contributions:

### 3.1 Design requirements for uncertainty in mobile transit prediction

The authors derive requirements from prior uncertainty visualization research and from a survey of **172 OneBusAway users**. These requirements explain what information users need and how it should be presented in a mobile interface.

### 3.2 Candidate mobile interface designs

The authors propose interface layouts for presenting bus predictions with uncertainty. These include:

- **Bus-timeline layout:** each row shows one bus prediction.
- **Route-timeline layout:** each row shows multiple predicted buses for a route.

They also compare multiple ways to encode uncertainty visually.

### 3.3 Quantile dotplots

The authors introduce **quantile dotplots**, a discrete representation of a continuous probability distribution. Instead of showing uncertainty as a smooth density curve, quantile dotplots show a fixed number of dots placed at evenly spaced quantiles of the distribution.

This lets users reason about uncertainty using countable hypothetical outcomes, such as “3 out of 20 dots are earlier than this time.”

---

## 4. Why uncertainty matters in everyday predictions

The authors argue that point predictions are often insufficient because they hide uncertainty. A prediction such as “5 minutes” may mean:

- The bus is very likely to arrive near 5 minutes, or
- The bus could plausibly arrive anywhere between 1 and 9 minutes.

Those two situations require different decisions.

### 4.1 False precision

A point estimate can imply more certainty than actually exists. Users may overtrust the exact number and fail to plan for plausible variation.

### 4.2 Trust and transparency

The authors draw on prior research showing that communicating uncertainty can improve trust. If users understand that predictions are uncertain, they may be less surprised when predictions change or fail.

### 4.3 User agency

Instead of having the system simply say “leave now” or “you have time,” showing uncertainty lets users apply their own risk tolerance. For example:

- A user going to an important meeting may want to leave earlier.
- A user going to a casual event may tolerate more risk.
- A user deciding whether to get coffee may want to know the chance the bus comes early.

---

## 5. Background: uncertainty visualization concepts

The article reviews several approaches to visualizing uncertainty.

### 5.1 Extrinsic uncertainty annotations

Extrinsic annotations add uncertainty information beside or on top of another chart. Examples include:

- Error bars.
- Confidence intervals.
- Prediction intervals.
- Boxplot-style summaries.

The authors argue that these can be problematic because users may misunderstand them or treat them as secondary information.

### 5.2 Intrinsic representations

Intrinsic representations integrate uncertainty directly into the main visual encoding. Examples include:

- Density plots.
- Violin plots.
- Gradient plots.

The authors prefer intrinsic representations because uncertainty becomes part of the main display rather than an optional add-on.

### 5.3 Continuous vs. discrete uncertainty representations

Continuous visualizations, like density plots, show probability as smooth curves or gradients. These can be compact, but they may require statistical literacy.

Discrete-outcome representations show probability as countable possible outcomes. Prior work suggests people often reason better with frequencies, such as “10 out of 100,” than abstract probabilities, such as “10%.”

The challenge is that discrete-outcome displays can require a lot of space, which is difficult on mobile screens.

---

## 6. Survey of OneBusAway users

The authors surveyed **172 users** of OneBusAway, a real-time transit app, to understand how people use bus predictions and what uncertainty information they want.

### 6.1 Current user goals

Users commonly used the app to answer questions such as:

1. **When should I leave?**  
   Users want to know when to start walking to the bus stop.

2. **How long will I wait?**  
   Users want to know whether leaving now means a long or short wait.

3. **How long until the next bus if I miss this one?**  
   Users want to understand the cost of missing a bus.

4. **Will I arrive on time?**  
   Users want to assess risk for meetings, classes, or events.

5. **Do I have time to do something before the bus arrives?**  
   Users want to know whether they can get coffee, finish a task, or delay leaving.

### 6.2 Common negative experiences

Users reported problems such as:

- The bus coming earlier than predicted.
- The bus coming much later than predicted.
- The app showing a bus as “arriving” or “departed” incorrectly.
- A bus appearing to be “9 minutes away” for a long time.
- Users skipping backup buses because the app implied their preferred bus was coming soon.

These examples show that uncertainty is not merely an abstract statistical issue. It affects everyday planning, waiting, anxiety, and missed opportunities.

### 6.3 Unaddressed needs

The top unsupported needs were:

- **Status probability:** What is the chance the bus has already arrived or departed?
- **Prediction variance:** How likely is the predicted arrival time to change unexpectedly?
- **Schedule frequency:** How often do buses arrive at different times of day?

---

## 7. Design requirements

From the literature and survey, the authors identify several design requirements.

### 7.1 Preserve the point estimate

Users still need a quick predicted arrival time. The point estimate supports glanceability and fast decision-making.

### 7.2 Add a probabilistic estimate of arrival time

The interface should show the range of likely arrival times, not just one number. This helps users evaluate whether the bus might come early or late.

### 7.3 Show probabilistic arrival status

Users want to know whether a bus has likely already arrived, is arriving now, or is still on the way. The authors argue this can be shown through an annotated timeline.

### 7.4 Account for data freshness

OneBusAway users sometimes infer reliability from how recently data was updated. The authors suggest that an improved probabilistic model should account for data freshness directly, rather than forcing users to interpret update times themselves.

### 7.5 Support situation-dependent risk tolerance

Different situations require different levels of caution. The visualization should allow users to judge uncertainty according to their own risk tolerance.

---

## 8. Proposed interface designs

The authors explored multiple interface options through sketching, paper prototyping, digital mockups, and informal testing with **24 users**.

### 8.1 Bus-timeline layout

In the bus-timeline layout, each row represents one predicted bus. This is similar to traditional transit apps, where buses are listed in order of predicted arrival.

**Advantages:**

- Simple.
- Familiar.
- Easy to scan.
- Good for comparing individual upcoming buses.

**Limitations:**

- Less compact when showing many buses.
- Less effective for understanding route frequency.

### 8.2 Route-timeline layout

In the route-timeline layout, each row represents a route and can show multiple predicted buses on that route.

**Advantages:**

- Better for seeing how often a route arrives.
- Helps users assess the consequence of missing the next bus.
- Useful for schedule opportunity decisions.

**Limitations:**

- More visually complex.
- Requires two-dimensional navigation.

### Figure: Alternative layout designs

![Figure 1: Bus-timeline and route-timeline layouts](whenish_assets/page5_fig1_design_layouts.png)

*Figure source: page 5 of the article. The left design shows a bus-timeline layout where each row corresponds to one bus. The right design shows a route-timeline layout where each row corresponds to a route and can include multiple predicted arrivals.*

---

## 9. Important design decisions

### 9.1 Point estimates and probability estimates should coincide spatially

The authors found that placing the point estimate away from the uncertainty visualization made it too easy for users to ignore uncertainty. They rejected designs where point estimates appeared separately on the right side of the screen.

Their solution was to place the point estimate directly on or near the probability distribution, so users see the estimate and its uncertainty together.

### 9.2 Annotated timelines communicate arrival status

Instead of creating a separate display for “has the bus arrived?”, the authors use timeline labels such as:

- Departed.
- Now.
- On the way.

When the probability distribution overlaps these regions, users can infer the probability of each status.

### 9.3 “When to leave” is implied by arrival time

The authors considered directly showing when the user should leave, but this would require knowing the user’s walking time, destination, plans, and risk tolerance. Instead, they focus on showing arrival uncertainty, allowing users to decide when to leave.

### 9.4 Synchronized timelines support comparison

Each row uses the same time axis, so users can compare uncertainty across buses. If each row had its own axis, a highly uncertain prediction and a precise prediction could look misleadingly similar.

---

## 10. Encoding uncertainty on small screens

The authors compare several candidate uncertainty encodings.

### 10.1 Density plot

A density plot shows probability as a smooth curve. Higher parts of the curve represent more likely arrival times.

**Strengths:**

- Familiar to visualization researchers.
- Compact.
- Visually appealing.

**Weaknesses:**

- Requires users to interpret area or curve height probabilistically.
- May be less intuitive for non-experts.

### 10.2 Stripeplot

A stripeplot represents theoretical quantiles as vertical stripes. Denser stripes indicate more probable regions.

**Strengths:**

- Represents discrete outcomes.
- Compact.

**Weaknesses:**

- Harder to count.
- Performed poorly in the experiment.

### 10.3 Dotplots

Dotplots show possible outcomes as dots. The authors test two versions:

- **Dotplot-20:** 20 dots.
- **Dotplot-100:** 100 dots.

Dotplot-20 is easier to count quickly. Dotplot-100 gives a smoother impression of the distribution but becomes visually dense.

### 10.4 Quantile dotplots

Quantile dotplots are the authors’ main novel visualization.

Instead of randomly sampling possible outcomes from a distribution, the visualization places dots at evenly spaced quantiles. This produces a stable, consistent discrete representation of the distribution.

For example, if there are 20 dots, each dot represents 1/20, or 5%, of the distribution. A user can count dots before a certain time to estimate the chance that the bus arrives by then.

### Figure: Quantile dotplot explanation

![Figure 2: Quantile dotplot construction and interpretation](whenish_assets/page6_fig2_quantile_dotplots.png)

*Figure source: page 6 of the article. The diagram explains how quantile dotplots are generated from a probability distribution using the inverse cumulative distribution function. It also shows how users can count dots to estimate prediction intervals and risk thresholds.*

### Figure: Encoding comparison and selected visualizations

![Figures 4 and 5: Encoding comparison and evaluated visualization types](whenish_assets/page7_fig4_5_encodings.png)

*Figure source: page 7 of the article. The comparison matrix evaluates density plots, stripeplots, and dotplots according to properties such as countability, ability to estimate density, handling of tight distributions, and ease of assessing range or mode. The article evaluates density, dotplot-20, dotplot-100, and stripeplot-50.*

---

## 11. Experiment design

The authors conducted an online experiment to test how well users could interpret probabilities from the visualizations.

### 11.1 Participants

After removing incomplete responses, the final dataset included:

- **320 participants** in the bus-timeline layout condition.
- **221 participants** in the route-timeline layout condition.
- **90%** were existing OneBusAway users.
- Participants skewed male, with **71% male**.

### 11.2 Visualization conditions

Participants saw the following visualization types:

- Density plot.
- Stripeplot-50.
- Dotplot-20.
- Dotplot-100.

Each participant saw each visualization type once.

### 11.3 Scenarios

The experiment used four scenarios based on user goals from the survey. For example, a participant might be asked to decide whether there is enough time to get coffee before the bus arrives.

For each scenario, participants estimated probabilities such as:

- The chance the bus arrives by a certain time.
- The chance the bus arrives within a certain interval.

Participants answered using a 100-point slider.

### 11.4 Measures

The authors measured:

- **Accuracy/error:** how close estimated probabilities were to true probabilities.
- **Bias:** whether participants tended to overestimate or underestimate.
- **Variance/precision:** how consistent estimates were.
- **Confidence:** how confident participants felt about their estimates.
- **Ease of use.**
- **Visual appeal.**

---

## 12. Statistical modeling approach

The authors used **beta regression** because probability estimates are bounded between 0 and 1. A standard linear model would be less appropriate because variance behaves differently near 0 and 1 than near 0.5.

They modeled:

- The **mean** of responses to estimate bias.
- The **dispersion** of responses to estimate variance.

They used a Bayesian model with priors informed by previous work on hypothetical outcome plots.

The key modeling idea is that a visualization is better if users’ probability estimates have lower variance, assuming bias is not large. Lower variance means users interpret the visualization more consistently.

---

## 13. Main results

### 13.1 Bias was low across visualizations

Participants slightly overestimated probabilities on average, but the bias was similar across visualization types.

The authors suggest this may be related to the right-skewed nature of transit arrival distributions.

### 13.2 Dotplot-20 produced the most precise estimates

Dotplot-20 had the lowest variance in probability estimates.

The authors estimate that dotplot-20 was approximately **1.15 times more precise than density plots**.

In practical terms, this means probability estimates were about **1 to 3 percentage points more precise** than density plots.

### 13.3 Dotplot-100 performed similarly to density plots

Dotplot-100 did not provide the same improvement as dotplot-20. The authors suggest that 100 dots may be too many to count, causing users to treat the visualization more like a continuous density plot.

### 13.4 Stripeplot performed worst

Stripeplot had the highest variance and was rated as harder to use.

### 13.5 Dotplot-20 increased confidence

Participants were most confident when using dotplot-20. The mean confidence score for dotplot-20 was **81/100**, compared with **73/100** for dotplot-100.

For dotplot-20, confidence was negatively correlated with absolute estimation error, meaning participants who felt more confident tended to be more accurate.

### 13.6 Density plots were most visually appealing

Density plots had the highest visual appeal rating, with a mean of **66/100**. Dotplot-20 was less visually appealing, with a mean of **43/100**.

This creates a design tradeoff: dotplot-20 improved precision and confidence, but density plots looked better to users.

### Figure: Experimental results

![Figures 6 and 7: Probability estimation error and variance comparisons](whenish_assets/page9_fig6_7_results.png)

*Figure source: page 9 of the article. Figure 6 shows that dotplot-20 produced the narrowest error distribution and lowest estimated standard deviation. Figure 7 compares standard deviation ratios across visualization types, showing that density and stripeplot were less precise than dotplot-20.*

---

## 14. Discussion and interpretation

### 14.1 Small numbers of discrete outcomes work best

The authors conclude that discrete-outcome visualizations can improve uncertainty interpretation, but only when the number of outcomes remains manageable.

Dotplot-20 worked well because users could count or quickly recognize small groups of dots. This relates to **subitizing**, the ability to rapidly perceive small quantities without counting one by one.

Dotplot-100 and stripeplot-50 were denser and harder to count, so they behaved more like continuous encodings.

### 14.2 Users value uncertainty, but not all users want it

Many participants liked the idea of uncertainty information because it could help them make better decisions and reduce anxiety when predictions changed.

However, some users preferred simple point estimates. A small number actively disliked uncertainty because they felt it shifted responsibility onto them. In other words, if the app gives only a point prediction and the bus is missed, the user can blame the app; if the app gives uncertainty, the user may feel responsible for interpreting it.

### 14.3 Precision vs. glanceability

The article emphasizes a central design tension:

- More uncertainty information can improve decision-making.
- But too much detail can make the mobile interface harder to scan quickly.

This is especially important in transit contexts, where users may be walking, rushing, or checking the app briefly.

### 14.4 Visual appeal vs. estimation performance

Dotplot-20 performed better statistically but was less visually appealing. Density plots looked better but were less precise.

The authors do not claim that dotplot-20 should always replace density plots. Instead, they recommend considering the tradeoff between interpretability, precision, confidence, and visual appeal.

---

## 15. Design implications

### 15.1 Use uncertainty when decisions involve risk

Transit apps should show uncertainty when users need to decide whether to leave, wait, take another route, or do something before the bus arrives.

### 15.2 Avoid separating the point estimate from uncertainty

Point predictions should be visually integrated with uncertainty displays to reduce false precision.

### 15.3 Prefer low-density dotplots when countability matters

When users need to estimate probabilities or risk thresholds, low-density dotplots may be especially effective.

### 15.4 Consider density plots when visual appeal and fast scanning matter

Density plots may be preferable when aesthetics and compactness are priorities, especially if exact probability estimation is less important.

### 15.5 Explore interactivity

The authors suggest that interactive tools, such as a **risk slider**, could help users adjust the displayed estimate according to their risk tolerance. For example, a conservative user could move the estimate to a time that gives a high probability of catching the bus.

---

## 16. Limitations and future research

The article identifies several areas for further work:

### 16.1 Field deployment is needed

The experiment was controlled and online. A real-world field study would show whether users can interpret these visualizations while actually walking, waiting, or making transit decisions.

### 16.2 Learning over time may matter

Users may initially find dotplots unfamiliar or visually busy, but they could become more comfortable with them through repeated use.

### 16.3 Interactivity was not fully tested

The evaluated visualizations were mostly static. Interactive features could improve usability and reduce cognitive load.

### 16.4 User preferences vary

Some users want uncertainty information; others prefer simple predictions. Future systems may need customizable levels of detail.

---

## 17. Key terms

| Term | Meaning in this article |
|---|---|
| Point estimate | A single predicted value, such as “bus arrives in 5 minutes.” |
| Uncertainty visualization | A visual representation of the range or probability of possible outcomes. |
| Prediction interval | An interval in which a future outcome is expected to fall with a certain probability. |
| Density plot | A smooth curve showing where outcomes are more or less likely. |
| Dotplot | A plot showing outcomes as individual dots. |
| Quantile dotplot | A dotplot where dots are placed at evenly spaced quantiles of a probability distribution. |
| Stripeplot | A plot using vertical stripes to show quantiles or possible outcomes. |
| False precision | The misleading impression that a prediction is more exact than it really is. |
| Glanceability | How quickly and easily a user can understand information at a glance. |
| Subitizing | Quickly recognizing small numbers of items without counting individually. |
| Beta regression | A regression method appropriate for modeling values bounded between 0 and 1, such as probabilities. |

---

## 18. Practical takeaway

The article shows that uncertainty can be communicated in everyday mobile interfaces, but the design must be carefully matched to the user’s context. For bus arrival predictions, users need both fast scanning and enough uncertainty information to make risk-aware decisions.

The strongest design lesson is that **small, countable discrete-outcome visualizations can help non-expert users estimate uncertainty more consistently**. In this study, **dotplot-20** gave users more precise and confident probability estimates than density plots, while density plots remained more visually appealing.

A good mobile prediction interface should therefore avoid presenting predictions as exact facts. Instead, it should show the “when-ish” nature of the prediction in a way that supports quick, situated decision-making.

---

## 19. One-sentence summary

Kay, Kola, Hullman, and Munson argue that mobile predictive systems should communicate uncertainty, and they show that low-density quantile dotplots can help everyday users make more precise and confident probability judgments about uncertain bus arrival times.
