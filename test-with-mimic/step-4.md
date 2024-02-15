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
The _MEDomicsLab\_TestingPhase\_Step4.zip_ also includes a _new\_demographic\_embeddings_ CSV file that you'll need for this _Step 4 - Explore Data_. The rationale behind providing this new file is explained in the "Set the demographics in T1 only" section ([5:41](https://www.youtube.com/watch?v=EbZ3xhG16pg\&t=341s)) of the video.
{% endhint %}

The current _Step 4 - Explore Data_ step is divided into seven parts, and involves exploring the learning set we obtained from [_Step 3 - Prepare ML tables_](step-3.md) of the Testing Phase as follows:

1. **Analyze the learning set using **_**YData profiling**_**:** Employ the YData profiling tool from the [_Exploratory Module_](../tutorials/design/exploratory-module.md) to delve into your learning set. Record the percentages of missing values for each class across all time points.
2. **Set demographic embeddings in T1 only:** Based on the insights from task 1, eliminate demographic embeddings from all time point CSV files, including learning and holdout sets. Consolidate all demographic data into T1 using the _new\_demographic\_embeddings_ CSV file. Conduct this operation in the [_Input Module_](../tutorials/design/input-module/).
3. **Remove chart events from T1:** Referencing the analysis in task 1, eliminate chart events from the T1 datasets (both learning and holdout) using the [_Input Module_](../tutorials/design/input-module/).&#x20;
4. **Transform procedure events:** Building on the findings from task 1, transform the procedure events columns in all time point datasets (learning and holdout) using the [_Input Module_](../tutorials/design/input-module/).
5. **Analyze the learning set using  **_**D-Tale**_**:** Leverage the _D-Tale_ tool from the [_Exploratory Module_](../tutorials/design/exploratory-module.md) to scrutinize your learning set. Explore the correlation matrices for each time point.
6. **Analyze the learning set using  **_**SweetViz**_**:** Utilize the _SweetViz_ tool from the [_Exploratory Module_](../tutorials/design/exploratory-module.md) to study your learning set. Identify sets of columns exhibiting a high correlation rate, considering the observations made with _D-Tale_.
7. **Remove high correlated columns from the time points datasets:** In the [_Input Module_](../tutorials/design/input-module/), eliminate the columns identified as having high correlation rates from the time point datasets (both learning and holdout), aligning with the insights gained in task 6.

{% hint style="info" %}
Please note that the CSV files for the time points obtained from [_Step 3 - Prepare ML tables_](step-3.md) are already tagged. This is done by the [_MEDprofiles Module_](../tutorials/design/input-module/medprofiles.md) when exporting the data as time points.
{% endhint %}

{% hint style="info" %}
We encourage you not only to follow the video but also to independently utilize the [_Exploratory Module_](../tutorials/design/exploratory-module.md) for exploring the learning set. This self-directed analysis will prove valuable in _Step 8 - Challenge_. :wink:&#x20;
{% endhint %}

## Recommendations

Before proceeding with _Step 4 - Explore Data_ of the MEDomicsLab Testing Phase, we recommend consulting the documentation of the [_Input Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/input-module) _and_ [_Exploratory Module_](../tutorials/design/exploratory-module.md).

{% content-ref url="../tutorials/design/input-module/" %}
[input-module](../tutorials/design/input-module/)
{% endcontent-ref %}

{% content-ref url="../tutorials/design/exploratory-module.md" %}
[exploratory-module.md](../tutorials/design/exploratory-module.md)
{% endcontent-ref %}

{% hint style="warning" %}
Please consider the warnings we've mentioned on the [_Input Module_](../tutorials/design/input-module/) page: we are continuously working on enhancing the MEDomicsLab platform.
{% endhint %}

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
