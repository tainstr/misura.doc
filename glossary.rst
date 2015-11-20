.. include:: substitutions.txt

Glossary 
===========

.. comment:
    NOTICE: these are just notes about |m| terminology and mappings to other TA products. The glossary will evolve into useful documentation once I collect enough terms!

    * Option
    * Representations in WinTA: Single-curve -> single-test, multi-curve-> multi-test
    * Thermal cycle, heating cycle, temperature profile
    
.. glossary::
    CCD
        The Charge-Coupled Device responsible for digital image acquisition. The term is usually referred to mean the active camera resolution, from which one or multiple regions of interests can be selected.
        
    ROI
    Region of Interest
        A rectangle representing a selection of the total camera resolution. 
        
    Optical Encoder
        The entity defining, forecasting and applying the conversion factor between one motor step and the number of pixels it produces on the image.
        
    Misura Platform
        The measurement instrument as a whole, comprising both software and hardware components.
        
    Misura Server
        The embedded software component controlling the instrument's hardware and actually performing measurements.
        
    Misura Client
        The user interface which allows to connect to a platform, carry out analysis, get the results, visualize, organize and post-process them.
    
    Instrument App 
        The software component used to carry out one kind of measurement technique (microscopy, dilatometry, fleximetry, etc). The Instrument App determines the user interface appearance, and is actually the category under which Measurement Apps are furtherer specified. The user never directly starts an Instrument App. 
        
    Measurement App 
        The specific configuration used to carry out a measurement. For example, the same measurement technique might be applied to very small or very big samples, requiring different Measurement Apps which configure hardware and software in order to meet different measurement requirements. The user always starts a Measurement App.
        
    Analysis App 
        A software component extending an Instrument App in order to add advanced functionalities. An Analysis App might add an experimental image analysis method or an innovative thermal control feature. 