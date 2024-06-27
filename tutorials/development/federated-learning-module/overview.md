# Overview

{% hint style="info" %}
This page provides an overview of the Federated Learning module in <mark style="color:blue;">**MEDomicsLab**</mark>, offering insights into both the application's interface and the backend package employed for conducting experiments.
{% endhint %}

## Introduction

The Federated Learning Module in <mark style="color:purple;">**MEDomicsLab**</mark> simulates the process of federated learning and allows for training models in a decentralized manner using multiple datasets. This approach preserves privacy and enhances data security by ensuring that data never leaves its original location.

#### Key Aspects of the Federated Learning Module:

* **Decentralized Training**: Models are trained across multiple nodes without transferring raw data.
* **Privacy Preservation**: Utilizing techniques like differential privacy to ensure data confidentiality.
* **Hyperparameter Optimization**: Tools to automatically tune and optimize model hyperparameters for improved performance.
* **Transfer learning**: Allowing the user to use pre-trained models to initialize the central server to improve the model performance&#x20;

## Video Tutorial

{% embed url="https://youtu.be/7vQFheeRvp4" %}

## MEDfl package

The Federated Learning module in the <mark style="color:purple;">**MEDomicsLab**</mark> application uses **MEDfl** in the backend, a standalone Python package designed for simulating federated learning.&#x20;

You can also use MEDfl independently from the app to create your networks and pipelines directly with code. Below is a brief example demonstrating how to do that.

```bash
# install MEDfl 
pip install MEDfl
```

<pre class="language-python"><code class="lang-python"><strong># import MEDfl
</strong><strong>import MEDfl 
</strong><strong>
</strong><strong># ... import the rest of the dependencies here 
</strong><strong>
</strong><strong># Create a network "Net_1"
</strong>Net_1 = Network(name="Auto_Net")
Net_1.create_network()

# Create a MasterDataSet from Net_1
Net_1.create_master_dataset()

# FLsetup creation
autoFl  = FLsetup(name = "Flsetup_1", description = "The first fl setup",network = Net_1)
autoFl.create()

# Create node 
hospital = Node(name="hospital_1", train=1)
Net_1.add_node(hospital)
hospital.upload_dataset("hospital_1"+'_dataset', base_url + '/notebooks/data/nodesData/output_1'+'.csv')

# Create FLDataSet
fl_dataset = autoFl.create_federated_dataset(
                output="deceased",
                fit_encode=[],
                to_drop=["deceased"]
 )


# Load the pre-trained model
model = Model.load_model("../../notebooks/.ipynb_checkpoints/trainedModels/grid_search_classifier.pth")


# Create the strategy
aggreg_algo = Strategy(config['aggreg_algo'],
                                   fraction_fit=1.0,
                                   fraction_evaluate=1.0,
                                   min_fit_clients=2,
                                   min_evaluate_clients=2,
                                   min_available_clients=2,
                                   initial_parameters=global_model.get_parameters())
aggreg_algo.create_strategy()

# Create The server
server = FlowerServer(global_model,
                                  strategy=aggreg_algo,
                                  num_rounds=server_rounds,
                                  num_clients=len(fl_dataset.trainloaders),
                                  fed_dataset=fl_dataset,
                                  diff_privacy=config['dp_activate'],
                                  # You can change the resources located for each client based on your machine
                                  client_resources={
                                      'num_cpus': 1.0, 'num_gpus': 0.0}
                                  )
# Create the pipeline
ppl_1 = FLpipeline(name="the second fl_pipeline",
                               description="This is our first FL pipeline",
                               server=server)
            
# Run the Training of the model
history = ppl_1.server.run()

# Test the model 
report = ppl_1.auto_test()
   

</code></pre>

For more detailed examples, you can check the tutorials on the GitHub repository.

## Application Interface

The interface of the MEDfl module in the MEDomicsLab application provides a user-friendly space where you can visually manage and connect multiple nodes to create your federated learning pipelines. Each node type in the interface has a specific role and attributes, allowing you to build and customize your federated learning networks seamlessly.

<figure><img src="../../../.gitbook/assets/List of nodes (2).png" alt=""><figcaption></figcaption></figure>

Below is a table explaining the role and attributes of each node:

