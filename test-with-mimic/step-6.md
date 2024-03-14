---
description: Mar 25 – Apr 8 | Create Model
---

# Step 6: Create Model

<figure><img src="../.gitbook/assets/MicrosoftTeams-image (5).png" alt=""><figcaption><p>Step 6 - Create Model</p></figcaption></figure>

{% hint style="info" %}
If you completed [_Step 4 - Explore Data_](step-4.md), you have data ready for _Step 6 - Create Model_.&#x20;

However, before proceeding to _Step 6 - Create Model,_ we recommend that you replace your own output data from [_Step 4 - Explore Data_](step-4.md) (the _MEDprofiles_/_timePoints_ folder) with the data that we prepared for you (_MEDomicsLab\_TestingPhase\_Step6.zip_). This will ensure consistency of results across all participants of the Testing Phase.&#x20;

An invitation to access the _MEDomicsLab\_TestingPhase\_Step6.zip_ data was sent by email.&#x20;
{% endhint %}

In this current _Step 6 - Create Model_, we will leverage the functionalities of the [_Learning Module_](../tutorials/development/learning-module.md) to build machine learning models using the learning set obtained from [_Step 4 - Explore Data_](step-4.md). In this step, we'll create two Learning scenes:

**Scene 1: Time-Dependent Model Comparison**&#x20;

We aim to assess the impact of patient timelines on model performance, hypothesizing that the performance will increase with time, particularly nearing the last hospital stay. We will compare the best models from the following datasets:

1. Dataset from the data obtained at the first time point (_T1\_learning\_modified.csv_).
2. Dataset combining data from the first and second time points (_T1\_learning\_modified.csv_ and _T2\_learning\_modified.csv_).
3. Dataset combining data from the first, second, and third time points (_T1\_learning\_modified.csv_, _T2\_learning\_modified.csv_, and _T3\_learning\_modified.csv_).
4. Dataset combining data from all time points (_T1\_learning\_modified.csv_, _T2\_learning\_modified.csv_, _T3\_learning\_modified.csv_, and _T4\_learning\_modified.csv_).

**Scene 2: Variable-Dependent Model Comparison**&#x20;

This scene aims to assess the impact of considered variables on model performance. We will use data from the first two time points (T1\_learning\_modified.csv and T2\_learning\_modified.csv), assuming that models involving data from the last time points might make predictions too late in a patient's timeline. We'll compare the best models from the following datasets:

1. All demographic and time-series data (_tslab_, _tsprocedure_, and _tschart_ classes) from _T1\_learning\_modified.csv_ and _T2\_learning\_modified.csv_.
2. All demographic and notes data (_ndischarge_ and _nradiology_) from _T1\_learning\_modified.csv_ and _T2\_learning\_modified.csv_.
3. All demographic and image data from _T1\_learning\_modified.csv_ and _T2\_learning\_modified.csv_.
4. Selected variables from various data types based on observations made using the first three pipelines, aiming to obtain the best possible model.

These scenes are designed to provide a comprehensive comparison of models under different temporal and variable considerations.

{% hint style="info" %}
You are welcome to use this step to conduct your own experiments and explore the functionalities of the [_Learning Module_](../tutorials/development/learning-module.md). However, please note that there are some missing options and tooltips that we haven't implemented yet, and we intend to address these before [_Step 8 - Challenge_](step-8.md).:wink:
{% endhint %}

## Recommendations

Before proceeding with _Step 6 - Create Model_ of the MEDomicsLab Testing Phase, we recommend consulting the documentation of the [_Learning Module_](../tutorials/development/learning-module.md).

{% content-ref url="../tutorials/development/learning-module.md" %}
[learning-module.md](../tutorials/development/learning-module.md)
{% endcontent-ref %}

{% hint style="info" %}
Please note that the [_Learning Module_](../tutorials/development/learning-module.md) is a graphical implementation of the [_PyCaret_ Python library](https://pycaret.gitbook.io/docs/). Additionally, if you are seeking information about elements in the Learning Module, you may find it in the [_PyCaret_ documentation](https://pycaret.gitbook.io/docs/).

The [_PyCaret_ documentation](https://pycaret.gitbook.io/docs/) often refers to other Python packages, as they built their functions around these packages. If you want to learn more about some options of certain functionalities, you may need to search in these other packages to find the information you are looking for.

For example, if you are looking for information on the `fold_strategy` parameter in the Dataset box:

1. Visit the [_PyCaret_ documentation](https://pycaret.gitbook.io/docs/), specifically the [Data Preprocessing section](https://pycaret.gitbook.io/docs/get-started/preprocessing).
2. Look for the category related to the `fold_strategy` parameter, which is under Other Setup Parameters -> Model Selection.
3. The [Model Selection part](https://pycaret.gitbook.io/docs/get-started/preprocessing/other-setup-parameters#model-selection) contains explanations about related parameters, including the `fold_strategy` parameter. It specifies that this parameter takes, as input, predefined strings or a cross-validation object compatible with [_scikit-learn_](https://scikit-learn.org/stable/). If you want additional information about the possible parameters, you'll have to search for the information on your own in the [_scikit-learn_ documentation](https://scikit-learn.org/stable/). For example, if you want to know more about the default value for `fold_strategy` (which is `stratifiedkfold`), you will have to search for 'stratifiedkfold' in the [_scikit-learn_ documentation](https://scikit-learn.org/stable/). The page related to this information is available [here](https://scikit-learn.org/stable/modules/generated/sklearn.model\_selection.StratifiedKFold.html).

Also, if you want to fully understand how [_PyCaret_](https://pycaret.gitbook.io/docs/) works in the background, this is an open-source library, and the code is available on [GitHub](https://github.com/pycaret/pycaret). (As we use the 3.1.0 version in our application, we recommend you to consult the [3.1.0 code](https://github.com/pycaret/pycaret/tree/3.1.0) if your research is related to our application).
{% endhint %}

## Instructions for Step 6 - Create Model

(Video + content here)
