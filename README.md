# 🧪 A/B Testing Analysis

## 📘 Project Overview
This project implements a **comprehensive A/B testing analysis** to evaluate whether a modification in an experimental group (e.g., new design, feature, or algorithm) has a **statistically significant effect** compared to a control group.

The notebook walks through each step of a rigorous statistical testing process — from hypothesis definition to significance testing and interpretation of results.

---

## 🎯 Purpose
The main objective is to **determine if the conversion rate difference between two groups (Control vs Experimental)** is significant enough to justify deploying the experimental change.

Specifically, the notebook helps answer:
> “Does the experiment lead to a measurable improvement in click-through or conversion performance?”

---

## 📈 Methodology

### 1. **Hypothesis Setup**
Formulates the null and alternative hypotheses:

\[
H_0: P_{con} = P_{exp} \\
H_1: P_{con} \neq P_{exp}
\]

Where:
- \( P_{con} \): Conversion rate of the control group  
- \( P_{exp} \): Conversion rate of the experimental group  

---

### 2. **Parameter Definitions**
Includes:
- \( \alpha \): Significance level (Type I error)  
- \( \beta \): Probability of Type II error  
- \( (1 - \beta) \): Statistical power  
- \( \delta \): Minimum detectable effect  

---

### 3. **Proportion Estimation**
Calculates proportions for both groups:

\[
\hat{p}_{con} = \frac{\#clicks_{con}}{\#impressions_{con}}, \quad
\hat{p}_{exp} = \frac{\#clicks_{exp}}{\#impressions_{exp}}
\]

---

### 4. **Pooled Variance and Standard Error**
Computes pooled proportion and its variance to prepare for the z-test:

\[
\hat{p}_{pooled} = \frac{\#clicks_{con} + \#clicks_{exp}}{\#impressions_{con} + \#impressions_{exp}}
\]

---

### 5. **Z-Test for Proportions**
Performs a **two-sample z-test** for the difference in proportions:

\[
z = \frac{\hat{p}_{exp} - \hat{p}_{con}}{s_{pooled}}
\]

The resulting **p-value** is compared against \( \alpha = 0.05 \) to assess statistical significance.

---

### 6. **Interpretation**
Interprets the statistical result:
- If \( p < \alpha \): reject \( H_0 \) → significant difference  
- If \( p \geq \alpha \): fail to reject \( H_0 \) → no significant difference  

---

## 🧮 Tools & Libraries
- **Python 3**
- **NumPy** – numerical computations  
- **SciPy** – statistical testing  
- **Matplotlib / Seaborn** – visualization  
- **Pandas** – data manipulation  

---

## 📊 Results Summary
The notebook provides:
- Conversion rate comparison between control and experiment  
- Z-test and p-value computation  
- Interpretation of whether the experimental group performs significantly better  
