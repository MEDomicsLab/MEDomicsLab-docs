---
description: >-
  This proof of concept demonstrates the ability of the MEDomics platform to
  support a complete end-to-end machine learning workflow in a healthcare
  context, from data preparation to cross-institutional
icon: wpforms
---

# End-to-End MEDomics Pipeline

{% hint style="success" %}
The data used in this demonstration is publicly available, and we recommend that you follow the steps below to obtain similar results.
{% endhint %}

### About the Datasets

This proof of concept relies on two publicly available intensive care unit (ICU) datasets:

* **MIMIC-IV**
* **eICU Collaborative Research Database**

Access to these datasets requires prior certification and approval through PhysioNet, due to the sensitive nature of clinical data.

To facilitate reproducibility and simplify the execution of this proof of concept, we provide preprocessed datasets derived from MIMIC-IV and eICU, corresponding to the final inputs used in the pipeline.

These preprocessed datasets include:

* MIMIC learning dataset
* MIMIC holdout dataset
* eICU learning datasets for 9 hospitals
* eICU holdout datasets for 9 hospitals
* Aggregated eICU holdout dataset

These processed datasets represent the final outputs of the preprocessing pipeline and allow users to directly reproduce the experimental workflow without repeating the full preprocessing steps.

For users who wish to fully replicate the pipeline from the raw datasets, all preprocessing steps will also be documented in detail in this page.

For data governance and compliance reasons, these processed datasets will be made available only to users who already have authorized access to MIMIC-IV and eICU through PhysioNet.

This approach ensures both reproducibility and compliance with data usage policies.

{% hint style="info" %}
You can find the original datasets here : MIMIC ([https://physionet.org/content/mimiciv/3.1/](https://physionet.org/content/mimiciv/3.1/)) and eICU ([https://physionet.org/content/eicu-crd/2.0/](https://physionet.org/content/eicu-crd/2.0/)).
{% endhint %}

### Goal

This proof of concept demonstrates how the MEDomics platform can support an end-to-end machine learning workflow in a healthcare context, while integrating federated learning capabilities and enabling the comparison of different training strategies.

This work is inspired by the **MED3pa framework** introduced in [_Predictive Performance Precision Analysis in Medicine: Identification of low-confidence predictions at patient and profile levels (MED3pa)_](https://doi.org/10.1093/jamia/ocag034) (JAMIA, 2026). In particular, this proof of concept reuses the same datasets (MIMIC-IV and eICU), adopts similar preprocessing principles, and relies on SAPS-based feature processing and cross-hospital evaluation settings described in the original study.

While [MED3pa](https://pypi.org/project/MED3pa/) focuses on analyzing model reliability and identifying low-confidence predictions, the objective of this proof of concept is different. Here, the goal is to demonstrate the integration of federated learning within MEDomics using MEDfl, to compare centralized and federated training strategies within a unified end-to-end workflow and to evaluate cross-hospital generalization.

Preprocessing steps adapted from the MED3pa study are referenced for transparency, but are not reproduced in detail in this proof of concept, as the focus is on model training with a MLP (Multi Layer Perceptron) supported within our platforms, federated learning, and cross-institutional evaluation within the MEDomics platform.

### Steps

Here are the steps followed in this demonstration:

{% stepper %}
{% step %}
### Preprocessing Steps&#x20;

In this step, we prepare the MIMIC-IV and eICU datasets using preprocessing procedures adapted from previous work. These steps include feature selection, dataset alignment, and preparation of learning and holdout datasets.

To keep the focus on training and evaluation, preprocessing is only briefly described for transparency, while preprocessed datasets are provided to directly run the end-to-end workflow.
{% endstep %}

{% step %}
### Learning Module

The Learning Module is used to train an MLP model using the MIMIC learning dataset. This step defines the centralized learning baseline that will later be evaluated on multiple datasets.
{% endstep %}

{% step %}
### MEDfl

In this step, we simulate a federated learning setup using multiple hospitals from the eICU dataset and the MEDfl app. This allows us to train a federated model and compare its performance with the centralized model.
{% endstep %}

{% step %}
### Evaluation Module for Centralized Learning

The centralized model trained on MIMIC is evaluated using:

* MIMIC holdout dataset (internal validation)
* eICU aggregated holdout (external validation)
* Selected hospitals (188, 199, 177) for site-specific evaluation
{% endstep %}

{% step %}
### Evaluation Module for Federated Learning

The federated model is evaluated using the same evaluation strategy, enabling a direct comparison between centralized and federated learning approaches.
{% endstep %}
{% endstepper %}
