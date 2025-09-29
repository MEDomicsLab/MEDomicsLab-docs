---
description: >-
  Here you will find a comprehensive guide to recommended best practices and
  common pitfalls to avoid, ensuring optimal performance and reliable execution
  within the learning module.
icon: triangle-exclamation
---

# DO'S & DON'TS

{% hint style="info" %}
If you prefer a quick summary,  jump to the [table below](dos-and-donts.md#summary) for the key takeaways.
{% endhint %}

### (Not) Using Clean Node

Including a data cleaning step in machine learning pipelines is a foundational requirement for building robust and accurate models. Data cleaning helps transform your data into a structured format that your machine learning algorithms can understand. Using the Clean node and linking it to your Dataset will help remove noise and irrelevant information, enabling models to learn better and enhancing training efficiency. Not using this node will have a negative impact on your model's performance, slower training and a higher risk of overfitting due to noise.

{% hint style="warning" %}
Note that the [Input Module](../../design/input-module/) offers several tools that can replace the Clean node usage.
{% endhint %}

### (Not) Using Split Node&#x20;

Using a split node in your pipeline is highly recommended, as it follows common practices of machine learning, resulting in more reliable estimators, a fair bias-variance trade-off, smaller risk of overfitting, etc. Not including the Split node in your pipeline is equivalent to training a selected machine learning algorithm using a single iteration, resulting in uncertain estimates.

### Using Tags in Split Node

Using Tags in the Split node enables you to stratify your data based on groups, such as institutions, sex, age, etc. This prevents data leakage by ensuring all samples from the same group stay together in either the train or the test set. Before you use Tags, ensure your dataset has either [Column Tags](../../design/input-module/#feature-or-column-tagging-tools) or [Row Tags](../../design/input-module/#sample-or-row-grouping-tools-subset-creation-tool). If no tags were detected, the node will return a warning, and you must manually select a stratification column.

### Random seed

Reproducible results are controlled by the `session_id` parameter, which sets a unique random seed for the entire PyCaret environment. This parameter, which functions identically to Python's `random_seed`, is best configured within the **Dataset** node.

For consistent outcomes across the complete workflow, it is critical that the **`random_seed` option in the Split node matches the `session_id` value**. Using a different value in the Split node will break the chain of reproducibility, making your experiment's results irreproducible.

### Tune Model is ON, but can't define the hyperparameters grid?

In the Train Model node, if you activate the Tune Model option and still do not see any options available, it means that you haven't added any additional Model options. To fix this issue, go to the Model node that you would like to tune, click the add button and select the settings you would like to include in your hyperparameters grid. By default, the option to use PyCaret's default hyperparameters grid will be on. To define your grid, you must deactivate it.

If the **Tune Model** option is activated in the [**Train Model**](training.md#train-model-model-training-and-optimization-node) node but no tuning parameters are visible, the required hyperparameters have not yet been defined. To resolve this:

1. Navigate to the corresponding [**Model Node**](initialization.md#model-node-configure-your-machine-learning-algorithm).
2. Click the **"+"** button to select the specific hyperparameters you wish to tune.
3. By default, the system uses **PyCaret's default tuning grid**. To define a custom grid of values for your selected hyperparameters, you must disable this default option.

### General recommendations

* Save your scene after every change: Changes in the scene are not saved automatically.
* Check your nodes' connections before running the experiment; a missing connection will lead to incomplete results.
* Check our [troubleshooting](../../../troubleshooting.md) page for common errors.

### Summary

The following table summarizes the key recommendations to follow when using the Learning Module.

| Component           | DO'S ✅                                                                                                                                                                                                                                            | DON'TS 🔴                                                                                                                                                                                                                                                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Clean Node          | <p>When using the clean node focus on the following:</p><ul><li>Remove redundant information.</li><li>Manage outliers.</li><li>Handle missing data.</li></ul>                                                                                     | <ul><li>Overcleaning your data</li><li>Ignoring illogical checks (e.g. year of birth> date of death)</li></ul>                                                                                                                                                                               |
| Split Node          | <ul><li>Stratified sampling is recommended for imbalanced data</li><li>Group-based splitting helps prevent data leakage.</li></ul>                                                                                                                | <ul><li>Splitting data before preprocessing</li><li>Small percentage of test data (e.g. small <code>test_size</code> in random subsampling)</li></ul>                                                                                                                                        |
| Train Model Node    | <ul><li>When calibrating, use sigmoid  for small datasets and isotonic for larger datasets.</li><li>Use smaller ensembles (number of estimators) for for high-dimensional data and larger ensembles for tabular data with many samples.</li></ul> | <ul><li>Massive parameter grids waste computational resources on unimportant parameters</li><li>Ensembling when the performance is low increases complexity without benefit.</li><li>In calibration, too many estimators can lead to overfitting and a high cost.</li></ul><p></p>           |
| Combine Models Node | <ul><li>Combine models from different algorithm families (tree-based, distance-based, linear, etc.)</li><li>Blend option is more suitable for smaller datasets while Stack is more fit for larger ones.</li></ul>                                 | <ul><li>The Blend option with method='hard' on uncalibrated models can reduce the ensemble performance.</li><li>Creating large ensembles of very similar models (e.g., multiple tree-based models) using either blending or stacking leads to overfitting and computational waste.</li></ul> |
