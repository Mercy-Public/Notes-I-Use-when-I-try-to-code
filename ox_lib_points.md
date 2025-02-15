Client
Simple and centralised distance checking, supporting callbacks when entering, leaving, and standing in-range of set coordinates.

CPoint Class
A table representing a point with the following properties.

id: number
coords: vector3
distance: number
The distance for the player to be "inside" a point (i.e. the point's radius).
currentDistance: number
The players current distance from the centre of the point.
isClosest?: boolean
remove: function()
Removes the point from the points registry.
onEnter?: function(self: CPoint)
Function triggered when player gets within distance of the point
onExit?: function(self: CPoint)
Function triggered when player goes beyond distance of the point
nearby?: function(self: CPoint)
Function triggered on frame when within distance of the point
lib.points.new
lib.points.new(data)
data: table
coords: vector3
distance: number
Returns:

point: CPoint
Usage Example
local point = lib.points.new({
    coords = GetEntityCoords(cache.ped),
    distance = 5,
    dunak = 'nerd',
})
 
function point:onEnter()
    print('entered range of point', self.id)
end
 
function point:onExit()
    print('left range of point', self.id)
end
 
function point:nearby()
    DrawMarker(2, self.coords.x, self.coords.y, self.coords.z, 0.0, 0.0, 0.0, 0.0, 180.0, 0.0, 1.0, 1.0, 1.0, 200, 20, 20, 50, false, true, 2, false, nil, nil, false)
 
    if self.currentDistance < 1 and IsControlJustReleased(0, 38) then
        print('inside marker', self.id, 'dunak is a '.. self.dunak)
    end
end
lib.points.getAllPoints
Get a table of all points created in the resource.

lib.points.getAllPoints()
Return:

points: CPoint[]
lib.points.getNearbyPoints
Get an array of all points in range of the player.

lib.points.getNearbyPoints()
Return:

nearbyPoints: CPoint[]
lib.points.getClosestPoint
Get the data for the closest point to the player.

lib.points.getClosestPoint()
Return:

closestPoint?: CPoint