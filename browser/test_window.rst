.. include:: ../substitutions.txt
Test Window
==================================
The |m| Test Window opens in Browser's tabs once a test has been selected. 

Its appearance is very similar to the :ref:`live_acquisition` window, with a central area displaying a plot and a lateral area showing test configurations and data Navigator.

The values contained in the configuration tabs (Measure, Sample 0...n, Thermal Cycle) are the ones recorded at the end of the test.

---------------------
Basic Plotting and Embedding
---------------------
At the opening of the test, a standard plot is displayed. In order to interact with this plot, switch to ``Results`` tab in the left panel.

You can operate on the plot with the usual Navigator functions (un/plotting a curve, smoothing, deriving, etc). You can also create a test report on a new plot page. 

Once you are satisfied by your plot, you can permanently save into the test file. 

* From ``Measure`` menu, click on ``Plots`` submenu.
* Select ``Save new plot``. Give a name to your plot.
* Your new plot will appear in the ``Plots`` submenu.

Saved plots can be recalled, overwriting any current plot.

---------------------
Re-evaluation of scripts
---------------------
The logic by which characteristic or important points are identified during the test is saved onto the test file. Through the Browser it is possible to change and replay this logic, for research purposes. 

The replay is accessible from the  ``Measure`` menu, at the ``Re-evaluate standards`` action. All affected values will be recalculated. 

---------------------
Versioning
---------------------

It is possible to change any configuration option and any metadata and save everything in a new test ``version``, and multiple versions can be saved in each test file. The original data is cannot be modified or removed from a test file.

Versioning allows, for example, to correct the test name, or add a comment, or manually edit characteristic shapes. To save a new version, starting from a file containing only the original data:

1. Do your changes to any configuration option
2. Click on ``Measure`` menu -> ``Version`` -> ``New version``
3. A dialog box will ask the label of the new version. 

After a new version is created, the ``Version`` menu will show an additional, checked item below the ``Original`` one. 
The active version will be overwritten by clicking ``Save configuration`` from the same Version menu. 

The ``Original`` version cannot be overwritten. A new version name is asked if attempting to do so.
