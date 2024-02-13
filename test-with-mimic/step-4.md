---
description: Feb 26 – Mar 11 | Explore Data
---

# Step 4: Explore data

<figure><img src="../.gitbook/assets/MEDomicsLab-TestingPhase-12.png" alt=""><figcaption><p>Step 4 - Explore Data</p></figcaption></figure>

{% hint style="info" %}
If you completed [_Step 3 - Prepare ML tables_](step-3.md), you have data ready for _Step 4 - Explore Data_.&#x20;

However, before proceeding to _Step 4 - Explore Data,_ we recommend that you replace your own output data from [_Step 3 - Prepare ML tables_](step-3.md) (the _timePoints_ folder) with the data that we prepared for you (_MEDomicsLab\_TestingPhase\_Step4.zip_). This will ensure consistency of results across all participants of the Testing Phase.&#x20;

An invitation to access the _MEDomicsLab\_TestingPhase\_Step4.zip_ data was sent by email.&#x20;
{% endhint %}

{% hint style="info" %}
The _MEDomicsLab\_TestingPhase\_Step4.zip_ also contains a _new\_demographic\_embeddings_ CSV file that you will need during this _Step 4 - Explore Data_. The reason we provided you a new file is explained in the part _Set the demographics in T1 only_ ([5:41](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=341s)) of the video.
{% endhint %}

The current _Step 4 - Explore Data_ step is divided into seven parts, and involves exploring the learning set we obtained from [_Step 3 - Prepare ML tables_](step-3.md) of the Testing Phase as follows:

1. **Analyze the learning set using **_**YData profiling**_**:** Use the _YData profiling_ tool from [_Exploratory Module_](../tutorials/design/exploratory-module.md) to explore your learning set and note the missing values percentages for each class for each time point.
2. **Set demographic embeddings in T1 only:** Depending on the analysis we made at point 1. you will remove the demographics embeddings from all the time points CSV files (including learning and holdout sets) and include all the demographic data into T1 only using the _new\_demographic\_embeddings_ CSV file. This step will be performed in the [_Input Module_](../tutorials/design/input-module/).
3. **Remove chart events from T1:** Depending on the analysis we made at point 1. you will remove the chart events from the T1 datasets (learning and holdout) using the [_Input Module_](../tutorials/design/input-module/).
4. **Transform procedure events:** Depending on the analysis we made at point 1. you will transform the procedure events columns in all the time points datasets (learning and holdout) using the  [_Input Module_](../tutorials/design/input-module/).
5. **Analyze the learning set using  **_**D-Tale**_**:** Use the _D-Tale_ tool from [_Exploratory Module_](../tutorials/design/exploratory-module.md) to explore your learning set and observe the correlation matrices for each time points.
6. **Analyze the learning set using  **_**SweetViz**_**:** Use the _SweetViz_ tool from [_Exploratory Module_](../tutorials/design/exploratory-module.md) to explore your learning set and note the sets of columns having a high correlation rate between them depending on the observation we made with _D-Tale_.
7. **Remove high correlated columns from the time points datasets:** Use the [_Input Module_](../tutorials/design/input-module/) to remove the high correlated columns we observed at point 6. from the time points datasets (learning and holdout).

{% hint style="info" %}
We encourage you to not simply follow the video and use the [_Exploratory Module_](../tutorials/design/exploratory-module.md) to explore the learning set by yourself. This analysis will be useful in Step 8 - Challenge :wink:&#x20;
{% endhint %}

## Recommendations

Before proceeding with _Step 4 - Explore Data_ of the MEDomicsLab Testing Phase, we recommend consulting the documentation of the [_Input Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/input-module) _and_ [_Exploratory Module_](../tutorials/design/exploratory-module.md).

{% content-ref url="../tutorials/design/input-module/" %}
[input-module](../tutorials/design/input-module/)
{% endcontent-ref %}

{% content-ref url="../tutorials/design/exploratory-module.md" %}
[exploratory-module.md](../tutorials/design/exploratory-module.md)
{% endcontent-ref %}

## Instructions for Step 4 - Explore Data

{% embed url="https://youtu.be/EbZ3xhG16pg" %}

**Content**

Intro [0:00](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=0s)

YData-profiling [0:54](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=54s)

Set the demographics in T1 only [5:41](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=341s)

Remove chart events from T1 [12:04](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=724s)

Transform procedure events [14:00](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=840s)

D-Tale [18:50](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=1130s)

SweetViz [23:24](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=1404s)

Remove Highly Correlated Columns [28:26](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=1706s)
