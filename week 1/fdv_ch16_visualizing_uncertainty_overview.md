# Chapter 16 Overview: “Visualizing Uncertainty”  
## *Fundamentals of Data Visualization* — Claus O. Wilke

**Chapter focus:** Chapter 16 explains why uncertainty is difficult to visualize, why common tools such as error bars and confidence bands are often misunderstood, and how alternative designs such as frequency framing, quantile dotplots, graded intervals, posterior distributions, and hypothetical outcome plots can make uncertainty more perceptible.

**Source:** Claus O. Wilke, *Fundamentals of Data Visualization*, Chapter 16, “Visualizing uncertainty.” Online chapter: <https://clauswilke.com/dataviz/visualizing-uncertainty.html>

> **Note on figures:** The figures below are recreated explanatory diagrams based on the chapter’s concepts. They are included to support studying and note-taking, not as exact reproductions of the original book figures.

---

## 1. Why uncertainty is hard to visualize

Wilke opens the chapter by emphasizing a central problem: when a viewer sees a plotted point, line, or bar, the viewer tends to read it as exact. In real analysis, however, most values are estimates based on incomplete data, measurement error, sampling variability, model assumptions, or future unpredictability.

The chapter contrasts two broad visualization goals:

| Goal | Typical audience | Common methods | Strength | Limitation |
|---|---|---|---|---|
| Precise, compact statistical communication | Expert or scientific audience | Error bars, confidence intervals, confidence bands | Space efficient; can show many estimates at once | Requires statistical literacy; easy to misinterpret |
| Intuitive uncertainty communication | Lay or mixed audience | Frequency framing, quantile dotplots, animations/HOPs | Builds a concrete sense of uncertainty | May be less mathematically exact or less data-dense |

The chapter’s practical message is that uncertainty visualization is not just about mathematical correctness. A visualization that is technically accurate but perceptually misleading is not useful.

---

## 2. Section 16.1 — Framing probabilities as frequencies

### 2.1 Defining uncertainty through probability

Uncertainty is easiest to understand with future events, such as a coin flip, but it also applies to past events when we do not know exactly what happened. Mathematically, uncertainty is handled through probability.

Wilke avoids a formal mathematical definition of probability and instead emphasizes a practical interpretation: for many applied situations, probabilities can be understood as **relative frequencies**.

Example:

- A 10% probability means that if we repeated a similar trial many times, we would expect success in about 1 out of 10 trials.
- This framing is easier for many people to understand than an abstract probability value shown as a single number.

### 2.2 Why a single probability is difficult to visualize

A single probability, such as “1% chance,” “10% chance,” or “40% chance,” can technically be shown as a bar, dot, or number. However, these displays often fail to convey how the chance feels in practice.

Wilke recommends **frequency framing**, where a probability is represented as a set of possible outcomes.

![!\[Recreated probability-frequency framing\](fdv_ch16_overview_assets/probability_frequency_framing.png)](<Ch 16 images/probability_frequency_framing.png>)

### 2.3 Discrete outcome visualizations

A **discrete outcome visualization** represents possible outcomes as individual objects. For example, a 10% chance can be represented as 10 success squares and 90 failure squares in a 100-square grid.

Key advantages:

- The viewer can see both success and failure outcomes.
- Random placement of successes creates a visual impression of unpredictability.
- Discrete objects are easier to count and compare than abstract areas or percentages.

Key caution:

- The total number of objects should not be too large. If there are too many objects, viewers stop reading the display as discrete outcomes and start seeing it as a continuous texture.

---

## 3. Election prediction example: distributions and dotplots

### 3.1 Probability distributions for numeric outcomes

Many uncertain outcomes are not simply success/failure. In an election forecast, for example, we may care not only who wins but also by how much.

Wilke uses a hypothetical election in which the blue party is predicted to lead the yellow party by about one percentage point, with a margin of error. Instead of treating the forecast as “blue will win,” the chapter shows that there is a distribution of possible outcomes.

![!\[Recreated election prediction distribution\](fdv_ch16_overview_assets/election_prediction_distribution.png)](<Ch 16 images/election_prediction_distribution.png>)

In this example:

- The peak of the curve is the **best estimate**.
- The spread of the curve reflects uncertainty.
- The area on one side of zero corresponds to the probability that one party wins.
- The chapter’s original example states that the blue party has about an 87% chance of winning and the yellow party about a 12.9% chance.

### 3.2 Why shaded probability distributions can still be hard to read

