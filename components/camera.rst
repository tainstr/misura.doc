.. include:: /substitutions.txt

.. camera:
    
Camera controller
==================================

The camera controller is showed by any :ref:`live_acquisition` App for controlling an instrument using cameras. When initially started it appears as a live acquisition sub-window containing a dark gray rectangle over a light gray area, the former representing the camera resolution or :term:`CCD`.

The principal mode of interaction with the camera is by right-clicking anywhere. The **camera menu** appears showing all possible controls.

If X or Y motors are defined for the camera, motion control sliders are showed near the sides of the window.

.. highlights::    
    - :ref:`heating_microscope` has 1 or 2 cameras
    - :ref:`vertical_dilatometer` and :ref:`horizontal_dilatometer` has 2 cameras
    - :ref:`relative_fleximeter` has 1 camera
    - :ref:`absolute_fleximeter` has 3 cameras
    - :ref:`furnace_instrument` has no cameras

Streaming
----------------

By streaming we mean that the user interface is receiving and showing images. Streaming can be started/stoppped from the camera menu by setting the **Streaming** flag (first menu entry). After a few seconds, frames will be displayed in the grey area. If the streaming is subsequently stopped, the last frame will remain visible. 

Streaming images will not interfere with a running test. It can be started, stopped and resumed without any effect on actual image analysis and acquired data. 

Saving the current frame
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The current frame can be saved with **Save frame** camera menu entry. The first frame you save you will be asked a destination directory where to save current and all future frames. 

That directory will be remembered for each time you click on **Save frame** and frames will be saved there with increasing sequence numbers.

All samples contained in the frame will be saved in separate images having the same sequence numbers.

File names will have the format  ``<name>_smp<N>_<seq>.jpg`` where ``<seq>`` is the sequence number increased each time you save, ``<N>`` is the sample number, ``<name>`` is the camera name. For example: ``Left_smp0_12``. 

.. _camera_imaging:
    
Imaging
------------------

Most important digital imaging options are displayed in the camera menu, submenu **Imaging**, as slider with an associated spinbox. You can either control the slider position or write the desired number in the spinbox and press Enter. 

On most models it is advisable to use the spinbox to control the exposure.

Available imagin options:
    * Exposure
    * Contrast 
    * Brightness 
    * Gamma (should be minimum possible)
    * Saturation (should be minimum)
    * Hue (should be minimum)

.. _camera_motion_control:

Motion Control
-----------------------

Camera position can be controlled by up to four motors roles:
    * **X**, lateral
    * **Y**, vertical
    * **Angle**, angular 
    * **Focus**, focus distance, usually shared by (and affecting) all cameras
    
If those motors are available, their movement can be set from the camera menu, submenu **Motion**. Each motor role shows an additional 

* Via menu
* Via sliders
* Via motion handle

.. _camera_analysis:

Analysis
------------------

* Regions of interest
* Overlays

.. _camera_samples:
    
Samples
^^^^^^^^^^^
* Configuring image analyzers
* Black/white level

.. _camera_advanced:
    
Advanced configurations
-------------------------

.. camera_troubleshooting:
    
Troubleshooting
------------------
* How to forcefully restart a camera

