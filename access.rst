.. include:: substitutions.txt

.. _access-management:
    
Access Management
==================================

Communication between :term:`Misura Server` and :term:`Misura Client` happens over an SSL-encrypted channel and is password-protected.
    
Server-side it is possible to define users, associate passwords and assign read and write permission levels. Users can be managed from the General configuration panel, under the ``users`` node. 

The ``Users``section exposes the ``Users List`` option table, with 4 columns which can be directly edited by double-clicking:
    
    * ``Name``: The user name asked at login time
    * ``Read level``: The permission level for reading. Only options having a read level equal or lower than the user's one will be visible to the user. 
    * ``Write level``: The permission level for writing. Only options having a write level equal or lower than the user's one will be editable by the user. 
    * ``Hash``: The password, currently in plain text

The users object is currently reserved for service purposes.
