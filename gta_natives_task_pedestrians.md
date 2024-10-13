-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_WANDER_IN_AREA
0xE054346CA3A0F315
0xC6981FB9
// TaskWanderInArea
void TASK_WANDER_IN_AREA(Ped ped, float x, float y, float z, float radius, int minimalLength, float timeBetweenWalks);
Parameters:
ped: The ped which will wander the area.
x: The X coordinate.
y: The Y coordinate
z: The Z coordinate
radius: The radius of the area to wander around in
minimalLength: The minimal length it will wander before waiting timeBetweenWalks seconds before continuing
timeBetweenWalks: The length of time the ped will stand still/rest between walks
Makes a ped wander/patrol around the specified area.

The ped will continue to wander after getting distracted, but only if this additional task is temporary, ie. killing a target, after killing the target it will continue to wander around.

Use GetIsTaskActive(ped, 222) to check if the ped is still wandering the area.

Examples:

Lua
-- Load model for panther
local model = `a_c_panther`
RequestModel(model)
while not HasModelLoaded(model) do
  Citizen.Wait(0)
end

-- Spawn a panther at current coordinates
local coords = GetEntityCoords(PlayerPedId())
local ped = CreatePed(0, model, coords.x, coords.y, coords.z, 0.0, true)

-- Make sure the ped doesn't flee or gets distracted
SetBlockingOfNonTemporaryEvents(ped, true)

-- Make ped wander in spawned area with radius of 100 meters, will wander at least 2 meters and wait for around 10 seconds between patrols
TaskWanderInArea(ped, coords.x, coords.y, coords.z, 100.0, 2, 10.0)

-- Check if the ped is wandering
-- Tasks don't trigger instantly, so wait a bit before checking
Citizen.Wait(1000)
print(GetIsTaskActive(ped, 222)) -- 1

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

_TASK_WANDER_SPECIFIC
0x6919A2F136426098
// TaskWanderSpecific
void _TASK_WANDER_SPECIFIC(Any p0, Any p1, Any p2, Any p3);
NativeDB Introduced: v1868

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_WANDER_STANDARD
0xBB9CE077274F6A1B
0xAF59151A
// TaskWanderStandard
void TASK_WANDER_STANDARD(Ped ped, float p1, int p2);
Makes ped walk around the area.  
set p1 to 10.0f and p2 to 10 if you want the ped to walk anywhere without a duration.  

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

