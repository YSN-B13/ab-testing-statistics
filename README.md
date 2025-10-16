# 🧪 A/B Testing Analysis

## 📘 Project Overview
This project presents a **comprehensive A/B testing analysis** designed to evaluate whether a modification in an experimental group (e.g., new design, feature, or algorithm) produces a **statistically significant effect** compared to a control group.

The notebook guides you through each step of a rigorous statistical testing workflow — from hypothesis definition to significance testing and result interpretation.

---

## 🎯 Objective
The main goal is to **determine whether the difference in conversion rates between two groups (Control vs Experimental)** is statistically significant enough to justify implementing the experimental change.

Specifically, the analysis aims to answer:

> “Does the experiment lead to a measurable improvement in click-through or conversion performance?”

---

## 📈 Methodology

## 📈 Methodology (corrected math)

### 1. **Hypothesis Definition**
We test:
\[
H_0: P_{con} = P_{exp}
\qquad\text{vs}\qquad
H_1: P_{con} \neq P_{exp}
\]
Where \(P_{con}\) and \(P_{exp}\) are the true conversion rates (proportions) for control and experiment.

---

### 2. **Parameter Definitions**
- \( \alpha \): Significance level (Type I error rate)  
- \( \beta \): Probability of Type II error  
- \( 1 - \beta \): Statistical power  
- \( \delta \): Minimum detectable effect (MDE) — absolute difference in proportions you care to detect

---

### 3. **Proportion Estimates**
Observed (sample) proportions:
\[
\hat{p}_{con} = \frac{\text{\#clicks}_{con}}{\text{\#impressions}_{con}}, \quad
\hat{p}_{exp} = \frac{\text{\#clicks}_{exp}}{\text{\#impressions}_{exp}}
\]
Sample sizes:
\[
n_{con} = \#\text{impressions}_{con}, \quad n_{exp} = \#\text{impressions}_{exp}
\]

---

### 4. **Pooled Proportion and Standard Error (for hypothesis test)**
When the null hypothesis assumes equal proportions, use the pooled estimate:
\[
\hat{p}_{pooled} = \frac{\#\text{clicks}_{con} + \#\text{clicks}_{exp}}{n_{con} + n_{exp}}
\]
Pooled standard error for the difference in proportions:
\[
SE_{pooled} = \sqrt{\hat{p}_{pooled}(1 - \hat{p}_{pooled})\left(\frac{1}{n_{con}} + \frac{1}{n_{exp}}\right)}
\]
Use this \(SE_{pooled}\) when computing the z-statistic under \(H_0: P_{con}=P_{exp}\).

**Note:** For confidence intervals or when you *do not* pool (i.e., estimating variance from each sample separately), use the unpooled standard error:
\[
SE_{unpooled} = \sqrt{\frac{\hat{p}_{con}(1 - \hat{p}_{con})}{n_{con}} + \frac{\hat{p}_{exp}(1 - \hat{p}_{exp})}{n_{exp}}}
\]

---

### 5. **Z-Test and p-value**
Z-statistic (two-sample z-test):
\[
z = \frac{\hat{p}_{exp} - \hat{p}_{con}}{SE_{pooled}}
\]
Two-sided p-value:
\[
p = 2 \times \big(1 - \Phi(|z|)\big)
\]
where \(\Phi\) is the standard normal CDF. Compare \(p\) to \(\alpha\) (commonly 0.05).

---

### 6. **Confidence Interval for Difference**
A (1 − α) two-sided confidence interval for \(\hat{p}_{exp} - \hat{p}_{con}\) uses the **unpooled** SE:
\[
(\hat{p}_{exp} - \hat{p}_{con}) \pm z_{1-\alpha/2} \cdot SE_{unpooled}
\]
where \(z_{1-\alpha/2}\) is the standard normal critical value (e.g., 1.96 for 95% CI).

---

### 7. **Decision Rule / Interpretation**
- If \(p < \alpha\): reject \(H_0\) → **significant difference detected**.  
- If \(p \ge \alpha\): fail to reject \(H_0\) → **no significant difference**.

Also check the confidence interval: if it **does not contain 0**, that supports a significant difference at the chosen confidence level.

---

### 8. **Practical notes**
- Use the pooled SE for the hypothesis test only when the null assumes equal proportions and sample sizes are reasonably large.  
- Use the unpooled SE for CIs and when variance differs notably between groups.  
- For small sample sizes or very small/large proportions, consider exact tests (e.g., Fisher's exact test) or continuity-corrected methods.

---

## 📊 Results Summary
The notebook outputs:
- Conversion rate comparison between control and experimental groups  
- Z-statistic and p-value calculations  
- A clear interpretation of whether the experimental group performs significantly better  

---
