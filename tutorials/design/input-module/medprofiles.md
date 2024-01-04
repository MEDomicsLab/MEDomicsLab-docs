---
description: >-
  This component of the input module includes all the necessary tools to enter
  the MEDprofiles process.
---

# MEDprofiles

The MEDprofiles 'Prepare Data' component is accessible on the input module page and looks like this :

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 151754.png" alt=""><figcaption><p>MEDprofiles 'Prepare Data' component</p></figcaption></figure>



## 1. Select the location of your master table data folder

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 153856.png" alt=""><figcaption><p>Select the location of your master table data folder</p></figcaption></figure>

The master table is the entry point of the MEDprofiles process. It is a CSV file that must adhere to the following format:

* Column names must be 'PatientID', 'Date', 'Time\_point', and others must contain '\_'.
* The first line (after columns) must contain 'string' or 'num' in the first position, 'datetime.date' in the second, and 'num' in all others.
* The first column (excluding the first line) must contain strings or integers.
* The second column (excluding the first line) must contain datetime values.
* The third column (excluding the first line) must contain null or integer values.
* The other columns (excluding the first line) must contain numerical values.

If you haven't created a master table yet, this component will allow you to create one. Depending on your actions in the application, a default folder must be selected:

* If you have already generated master tables, the 'master\_tables' folder will be selected.
* If you have generated embeddings using the extraction module, the 'extracted\_features' folder will be selected.
* Otherwise, there will be no default selected folder. In this case, if you want to use the MEDprofiles prepare data component, you will need to explore the extraction module and generate data that adheres to the master table format (refer to the extraction pages tutorials for more information).

## 2. Create or select your master table

This section is divided into two subparts: one for master table creation and the other for master table selection.

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 153936.png" alt=""><figcaption><p>Create or select your master table</p></figcaption></figure>

### 2.1. Create your master table

The list of available CSV files for master table creation will be displayed in the first selector. If the selector indicates 'No CSV files to show,' it means that no CSV files matching the required format are available in your selected folder from the first part.

You need to select the files you want to include in your master table. Afterward, you can choose the name under which you want to save your master table. The default name is 'master\_table.csv.' It's important that your chosen name ends with the CSV extension. If some of your selected files contain columns with type mismatches (for example, if your patient identifiers are numbers in some files and strings in another), a warning will appear, and you won't be able to proceed with master table creation. If this is the case, check your data types.

If everything is in order, you can press the 'Create Master Table' button. Once the master table creation process is complete (which usually takes a few seconds), a message will appear at the bottom of this section, indicating the path where your master table has been generated. Additionally, the selected folder in the first part will be updated to the folder where your master table is located (under DATA/MEDprofiles/master\_tables). This will also update the master table selection (see part 2.2.).

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 160043.png" alt=""><figcaption><p>Create or select your master table after master table creation</p></figcaption></figure>

### 2.2. Select your master table

Here, you only need to select a master table from the list of available master tables in your chosen folder. If the selector indicates 'No CSV files to show,' it means that no CSV files matching the required format are available in your selected folder from the first part.

## 3. Create MEDclasses

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 160420.png" alt=""><figcaption><p>Create MEDclasses</p></figcaption></figure>

Once you have selected your master table, you will be able to press the 'Create MEDclasses' button. The process analyzes your selected master table and creates the classes that will be associated with your MEDprofiles.

{% hint style="info" %}
The classes will be created based on the column names of the master table.
{% endhint %}

{% hint style="info" %}
In the master table, the column names adhere to the format 'className\_attributeName'.
{% endhint %}

{% hint style="warning" %}
If the 'Create MEDclasses' button is disabled, make sure you have selected a master table in section 2.
{% endhint %}

While the process of MEDclasses creation is done, the created classes will be registered under 'DATA/MEDprofiles/MEDclasses' and will be displayed in the application as follows :

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 160500.png" alt=""><figcaption><p>Generated MEDclasses</p></figcaption></figure>

## 4. Instantiate MEDprofiles

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 161417.png" alt=""><figcaption><p>Instantiate MEDprofiles</p></figcaption></figure>

Once all the previous steps have been successfully completed (master table selection and MEDclasses creation), you can instantiate your master table data as MEDprofiles using the generated MEDclasses. You can choose the name under which you want your data to be registered. It is important that the filename ends with the '.pkl' extension.

The process of instantiating MEDprofiles data may take a few minutes. While the process is running, a progress bar will be displayed, indicating the advancement of the process.

{% hint style="warning" %}
If the button "Instantiate MEDprofiles" is disabled, make sure you have selected a master table in the section 2. and generated MEDclasses in section 3.
{% endhint %}

## 5. Visualize your MEDprofiles data

<figure><img src="../../../.gitbook/assets/Capture d&#x27;écran 2023-12-11 162147.png" alt=""><figcaption><p>Visualize you MEDprofiles data</p></figcaption></figure>

To open the MEDprofiles figure, you need to select the folder containing the MEDclasses and the corresponding binary MEDprofiles file. The selected elements are updated as you complete the previous steps, and they also detect elements matching the required format in case you already have the necessary data to open the MEDprofiles figure.

{% hint style="warning" %}
If either of the two elements (MEDclasses folder and/or MEDprofiles binary file) doesn't contain elements to select, ensure that the previous steps have been completed successfully.
{% endhint %}
