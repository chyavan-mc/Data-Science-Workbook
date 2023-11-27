# A/B Testing

## Basics
An A/B test, also known as a split test, is a controlled experiment in which two or more variants are compared to determine which one performs better.

Example environments where A/B Testing is employed - 
* User interface (UI)
* Relevance algorithms (search, ads, personalization, recommendations, etc.)
* Latency/performance
* Content management systems
* Customer support systems

Experiments can be run on multiple channels -
* Websites
* Desktop applications
* Mobile applications
* E-mail
* Social Media
* ATM
* Customer Relationship Management (CRM) Systems


### Overall Evaluation Criteria (OEC)
OEC is a quantitative measure of the experiment‘s objective. The OEC must be measurable in the short term (the duration of an experiment) yet believed to causally drive long-term strategic objectives. An OEC can be a combination of metrics of usage, relevance, ad revenue, etc. OECs are also called the *Response variable*, *Dependent variable*, *Outcome*, *Evaluation*, and *Fitness Function*. An example of an OEC is *Active days per user*, where the outcome is the users' frequency measure.

An experiment may have multiple objectives and maintain a balanced scorecard for the metrics, but it is often desired to select a single metric as a weighted combination of such objectives.


### Parameter
A controllable experimental variable that is thought to influence the OEC or other metrics of interest. In simple A/B tests, there is commonly a single parameter with two values. It is common to use univariable designs with multiple values (such as A/B/C/D). 

Multivariable tests, also called *Multivariate Tests* (MVTs), evaluate multiple parameters (variables) together, such as font color and font size, allowing experimenters to discover a global optimum when parameters **interact**


### Variant
A variant is a user experience being tested, typically by assigning values to parameters. In a simple A/B test, A and B are the two variants, usually called *Control* and *Treatment*.


### Randomization Unit
Randomization unit is a pseudo-randomization (e.g., hashing) process that is applied to units (e.g., users or pages) to map them to variants. Randomization units must be *persistent* and *independent*

* Persistent - A user should consistently see the same experience. Some experimental designs choose to randomize by pages, sessions, or user-day (a 24-hour window where the experience is consistent)
* Independent - The assignment of a user to a variant should be independent of the assignment of a different user to its variant


Controlled experiments are -
* The best scientific way to establish causality with high probability.
* Able to detect small changes that are harder to detect with other techniques. Eg: changes over time (sensitivity).
* Able to detect unexpected changes. Eg: Cannibalizing clicks from other features.



## Necessary conditions for a successful A/B Test
* There are experimental units (e.g., users) that can be assigned to different variants with no interference
* There are enough experimental units (e.g., users)
* Key metrics, ideally an OEC, are agreed upon and can be practically evaluated
* Changes are easy to make



## Considerations for an A/B Test
1. **OEC** - Points to remember w.r.t to the OEC are
    * Metrics should not be game-able
    * **Guardrail metric** -  These are business-critical metrics to be monitored for negative change while conducting A/B tests.
        - Software crashes as a guardrail metric for new software feature development
        - Passenger safety as a guardrail metric for food and lighting improvements (Sinking cruise ship example)
2. **Optimization problem** - Consider A/B Testing as a gradient ascent (hill-climbing) optimization problem.
    * Sometimes based on the data, we may need to consider a pivot:
        1. Jumping to a different location in the space, which may be on a bigger hill
        2. Changing the strategy and the OEC (and hence the shape of the optimization terrain).
3. **Tactic vs Strategy** - An A/B Test is based on a tactic which is a subset/particular implementation of the strategy. Therefore, even with great strategy, a particular tactic may fail to produce results and may require ideating new tactics.
4. **Randomness in usage** - Even if variants are assigned with equal probability, *due to chance* the users interacting may differ, so per-user metrics are a better OEC
5. **Targeted Population** - Targeting a specific population means that you only want to run the experiment for users with a particular characteristic. Common targeting attributes include geographic region, platform, language, and device type
6. **Duration of the experiment** - A vital question is how long to run the experiment. Here are other factors to consider -
    * More users - Over time, the experiment collects more new users. This may result in -
        * Increased statistical power
    * Day-of-week effect - This addresses the weekly seasonality in the feature usage
    * Seasonality - This addresses long-term seasonality and effects of exceptional seasonal effects (Christmas, Thanksgiving, geography-specific holidays, etc.)
    * *Primacy* and *Novelty* effects - Some experiments tend to have a larger or smaller initial effect that takes time to stabilize.

### Threats to Internal Validity

Internal validity refers to the correctness of the experimental results without attempting to generalize to other populations or time periods.

1. Violations of SUTVA <br>
Stable Unit Treatment Value Assumption (SUTVA) states that experiment units (e.g., users) do not interfere with one another. The assumption could be easily violated in many cases

2. Survivorship Bias <br>
Analyzing users who have been active for some time (e.g., two months) introduces survivorship bias.

3. Intention-to-Treat <br>
The Treatment effect we measure should be based on the offer, or intention to treat, not whether it was actually applied.

4. Sample Ratio Mismatch (SRM) <br>
SRM refers to a situation where the distribution of users between the control group (A) and the experimental group (B) is not as originally intended or specified.


