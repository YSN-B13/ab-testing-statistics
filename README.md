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

### 1. **Hypothesis Definition**
We define the null and alternative hypotheses as follows:

\[
H_0: P_{con} = P_{exp} \\
H_1: P_{con} \neq P_{exp}
\]

Where:  
- \( P_{con} \): Conversion rate of the control group  
- \( P_{exp} \): Conversion rate of the experimental group  

---

### 2. **Parameter Definitions**
Key statistical parameters include:

- \( \alpha \): Significance level (Type I error rate)  
- \( \beta \): Probability of Type II error  
- \( (1 - \beta) \): Statistical power  
- \( \delta \): Minimum detectable effect (MDE)  

---

### 3. **Proportion Estimation**
Conversion rate (proportion) for each group is computed as:

\[
\hat{p}_{con} = \frac{\#clicks_{con}}{\#impressions_{con}}, \quad
\hat{p}_{exp} = \frac{\#clicks_{exp}}{\#impressions_{exp}}
\]

---

### 4. **Pooled Variance & Standard Error**
The pooled proportion and its variance are calculated to prepare for the z-test:

\[
\hat{p}_{pooled} = \frac{\#clicks_{con} + \#clicks_{exp}}{\#impressions_{con} + \#impressions_{exp}}
\]

---

### 5. **Z-Test for Difference in Proportions**
A **two-sample z-test** is conducted to assess whether the observed difference is statistically significant:

\[
z = \frac{\hat{p}_{exp} - \hat{p}_{con}}{s_{pooled}}
\]

The corresponding **p-value** is then compared with \( \alpha = 0.05 \).

---

### 6. **Result Interpretation**
- If \( p < \alpha \): Reject \( H_0 \) → **Significant difference detected**  
- If \( p \geq \alpha \): Fail to reject \( H_0 \) → **No significant difference**  

---

## 📊 Results Summary
The notebook outputs:
- Conversion rate comparison between control and experimental groups  
- Z-statistic and p-value calculations  
- A clear interpretation of whether the experimental group performs significantly better  

---
