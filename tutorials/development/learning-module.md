---
description: This is where the magic happens 🧙🪄
---

# Learning Module

{% hint style="info" %}
The Learning Module is constructed using the open-source Python library [_PyCaret_](https://pycaret.gitbook.io/docs/). You can find valuable information about [_PyCaret_](https://pycaret.gitbook.io/docs/) at the following links:

* [_PyCaret_ Gitbook](https://pycaret.gitbook.io/docs/)
* [_PyCaret_ ReadTheDocs](https://pycaret.readthedocs.io/en/stable/)
* [_PyCaret_ GitHub](https://github.com/pycaret/pycaret)
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

To create a scene, follow these steps:

1. Click on the Learning Module Icon.  <img src="../../.gitbook/assets/icon (2).png" alt="" data-size="line">
2. Click on the "Create scene" button.
3. Enter a name for the new scene.

The application will generate a folder that includes:

* Your scene (._medml_ file).
* A folder for your scene models.
* A folder for your scene notebooks.

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
The _Add options_ button opens a panel where you can select additional options. These options are automatically generated from the online [ReadTheDocs documentation of _PyCaret_](https://pycaret.readthedocs.io/en/stable/).
{% endhint %}

{% hint style="info" %}
The links we use to explain the _PyCaret_ specific functions refer to the [Classification section of the _PyCaret_ documentation](https://pycaret.readthedocs.io/en/latest/api/classification.html). However, please note that these functions are also present in other machine learning types within _PyCaret_. For instance, you can find them in the [Regression documentation of _PyCaret_ as well](https://pycaret.readthedocs.io/en/latest/api/regression.html).
{% endhint %}

<table data-full-width="true"><thead><tr><th width="219">Node</th><th width="468.5">Description</th><th width="135">Input</th><th>Output</th></tr></thead><tbody><tr><td><img src="../../.gitbook/assets/dataset (2).png" alt="" data-size="original"></td><td><p>This serves as the starting point for an experiment.</p><p>You have two options here:</p><ol><li><strong>MEDomicsLab Standard:</strong> This option takes files from a learning folder, which may represent the learning set from static .<em>csv</em> files obtained through the <a href="../design/input-module/medprofiles/"><em>MEDprofiles</em> process</a>. The node automatically detects files that match the format and displays them in a dropdown selector. You then need to choose which column from your selected .<em>csv</em> file(s) should be the target for prediction. If you select more than one file, all the selected files should have the same target column.</li><li><strong>Custom File:</strong> You can choose any .<em>csv</em> file from the dropdown selector displaying all your .<em>csv</em> files from your workspace. Then, you need to choose which column from your selected .<em>csv</em> file should be the target for prediction.</li></ol><p>The available options for this node correspond to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.setup"><em>PyCaret</em> setup function options</a> that are not directly related to data cleaning.</p></td><td>-</td><td>Dataset</td></tr><tr><td><img src="../../.gitbook/assets/clean (2).png" alt="" data-size="original"></td><td>This node enables you to clean your dataset. The available options for this node correspond to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.setup"><em>PyCaret</em> setup function options</a> that are directly related to data cleaning.</td><td>Dataset</td><td>Dataset</td></tr><tr><td><img src="../../.gitbook/assets/model.png" alt="" data-size="original"></td><td>This node allows you to select a model and its associated parameters. It corresponds to the estimator parameter of the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.create_model"><em>PyCaret</em> create_model function</a>. The models are directly sourced from the <a href="https://scikit-learn.org/stable/"><em>scikit-learn</em></a> package. In fact, if you are seeking documentation about a specific model parameter, you will find it in the <a href="https://scikit-learn.org/stable/"><em>scikit-learn</em></a> documentation.</td><td>-</td><td>Model_config</td></tr><tr><td><img src="../../.gitbook/assets/train.png" alt="" data-size="original"></td><td>This node allows you to train a model. The available options for this node correspond to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.create_model"><em>PyCaret</em> create_model function options</a> (except the <em>estimator</em> parameter, which is defined through the Model node).</td><td>Model_config AND Dataset</td><td>Model</td></tr><tr><td><img src="../../.gitbook/assets/compare (1).png" alt="" data-size="original"></td><td>This node allows you to train and evaluate the performance of all estimators available in the <a href="https://pycaret.gitbook.io/docs/get-started/functions/train#model-library"><em>PyCaret</em> model library</a> using cross-validation. The available options for this node correspond to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.compare_models"><em>PyCaret</em> compare_models function options</a>.</td><td>Dataset</td><td>Model(s)</td></tr><tr><td><img src="../../.gitbook/assets/load_model (1).png" alt="" data-size="original"></td><td>This node allows you to load a model from a file. It takes as input a model from the ones you saved in your scene, displayed in a dropdown selector. The available options for this node are the ones available in the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.load_model"><em>PyCaret</em> load_model function</a>, except the model name, which is replaced by the selected file.</td><td>Dataset</td><td>Model</td></tr><tr><td><img src="../../.gitbook/assets/optimize (2).png" alt="" data-size="original"></td><td>This node allows you to optimize a model. It is different from the other nodes as, when clicking on it, it opens a subflow containing other nodes. It gathers the <a href="https://pycaret.gitbook.io/docs/get-started/functions/optimize">optimization functions of <em>PyCaret</em></a>.**</td><td>Model</td><td>Model</td></tr><tr><td><img src="../../.gitbook/assets/analyze.png" alt="" data-size="original"></td><td>This node allows you to analyze a model. It gathers the <a href="https://pycaret.gitbook.io/docs/get-started/functions/analyze">analysis and model explainability functions of <em>PyCaret</em></a>. For now, only the <a href="https://pycaret.gitbook.io/docs/get-started/functions/analyze#plot_model">plot_model function</a> is implemented in our application.</td><td>Model</td><td>-</td></tr><tr><td><img src="../../.gitbook/assets/finalize.png" alt="" data-size="original"></td><td>This node allows you to finalize a model. The available options for this node correspond to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.finalize_model"><em>PyCaret</em> finalize_model function options</a> (except the <em>estimator</em> parameter, which is passed as input to this node).</td><td>Model</td><td>Model</td></tr><tr><td><img src="../../.gitbook/assets/save_model.png" alt="" data-size="original"></td><td>This node allows you to save a model. The available options for this node correspond to the <a href="https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.save_model"><em>PyCaret</em> save_model function options</a> (except the estimator parameter, which is passed as input to this node).</td><td>Model</td><td>-</td></tr></tbody></table>

#### \*\*Optimize Node

When clicking on an Optimize Node, it opens a subflow as shown below, allowing you to construct pipelines for optimization.

<figure><img src="../../.gitbook/assets/optimize (3).png" alt=""><figcaption><p>Optimize Node</p></figcaption></figure>

The available nodes differ from those displayed in the original flow. You can find useful information on how to use them on this page of the [_PyCaret_ GitBook](https://pycaret.gitbook.io/docs/). For additional information about the available nodes, please refer to the [_PyCaret_ ReadTheDocs](https://pycaret.readthedocs.io/en/stable/) documentation:

* **Tune Model** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.tune\_model).
* **Ensemble Model** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.ensemble\_model).
* **Blend Models** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.blend\_models).
* **Stack Models** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.stack\_models).
* **Calibrate Model** documentation is available [here](https://pycaret.readthedocs.io/en/latest/api/classification.html#pycaret.classification.calibrate\_model).

The name of the node is where you can edit the name. The green blocks (I/O nodes) represent the input and output of the Optimize node. They are movable, and to connect them, simply intersect them with your nodes.

### 2. Results Button

This button is used to view the results of the experiment. It is disabled until you run an experiment. Once you have run an experiment, a ._medmlres_ file is created in your scene folder, containing the generated results from the experiment. In fact, if you quit the app, your generated results will still be available the next time you open the app.

Once you click on the _See results_ button, you activate the _Result Mode_. In this mode, you cannot manipulate the scene to build pipelines. The _Result Mode_ only allows you to select the pipelines you want to observe the results from. To exit the _Result Mode_, simply press the _See results_ button again, which becomes the _Results mode on_ button while the Result Mode is activated.

{% hint style="info" %}
Refer to the [Results Panel](learning-module.md#id-3.-results-panel) section for more information about the results.
{% endhint %}

### 3. Utils Menu

This menu contains different functionalities that can be used to help you build your scene.

| Element                                                                                                          | Description                                                                                                                                                         |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Machine Learning type dropdown <img src="../../.gitbook/assets/ml_dropdown (1).png" alt="" data-size="original"> | This dropdown allows you to select the type of machine learning you want for your experiment. When changing the type, all settings are reset.                       |
| <p>Play </p><p><img src="../../.gitbook/assets/play.png" alt="" data-size="original"></p>                        | This button allows you to run the experiment. You can find additional information about running the experiment [here](learning-module.md#id-2.-run-the-experiment). |
| <p>Garbage bin</p><p><img src="../../.gitbook/assets/bin.png" alt="" data-size="original"></p>                   | This button allows you to delete all nodes in the scene.                                                                                                            |
| <p>Save </p><p><img src="../../.gitbook/assets/save.png" alt="" data-size="original"></p>                        | This button allows you to save the scene.                                                                                                                           |
| <p>Load </p><p><img src="../../.gitbook/assets/load.png" alt="" data-size="original"></p>                        | This button allows you to load a scene from a file.                                                                                                                 |

### 4. Minimap

This minimap allows you to navigate the scene and visualize the nodes present in it.

### 5. Flow Utils

This menu contains various functionalities that interact with the flow section.

| Element                                                                                              | Description                                                                                    |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| <p>Plus Button </p><p><img src="../../.gitbook/assets/plus.png" alt="" data-size="original"></p>     | This button allows you to zoom in the flow section.                                            |
| <p>Minus Button </p><p><img src="../../.gitbook/assets/minus.png" alt="" data-size="original"></p>   | This button allows you to zoom out the flow section.                                           |
| <p>Square Button </p><p><img src="../../.gitbook/assets/square.png" alt="" data-size="original"></p> | This button allows you to fit the flow section in the view.                                    |
| <p>Lock Button </p><p><img src="../../.gitbook/assets/lock.png" alt="" data-size="original"></p>     | This button allows you to lock the flow section. When locked, you can't move the flow section. |
| <p>Map Button </p><p><img src="../../.gitbook/assets/map.png" alt="" data-size="original"></p>       | This button allows you to show/hide the minimap.                                               |

***

## Example

### 1. Creation of your Pipeline

Drag and drop nodes from the menu to create your own [pipeline(s)](learning-module.md#multiple-pipelines). Here is an example of a simple classification pipeline that takes a dataset, trains a Gradient Boosting Classifier model, and then plots the resulting AUC (Area Under the Curve) plot.

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Learning_module_5.png" alt=""><figcaption><p>Simple scene example</p></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/simple_pipe_w_params.png" alt=""><figcaption><p>Parameters</p></figcaption></figure>

</div>

### 2. Run the Experiment

You can execute the experiment by clicking on the _Run_ button.

<figure><img src="../../.gitbook/assets/Learning_module_6.png" alt=""><figcaption></figcaption></figure>

A progress bar will appear, and upon completion of the experiment:

* A Toast message will confirm that the results have been saved.
* A new file (._medmlres_) will be generated in your scene folder, containing results related to your scene (you can't open the ._medmlres_ file).
* The _See results_ button will be enabled.

### 3. Results Panel

When you click the _See Results_ button, you will activate the _Result Mode_.

<figure><img src="../../.gitbook/assets/Learning_module_7.png" alt=""><figcaption><p>Result Panel</p></figcaption></figure>

As you can see, a panel opens at the bottom with various collapsible items:

<figure><img src="../../.gitbook/assets/Learning_module_7_pipe_zoom.png" alt=""><figcaption><p>P<strong>ipeline's Results Viewer</strong></p></figcaption></figure>

They are called the **Pipeline's Results Viewer**.

On the **left**, you can see all the nodes in the pipeline. You can click on them to view associated results.

On the **right**, there is a button that generates a notebook for the associated pipeline.

{% hint style="info" %}
You can also filter which pipeline(s) you want to see in the results panel by checking the nodes in the flow section. Refer to the [Pipeline Selection box section](learning-module.md#id-2.-pipelines-selection-box) for more information.
{% endhint %}

#### 3.1 [Notebook ](https://docs.jupyter.org/en/latest/running.html)Generation

The generated file is saved in the notebook folder of the associated scene. You can open it directly from the application by right-clicking and selecting "Open in..." and then choosing, for example, _VSCode_.

{% hint style="warning" %}
You need to run an experiment to access this functionality.
{% endhint %}

{% hint style="warning" %}
The default code editor is not implemented yet, but it's coming soon! 😉
{% endhint %}

<figure><img src="../../.gitbook/assets/Learning_module_13.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/learning_14.png" alt=""><figcaption><p>Automatically Generated Notebook opened in <em>VSCode</em></p></figcaption></figure>

***

## Multiple Pipelines

When constructing your scene, you can connect multiple nodes to each other, creating multiple pipelines!

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

Each runnable node has a checkbox on top of the node in results mode. Checked nodes, especially those in green, will be displayed in the results panel.

<div>

<figure><img src="../../.gitbook/assets/checkbox_blue (1).png" alt="" width="90"><figcaption><p>Selection box</p></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/checkbox_green (2).png" alt="" width="90"><figcaption><p>Independent selection box</p></figcaption></figure>

</div>

{% hint style="info" %}
The **independent selection box** (green ones) indicates that every pipeline goes through this node. Therefore, it will always be shown in the associated results.
{% endhint %}

<figure><img src="../../.gitbook/assets/Learning_module_15.png" alt=""><figcaption><p>Pipelines Selection Example</p></figcaption></figure>
