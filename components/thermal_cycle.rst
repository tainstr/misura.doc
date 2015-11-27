.. _thermal_cycle:

=================================
Thermal Cycle Designer
=================================

The Thermal Cycle Designer contains the controls to setup the wanted thermal cycle.

It is divided in three parts:
    
1. The upper area contains a table where you can define the thermal cycle.
2. The middle area shows general control options and furnace positions before the start or after the end of the test (if the furnace is motorized).
3. The lower area displayes a plot of temperature (red) and heating rate (blue) against forecasted time.

To set a thermal cycle, fill the upper table with rows. Each row of this table represents a target status to be reached by the furnace as the test execution proceeds, and how that status should be reached by the temperature controller. 

Each row will be executed in sequence. When there are no more rows left, the thermal cycle ends, which can cause also the end of the tests depending on how control options are configured.

You can load a predefined thermal cycle from the upper-right combo box, showing all saved cycles.

The table has four columns:
    
    1. **Time**: the expected end time of the row, relative to the start of the test (zero).
    2. **Temperature**: the target setpoint of the row, which the furnace controller will try to reach by modulating power emission.
    3. **Heating Rate**: the rate by which the temperature is changed from the previous row up (or down to) to the target setpoint.
    4. **Duration**: the expected duration needed to finish the row.

To insert or delete rows you can use the **Edit** menu or the context menu appearing by right-clicking on the table. On insert, a new row will be added after the currently selected row. On **Remove current line**, the current row will be removed from the table. On insert/delete/edit of a row, all subsequent rows might get automatically updated to reflect the changes (eg: in Time column).

The **File** menu allows to import/export from CSV (comma separed values) text files and to completely clear the table.

Each time a row is edited or a cycle is loaded, its value is validated against temperature and heating rate limits, and the whole table is updated with valid data. 

.. hint:: The time-temperature curve obtained by filling this table is not the real temperature profile that you will get at the end of the test. This is due to thermal inertia of the furnace, power emission limits, automatic control adjustments and variable length events. 

-------------------------------------
Inserting a Temperature Ramp (Point)
-------------------------------------

A temperature ramp is defined by a setpoint temperature and a time by which that temperature must be reached by the furnace (a time, temperature point). Before you input the target temperature, you should input either the end time of the ramp (**Time** column), or the desired **Heating Rate**, or the **Duration** of the ramp. 

After having defined one of the three columns, you can input the **Temperature** target for that row. The remaining columns will be filled accordingly.

The default way of defining the ramp is by setting the **Heating Rate** column (°C per minute). The row **Time** and **Duration** will be auto-filled. 

Filling the **Duration** column is mostly useful to express dwell ramps, where the heating rate is zero and the temperature must be kept fixed for a certain duration.

To add a temperature ramp to the table:
    1. Right click on the row before the position where you want the new row to appear and select *Insert point*. 
    2. Once the row appears, double-click either on the Heating Rate, Duration or Time cell and set the correct value.
    3. Double-click on the Temperature cell and insert the target setpoint.
    4. Other cells will be automatically calculated.
    5. Subsequent rows in the table will be re-calculated as needed.
    
.. hint:: Use negative values to express controlled cooling.

..  
    Add EXAMPLES for ramps and dwells.

--------------------------
Inserting a Checkpoint
--------------------------

When a checkpoint row is reached, the setpoint will be kept constant until the real furnace temperature reaches it within a tolerance, or a timeout expires. 

As the real temperature reached by the furnace is never exactly equal to the setpoint temperature, the checkpoint event allows to wait until the setpoint is actually reached before proceeding with the next row. 

This is useful, for example, to start the controlled cooling always from the same temperature.

The setpoint will be the last available in the thermal cycle - usually the previous row in the table. 

The typical temperature profile will be the same as a dwell row.

To add a checkpoint, right click and select *Insert checkpoint*. A dialog will show up, where you'll be able insert the desired temperature and timeout.

The plot displayes checkpoints as dwell segments with few minutes duration, but their real duration cannot be forecasted because it depends from tolerance, timeout and furnace inertia.

.. tip:: 
    A checkpoint with tolerance 3°C and timeout 60min is added after a row with setpoint temperature at 1000°C.
    
    When the execution reaches the checkpoint event, suppose the real temperature is 980°C. The checkpoint will cause the controller to keep the setpoint fixed at 1000°C, until the temperature raises above 997°C (1000°C - 3°C tolerance). If this condition is not satisfied in 60min timeout, the control will anyway pass to the next row.


-----------------------------------
Inserting a Furnace Movement
-----------------------------------

Furnace movement events are available only if your instrument has a motorized furnace.

Movement events will cause the furnace to reach the configured position when executed. After movement execution, the control will pass to the next row.

During *Open* movements the thermal control will suspend and power emission will be zero until the movement ends.

