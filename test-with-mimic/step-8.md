---
description: Apr 22 – May 13 | Challenge
---

# Step 8: Challenge

<figure><img src="../.gitbook/assets/MicrosoftTeams-image (7).png" alt=""><figcaption><p>Step 8 - Challenge</p></figcaption></figure>

{% hint style="info" %}
This step will require you to download the new learning set that we sent you (_MEDomicsLab\_TestingPhase\_Step8.zip_). This set comprises two datasets, combining the learning and holdout sets obtained in[ _Step 4 - Explore Data_](step-4.md) at _Time Point 1_ and _Time Point 2_.

To avoid confusion among all the datasets from the beginning of the Testing Phase, we recommend creating a new workspace for this step containing only the new learning set.

An invitation to access the _MEDomicsLab\_TestingPhase\_Step8.zip_ data has been sent via email.
{% endhint %}

Welcome to the final step of the MEDomicsLab Testing Phase! We appreciate your engagement throughout this journey.

In _Step 8 - Challenge_, you will leverage the knowledge you have gained from the MEDomicsLab platform in the preceding steps of the Testing Phase. You are the master here :clap:!

The objective here is that participants design their own model via the use of the [_Machine Learning (ML) Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module)_._ These models will be evaluated by the MEDomicsLab team using a fresh, private holdout set from the [MIMIC](https://mimic.mit.edu/) database.&#x20;

{% hint style="info" %}
Considering the insights we have gained during the Testing Phase, we have now updated the rules for this step. In contrast to what we initially planned, there will be a single challenge that involves manipulations in the [_Machine Learning (ML) Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module) only.
{% endhint %}

{% hint style="info" %}
We are continuously working on enhancing the MEDomicsLab platform, and we would like to inform you that there may still be some missing options and tooltips in the  [_Machine Learning (ML) Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module), which we intend to implement in the future.
{% endhint %}

## Recommendations

Before proceeding with _Step 8 - Challenge_ of the MEDomicsLab Testing Phase, we recommend revisiting the documentation related to [_Step 6 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-6).

{% content-ref url="step-6.md" %}
[step-6.md](step-6.md)
{% endcontent-ref %}

## Instructions for Step 8 - Challenge

* Download the new learning set provided in _MEDomicsLab\_TestingPhase\_Step8.zip_.
* Create a model similarly to the one we created in [_Step 6 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-6) using the [_Machine Learning (ML) Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module). Follow these guidelines for creating your best possible model:
  * Train, optimize, and test models.
  * Compare different data combinations.
  * Choose a learning hypothesis and create a final model.
* Once you have trained your best model, send it to [sarah.denis@usherbrooke.ca](mailto:sarah.denis@usherbrooke.ca) with "Step 8 - Challenge | Submission" as the Subject of your email. You are allowed to send multiple submissions, but please note that we will only evaluate your latest submission.&#x20;
  * If you wish, you can let us know in the email the name that we should use for the public ranking of your submission (e.g. _MLrocks_ :smile:). If not specified, we will use your full name.&#x20;

{% hint style="warning" %}
For this _ML Challenge_, most of your work will therefore be done inside the [_Machine Learning (ML) Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module).  However, you are also welcome to use the other capabilities of the MEDomicsLab platform. For example, you may want to use the [_Exploratory Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/exploratory-module) to continue to gain useful insights about the dataset prior to the learning step.&#x20;

However, to facilitate the Evaluation process of the models submitted by the participants, **we please ask the following:**

* _**Only use**_ the data we provided in the  _MEDomicsLab\_TestingPhase\_Step8.zip file._
  * Therefore, you should not be able to use the _Extraction Module_ or the _MEDprofiles_ package_._&#x20;
* _**Do not change**_ column names in the data we provided (this includes the use of the Groupping/Tagging tool).
* _**Do not merge**_ the time point CSV files together.&#x20;
* _**Dot not use**_ the "Transform Columns tool".&#x20;
* _**Do not use**_ the "PCA" utility of the "Feature Reduction tool".
* If you use the "Spearman" utility of the "Feature Reduction tool", **make sure to keep the **_**subject\_id**_** and **_**target**_** columns in your dataset** by enabling the "Merge unselected columns in the result dataset" and "Keep target in dataset" options.
  * Note that you new dataset will be placed in the _reduced\_features_ folder and that you will have to move it in your _learning_ folder to retrieve it in the [_Learning Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module).

If these instructions are not followed, we will not be able to evaluate your submission, and it will unfortunately be discarded.&#x20;

Also, note that to create a model in the [_Learning Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/development/learning-module), your CSV files must be placed under a "learning" folder and have the prefix "TX\_" (e.g., _T1\_new\_learning_) as in the data we provided you.
{% endhint %}

{% embed url="https://youtu.be/AMiNfv1J67g?si=oE8czBaEsADO-Yyg" %}

**Content**

Intro [0:00](https://www.youtube.com/watch?v=AMiNfv1J67g\&t=0s)

Rules [0:38](https://www.youtube.com/watch?v=AMiNfv1J67g\&t=38s)

Dealing with Server Errors [4:03](https://www.youtube.com/watch?v=AMiNfv1J67g\&t=243s)

Documentation [5:08](https://www.youtube.com/watch?v=AMiNfv1J67g\&t=308s)

The Optimize node [8:58](https://www.youtube.com/watch?v=AMiNfv1J67g\&t=538s)

General Advice [11:05](https://www.youtube.com/watch?v=AMiNfv1J67g\&t=665s)

***

{% hint style="info" %}
After the conclusion of the Testing Phase on May 13, we will evaluate the performance of the models submitted by all participants and establish a ranking through an evaluation using our private holdout set.&#x20;

Following this, we will make the ranking public and reveal the winners of both the _ML Challenge_ :tada: and the _Bug Finder Challenge_ :smile: at the **wrap-up meeting scheduled for May 17**. An invitation to this meeting will be sent out soon.
{% endhint %}