A shaded distribution is mathematically precise, but people are not especially good at estimating probability from shaded areas. A viewer may understand that the blue region is larger than the yellow region, but not accurately judge the relative probability.

This is why the chapter introduces **quantile dotplots**.

### 3.3 Quantile dotplots

A **quantile dotplot** divides the probability distribution into equal-probability units and displays those units as dots.

![!\[Recreated quantile dotplot\](fdv_ch16_overview_assets/quantile_dotplot_election.png)](<Ch 16 images/quantile_dotplot_election.png>)

In a 10-dot version:

- Each dot represents about 10% probability.
- One yellow dot roughly communicates a 10% chance that yellow wins.
- The display is less precise than the full distribution, but it can be easier to interpret.

In a 50-dot version:

- Each dot represents about 2% probability.
- The result is more numerically accurate.
- However, it may be harder to read because there are too many dots.

### 3.4 Precision vs. perception

A major principle from this section is that visualization involves a tradeoff between mathematical precision and perceptual effectiveness.

A technically exact visualization can still fail if readers misread it. For a general audience, a slightly simplified but perceptually clear display may communicate uncertainty better.

---

## 4. Section 16.2 — Visualizing uncertainty of point estimates

### 4.1 Population, sample, parameters, and estimates

Wilke explains point-estimate uncertainty by reviewing statistical sampling.

| Term | Meaning |
|---|---|
| Population | The full set of values or cases we want to understand |
| Sample | The subset of the population we actually observe |
| Parameter | A true population quantity, such as the true mean or true standard deviation |
| Estimate | A value calculated from the sample to approximate a parameter |
| Point estimate | A single estimated value, such as a sample mean |
| Sampling distribution | The distribution of estimates that would arise from repeated sampling |
| Standard error | The spread of the sampling distribution; a measure of uncertainty in the estimate |

![!\[Recreated sampling concepts schematic\](fdv_ch16_overview_assets/sampling_concepts_schematic.png)](<Ch 16 images/sampling_concepts_schematic.png>)

### 4.2 Standard deviation vs. standard error

Wilke stresses that **standard deviation** and **standard error** must not be confused.

| Concept | What it describes | Interpretation |
|---|---|---|
| Standard deviation | Spread among individual observations | How variable the data values are |
| Standard error | Spread of an estimate across repeated samples | How uncertain the estimate is |

A useful approximation:

```text
standard error ≈ sample standard deviation / sqrt(sample size)
```

This means larger samples generally produce smaller standard errors, even when the underlying data variation stays the same.

### 4.3 Error bars: useful but ambiguous

Frequentist uncertainty is often displayed with **error bars**. Error bars are compact and useful, but the chapter highlights a major problem: the same visual form can mean many different things.

For example, error bars around a mean might represent:

- plus/minus one standard deviation,
- plus/minus one standard error,
- an 80% confidence interval,
- a 95% confidence interval,
- a 99% confidence interval.

![Recreated error-bar comparison](fdv_ch16_overview_assets/error_bar_meaning_comparison.png)

These intervals are related, but they communicate different claims. Therefore, Wilke’s rule is direct:

> Whenever you visualize uncertainty with error bars, state exactly what the bars represent.

### 4.4 Confidence intervals and sample size

Confidence intervals are based on the standard error. A rough approximation for a 95% confidence interval is:

```text
estimate ± 2 × standard error
```

Because standard error decreases as sample size increases, a larger sample can produce a narrower confidence interval even if the data’s standard deviation is similar.

This is the conceptual reason Wilke’s chocolate-rating example shows wider intervals for countries with fewer rated chocolate bars.

### 4.5 Graded error bars

A **graded error bar** shows multiple confidence levels at once, often by varying line width or intensity. For example, a plot might show 80%, 95%, and 99% intervals together.

Advantages:

- Communicates that uncertainty is not a hard boundary.
- Reduces the impression that values inside the bar are possible and values outside are impossible.
- Helps viewers see a range of plausible values.

Disadvantages:

- Adds visual complexity.
- Can become noisy in dense figures.
- May not be necessary for expert audiences or simple plots.

### 4.6 Deterministic construal error

A key concept in this chapter is **deterministic construal error**. This occurs when viewers interpret an uncertainty display as if it were a fixed, deterministic feature of the data.

Examples:

- Interpreting error bars as the minimum and maximum values.
- Thinking that the true value cannot fall outside an error bar.
- Treating a confidence band as a literal boundary that the trend cannot cross.

