# RishabhKumar_bitsom_ba_2511764_part2_kpi_experiment
# Campaign A/B Experiment — 

---

## Task 1: Business Problem Statement

### Decision to Be Made
Should we roll out the new **Treatment campaign** (new landing page + onboarding flow) to all users, or keep the existing Control experience?

### Who the Decision Impacts
- **Product & Growth Teams** — drive roadmap priorities for conversion optimization
- **Marketing** — determines campaign spend allocation
- **Finance** — affects revenue forecasting and unit economics
- **Customer Success** — implications for onboarding quality and support load

### Metric That Should Improve
**Primary:** Paid Conversion Rate — the share of users who convert from free/trial to a paying subscription. This directly drives revenue growth and validates product-market fit.

### Risks That Must Be Monitored
1. **Refund Rate** — an increase could indicate over-promising in the new flow
2. **Support Ticket Rate** — higher tickets signal confusion or friction post-signup
3. **Revenue Quality** — average revenue per converted user must not decline
4. **Segment-level decline** — gains in aggregate may hide losses in key sub-segments (e.g. Mobile, Organic)

### Evidence Required Before Making a Recommendation
- Statistically significant improvement in Paid Conversion Rate (α = 0.05, two-tailed)
- No material degradation in at least 3 guardrail metrics
- Consistent positive signal across at least 2 of the 4 key segments (Region, Device, Traffic Source, Plan Type)
- Hypothesis test outcome with p-value documented

---

## Task 4: Data Cleaning Documentation


### Cleaning Steps Performed

| Check | Finding | Action Taken |
|---|---|---|
| Missing values | `engagement_score`: 30 missing; `days_to_convert`: 4,675 missing (expected — non-converters) | Imputed `engagement_score` with group mean; `days_to_convert` missing for non-converters is valid |
| Group counts | Control: 2,524 / Treatment: 2,526 (raw) | Balanced after deduplication |
| Duplicate user IDs | 50 duplicate rows found | Removed all duplicates; kept first occurrence |
| Invalid binary values | `converted_to_paid` had 5 rows with value `2` | Set invalid values to `NaN` (excluded from rate calculations) |
| Outliers in revenue | 3 rows with negative revenue (-$50) | Clipped to 0 (likely data entry errors or system artifacts) |
| Segment distribution | Checked Control vs Treatment split across Region, Device, Traffic Source | Distribution was balanced — no systematic bias detected |

### Final Clean Dataset
- **Rows:** 5,000 (after removing 50 duplicates)
- **Control users:** 2,500
- **Treatment users:** 2,500
- **No formula errors in output file**

---
<img width="2985" height="1934" alt="kpi_tree" src="https://github.com/user-attachments/assets/55341a33-1871-416f-b6be-7001abfd15c0" />
<img width="2384" height="1034" alt="hypothesis_test_output" src="https://github.com/user-attachments/assets/b2826e40-28be-4811-9b05-05938c21e0a7" />
<img width="772" height="478" alt="summary_metrics_By_Device" src="https://github.com/user-attachments/assets/b7abb8d7-bab2-400a-bdda-55f23c719694" />
<img width="1150" height="605" alt="summary metrices" src="https://github.com/user-attachments/assets/c398b481-d4c6-46eb-8f2e-df6ad690dceb" />
<img width="852" height="495" alt="summary_metrics_By_Region" src="https://github.com/user-attachments/assets/489d7ba6-d4ed-45ed-9c05-6b2e168369af" />
<img width="888" height="449" alt="summary_metrics_By_Traffic_Source" src="https://github.com/user-attachments/assets/3783b94c-1884-4557-915d-6d9541eb8421" />

