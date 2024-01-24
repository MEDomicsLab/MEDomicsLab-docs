---
description: >-
  The Input module consolidates all the tools necessary for preprocessing
  tabular data.
---

# Input Module

<details>

<summary>Merge tool</summary>

The _Merge tool_ functions as a visual representation of the _pandas_ Python library merge function ([https://pandas.pydata.org/docs/reference/api/pandas.merge.html](https://pandas.pydata.org/docs/reference/api/pandas.merge.html)). Follow these steps to merge dataframes:

1. Select your first dataset from the dataset list.
2. Choose a column for merging your dataset. Other dataset(s) you select should contain a column with the same name.
3. Select the columns you wish to retain from your first dataset, including the merge column. By default, all columns are selected.
4. Choose a second dataset (Dataset #1) from the list. It must contain a column with the same name as the one selected for merging.
5. Select the merge type. For additional information about merge types, consult the _pandas_ documentation ([https://pandas.pydata.org/docs/reference/api/pandas.merge.html](https://pandas.pydata.org/docs/reference/api/pandas.merge.html)).
6. Choose the columns you want to retain from your second dataset. By default, only the merge column is selected.
7. (Add other datasets by pressing the "+" button.) (Not necessary)
8. Provide a name for your result dataset and choose a file extension.
9. Click the "Merge" button.

If you don't specify a name for your result dataset, it will be named "mergedDataset" by default. Your merged dataset is saved in the same folder as your first dataset.

</details>

<details>

<summary>Grouping/Tagging tool</summary>



</details>

<details>

<summary>Simple Cleaning tool</summary>



</details>

<details>

<summary>Holdout Set Creation tool </summary>

The Holdout Set Creation tool serves as a visual representation of the _scikit-learn_ Python package's _model\_selection train\_test\_split_ function ([https://scikit-learn.org/stable/modules/generated/sklearn.model\_selection.train\_test\_split.html](https://scikit-learn.org/stable/modules/generated/sklearn.model\_selection.train\_test\_split.html)). Follow these steps to create a holdout set:

1. Choose the dataset for which you want to create the holdout set from the displayed list.
2. If the Shuffle option is selected, rows will be shuffled before the split.
3. If Shuffle is selected, you can also choose to Stratify the holdout set based on selected columns. Refer to the documentation for additional information ([https://scikit-learn.org/stable/modules/generated/sklearn.model\_selection.train\_test\_split.html](https://scikit-learn.org/stable/modules/generated/sklearn.model\_selection.train\_test\_split.html)).
4. Select the size of your holdout set as a percentage of your chosen dataset size.
5. Choose how to handle NaN values in your selected dataset if necessary.
6. Provide a name for the folder of  your resulting datasets (learning and holdout) and select a file extension.
7. Click the "Create holdout set" button.

The function will generate two datasets based on your selected options: a learning set and a holdout set. These datasets will be saved in a folder with the specified name, located in the same directory as your selected dataset.

</details>

<details>

<summary>Subset Creation tool</summary>



</details>

{% content-ref url="feature-reduction-tool.md" %}
[feature-reduction-tool.md](feature-reduction-tool.md)
{% endcontent-ref %}

{% content-ref url="medprofiles/" %}
[medprofiles](medprofiles/)
{% endcontent-ref %}
