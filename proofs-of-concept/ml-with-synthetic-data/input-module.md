---
description: >-
  This page documents the Input Module step of the demo, where we will perform
  two processing steps on our new "homr_any_visit_10pct.csv" file before model
  training in the Learning Module.
icon: '2'
---

# Input Module

The [Input Module](../../tutorials/design/input-module/) provides multiple data processing key tools needed to fulfill various tasks within the MEDomics platform. In this proof of concept, we will use two tools: the _Column Tagging Tools_ and the _Holdout Set Creation Tools_.

Before these two steps, we have to delete a column from our dataset file named "CSO". This column is not used in the original study and therefore we don't need to keep it. Double click on the `homr_any_visit_10pct.csv` file in your workspace to open it in the _MEDomics_ editor. Then, click on the bin above the "CSO" column to delete it.

<figure><img src="../../.gitbook/assets/image 16.png" alt=""><figcaption><p>Data in <em>MEDomics</em> editor</p></figcaption></figure>

#### Column Tagging&#x20;

This [tool](https://medomicslab.gitbook.io/medomics-docs/tutorials/design/input-module#feature-or-column-tagging-tools) is a core component of the _MEDomics_ platform, as it enables the use of the _MEDomics Standard_ data format.

In _MEDomics_, a **tag** represents a _group of columns_. Each tag corresponds to a coherent subset of features sharing a common meaning or role (e.g., administrative data, demographic variables, clinical diagnoses). Column selection for tags is defined by the user based on data understanding and domain knowledge.

The _MEDomics Standard_ format is built on this tagging mechanism. Rather than relying on a fixed dataset schema, _MEDomics_ allows users to define multiple semantic views over the same dataset through tags. This design provides flexibility while preserving consistency and traceability.

The predictors in our dataset include&#x20;demographics (age and sex at birth), admission characteristics (10 variables), comorbidity diagnoses&#x20;(85 binary variables), and admission diagnoses (147 binary variables), for a total of 244&#x20;predictors. More info about the dataset can be found [here](https://www.researchsquare.com/article/rs-5363467/v1).&#x20;

The [POYM](https://github.com/MEDomicsLab/POYM) (Prediction Of One-Year Mortality) study uses two sets of predictors for model training and evaluation: **AdmDemo** and **AdmDemoDx**. AdmDemo includes demographics and admission characteristics, and AdmDemoDx includes demographics,&#x20;admission characteristics, comorbidity diagnoses, and admission diagnoses.

For this proof of concept, we will use 3 tags to represent our two sets:&#x20;

1. **adm** for admission characteristics.
2. **demo** for demographics.
3. **dx** for comorbidity diagnoses and admission diagnoses.&#x20;

To access the tool, open the _Input Module_ from the left navigation panel. Under _Data Organization_, select _Structuring & Tagging_, then click on _Column Tagging Tools_.

#### <mark style="color:blue;">Variable Mapping by Tag</mark>

| Tag      | Variables                                                                                                                                                                 |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Adm**  | ed\_visit\_count, ho\_ambulance\_count, total\_duration, flu\_season, living\_status, admission\_group, is\_ambulance, is\_icu\_start\_ho, is\_urg\_readm, service\_group |
| **Demo** | age\_original, gender                                                                                                                                                     |
| **Dx**   | All remaining variables not included in Adm or Demo                                                                                                                       |

<figure><img src="../../.gitbook/assets/image 1.png" alt=""><figcaption><p>Create the "adm", "demo" and "dx" tags</p></figcaption></figure>

You can visualize the tags within the dataset in the _MEDomics_ editor.

#### Holdout set creation

After creating our tags, the final step is to split our data into a learning set and a holdout set. For this task, we will use the _Holdout Set Creation Tools_. To access this tool, select _Sampling_ under the _Data Wrangling_ section in the _Input Module_. After selecting our dataset (`homr_any_visit_10pct.csv`), click on _Shuffle_ and _Stratify_, keep the split percentage at 20%, "drop" as the empty cells cleaning method, select "**oym**" as our target column and make sure that the _Keep tags_ toggle button is active so that the tags can be applied to the Learning and Holdout sets. Then hit the plus icon. This will create two new CSV datasets: `Holdout_homr_any_visit_10pct.csv` and `Learning_homr_any_visit_10pct.csv`. These steps are illustrated in the figure below:

<figure><img src="../../.gitbook/assets/image 2.png" alt=""><figcaption><p>Create a holdout set for our synthetic dataset</p></figcaption></figure>

With the creation of the Holdout and the Learning sets, we conclude our Input Module steps, and we can now start the machine learning phase.

> This step ensures that the dataset is properly prepared for the demo and ready to be used in a complete end-to-end workflow within _MEDomics_, including the **Learning**, **Evaluation** and **Application** modules. In the next section, we will both `homr_any_visit_10pct.csv` and `homr_any_visit.csv` datasets (with the applied tags preserved, of course!) to run machine learning experiments and replicate the POYM study.

This concludes our _Input Module_ section. Now our data is ready for model training!
