# GT Racing Entry Decision Framework  
### A Stage-Gated Analytics Model for OEM Go / No-Go Strategy

## Overview

This project develops a repeatable decision framework for evaluating whether an automotive OEM should enter a GT racing series by converting an existing production vehicle into a race-ready platform.

The framework combines synthetic motorsport datasets, public-style market benchmarks, engineering feasibility assumptions, regulatory risk factors, customer economics, and brand strategy inputs to generate a structured **Go / Conditional Go / No-Go** recommendation.

This was completed as a Carnegie Mellon University Tepper School of Business MSBA capstone project.

---

## Business Problem

GT racing entry decisions are complex because OEMs must commit significant capital before market demand, performance outcomes, and regulatory constraints are fully known.

Key challenges include:

- Multi-million-dollar vehicle development and conversion costs
- Homologation and compliance uncertainty
- Balance of Performance, or BoP, volatility
- Uncertain customer racing demand
- Different economics across GT3 and GT4 tiers
- Competitive pressure from established OEM racing programs

The core question this project addresses is:

> Which vehicle-to-racing-class pairing creates the strongest business case when evaluated across platform feasibility, regulatory risk, customer economics, brand impact, and competitive dynamics?

---

## Analytical Approach

The model uses a multi-stage gate framework. Instead of producing a single black-box score, each gate evaluates a specific decision layer and passes only viable candidates forward.

### Stage-Gate Framework

| Gate | Focus Area | Purpose |
|---|---|---|
| Gate 0 | Brand Intent | Defines the OEM’s strategic objective and KPI priorities |
| Gate 1 | Platform Feasibility | Filters production vehicles based on feasibility, compliance risk, and platform status |
| Gate 2 | Compliance & BoP Risk | Scores regulatory and performance-balancing risk |
| Gate 3 | Customer Economics | Estimates demand, unit economics, breakeven feasibility, and profit potential |
| Gate 4 | Brand Ladder Fit | Evaluates GT4-to-GT3 ladder potential, activation value, and brand alignment |
| Gate 5 | Final Weighted Score | Produces Go / Conditional Go / No-Go recommendations |

---

## Data Sources

The public-facing version of this project uses synthetic and public-style proxy datasets to protect sponsor-sensitive information.

The model is structured around 13 Excel sheets, including:

- Brand KPI weights
- Competitive activation benchmarks
- Customer personas and preferences
- Production platform inventory
- Regulatory fit and conversion burden
- BoP volatility risk index
- GT series assumptions
- Regional team demand proxies
- Competitor economics benchmarks
- Synthetic bill-of-materials proxy
- Unit economics model
- Stage-gate decision log

---

## Tools Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Excel
- Jupyter Notebook / Google Colab
- Business analytics storytelling
- Stage-gate decision modeling
- Synthetic data design
- Scenario analysis

---

## Model Logic

### Gate 0: Brand Intent Scoring

Gate 0 defines the OEM’s strategic objective by evaluating weighted brand KPIs such as earned media, dealer event attendance, qualified leads, and customer racing unit sales.

The model calculates KPI lift from baseline to Year 1 target, multiplies each lift by KPI weight, and aggregates the result into a brand intent score.

In the final model, the top strategic objective was identified as:

> Tiered ladder strategy

---

### Gate 1: Platform Feasibility Filtering

Gate 1 screens production platforms using feasibility flags, program status, compliance risk, and platform strength.

Candidates are removed if they fail hard filters such as:

- Infeasible conversion status
- Sunset production platform
- Excessive compliance risk

The surviving shortlist contained 8 platform-class combinations.

---

### Gate 2: Compliance and BoP Risk

Gate 2 evaluates whether a candidate can remain competitive under regulatory and performance-balancing constraints.

The combined risk score incorporates:

- BoP volatility index
- Compliance risk index
- Setup window
- Drivability
- Engineering complexity

This helps separate candidates that are technically feasible from competitively sustainable candidates.

---

### Gate 3: Customer Economics

Gate 3 evaluates whether the racing program can make financial sense.

The economics model considers:

- Active cars by region and series
- New purchases per season
- Race car MSRP
- Gross margin
- Annual spares revenue
- Annual support cost
- Breakeven volume
- Three-year projected unit sales

The output is an economics score and an estimated annual profit indicator for each surviving candidate.

---

### Gate 4: Brand Ladder Fit

Gate 4 evaluates whether the candidate supports a broader racing ecosystem.

The ladder score combines:

- Persona coverage across GT4 and GT3 budgets
- Market activation potential
- Earned media and social index benchmarks
- KPI alignment with brand strategy

This gate is designed to capture whether a platform supports more than a one-time racing entry.

---

### Gate 5: Final Weighted Recommendation

The final score combines brand, platform, risk, economics, and ladder dimensions.

```text
Total Score =
  Brand Score   * 0.20
+ Platform Fit  * 0.20
+ Risk Score    * 0.20
+ Econ Score    * 0.25
+ Ladder Score  * 0.15
