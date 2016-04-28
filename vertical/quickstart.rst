.. include:: ../substitutions.txt

.. _quickstart_vertical:
    
Quick Start: Running a Vertical Dilatometer test
=================================================
This section documents specific dilatometric functions. 
Read :ref:`live_acquisition` for a general description of the acquisition window.
    
 
.. _vertical_window:
    
Vertical Dilatometer Acquisition Window
--------------------------------------------

The Vertical Dilatometer :ref:`live_acquisition` window additionally comprises:
    
    * Two :ref:`camera` windows with X, Y motion controllers.
    * :term:`Global Focus` motion controllers.
    * Sample Total displacement information displayed on the :ref:`live_status` panel, updated realtime during the analysis.
    * One :ref:`live_samples` tab in the left Test Configuration area.
        
The workflow for an vertical dilatometer test follows the general rules described in section :ref:`live_acquisition`.
   
.. vertical_camera:
    
Adjusting cameras position
--------------------------------
    
The initial position of the camera should be automatically reached during instrument initialization, as described in :ref:`camera_motion_control`.
    
Use the Y motion control on the left side of each camera to find the border of the sample and of the holding plate. They both appear as an horizontal division line between a white and a black area, where the black represents the sample for the Height camera and the holding plate for the Base camera. 

In case of indented sample borders, use the X motion control to frame the most planar section of the surface.

Once the position of the camera has been established you have to find the right focal distance, by moving the focus slider on the bottom of the Acquisition window. 

It is advisable to close the furnace before starting a new tests. Vibrations produced during furnace movements can slightly change the sample position. 

.. vertical_dimension:

Setting initial sample dimension
----------------------------------

The Vertical Optical Dilatometer measures changes in length, but cannot measure the initial length of the sample. 

The operator must measure it before starting a test, by using a high precision caliper. 

.. vertical_stopping:
    
Stopping the test on excess deformation
-----------------------------------------

The vertical dilatometer is designed to follow the sample until complete melting. Nevertheless, this might pose the risk of sample flowing below the sample holder if its viscosity drops down enough.

In thermal cycle tab, under ref:`stopping_conditions` section, the Horizontal Optical Dilatometers offers a security option to stop the test whenever deformation exceeds a configurable threshold, **Stop on deformation excess**. 
    
The security limits are +25 and -50 and are active by default.
    
This option helps preventing sample flowing in the furnace. 

We advise to enable this option and set reasonable limits for the specific material analysed.


