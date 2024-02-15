---
description: >-
  The Input module consolidates all the tools necessary for preprocessing
  tabular data.
---

# Input Module

{% embed url="https://youtu.be/tj3qsXLnudk" %}
Video Tutorial of the Input module
{% endembed %}

{% hint style="warning" %}
We are continuously working on enhancing the MEDomicsLab platform, and we'd like to inform you about the upcoming improvements:

* **Definition of Empty Cells:** While we often refer to empty cells as NaN (Not A Number) values, it's important to note that empty does not necessarily mean NaN.
* **Display in Simple Cleaning Tool:** In the _Simple Cleaning tool_, we currently display the percentages of non-NaN values. However, we acknowledge that this can be confusing, and we plan to improve it by showing the percentage of NaN values instead.
* **Cleaning Columns and Rows in Simple Cleaning Tool:** When cleaning columns and rows simultaneously in the _Simple Cleaning tool_, the cleaning is currently done independently, and all the columns and rows displayed in red are removed. We are working on enhancing this tool. Additionally, please be aware that imputation methods are available in the [_Learning Module_](../../development/learning-module.md).
* **Holdout Set Creation Tool:** In the _Holdout Set Creation tool_, the NaN method is applied only to rows that contain NaN values in selected stratified columns. We plan to enhance the NaN handling method by introducing options such as mean fill, median fill, and mode fill.
* **Feature Reduction Tool:** The _Feature Reduction tool_ currently has only basic utilities. We are committed to improving it, including allowing the transportation of PCA (Principal Component Analysis) transformations through the [_Evaluation Module_](../../development/evaluation-module.md).

We appreciate your understanding as we work towards making MEDomicsLab even more effective and user-friendly.
{% endhint %}

**Content**&#x20;

* Introduction [00:00](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=0s)&#x20;
* Merge tool [00:23](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=23s)&#x20;
* Grouping/Tagging tool [04:06](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=246s)
* Simple Cleaning tool [08:07](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=487s)&#x20;
* Holdout Set Creation tool [11:15](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=675s)
* Subset Creation tool [13:43](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=823s)
* Feature Reduction tool [17:30](https://www.youtube.com/watch?v=tj3qsXLnudk\&t=1050s)

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

The _Grouping/Tagging tool_ enables you to create and apply tags to dataset columns. Follow these steps to set tags on dataset columns:

1. Select at least one dataset from the dataset list; you can choose multiple datasets if needed.
2. Create your tags: Press the "+" button to access default tags or type the name of your tag and press "Enter" to add it.
3. Customize your tags: Your created tags are displayed, and you can update, delete, or customize their color (text and background).
4. Select the column(s) on which you want to apply/modify tags. Columns are displayed by dataset.
5. Once the desired column(s) are selected, choose the tag(s) you want to apply.
6. After selecting tags, press the green button. A popup will appear, asking if you want to proceed with the tagging. Press "Yes."
7. Another popup will appear, asking if you want to overwrite existing tags. If you press "Yes" and the selected columns were already tagged, their previous tags will be overwritten.

If you open your dataset in the app, you will then be able to see your tags.

</details>

<details>

<summary>Simple Cleaning tool</summary>

The Simple Cleaning tool assists in removing NaN values from datasets, either by rows or columns. Follow these steps to clean a dataset:

1. Select a dataset from the dataset list, displaying information about NaN values in your dataset.
   1. The first table associates your dataset columns with the number and percentage of non-NaN values. You can order this dataframe by column name or number/percentage of non-NaN values.
   2. The second table associates your dataset rows with the number and percentage of non-NaN values. You can order this dataframe by row index or number/percentage of non-NaN values.
2. Depending on your cleaning preferences, select a percentage of NaN values to consider for dropping columns and/or rows using the corresponding selectors. This will display which columns/rows will be affected and update this data in the two tables by showing the number of columns/rows to be dropped at the head of the "% of non-NaN" column and highlighting the concerned rows in red.
3. Choose a name and extension for your result dataset. The default name is your selected CSV file with the "\_clean" extension.
4. Press the "Create a clean copy" button.&#x20;

Your result dataset will be saved in the same directory as your selected dataset.

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

The Subset Creation tool enables the creation of a subset of rows from a dataset by applying filters to columns. Follow these steps to create a subset:

1. Select a dataset from the dataset list. Your dataset will be displayed, allowing you to sort and filter each column.
2. You can filter your dataframe by clicking the filter icon at the right of the header of each column. Create rule(s) using the displayed components to filter columns. Rows that don't satisfy the rules will be removed from the displayed dataset, updating the number of rows displayed under the dataset.
3. You can make a global search in the dataframe using the search component at the top right of the displayed dataframe.
4. You can clear your filters by pressing the "Clear" button at the top left of the displayed dataframe.
5. Choose a name and extension for your result dataset. The default name is your selected CSV file with the "\_filtered" extension.
6. Press the "Create subset from filtered rows" button.

Your result dataset will be saved in the same directory as your selected dataset.

</details>

<details>

<summary>Delete Columns tool</summary>

The Delete Columns tool allows you to create a subset from a dataset by specifying the columns you want to retain. Follow these steps to delete columns from a dataset:

1. Select the dataset from which you want to delete columns in the "Select the dataset" section. Your dataset will be presented in a table within the Accordion component.
2. In the "Select the columns to keep" section, choose the columns you wish to retain from your dataset. By default, all columns are selected, and you only need to unselect the ones you want to delete. The "Columns selected" number at the bottom right of the displayed dataset will be updated accordingly.
3. Provide a name for saving the new dataset. The default name is your selected dataset name followed by the "\_modified" suffix.
4. Click the "Create subset from selected columns" button.

Your new dataset will be saved at the same location as your selected dataset.

</details>

<details>

<summary>Transform Columns tool</summary>

The Transform Columns tool enables you to modify columns in a dataset, either by converting selected columns into binaries or by replacing missing cells with zeros. Here's how to use this tool:

1. Select the dataset from which you want to transform columns in the "Select the dataset" section. Your dataset will be displayed in a table within the Accordion component.
2. In the "Select the columns to keep" section, choose the columns you want to transform from your dataset. By default, all columns are selected. Make sure to unselect the ones you don't want to apply the transformation to. The "Columns selected" number at the bottom right of the displayed dataset will be updated accordingly.
3. Choose the type of transformation you need in the "Choose the type of transformation" section:
   * Binary: Empty cells become zeros, and non-empty cells become ones.
   * NaN to 0: Empty cells become zeros, and others remain the same.
4. Provide a name for saving the new dataset. The default name is your selected dataset name followed by the "\_modified" suffix.
5. Click the "Create subset with the transformed columns" button.

Your new dataset will be saved at the same location as your selected dataset.

</details>

{% content-ref url="feature-reduction-tool.md" %}
[feature-reduction-tool.md](feature-reduction-tool.md)
{% endcontent-ref %}

{% content-ref url="medprofiles/" %}
[medprofiles](medprofiles/)
{% endcontent-ref %}
