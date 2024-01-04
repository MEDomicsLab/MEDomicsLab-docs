# 🤕 Troubleshooting

<details>

<summary>Go server not working ?</summary>

* Check if anaconda3 or miniconda3 exists
* Check if conda environnement exists
  * Open a conda terminal
  * `conda env list`
  * Do you see a conda environnement named med\_conda\_env ?
    * yes ? Check environnement variable MED\_ENV on your system
    * no ? Did you make this step -> [#2.-unzip-the-python-environment-installer-1](quick-start.md#2.-unzip-the-python-environment-installer-1 "mention")

</details>

<details>

<summary>Go server is working properly but i got errors when clicking on process buttons</summary>

Your python environnement could have problems.

#### Test the environnement variable MED\_ENV

on WINDOWS:\
open a cmd terminal( `🪟 + cmd`) and write `set MED_ENV`&#x20;

on LINUX and MACOS:\
Open a terminal and write `echo $MED_ENV`

**It should print a path to where your** [**conda** ](https://www.anaconda.com/)**env is installed.** \
If not:&#x20;

</details>