<table><thead><tr><th width="198">Node </th><th width="410">Description</th><th width="124">input</th><th>Output</th></tr></thead><tbody><tr><td><img src="../../../.gitbook/assets/image (25).png" alt="" data-size="original"></td><td><p>The <strong>Dataset Node</strong> is where you specify the master dataset for your experiment. The master dataset is used differently based on the type of network you create:</p><ul><li><strong>Auto Network</strong>: The master dataset is split between the different created nodes based on a specified column value.</li><li><strong>Manual Network</strong>: The master dataset is used to validate the schema of the dataset selected for each node.</li></ul><p>To select a master dataset, click on the "Select Dataset" button, choose the file, and specify the target of the dataset.</p></td><td>/</td><td>Dataset</td></tr><tr><td><img src="../../../.gitbook/assets/image (26).png" alt="" data-size="original"></td><td>The <strong>Network Node</strong> is responsible for creating the federated network. A new screen will appear when you click on it, displaying additional node types: the Client Node and the Server Node. You will have the option to add multiple clients and a central server that will aggregate the results.</td><td>Dataset</td><td>Network</td></tr><tr><td><img src="../../../.gitbook/assets/image (27).png" alt="" data-size="original"></td><td>The <strong>FL Setup Node</strong> is responsible for configuring the federated learning setup. The user only needs to specify the name and description of the setup.</td><td>Network</td><td>Flsetup</td></tr><tr><td><img src="../../../.gitbook/assets/image (28).png" alt="" data-size="original"></td><td><p></p><p>The <strong>FL Dataset Node</strong> creates the federated dataset, which generates train, test, and validation loaders from the clients' datasets. To create a federated dataset, the user must specify two parameters:</p><ul><li><strong>Validation fraction</strong>: The fraction of the data used for validation.</li><li><strong>Test fraction</strong>: The fraction of the data used for testing.</li></ul></td><td>Flsetupt</td><td>FL dataset</td></tr><tr><td><img src="../../../.gitbook/assets/image (29).png" alt="" data-size="original"></td><td><p></p><p>The <strong>Model Node</strong> is responsible for creating the model that initializes the federated learning process. The user has several options based on whether they activate or deactivate transfer learning:</p><ul><li><strong>Transfer Learning Activated</strong>: Specify a pre-trained model and additional parameters such as optimizer and learning rate.</li><li><p><strong>Transfer Learning Deactivated</strong>: Choose between two options:</p><ol><li>Use custom models provided by MEDfl, specifying parameters like the number of layers, hidden size, optimizer, and learning rate. Optionally, parameters can be filled using results from a hyperparameter optimization experiment.</li><li>Create a model from scratch using a code editor to define a custom model.</li></ol></li></ul></td><td>FL datatset</td><td>model</td></tr><tr><td><img src="../../../.gitbook/assets/image (30).png" alt="" data-size="original"></td><td><p>The <strong>Optimize Node</strong> is responsible for hyperparameter optimization. Users can optimize hyperparameters using the following methods:</p><ul><li><strong>Grid Search Optimization</strong>: A straightforward method where the user specifies a list of metrics to optimize, such as the number of layers, hidden size, and others.</li><li><strong>Optuna Central Optimization</strong>: Utilizes Optuna to optimize parameters on the central server. Users can specify Optuna parameters like metric, direction, optimization algorithm, and intervals for each hyperparameter.</li><li><strong>Optuna Federated Optimization</strong>: Uses Optuna for hyperparameter optimization in a federated manner. Optimization occurs during the execution of the federated pipeline, adapting parameters based on distributed data.</li></ul><p>For more details on Optuna, you can find additional information <a href="https://optuna.org/">here</a>.</p></td><td>Model + Dataset</td><td>Model</td></tr><tr><td><img src="../../../.gitbook/assets/image (31).png" alt="" data-size="original"></td><td><p></p><p>The <strong>FL Strategy Node</strong> is responsible for creating the server strategy to aggregate and manage the network it contains. This includes defining:</p><ul><li><strong>Aggregation Algorithm</strong>: A list of algorithms from the <a href="https://flower.ai">Flower</a> package.</li><li><strong>fraction_fit</strong>: The fraction of clients sampled for training the model.</li><li><strong>fraction_evaluate</strong>: The fraction of clients sampled for model evaluation (validation).</li><li><strong>min_fit_clients</strong>: The minimum number of clients sampled for training in each round.</li><li><strong>min_evaluate_clients</strong>: The minimum number of clients sampled for evaluation in each round.</li><li><strong>min_available_clients</strong>: The minimum required number of available clients to initiate a federation round.</li></ul></td><td>Model</td><td>fl strategy</td></tr><tr><td><img src="../../../.gitbook/assets/image (32).png" alt="" data-size="original"></td><td>The <strong>Train Model Node</strong> is used to define the client resources for training, specifying whether to utilize GPU or CPU resources during the training process.</td><td>flstrategy</td><td>train results</td></tr><tr><td><img src="../../../.gitbook/assets/image (34).png" alt="" data-size="original"></td><td>The <strong>Train Model Node</strong> is used to define the client resources for training, specifying whether to utilize GPU or CPU resources during the training process.</td><td>train results</td><td>save results</td></tr><tr><td><img src="../../../.gitbook/assets/image (35).png" alt="" data-size="original"></td><td>This node is used to merge two or more results files into one file</td><td>save results / none</td><td></td></tr></tbody></table>

