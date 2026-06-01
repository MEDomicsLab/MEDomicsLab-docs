---
description: >-
  We evaluate our centralized trained MLP model in different contexts. The goal
  is to assess model performance in every case and its ability to generalize to
  external hospitals and datasets.
icon: '3'
---

# Evaluation Module for Centralized Learning

These evaluations allow us to understand how well the model performs within the same domain, as well as its ability to generalize to new hospitals and datasets.

{% hint style="info" %}
If this is your first time using this module, you can refer to the [documentation](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/evaluation-module) for more info.
{% endhint %}

> Before presenting and interpreting the results, we first demonstrate how to perform these evaluations in MEDomics using the Evaluation Module.
>
> The evaluation procedure remains the same, but different datasets are used for each evaluation.
>
> In total, the process must be repeated **five times**:
>
> * once for **Evaluation 1 (MIMIC holdout)**
> * once for **Evaluation 2 (aggregated eICU holdout)**
> * three times for **Evaluation 3 (hospital-specific evaluations)**
>
> This process produces the results presented in this section.

Follow these steps to create a new evaluation page in the Evaluation Module:

1. Double-click the Evaluation Module icon in the left sidebar.
2. Click on the Create evaluation page "+" button.
3. Provide a name for your evaluation page (e.g., _eval1 for Evaluation 1_).
4. Click Create to generate the evaluation page.

<figure><img src="../../.gitbook/assets/image 36.png" alt="" width="369"><figcaption><p>Creating a new evaluation page in the Evaluation Module</p></figcaption></figure>

