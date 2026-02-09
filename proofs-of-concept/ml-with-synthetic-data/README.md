---
description: >-
  This proof of concept demonstrates the ability of the MEDomics platform to
  support the full end-to-end machine learning workflow in a healthcare context,
  using synthetic data.
icon: wpforms
---

# ML with Synthetic Data

{% hint style="success" %}
The data used in this demo is publicly available, and we recommend that you follow the steps below to obtain similar results.
{% endhint %}

### About the Dataset

The synthetic dataset used in this proof of concept replicates the structure of real hospital admission data while ensuring complete privacy. It simulates realistic patient profiles, admission characteristics, comorbidities, and diagnostic patterns, offering a reliable environment for developing and validating predictive models. It is accessible in Zenodo under this [link](https://zenodo.org/records/12954673).

{% hint style="info" %}
The dataset is accessible on Zenodo at the following link: 👉 [Access the dataset on Zenodo](https://zenodo.org/records/12954673).
{% endhint %}

### Goal

This demo illustrates how the _MEDomics_ platform can be used to explore a fully synthetic hospital dataset from data exploration to predictive modeling. We use key MEDomics modules to build an end-to-end predictive pipeline. The goal is to evaluate model performance in this setting while showcasing MEDomics’ ability to handle large-scale clinical data and produce explainable and comparable results. This workflow replicates the reference study available [here](https://github.com/MEDomicsLab/POYM). The end goal of the study is to predict one-year mortality using demographics, admission characteristics, comorbidity and admission diagnoses using binary classification.&#x20;

### Steps

Here are the steps followed in this demo:

{% stepper %}
{% step %}
### [Code Editor & MEDomics Terminal](https://app.gitbook.com/o/0MYkcFwIjU9gRWqGMkr5/s/UO0RN9PzFLqAgLEwwaSn/~/edit/~/changes/218/proofs-of-concept/ml-with-synthetic-data/code-editor-and-medomics-terminal)&#x20;

We will give you a code snippet to extract the "any\_visit\_homr.csv", which will be the data used in the next steps. This specific file contains random visits from every patient in our initial data. This tool can be used to change the random seed.
{% endstep %}

{% step %}
### [Input Module](../the-paris-demo/input-module.md)

This module is used to create the AdmDemo and AdmDemoDx tags to form 2 categories used in prediction, and to partition data into training and holdout sets.
{% endstep %}

{% step %}
### [Learning Module](../the-paris-demo/learning-module.md)

The Learning Module represents the main step of the demo. It will be used to replicate the pipeline from the original study to form a model, train it and save a final model.
{% endstep %}

{% step %}
### [Evaluation Module](../the-paris-demo/evaluation-module.md)

In this module, we will use the saved machine learning model to make predictions on the holdout set and try to interpret and explain the model's choices.
{% endstep %}

{% step %}
### [Application Module](../the-paris-demo/#application-module)

This final step is similar to model deployment, where we will use the saved model from the Learning Module to generate predictions on an unseen patient.
{% endstep %}
{% endstepper %}
