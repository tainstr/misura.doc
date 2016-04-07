.. include:: ../substitutions.txt

.. _quickstart_flex:
    
Quick Start: Running an Absolute Optical Fleximeter Test
=========================================================

This section documents specific dilatometric functions. 
Read :ref:`live_acquisition` for a general description of the acquisition window.

.. _flex_window:
    
Fleximeter Acquisition Window
--------------------------------------------

The Absolute Fleximeter :ref:`live_acquisition` window additionally comprises:
    
    * Three :ref:`camera` windows. Two lateral (right/left) cameras with X, Y motion controllers and one center camera with Y motion controller.
    * :term:`Global Focus` motion controllers.
    * Sample Total displacement information displayed on the :ref:`live_status` panel, updated realtime during the analysis.
    * One :ref:`live_samples` tab in the left Test Configuration area.
        
The workflow for an Absolute Fleximeter test follows the general rules described in section :ref:`live_acquisition`.
   
.. flex_camera:
    
Adjusting cameras position
--------------------------------
    
The initial position of the camera should be automatically reached during instrument initialization, as described in :ref:`camera_motion_control`.

Use the Y motion control on the left side of each camera window to find the border of the sample, which should appear as an horizontal division line between a white and a black area, where the black represents the sample. 

X motion controllers should not be changed, unless default positions make it impossible to carry out the test. 

Once the position of the camera has been established you have to find the right focal distance, by moving the focus slider on the bottom of the Acquisition window. 

It is advisable to close the furnace before starting a new tests. Vibrations produced during furnace movements can slightly change the sample position. 


