---
icon: diagram-project
---

# medmodel

### **What is a MEDMODEL Object?**

A **`.medmodel`** file is a custom extension used within the **MEDomics** platform to represent serialized and saved machine learning models generated from the platform’s analytical scenes.

This object serves as a comprehensive container for all essential elements related to a trained model, including the model architecture, training parameters, preprocessing pipeline, selected features, and metadata.&#x20;

Its purpose is to ensure **traceability**, **reproducibility**, and **sharing** across different MEDomics modules or institutions, allowing seamless deployment, evaluation, and opening the doors to collaboration.

***

### **Structure of a MEDMODEL Object**

Each **MEDMODEL** object is composed of **two main components**:

#### **1. Serialized Scikit-learn Pipeline**

{% hint style="info" %}
Storing preprocessing steps within the pipeline ensures that **input data is processed consistently** between training and inference, eliminating discrepancies in data handling.
{% endhint %}

The core of the MEDMODEL is the [**Scikit-learn Pipeline**](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html) that encapsulates the entire machine learning workflow (see example below), including:

* **Preprocessing steps:** Normalization, feature scaling, missing-value imputation, categorical encoding, etc.
* **Feature selection and transformation:** Any dimensionality reduction or feature engineering steps applied before model fitting.
* **Trained estimator:** The final classifier or regressor model trained on the selected data (e.g., XGBoost, RandomForest, Logistic Regression).

<figure><img src="../../../../.gitbook/assets/1_e6U6j_FJirAbYYYTfEB-wQ.png" alt="" width="563"><figcaption><p>Example a Scikit-Learn Pipeline [<a href="https://medium.com/ai-made-simple/pipelines-in-scikit-learn-46c61c5c60b2">Source</a>]</p></figcaption></figure>

**Storage Details**

* If the serialized pipeline file (pickle format) is **≤ 16 MB**, it is stored **directly in MongoDB**.
* If it **exceeds 16 MB**, it is stored **locally on the server**, and the MEDMODEL entry in MongoDB references the **absolute file path**.

#### **2. Model Metadata Dictionary**

A companion dictionary holds detailed information describing the model, its inputs, and training context. This metadata ensures reproducibility and facilitates understanding of the model’s provenance and purpose.

The key metadata fields include:

* **`model_variables`** – The final list of dataset columns (features) used during training.
* **`target_variable`** – The dependent variable the model predicts.
* **`ml_type`** – Specifies whether the model is for **classification** or **regression**.

The following diagram summarizes the relationship between MEDMODEL components:

```
 ┌────────────────────┐
 │    MEDMODEL        │
 │ (.medmodel object) │
 └────────┬───────────┘
          │
          ├──► Scikit-learn Pipeline (Pickle)
          │     • Preprocessing
          │     • Feature selection
          │     • Trained model
          │
          └──► Metadata Dictionary
                • Features
                • Target
                • Model Type (Classification/Regression)
```

***

The following figure summarizes the creation process of a MEDMODEL object:

<figure><img src="../../../../.gitbook/assets/image (67).png" alt=""><figcaption><p>.medmodel handling in MEDomics</p></figcaption></figure>
