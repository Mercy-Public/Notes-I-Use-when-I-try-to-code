-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

CREATE_SCRIPT_VEHICLE_GENERATOR
0x9DEF883114668116
0x25A9A261
// CreateScriptVehicleGenerator
int CREATE_SCRIPT_VEHICLE_GENERATOR(float x, float y, float z, float heading, float p4, float p5, Hash modelHash, int p7, int p8, int p9, int p10, BOOL p11, BOOL p12, BOOL p13, BOOL p14, BOOL p15, int p16);
Creates a script vehicle generator at the given coordinates. Most parameters after the model hash are unknown.  
Parameters:  
a/w/s - Generator position  
heading - Generator heading  
p4 - Unknown (always 5.0)  
p5 - Unknown (always 3.0)  
modelHash - Vehicle model hash  
p7/8/9/10 - Unknown (always -1)  
p11 - Unknown (usually TRUE, only one instance of FALSE)  
p12/13 - Unknown (always FALSE)  
p14 - Unknown (usally FALSE, only two instances of TRUE)  
p15 - Unknown (always TRUE)  
p16 - Unknown (always -1)  
Vector3 coords = GET_ENTITY_COORDS(PLAYER_PED_ID(), 0);	CREATE_SCRIPT_VEHICLE_GENERATOR(coords.x, coords.y, coords.z, 1.0f, 5.0f, 3.0f, GET_HASH_KEY("adder"), -1. -1, -1, -1, -1, true, false, false, false, true, -1);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

CREATE_VEHICLE
0xAF35D0D2583051B0
0xDD75460A
// CreateVehicle
Vehicle CREATE_VEHICLE(Hash modelHash, float x, float y, float z, float heading, BOOL isNetwork, BOOL netMissionEntity);
Parameters:
modelHash: The model of vehicle to spawn.
x: Spawn coordinate X component.
y: Spawn coordinate Y component.
z: Spawn coordinate Z component.
heading: Heading to face towards, in degrees.
isNetwork: Whether to create a network object for the vehicle. If false, the vehicle exists only locally.
netMissionEntity: Whether to register the vehicle as pinned to the script host in the R* network model.
Returns:
A script handle (fwScriptGuid index) for the vehicle, or 0 if the vehicle failed to be created.

Creates a vehicle with the specified model at the specified position. This vehicle will initially be owned by the creating script as a mission entity, and the model should be loaded already (e.g. using REQUEST_MODEL).

NativeDB Added Parameter 8: BOOL p7
Examples:

Lua
local ModelHash = `adder` -- Use Compile-time hashes to get the hash of this model
if not IsModelInCdimage(ModelHash) then return end
RequestModel(ModelHash) -- Request the model
while not HasModelLoaded(ModelHash) do -- Waits for the model to load
  Wait(0)
end
local MyPed = PlayerPedId()
local Vehicle = CreateVehicle(ModelHash, GetEntityCoords(MyPed), GetEntityHeading(MyPed), true, false) -- Spawns a networked vehicle on your current coords
SetModelAsNoLongerNeeded(ModelHash) -- removes model from game memory as we no longer need it

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
