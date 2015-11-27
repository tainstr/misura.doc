.. include:: substitutions.txt

.. _live_acquisition:

Live Acquisition
==================

The Live Acquisition software allows to carry on any kind of measurement available on a Misura platform. 

This section describes basic concepts, functionalities and procedures which are general enough to be applicable to any measurement. 

More specific instructions can be found in :ref:`measurement_apps` sections dedicated to each instrument.
    
.. contents:: How to run a test
   

.. _live_connect:
    
Connecting 
-----------

When you first launch Acquisition software, you have to select a server to connect to. From the **Connect** menu, choose **Server** sub-menu and **Open** action. 

An input dialog will let you specify the server protocol, IP, port and path. In a normal environment, the server address will be:

    https://172.16.8.68:3880/RPC

A username and a password will be prompted, and saved for any future connection to that machine. 

Saved connections will be displayed both as items in the **Recent servers** box on the welcome page of Live Acquisition, and as **Connect**->**Server** menu items.

Time synchronization
^^^^^^^^^^^^^^^^^^^^^^^^
The time between instrument and client computer is kept synchronized. The user may periodically see a warning message upon connection, asking to re-synchronize times. If replied positively, the instrument will restart for synchronization. 

It's up to the user keep the client's computer time up-to-date, manually or by using exact time services.

When connecting from multiple clients, you should keep all client synchronized at the same time, to avoid multiple re-sync. 


.. _live_init:
    
Initializing the Measurement App
---------------------------------

After a successful connection you will be shown a list with available :ref:`measurement_apps`, a button for each instrument. Click the corresponding button to select your desired instrument.

Once the instrument is selected, the machine will start its setup, also called *measurement morphing*.

A "Pending Tasks" dialog will appear in the left panel, showing some details about what is happening.

This operation can take up to a couple of minutes, depending on the instrument. Any interaction with the application is discouraged until when the dialog disappears.

Once the initialization is complete, the application will display all relevant controls needed to configure, start and follow the execution of the test.

The menu bar contains:
    * **Connect**: to connect to a different machine or to change measurement app. 
    * **Measure**: allows to re-initialize the instrument from zero, set a delayed start, hide/show user interface components (Test Configuration, Storyboard, Data Plot, Data Table, Log Window), Reload Data from the instrument, Quit client.
    * **Settings**: gives access to advanced configuration panels for the **Instrument** itself, its individual **Devices**, or the full **Global** configuration.
    * **Help**: client configuration, documentation link opening the documentation you are reading, the :ref:`pending_tasks` dialog, the software information dialog.

On the left side of the window you find a tabbed **Test Configuratio** area, showing:
    * **Status** tab: contains short summary of the current test condition. The first two options shows if a test is running (data recording) and if the thermal control is active. They are underlined in green when not active, in red when running. Then follows information on test name and test duration (if running); the furnace position if motorized; temperatures, setpoint and power output. More sample-dependent option can be shown based on the active measurement app. 
    * **Measure** tab: generic test configurations can be made (starting and stopping conditions) and metadata can be viewed (eg: maximum temperature reached)
    * **Thermal Cycle** tab: allows to define the thermal cycle and preview it
    * **Sample<N>** tabs: one tab for each sample defined in the analysis.
    * **Results** tab: empty until the start of the test. Will be populated with tools for :ref:`live_interact`.
        
On the bottom, a bar showing: 
    * **Focus** slider and spin-box, to adjust the focus distance. 
    * **Furnace:** option to view and control furnace position (Opened/Closed). Only available if furance is motorized.
    

.. _live_config: 
    
Configuring the test
----------------------

The following paragraphs explain common procedures or concepts needed to carry out any test with |m|.

Moving the furnace
^^^^^^^^^^^^^^^^^^^
The first step of test configuration is placing the sample in the right position. If the furnace is motorized, you should always open it by using the option **Is the furnace closed?** in the Status tab, or the **Furnace:** box in the bottom bar. That option should be changed to the desired position: *Closed* or *Opened*. Once the sample is positioned and correctly framed, it is advisable to close the furnace using the same option, and proceed with test configuration.