Wilke argues that uncertainty graphics should be designed to reduce this error whenever possible.

### 4.7 Comparing groups: do not rely on error-bar overlap

Wilke warns against judging statistical significance by visually checking whether two groups’ error bars overlap. This rule of thumb is unreliable because each group’s estimate has uncertainty, and the question of difference requires uncertainty around the **difference**, not just around each individual mean.

Correct approach:

1. Compute the difference between estimates.
2. Compute the confidence interval for that difference.
3. Check whether the interval includes or excludes zero.

In the chocolate-rating example, the chapter shows country ratings relative to U.S. chocolate bars and notes that only Canada is significantly higher at the 95% level after adjusting for multiple comparisons.

### 4.8 Variants of error bars and interval displays

The chapter discusses several design variants:

| Design | Strength | Weakness |
|---|---|---|
| Capped error bars | Clearly marks interval endpoints | Adds visual noise |
| Uncapped error bars | Cleaner; emphasizes interval as a range | Endpoints may be less visually precise |
| Graded error bars | Shows multiple uncertainty levels | More visually complex |
| Confidence strips | Suggest gradual probability changes | Hard to read exact levels |
| Confidence distributions | Shows full uncertainty shape | Requires viewers to interpret area under a curve |
| Quantile dotplots | Converts distribution into countable units | Lower resolution if few dots are used |

### 4.9 Bar plots with error bars

Wilke notes that bar plots with error bars are common in scientific publications, but they often have two limitations:

- They may not show the variation among individual observations.
- They may not communicate uncertainty around the means particularly well.

When possible, showing raw data points, distributions, or more informative summaries may be better than relying only on bars plus error bars.

### 4.10 Error bars in scatter plots

Error bars can be drawn in both the x and y directions. This is useful when both variables have uncertainty. The chapter’s example uses median income and median age for Pennsylvania counties with 90% confidence intervals.

---

## 5. Frequentist confidence intervals vs. Bayesian credible intervals

### 5.1 Frequentist framing

Frequentists assess uncertainty through confidence intervals and hypothesis-testing logic. A confidence interval can be understood through repeated sampling:

- For one sample, the interval either contains the true parameter or it does not.
- Across many repeated samples, a 95% confidence procedure captures the true parameter about 95% of the time.

![Recreated repeated-sampling confidence interval schematic](fdv_ch16_overview_assets/repeated_sampling_ci.png)

### 5.2 Bayesian framing

Bayesians use prior knowledge plus observed data to calculate a **posterior distribution**. A Bayesian credible interval gives a probability statement about where the true parameter is expected to lie.

Example:

- A 95% credible interval means the parameter has a 95% probability of lying in that interval, according to the posterior distribution.

### 5.3 Practical comparison

Wilke emphasizes that Bayesian and frequentist uncertainty visualizations often look similar in practice. However, their interpretation differs.

| Interval type | Main question answered | Typical visualization |
|---|---|---|
| Confidence interval | What values would not be rejected under repeated-sampling logic? | Error bars, confidence bands |
| Credible interval | Where do we expect the true parameter to lie, given the data and prior? | Posterior distributions, credible intervals |

### 5.4 Bayesian posterior distributions

Because Bayesian analysis produces an entire posterior distribution, the chapter recommends visualizing the distribution when possible. Useful choices include:

- histograms,
- density plots,
- boxplots,
- violin plots,
- ridgeline plots,
- half-eye plots,
- eye plots,
- quantile dotplots.

Wilke’s example uses ridgeline plots of posterior distributions for chocolate-rating means, with shaded regions marking 80%, 95%, and 99% credible intervals.

---

## 6. Section 16.3 — Visualizing uncertainty of curve fits

### 6.1 Confidence bands for trend lines

When a line or curve is fitted to data, the fit itself has uncertainty. A common way to display this uncertainty is a **confidence band** around the fitted trend.

![Recreated curve-fit uncertainty](fdv_ch16_overview_assets/curve_fit_uncertainty.png)

The band represents a range of fitted lines or curves compatible with the data at a given confidence level.

### 6.2 Why straight-line confidence bands are curved

A confidence band around a straight line often looks curved. Wilke explains that this happens because the fitted line can vary in both:

- intercept, meaning the line can shift up or down;
- slope, meaning the line can rotate.

The combination of these possibilities creates a band that is often narrow near the center of the data and wider toward the edges.

### 6.3 Alternative fitted lines

