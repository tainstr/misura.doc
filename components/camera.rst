.. include:: /substitutions.txt

.. _camera:
    
Camera controller
==================================
The camera controller is showed by any :ref:`live_acquisition` App for controlling an instrument which is using cameras. When initially started, it appears as a live acquisition sub-window containing a dark gray rectangle over a light gray area, the former representing the camera resolution or :term:`CCD`.

The principal mode of interaction with the camera is by right-clicking anywhere. The **camera menu** appears showing all possible controls.

If X or Y motors are defined for the camera, motion control sliders are shown near the sides of the window.

.. hint::    
    - :ref:`heating_microscope` has 1 or 2 cameras
    - :ref:`vertical_dilatometer` and :ref:`horizontal_dilatometer` has 2 cameras
    - :ref:`relative_fleximeter` has 1 camera
    - :ref:`absolute_fleximeter` has 3 cameras
    - :ref:`furnace_instrument` has no cameras

Streaming
----------------
Streaming can be started/stopped from the camera menu by setting the **Streaming** flag (first menu entry). Streaming means the user interface is continuously receiving and showing images. After a few seconds from when it is started, frames will be displayed in the gray area. If the streaming is subsequently stopped, the last frame will remain visible. 

Streaming images will not interfere with a running test. It can be started, stopped and resumed without any effect on actual image analysis and acquired data. 

The image viewed in the controller can be quickly **zoomed** in/out by using the mouse wheel. The **Fit view** action, accessible from the context menu, will resize back the image so it fits the window. 

Saving the current frame
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The current frame can be saved with **Save frame** camera menu entry. The first frame you save you will be asked a destination directory where to save current and all future frames. 

That directory will be remembered for each time you click on **Save frame** and frames will be saved there with increasing sequence numbers.

All samples contained in the frame will be saved in separate images having the same sequence numbers.

File names will have the format  ``<name>_smp<N>_<seq>.jpg`` where ``<seq>`` is the sequence number increased each time you save, ``<N>`` is the sample number, ``<name>`` is the camera name. For example: ``Left_smp0_12``. 


.. _camera_simulation:
    
Simulation 
^^^^^^^^^^^^^^^
The **Simulation** flag activates image analysis on the received frames. This flag can be changed only when no test is running. 

Simulation can be used before starting a real test, in order to validate the image quality. For example, to check that sample borders and limits are correctly detected, or that motors react in the right way to sample movements.

.. _camera_imaging:

Imaging
------------------
Most important digital imaging options are displayed in the camera menu, submenu **Imaging**, as a slider with an associated spinbox. You can either control the slider position or write the desired number in the spinbox and press Enter. 

Available imagin options:
    * Exposure (should be in range 1-1000)
    * Contrast 
    * Brightness 
    * Gamma (should be minimum possible)
    * Saturation (should be minimum)
    * Hue (should be minimum)
    
.. hint:: On most models it is advisable to use the spin-box to control the exposure. High values (>1000) might freeze the camera.

.. _camera_motion_control:

Motion Control
-----------------------
Camera position can be controlled by up to four motors roles, depending on your instrument's hardware:
    
    * **X**, lateral
    * **Y**, vertical
    * **Angle**, angular 
    * **Focus**, focus distance, usually shared by (and affecting) all cameras
    
If those motors are available, their movement can be set from the camera menu, submenu **Motion**. 

Each motor role shows an additional submenu called after its name, with those entries:
    
    * A slider, to control the position.
    * An **Is moving?** flag: can be unset to block the motor (but cannot be set).
    * A **Set zero position** action: define any current motor position as the new zero.
    * A **Configure motor** action: opens the extended configuration panel for the motor.
    * A **Configure encoder** action: opens the motion-to-image :term:`optical encoder` configuration panel.

Moreover, **X** and **Y** motors are represented directly in the camera controller as a bottom slider (**X**) and a lateral slider on the left (**Y**). A right click on these sliders opens a context menu showing the current position and offering a **Configure** action to open motor configuration panel.

There is a third way to interact with camera positioning: the **motion handle**. It is displayed as a red square in the top-left corner of the image. Dragging and dropping it around the image will cause a motion such that the new position of the top-left corner of the image will correspond to the position where you dropped the square.

