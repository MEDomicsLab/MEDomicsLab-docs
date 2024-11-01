# Crash tutorial

{% hint style="info" %}
On this page, we will apply everything we've covered in the previous tutorials. We will start from scratch and guide you through the final steps of viewing and saving the results.
{% endhint %}

## Video tutorial

{% embed url="https://youtu.be/pFXtTte8BjY?si=6JXBdeW4ge75ccWg" %}

## Steps&#x20;

### 1. Creating the workspace:&#x20;

When you first open the MedomicsLab application, you see this window where we can view our previously created workspaces. In my case, there is an old workspace, but if you are new to this application, you should click the 'Set workspace' button and choose a folder. It's preferable to choose an empty folder.

<figure><img src="../../../.gitbook/assets/List of nodes (10).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

### 2. Uploading Datasets:

&#x20;For this experience, we will need a dataset to run the pipelines, so we need to add the datasets to the workspace.

For our example, we will use the [Diabetes dataset](https://drive.google.com/drive/folders/1i3kGKTxq-1XulRQNU7iKksYs2fGGzCAj?usp=sharing). Make sure to download the files, and once you have them, add them to the DATA folder and refresh the workspace.\


{% hint style="warning" %}
MEDfl supports numerical tabular datasets. If you want to test your dataset, ensure it is compatible and clean. It's always preferable to start the tutorial with our provided dataset for consistency.
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

### 3. Configuring Database:&#x20;

When you first open MEDfl, you'll see a popup containing instructions on how to create a configuration file. This file will be used to connect to the MySQL database on your local machine.

To get started, create a file named `config.ini` in your workspace and add your connection information, including the username and password.

for more details about configuring the database feel free to check [the configuration tutorial page ](configure-database.md)

```ini
[mysql]
host = localhost
port = 3306
user = YOUR_SQL_USERNAME
password = YOUR_PASSWORD
database = MEDfl
```

<figure><img src="../../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

### 4. Optimizing hyperparameters:&#x20;

Before we create the pipeline, we can optimize the model hyperparameters to improve performance.&#x20;

{% hint style="info" %}
After the optimization, we can use the results to initialize the central model hyperparameters.
{% endhint %}

For our example, we will use the Optuna central optimization to optimize the hyperparameters. MEDfl offers various options for optimization, so feel free to check the[ Optimization tutorial page](hyperparameters-optimization.md) for more details.

<figure><img src="../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

After Having the optimization results we will save them, so we can use them later&#x20;

\


<figure><img src="../../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

### 5. Creating and running pipelines&#x20;

for this experience, we will create two configurations and run them simultaneously, each configuration will have a different aggregation algorithm \
for more details on how to create the pipeline and add the different nodes please check [this tutorial page  ](create-pipelines.md)\


<figure><img src="../../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

### 6. Pipeline results&#x20;

After the execution of the pipelines, you will have the option to see results by clicking on the <mark style="color:yellow;">"See results"</mark> button ![](<../../../.gitbook/assets/image (2).png>).

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

&#x20;You can switch between different configuration results and also between different types of results. There are mainly three types of results: <mark style="color:yellow;">Global results, results by node, and compare results</mark>.&#x20;

{% hint style="info" %}
For more details about the results, refer to the [Pipeline Results tutorial page](pipeline-results.md).
{% endhint %}

To save the results, click on the "Save" button and an input field will appear where you can enter the file name ![](<../../../.gitbook/assets/image (2) (1).png>). After confirming, two types of files will be created, and you can open them directly by clicking on them.&#x20;

### 7. Merge results&#x20;

In this section, we will merge two different result files into one file containing both sets of results.

&#x20;You have the option to add the "Merge Results" node separately from the pipeline, or you can link it to the pipeline so that the pipeline results will be automatically merged with the specified file.
