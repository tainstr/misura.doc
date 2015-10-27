=================================
Thermal Cycle Designer
=================================

The Thermal Cycle Designer contains the controls to setup the wanted thermal cycle.

It is divided in three parts:
1. The upper area contains a table where you can define the thermal cycle.
2. The middle area contains general termination options and furnace positions before the start or after the end of the test (if the furnace is motorized).
3. The lower area displayes a plot of temperature and heating rate against forecasted time.

To set a thermal cycle, you have to insert your desired values in the upper table. Each row of this table represents a target status to be reached by the furnace as the test execution proceeds, and how that status should be reached by the temperature controller.

It has four column:
    1. **Time**: the expected end time of the row, relative to the start of the test (zero).
    2. **Temperature**: the target setpoint of the row, which the furnace controller will try to reach by modulating power emission.
    3. **Heating Rate**: the rate by which the temperature is changed from the previous row up (or down to) to the target setpoint.
    4. **Duration**: the expected duration needed to finish the row.

To insert or delete rows you can use the **Edit** menu or the context menu appearing by right-clicking on the table. On insert, a new row will be added after the currently selected row. On **Remove current line**, the current row will be removed from the table. On insert/delete/edit of a row, all subsequent rows might get automatically updated to reflect the changes (eg: in Time column).

The **File** menu allows to import/export from CSV (comma separed values) text files and to completely clear the table.

#### AUTOUPDATE/AUTOCORRECTION

-------------------------------------
Inserting a Temperature Ramp (Point)
-------------------------------------

A temperature ramp is defined by a setpoint temperature and a time by which that temperature must be reached by the furnace (a time, temperature point). Before you input the target temperature, you should input either the end time of the ramp (**Time** column), or the desired **Heating Rate**, or the **Duration** of the ramp. 

After having defined one of the three columns, you can input the **Temperature** target for that row. The remaining columns will be filled accordingly.

The default way of defining the ramp is by setting the **Heating Rate** column (Celsius per minute). The row **Time** and **Duration** will be auto-filled. 

Filling the **Duration** column is mostly useful to express dwell ramps, where the heating rate is zero and the temperature must be kept fixed for a certain duration.

To add a temperature ramp to the table:
    1. Right click on the row before the position where you want the new row to appear and select *Insert point*. 
    2. Once the row appears, double-click either on the Heating Rate, Duration or Time cell and set the correct value.
    3. Double-click on the Temperature cell and insert the target setpoint.
    4. Other cells will be automatically calculated.
    5. Subsequent rows in the table will be re-calculated as needed.
    
.. hint:: Use negative values to express controlled cooling.

--------------------------
Inserting a Checkpoint
--------------------------

When a checkpoint row is reached, the setpoint will be kept constant until the real furnace temperature reaches it within a tolerance or a timeout expires. 
(wait until a given temperature is reached or a given timeout has expired)
To add a checkpoint, right click and select *Insert checkpoint*. A dialog will show up, where you'll be able insert the desired temperature and timeout.


-----------------------------------
Inserting a Furnace Movement
-----------------------------------

(open or close the furnace)
To add a movement, right click and select *Insert movement*. A dialog will show up, and you'll be able to select a *Open* or *Close* furnace movement.

-----------------------------------
Inserting a Natural Cooling
-----------------------------------

(do not emit power until the temperature drops below a target value)


---------------------------------------------
Inserting a Thermocouple Control Transition
---------------------------------------------

(change which thermocouple is used to control the cycle)
To add a control transition, right click and select *Insert control transition*. A dialog will show up, and you'll be able to select to which of the thermocouples move the control and how fast.



---------------------------------------------
Additional Control Options
---------------------------------------------

The *Stop after thermal cycle* flag defines wether the acquisition should stop or not, when the thermal cycle reaches its end. If not, the acquisition will have to be stopped manually.

---------------------------------------------
Managing multiple thermal cycle definitions
---------------------------------------------