Measure and Sample names
^^^^^^^^^^^^^^^^^^^^^^^^^^^
The test name can be directly set in the Status panel, or in the Measure tab. 

This is the name of your measurement, but the sample (and each sample) can have a different name. Sample names can be set in their Sample<N> tab, in *Name* option.

The test name should identify the kind of measurement, while the sample name should identify the material the measurement method is applied to. You will be able to recall the both test name and sample name from the :ref:`database`.
    
For simplicity you can just set the test name to a string identifying both the kind of test and the sample name, and leave the sample name field to the default value (`Sample N. 0`).
    
The test name will also be used as the output file name. If a file with the same name already exists, it will be postfixed with `_<N>`, where `<N>` will be increased until an unique name exists (`measure`, `measure_1`, `measure_2`, etc).

Thermal cycle 
^^^^^^^^^^^^^^
The **Thermal Cycle** tab in the Test Configuration area allows to load a thermal cycle preset or to design a new one. Refer to :ref:`thermal_cycle` for a detailed explanation.

Additional test termination options can be configured in the Measure and Sample sections, depending on the :ref:`measurement_app` you are using. 


.. _live_start:

Starting the test
-------------------

Once the test is completely configured, the sample positioned and the furnace moved to its intended initial position, you can start it by clicking on **Start** button in the upper-left toolbar. A confirmation dialog will ask you to review the Status panel. By confirming, the test will start. 

.. _delayed_start:
Delayed start
^^^^^^^^^^^^^^
To schedule a test to start at a specified date in the future, you can use the **Delayed start** feature, available from the **Measure** menu. 

The Delayed Test Start dialog will appear with the options needed to control its behaviour. 

* **Enable delayed start**: click on the checkbox to engage the delayed start. When the configured time is reached, the test will automatically start.
* **Delayed start date**: Set date and time when the test will start. 

Then 3 fields allows to understand how and when the test will be started.
* **Target instrument**: the current instrument app name. It will not be possible to change instrument a delayed start is already configured.
* **Remaining time**: a countdown showing remaining time to test start
* **Operator**: the user name of the operator who set the delayed start

Finally, 2 buttons:
* **Save and exit**: close the client application. The delayed start will remain active and the test will be started at the configured time, even if no client is connected to the instrument.
* **Abort delayed start**: cancel delayed start and dismiss the dialog. 

The dialog will remain active until the test starts. If you close the client application or click **Save and exit**, the delayed start will remain effective. If you later reconnect to the instrument, the delayed start dialog will pop up again, until test starts or delayed start is aborted. 

Dismissing the dialog equals aborting the delayed start.


.. _live_interact:
    
Interacting with a running test
----------------------------------

Status panel
^^^^^^^^^^^^^
* Status panel

Data Plot
^^^^^^^^^^^^^^^^
* Plotting results

Data Table
^^^^^^^^^^^
* Viewing data table

Storyboard
^^^^^^^^^^^
* The storyboard
    

.. _live_end:
    
Ending the test
----------------
The test will naturally end when a termination option is triggered (end of thermal cycle, test duration elapsed, etc). At the end of the test, the output file will be downloaded to the client PC - if the client is connected - or scheduled for download with the :ref:`storage_tasks` mechanism.

To forcefully stop the test, click **Stop** button in upper-left toolbar. You will be asked to confirm your decision, and if you want to save the partial output file or immediately delete it. 

In certain conditions it is useful to stop the thermal control without stopping the test. Click the **Cool** button in the upper-left toolbar and confirm your decision. The confirmation dialog will warn you that, in order to stop the thermal cycle without stopping the test, the option *Stop after thermal cycle* was implicitly disabled. If you did not provide a maximum duration for your test, or other special termination option, it is possible that your test will never end. 

**Never ending tests** are possible by disabling the *Stop after thermal cycle* option and setting a zero or negative *Maximum test duration*. It's up to you to manually stop these tests.

Changing termination options has immediate effect on the running test. For example, if the thermal control ended and enable the *Stop after thermal cycle* option, the test will instantly stop. Or, if you set a maximum test duration greater than zero but smaller than current elapsed time.