Another way to visualize trend uncertainty is to draw multiple alternative fits sampled from the posterior distribution. This makes the meaning of the confidence band more concrete because the viewer can see many plausible trend lines rather than one deterministic line plus a shaded region.

### 6.4 Graded confidence bands

A **graded confidence band** shows multiple confidence levels at the same time, such as darker shading for the most likely region and lighter shading for wider, less likely regions.

Advantages:

- Makes uncertainty feel less like a hard boundary.
- Shows that some alternative trends are more plausible than others.
- Encourages readers to consider multiple compatible trends.

### 6.5 Nonlinear curve fits

Wilke warns that confidence bands for nonlinear smooths can be difficult to interpret. Viewers may think uncertainty means the curve simply moves up or down. In reality, uncertainty in nonlinear fits may also involve changes in shape or “wiggliness.”

Main idea:

- For nonlinear fits, plausible alternatives can be substantially different in shape from the best-fit curve.
- Showing alternative curves can reveal uncertainty that a simple band may hide.

---

## 7. Section 16.4 — Hypothetical outcome plots

### 7.1 What is a hypothetical outcome plot?

A **hypothetical outcome plot** (HOP) is an animated uncertainty visualization that cycles through possible outcomes. Rather than showing all possible outcomes at once, it shows one plausible outcome at a time.

This approach can reduce deterministic construal error because viewers are less likely to treat a single static boundary or band as a fixed truth.

![Recreated HOP schematic](fdv_ch16_overview_assets/hop_schematic.png)

### 7.2 Chocolate-rating example

Wilke’s chocolate example reframes the question from “Which country has the higher mean rating?” to a more practical question:

> If I randomly choose one Canadian chocolate bar and one U.S. chocolate bar, which is more likely to taste better?

The chapter explains that repeated random draws show Canadian bars rank higher in about 53% of cases, while U.S. bars rank higher or tie in about 47% of cases. A HOP can animate these draws so the viewer sees the variability directly.

### 7.3 Curve-fit example

Wilke also applies HOPs to trend lines. Instead of showing many possible curves at once, a HOP cycles through plausible fitted curves one at a time. This helps viewers perceive the range of possible trends without reducing everything to a static shaded region.

### 7.4 Design cautions for HOPs

HOPs are powerful but require care.

| Issue | Recommendation |
|---|---|
| Print limitations | HOPs work best online, in slides, GIFs, or videos |
| Smooth transitions | Avoid slow morphing if it makes probabilities harder to judge |
| Outcome representativeness | Ensure displayed outcomes reflect the true distribution |
| Sampling bias | Use enough outcomes or verify that the chosen frames are representative |

Wilke notes that smooth animation between outcomes may sometimes make probability judgment harder. A faster switch, fade, or discrete transition may preserve the sense that each frame is a separate possible outcome.

---

## 8. Key concepts and definitions

| Concept | Definition | Why it matters for visualization |
|---|---|---|
| Uncertainty | Lack of certainty about a value, outcome, estimate, or model | Most data visualizations imply more precision than the data support |
| Probability | A mathematical way to reason about uncertainty | Can be abstract; often easier to explain as frequency |
| Frequency framing | Showing probability as expected counts out of repeated trials | Makes probability concrete and intuitive |
| Discrete outcome visualization | A visual display where each object represents one possible outcome | Helps viewers count and compare probabilities |
| Quantile dotplot | A dotplot where each dot represents an equal amount of probability | Combines distribution shape with countable outcomes |
| Point estimate | A single numerical estimate of a parameter | Should often be accompanied by uncertainty |
| Standard deviation | Variation among individual observations | Describes data spread, not precision of the estimate |
| Standard error | Variation among estimates across repeated samples | Describes uncertainty in a parameter estimate |
| Confidence interval | Frequentist interval based on repeated-sampling logic | Common but often misinterpreted |
| Credible interval | Bayesian interval from a posterior distribution | Easier intuitive interpretation but depends on Bayesian modeling |
| Deterministic construal error | Mistaking uncertainty displays for fixed deterministic features | A major design problem in uncertainty visualization |
| Confidence band | Interval around a fitted line or curve | Shows uncertainty in the estimated trend |
| Hypothetical outcome plot | Animation cycling through plausible outcomes | Makes uncertainty experiential rather than static |

---

## 9. Practical checklist for visualizing uncertainty

Use this checklist when deciding how to show uncertainty:

