.. include:: ../substitutions.txt

.. _flash_data_import:
    
Importing |fl| data
===================

Flash functionalities have been implemented in the :ref:`browser`.

|fl| saves each data item in a separate file. This large number of files is then organized in a hierarchy of directories. 
|fl| data strcuture cannot be directly opened by |mf|: a conversion procedure will be needed in order to compress every data file into 
a single test file. 

Data import functionalities are available from the :ref:`datasources` base tab in the Browser. 

The import procedure will start when the **TestInformation.xml** file either dragged and dropped onto the gray area in the ``Databases`` tab, 
or selected from the filesystem after clicking the ``Import...`` button. 
Other files which will trigger the import procedure are the shot files with **.fw0 or .fw1** extensions (like ``00101001.fw0``).

Opening any other file will abort the procedure. 

When the import starts, a progress bar will appear in a popup-up window. A ``Log`` button allows to follow the conversion of each file and each shot. 

Upon successful completion, the resulting file is directly opened in a new browser tab.

Double import
----------------

In the case the user attempts to import a file which was already converted in the past,
 and still existing on the file system, a dialog will prompt the user to choose what to do.
 
- ``Open``, will just open the already converted file, without converting it again 
- ``Rename``, will import the file again, and save it with a different name
- ``Overwrite``, will delete the old file and import all the data again
- ``Cancel``, abort any action and just exit the dialog (same effect as clicking X button)

Most of the times it is advisable to just ``Open`` the old file and save the long import procedure.

Locating the converted file
-----------------------------

The converted file will be added to the default database index, so that the user will be able to query all previously converted tests.
Available database indexes are visible in the second column of the :ref:`datasources` subwindow. 
If the user has not configured additional indexes, only the default one is visible.

During the conversion, data is copied from the original location into a compressed and optimized :term:`HDF5` file.
By default, the file is in the user folder on the local computer, under a ``flash`` subfolder in the default database directory.

The location of the default database is ``MisuraData`` under the **user** home folder. 
On most modern windows systems, it will be something like ``C:\Users\<username>\MisuraData``.

The default database name and location is visible under ``Default Database`` :ref:`preference <preferences>`.