During *Close* event, if the furnace thermocouple is controlling the temperature, the controller will try to keep any previously configured setpoint until the movement ends.

Furnace movement can be used to obtain flash heating / flash cooling temperature profiles.

To add a movement, right click on the previous row and select *Insert movement*. A dialog will show up, and you'll be able to select a *Open* or *Close* furnace movement.

.. hint:: If the furnace is already in the position configured in the event, nothing will happen. 

-----------------------------------
Inserting a Natural Cooling
-----------------------------------

During natural cooling events the thermal control is suspended and power emission is set to zero. The event will end, and pass control to the next row, when a target temperature is reached or a timeout occurs.

The resulting temperature profile is a double exponential decay.

To add a natural cooling, right click on the previous row and select *Insert natural cooling*. A dialog will show up, where you can set target temperature and timeout.

.. hint:: Set timeout to a negative value to avoid a timeout to occur. This might lead to unlimited acquisition whenever the room temperature is above the target temperature of the event. The suggested minimum target temperature is 40°C.

---------------------------------------------
Inserting a Thermocouple Control Transition
---------------------------------------------

Thermocouple transition events can switch the control temperature between two thermocouples.

The control temperature is usually equal to the sample temperature for the whole duration of the test. This means that the controller will try to obtain equality between sample temperature and setpoint temperature.

Under some circumstances it is preferable to control the furnace temperature instead, meaning that the controller will emit power to obtain equality between furnace temperature and setpoint.

A typical usage is to pre-heat a motorized furnace while it is opened, in order to obtain a flash heating temperature profile.

To add a control transition, right click and select *Insert control transition*. A dialog will show up, and you'll be able to select to which of the thermocouples move the control and how fast.


.. tip::
    We want to pre-heat the furnace to 1000°C while it is opened, then close it over the sample to flash-heat it. Then, we need to continue the thermal cycle up to 1400°C.

    We should:
        1. Set the "Kiln position before start" in execution options to "Opened".
        2. Insert a thermocouple control transition as the first line of the cycle. We need to pass the control to the furnace in order to pre-heat it.
        3. Insert the pre-heating ramp to 1000°C as usual.
        4. Insert a furnace movement event to close it.
        5. Insert a thermocouple control transition to transfer the control back to the sample thermocouple. This transition should not be instantaneous, because after the movement there will still be turbolence due to thermal inertia. Give the transition a 5°C/min speed. 
        6. Insert the last ramp up to 1400°C as usual. This ramp will be executed while the sample thermocouple is controlling.


.. hint:: This event is meaningful only when your instrument supports more than one thermocouple (samples and/or furnace).

---------------------------------------------
Additional Control Options
---------------------------------------------

Additional control options are displayed under the thermal cycle table. These can influence how the heating cycle and the test are stopped, plus initial and final furnace positions.

Stop after thermal cycle
^^^^^^^^^^^^^^^^^^^^^^^^^^

The *Stop after thermal cycle* flag defines wether the acquisition should stop or not, when the thermal cycle reaches its end. If not, the acquisition will have to be stopped manually.

By clicking on the ``+`` button, two more sub-options are available. These are active only if the *Stop after thermal cycle* flag is checked, and are used to protract the acquisition further after thermal cycle end.

- **Wait T smaller than**: After the cycle is stopped, the test will be stopped as well only when the temperature is smaller than the configured value. Leave zero to disable this behaviour.
- **Wait minutes**: After the cycle is stopped, the test will be stopped as well after a certain amount of additional minutes. Leave zero to disable this behaviour.


Maximum test duration
^^^^^^^^^^^^^^^^^^^^^^^

This option will interrupt the test when the total duration reaches the configured valued. The thermal cycle will be implicitly interrupted.

This option will not *force* the test to have this duration: the test can end before this target duration if any other termination condition is met (end of thermal cycle, error condition, analytical condition).

Leave zero to disable.


Kiln position before start/after end
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

These two options allow to set a position of the furnace before and after the test. These options can be set either on *Closed*, *Opened* or *Unchanged*.

The movement needed to comply with this position will not be recorded in the test result.

The position before start is usually *Closed*, to avoid forgetting the furnace open. It can be set to *Opened* in case we need to pre-heat the furnace and then close on the sample. It should be avoided to set on *Unchanged*.  

The position after end is usually *Unchanged* or *Closed*, to reduce thermal shock on the heating elements. It can be *Opened* to minimize the risk of sample flowing on the furnace or to quickly cool it for the next test.

.. hint:: Available only for instruments with motorized furnaces.



---------------------------------------------
Saving your thermal cycle definition
---------------------------------------------

Once you finished editing your thermal cycle, you can save it to the current cycle name visibile in the upper-right combo box, by clicking on **Save** button.

To save the currently edited cycle with a different name, select the last combo box special entry **+Add**. An input dialog will appear where you can set your cycle name. 

To delete a cycle, select it from the combo box and click **Del** button.

