.. include:: substitutions.txt

.. _misura_server:
    
Misura Server
================

Misura Server is the software component embedded in the measurement instrument. It is responsible for the control of all of the instrument's hardware and for data recording.

Web Interface
--------------
A very basic web interface is available to retrieve test files, logs and configurations. 

* Test files: https://172.16.8.68:3880/data
* Log files: https://172.16.8.68:3880/data/log
* Configuration files: https://172.16.8.68:3880/conf
* Status: https://172.16.8.68:3880/stream

.. _server_process:
    
Process Management
-------------------

.. _server_restart:

Soft-Restart 
^^^^^^^^^^^^^^

Most of the software problems will go away after a server restart, which means you just close and reopen the server application. 

In order to restart the server:
    
    1. Open the Acquisition application. Connect to the instrument you want to restart.
    2. From the **Connect** menu (top-left), select **Restart**
    3. Wait few seconds, then reconnect to the instrument.

.. _server_reboot:

Rebooting 
^^^^^^^^^^^
Rare but serious operative system issues are usually solved by an embedded computer restart. Only the controller will restart: you shall not turn off the main power.

To reboot the controller:
    
    1. Open the Acquisition application. Connect to the instrument you want to reboot.
    2. From the **Settings** menu, select **Global** action.
    3. Double-click on **support** entry from the tree on the left. The support configuration panel is displayed as first tab on the right.
    4. Locate the **Reboot machine OS** option and click on the button on the left.
    5. The reboot will immediately start. At this point you can close the Acquisition application.
    6. After 5 minutes you can reconnect to your instrument.

.. _server_shutdown:

Shutting down
^^^^^^^^^^^^^^^

The shutdown command from the **Connect** menu will cause the onboard computer controlling the instrument to shutdown.

	1. Open the Acquisition application. Connect to the instrument you want to shutdown.
	2. From the **Connect** menu, select **Shutdown**.
	3. A confirmation message box will be shown. 
	4. Acquistion app can be closed. 

The onboard computer should start up automatically after next connection tentative from Acquisition application.

.. _server_upgrade:

Upgrading
-----------

Server upgrade package might be provided as tarballs (.tar) or zipped (.zip) archives. 
An upgrade archive needs to be transferred onto the instrument while it is active, and then the server process should be restarted.

	1. Open Acquisition and connect to the instrument.
	2. From **Settings** menu, select **Global** action.
	3. From the objects tree on the left of the new window, double-click on **Support** node.
	4. Activate the **Status** configuration section by clicking the checkbox.
	5. Locate the **Available software versions** option and click on the **Send** button on the left of the combobox.
	6. Navigate through your filesystem to reach the upgrade archive and select it. 
	7. Double-click on the **Support** node on the left tree to refresh the Support page you are editing.
	8. Locate again the **Available software versions** and select from the combobox the latest package name you uploaded.
	9. Expand sub-options by clicking on the ``[+]`` leftmost button.
	10. Click on **Apply selected software version**.
	11. A confirmation dialog appears. Acknowledge it and close the global configuration window.
	12. Return to Acquisition application and command a :ref:`server_restart` to make the changes effective.



