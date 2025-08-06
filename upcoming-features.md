---
description: Explore the upcoming implementations in the next releases.
icon: bullhorn
---

# Upcoming features

## Superset

<figure><img src=".gitbook/assets/Superset_logo.svg.png" alt="" width="188"><figcaption></figcaption></figure>

[Apache Superset](https://superset.apache.org/) is an open-source modern data exploration and visualization platform, loaded with options that make it easy for users of all skill sets to explore and visualize their data, from simple line charts to highly detailed ones. The MEDomics platform will integrate direct access to Superset, eliminating the need for multiple installations and making MEDomics a comprehensive, all-in-one solution for modeling and visualizing heterogeneous data in medicine.

## MEDfl

<figure><img src=".gitbook/assets/MEDomicsLabNoShadowNoText100.png" alt=""><figcaption></figcaption></figure>

In the upcoming releases, the MEDomics platform will offer a graphical implementation of the [Federated Learning](https://en.wikipedia.org/wiki/Federated_learning) package [MEDfl](https://github.com/MEDomics-UdeS/MEDfl). This module, part of the development layer, represents the third major component in MEDomics’s toolset, enabling simulated federated learning to support collaborative model training across multiple sites without sharing raw data. By facilitating decentralized training, this module enhances data privacy and security, empowering researchers and developers to build, refine, and deploy federated learning models directly within the platform.

**Key Aspects of the Federated Learning Module:**

* **Decentralized Training**: Models are trained across multiple simulated nodes without transferring raw data.
* **Privacy Preservation**: Utilizing techniques like differential privacy to ensure data confidentiality.
* **Hyperparameter Optimization**: Tools to automatically tune and optimize model hyperparameters for improved performance.
* **Transfer Learning**: Allows the user to use pre-trained models to initialize the central server, enhancing model performance.

## MED3pa

<figure><img src=".gitbook/assets/MEDomicsLabNoShadowNoText100.png" alt=""><figcaption></figcaption></figure>

The MEDomics platform will also offer a graphical implementation of the [**MED3pa** ](https://github.com/MEDomics-UdeS/MED3pa)package. It is designed to address critical challenges in deploying machine learning models, particularly focusing on the robustness and reliability of models under real-world conditions. It provides comprehensive tools for evaluating model stability and performance in the face of **covariate shifts**, **uncertainty**, and **problematic data profiles**.

**Key Functionalities**

* **Covariate Shift Detection**: Utilizing the _Detectron_ sub-package, MED3pa can identify significant shifts in data distributions that might affect the model’s predictions. This feature is crucial for applications such as healthcare, where early detection of shifts can prevent erroneous decisions.
* **Uncertainty and Confidence Estimation**: Through the med3pa subpackage, the package measures the uncertainty and predictive confidence at both individual and group levels. This helps in understanding the reliability of model predictions and in making informed decisions based on model outputs.
* **Identification of Problematic Profiles**: MED3pa analyzes data profiles that consistently lead to poor model performance. This capability allows developers to refine training datasets or retrain models to handle these edge cases effectively.
