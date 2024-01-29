---
description: >-
  The MEDprofiles figure may be open through the MEDprofiles Accordion in the
  Input Module, as 'MEDprofiles Viewer'.
---

# MEDprofiles Viewer

{% embed url="https://www.youtube.com/watch?v=3xRqnlpjgBM" %}
MEDprofiles Viewer Video Tutorial
{% endembed %}

**Content**

Introduction [0:00](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=0s)

Open the MEDprofiles viewer [0:16](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=16s)

Presentation of the MEDprofiles viewer [0:34](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=34s)

Zoom In on your figure [1:07](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=67s)

Separate Horizontally tool [2:07](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=127s)

Separate Vertically tool [2:35](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=155s)

Make your data relative to a class [2:56](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=176s)

Set time points to selected data points [3:56](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=236s)

Export time points to CSV [4:57](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=297s)

Set time points by classes [6:03](https://www.youtube.com/watch?v=3xRqnlpjgBM\&t=363s)

***

The _MEDprofiles Viewer_ can be accessed through the _Input Module_, provided you have a MEDclasses folder and a MEDprofiles binary file. To obtain these two components, refer to the [MEDprofiles](./) section.

&#x20;The _MEDprofiles viewer_ looks like this:

<figure><img src="../../../../.gitbook/assets/Capture d&#x27;écran 2024-01-29 114910.png" alt=""><figcaption><p>MEDprofiles Viewer with 200 patients</p></figcaption></figure>

The figure displays MEDprofiles data by classes and dates, with each patient represented by a unique color.

## 1. Figure Tools

The figure provides several tools. Sliders in both axes allow you to narrow down your view. Additional tools are located at the upper right of the figure:

* **Zoom:** Allows you to zoom in on your figure by selecting an area.
* **Zoom Reset:** Takes a step back in zoom if you've made multiple zooms and want to revert to the previous view.
* **Restore:** Retrieves the original figure view.
* **Save as Image:** Allows you to download your figure as a PNG file.
* **Horizontally Select:** Enables the selection of data points between specific dates on the X-axis.
* **Clear Selections:** Clears your horizontal selections.

## 2. Right Panel Tools

Several tools have been implemented in the right panel to assist you in defining time points in your figure.

* **Separate Horizontally:** Separates overlapping points on a class axis by moving them slightly.
* **Separate Vertically:** Separates all points by patients, displaying an axis per patient class.
* **Select the Class for Relative Time:** Aligns all patient data by setting time relative to the first data point of the selected class for each patient. The X-axis represents the time between the first data point of the selected class and other patient points.
* **Set Time Points to Selected Data Points:** Attributes the selected time point to the points chosen in the figure through horizontal selection.
* **Set Time Points by Classes:** Attributes the selected time point to the chosen classes.
* **Merge Time Points by Patient:** If checked during time point export, all patient data will be merged using the selected method (default is mean) to obtain at most one line per patient in each time point CSV file.
* **Export Time Points to CSVs:** Exports your data associated with time points as CSV files under the MEDprofiles folder. One CSV file is generated per time point.