### Threats to External Validity
External validity refers to the extent to which the results of a controlled experiment can be generalized along axes

1. Primacy Effects <br>
Complete redesigns that adversely affect users primed to the old design. This is a major reason for continuous redesign being superior to a one-shot complete redesign. However small the change, any change may result in primacy effects in the treatment group that may overstate or understate the actual effect in the short term. *Negatively affects the changes as users take time to adopt the new feature*.

2. Novelty Effects <br>
The term is usually used to describe a positive effect that is entirely due to the fact that there is a change, a new design feature, module, or process being introduced, regardless of what the change is. *Positively affects the changes as users curiously try the new feature*

### Simpson’s Paradox
If an experiment goes through ramp-up that is, two or more periods with different percentages assigned to the variants, combining the results can result in directionally incorrect estimates of the Treatment effects. That is, Treatment may be better than Control in the first phase and the second phase, but worse overall when the two periods are combined. Examples from controlled experiments where Simpson’s paradox may arise

1. Users are sampled
2. Users are segmented
3. Sequential Tests with different populations


## Decision Making
A/B Testing falls under the larger umbrella of executing successful strategies. This includes the data-driven understanding of the changes being done to implement the strategy, and making decisions that optimally influence the business value.

### Statistical significance vs Practical significance

**Statistical Significance** - Statistical hypothesis testing is used to determine whether the result of a data set is statistically significant. This is to identify if the changes being made objectively have an effect.

**Practical Significance** - The size of that change that would matter in practice. This is to identify if the changes being made subjectively have an impact on the business value.
    Example - A feature that provides a 1% improvement in an established process of a large-scale company like Google may result in Hundreds/Millions of Dollars of revenue increase. For a start-up, they may have a practical significance only if the features they are providing show at least a 10% improvement.


### From Results to Decisions
A decision needs to take into consideration both the conclusion from the measurement and the broader context, such as
* Are there any tradeoffs between different metrics?
* What is the cost (launching and maintaining) of launching this change?
* What is the downside of making wrong decisions?

Illustrating how to use these thresholds to guide our decisions


![Decision Making](./assets/06_AB_Testing/Significance.png)

1. The result is neither statistically significant nor practically significant. *Iterate or abondon the idea*.

2. The result is statistically and practically significant. *Again, an easy decision: launch!*

3. The result is statistically significant but not practically significant. *This change may not be **worth** launching*.

4. Similar to the first example, the confidence intervals do overlap the practical significance region. *So, it's better to run a follow-up test with more units, providing greater statistical power*.

5. The result is likely practically significant but not statistically significant. *The best recommendation would be to repeat this test but with greater power to gain more precision in the result*.

6. The result is statistically significant, and likely practically significant. Like 5, it is possible that the change is not practically significant. *Thus here, like the prior example, we suggest repeating the test with more power. From a launch/no-launch decision, however, choosing to launch is a reasonable decision.*


## Statistical Analysis of an A/B Test

### For a discrete OEC

$N_c$ = Number of control group units <br>
$N_t$ = Number of treatment group units <br>
$S_c$ = Number of successes in the control group <br>
$S_t$ = Number of successes in the treatment group <br>

$P_c$ = $\frac{S_c}{N_c}$ <br>
$P_t$ = $\frac{S_t}{N_t}$ <br>
$\Delta$ = $P_t - P_c$ <br>
$SE_c^2$ = $\frac{P_c(1-P_c)}{N_c}$ <br>
$SE_t^2$ = $\frac{P_t(1-P_t)}{N_t}$ <br>

$Z$ = $\frac{\Delta}{\left[SE_t^2 + SE_c^2\right]^{1/2}}$

[Online Z-Score to P-value Calculator](https://www.socscistatistics.com/pvalues/normaldistribution.aspx)


| $\alpha$ |One-tailed (Left) | One-tailed (Right) | Two-tailed |
| --- | --- | --- | --- |
| $\alpha = 0.05$ | $Z = -1.64$ | $Z = 1.64$ | $Z = \pm 1.96$ |
| $\alpha = 0.01$ | $Z = -2.33$ | $Z = 2.33$ | $Z = \pm 2.57$ |
| $\alpha = 0.001$ | $Z = -3.08$ | $Z = 3.08$ | $Z = \pm 3.32$ |


### For a continuous OEC

$N_c$ = Number of control group units <br>
$N_t$ = Number of treatment group units <br>
$\bar{X}_c$ = Sample Mean of the control group <br>
$\bar{X}_t$ = Sample Mean of the treatment group <br>
$\sigma_c^2$ = Sample variance of the control group <br>
$\sigma_t^2$ = Sample variance of the treatment group <br>

$\Delta$ = $\bar{X}_t - \bar{X}_c$ <br>
$SE_c^2$ = $\frac{\sigma_c^2}{N_c}$ <br>
$SE_t^2$ = $\frac{\sigma_t^2}{N_t}$ <br>

$t$ = $\frac{\Delta}{\left[ SE_t^2 + SE_c^2 \right]^{1/2}}$ <br>
DF = $(N_c - 1)$ + $(N_t - 1)$


[Online t-value to P-value Calculator](https://www.socscistatistics.com/pvalues/tdistribution.aspx)

