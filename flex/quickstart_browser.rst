.. include:: ../substitutions.txt
.. |smp| replace:: ``Absolute Fleximeter Sample File 1.h5``
.. |smprep| replace:: ``Absolute Fleximeter Sample Report 1.pdf``
.. |instr| replace:: ``flex``
.. |instrn| replace:: Absolute Fleximeter

Quick Start: Browsing an |instrn| file
======================================
This Demo will guide you through the data analysis of an |instrn| output file. 

.. include:: ../browser/quickstart/opening.txt
.. include:: ../browser/quickstart/config.txt

==============================
Interacting with the Data Plot
==============================

The :ref:`navigator` tree is the gate to the most important actions you can perform on the data plot. 

In order to plot one more dataset (for example the temperature setpoint):

#. Right-click on the dataset you wish to plot on the Navigator tree (``/kiln/S``). 
#. Select the **Plot** action from the context menu.

The same apply for removing a dataset and all its related objects from the plot. The Plot action will be checked if the curve is visible, unchecked if not visibile.

The setpoint curve plot is now referred to its own axis labelled *S (°C)*. To better compare temperature and setpoint, it is useful to refer the setpoint plot to the temperature axis:

#. Right-click on the setpoint curve on the Data Plot window. Select **Properties** from the context menu. 
#. A new dialog window opens, listing all the properties of the plotted curve. Search for the bold **Y axis** entry. 
#. Change **Y axis** from **ax:S** to **ax:T**. The curve will be immediately referred to the *T (°C)* axis.

The *S (°C)* axis loses its scale (it's now from 0 to 1). It's no longer useful, so you can hide it: 

#. Right-click on the *S (°C)* axis, select **Properties**. 
#. The first entry is **Hide**. Check the checkbox. The axis disappears.

You can freely move any axis by clicking on it and dragging.

------------------------------
Viewing flexion in micron unit
------------------------------
The ``/flex/sample0/d`` dataset represents flexion. It is recorded in microns and automatically converted to percentile on dataset loading, but is frequently useful to analyze it as an absolute value in microns. The percentile is calculated towards the distance between the flex rods, set before starting the test. 

Follow these steps to convert the curve back to microns:
    
#. Locate the ``d`` (``/flex/sample0/d``) element in the Navigator. #. Right-click and select the flagged action **Percentile**. 
#. A dialog will appear. Click **Apply**. 
#. A new temporary label in the dialog confirms the dataset was created (Done). Click **Close**. 
#. If the curve is currently plotted, you immediately view the effect in the graph. 
#. By right-clicking again on the dataset node the **Percentile** action is now unflagged. 

