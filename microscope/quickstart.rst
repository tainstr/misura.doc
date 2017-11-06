.. include:: ../substitutions.txt

.. _quickstart_heating_microscope:
    
Quick Start: Running an Heating Microscope Test
===============================================

While the general :ref:`live_acquisition` instructions apply also for the Heating Microscope, this section describes specific topics which should be considered to carry out microscopy tests.

.. _microscope_window:
    
Microscope Acquisition Window
-----------------------------

The Microscope :ref:`live_acquisition` window additionally comprises:
    
    * One/two high-resolution :ref:`camera` windows with height motion controller.
    * :term:`Global Focus` motion controller.
    * Samples height information displayed on the :ref:`live_status` panel, updated realtime during the analysis.
    * One to eight :ref:`live_samples` tabs in the left Test Configuration area.
    * The :ref:`storyboard` bottom area.
        
The workflow for a microscope test follows the general rules described in section :ref:`live_acquisition`.
   
.. microscope_camera:
    
Adjusting the camera position
-----------------------------
:term:`ODP` cameras are mounted on two motorized axes: the height and the focus. Older/simpler models might still have manual positioning with micrometric translation stages. 
    
The initial position of the camera should be automatically reached during instrument initialization, as described in :ref:`camera_motion_control`.
    
Use the height motion control to ensure the holding plate is always visible. 

Once the position of the camera has been established you have to put the sample in focus.  This should be carried out before every test.  Note that the typical cylindrical shape of the sample means that when the centre of the sample is in focus the sides are not.  This is absolutely normal and does not affect the reliability of the analysis which will get the best results anyway.

The :term:`Region Of Interest` should then be reduced so that the height of the sample occupies just 3/4 of the active region, and the width is 1/2. If multi-sampling, each region should manually be placed around each sample.    
The excess of the region dimensions with respect to the sample depend on the limiting sample behaviours. If the melting should be observed, enough region width should be provided for the molten sample to be still framed. If the sample undergoes a huge expansion, the region height should exceed the initial sample width by appropriate amount.     

.. microscope_recording:
    
Recording Frames and Profiles
-----------------------------

|m| records can record raw frames, as they are received from the camera, and/or analyzed (x,y) profiles produced by the morphometric analysis. 

The default behaviour is to record profiles and discard frames, to save space. 

This option can be set in :ref:`live_samples` sections independently for each sample. 


.. microscope_shapes:
    
Standards for Characteristic shapes identification
--------------------------------------------------

Characteristic shapes are displayed in the :ref:`live_samples` tab in **Test Configuration** side area, as a Time/Temperature :ref:`metadata` label. 
    
Basic shape recognition parameters can be affected by expanding sub-options ([+] button on the right) and adjusting the sliders to the desired values.

|m| always calculate shapes according to its advanced morphometric logic, making use of 3D extrapolations and 



.. microscope_afterShape:


Stopping the test when a shape is recognized
--------------------------------------------

A Microscope test can be automatically interrupted when a characteristic shape is recognized. To activate this termination option:
    
    * Select the :ref:`live_measure` tab in **Test Configuration** side area and scroll to the bottom of the page. 
    * Locate the ``After recognized shape`` option and click on the checkbox on the right to enable it. 
    * The the test will end when the ``Melting`` shape is recognized. 

To fine-tune the test termination, expand sub-options by clicking on the "+" sign on the right of the ``Edit`` button. 

    * ``Stop after temperature changed by`` will cause the test to interrupt after the temperature changed by the configured number of degrees from the instant when the shape was recognized. The default value is 10°C. This means that if the melting is recognized at 600°C, the test will be interrupted at 610°C, or 590°C in the unlikely event the furnace was cooling down. 
    * ``Stop after time passed`` will wait the configured amount of seconds before interrupting the test. The default value is zero, meaning as soon as the condition is met. 
    * The test will end when ``both`` termination options are met (after temperature changed enough and after the minimum amount of time has passed).
    * ``Require all samples``: in case of multi-sample tests, the default behaviour is to interrupt the test as soon as any sample meets the conditions (as soon as any sample melts). If this option is activated, all samples are required to meet the termination conditions for the test to be stopped (all samples must melt).


