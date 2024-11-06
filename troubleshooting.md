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

<summary>LightGBM Model is taking forever to train</summary>

This is a common issue in Ubuntu that occurs when training a lightGBM  model using `n_jobs=-1`. When you set `n_jobs=-1`, the process can sometimes hang or slow down due to how the library manages parallel threads on certain systems. Here are some common reasons for this behavior:

1. **CPU Thread Saturation**: Setting `n_jobs=-1` tells LightGBM to use all available CPU cores. On Linux systems, particularly with high core counts, this can overwhelm the CPU scheduler, leading to inefficient thread management, especially if other processes are running concurrently.
2. **OpenMP Configuration**: LightGBM uses OpenMP for parallelism, and certain configurations of OpenMP on Linux can lead to deadlocks or excessive thread contention. This issue can be specific to how OpenMP handles threads in certain Linux distributions, including Ubuntu. More details here: [https://lightgbm.readthedocs.io/en/latest/FAQ.html#lightgbm-hangs-when-multithreading-openmp-and-using-forking-in-linux-at-the-same-time](https://lightgbm.readthedocs.io/en/latest/FAQ.html#lightgbm-hangs-when-multithreading-openmp-and-using-forking-in-linux-at-the-same-time)
3. **Memory Bandwidth and Latency**: Using all CPU cores can lead to high memory bandwidth consumption. If LightGBM needs more memory per thread than available, this can slow down training significantly. Lowering the `n_jobs` setting reduces the number of simultaneous threads and can help manage memory load.
4. **Compatibility with Specific Libraries**: LightGBM's multithreading may not work smoothly with all versions of system libraries on Ubuntu, such as `libgomp` (GNU OpenMP). Sometimes, upgrading or downgrading certain libraries (e.g., `libgomp1`) can resolve this issue.

#### Solutions:

* **Limit `n_jobs`**: Set `n_jobs` to a smaller number (e.g., 4 or 8), which often yields good performance without overloading the system.
* **Upgrade/Downgrade System Libraries**: Update your OpenMP libraries.

You can test different `n_jobs` values to find the optimal setting, which balances speed and stability.

</details>

<details>

<summary>How to update to the latest release ? </summary>

## 1. Uninstall the application first

### Ubuntu

In a terminal, write the following command:

```bash
sudo apt remove medomicslab-application
```

if you had installed the v0.0.1

```bash
sudo apt remove medapp
```

***

### MacOS

Go in your Applications Folder in Finder.

Then, click on the MEDomicsLab Icon while holding the `Ctrl` key.

Finally, click on "Move to Trash"

![](<.gitbook/assets/image (21) (1).png>)&#x20;



***

### Windows

Go to Settings > Apps

![](<.gitbook/assets/image (16) (1).png>)&#x20;

Then, click on "Installed Apps"

<img src=".gitbook/assets/image (17) (1).png" alt="" data-size="original">

Search for "MEDomicsLab"

<img src=".gitbook/assets/image (18) (1).png" alt="" data-size="original">

Click on the `...` and finally click on "Uninstall" &#x20;

<img src=".gitbook/assets/image (20) (1).png" alt="" data-size="original">

## 2. Reinstall the application

Now, you can follow the same instructions you followed for your first installation [here](quick-start.md).

**Don't worry, the Python Environment installation won't be as long as the first time.**



</details>
