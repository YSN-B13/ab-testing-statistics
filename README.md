# A/B Testing Analysis

## Overview

This guide walks through a complete A/B testing analysis to determine whether an experimental change (new design, feature, or algorithm) produces a statistically significant improvement over a control group.

## Goal

Answer the core question: **Does the experiment meaningfully improve conversion or click-through rates compared to the control?**

## Key Concepts

**Statistical Parameters**
- α (alpha): Significance level; probability of rejecting H₀ when it's true (typically 0.05)
- β (beta): Probability of failing to detect a real effect (Type II error)
- Power (1 - β): Ability to detect a true effect
- δ (delta): Minimum detectable effect size you care about

---

## Testing Framework

### Step 1: Define Hypotheses

**Null hypothesis (H₀):** Control and experimental conversion rates are equal
**Alternative hypothesis (H₁):** The conversion rates differ

In mathematical form:
- H₀: P_control = P_experiment
- H₁: P_control ≠ P_experiment

### Step 2: Calculate Conversion Rates

For each group, calculate the observed conversion rate:

```
p̂_control = (clicks in control) / (total impressions in control)
p̂_experiment = (clicks in experiment) / (total impressions in experiment)
```

### Step 3: Compute Standard Error

**For the hypothesis test** (assuming equal proportions under H₀), use the pooled standard error:

```
p̂_pooled = (total clicks) / (total impressions)

SE_pooled = √[p̂_pooled(1 - p̂_pooled) × (1/n_control + 1/n_experiment)]
```

**For confidence intervals**, use the unpooled standard error:

```
SE_unpooled = √[(p̂_control(1 - p̂_control)/n_control) + (p̂_experiment(1 - p̂_experiment)/n_experiment)]
```

### Step 4: Calculate Z-Statistic and P-value

```
z = (p̂_experiment - p̂_control) / SE_pooled

p-value = 2 × P(Z > |z|)
```

The p-value represents the probability of observing this difference (or larger) if the null hypothesis is true.

### Step 5: Build Confidence Interval

Calculate a 95% confidence interval for the true difference in conversion rates using the unpooled standard error:

```
(p̂_experiment - p̂_control) ± 1.96 × SE_unpooled
```

If this interval doesn't contain zero, the difference is statistically significant at the 0.05 level.

### Step 6: Interpret Results

**If p-value < α (typically 0.05):**
- Reject the null hypothesis
- The difference is statistically significant
- Strong evidence that the experiment differs from control

**If p-value ≥ α:**
- Fail to reject the null hypothesis
- Insufficient evidence of a significant difference
- Cannot conclusively say the experiment outperforms control

**Check the confidence interval:** If it excludes zero, this confirms statistical significance.

---

## Key Takeaways

- **Pooled SE** is used only for the hypothesis test under H₀
- **Unpooled SE** is used for confidence intervals
- Always verify findings using both the p-value and confidence interval
- For very small samples or extreme proportions, consider exact tests (Fisher's exact test) or continuity corrections
- Statistical significance doesn't guarantee practical significance—consider the effect size in business context

---

## Outputs

The analysis produces:
- Side-by-side comparison of control vs. experimental conversion rates
- Z-statistic and p-value
- 95% confidence interval for the difference
- Clear recommendation on whether to implement the experimental change