1. **Identify what is uncertain.** Is it a probability, a mean, a difference between means, a trend line, a model prediction, or a future outcome?
2. **Choose the right uncertainty quantity.** Do not mix up standard deviation, standard error, confidence interval, credible interval, or prediction interval.
3. **Label error bars explicitly.** State whether they show standard deviation, standard error, or a specific confidence/credible interval.
4. **Avoid relying on overlap rules.** Do not infer group differences by eyeballing whether error bars overlap. Plot intervals for differences when comparing estimates.
5. **Match the method to the audience.** Expert audiences can handle compact intervals; lay audiences may benefit from frequency framing or HOPs.
6. **Reduce deterministic construal error.** Avoid designs that make uncertainty look like a hard boundary.
7. **Use graded displays when helpful.** Multiple confidence/credible levels can show that uncertainty fades rather than stops suddenly.
8. **Show raw data when possible.** A bar with an error bar can hide distributional structure.
9. **Use dotplots or discrete outcomes for probabilities.** Countable objects often communicate probability more effectively than shaded areas.
10. **For animations, verify representativeness.** The outcomes shown in a HOP should accurately reflect the distribution of possible outcomes.

---

## 10. Common mistakes to avoid

| Mistake | Why it is a problem | Better approach |
|---|---|---|
| Showing a point estimate with no uncertainty | Implies false precision | Add uncertainty intervals, distribution, or scenario-based display |
| Using error bars without explanation | Readers may not know what they represent | Label the interval type and confidence level |
| Confusing standard deviation and standard error | Misstates whether you are showing data spread or estimate precision | Use SD for variation; SE/CI for estimate uncertainty |
| Using bar plots with error bars by default | Hides raw data and distribution shape | Use dotplots, boxplots, violins, or raw data overlays |
| Judging significance by overlapping error bars | Visually unreliable | Plot the confidence interval of the difference |
| Treating confidence bands as fixed boundaries | Creates deterministic construal error | Consider graded bands, sampled alternative fits, or HOPs |
| Using too many dots in a quantile dotplot | Viewers stop seeing individual outcomes | Use a small to moderate number of dots |
| Animating HOPs with unrepresentative frames | Can mislead viewers about probability | Check that displayed outcomes match the underlying distribution |

---

## 11. Key takeaways

- Uncertainty is present in nearly all data analysis, but standard visual forms often make estimates look overly precise.
- Frequency framing makes probability more concrete by translating abstract percentages into countable outcomes.
- Quantile dotplots are useful because they combine probability distributions with discrete, countable units.
- Error bars are compact and useful, especially for expert audiences, but they must be labeled clearly.
- Standard deviation describes variation in observations; standard error describes uncertainty in an estimate.
- Confidence intervals and Bayesian credible intervals can look similar but have different interpretations.
- When comparing groups, plot uncertainty around the difference rather than relying on error-bar overlap.
- Confidence bands show uncertainty in fitted trends, but nonlinear fits can involve uncertainty in both position and shape.
- Hypothetical outcome plots can communicate uncertainty intuitively by cycling through plausible outcomes.
- The best uncertainty visualization depends on the audience, the task, and the risk of misinterpretation.

---

## 12. Study questions

1. Why does Wilke argue that a single probability value is hard to visualize effectively?
2. What is frequency framing, and why can it be more intuitive than a probability curve?
3. How does a quantile dotplot differ from a density plot?
4. Why should a quantile dotplot use a small to moderate number of dots?
5. What is the difference between standard deviation and standard error?
6. Why is it misleading to judge statistical significance by whether error bars overlap?
7. What is deterministic construal error?
8. How do confidence intervals and credible intervals differ conceptually?
9. Why can a confidence band around a straight line be curved?
10. What makes hypothetical outcome plots useful for communicating uncertainty?

---

## 13. One-page summary

Chapter 16 teaches that uncertainty visualization is a communication problem as much as a statistical problem. Viewers often interpret plotted values as exact, so visualizations must actively communicate uncertainty rather than merely attach technical intervals. For probabilities, frequency framing and quantile dotplots can make uncertainty concrete by showing countable outcomes. For point estimates, error bars are useful but ambiguous; they must be labeled, and viewers must understand whether they represent standard deviation, standard error, confidence intervals, or credible intervals. For group comparisons, uncertainty should be shown around differences rather than inferred from overlapping intervals. For fitted curves, confidence bands and sampled alternative fits reveal that the estimated trend is only one of many plausible patterns. Finally, hypothetical outcome plots use animation to show uncertainty as a sequence of possible realities, helping viewers avoid treating static uncertainty displays as deterministic truths.
