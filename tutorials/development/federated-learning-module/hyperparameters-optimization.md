# Hyperparameters optimization

{% hint style="info" %}
In this tutorial, we will learn how to use MEDfl to optimize the hyperparameters of the model and apply them effectively.
{% endhint %}

## Introduction

We will explore how to use **MEDfl** to optimize the hyperparameters of your machine-learning models. [Hyperparameter optimization](https://en.wikipedia.org/wiki/Hyperparameter\_optimization) is a crucial step in enhancing the performance of your models. MEDfl provides robust tools to streamline this process, allowing you to fine-tune your models efficiently. By the end of this tutorial, you will understand how to leverage **MEDfl** for hyperparameter optimization and utilize the optimized parameters to improve your model's accuracy and effectiveness.&#x20;

**Let's get started!**

## Video tutorial

{% embed url="https://youtu.be/q3__0SdatiA" %}



## Optimization methods&#x20;

MEDfl gives the possibility to optimize hyperparameters with 3 different methods&#x20;

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

* **Grid Search Optimization**: A straightforward method where the user specifies a list of metrics to optimize, such as the number of layers, hidden size, and others.

<figure><img src="../../../.gitbook/assets/image (14).png" alt="" width="257"><figcaption></figcaption></figure>

* **Optuna Central Optimization**: Utilizes Optuna to optimize parameters on the central server. Users can specify Optuna parameters like metric, direction, optimization algorithm, and intervals for each hyperparameter.

<figure><img src="../../../.gitbook/assets/image (15).png" alt="" width="247"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

* **Optuna Federated Optimization**: Uses Optuna for hyperparameter optimization in a federated manner. Optimization occurs during the execution of the federated pipeline, adapting parameters based on distributed data.

## Run optimization

To run the optimization click on the run button and a new popup will show to verify the optimization configuration then click the button <mark style="color:yellow;">"Optimize hyperparameters"</mark>

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

After running the optimization you will see a progress bar showing the progress of the execution&#x20;

<figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

## Optimization results&#x20;

Once the execution is completed a popup will show the results&#x20;

* GRID SEARCH results : The results contains the best score and best hyperparameters&#x20;

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

* Optuna Results: The results contain the best score and best hyperparameters and some statistical graphs&#x20;

<figure><img src="../../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

## Save Optimization results&#x20;

MEDfl allows users to save the optimization results into files and visualize them on separate screens. This feature helps in easily tracking and analyzing the performance of different hyperparameter configurations.

to save the results click on the button "Save results" and an input will show to give the file name&#x20;

<figure><img src="../../../.gitbook/assets/List of nodes (9).png" alt=""><figcaption></figcaption></figure>

The application will save two files under the specified name (JSON and medflopt) in the "optimization" folder.

<pre><code><strong>EXPERIMENTS                          
</strong>    ├───FL                 
        └─── Optimization
             └─── optimization_results.json       -> json file 
             └─── optimization_results.medflopt   -> medflres file
</code></pre>

{% hint style="info" %}
You can visualize the file by double-clicking on them directly
{% endhint %}
