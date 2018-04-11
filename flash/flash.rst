.. Misura Flash documentation master file, created by
   sphinx-quickstart on Fri Feb  2 11:15:26 2018.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. include:: ../substitutions.txt

|mf| documentation
========================================

|mf| is a post-analysis tool for reading, organizing and processing data obtained from 
FlashLine instrument control software running on TA Instrument's flash products. 

|mf| extends the functionality of |m4| software: it is build upon the common platform explained in the general documentation.

It currently supports the calculation of thermal diffusivity from flash thermograms, 
according to advanced curve fitting models as: 

- :ref:`model_gembarovic`
- :ref:`model_inplane`
- :ref:`model_multilayer` (two and three layers)


.. toctree::
   :maxdepth: 3
   :caption: Contents:
   
   quickstart
   data_import
   interface
   models
   flash_options


