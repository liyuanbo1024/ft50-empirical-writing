---
name: ft50-empirical-writing
description: Use when writing empirical research papers targeting FT50 journals across management disciplines. Covers causal identification (DID, RDD, IV, synthetic control, RCT), panel data methods, endogeneity solutions, robustness frameworks, and the full empirical pipeline from research question through identification, analysis, robustness, and writing.
---

# FT50 Empirical Research Paper Writing

## Overview

This skill covers empirical research methods and writing conventions for the **FT50 journal list**—the 50 premier journals used in the Financial Times research ranking across all management disciplines (accounting, finance, management, marketing, operations, information systems, etc.).

The empirical pipeline: **Research Question → Theory/Mechanism → Identification Strategy → Data → Baseline Results → Robustness → Mechanism Evidence → Implications**.

**Core Principle**: An empirical paper's credibility rests on its **identification strategy**. The central question is not "Did the authors find an association?" but "Have the authors convincingly established a causal relationship, and through what mechanism?"

---

## When to Use This Skill

- Writing any empirical paper targeting FT50 journals
- Designing causal identification strategies (DID, RDD, IV, RCT, synthetic control)
- Addressing endogeneity concerns
- Building robustness sections that satisfy FT50 reviewers
- Conducting mechanism/mediation analysis
- Writing up empirical results for top management journals

---

## The FT50 Empirical Paper Structure

| Section | Typical Pages | Key Content |
|---------|--------------|-------------|
| Abstract | 150-250 words | Research question, identification, key finding, implication |
| S1 Introduction | 2-3 pages | Motivating puzzle → Research question → Identification approach → Findings → Contributions |
| S2 Theory & Hypotheses | 2-4 pages | Theoretical mechanism → Testable predictions (H1, H2, H3...) |
| S3 Institutional Context & Data | 3-5 pages | Institutional details, data sources, sample construction, descriptive statistics |
| S4 Identification Strategy | 1-2 pages | Source of variation, identifying assumptions, specification |
| S5 Baseline Results | 3-5 pages | Main regression tables, economic significance |
| S6 Robustness | 3-5 pages | Alternative specifications, samples, measures; placebo tests |
| S7 Mechanism Evidence | 2-4 pages | Mediation, moderation, cross-sectional heterogeneity |
| S8 Discussion & Conclusion | 1-2 pages | Contributions, limitations, implications |

---

## Identification Strategies

### 1. Difference-in-Differences (DID)

**Standard 2×2 DID**:
$Y_{it} = \alpha_i + \lambda_t + \beta \cdot \text{Treat}_i \times \text{Post}_t + \varepsilon_{it}$

**Staggered DID** (treatment at different times):
- Problem: Two-way fixed effects (TWFE) with staggered adoption gives biased estimates under heterogeneous treatment effects
- Solutions: Callaway & Sant'Anna (2021), Sun & Abraham (2021), Borusyak et al. (2024), de Chaisemartin & D'Haultfoeuille (2020)
- Event study plots: $\beta_k$ for $k$ periods before/after treatment, with binned endpoints

**DID Checklist**:
- [ ] Parallel pre-trends shown visually (event study plot)
- [ ] No anticipation effects (pre-trend coefficients ≈ 0)
- [ ] Staggered DID uses modern estimator (not vanilla TWFE)
- [ ] Treatment is as-good-as-random conditional on covariates
- [ ] Results robust to: different control groups, excluding never-treated, different estimators

### 2. Regression Discontinuity (RDD)

**Sharp RDD**: $Y_i = \alpha + \beta \cdot I\{X_i \geq c\} + f(X_i - c) + \varepsilon_i$

**Fuzzy RDD**: When compliance is imperfect; treatment effect = Wald estimator (jump in outcome / jump in treatment)

**RDD Checklist**:
- [ ] McCrary density test: no manipulation of the running variable at cutoff
- [ ] Pre-determined covariates are smooth across cutoff (balance test)
- [ ] Results robust to bandwidth choice (IK, CCT, alternative bandwidths)
- [ ] Results robust to polynomial order (linear, quadratic)
- [ ] Placebo cutoffs at other values show no effect
- [ ] Donut-hole RDD (excluding observations near cutoff) as robustness

### 3. Instrumental Variables (IV)

**2SLS**: First stage: $X_i = \pi Z_i + \gamma' W_i + \nu_i$; Second stage: $Y_i = \beta \hat{X}_i + \delta' W_i + \varepsilon_i$

**IV Checklist**:
- [ ] First-stage F-statistic > 10 (Stock-Yogo critical values)
- [ ] Relevance: instrument strongly predicts endogenous variable
- [ ] Excludability: instrument affects outcome only through the endogenous variable
- [ ] Monotonicity: instrument affects treatment in one direction for all units
- [ ] Plausible exogeneity argument (institutional knowledge, not just statistical tests)
- [ ] Overidentification tests (if multiple instruments): Hansen J p > 0.10
- [ ] "Plausibly exogenous" bounds (Conley et al. 2012) if exogeneity is imperfect

### 4. Randomized Controlled Trials (RCT)

**Analysis**: $Y_i = \alpha + \beta \cdot T_i + \gamma' X_i + \varepsilon_i$

**RCT Checklist**:
- [ ] Pre-registration (AEA RCT Registry, OSF, AsPredicted)
- [ ] Power analysis justifying sample size
- [ ] Randomization procedure described
- [ ] Balance table comparing treatment/control on observables
- [ ] Attrition analysis (differential attrition?)
- [ ] Intent-to-treat (ITT) as primary; TOT/LATE as secondary
- [ ] Multiple testing correction (Bonferroni, Holm, FDR)
- [ ] CONSORT flow diagram for participant flow

