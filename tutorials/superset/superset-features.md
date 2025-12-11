---
description: >-
  This page goes through all the superset features and provides information on
  how to use them.
---

# Superset Features

### Connect to Other Databases

{% hint style="info" %}
Pro Tip: Ensure you have installed the proper database driver(s) for your database before attempting to establish the connection. You can find more details [here](https://superset.apache.org/docs/configuration/databases).
{% endhint %}

Superset provides users with a streamlined way to connect to various remote databases, including SQLite, PostgreSQL, and more. This feature enables the integration of remote data for creating dashboards and visualizing charts.

In MEDomicsLab, after [launching Superset](./#launch-superset-button), you can easily connect to any remote database via the "Connect a Database" interface. To access this, navigate to _**Settings -> Database Connections**_

<figure><img src="../../.gitbook/assets/SupersetAddConnection (1).png" alt=""><figcaption><p>How to open Database Connections Interface</p></figcaption></figure>

Once the interface is open (see image below), select your desired database—this tutorial uses PostgreSQL as an example.

<figure><img src="../../.gitbook/assets/ConnectDatabseInterface.PNG" alt=""><figcaption><p>Database Connections Interface</p></figcaption></figure>

Then enter your database credentials, such as the host, port, username, and other required details. Refer to the image below for guidance.

<figure><img src="../../.gitbook/assets/ConnectDatabseSteps.png" alt=""><figcaption><p>Connection interface to PostgreSQL through Superset</p></figcaption></figure>

Once you hit and _**CONNECT**_, you should  see a confirmation message as depicted below:

<figure><img src="../../.gitbook/assets/ConnectDatabseSuccess.png" alt=""><figcaption><p>Successful connection to database</p></figcaption></figure>

If you encounter an error, please refer to the [Superset documentation](https://superset.apache.org/docs/configuration/databases) for guidance on troubleshooting the issue. Should the problem persist, feel free to [reach out to us](../../forms/contact-us.md) for further assistance.

### Explore & Visualize

To explore data from your connected dataset, you can use either SQL Lab or the "Add Dataset" option, as illustrated in the figure below:

* _**SQL Lab**_: Provides a complete preview of the data, displays column data types, and allows for custom SQL queries on the dataset.

<figure><img src="../../.gitbook/assets/SQLLab.png" alt=""><figcaption><p>SQL Lab depiction</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/SQLLabSaveDataset.png" alt=""><figcaption><p>How to save the output data of your SQL query</p></figcaption></figure>

* _**Add new dataset**_: Lets you explore the columns and their data types, with the ability to create charts based on the data if needed.

<figure><img src="../../.gitbook/assets/CreateNewDataset.png" alt=""><figcaption><p>Steps to create a dataset and a chart from a connected database</p></figcaption></figure>

### Create Dashboards

One of the main features of Superset is charts and dashboard creation. It offers a no-code procedure for building charts quickly. To do so:

* Create a new dashboard:

<figure><img src="../../.gitbook/assets/NewDashboard.png" alt=""><figcaption><p>Create new dashboard steps</p></figcaption></figure>

* Create a new chart and add it to the dashboard:

<figure><img src="../../.gitbook/assets/newChart.png" alt=""><figcaption><p>Create new chart and add it to a dashboard</p></figcaption></figure>



### Export Data to Workspace

Superset enables data exportation through SQL Lab. This empowers users to further process and explore their data within MEDomicsLab by leveraging the different tools available.

<figure><img src="../../.gitbook/assets/ExportToWS.png" alt=""><figcaption><p>Export data to your local workspace</p></figcaption></figure>

### Useful resources

* How to [configure your Superset](https://superset.apache.org/docs/configuration/configuring-superset)?
* [Connect to a database](https://superset.apache.org/docs/configuration/databases).
* How to [use Superset](https://superset.apache.org/docs/using-superset/creating-your-first-dashboard) (dashboard creation, data exploration, etc.)
* [FAQ](https://superset.apache.org/docs/faq)

