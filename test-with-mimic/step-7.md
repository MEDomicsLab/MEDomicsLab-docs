---
description: Apr 8 – Apr 22 | Evaluate & Apply Model
---

# Step 7: Evaluate & Apply Model

<figure><img src="../.gitbook/assets/MicrosoftTeams-image (6).png" alt=""><figcaption><p>Step 7 - Evaluate &#x26; Apply Model</p></figcaption></figure>

{% hint style="info" %}
Before proceeding to _Step 7 - Evaluate & Apply Model_, you will need to download the models folder (_MEDomicsLab\_TestingPhase\_Step7.zip_) into your _EXPERIMENTS_ folder. This folder contains the models we prepared for you. One of the models corresponds to the model you created during [_Step 6 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-6). However, for consistency across all participants of the Testing Phase, we recommend using the model we provided specifically for _Step 7 - Evaluate & Apply Model_.

Additionally, for this step, you will also need the data we sent you for [_Step 6 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-6) (_MEDomicsLab\_TestingPhase\_Step6.zip_), which contains the holdout patient set we will use to evaluate our models.

An invitation to access the _MEDomicsLab\_TestingPhase\_Step7.zip_ data has been sent to you via email.
{% endhint %}

In this current _Step 7 - Evaluate & Apply Model_, we will explore the functionalities of the [_Evaluation Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/evaluation-module) by evaluating two machine learning models on our holdout set. As the models were created using only _Time point 1_ and _Time point 2_ from the learning set (see [_Step 6 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-6) for more details), we are going to evaluate them on _Time point 1_ and _Time point 2_ from the holdout set.

Additionally, we will explore the functionalities of the [_Application Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/deployment/application-module) by applying one of the models to a single patient from the holdout set.

**Model 1: ExtraTrees Classifier**&#x20;

Documentation related to this model is available [here](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesClassifier.html). In our experiment, we kept the model's default values.&#x20;

This model is the one we obtained at the end of [_Step 6 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-6). It is trained on _Time point 1_ and _Time point 2_ from our learning set, using the following columns (T1 and T2 suffix refers to T1 and T2 datasets):

* tslab\_|\_attr\_MCHC\_\_maximum\_T1
* nradiology\_|\_attr4\_T1
* nradiology\_|\_attr6\_T1
* image\_|\_attr5(3)\_T1
* image\_|\_attr7(3)\_T1
* demographics\_|\_anchor\_age\_T1
* nradiology\_|\_attr4\_T2
* nradiology\_|\_attr6\_T2
* tslab\_|\_attr\_Platelet\_Count\_\_mean\_T2
* tslab\_|\_attr\_MCHC\_\_maximum\_T2
* tslab\_|\_attr\_MCH\_\_maximum\_T2
* image\_|\_attr5(3)\_T2
* image\_|\_attr7(3)\_T2

**Model 2: Random Forest Classifier**&#x20;

Documentation related to this model is available [here](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html). In our experiment, we kept the model's default values.&#x20;

We created this model specifically for this step. Like the previous model, it was trained on _Time point 1_ and _Time point 2_ from the learning set, using the same columns.

**Apply Model**&#x20;

This section involves selecting a model and applying it to a new patient. You will need to enter the patient's required information, based on the columns the model was trained on, and observe the prediction the model makes for this new patient.

{% hint style="info" %}
Please note that the [_Evaluation Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/evaluation-module) dashboard is a basic implementation of the [_ExplainerDashboard_ Python library](https://explainerdashboard.readthedocs.io/en/latest/index.html). Additionally, if you are seeking information about the dashboard elements, you may find it in the [_ExplainerDashboard_ documentation](https://explainerdashboard.readthedocs.io/en/latest/index.html).&#x20;

Also, if you want to fully understand how _ExplainerDashboard_ works in the background, it is an open-source library, and the code is available on [GitHub](https://github.com/oegedijk/explainerdashboard/tree/master).
{% endhint %}

## Recommendations

Before proceeding with _Step 7 - Evaluate & Apply Mode_l of the MEDomicsLab Testing Phase, we recommend consulting the documentation of the [_Evaluation Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/evaluation-module) and the [_Application Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/deployment/application-module).

{% content-ref url="../tutorials/development/evaluation-module.md" %}
[evaluation-module.md](../tutorials/development/evaluation-module.md)
{% endcontent-ref %}

{% content-ref url="../tutorials/deployment/application-module.md" %}
[application-module.md](../tutorials/deployment/application-module.md)
{% endcontent-ref %}

## Instructions for Step 7 - Evaluate & Apply Model

{% embed url="https://youtu.be/klxuMgQWI00" %}

**Content**

Intro [0:00](https://www.youtube.com/watch?v=klxuMgQWI00\&t=0s)

Evaluate 1st model [2:25](https://www.youtube.com/watch?v=klxuMgQWI00\&t=145s)

Evaluate 2nd model [14:59](https://www.youtube.com/watch?v=klxuMgQWI00\&t=899s)

Apply model [18:19](https://www.youtube.com/watch?v=klxuMgQWI00\&t=1099s)