### 5. Synthetic Control

For single or few treated units, construct a synthetic counterfactual as a weighted combination of control units.

**SCM Checklist**:
- [ ] Pre-treatment fit is good (low MSPE relative to post-treatment)
- [ ] Weights are sparse (few control units get positive weight)
- [ ] Placebo tests: apply to each control unit; treatment effect should be extreme
- [ ] Robustness to donor pool composition
- [ ] Inference via permutation/randomization

### 6. Matching Methods

- **Propensity Score Matching (PSM)**: Match on estimated propensity score
- **Coarsened Exact Matching (CEM)**: Match on discretized covariates
- **Entropy Balancing**: Weight control units to match treatment moments
- **Note**: Matching is increasingly viewed as supplementary to, not a substitute for, quasi-experimental design in FT50 journals

---

## Robustness: The FT50 Standard

FT50 reviewers expect extensive robustness. A minimal robustness section includes:

| Category | Typical Checks |
|----------|---------------|
| **Alternative dependent variable** | Different measure, logged vs. level, per-capita vs. total |
| **Alternative independent variable** | Continuous vs. binary, different threshold |
| **Alternative sample** | Exclude outliers, different time window, different industries |
| **Alternative specification** | Different fixed effects, different controls, different functional form |
| **Alternative estimator** | OLS vs. Poisson, FE vs. RE, different cluster level |
| **Placebo / Falsification** | Fake treatment at different time/place; outcome shouldn't respond |
| **Selection on unobservables** | Oster (2019) bounds; Altonji et al. (2005) ratio test |

### Oster Bounds

$\beta^* \approx \tilde{\beta} - \delta(\dot{\beta} - \tilde{\beta}) \frac{R_{\max} - \tilde{R}}{\tilde{R} - \dot{R}}$

Where $\dot{\beta}, \dot{R}$ are from uncontrolled regression; $\tilde{\beta}, \tilde{R}$ from controlled. $\delta = 1$ assumes equal selection on observables and unobservables. $R_{\max} = 1.3 \times \tilde{R}$ is standard.

---

## Mechanism Evidence

FT50 reviewers increasingly demand evidence on **why** an effect occurs.

### Approaches

1. **Mediation analysis** (Baron-Kenny or Imai et al. 2010): Decompose total effect into direct and indirect
2. **Moderation / Heterogeneity**: Effect stronger where theory predicts it should be
3. **Cross-sectional tests**: Split sample by predicted mechanism strength
4. **Additional dependent variables**: Show treatment affects the hypothesized mediator
5. **Process evidence**: Qualitative or survey evidence on the mechanism

### Reporting Guideline

For each hypothesis:
1. State the hypothesized mechanism
2. Report the test of the mechanism
3. Interpret the economic significance of the mechanism channel
4. Acknowledge alternative mechanisms that cannot be ruled out

---

## Writing Patterns for FT50 Journals

### Pattern 1: The Motivating Puzzle
Open with an empirical puzzle that contradicts conventional wisdom or theory. "Why do firms continue to [action] despite [evidence that it's suboptimal]?"

### Pattern 2: The Institutional Detail
Use rich institutional knowledge to motivate the identification strategy. The best FT50 papers make the reader feel "only someone who deeply understands this setting could have designed this test."

### Pattern 3: The Coefficient of Interest
Lead every results table with the coefficient of interest, not control variables. Make the key finding visually immediate.

### Pattern 4: The Robustness Pyramid
Structure robustness from most to least threatening: (1) alternative identification, (2) alternative measures, (3) alternative samples, (4) alternative specifications, (5) alternative estimators.

---

## Common FT50 Rejection Reasons

| Reason | Frequency | Prevention |
|--------|-----------|------------|
| Endogeneity not convincingly addressed | Very High | Explicit identification section; multiple strategies |
| Mechanism unclear ("black box" result) | High | Dedicated mechanism section |
| Selection on unobservables threatens inference | High | Oster bounds, Altonji tests, Rosenbaum bounds |
| Low economic significance | Medium | Report elasticities, not just coefficients |
| Generalizability concerns | Medium | Discuss external validity explicitly |
| Contribution is incremental | Medium | Clearly articulate novelty relative to 3-5 closest papers |

---

## 0-to-Draft Pipeline

### Stage 1: Question & Positioning
- Formulate research question as a causal claim
- Identify 3-5 closest papers and articulate gap
- Choose target FT50 journal based on topic fit

### Stage 2: Identification Design
- Articulate identification strategy
- Source of exogenous variation
- Identifying assumptions and how they're tested
- Draft §4 (Identification) and §3 (Data)

### Stage 3: Analysis
- Baseline results (main tables)
- Robustness section (10+ checks)
- Mechanism evidence
- Draft §5-7

### Stage 4: Writing
- Introduction with motivating puzzle
- Theory & hypotheses section
- Discussion connecting to literature
- Draft §1, §2, §8

### Stage 5: Polish
- Abstract
- Tables formatted to FT50 standard
- All checks completed
- Circulate for colleague feedback before submission

---

## References

- [references/identification-strategies.md](references/identification-strategies.md): DID, RDD, IV, RCT, synthetic control, matching — detailed implementation
- [references/robustness-framework.md](references/robustness-framework.md): Comprehensive robustness checklist by method type
- [references/ft50-journals.md](references/ft50-journals.md): FT50 journal list with discipline mapping and editorial expectations
- [references/writing-patterns.md](references/writing-patterns.md): Reusable writing patterns for empirical papers
