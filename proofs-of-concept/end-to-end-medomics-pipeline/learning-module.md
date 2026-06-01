---
description: >-
  In this section, we train a baseline MLP model using the MIMIC-IV learning
  dataset prepared earlier. The objective is to build a reference model that
  will later be evaluated across multiple hospitals.
icon: '2'
---

# Learning Module

{% hint style="info" %}
The [Learning Module](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module) is a core component of the MEDomics platform, allowing users to train machine learning models using a visual pipeline and configurable model parameters.
{% endhint %}

In this section, we train a centralized baseline model using the MIMIC-IV learning dataset prepared during the preprocessing steps. The objective is to build a reference model that will later be evaluated across multiple hospitals and compared with a federated learning approach.

Although the MED3pa study used XGBoost as the baseline model, we instead use a **Multi-Layer Perceptron (MLP)**. This choice was made to ensure compatibility with MEDfl, which requires a neural network architecture for federated learning (for now). The trained centralized model will later be used as the starting point for federated training across multiple hospitals.

### Workspace Setup

First, download all files from the link shared in the Preprocessing Steps section.&#x20;

Put them in a folder called PoC4. Open the MEDomics platform and select this folder as your workspace.&#x20;

### &#x20;Scene Creation

{% hint style="info" %}
If this is your first time using the Learning Module, please refer to our documentation for more info on scene creation and nodes [here](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module).
{% endhint %}

Follow the steps shown in the figure to create a scene :

1. Double-click on the Learning Module icon located in the left sidebar.
2. Click the "+" button next to Create scene.
3. Enter the scene name **:** In the pop-up window, enter `training_with_mimic` as name for the scene.
4. Click Create to generate the new scene.

<figure><img src="../../.gitbook/assets/image 31.png" alt="" width="375"><figcaption><p>Create the scene</p></figcaption></figure>

Then, open your newly created scene and build the evaluation pipeline by dragging, dropping, and connecting the nodes.

At this stage, simply reproduce the structure shown in the figure below by adding and connecting the nodes accordingly.

The configuration of each node will be detailed in the next section.

<figure><img src="../../.gitbook/assets/image (94) (1).png" alt=""><figcaption><p>Scene workflow </p></figcaption></figure>

