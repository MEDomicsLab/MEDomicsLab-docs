---
description: >-
  This page documents the evaluation of the federated model based on our
  centralized model.
icon: '4'
---

# Evaluation Module for Federated Learning

The federated learning evaluation workflow is not yet fully integrated into the MEDomics graphical interface. Therefore, the evaluation and comparison of federated models must currently be performed using an external Python script.

For PoC3, the federated model is trained externally using **MEDfl**, while the evaluation procedure is reproduced outside MEDomics using the `evaluate_models.py` script. This script enables users to:

* load and compare centralized and federated models;
* correctly inject the federated weights into the PyCaret model used for inference;
* apply the same preprocessing pipeline to the evaluation datasets;
* compute performance metrics including AUC, accuracy, recall, precision, and F1-score;
* generate confusion matrices;
* perform SHAP-based feature importance analysis for selected hospitals.

This external workflow provides a temporary bridge between **MEDomics** and **MEDfl** until federated learning evaluation becomes directly available within the MEDomics interface.

For a detailed explanation of the evaluation procedure, required files, model preparation, metrics, generated outputs, and instructions for running the script, please refer to the following complementary [documentation](https://usherbrooke-my.sharepoint.com/:b:/g/personal/kalm7073_usherbrooke_ca/IQCn4Hja3DeeQaY_VJyC5Na7ATgCPVvRQGdMV0F3juIyq9U?e=Vmm1fb).

Thank you for taking the time to review this proof of concept!
