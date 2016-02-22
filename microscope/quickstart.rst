.. include:: ../substitutions.txt

.. _quickstart_heating_microscope:
    
Quick Start: Running an Heating Microscope Test
=================================================

While the general :ref:`live` instructions apply also for the Heating Microscope, this section describes specific topics which should be considered to carry out microscopy tests.

.. _microscope_window:
    
Microscope Acquisition Window
-------------------------------

The Microscope :ref:`live_acquisition` window additionally comprises:
    
    * One/two high-resolution :ref:`camera` windows.
    * Focus and height motion controllers.
    * Samples height information displayed on the :ref:`live_status` panel, updated realtime during the analysis.
    * One to eight :ref:`live_samples` tabs in the left Test Configuration area.
    * The :ref:`storyboard` bottom area.
        
The workflow for a microscope test follow the general rules described in section :ref:`live_acquisition`.
   
.. microscope_camera:
    
Adjusting the camera position
--------------------------------
:term:`ODP` cameras are mounted on two motorized axes: the height and the focus. Older/simpler models might still have manual positioning with micrometric translation stages. 
    
The initial position of the camera should be automatically reached during instrument initialization, as described in :ref:`camera_motion_control`.
    
Use the height motion control to ensure the holding plate is always visible. 

Once the position of the camera has been established you have to put the sample in focus.  This should be carried out before every test.  Note that the typical cylindrical shape of the sample means that when the centre of the sample is in focus the sides are not.  This is absolutely normal and does not affect the reliability of the analysis which will get the best results anyway.

The :term:`Region Of Interest` should then be reduced so that the height of the sample occupies just 3/4 of the active region, and the width is 1/2. If multi-sampling, each region should manually be placed around each sample.    
The excess of the region dimensions with respect to the sample depend on the limiting sample behaviours. If the melting should be observed, enough region width should be provided for the molten sample to be still framed. If the sample undergoes a huge expansion, the region height should exceed the initial sample width by appropriate amount.     

.. microscope_recording:
    
Recording Frames and Profiles
-------------------------------

.. microscope_shapes:
    
Characteristic shapes
-----------------------

Characteristic shapes are displayed in the :ref:`live_samples` tab under **Test Configuration** area, as a Time/Temperature couple. 
    
Basic shape recognition parameters can be affected by expanding sub-options ([+] button on the right) and adjusting the sliders to the desired values.

Stopping the test when a shape is recognized
---------------------------------------------

