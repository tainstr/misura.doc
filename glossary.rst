.. include:: substitutions.txt

Glossary 
===========

.. comment:
    NOTICE: these are just notes about |m| terminology and mappings to other TA products. The glossary will evolve into useful documentation once I collect enough terms!

    * Option
    * Representations in WinTA: Single-curve -> single-test, multi-curve-> multi-test
    * Thermal cycle, heating cycle, temperature profile
    
.. glossary::
    ODP
        Optical Dilatometry Platform, the most complete hardware controlled by Misura software.
    
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
        
    Head Morphing
    Measurement Head Morphing
    Instrument Initialization
        The process of configuring the measuring instrument to make a specific kind of measurement. This involves many software controllers setup and moving parts.
        
    Loaded
    Loaded Dataset
    Loaded Datasets
        A loaded dataset is currently loaded into the application memory. It can be plotted and used as the input for any data processing step. Opposite of :term:`Available Dataset`.
            
    Available
    Available Dataset
    Available Datasets
        An available dataset is not loaded into the application memory, but exists on the output file containing test data (it is *available for loading*). They are usually filtered out from the :ref:`navigator` and are not visible in data processing steps. An available dataset can be easily loaded through the use of :ref:`navigator`. 
            
    Free Sample Positioning
        A characteritic of all :term:`ODP` instrument is that samples are placed by hand with no physical constraints and very ample limiting geometries.
            
    Metadata
        Test metadata summarizes high-level aspects about test execution, expressed as a value, a time and a temperature. Test data contains time series of recorded values: eg how the length of the sample changes with time. A metadata is, for example, the maximum rate of change of the length: its value, the time at which it happened and the sample temperature at that time. Metadata is usually calculated runtime during the test execution, and can be replayed offline from the :ref:`browser`. 
            
    Scripts
    Script
        Small portions of source code which is executed by :term:`Misura Server` during a test. Scripts are exposed to the client and can be customized by the user to meet specific control procedures or experimental morphometrics standards. 
            
    Global Focus
        The focus distance can be adjusted for all cameras at the same time by means of a motorized translation stage. It is not possible to independently adjust the focus of each single camera. This is actually intentional as a discrepancy in focus distances usually suggests a sub-optimal sample orientation.
        
        