.. include:: ../substitutions.txt

Data Sources
==================================

Data Sources is always the first Browser's tab, and is not possible to close it.

On startup it shows a ``Recent Data Sources`` window displaying two columns: one for recently opened files; one for recently accessed databases.

The recently opened tests listing is a quick way to directly re-open a recent file, no matter if it is indexed in a database. If a recent file is double-clicked or selected from the file system, it is opened in a new Test Window, in a new tab.
The more recently accessed file is placed at the top of the list.

The more convenient way to open a test file is to use the database index.

.. _database:
    
---------------------------------
|m| Databases
---------------------------------

|m| databases are a way to organize and search large amounts of tests, and for finding or establishing relations between them.

They are advanced indexes, collecting all important information about each test (metadata) but not storing any raw dataset. 

They are ephermeral, in the sense that they can be safely removed and recreated identical from the same set of files. They do not hold any unique information about your test. All information is actually saved only into the test files or into the plotting files.

There should always be a default database defined at the top of the list. This is the database where finished tests are automatically saved and indexed, configured in :ref:`preferences` under **Default database** option. 
    
    
Sharing databases
~~~~~~~~~~~~~~~~~~~~
The database can be located on a network share, to enable multi-user collaboration. Every client which needs to access the output files or the machine can configure it as its **Default database** in :ref:`preferences`, so finished tests are automatically added to that location only once.
        
This is an easy way to collaborate on data post-processing. It is advisable to save also the plots in the same, shared folder, so any user participating in the network will be able to open them.
        
.. warning::
    You might experience problems if a Linux client is accessing a database on a windows share through Samba. You will probably need to disable byte range locks by setting the ``nobrl`` flag when mounting the CIFS filesystem. Example ``/etc/fstab`` entry: ``//192.168.0.1/database /media/database cifs rw,users,nobrl,user=misura,pass=xxxx,exec 0 0``
        

---------------------------------
Database Dialog
---------------------------------
The interface towards a database is the Database Dialog. It shows a listing with all indexed tests, plus a query line with some filtering options to filter the list. 

The toolbar holds three buttons: ``Delete``, ``Refresh``, ``Rebuild``. 

* ``Delete`` will definitely remove the file both from the index **and from the filesystem**.
* ``Refresh`` will search for indexed files that no longer exists and for new files that are still not indexed.
* ``Rebuild`` will clear the current listing and rebuild entirely from the file found in the same folder or below the folder where the database file is located.

The query line allows to match the input line against one database column at a time. Select the column name, insert the text to be searched and press enter.

The database dialog as displayed in the :ref:`browser` will cause the test to be opened in a new tab. If called from :ref:`plotting` will cause the test datasets to be added to the active document and default plots to be created.
    






    


