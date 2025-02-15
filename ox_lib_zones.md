Shared
Faster alternative to PolyZone utilising glm.polygon.

Currently zones only have basic support on the server side. Some features will not work such as onEnter, onExit, and inside.

lib.zones.poly
lib.zones.poly(data)
data: table
points: vector3[]
All z values must match
thickness?: number
Default: 4
onEnter?: function(self: table)
onExit?: function(self: table)
inside?: function(self: table)
debug?: boolean
lib.zones.box
lib.zones.box(data)
data: table
coords: vector3
size?: vector3
Default: vec3(2, 2, 2)
rotation?: number
Angle in degrees
Default: 0
onEnter?: function(self: table)
onExit?: function(self: table)
inside?: function(self: table)
debug?: boolean
lib.zones.sphere
lib.zones.sphere(data)
data: table
coords: vector3
radius?: number
Default: 2
onEnter?: function(self: table)
onExit?: function(self: table)
inside?: function(self: table)
debug?: boolean
Methods
remove
Zones can be deleted by using the remove method. The data will not be cleared from the script, and can be used to recreate a zone later.

local zone = lib.zones.box({...})
 
zone:remove()
 
SetTimeout(500, function()
    lib.zones.poly(zone)
end)
contains
Tests if a point exists inside the zone, returning a boolean.

local zone = lib.zones.box({...})
 
if zone:contains(vec3(1, 1, 1)) then
    print('point is inside zone!')
end
Usage Examples
function onEnter(self)
    print('entered zone', self.id)
end
 
function onExit(self)
    print('exited zone', self.id)
end
 
function inside(self)
    print('you are inside zone ' .. self.id)
end
 
local poly = lib.zones.poly({
    points = {
        vec(413.8, -1026.1, 29),
        vec(411.6, -1023.1, 29),
        vec(412.2, -1018.0, 29),
        vec(417.2, -1016.3, 29),
        vec(422.3, -1020.0, 29),
        vec(426.8, -1015.9, 29),
        vec(431.8, -1013.0, 29),
        vec(437.3, -1018.4, 29),
        vec(432.4, -1027.2, 29),
        vec(424.7, -1023.5, 29),
        vec(420.0, -1030.2, 29),
        vec(409.8, -1028.4, 29),
    },
    thickness = 2,
    debug = true,
    inside = inside,
    onEnter = onEnter,
    onExit = onExit
})
 
local sphere = lib.zones.sphere({
    coords = vec3(442.5363, -1017.666, 28.65637),
    radius = 1,
    debug = true,
    inside = inside,
    onEnter = onEnter,
    onExit = onExit
})
 
local box = lib.zones.box({
    coords = vec3(442.5363, -1017.666, 28.65637),
    size = vec3(1, 1, 1),
    rotation = 45,
    debug = true,
    inside = inside,
    onEnter = onEnter,
    onExit = onExit
})
Zone creation script
You can use our builtin zone-creator with /zone - with poly, box or sphere as an argument.
Available controls will be displayed on the right side.

Zones will be saved to ox_lib/created_zones.lua with your chosen format.

local poly = lib.zones.poly({
    name = poly,
    points = {
        vec(447.9, -998.8, 25.8),
        vec(450.3, -998.2, 25.8),
        vec(449.9, -995.5, 25.8),
        vec(447.2, -995.6, 25.8),
        vec(446.3, -997.9, 25.8),
    },
    thickness = 2,
})