
<!-- README.md is generated from README.Rmd. Please edit that file -->

# Comparing approaches for combining infectious disease models using synthetic data.

## Introduction

*Background*

Applied infectious disease modelling studies typically only consider a
single model structure. This may be because there is only a single
plausible model or it may be because of limited compute, little
awareness of the impact of assuming a single model structure or no
awareness as to the methods available for multi-model weighting. An
example of this problem in practise is Tuberculosis (TB) modelling where
the biological mechaism for latent TB must be assumed and often cannot
be inferred from the data. The choice of serial latency will then impact
model fit and may also influence the estimation of the impact of
interventions on Latent TB cases. In this stuy we explore the impact of
considering multiple model approaches using a variety of sythentic data
scenarios. *Detail*

**Model weighting**

  - DIC
  - SMC-SMC
  - Posthoc weighting?

**Latency** - after an initial infection 5-10% of individuals develop
symptomatic TB within 1-2 years. The majority of individuals enter a
latent state in which they passively carry TB mycobacterium but are not
symptomatic. Reactivation of the bacilli can then occur many years later
due to a lose of immune control.\[10\] Simplistically latent TB may be
modeled with a single latent compartment\[99\], more commonly an
additional transition rate between the susceptible and active disease
states is added.\[100\] This represents rapid progression to active
disease, and slower progression via a low risk latent stage. Both of
these model structures have been shown to not fit activation data
well.\[100,101\] More complex structures that are commonly used
incorporate either parallel or serial latency (Figure 8.1). Both of
these structures incorporate both slow and fast latent periods and have
been shown to produce identical activation dynamics.\[101\] This is
unfortunate as they represent two disparate biological mechanisms, with
the serial assumption representing decreasing risk over time for
individuals and the parallel assumption suggesting that a subset of
individuals are at a greater risk of developing active TB disease. For
models that seek to investigate interventions targeted at latent cases
this structural uncertainty is problematic.

*Aim*

Compare and contrast modelling approaches when the underlying data
generation mechaism maybe uncertain

## Methods

### Models

  - Simple latency
  - Serial latency
  - Parallel latency
  - Combined serial and parallel latency
  - All coded in a combined `LibBi` format.
  - Other model details kept as simple as possible.

### Sythentic data scenarios

  - Assume a local epidemic scenario.
  - Generate data via an observational model on incidence. Assume data
    collection here is relatively robust (i.e a national surveillance
    network).
  - Generate data via an observational model on initial infection (i.e
    susceptible -\> latent). Assume data collection here is very poor.
  - Generate data using `rbi` and `LiBbi`.
  - Scenarios: All serial latency; all parallel latency; equal split
    between all 3 models; 50% serial latency, 30% parallel latency, and
    20% simple latency.
  - Secondary scenarios: No information on initial infection, partial
    information on initial infections, full (with noise) informations in
    initial infection.

*I am concerned about using TB latency here as it is very unlikely that
the modeller will have data on initial infections. Without this they
cannot determine which model to use (nor can any of the approaches
below). It might be better to choose a case study for which data is
available to fit to but for which it is plausible that a combination of
mechanisms (that changes depending on scenario) is in place.*

### Model fitting

  - Fit models using SMC-SMC via `LibBi` and `rbi`.

### Multi-model approaches

  - Model weighting during SMC-SMC fitting (via particle selection).
  - Posthoc model weighting - more detail needed here on how to do this.

## Results

### Best fitting models by scenario

  - Using DIC compare the best fitting models by scenario

### Combination model selected using SMC

  - Results from SMC compared to best model per scenario
  - Discuss impact of considering results across scenarios

### Combination model selected using posthoc weighting

  - Results from posthoc weighting compared to best model per scenario
  - Results from posthoc weighing compared to SMC
  - Discuss results across scenarios

### Computational efficiency

  - Compare compute time for each method by scenario
  - Discuss trends across scenarios

## Discussion

### Statement of primary findings

  - Summarise impact of combination model use across scenarios
  - Summarise the benefits of each approach.

### Strengths and limitations of the study

  - Synthetic data so complexity of mechanisms can be adjusted.
  - Only a single case study.
  - Not real data.

### Strengths and limitations in comparison to the literature

### Meaning of the study

  - Combined modelling approaches should be considered when the
    underlying biological mechanism is uncertain. In scenarios with
    several plausible mechanisms not doing so may introduce bias into
    the findings.
  - Within model fitting approaches (such as SMC-SMC) are likely to be
    more computationally efficient than posthoc model weighting
    approaches.

### Unanswered questions and future research

  - Other case studies
  - Apply to real data\!
