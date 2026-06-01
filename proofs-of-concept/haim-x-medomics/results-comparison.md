---
description: This page documents the final step of model application on new input data.
icon: '5'
---

# Results Comparison

This is where our file `patient_ID.csv` comes in handy. We're going to use the data in that file to test our model performance. Since we only registered the AdmDemo model, we will have 13 variables to file : age and sex, admission characteristics (10) and patient\_id.

### Manual Sample entry

Once you open the **Application Module**, select the **AdmDemo** model that was previously saved in the Learning Module.

After selecting the model, a list of input fields corresponding to each feature used during training will appear. You must manually enter a value for every variable required by the model.

For demonstration purposes, we saved the _simplest version_ of the model (the one with fewer input variables). This makes the manual data entry process clearer and easier to follow.

To illustrate the procedure, we selected the data corresponding to **Patient 16** from the saved dataset. These values can either:

* Be entered manually by referring to the saved file, or
* Be copied directly from the figure shown below.

This allows users to reproduce the exact same prediction and verify the consistency of the Application Module.

<figure><img src="../../.gitbook/assets/image (19) (2).png" alt=""><figcaption><p>Manual Sample Entry for patient 16</p></figcaption></figure>

Once all the values have been filled in:

1. Review the entries to ensure they are correct.
2. Click the **“Predict”** button.
3. Wait a few seconds for the model to generate the prediction result.

The result displayed is in the figure below:&#x20;

<figure><img src="../../.gitbook/assets/image (28) (2).png" alt=""><figcaption><p>Predicted value for the patient</p></figcaption></figure>

The predicted target value (0) is aligned with the true target value, which is False.

This demonstrates how we can use the Application module to deploy and test on trained machine learning models on unseen data.&#x20;
