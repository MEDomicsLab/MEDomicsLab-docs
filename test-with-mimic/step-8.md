---
description: Apr 22 – May 13 | Challenge
---

# Step 8: Challenge

{% hint style="info" %}
This step will require you to download the new learning set that we sent you (_MEDomicsLab\_TestingPhase\_Step8.zip_). This set comprises four datasets (one for each time point), combining the learning and holdout sets obtained in [_Step 3 - Prepare ML tables_](step-3.md). Similar to [_Step 4 - Explore Data_](step-4.md), we've merged the demographics embeddings only in the T1 dataset.

An invitation to access the _MEDomicsLab\_TestingPhase\_Step8.zip_ data has been sent via email.
{% endhint %}

Welcome to the final step of the MEDomicsLab Testing Phase! We appreciate your engagement throughout this journey.

In _Step 8 - Challenge_, you'll leverage the knowledge you've gained from the MEDomicsLab platform in the preceding steps of the Testing Phase. Since the tasks to be accomplished depend on your choices, there isn't an instructional video for this step.

The objective here is to optimize the use of the MEDomicsLab platform through a new experiment, which will be evaluated using a fresh, private holdout set from the [MIMIC](https://mimic.mit.edu/) database. Considering our growing familiarity with the MEDomicsLab platform and the insights gained during the Testing Phase, we've updated the rules for this step. There will be a singular challenge that involves manipulations in both the [_Design Layer_](../tutorials/design/) and the [_Development Layer_](../tutorials/development/).

## Recommendations

Before proceeding with _Step 8 - Challenge_ of the MEDomicsLab Testing Phase, we recommend revisiting the pages related to [_Step 4 - Explore Data_](step-4.md) and [_Step 5 - Create Model_](step-5.md).

{% content-ref url="step-4.md" %}
[step-4.md](step-4.md)
{% endcontent-ref %}

{% content-ref url="step-5.md" %}
[step-5.md](step-5.md)
{% endcontent-ref %}

## Instructions for Step 8 - Challenge

* Download the new learning set provided in _MEDomicsLab\_TestingPhase\_Step8.zip_.
*   Explore the new learning set using the [_Exploratory module_](../tutorials/design/exploratory-module.md), as done in [_Step 4 - Explore Data_](step-4.md).

    Based on your analysis, manipulate the learning set using the _Delete Columns tool_ and/or the _Transform Columns tool_ **only** from the [_Input Module_](../tutorials/design/input-module/). Avoid any other manipulations on the learning set for this challenge. Document the operations performed on the learning set for replication on our holdout set during the evaluation of your model.
* Create a model following the instructions from [_Step 5 - Create Model_](step-5.md) in the [_Learning Module_](../tutorials/development/learning-module.md). Follow these guidelines for creating the best model:
  * Train, optimize, and test models.
  * Compare different data combinations at different time points.
  * Choose a learning hypothesis and create a final model.
* Once you believe you have the best model for the experiment, submit your model as you did at the end of [_Step 5 - Create Model_](step-5.md). Include explanatory notes about the manipulations made on the learning set in the Design Layer.

{% hint style="info" %}
It is crucial that you document every manipulation made on the learning set in the [_Design Layer_](../tutorials/design/). This documentation is necessary for us to replicate the manipulations on our holdout set during the evaluation of your model. Without this information, we won't be able to assess your model and include it in our Challenge ranking.
{% endhint %}

{% hint style="info" %}
After the conclusion of the Testing Phase on May 13, we will assess the models submitted by all participants and establish a ranking through an evaluation using our private holdout set. Following this, we will communicate the ranking and announce the winner of this Challenge.

Additionally, we will reveal the winner of another challenge in this Testing Phase: the individual who discovered the most bugs in our application!
{% endhint %}
