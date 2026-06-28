# Hypothesis Test Notes — Campaign A/B Experiment

## Task 6: Hypothesis Framing

### Primary Metric: Paid Conversion Rate

**Null Hypothesis (H₀):**
> The Paid Conversion Rate for the Treatment group is equal to the Paid Conversion Rate for the Control group.
> H₀: p_treatment = p_control

**Alternate Hypothesis (H₁):**
> The Paid Conversion Rate for the Treatment group is different from the Control group.
> H₁: p_treatment ≠ p_control

**Test Type:** Two-tailed (we want to detect both positive and negative effects)

**Significance Level:** α = 0.05

**Metric Being Tested:** Paid Conversion Rate (binary: 1 = converted, 0 = not converted)

**Reason for Choosing This Metric:**
Paid Conversion Rate is the North Star metric for this experiment. It directly measures whether the new campaign experience drives users to become paying customers. All other funnel metrics (landing page visits, trial starts, onboarding completion) are intermediate — only paid conversion translates to revenue.

**Interpretation Logic:**
- If p-value < 0.05 → Reject H₀ → Treatment has a statistically meaningful effect on conversion
- If p-value ≥ 0.05 → Fail to reject H₀ → No sufficient evidence of a real difference
- Connection to business decision: A statistically significant positive result supports a launch recommendation, **subject to guardrail checks**

---

## Task 7: Hypothesis Test Results

### Test Method: Two-Proportion Z-Test

| Parameter | Value |
|---|---|
| Control conversion rate | 5.00% (125 / 2,500) |
| Treatment conversion rate | 9.80% (245 / 2,500) |
| Absolute lift | +4.80 percentage points |
| Relative lift | +96.0% |
| Pooled proportion | 0.0740 |
| Standard error | 0.00741 |
| **Z-statistic** | **6.4830** |
| **p-value** | **< 0.000001** |
| Critical value (α=0.05, two-tailed) | ±1.96 |
| **Decision** | **REJECT H₀** |

### Secondary Test: Average Revenue Per User (t-test)

| Parameter | Value |
|---|---|
| Control ARPU | $5.19 |
| Treatment ARPU | $10.83 |
| t-statistic | 5.12 |
| p-value | < 0.000001 |
| Decision | REJECT H₀ — ARPU also significantly higher |

### Business Interpretation

> **The Treatment campaign produces a statistically significant improvement in Paid Conversion Rate at the 99.99%+ confidence level.** The Z-statistic of 6.48 is far beyond the critical value of ±1.96, and the p-value is essentially zero — this result is extremely unlikely to have occurred by chance. The treatment nearly doubles conversion rate and more than doubles average revenue per user. **This is a strong signal to proceed with launch, pending guardrail review.**

*Evidence saved as: `screenshots/hypothesis_test_output.png`*
