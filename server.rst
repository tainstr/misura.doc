.. include:: substitutions.txt

.. _misura_server:
    
Misura Server
================

Misura Server is the software component embedded in the measurement instrument. It is responsible for the control of all of the instrument's hardware and for data recording.


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

TODO
