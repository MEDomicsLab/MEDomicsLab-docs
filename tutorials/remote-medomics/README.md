---
description: >-
  A recently implemented feature of MEDomics allowing it to connect to a remote
  workspace, hosted on a server.
---

# 🛜 Remote MEDomics

{% hint style="info" %}
This section acts as an introduction to the new architecture used in MEDomics to allow the usage of remote workspaces.&#x20;

* If you are a **user** and want a quick start guide on how to use MEDomics remotely, check out the [Connection Tutorial subpage](connection-tutorial.md).
* If you are a **developer** looking for documentation about the current implementation of the remote-compatible architecture, check out the [Development subpage](development/) and its own subpages.
{% endhint %}

A big part of the work done on MEDomics over the last year was to split the all-in-one app into two components without affecting the current functonalities :

<figure><img src="../../.gitbook/assets/image (106).png" alt="A schema showing which components are included in the lightweight client (Electron) and the server (NodeJS, MongoDB, Python, GO and Jupyter), as well as the possibility to use both combined as an all-in-one app."><figcaption></figcaption></figure>

This implied a refactor of where the components are located, as well as how they communicate with each other, in order to allow the server to be on a different computer than the client in use-cases where we would want to access a workspace already instanciated elsewhere without having to move data or to redownload the full package.

#### Electron Client:

* Acts as the front-end of the app and has been modified to be aware of whether it is being used in a remote or local workspace.
* Through SSH tunnels, the client can make requests to Express, Go and MongoDB or load pages through iFrames for servers like Jupyter, D-Tale and SweetViz.
* Can install the backend server both remotely (after connecting to a remote computer using SSH through the app) or locally (if the lightweight version without the server is downloaded).

#### NodeJS Server:

* Is downloadable and usable remotely through a separate GitHub release from the client (look for "server-vX.X.X" tags).
* Express is at the base of the backend, controlling servers (GO, MongoDB, Jupyter, etc.) and storing their status (as well as the ports they are running on) to ensure a centralized entry-point.
* "Hosts" the workspace, and thus has the code to manage them and their files.

The fact that the MEDomics was at first designed to be only used locally means a lot of work had (and still has) to be done to transform the app into using this architecture. The transition is not yet fully complete and still needs some quirks ironed out, so if you find new bugs or issues related to this refactor in the new versions of the app, please [report the issue here](../../forms/report-an-issue.md), [contact us directly](../../forms/contact-us.md) or [open a GitHub discussion thread](https://github.com/MEDomicsLab/MEDomics/discussions).
