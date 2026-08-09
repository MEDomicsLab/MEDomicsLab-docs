---
description: >-
  This proof of concept relies on preprocessed datasets derived from the
  MIMIC-IV and eICU databases. The preprocessing pipeline is inspired by the
  MED3pa study, including SAPS-based feature processing.
icon: '1'
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
---

# Preprocessing Steps

{% hint style="warning" %}
This page won't contain actual tutorials on the preprocessing steps, but more of an overview of these steps. We will link similar tutorials for some steps.
{% endhint %}

The main preprocessing steps are described below.

### Source Datasets

In this proof-of-concept, we use two publicly-available datasets.

_<mark style="color:$warning;">**MIMIC-IV**</mark>_

The MIMIC-IV (Medical Information Mart for Intensive Care) dataset is a publicly available clinical database developed by the MIT Laboratory for Computational Physiology. It contains de-identified health data from patients admitted to intensive care units at Beth Israel Deaconess Medical Center in Boston, USA.

MIMIC-IV includes:

* More than 70,000 ICU stays
* Approximately 40,000–50,000 unique patients
* Data collected between 2008 and 2019
* Demographics, vitals, lab results, diagnoses, procedures, and outcomes

In this proof of concept, MIMIC-IV is used as the centralized training dataset, allowing us to train a baseline model that will later be evaluated across hospitals.

_<mark style="color:$warning;">**eICU Collaborative Research Database**</mark>_

The eICU Collaborative Research Database is a multi-center ICU database developed by Philips Healthcare and released via PhysioNet. It contains data collected from multiple hospitals across the United States.

The eICU dataset includes:

* Data from over 200 hospitals
* More than 200,000 ICU admissions
* Approximately 139,000 patients
* Data collected between 2014 and 2015

Unlike MIMIC-IV, eICU is **multi-center**, making it particularly suitable for cross-hospital evaluation, model generalization studies and federated learning simulations.

{% hint style="warning" %}
Access to both datasets requires certification through PhysioNet.
{% endhint %}

### 1- SAPS-based Processing

The **Simplified Acute Physiology Score II (**[**SAPS-II**](https://www.mdcalc.com/calc/4044/simplified-acute-physiology-score-saps-ii)**)** is a clinical scoring system used to estimate mortality risk in ICU patients based on physiological and clinical predictors.

In this proof of concept, we apply SAPS-based transformations inspired by the MED3pa study to harmonize variables across datasets. Raw physiological measurements are converted into clinically meaningful predictors following SAPS-II definitions.

{% hint style="info" %}
The SAPS preprocessing transformations are available through [this](https://github.com/Olivier998/study_3pa/blob/main/src/data/saps_processing.py) Python code from the 3PA study.
{% endhint %}

These transformations include variables such as age, vital signs, laboratory values, and clinical indicators. Applying SAPS-based processing helps standardize features across MIMIC-IV and eICU, improving cross-dataset comparability and model generalization.

Additional preprocessing steps are also applied to handle specific clinical variables. In particular, a **ventilation correction** is performed to infer missing values for ventilation indicators based on the availability of **PaO₂/FiO₂** measurements.

{% hint style="info" %}
This transformation is also implemented in the preprocessing [code](https://github.com/Olivier998/study_3pa/blob/main/src/data/processing_in_hospital_mortality.py) provided with the 3PA study.
{% endhint %}

These preprocessing steps are applied consistently to both **MIMIC-IV** and **eICU** datasets to ensure aligned feature representations across hospitals and datasets.

### 2- Hospital Selection

For the next step, we select the nine most populated hospitals from the eICU dataset using a minimum threshold of **200 patients per hospital**.

This step allows us to simulate a multi-center environment, enable federated learning and ensure sufficient sample size per hospital.

At this stage, we obtain:

* 1 MIMIC dataset
* 9 eICU hospital datasets

_<mark style="color:$success;">**Total : 10 datasets.**</mark>_

### 3- Learning/Holdout Splits

Each dataset is split into learning and holdout subsets.

Due to scalability constraints, we divided our datasets as follows :

* <mark style="color:$info;">**MIMIC-IV**</mark><mark style="color:$info;">:</mark> <mark style="color:$info;"></mark><mark style="color:$info;">**95% learning / 5% holdout**</mark>
* <mark style="color:$info;">**eICU hospitals**</mark><mark style="color:$info;">:</mark> <mark style="color:$info;"></mark><mark style="color:$info;">**80% learning / 20% holdout**</mark>

This strategy allowed us to obtain comparable holdout sizes and consistent evaluation results.

This step results in:

* <mark style="color:$info;">**10 learning datasets (1 MIMIC + 9 eICU learning datasets)**</mark>
* <mark style="color:$info;">**10 holdout datasets (1 MIMIC + 9 eICU holdout datasets)**</mark>

_<mark style="color:$success;">**Total :**</mark>_ _<mark style="color:$success;">**20 datasets.**</mark>_

This operation can also be performed directly within the _MEDomics Input Module_ ([Holdout Set Creation Tool](https://medomicslab.gitbook.io/medomics-docs/tutorials/design/input-module#holdout-set-creation-tool)).

### 4- Independent Imputation

Missing values are handled using **median imputation**, applied independently to each of the 20 dataset files mentioned below to prevent data leakage.

This step can also be performed using the _MEDomics Input Module_ ([Simple Cleaning Tool](https://medomicslab.gitbook.io/medomics-docs/tutorials/design/input-module#simple-cleaning-tool)).

### 5- Aggregated eICU Holdout

Finally, the holdout datasets from the 9 eICU hospitals are combined into a single aggregated eICU holdout dataset, used for global external evaluation.

_<mark style="color:$success;">**Total :**</mark>_ _<mark style="color:$success;">**21 datasets.**</mark>_

{% hint style="info" %}
You can find the 21 files [here](https://usherbrooke-my.sharepoint.com/my?id=%2Fpersonal%2Fkalm7073%5Fusherbrooke%5Fca%2FDocuments%2Fimputed).
{% endhint %}

#### <mark style="color:$warning;">Why These Datasets Are Needed</mark>

These datasets enable comparison between **centralized** and **federated learning** strategies (explored in later steps) :

Learning :&#x20;

* **MIMIC learning** → centralized training of an MLP baseline model
* **eICU learning (9 hospitals)** → federated learning (MEDfl) using our trained MLP model

Evaluation :&#x20;

* **MIMIC holdout** → internal evaluation
* **eICU holdouts** → hospital-specific evaluation
* **Aggregated eICU holdout** → global external evaluation

This concludes the processing steps of this PoC. In the next one, we will dive deeper into our centralized learning section.