{% hint style="info" %}
If you are unfamiliar with the input/output (I/O) ports of each node, please refer to the [documentation](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module#available-nodes-summary-table) for more information.
{% endhint %}

#### Initialization Nodes

{% hint style="info" %}
You can learn more about Initialization Nodes [here](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module/initialization).
{% endhint %}

<mark style="color:$success;">**1- Dataset Node**</mark> <mark style="color:$success;"></mark><mark style="color:$success;">:</mark> Use the following configuration:

* **Type**: Custom data file
* **Files**: Learning\_MIMIC\_95.csv
* **Target**: deceased

<figure><img src="../../.gitbook/assets/image (95) (1).png" alt=""><figcaption><p>Dataset Node configuration</p></figcaption></figure>

<mark style="color:$success;">**2- Clean Node**</mark> <mark style="color:$success;"></mark><mark style="color:$success;">:</mark> We're going to apply normalization on our data. To do that, select the following parameters using the plus button.

* **normalize** : to activate normalization. Set it to **True**.
* **normalize\_method** : to choose the normalization method. Set it to **minmax**.&#x20;

<figure><img src="../../.gitbook/assets/image (10).jpg" alt=""><figcaption><p>Clean Node configuration</p></figcaption></figure>

{% hint style="warning" icon="thumbtack-angle" %}
This method is chosen because it has proven to be the best method for our MLP model. You can also try the zscore method.
{% endhint %}

<mark style="color:$success;">**3- Model Node**</mark> <mark style="color:$success;"></mark><mark style="color:$success;">:</mark> Select "_Multi-Layer Perceptron_" as our machine learning algorithm.&#x20;

{% hint style="info" %}
A summary of the configuration can be found after this section.
{% endhint %}

<mark style="color:green;">**Initial Model Configuration**</mark>

Specifying initial values for hyperparameters in the Model node is not mandatory.\
The selected hyperparameters will later be optimized in the _Train Model node_ using a custom search space.

However, it is important to select the hyperparameters that will be optimized, as only selected parameters will be available during tuning.

In addition, some parameters such as the MLP architecture are fixed and define the model structure, and therefore must be explicitly set in the Model node.

<mark style="color:green;">**Fixed Model Architecture**</mark>

In this proof of concept, we fix the MLP architecture to:

* **`hidden_layer_sizes`** **= (32, 16)**

This configuration is chosen for a lightweight architecture suitable for federated learning experiments.\
The final hidden layer size is set close to the **15 predictive features** used in this proof of concept, ensuring a compact representation while maintaining model flexibility.

<mark style="color:green;">**Hyperparameters to Select**</mark>

The following hyperparameters must be selected to ensure they are optimized:

* **`activation`** — Activation function used in hidden layers.
* **`solver`** — Optimization algorithm.
* **`alpha`** — L2 regularization parameter.
* **`learning_rate_init`** — Initial learning rate.

{% hint style="warning" %}
You don't need to change the default values fixed when you select the hyperparameters.
{% endhint %}

The figure below summarizes the configuration for the Model Node.&#x20;

<figure><img src="../../.gitbook/assets/image (124).png" alt="" width="563"><figcaption><p>Model Node configuration </p></figcaption></figure>

#### Training Nodes

{% hint style="info" %}
You can learn more about Training Nodes [here](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module/initialization).
{% endhint %}

<mark style="color:$success;">**Train Model Node :**</mark> Make sure to activate the **Tune Model** toggle button as shown in the figure below.

<mark style="color:green;">**Hyperparameter Tuning Configuration**</mark>

When activating the **Tune Model** toggle (1) in the _Train Model_ node, you will notice that the option **"Use PyCaret's default hyperparameter search space"** is automatically enabled (2).

Since we are defining a custom tuning grid, the default PyCaret search space is not required. Make sure to **deactivate this toggle (2)**.

Once disabled, the **Custom Tuning Grid** section **(3)** for our MLP model becomes available, allowing you to configure the hyperparameters manually.&#x20;

The figure below illustrates these steps.

<figure><img src="../../.gitbook/assets/image 33 (2).png" alt="" width="325"><figcaption><p>Custom hyperparameter tuning configuration</p></figcaption></figure>

Click on the plus button next to MLP. Each hyperparameter selected in the Model node will appear in the grid, where you can specify either:

* A Range (start, end, step), or
* Discrete values.

<mark style="color:green;">**Custom Grid Configuration**</mark>

Set the hyperparameters as follows:

**1. `solver` :** Optimization algorithm used for training the neural network.

Discrete values : **{adam**, **sgd}**

**2. `learning_rate_init` :** Initial learning rate used during training.

Discrete values : **{0.001**, **0.0001**, **0.005}**

**3. `alpha` :** L2 regularization parameter controlling model complexity.

Discrete values : **{0.0001**, **0.0003**, **0.001**, **0.003}**

A summary of the custom grid can be seen in the figures below.

<figure><img src="../../.gitbook/assets/Group 7.png" alt=""><figcaption><p>Custom Grid values</p></figcaption></figure>

<mark style="color:green;">**Tune Model Options**</mark>&#x20;

After defining the custom hyperparameter grid, click on the "+" button in General Options to select the following parameters and configure them as follows:&#x20;

**1. `search_library`**

Set the **search\_library** parameter to **"scikit-learn"**.

**2. `search_algorithm`**

Set the **search\_algorithm** parameter to **"random"**. Random search is used to efficiently explore the hyperparameter space while keeping computation time reasonable.

Every step is documented in the figure below.

<figure><img src="../../.gitbook/assets/image 35.png" alt="" width="315"><figcaption><p>Tune Model Options configuration</p></figcaption></figure>

{% hint style="info" %}
These custom grid and search strategy were selected to improve neural network performance while keeping the search space lightweight and efficient.
{% endhint %}

<mark style="color:green;">**Threshold Optimization**</mark>

After configuring the tuning options, we enable threshold optimization to improve classification performance. This is the last switch button in the node.

Activate the Optimize Threshold switch in the Train Model node and set:

* optimization\_metric → `Youden`

<figure><img src="../../.gitbook/assets/Group 8.png" alt="" width="362"><figcaption><p>Threshold Optimization configuration</p></figcaption></figure>

Threshold optimization adjusts the decision threshold used to convert predicted probabilities into class labels. Instead of relying on the default threshold (typically 0.5), the model selects the threshold that maximizes the chosen optimization metric.

In this proof of concept, we use the **Youden index**, which balances **sensitivity** and **specificity**. This is particularly important in healthcare settings, where both **false negatives** and **false positives** can have significant clinical consequences.

By optimizing the threshold using the Youden index, we aim to achieve a balanced model that detects high-risk patients while limiting unnecessary alerts. This step improves the robustness of the model before evaluating it across multiple hospitals and training strategies.

{% hint style="success" icon="thumbtack-angle" %}
Plots documenting the evolution of our threshold optimization process will be automatically generated in your default browser. You can visualize them for more info on the process.
{% endhint %}

#### Analysis Nodes

* No changes required for the _Analyze Node_.

{% hint style="warning" %}
Make sure all connections are correctly established before launching the scene.
{% endhint %}

#### Run the scene and analyze the results

{% hint style="info" %}
An overview of each button in the Learning Module, along with its corresponding functionality, is available in the documentation. You can access it [here](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module#id-4.-utils-menu).
{% endhint %}

Once the scene is fully configured, Click the Run button located in the top-right corner of the interface, as highlighted in the figure below.

You can monitor the progress using the progress bar displayed at the bottom of the interface.

When the execution is complete, the _Analysis Mode_ button will become active. Click on it to open the analysis panel at the bottom of the screen, where the results will be displayed.

#### Results

The figure below shows the performance of the centralized MLP model trained on the MIMIC-IV learning dataset.

<figure><img src="../../.gitbook/assets/image - 2026-04-08T113057.641.png" alt=""><figcaption><p>MLP results</p></figcaption></figure>

Although the MED3pa study reports results obtained with XGBoost and a temporal split of MIMIC-IV (2008–2013 for training), our proof of concept uses an MLP model trained on a 95/5 split without temporal separation. Therefore, a direct comparison is not possible.

However, the obtained performance falls within a similar range to the MED3pa baseline results, providing an **indicative validation** of the pipeline and confirming that the trained MLP model is suitable for subsequent **cross-hospital** and **federated learning** experiments.

<mark style="color:green;">**Finalize and Save the model**</mark>&#x20;

In order to evaluate our model, click on the _Finalize & Save Model_ button, seen on the pipeline presentation. Click on the button again if you can't see the saved model in the _Models_ folder.&#x20;

{% hint style="info" %}
You can read this [documentation](https://medomicslab.gitbook.io/medomics-docs/tutorials/development/learning-module/analysis#finalize-and-save-model) for more info on how to proceed.
{% endhint %}

<figure><img src="../../.gitbook/assets/Group 5.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Make sure your model is saved before moving on to the next section.
{% endhint %}

This concludes our _Learning Module_ section. Now our model is ready for evaluation!
