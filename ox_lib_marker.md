Client
lib.marker
Simple way to create markers

Marker Class
A table representing a marker with the following properties.

type: number or string
This field accepts either a numerical value representing the marker ID or a string containing the name of a marker as documented on FiveM Docs.
coords?: vector3
width?: number
height?: number
color?: { r: number, g: number, b: number, a: number}
direction?: vector3
rotation?: vector3
lib.marker.new
lib.marker.new(options)
Returns: Marker
Usage Example
local marker = lib.marker.new({
	type = 1,
	coords = GetEntityCoords(cache.ped),
	color = { r = 255, g = 0, b = 0, a = 200 },
})
 
Citizen.CreateThread(function()
	while true do
		marker:draw()
 
		Citizen.Wait(1)
	end
end)
Interactive Example
 
local center = vec3(430.452759, -1026.108032, 27.846140)
local uiText = "Press [E] to get notified"
 
local point = lib.points.new({
  coords = center,
  distance = 20,
})
 
local marker = lib.marker.new({
  coords = center,
  type = 1,
})
 
function point:nearby()
  marker:draw()
 
  if self.currentDistance < 1.5 then
    if not lib.isTextUIOpen() then
      lib.showTextUI("Press [E] to get notified")
    end
 
    if IsControlJustPressed(0, 51) then
      lib.notify({
        description = "Hello, World!"
      })
    end
  else
  local isOpen, currentText = lib.isTextUIOpen()
    if isOpen and currentText == uiText then
      lib.hideTextUI()
    end
  end
end


-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Shared
lib.math
Extends the standard Lua math table with extra functions.

math = lib.math
math.toscalars
Takes a string and returns a set of scalar values.

math.toscalars(input, min, max, round)
input: string
min?: number
max?: number
round?: boolean
Return:

...: number
math.tovector
Takes a string or table and returns a vector value, or a number if only one value was found.

math.tovector(input, min, max, round)
input: string or table
min?: number
max?: number
round?: boolean
Return:

value: number or vector2 or vector3 or vector4
math.normaltorotation
Takes a surface normal and tries to convert it to a vector3 rotation.

math.normaltorotation(input)
input: vector3
Return:

value: vector3
math.torgba
Takes a string or table and returns a vector value, or a number if only one value was found.
Values are rounded and must be within the range of 0-255.

math.torgba(input)
input: string or table
Return:

value: number or vector2 or vector3 or vector4
math.hextorgb
Takes a hexadecimal string and returns three integers.

math.hextorgb(input)
input: string
A hexadecimal value, e.g. 'eb4034'.
Return:

r: number
g: number
b: number
math.tohex
Takes a number or string and formats it as a hexadecimal string.

math.tohex(n, upper)
n: number or string
upper?: boolean
Return:

hex: string
math.groupdigits
Takes a number and formats it into grouped digits.

math.groupdigits(number, seperator)
number: number
seperator?: string
Default: ,
Return:

groupedDigits: string
math.clamp
Clamps a number between a lower and upper limit.

math.clamp(number, lower, upper)
number: number
lower: number
upper: number
Return:

number: number
math.round
Rounds a number to a whole number or to the specified number of decimal places.

math.round(value, places)
value: number | string
places?: number | string
Return:

roundedValue: number
math.interp
Calculates an intermediate value between start and finish based on the interpolation factor.

math.interp(start, finish, factor)
generic T: number | vector2 | vector3 | vector4
start: T
finish: T
factor: number
The interpolation factor between 0 and 1.
Return:

result: T
math.lerp
Linearly interpolates between two values over a specified duration, returning an iterator function that will run once per game-frame.

math.lerp(start, finish, duration)
generic T: number | table | vector2 | vector3 | vector4
start: T
The starting value of the interpolation
finish: T
The ending value of the interpolation
duration: number
The duration over which to interpolate over in milliseconds.
Return:

iteratorFunction: fun(): T, number

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

