-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_WARP_PED_INTO_VEHICLE
0x65D4A35D
// TaskWarpPedIntoVehicle
void TASK_WARP_PED_INTO_VEHICLE(Ped ped, Vehicle vehicle, int seatIndex);
TASK_WARP_PED_INTO_VEHICLE

This is the server-side RPC native equivalent of the client native TASK_WARP_PED_INTO_VEHICLE.

TASK_WARP_PED_INTO_VEHICLE
0x9A7D091411C5F684
0x65D4A35D
// TaskWarpPedIntoVehicle
void TASK_WARP_PED_INTO_VEHICLE(Ped ped, Vehicle vehicle, int seatIndex);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

ALLOW_MISSION_CREATOR_WARP
0xDEA36202FC3382DF
0x082BA6F2
// AllowMissionCreatorWarp
void ALLOW_MISSION_CREATOR_WARP(BOOL toggle);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_WARP_PED_INTO_VEHICLE
0x9A7D091411C5F684
0x65D4A35D
// TaskWarpPedIntoVehicle
void TASK_WARP_PED_INTO_VEHICLE(Ped ped, Vehicle vehicle, int seatIndex);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

ADD_VEHICLE_STUCK_CHECK_WITH_WARP
0x2FA9923062DD396C
0xC8B789AD
// AddVehicleStuckCheckWithWarp
void ADD_VEHICLE_STUCK_CHECK_WITH_WARP(Any p0, float p1, Any p2, BOOL p3, BOOL p4, BOOL p5, Any p6);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

IS_SEAT_WARP_ONLY
0xF7F203E31F96F6A1
0x769E5CF2
// IsSeatWarpOnly
BOOL IS_SEAT_WARP_ONLY(Vehicle vehicle, int seatIndex);
Parameters:
vehicle: The vehicle to check.
seatIndex: See eSeatPosition declared in IS_VEHICLE_SEAT_FREE.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------