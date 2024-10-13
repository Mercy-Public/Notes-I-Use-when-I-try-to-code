-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
Client

Functions
pickClosestDoor
Attempt to pick the lock of the closest door. Dependant on server-side checks and may fail.

exports.ox_doorlock:pickClosestDoor()
useClosestDoor
Interact with the closest door. Dependant on server-side checks and may fail.

exports.ox_doorlock:useClosestDoor()

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Server Events

Events
Handlers
These events should not be triggered by any other scripts.

ox_doorlock:stateChanged
Triggered when a doors state is updated.

AddEventHandler('ox_doorlock:stateChanged', function(source, doorId, state, usedItem) end)
source: number or nil
doorId: number
state: boolean
usedItem: string or false or nil

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Server Functions

Functions
Gets data for a door with the given id, matching the id for the database entry.

getDoor
exports.ox_doorlock:getDoor(doorId)
Gets data for a door with the given id, matching the id for the database entry.

id: number
Return:

door: table
getDoorFromName
exports.ox_doorlock:getDoorFromName(name)
Gets data for a door with the given name, matching the name for the database entry.

name: string
Return:

door: table
editDoor
exports.ox_doorlock:editDoor(doorId, data)
Edit configuration for the given doorId.

doorId: number
data: table
setDoorState
exports.ox_doorlock:setDoorState(doorId, state)
Sets a door with the given doorId as locked if state is true or 1.

doorId: number
state: 0 or 1 or boolean

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

