# Modeling Reliance on Social Media for Political Information  
### An Ordinal Logistic Regression Analysis Using World Values Survey Data

## Overview

This repository contains a short academic paper and supporting materials for an analytics project examining how socioeconomic status (SES) relates to individuals’ reliance on social media as a source of political and public information.

The study models the frequency of social media use for information as an ordinal outcome and investigates how social class and income level shape digital information behavior. The analysis is based on data from the World Values Survey (WVS) and applies ordinal logistic regression.

This work was completed during my second semester of graduate study as part of an analytics project requirement.

---

## Research Question

**How do income level and perceived social class influence the frequency with which individuals rely on social media for political and public information?**

---

## Data

- **Source:** World Values Survey (WVS)
- **Sample size:** 1,199 observations after excluding incomplete cases
- **Missing values:** WVS codes for non-response were converted to `NA` and removed via complete-case filtering
- **Software:** R

No proprietary or restricted data are included in this repository.

---

## Variables

### Response Variable
**Q207 – Frequency of Social Media Use for Information**  
Ordinal outcome with five ordered levels:
1. Daily  
2. Weekly  
3. Monthly  
4. Less than monthly  
5. Never  

### Predictor Variables
- **Q287 – Subjective Social Class**  
  Self-reported class identification ranging from upper class to lower class.

- **Q288R – Income Level (Recoded)**  
  Recoded into three ordinal categories:
  - Low income (steps 1–3)
  - Medium income (steps 4–7)
  - High income (steps 8–10)

Both predictors were modeled as ordered factors to preserve ordinal structure.

---

## Methodology

The analytical pipeline combines exploratory and inferential techniques:

1. **Exploratory Analysis**
   - Spearman’s rank correlations to assess monotonic relationships between SES variables and social media reliance.

2. **Ordinal Logistic Regression**
   - Cumulative logit model estimated using `polr()` from the `MASS` package:
     
     \[
     \log\left(\frac{P(Y \ge j)}{P(Y < j)}\right) = \theta_j - (\beta_1 \text{Social Class} + \beta_2 \text{Income}), \quad j = 2,\dots,5
     \]

3. **Model Diagnostics**
   - Brant test to formally assess the proportional odds assumption
   - Stratified cumulative log-odds summaries
   - Auxiliary binary logistic regressions across cumulative thresholds

4. **Interpretation**
   - Predicted probabilities computed and visualized to illustrate behavioral gradients across SES groups

---

## Key Findings

- Both **subjective social class** and **income level** exhibit statistically significant positive associations with more frequent reliance on social media for political information.
- The proportional odds assumption is satisfied (Brant test, p > 0.05), validating the ordinal modeling framework.
- The strongest variation appears at the extremes (“Daily” vs. “Never”), indicating polarized engagement patterns driven by SES.
- Social class effects persist even among higher-income groups, highlighting the importance of subjective status beyond material access.

---

## Practical Implications

The findings suggest that:
- Digital engagement strategies can be better targeted by accounting for both economic and perceived social positioning.
- Policymakers, advocacy groups, and media organizations may more effectively reach specific audiences by leveraging platforms aligned with SES-driven consumption behaviors.

---

## Notes on Scope and Limitations

- The analysis prioritizes **interpretability and statistical validity** over model complexity.
- Results are observational and do not imply causality.
- Extensions could include additional covariates, interaction effects, or longitudinal analysis.

---

## Contents

