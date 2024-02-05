---
description: Feb 12 – Feb 26 | Prepare ML tables
---

# Step 3: Prepare ML tables

<figure><img src="../.gitbook/assets/MEDomicsLab-TestingPhase-11.png" alt=""><figcaption><p>Step 3 - Prepare ML tables</p></figcaption></figure>

{% hint style="info" %}
If you completed [_Step 2 - Extract Data_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-2), you have data ready for _Step 3 - Prepare ML tables_.&#x20;

However, before proceeding to _Step 3 - Prepare ML tables,_ we recommend that you replace your own output data from [_Step 2 - Extract Data_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-2) (the _extracted\_features_ folder) with the data that we prepared for you (_MEDomicsLab\_TestingPhase\_Step3.zip_). This will ensure consistency of results across all participants of the Testing Phase.&#x20;

An invitation to access the _MEDomicsLab\_TestingPhase\_Step3.zip_ data was sent by email.&#x20;
{% endhint %}

The current _Step 3 - Prepare ML tables_ step is divided into five parts, and involves preparing Machine Learning tables using the extracted features from [_Step 2 - Extract Data_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-2) of the Testing Phase as follows:

1. **Reduce Extracted Features:** Use the [_Input Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/input-module) to reduce the large CSV files obtained from the previous step via Principal Component Analysis (PCA) and Spearman correlation.
2. **Merge All Data:** Combine the reduced extracted features with demographic embeddings into a master CSV table using the [_MEDprofiles package_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/input-module/medprofiles). Additionally, create _MEDprofiles_ with the master table.
3. **Visualize Data:** Use the _MEDprofiles_ figure to visualize the data.
4. **Define Static Time Points:** Use the _MEDprofiles_ figure to set static time points and export the data as static CSV tables.&#x20;
5. **Create **_**Learning**_** and **_**Holdout**_** Sets:** Use the [_Input Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/input-module) to generate Learning and Holdout sets.

{% hint style="info" %}
The goal of defining static time points is to simulate a longitudinal CDSS (Clinical Decision Support System) scenario using data aggregated over time. In [_Step 5 - Create Model_](https://medomics-udes.gitbook.io/medomicslab-docs/test-with-mimic/step-5) of the Testing Phase, we will attempt to identify the point in time where we reach sufficient predictive power (the point in time when, in real-life, we could potentially intervene).
{% endhint %}

## Recommendations

Before proceeding with _Step 3 - Prepare ML tables_ of the MEDomicsLab Testing Phase, we recommend consulting the documentation of the [_Input Module_](https://medomics-udes.gitbook.io/medomicslab-docs/tutorials/design/input-module).

{% content-ref url="../tutorials/design/input-module/" %}
[input-module](../tutorials/design/input-module/)
{% endcontent-ref %}

## Instructions for Step 3 - Prepare ML tables

{% embed url="https://youtu.be/lVvszz01cDk" %}

{% hint style="info" %}
**Reminder**: Make sure to save your datasets when updating column names by pressing the 'Save' button icon (an example is shown at 16:08 in the video above).&#x20;

If you do not press the 'Save' button icon after modifying a CSV file in the app, the changes will not be applied in your workspace.
{% endhint %}

**Content**

Intro [0:00](https://www.youtube.com/watch?v=lVvszz01cDk\&t=0s)

Reduce extracted features [0:50](https://www.youtube.com/watch?v=lVvszz01cDk\&t=50s)

Merge all our data [8:24](https://www.youtube.com/watch?v=lVvszz01cDk\&t=504s)

Visualize _MEDprofiles_ [10:52](https://www.youtube.com/watch?v=lVvszz01cDk\&t=652s)&#x20;

Define static time points [12:01](https://www.youtube.com/watch?v=lVvszz01cDk\&t=721s)&#x20;

Create learning and holdout sets [14:13](https://www.youtube.com/watch?v=lVvszz01cDk\&t=853s)

***

{% hint style="info" %}
We acknowledge that using Spearman correlation with the target variable to massively reduce the feature set dimension **on the whole dataset** is not part of best practices in machine learning.&#x20;

This Spearman correlation process, if needed as a feature set reduction method, should normally be performed "on-the-fly" on the training sets of the _Learning set_ (and ideally, the PCA process too).&#x20;

Here, we decided to use Spearman correlation on the whole dataset during the _Reduce extracted features_ process to get around some difficulties we have in handling large feature sets in downstream processes.&#x20;

However, please note that we are actively working on enhancing the scalability of our application to eliminate the need of applying Spearman correlation on the whole dataset in the future.&#x20;
{% endhint %}
