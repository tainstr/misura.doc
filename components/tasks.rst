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

The default user's :ref:`database` is always kept synchronized with each instrument the client connects to. This allows to build an unified archive of all tests, independently from where they are carried out.
    
The position of the database on the client machine can be configured in the :ref:`preferences` dialog, under **Default database** option. If you change this path without actually moving the database folder from the old location to the new one, the storage synch mechanism will re-download any available output file on the remote machine. You might loose old tests.

If the client is connected to the instrument when the a test finishes, the test is automatically downloaded to the local database. If the client was not connected, or other errors occurred, the next time you connect to the machine you will be warned about output files which were not downloaded.

The warning appears in the :ref:`pending_tasks` dialog, under the **Storage** tab. The Storage widget allows manual management of storage synchronization. It is composed by four  sub-tabs containing tables, each table listing metadata about tests which can either be downloaded or ignored. 
    
The workflow of a test which was not automatically downloaded is the following:
    
    1. It appears as row in **Waiting approval** table. You should right-click on the table and select *Download* from the context menu.
    2. This will move the row to the **Download Queue** table. After a while the download will start.
    3. Before the download starts you can still choose to *Ignore* the file by right-clicking on its row in the table and selecting *Ignore*. This will move the file to the **Ignored** table. Suppose you do not choose to *Ignore* it.
    4. The file download will cause a progress bar to appear in the :ref:`local_tasks`, until downloads finishes.
    5. If an error occurs, the row will be moved from **Download Queue** to the **Errors** table. 
    6. From the **Errors** table you can right-click again on the row representing the remote file and ask for a *Retry*.
    7. If you are unable to download a file, you can copy the full error log from the **Errors** table and send to the developers for debug.
    8. Once the file is correctly downloaded, its associated metadata row will disappear from the tables. A new entry will be added to the local :ref:`database`.


Waiting approval
~~~~~~~~~~~~~~~~~
This table lists tests which are available on the machine but not on the local database. 

By right clicking on one or more rows you can either:
    
    - *Download*: Try to download the test by moving it to the **Download Queue**.
    - *Ignore*: Discard the test by moving it to the **Ignored** table.

Download Queue 
~~~~~~~~~~~~~~~
This table lists tests which are waiting to be downloaded. 

By right-clicking on one or more rows you can *Ignore* the file by removing it from the queue and adding to the **Ignored** table.

Ignored
~~~~~~~~~
This table lists tests for which a download will not be tried again and for which the user will never be warned about. 

By right-clicking on one or more rows you can *Download* the file again by moving its entry to the **Download Queue**.

Errors
~~~~~~~
This table lists tests which were not possible to download due to errors, along with a log message about the error which occurred. By right-clicking on one or more rows you can either:
    
    - *Retry* the download it by sending back to the **Download Queue**.
    - *Ignore* it by moving to the **Ignored** table.


Sharing a database through Windows/Samba
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 The database can be located on a network share. Every client which needs to access the output files or the machine can configure it as its **Default database** in :ref:`preferences`. 
     
This is an easy way to collaborate on data post-processing.

.. warning::
    
    You might experience problems if a Linux client is accessing a database on a windows share through Samba. You will probably need to disable byte range locks by setting the ``nobrl`` flag when mounting the CIFS filesystem. Example ``/etc/fstab`` entry: ``//192.168.0.1/database /media/database cifs rw,users,nobrl,user=misura,pass=xxxx,exec 0 0``
    

