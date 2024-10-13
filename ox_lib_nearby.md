Shared
lib.getNearbyObjects
Get the object handle and coords of all objects within range of a set of coordinates.

lib.getNearbyObjects(coords, maxDistance)
coords: vector3
The coords to check from.
maxDistance?: number
The max distance to check.
Default: 2.0
Return:

objects: { object: number, coords: vector3 }[]

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Shared
lib.getNearbyPeds
Get the ped handle and coords of all peds within range of a set of coordinates.

lib.getNearbyPeds(coords, maxDistance)
coords: vector3
The coords to check from.
maxDistance?: number
The max distance to check.
Default: 2.0
Return:

peds: { ped: number, coords: vector3 }[]

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Shared
lib.getNearbyPlayers
Get the player id, ped handle, and coords of all players within range of a set of coordinates.

lib.getNearbyPlayers(coords, maxDistance, includePlayer)
coords: vector3
The coords to check from.
maxDistance?: number
The max distance to check.
Default: 2.0
includePlayer?: boolean
Whether or not to include the current player. Ignored on the server.
Default: false
Return:

players: { id: number, ped: number, coords: vector3 }[]

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Shared
lib.getNearbyVehicles
Get the vehicle handle and coords of all vehicles within range of a set of coordinates.

lib.getNearbyVehicles(coords, maxDistance, includePlayerVehicle)
coords: vector3
The coords to check from.
maxDistance?: number
The max distance to check.
Default: 2.0
includePlayerVehicle?: boolean
Whether or not to include the player's current vehicle. Ignored on the server.
Default: false
Return:

vehicles: { vehicle: number, coords: vector3 }[]

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

