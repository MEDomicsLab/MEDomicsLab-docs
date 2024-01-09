---
description: Jan 29 - Feb 12 | Extract Data
---

# Step 2 : Extract data

<figure><img src="../.gitbook/assets/MEDomicsLab-TestingPhase-10.png" alt=""><figcaption><p>Step 2 - Extract Data</p></figcaption></figure>

{% hint style="warning" %}
This step will take a considerable amount of time due to the extraction computation of all the data. If you realize you don't have enough time, we will provide you with the result data for step 3.
{% endhint %}

## About the data

We choose to use the MIMIC database for testing our application because it's the only publicly available multimodal dataset in healthcare field. This dataset contains images, text, time series and regular CSV data.

The way we choose to manipulate this data in order to make it compatible with machine learning models was inspired by the HAIM study, especially for their extraction types we analyzed through their GitHub repository. Indeed, for now we offer one extraction type by modality, which correspond to the ones used in the HAIM study, but we will implement more tools in the future, including the possibility to extract data from DICOM images.

In order to create an interesting experiment that not take too long in every steps of the MEDomicsLab process, we selected a subset of 200 patients and their data for the last year from their last register. The final goal is to predict their mortality. The data we considered for each patient is :&#x20;

* Their images from the MIMIC-CXR-JPG database
* Their laboratory events (time series) from the MIMIC-IV database (we considered a subset of events as in the HAIM study)
* Their chart events (time series) from the MIMIC-IV database (we considered a subset of events as in the HAIM study)
* Their procedure events (time series) from the MIMIC-IV database (we considered a subset of events as in the HAIM study)
* Their radiology notes from the MIMIC-IV-Note database
* Their discharge notes from the MIMIC-IV-Note database&#x20;
* Their demographic data from the MIMIC-IV database (we pre-processed this data from the admission table)

Also, we selected the patients considering these steps :&#x20;

* We only considered patients having at least one image
* We computed entropy from the patient's data distribution by month in the considered time interval (one year from their last register)
* We computed entropy from the patient's data distribution in the different data types considered (images, laboratory events, chart events, procedure events, radiology notes and discharge notes)
* We computed the result of the multiplication of the two normalized entropies, and kept the 100 patients with the best result in the two categories (dead or alive)

## Get the data for this step

{% hint style="info" %}
At this point you must have completed the[ MIMIC data access](mimic-data-access.md) requirements to have access to the data.
{% endhint %}

After you submitted the required documents for the Testing Phase, you must have received en email with a link to a drive space, containing a zip folder. Simply download the folder into your documents, and then follow the tutorial video of the step 2.

## Extract Data

For additionnal informations about the extraction module and the extraction types used in our application, refer to the [Extraction Module tutorials](../tutorials/design/extraction-modules/), and the three pages : [Image Extraction](../tutorials/design/extraction-modules/image-extraction-page.md), [Text Extraction](../tutorials/design/extraction-modules/text-extraction-page.md) and [Time Series Extraction](../tutorials/design/extraction-modules/time-series-extraction-page.md).

## Tutorial Video

{% embed url="https://youtu.be/vIPnv4JBnL0" %}

