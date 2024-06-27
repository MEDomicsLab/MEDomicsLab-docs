# Configure database

{% hint style="info" %}
In this tutorial, we will learn how to configure the database connection
{% endhint %}

## Introduction

**MEDfl** uses a **MySQL** database to store configurations and results. To configure this setup on your local machine, you'll need to set the configuration file to establish the connection with MySQL.

## Video tutorial

{% embed url="https://youtu.be/vME_fV_jWfA" %}

## Steps:&#x20;

{% hint style="info" %}
Once you open the MEDfl window you will see a popup window containing the instructions on how to create the config file
{% endhint %}

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

1. Create `config.ini` inside the `DATA` directory&#x20;

<pre class="language-javascript"><code class="lang-javascript"><strong>  DATA                             -> DATA folder
</strong>    ├───config.ini                 -> config file 
    └─── ...  
</code></pre>

1. modify the `config.ini content`  &#x20;

```ini
[mysql]
host = localhost
port = 3306
user = YOUR_SQL_USERNAME
password = YOUR_PASSWORD
database = MEDfl
```

3. Click on the <mark style="color:orange;">**"DB config file"**</mark>  button, select your file, and upon successful configuration, you will see a success message confirming that the setup is complete.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
