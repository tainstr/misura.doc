.. include:: ../substitutions.txt

.. _quickstart_horizontal:
    
Quick Start: Running an Horizontal Dilatometer Test
=====================================================

This section documents specific dilatometric functions. 
Read :ref:`live_acquisition` for a general description of the acquisition window.

.. _horizontal_window:
    
Horizontal Dilatometer Acquisition Window
--------------------------------------------

The Horizontal Dilatometer :ref:`live_acquisition` window additionally comprises:
    
    * Two :ref:`camera` windows with X, Y motion controllers.
    * :term:`Global Focus` motion controllers.
    * Sample Total displacement information displayed on the :ref:`live_status` panel, updated realtime during the analysis.
    * One :ref:`live_samples` tab in the left Test Configuration area.
        
The workflow for an horizontal dilatometer test follows the general rules described in section :ref:`live_acquisition`.
   
.. horizontal_camera:
    
Adjusting cameras position
--------------------------------
    
The initial position of the camera should be automatically reached during instrument initialization, as described in :ref:`camera_motion_control`.
    
Use the X motion control under each camera to find the border of the sample, which should appear as a vertical division line between a white and a black area, where the black represents the sample. 

In case of indented sample borders, use the Y motion control to frame the most planar section of the surface.

Once the position of the camera has been established you have to find the right focal distance, by moving the focus slider on the bottom of the Acquisition window. 

It is advisable to close the furnace before starting a new tests. Vibrations produced during furnace movements can slightly change the sample position. 

.. horizontal_dimension:

Setting initial sample dimension
----------------------------------

The Horizontal Optical Dilatometer measures changes in length, but cannot measure the initial length of the sample. 

The operator must measure it before starting a test, by using a high precision caliper. 

