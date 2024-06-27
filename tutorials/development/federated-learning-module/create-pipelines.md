# Create pipelines

{% hint style="info" %}
In this tutorial, we will learn how to create and run federated learning pipelines using the Federated learning module
{% endhint %}

## Introduction

Using the Federated Learning module, you can create and run your own pipelines by simply dragging and dropping nodes onto the open map. The application offers the flexibility to create multiple configurations and run them simultaneously.

In the next video, we will demonstrate how to create your configurations, verify them, and launch the execution.\


## Video tutorial

{% embed url="https://youtu.be/WR5IC0aVMZ8" %}

## Steps

1. Add your nodes and link each one with their respective inputs and outputs. If you need more details about the role of each node, you can refer to the[overview.md](../../../overview.md "mention") page where you'll find a table containing all the details.

{% hint style="info" %}
Each node must be configured properly to ensure the execution runs smoothly. Make sure to fill in all the required fields for each node.

The two last nodes ( saved results and merge results ) are optional and you can run your pipeline without adding them
{% endhint %}



<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

When you click on the network node, you will see the space where you can create your federated network

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

2. Run the pipeline: to run the pipeline you need to click the button <img src="../../../.gitbook/assets/image (10).png" alt="" data-size="line">, after that a new popup will appear to check your configurations

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

3. Add a New Configuration: The application allows users to add multiple configurations. To do this, simply add more nodes of the same type with different configurations. The system will count the number of possible paths to create the final configurations.

{% hint style="info" %}
in my example, I will add a new FL Strategy node with a different aggregation algorithm
{% endhint %}

<figure><img src="../../../.gitbook/assets/List of nodes (4) (1).png" alt=""><figcaption></figcaption></figure>

Now when we click the button run pipeline we can see a tab showing two configurations

<figure><img src="../../../.gitbook/assets/List of nodes (5).png" alt=""><figcaption></figcaption></figure>

4. Run pipelines: to tun the pipeline click the <mark style="color:yellow;">**"Run pipeline"**</mark> Button and you will see a progress bar showing the progress of the execution

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

In the next tutorial, we will see how to visualize and save results!&#x20;
