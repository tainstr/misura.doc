.. include:: ../substitutions.txt

.. _pending_tasks:
    
Pending Tasks
==============
    
|m| is an heavily multi-threaded and multi-processing application, usually distributed between two computers (the client and the instrument itself).

It is important to have a clear visualization of what is happening and have a feedback about long-running tasks. When it is possible, the user should also have the choice to interrupt a task.

The **Pending Tasks** component is divided in three *tasks tabs*, each visualizing the ongoing operations on the **Remote** machine (the instrument), on the **Local** computer (the client) or data transfers involved in **Storage synchornization**.

A task is represented as a label containing the task name and a progress bar showing its current status. 

Tasks can involve sub-tasks, which are displayed as rows below the main task.

The Pending Tasks component is usually hidden, and can be showed only from the **Help** menu. When a Remote, Local or Storage task is started, it pops up either in the form of a dialog or integrated into the :ref:`live_acquisition` window.
When no more tasks are running anymore, the Pending Tasks component usually hides itself. 


.. _remote_tasks:
    
Remote operations
-------------------

Remote operations, or tasks, run on the instrument hardware and involve electronics configuration, motor positioning, multi-processing initialization or termination, output file creation or closure, calibration procedures and much more.  

The unique feature of :term:`Head Morphing`, which allows to change the observing system as a function of the kind of measurement you want to make, implies a reconfiguration step which can take few minutes and involve many moving parts. All concurrent remote operations involved in this *transformation* are showed each time you connect for the first time to a :term:`Measurement App` or each time you select a different Measurement App. 
    
Starting and stopping a test involve the coordination of multiple processes, the creation of complex data structures and the writing of big chunks of data on disk. These remote operations appear when a new test starts and even more when it finishes. 

The **Remote** tasks tab is empty when no remote tasks are running. It populates with a list of ongoing tasks when as the server performs them.

**Remote tasks cannot be interrupted. You should not interact with the software in any way while remote tasks are running.** If remote operations are forcefully interrupted or the user unintentionally interacts with the system while performing remote tasks, it is advisable to :ref:`server_restart` the server.

.. hint:: It is safe to interrupt the test initialization for security reasons by clicking the **Stop** button in the :ref:`live_acquisition` window. After that, anyway, it is advisable to run a new instrument initialization by clicking *Initialize new test* under the *Measure* menu.

.. _local_tasks:
    
Local operations
-----------------

Tasks ran by the client application are listed in the *Local* tab. For example:
    
    * Connecting to an instrument or opening an output file
    * Drawing the user interface for the various components (cameras, thermal cycle, graphs, etc)
    * Accessing to datasets
    
Local operations are generated both when connected to a remote server and when accessing to local output data files.


.. _storage_tasks:
    
Storage synchronization
-------------------------

The default user :ref:`database` is always kept synchronized with each instrument the client connects to. This allows to build an unified archive of all tests, independently from where they are performed.
    
    