.. _camera_analysis:

Analysis
------------------

The **Analysis** submenu allows to visualize some of the results obtained from image analysis. The results will be displayed as lines overlaid on the original frames. 

The most useful analysis overlay is the :term:`Regions of Interest`, which can be activated by the **View Regions** action. Each sample defined for the camera will be surrounded by a colored rectangle, representing the area of analysis. This rectangle can be resized by dragging and dropping two hook points on the top-left and bottom-right corners.
    
The **Reset Regions** action will restore the default region sizes.

Then we have 6 overlays. 

    * **Profile**: the border detected as the sample will be overlaid by a blue line, and the area of the sample with a faded blue.
    * **Points**: relevant profile point are highlighted with circles.
    * **Values Label**: a movable label is added. The label will contain lines in the form ``name: value``, where name stays for any sample option and value shows the current value for that option (e.g.: height).
    * **Base and Height**: (only for :ref:`heating_microscope`) two perpendicular segments starting from the bottom-left starting point of the sample, representing base and height.
    * **Circle Fitting**: (only for :ref:`heating_microscope`) a circle representing the best circular fitting to the profile.
    * **Pixel Calibration**: the :ref:`pixel_calibration` tool discussed below.

.. _camera_samples:
    
Samples
^^^^^^^^^

The concept of **sample** is fundamental to understand the camera controller, the management of :term:`ROI` and the image analysis. From the point of view of the camera, a sample is a portion of image, delimited by a :term:`ROI`, which can be analyzed in some way to extract results. This not always correspond to the concept of **physical sample** known to the instrument's operator.

For example, a sample is a cylinder of pressed powder used for :ref:`heating_microscope` analysis. In this case, the sample known to the camera is the same physical sample intended by the operator. 
    
The situation is less intuitive in the case of dilatometers or fleximeters. In this case, the operator places one physical sample, but two (or more) cameras view just one side of it. Each side is viewed as a separate **sub-sample**, one assigned to each camera.
    
The samples are defined in the active instrument. The camera just points to them, and use them to analyze images and associate output results. 

A camera can view one or more samples at the same time. The number of defined samples is available under the **Number of samples** option in the camera configuration panel. The camera defines an equivalent number of sub-options, accessible by clicking on the right **+** button, each pointing to the sample which should be used for the corresponding sample number.

Each sample defines its own image analyzer configuration. The advanced user can thus fine-tune image analysis parameters for each sample in the image, separately, making simultaneous multi-standard analysis straight-forward.

Active samples are shown in the camera menu, as **Sample <N>** menu items where `<N>` is the sample index from 0 (first sample) to the number of samples minus one. 

Each sub-menu contains these items:
    
    * **Configure**: opens the sample configuration panel, where image analysis results are stored. From the object tree on the left, it is possible to access to the image analysis option. Some true/false flags are repeated as menu items.
    * **Balck/white levelling**: convert the grayscale image to black/white. Color levels are accessible from the image analysis configuration panel.
    * **Adaptive threshold**: convert grayscale image to black/white. Color levels are adaptively calculated point-by-point as a function of neighborhood intensities.
    * **Dynamic regions**: activate :term:`ROI` auto-follow.

.. _camera_advanced:
    
Advanced configurations
-------------------------

The complete camera configuration panel is reserved for service purposes.

.. _pixel_calibration:
    
Pixel calibration
^^^^^^^^^^^^^^^^^^^^^^
A visual tool to calibrate the translation between :term:`CCD` pixels and real sample's microns. Reserved for service purposes.

.. camera_troubleshooting:
    
Troubleshooting
^^^^^^^^^^^^^^^^^^^^^^

To forcefully restart a camera which is no longer working correctly follow these steps:
    
    1. Open a camera controller, either from an instrument using it or from the global configuration panel.
    2. Right click on the camera frame. Select **Configure** action.
    3. Locate the **Running acquisition** option and set its value to **Stopped**.
    4. Back to the controller. Ensure the camera is **Streaming** by activating the corresponding context menu option.
    5. The camera will try to restart itself. On repeated failures, :ref:`server_restart` the server. On continued failure, :ref:`server_reboot` the embedded controller.

