Client
lib.raycast.fromCoords
Starts a shapetest originating from starting coordinates and ending at destination coordinates.

lib.raycast.fromCoords(coords, destination, flags, ignore)
coords: vector3
Starting coords for raycast
destination: vector3
Destination coords for raycast
flags?: number
See: https://docs.fivem.net/natives/?_0x377906D8A31E5586
Default: 511
ignore?: number
A bit mask with bits 1, 2, 4, or 7 relating to collider types. 4 and 7 are usually used.
Default: 4
Return:

hit: boolean
Whether or not an entity was hit
entityHit: number
Entity handle of hit entity
endCoords: vector3
Closest coords to where the raycast hit
surfaceNormal: vector3
Normal to the surface that was hit
materialHash: number
lib.raycast.fromCamera
Starts a shapetest originating from the camera, extending to ~10m by default.

lib.raycast.fromCamera(flags, ignore, distance)
flags?: number
See: https://docs.fivem.net/natives/?_0x377906D8A31E5586
Default: 511
ignore?: number
A bit mask with bits 1, 2, 4, or 7 relating to collider types. 4 and 7 are usually used.
Default: 4
distance?: number
Default: 10
Return:

hit: boolean
Whether or not an entity was hit
entityHit: number
Entity handle of hit entity
endCoords: vector3
Closest coords to where the raycast hit
surfaceNormal: vector3
Normal to the surface that was hit
materialHash: number
lib.raycast.cam
lib.raycast.cam is depreciated alias for lib.raycast.fromCamera and may be removed at any time. Use lib.raycast.fromCamera instead!