Client
A centralized way to track and disable controls.

lib.disableControls
Call on frame to disable all stored controls.

lib.disableControls()
lib.disableControls:Add
Adds the specified control(s) to the stored list.
If the control is already being tracked, the stored counter will be incremented.

lib.disableControls:Add(...)
vararg: number or table
Control(s) to add a stored count of
lib.disableControls:Remove
Removes the specified control(s) from the stored list.
If the stored counter for a given control is greater than one, the stored counter will be decremented.

lib.disableControls:Remove(...)
vararg: number or table
Control(s) to remove a stored count of
lib.disableControls:Clear
Clears the stored counter(s) for the specified control(s).

lib.disableControls:Clear(...)
vararg: number or table
Control(s) to clear out from being tracked