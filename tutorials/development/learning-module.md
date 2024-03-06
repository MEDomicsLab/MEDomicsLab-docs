---
description: This is where the magic happens 🧙🪄
---

# Learning Module

{% hint style="info" %}
The Learning Module is built around the open-source Python library [PyCaret](https://pycaret.gitbook.io/docs/). You can found useful informations about [PyCaret](https://pycaret.gitbook.io/docs/) at the following links:

* [PyCaret Gitbook](https://pycaret.gitbook.io/docs/)
* [PyCaret ReadTheDocs](https://pycaret.readthedocs.io/en/latest/)
* [PyCaret GitHub](https://github.com/pycaret/pycaret)
{% endhint %}

## Overview Videos

{% embed url="https://youtu.be/0PsuT_zXllk" %}
Learning Module - Scene Creation
{% endembed %}

{% embed url="https://youtu.be/9vcAkIaAcxE" %}
Learning Module - Understanding Pipelines and Results
{% endembed %}

***

## Create a Scene

* Click on the _Learning Module_ Icon. <img src="../../.gitbook/assets/icon (2).png" alt="" data-size="line">
* Click on the _Create scene_ button.
* Enter a name for the new scene.
* The app will generate a folder containing:
  * Your scene (._medml_ file).
  * A folder for your scene models.
  * A folder for your scene notebooks.&#x20;

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Learning_module_1.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/Learning_module_2.png" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Learning_module_3.png" alt="" width="563"><figcaption></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/learning_scene (1).png" alt="" width="375"><figcaption></figcaption></figure>

</div>

{% hint style="info" %}
```javascript
breast_cancer_scene                -> Scene folder
    ├───models                     -> Folder where models are saved
    ├───notebooks                  -> Folder where notebooks are saved
    └───breast_cancer_scene.medml  -> Scene file
```
{% endhint %}

***

## Module Overview

{% hint style="info" %}
Double click on the ._medml_ file to open the scene.
{% endhint %}

<figure><img src="../../.gitbook/assets/Learning_module_4.png" alt=""><figcaption><p>Empty scene</p></figcaption></figure>

### 1. Available Nodes

<figure><img src="../../.gitbook/assets/node.png" alt=""><figcaption><p>Structure of a Node</p></figcaption></figure>

{% hint style="info" %}
_Add options_ button open a panel where you can select additional options. These options are automatically generated from the online [_ReadTheDocs_ documentation of PyCaret](https://pycaret.readthedocs.io/en/latest/).&#x20;
{% endhint %}

{% hint style="info" %}
The links we use to explain the _PyCaret_ specific functions are refering to the [Classification part of the _PyCaret_ documentation](https://pycaret.readthedocs.io/en/latest/api/classification.html), but please note that the functions are also present on the other Machine Learning types of _PyCaret_ (for example you can found them in the [Regression documentation of PyCaret](https://pycaret.readthedocs.io/en/latest/api/regression.html)).
{% endhint %}

<table data-full-width="true"><thead><tr><th width="219">Node</th><th width="468.5">Description</th><th width="135">Input</th><th>Output</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/dataset (2).png" alt="" data-size="original"></td><td><p>This is the entry point of an experiment.<br>You have 2 options here:</p><ol><li><strong>MEDomicsLab standard</strong>: It takes as entry files contained in a learning folder, that may represent the learning set from static .<em>csv</em> files obtained trough the <a href="../design/input-module/medprofiles/"><em>MEDprofiles</em> process</a>. The node automatically detects which files are matching the format and display them in a Dropdown selector. Then you will have to choose which column from your selected .<em>csv</em> file(s) should be the target to predict. If you selected more than one file, all the selected files should have the same target column.</li><li><strong>Custom file</strong>: You can choose any .<em>csv</em> file from the Dropdown selector displaying all your .<em>csv</em> files from your workspace. Then you will have to choose which column from your selected .<em>csv</em> file should be the target to predict.</li></ol><p>The available options for this node corresponds to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.setup"><em>PyCaret</em> <em>setup</em> function options</a> that are not directly relative to data cleaning.</p></td><td>-</td><td>dataset</td></tr><tr><td><img src="../../.gitbook/assets/clean (2).png" alt="" data-size="original"></td><td>This node allows you to clean your dataset. The available options for this node corresponds to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.setup"><em>PyCaret</em> <em>setup</em> function options</a> that are directly relative to data cleaning.</td><td>dataset</td><td>dataset</td></tr><tr><td><img src="../../.gitbook/assets/model.png" alt="" data-size="original"></td><td>This node allows you to select a model and its associated parameters. It corresponds to the <em>estimator</em> parameter of the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.create_model"><em>PyCaret</em> <em>create_model</em> function</a>. The models directly comes from the <a href="https://scikit-learn.org/stable/"><em>sickit-learn</em></a> package. Infact, if you are looking for documentation about a certain model parameter, you will find it in the <a href="https://scikit-learn.org/stable/"><em>sickit-learn</em></a> documentation.</td><td>-</td><td>model_config</td></tr><tr><td><img src="../../.gitbook/assets/train.png" alt="" data-size="original"></td><td>This node allows you to train a model. The available options for this node corresponds to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.create_model"><em>PyCaret create_model</em> function options</a> (except the <em>estimator</em> parameter which is defined through the Model node).</td><td>model_config AND dataset</td><td>model</td></tr><tr><td><img src="../../.gitbook/assets/compare (1).png" alt="" data-size="original"></td><td>This node allows you to train and evaluate performance of all estimators available in the <em>PyCaret</em> model library using cross validation. The available options for this node corresponds to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.compare_models"><em>PyCaret compare_models</em> function options</a>.</td><td>dataset</td><td>model(s)</td></tr><tr><td><img src="../../.gitbook/assets/load_model (1).png" alt="" data-size="original"></td><td>This node allows you to load a model from a file. It takes as entry a model from the ones you saved in your scene, displayed in a Dropdown selector. The available options for this node are the ones available in the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.load_model"><em>PyCaret load_model</em> function</a>, except the model name, replaced by the selected file.</td><td>dataset</td><td>model</td></tr><tr><td><img src="../../.gitbook/assets/optimize (2).png" alt="" data-size="original"></td><td>This node allows you to optimize a model. It is different from the other nodes as when clicking on it it opens a subflow containing other nodes. It gather the <a href="https://pycaret.gitbook.io/docs/get-started/functions/optimize">Optimization functions of <em>PyCaret</em></a>. **</td><td>model</td><td>model</td></tr><tr><td><img src="../../.gitbook/assets/analyze.png" alt="" data-size="original"></td><td>This node allows you to analyze a model. It gather the <a href="https://pycaret.gitbook.io/docs/get-started/functions/analyze">Analysis and model explainability functions of <em>PyCaret</em></a>. For now, only the <a href="https://pycaret.gitbook.io/docs/get-started/functions/analyze#plot_model"><em>plot_model</em> function</a> is implemented in our application.</td><td>model</td><td>-</td></tr><tr><td><img src="../../.gitbook/assets/finalize.png" alt="" data-size="original"></td><td>This node allows you to finalize a model. The available options for this node corresponds to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.finalize_model"><em>PyCaret finalize</em> function options</a> (except the <em>estimator</em> parameter which is pass as input of this node).</td><td>model</td><td>model</td></tr><tr><td><img src="../../.gitbook/assets/save_model.png" alt="" data-size="original"></td><td>This node allows you to save a model. The available options for this node corresponds to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.save_model"><em>PyCaret save_model</em> function options</a> (except the <em>estimator</em> parameter which is pass as input of this node).</td><td>model</td><td>-</td></tr></tbody></table>

#### \*\*Optimize Node

When clicking on an **Optimize** Node, it opens a subflow like below where you can build pipelines for optimization.

<figure><img src="../../.gitbook/assets/optimize (3).png" alt=""><figcaption><p>Optimize Node</p></figcaption></figure>

* Available nodes are different from the ones displayed original flow. You will find useful informations about how to use them in [this page of the _PyCaret_ GitBook](https://pycaret.gitbook.io/docs/get-started/functions/optimize). For additional information about the available nodes, please check the [_PyCaret_ _ReadTheDocs_](https://pycaret.readthedocs.io/en/latest/index.html) documentation:
  * **Tune Model** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.tune\_model).
  * **Ensemble Model** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.ensemble\_model).
  * **Blend Models** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.blend\_models).
  * **Stack Models** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.stack\_models).
  * **Calibrate Model** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.calibrate\_model).
* Name of the node is where you can edit the name.
* Green block (I/O nodes) are input and output of the Optimize node. They are movable. To connect them, simply intersect them with your nodes.

### 2. Results Button

This button is used to see the results of the experiment. It is disabled until you run a experiment. Once you have run an experiment, a ._medmlres_ file is created in your scene folder, containing your generated results from the experiment. Infact, if you quit the app your generated results will still be available the next time you open the app.

Once you click on the See result button, you activate the Result Mode. In this mode you can not manipulate the scene in order to build pipelines. The Result Mode only offers you to select the pipelines you want to observe the results from. To quit the Result Mode, simply press again the See results button, which become Results mode on button while Result Mode is activated.

{% hint style="info" %}
See the [Results Panel](learning-module.md#id-3.-results-panel) section for more informations about the results.
{% endhint %}

### 3. Utils Menu

This menu contains different functionalities that can be used to help you build your scene.

| Element                                                                                   | Description                                                                                                                                                          |
| ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Machine Learning type Dropdown ![](<../../.gitbook/assets/ml\_dropdown (1).png>)          | This dropdown allows you to select the type of machine learning you want for your experiment. When changing the type, all settings are reseted.                      |
| <p>Play </p><p><img src="../../.gitbook/assets/play.png" alt="" data-size="original"></p> | This button allows you to run the experiment. You can find additional informations about Running the experiment [here](learning-module.md#id-2.-run-the-experiment). |
| <p>Garbage bin</p><p><img src="../../.gitbook/assets/bin.png" alt=""></p>                 | This button allows you to delete all nodes in the scene.                                                                                                             |
| <p>Save </p><p><img src="../../.gitbook/assets/save.png" alt=""></p>                      | This button allows you to save the scene.                                                                                                                            |
| <p>Load </p><p><img src="../../.gitbook/assets/load.png" alt=""></p>                      | This button allows you to load a scene from a file.                                                                                                                  |

### 4. Minimap

This Minimap allows you to navigate in the scene and to see the nodes that are in the scene.

### 5. Flow Utils

This menu contains different functionalities that interact with the flow section.

* **Plus button**: This button allows you to zoom in the flow section.
* **Minus button**: This button allows you to zoom out the flow section.
* **Square button**: This button allows you to fit the flow section in the view.
* **Lock button**: This button allows you to lock the flow section. When locked, you can't move the flow section.
* **Map button**: This button allows you to show/hide the Minimap.

***

## Example

### 1. Creation of your Pipeline

Drag and drop nodes from the menu and create your own [pipeline(s)](learning-module.md#multiple-pipelines). Here is an example of a simple classification pipeline that takes a dataset, train a _Gradient Boosting Classifier_ model and then, plot the resulting AUC (Area Under the Curve) plot.

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Learning_module_5.png" alt=""><figcaption><p>Simple scene example</p></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/simple_pipe_w_params.png" alt=""><figcaption><p>Parameters</p></figcaption></figure>

</div>

### 2. Run the Experiment

You can run the experiment by clicking on the **Run button**.

<figure><img src="../../.gitbook/assets/Learning_module_6.png" alt=""><figcaption></figcaption></figure>

A progress bar will appear and **when the experiment finishes**:

* A Toast message will confirm that the results has been saved.
* A new file (._medmlres_)  will be generated in your scene folder, containing results related to your scene (you can't open the ._medmlres_ file).
* The _See results_ button will be enabled.

### 3. Results Panel

When clicking on the _See results_ button you will activate the _Result Mode_:

<figure><img src="../../.gitbook/assets/Learning_module_7.png" alt=""><figcaption></figcaption></figure>

As you can see, a panel open in the bottom with different collapsible items:

<figure><img src="../../.gitbook/assets/Learning_module_7_pipe_zoom.png" alt=""><figcaption><p>P<strong>ipeline's Results Viewer</strong></p></figcaption></figure>

They are called **Pipeline's Results Viewer.**\
On the **left**, you can see all the nodes in the pipeline. You can click on those to see associated results.\
On the **right**, you can see a button that [generates a notebook](learning-module.md#3.1-notebook-generation) for the associated pipeline

{% hint style="info" %}
You can also filter which pipeline(s) you want to see in the results panel by checking node in the flow section. Consult the [Pipeline Selection box section](learning-module.md#id-2.-pipelines-selection-box) for more information.
{% endhint %}

#### 3.1 [Notebook ](https://docs.jupyter.org/en/latest/running.html)Generation

The generated file is saved in the notebook folder of the associated scene. You can open it directly from the application by right clicking and selecting _Open in..._ and then _VSCode_ for example.

{% hint style="warning" %}
You have to run an experiment to access this functionality
{% endhint %}

{% hint style="warning" %}
Default code editor is not implemented yet, but coming soon ! 😉
{% endhint %}

<figure><img src="../../.gitbook/assets/Learning_module_13.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/learning_14.png" alt=""><figcaption><p>Automatically Generated Notebook opened in <em>VSCode</em></p></figcaption></figure>

***

## Multiple Pipelines

When building your scene, you can connect multiple nodes to each other, creating multiple pipelines!

### 1. Single VS Multiple Pipelines:

{% tabs %}
{% tab title="Single pipeline" %}
<figure><img src="../../.gitbook/assets/Learning_module_19.png" alt=""><figcaption><p>Single Pipeline Example</p></figcaption></figure>
{% endtab %}

{% tab title="Multiple pipelines" %}
<figure><img src="../../.gitbook/assets/Learning_module_18 (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Learning_module_14 (2).png" alt=""><figcaption><p>Multiple Pipelines Example</p></figcaption></figure>
{% endtab %}
{% endtabs %}

### 2. Pipelines Selection box

Each runnable node has this checkbox on top of the node in results mode. Checked ones and green ones will be displayed in the results panel.

<div>

<figure><img src="../../.gitbook/assets/checkbox_blue (1).png" alt="" width="90"><figcaption><p>Selection box</p></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/checkbox_green (2).png" alt="" width="90"><figcaption><p>Independent selection box</p></figcaption></figure>

</div>

{% hint style="info" %}
**Independent selection box** (green ones) indicates that every pipeline go through this one, so in any case, its gonna show in the associated results.
{% endhint %}

<figure><img src="../../.gitbook/assets/Learning_module_15.png" alt=""><figcaption><p>Pipelines Selection Example</p></figcaption></figure>
