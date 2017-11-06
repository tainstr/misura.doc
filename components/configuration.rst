.. components:

Components and options 
======================

The configuration of a test involves many different components of the system: the measurement definition, one or more samples, the thermal cycle. 

Under the hood, many other components are configured automatically or based on the user's input: real physical devices (cameras, motors, power controllers, etc) 
and virtual components like sub-samples (Left/Right/Center, Base/Heigt), feedback regulators, the instrument itself, etc.

All these configurations are defined and saved in a consistent hierarchy of components both in the live instrument and in the output file. 

Each component defines several options: all summed up, they represent the **component's configuration**. 
Component configurations can be saved as **Configuration presets**, and recalled by their name to quickly get the device back in the desired configuration.

The user interface displays a device configuration as a **Configuration panel**: 
a structured list containing all available options (according to the user's :ref:`access-management`).

Components are organized in a hierarchical way, in order to make easier to search for them and to automate some actions on group of related components.

.. options:

Configuration options 
-----------------------

|m| offers a unified experience to visualize and edit any variable, generically called **Option**. 

Options can represent proper **Configuration** variables, which the user can change to obtain an effect, 
but also the **Status** of some server-side variable, or a read-only **Result** from an analysis.

This distinction is well visible in any configuration panel, where options are grouped in 3 boxes - one for each role.

Options have types (String, Integer, Float, etc) which determine their appearance in the user interface. 

All options share a common representation pattern: a label, containing the option's name, and the option value. 
The option value can be represented as an input box (for text), a spinbox (for numbers), a slider and a spinbox (for number with boundaries), 
a combo-box (for selections), a checkbox (for booleans), etc.

If a numerical option has an associated measurement unit, it will be displayed between the label and the value.

Option's menu
^^^^^^^^^^^^^^

The options's context menu can be visualized by right-clicking on the option's label.

* **Units**: Change measurement unit. Only for numerical options defining a number.
* **Set default value**: resets to factory default.
* **Check for modifications**: force to read the current value on the instrument's side and refresh. It as the same effect as passing the mouse over the option.
* **Option info**: opens a dialog where all option's attributes are listed
* **Detatch**: opens an enlargeable dialog containing the option label and value alone. This can be useful to view more clearly complex options, like tables.
* **Presets**: lists all values in any saved configuration preset for this component. By clicking on a submenu action, the related value will be applied. 
* **Compare**: list all values for options with the same name in any other component. By clicking on a submenu action, the related value will be applied.


Configuration panel
^^^^^^^^^^^^^^^^^^^^
A configuration panel lists all options related to a single component. For example, left-side panel in :ref:`live_config`, is a configuration panel. 

It can contain tabs, one for each major configuration section. 
For example, shape identification standards, listed as tabs in microscope :ref:`microscope_shapes`, 
are configuration sections.

The options listing can be divided up to 3 boxes, one for each option role:

* **Configuration**: options which can be edited by the user.
* **Status**: options which are generally changed server-side to reflect internal status. The user can interact with some of them. 
* **Results**: options which represent the output of a server process - usually read-only. 

Box visibility can be toggled by clicking on the checkbox near the header.