The Evaluation Module presents two sections : Predictions and Dashboard. The first section has predictions for the holdout set and the second section is generated using the [explainerdashboard](https://explainerdashboard.readthedocs.io/en/latest/) package with different subsections.&#x20;

{% hint style="info" %}
For this tutorial, we will focus on the Dashboard section and specifically on the Feature Importances and Classification Stats (performance metrics and confusion matrices) subsections.
{% endhint %}

### <mark style="color:$success;">**Evaluation 1 : Internal Validation (MIMIC Holdout)**</mark>

The first evaluation is performed on the **MIMIC holdout dataset**, which originates from the same dataset used for training.

The objective of this evaluation is to measure model performance within the same domain. This serves as a **reference baseline** for subsequent evaluations.

Since the training and evaluation data come from the same distribution, this evaluation typically provides the best expected performance.

#### Performance Metrics

The results obtained on the MIMIC holdout dataset demonstrate **strong overall performance**, confirming that the model effectively captures predictive patterns from the training data.

The model achieved:

* **Accuracy:** 0.752
* **Recall (Sensitivity):** 0.683
* **F1-score:** 0.49
* **AUC:** 0.825

The figure below presents all the metrics for this evaluation.

<figure><img src="../../.gitbook/assets/image (61) (1).png" alt="" width="379"><figcaption><p>Metrics for Evaluation 1 (MIMIC holdout set)</p></figcaption></figure>

These results indicate good discrimination capability and a strong ability to detect high-risk patients. The relatively high ROC-AUC confirms that the model performs well in distinguishing between positive and negative cases.

As expected, performance is highest in this evaluation since there is **no dataset shift** between training and testing data.

#### Confusion Matrix

The confusion matrix provides additional insight into model behavior.

The results in the figure below show:

* A **low number of false negatives**
* A **balanced number of true positives and true negatives**
* A moderate number of false positives

<figure><img src="../../.gitbook/assets/image (62) (1).png" alt="" width="464"><figcaption><p>Confusion matrix for the evaluation on MIMIC holdout set</p></figcaption></figure>

This behavior is particularly important in clinical settings, where minimizing false negatives is crucial to avoid missing high-risk patients.

Overall, the confusion matrix confirms that the model prioritizes **sensitivity**, which is desirable for mortality prediction tasks.

#### Feature Importance

The feature importance analysis in the figure below reveals that the model relies on **clinically relevant variables**. The most influential features include:

* Age
* Vital signs
* Laboratory values
* Comorbidities
* Admission characteristics

<figure><img src="../../.gitbook/assets/image (63) (1).png" alt="" width="563"><figcaption><p>Feature Importance for the evaluation on MIMIC holdout set</p></figcaption></figure>

These findings are consistent with clinical expectations and previous studies, including MED3PA, where similar variables were identified as key predictors of patient outcomes.

The consistency of feature importance across evaluations also suggests that the model learns robust and meaningful clinical patterns.

#### Interpretation

Overall, the internal validation on the MIMIC holdout dataset demonstrates strong predictive performance, good discrimination capability, high sensitivity for detecting high-risk patients and clinically meaningful feature importance.

These results confirm that the centralized model performs well within the training domain and provides a **solid baseline** for comparison with external validation results on the eICU dataset.

The next evaluation assesses model generalization performance on external hospitals, where **dataset shift** is expected.

### <mark style="color:$success;">**Evaluation 2 : Global External Validation (Aggregated eICU Holdout)**</mark>

The second evaluation is performed on the **aggregated eICU holdout dataset**, which combines holdout data from multiple hospitals.

The objective of this evaluation is to measure **model generalization** when applied to a different dataset. This setup introduces a **dataset shift** between MIMIC and eICU, allowing us to assess how robust the centralized model is across domains.

This evaluation provides a global external performance estimate across hospitals.

#### <mark style="color:green;">Performance Metrics</mark>

The results obtained on the aggregated eICU holdout dataset show a **moderate decrease in performance**, which is expected due to the dataset shift between MIMIC and eICU.

The model achieved:

* **Accuracy:** 0.633
* **Recall (Sensitivity):** 0.651
* **F1-score:** 0.419
* **ROC-AUC:** 0.701

The figure below presents all the metrics for this evaluation.

<figure><img src="../../.gitbook/assets/image (65) (1).png" alt="" width="368"><figcaption><p>Metrics for the evaluation on eICU hospitals holdout set</p></figcaption></figure>

Although performance slightly decreases compared to the MIMIC evaluation, the model still maintains good discrimination capability and reasonable sensitivity.

This result indicates that the centralized model **generalizes well across different hospitals**, despite differences in patient populations and clinical practices.

#### <mark style="color:green;">Confusion Matrix</mark>

The confusion matrix in the figure below for the aggregated eICU dataset shows:

* A moderate number of false positives
* A balanced number of true positives
* A slight increase in false negatives compared to MIMIC

<figure><img src="../../.gitbook/assets/image (66) (1).png" alt="" width="467"><figcaption><p>Confusion matrix for the evaluation on eICU hospitals holdout set</p></figcaption></figure>

This behavior is expected when evaluating on external data, as differences between datasets may affect prediction performance.

Despite this, the model maintains **good sensitivity**, which remains important for detecting high-risk patients in clinical settings.

Overall, the confusion matrix confirms that the model retains **reasonable predictive performance** under dataset shift conditions.

#### <mark style="color:green;">Feature Importance</mark>

Feature importance analysis shows that the model continues to rely on **clinically relevant features**, similar to those observed in the MIMIC evaluation.

The most important features (in the figure below) include:

* Age
* Vital signs
* Laboratory values
* Comorbidities
* Admission characteristics

<figure><img src="../../.gitbook/assets/image (64) (1).png" alt="" width="563"><figcaption><p>Feature Importance for the evaluation on eICU hospitals holdout set</p></figcaption></figure>

The consistency of feature importance across MIMIC and eICU suggests that the model learns **robust clinical patterns** that generalize across datasets.

This is an important result, as it indicates that the centralized model does not rely on dataset-specific features.

#### <mark style="color:green;">Interpretation</mark>

The global external validation on the aggregated eICU dataset demonstrates a moderate decrease in performance due to dataset shift, good generalization capability across hospitals, consistent feature importance across datasets and reasonable sensitivity for detecting high-risk patients

These results confirm that the centralized model is **robust across domains** and provides reliable performance when applied to external hospital data.

The next evaluation further investigates **performance variability across individual hospitals**, allowing for a more detailed analysis of inter-site heterogeneity.

### <mark style="color:$success;">**Evaluation 3 : Hospital-Specific External Validation**</mark>&#x20;

Finally, we evaluate the model separately on **selected eICU hospitals**.

The objective of this evaluation is to measure **inter-site heterogeneity**. Some hospitals may differ significantly in patient population, clinical practices, or data distributions.

This evaluation helps identify whether model performance varies across hospitals and provides additional insight into **model generalization across institutions**.

In the next part, we will present the three best performing eICU hospitals.

#### <mark style="color:orange;">1- Hospital 264 : Best Performance</mark>

This hospital shows the best performance among all evaluated hospitals.

* Accuracy: 0.783
* Recall (Sensitivity): 1.00
* F1-score: 0.545
* ROC-AUC: 0.929

More metrics can be seen in the figure below.

<figure><img src="../../.gitbook/assets/image (92) (1).png" alt="" width="315"><figcaption><p>Metrics for hospital 264 holdout set</p></figcaption></figure>

These results indicate **excellent model performance** and strong generalization to this hospital.

The very high recall indicates that the model successfully identifies **all high-risk patients**, which is particularly important in clinical settings.

<mark style="color:green;">**Confusion Matrix**</mark>

The confusion matrix for Hospital 264 in the figure below shows:

* Very high true positive rate
* No false negatives
* Moderate false positives

<figure><img src="../../.gitbook/assets/image (93) (1).png" alt="" width="392"><figcaption><p>Confusion Matrix for the evaluation on hospital 264 holdout set</p></figcaption></figure>

This behavior indicates that the model **prioritizes sensitivity**, ensuring that high-risk patients are not missed.

This is desirable in mortality prediction tasks, where missing high-risk patients can have serious consequences.

<mark style="color:green;">**Feature Importance**</mark>

Feature importance for Hospital 264 remains consistent with previous evaluations. The most influential variables include:

* Age
* Vital signs
* Laboratory values
* Comorbidities
* Admission characteristics

The results are shown in the figure below.

<figure><img src="../../.gitbook/assets/image (91) (1).png" alt="" width="563"><figcaption><p>Feature Importance for the evaluation on hospital 264 holdout set</p></figcaption></figure>

This consistency confirms that the model learns **robust clinical patterns**.

<mark style="color:green;">**Interpretation**</mark>

Hospital 264 demonstrates excellent generalization, high sensitivity and strong predictive performance

This hospital represents the best-case scenario for model generalization.

#### <mark style="color:orange;">2- Hospital 420 : Good Balance</mark>

Hospital 420 shows **balanced performance** across metrics.

* Accuracy: 0.633
* Recall (Sensitivity): 0.75
* F1-score: 0.522
* ROC-AUC: 0.775

More metrics can be seen in the figure below.

<figure><img src="../../.gitbook/assets/image - 2026-05-25T115519.858.png" alt="" width="316"><figcaption><p>Metrics for hospital 420 holdout set</p></figcaption></figure>

These results indicate good model performance, with a strong ability to detect high-risk patients.

<mark style="color:green;">**Confusion Matrix**</mark>

The confusion matrix for Hospital 420 in the figure below shows:

* High sensitivity
* Moderate specificity
* Higher false positives

<figure><img src="../../.gitbook/assets/image - 2026-05-25T115530.375.png" alt="" width="391"><figcaption><p>Confusion Matrix for the evaluation on hospital 420 holdout set</p></figcaption></figure>

This indicates that the model tends to **favor sensitivity over specificity**, which is acceptable in clinical applications.

<mark style="color:green;">**Feature Importance**</mark>

Feature importance (shown in the figure below) remains consistent with previous evaluations:

* Age
* Vital signs
* Laboratory values
* Comorbidities
* Admission characteristics

<figure><img src="../../.gitbook/assets/image - 2026-05-25T115542.439.png" alt="" width="563"><figcaption><p>Feature Importance for the evaluation on hospital 420 holdout set</p></figcaption></figure>

This consistency further supports model robustness.

<mark style="color:green;">**Interpretation**</mark>

Hospital 420 demonstrates:

* Good generalization
* Balanced performance
* Strong sensitivity

This hospital represents a **realistic generalization scenario**.

#### <mark style="color:orange;">3- Hospital 188 : Intermediate Performance</mark>

Hospital 188 shows **moderate performance**, representing a more challenging generalization scenario.

* Accuracy: 0.667
* Recall (Sensitivity): 0.778
* F1-score: 0.424
* ROC-AUC: 0.808

The figure below showcases more metrics for this evaluation.

<figure><img src="../../.gitbook/assets/image (71) (1).png" alt="" width="362"><figcaption><p>Metrics for hospital 188 holdout set</p></figcaption></figure>

These results indicate reasonable model performance with moderate generalization.

<mark style="color:green;">**Confusion Matrix**</mark>

The confusion matrix figure below shows:

* Good sensitivity
* Moderate false positives
* Balanced performance

<figure><img src="../../.gitbook/assets/image (72) (1).png" alt="" width="473"><figcaption><p>Confusion Matrix for the evaluation on hospital 188 holdout set</p></figcaption></figure>

The model still detects most high-risk patients, though performance is lower compared to the previous hospitals.

<mark style="color:green;">**Feature Importance**</mark>

Feature importance remains consistent with previous evaluations:

* Age
* Vital signs
* Laboratory values
* Comorbidities
* Admission characteristics

You can check the different values in the figure below.

<figure><img src="../../.gitbook/assets/image (70) (1).png" alt="" width="563"><figcaption><p>Feature Importance for the evaluation on hospital 188 holdout set</p></figcaption></figure>

This confirms that model behavior remains stable across hospitals.

### <mark style="color:$success;">Performance Comparison Across Evaluations</mark>

To better understand model behavior and generalization, we compare the results across the three evaluations:

* **Evaluation 1:** Internal Validation (MIMIC Holdout)
* **Evaluation 2:** Global External Validation (Aggregated eICU Holdout)
* **Evaluation 3:** Hospital-Specific External Validation (Hospitals 264, 420, 188)

This comparison highlights performance variations across datasets and assesses the stability of feature importance.

The results show a **progressive performance decrease** from internal to external evaluations, which is expected due to **dataset shift**. We summarized everything shown above in the table below.

| Evaluation   | Dataset       | Accuracy | Sensitivity | F1-score | ROC-AUC | Interpretation           |
| ------------ | ------------- | -------- | ----------- | -------- | ------- | ------------------------ |
| Evaluation 1 | MIMIC Holdout | 0.752    | 0.683       | 0.49     | 0.825   | Internal baseline        |
| Evaluation 2 | eICU Global   | 0.633    | 0.651       | 0.419    | 0.784   | Global generalization    |
| Evaluation 3 | Hospital 264  | 0.783    | 1.00        | 0.545    | 0.939   | Best performance         |
| Evaluation 3 | Hospital 420  | 0.633    | 0.75        | 0.522    | 0.775   | Balanced performance     |
| Evaluation 3 | Hospital 188  | 0.667    | 0.778       | 0.424    | 0.808   | Intermediate performance |

As for the feature importance, it remains **consistent across all three evaluations**, indicating stable model behavior.

#### **Conclusion**&#x20;

Although the model demonstrates reasonable performance, several limitations should be acknowledged:

* Performance metrics remain moderate
* Generalization across hospitals remains challenging
* Inter-site variability impacts performance

However, these results should be interpreted in the context of a proof of concept. This work represents a first centralized learning experiment within the MEDomics framework using MIMIC and eICU datasets.

The primary objective of this proof of concept is not to achieve optimal performance but rather to:

* Validate the centralized learning pipeline
* Assess generalization across datasets
* Establish a baseline for future experiments

This concludes our Evaluation Module for Centralized Learning section. In the next section, we will do the same steps but with our federated learning module.&#x20;
