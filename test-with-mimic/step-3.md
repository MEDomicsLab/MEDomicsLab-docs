---
description: Feb 12 – Feb 26 | Prepare ML tables
---

# Step 3: Prepare ML tables

<figure><img src="../.gitbook/assets/MEDomicsLab-TestingPhase-11.png" alt=""><figcaption><p>Step 3 - Prepare ML tables</p></figcaption></figure>

{% hint style="info" %}
If you've completed Step 2, you likely have data for Step 3. However, we recommend replacing it with the data we've sent you to ensure consistency and obtain uniform results across all participants of the Testing Phase.
{% endhint %}

This step, divided into five parts, involves preparing Machine Learning tables using the extracted features from Step 2 of the Testing Phase. The parts are as follows:

1. **Reduce Extracted Features:** Utilize the _Input module_ to reduce the large CSV files obtained from the previous step. Apply Principal Component Analysis and Spearman correlation to enhance data visualization and manipulation.
2. **Merge All Data:** Combine the reduced extracted features with demographic embeddings into a master CSV table using the _MEDprofiles module_. Additionally, create _MEDprofiles_ with the master table.
3. **Visualize Data:** Use the _MEDprofiles_ figure to visualize the data.
4. **Define Static Time Points:** Use the _MEDprofiles_ figure to set static time points and export the data as static CSV tables. The goal of this step is to formulate a longitudinal CDSS (Clinical Decision Support System) scenario and determine the point in time when we have adequate predictive power to potentially intervene.
5. **Create Learning and Holdout Sets:** Use the _Input module_ to generate Learning and Holdout sets.

## Recommendations

Before proceeding with Step 3 of the MEDomicsLab Testing Phase, we recommend consulting the documentation for the _Input Module_.

{% content-ref url="../tutorials/design/input-module/" %}
[input-module](../tutorials/design/input-module/)
{% endcontent-ref %}

## Instructions for Step 3 - Prepare ML tables

{% embed url="https://youtu.be/lVvszz01cDk" %}

{% hint style="info" %}
Reminder: Make sure to save your datasets when updating column names. If you don't press the 'save' button after modifying a CSV file in the app, your changes won't be applied (this will be helpful during the last part of the video).
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
We understand that utilizing Spearman correlation with the target variable is not the ideal approach for machine learning. However, we are actively working on enhancing the scalability of our application to eliminate the need for such practices.
{% endhint %}
