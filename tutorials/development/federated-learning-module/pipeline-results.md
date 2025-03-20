# Pipeline results

{% hint style="info" %}
In this tutorial, we will learn how to visualize the pipeline results, save them, and use them in various formats.
{% endhint %}

## Video tutorial

{% embed url="https://youtu.be/1CPXFI8QV9M" %}

## Visualizing the pipeline results

1. When you run the pipelines, you will see a success message. Then, you can click on the <mark style="color:yellow;">"See Results"</mark> button to view the results.
2. On the top left of the results page, there is a tab to switch between configurations. There are three available types of results:

* **Global Results**: These are the general results on the central server, representing the average results of all clients.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* **Results by Node**: This shows the results for a single client. A drop-down menu at the top allows you to switch between clients.

<figure><img src="../../../.gitbook/assets/List of nodes (6) (1).png" alt=""><figcaption></figcaption></figure>

* **Compare Results**: This type of result allows you to compare results between different clients. You can select the clients you want to compare using the provided options.

<figure><img src="../../../.gitbook/assets/List of nodes (7).png" alt=""><figcaption></figcaption></figure>

## Saving the results

To save the results, you have two options:

1. **Auto Save**: This occurs when you add the "Save Results" node to the pipeline. The node contains a single input field where you specify the name of the file to save the results.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1).png" alt=""><figcaption></figcaption></figure>

1. **Manual Save**: After visualizing the results, you can save them manually by clicking the "Save" button on the results page. When you click the button, an input field will appear for you to enter the name of the file.

<figure><img src="../../../.gitbook/assets/List of nodes (8).png" alt=""><figcaption></figcaption></figure>

The results can be saved in two different formats, and you can visualize them by double-clicking on them directly from the working directory:

<pre class="language-javascript"><code class="lang-javascript"><strong>EXPERIMENTS                          
</strong>    ├───FL                 
        └─── Results  
             └─── results.json       -> json file 
             └─── results.medflres   -> medflres file 
              
</code></pre>

* **JSON Format**

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

* **medflres Format**

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

These options ensure you can easily store and manage your pipeline results.
