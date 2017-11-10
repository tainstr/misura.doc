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

Follow these steps:

	#. :ref:`live_connect <Connect>` to the server with `admin` rights.
	#. From main window menu: `Settings > Send update package`.
	#. Navigate to the update package (`misura_pkg_<version>.tar`) and send.
	#. The server will reboot and the client will shortly close itself.
	#. When you reconnect to the server, it will be at the selected version.

You can check package name and last update date in the sub-options **Last applied package name** and **date** 
in the **Support** configuration node (`Settings > Global` menu action).

Downgrading
^^^^^^^^^^^^
Each upgrade package which is sent to the server remains saved locally, so that it is possible to rollback any previous release.
Since this operation is much less usual, the procedure is less straightforward than upgrading.

	#. Open Acquisition and connect to the instrument.
	#. From **Settings** menu, select **Global** action.
	#. From the objects tree on the left of the new window, double-click on **Support** node.
	#. Activate the **Status** configuration section by clicking the checkbox.
	#. Locate the **Available software versions** option and select the version you want to revert to.
	#. Expand sub-options by clicking on the ``[+]`` leftmost button.
	#. Click on **Apply selected software version**.
	#. A confirmation dialog appears. Acknowledge it and close the global configuration window.
	#. Return to Acquisition application and command a :ref:`server_restart` to make the changes effective.



