.. include:: substitutions.txt

.. _live_acquisition:

Live Acquisition
==================

The Live Acquisition software allows to carry on any kind of measurement available on a Misura platform. 

This section describes basic functionalities which are general enough to be applicable to any measurement. 
    
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

When connecting from multiple clients, you should either keep all client synchronized between them, to avoid multiple re-sync. 



.. _live_init:
    
Initializing the Measurement App
---------------------------------

After a successful connection you will be shown a list with available Measurement Apps, a button for each instrument. Click the corresponding button to select your desired instrument.

Once the instrument is selected, the machine will start its setup.

A "Pending Tasks" dialog will appear in the left panel, showing some details about what is happening.

This operation can take up to a couple of minutes, depending on the instrument. Any interaction with the application is discouraged until when the dialog disappears.

Once the initialization is complete, the application will display all relevant controls needed to configure, start and follow the execution of the test.

The menu bar contains:
    * **Connect**: to connect to a different machine or to change measurement app. 
    * **Measure**: allows to re-initialize the instrument from zero, set a delayed start, hide/show user interface components (Test Configuration, Storyboard, Data Plot, Data Table, Log Window), Reload Data from the instrument, Quit client.
    * **Settings**: gives access to advanced configuration panels for the **Instrument** itself, its individual **Devices**, or the full **Global** configuration.
    * **Help**: client configuration, documentation link opening the documentation you are reading, the :ref:`pending_tasks` dialog, the software information dialog.

On the left side of the window you find a tabbed area showing:
    * **Status** tab: contains short summary of the current test condition. The first two options shows if a test is running (data recording) and if the thermal control is active. They are underlined in green when not active, in red when running. Then follows information on test name and test duration (if running); the furnace position if motorized; temperatures, setpoint and power output. More sample-dependent option can be shown based on the active measurement app. 
    * **Measure** tab: generic test configurations can be made (starting and stopping conditions) and metadata can be viewed (eg: maximum temperature reached)
    * **Thermal Cycle** tab: allows to define the thermal cycle and preview it
    * **Sample<N>** tabs: one tab for each sample defined in the analysis.
    * **Results** tab: empty until the start of the test. Will be populated with tools for :ref:`live_interact`.
        
On the bottom, a bar showing: 
    * **Focus** slider and spin-box, to adjust the focus distance. 
    * **Furnace:** option to view and control furnace position (Opened/Closed). Only available where furance is motorized.
    


.. _live_config: 
    
Configuring the test
----------------------

The first step of test configuration is placing the sample in the right position. If the furnace is motorized, you should always open it by using the option **Is the furnace closed?** in the Status tab, or the **Furnace:** box in the bottom bar. That option should be changed to the desired position: *Closed* or *Opened*. Once the sample is positioned and correctly framed, it is advisable to close the furnace using the same option, and proceed with test configuration.

The test name can be directly set in the Status panel.
* Status: Setting the test name
* Measure: Setting the number of samples. Setting termination options.
* Configuring the thermal cycle. Cycle termination option.
* Setting individual sample names in a multi-samples test.




.. _live_start:

Starting the test
-------------------

Once the specimen is correctly framed by the cameras, you can give a name to the test (in the *Status* tab) and start the test, by clicking the *Start* button.

* Delayed start option


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
* Forcefully stopping the test
* Stopping the thermal control without stopping the test
* Changing termination options which might cause the test to immediately stop
* Never-ending testing





