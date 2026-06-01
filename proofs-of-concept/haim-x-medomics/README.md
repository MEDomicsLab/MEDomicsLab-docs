---
description: >-
  This proof of concept demonstrates the ability of the MEDomics platform to
  support the full end-to-end machine learning workflow in a healthcare context,
  using synthetic data.
icon: wpforms
---

# HAIM x MEDomics

{% hint style="success" %}
The data used in this demonstration is publicly available, and we recommend that you follow the steps below to obtain similar results.
{% endhint %}

### About the Dataset

The synthetic dataset used in this proof of concept replicates the structure of real hospital admission data while ensuring complete privacy. It simulates realistic patient profiles, admission characteristics, comorbidities, and diagnostic patterns, offering a reliable environment for developing and validating predictive models.

{% hint style="info" %}
The dataset is accessible on Zenodo at the following link: 👉 [Access the dataset on Zenodo](https://zenodo.org/records/12954673).
{% endhint %}

### Goal

This demonstration illustrates how the MEDomics platform can be used to explore a fully synthetic hospital dataset, from data exploration to predictive modeling. We leverage key MEDomics modules to build an end-to-end predictive pipeline. The objective is to evaluate model performance in this setting while showcasing MEDomics’ ability to handle large-scale clinical data and generate explainable, reproducible, and comparable results.

This proof of concept is based on the study [_“_&#x4C;everaging patients’ longitudinal data to improve the Hospital One-year Mortality Ris&#x6B;_”_](https://link.springer.com/article/10.1007/s13755-024-00332-4), conducted by Hakima Laribi, a member of our laboratory, in collaboration with clinical and academic partners. The original work introduces both a predictive modeling framework and a publicly available synthetic dataset designed to enable privacy-preserving and reproducible research in healthcare AI.

In that study, two modeling approaches were evaluated: a baseline **Random Forest** model that predicts one-year mortality risk at hospital admission, and a longitudinal ensemble model that incorporates patients’ hospitalization history over time. The comparison between these two approaches demonstrated the added value of leveraging longitudinal information for mortality prediction.

In the present proof of concept, we focus exclusively on implementing and evaluating the **Random Forest baseline** using the synthetic dataset released with the original study. This allows us to establish a clear reference performance while working within a fully accessible and privacy-preserving framework.

### Steps

Here are the steps followed in this demonstration:

{% stepper %}
{% step %}
### [Code Editor & MEDomics Terminal](https://medomicslab.gitbook.io/medomics-docs/proofs-of-concept/ml-with-synthetic-data/code-editor-and-medomics-terminal)&#x20;

We will give you a code snippet to extract the "any\_visit\_homr\_10pct.csv", which will be the data used in the next steps. This specific file contains random visits from every patient in our initial data. This tool can be used to change the random seed.
{% endstep %}

{% step %}
### [Input Module](https://medomicslab.gitbook.io/medomics-docs/proofs-of-concept/ml-with-synthetic-data/input-module)

This module is used to create the AdmDemo and AdmDemoDx tags to form 2 categories used in prediction, and to partition data into training and holdout sets.
{% endstep %}

{% step %}
### [Learning Module](../the-paris-demo/learning-module.md)

The Learning Module represents the main step of the demonstration. It will be used to replicate the pipeline from the original study to form a model, train it and save a final model.
{% endstep %}

{% step %}
### [Evaluation Module](https://medomicslab.gitbook.io/medomics-docs/proofs-of-concept/ml-with-synthetic-data/evaluation-module)

In this module, we will use the saved machine learning model to make predictions on the holdout set and try to interpret and explain the model's choices.
{% endstep %}

{% step %}
### [Application Module](https://medomicslab.gitbook.io/medomics-docs/proofs-of-concept/ml-with-synthetic-data/application-module)

This final step is similar to model deployment, where we will use the saved model from the Learning Module to generate predictions on an unseen patient.
{% endstep %}
{% endstepper %}
