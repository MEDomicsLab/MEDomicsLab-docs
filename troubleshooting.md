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

<summary>Go server is working properly but I got errors when clicking on process buttons</summary>

Your python environnement could have problems.

#### Test the environnement variable MED\_ENV

on WINDOWS:\
open a cmd terminal( `🪟 + cmd`) and write `set MED_ENV`&#x20;

on LINUX and MACOS:\
Open a terminal and write `echo $MED_ENV`

**It should print a path to where your** [**conda** ](https://www.anaconda.com/)**env is installed.** \
If not:&#x20;

</details>

<details>

<summary>MacOS: the app does not want to launch and/or the app seems buggy when opening multiple <strong>tabs</strong>. <em>KNOWN ISSUE FOR MAC USERS AT UNIVERSITÉ DE SHERBROOKE WITH THE TRELLIX ANTIVIRUS.</em></summary>

Problem description:&#x20;

The app seems to be stuck at startup. Or after startup, when opening multiple tabs (e.g. two different csv files), the app turns all white.&#x20;

***

Probable cause:&#x20;

If you have an insitutitonal antivirus like Trellix at Université de Sherbrooke, we believe the firewall of Trellix prevents MEDomicsLab to run properly. We hope the problem will be solved once we certify (signing Mac software) the MEDomicsLab app with Apple (_work in progress_).

***

Workaround:&#x20;

If you encounter a similar issue, and you have an antivirus installed on your computer, we recommend that you disable it when using MEDomicsLab. For Mac users at Université de Sherbrooke with Trellix, one way to momentarily disable the utilities of Trellix is to:

1. Go to _System Settings_, _Privacy & Security,_ _Full Disk Access_.
2. Disable the following six extensions: _fmpd_, _VShieldScanManager_, _VShieldScanner_, _masvc_, _TrellixEndpointSecurity_, _TrellixNetworkExtension_.
3. Restart yur computer.

Of course, once you are done working with MEDomicsLab, we recommend you enable again your antivirus! For Mac users at Unversité de Sherbrooke with Trellix, this would mean to enable again the six extensions above, and to restart your computer.&#x20;

</details>

<details>

<summary>How to update to the latest release ? </summary>

1. Go to the releases on the GitHub page
2. Uninstall the application first&#x20;
   1.
3. &#x20;

</details>
