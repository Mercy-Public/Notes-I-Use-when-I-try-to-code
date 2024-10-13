-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_USE_NEAREST_SCENARIO_TO_COORD
0x277F471BA9DB000B
0x9C50FBF0
// TaskUseNearestScenarioToCoord
void TASK_USE_NEAREST_SCENARIO_TO_COORD(Ped ped, float x, float y, float z, float distance, int duration);
Updated variables
An alternative to TASK::TASK_USE_NEAREST_SCENARIO_TO_COORD_WARP. Makes the ped walk to the scenario instead.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_USE_NEAREST_SCENARIO_TO_COORD_WARP
0x58E2E0F23F6B76C3
0x1BE9D65C
// TaskUseNearestScenarioToCoordWarp
void TASK_USE_NEAREST_SCENARIO_TO_COORD_WARP(Ped ped, float x, float y, float z, float radius, Any p5);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_AIM_AT_COORD
0x447C1E9EF844BC0F
0x010F47CE
// TaskVehicleAimAtCoord
void TASK_VEHICLE_AIM_AT_COORD(Ped ped, float x, float y, float z);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_AIM_AT_PED
0xE41885592B08B097
0x920AE6DB
// TaskVehicleAimAtPed
void TASK_VEHICLE_AIM_AT_PED(Ped ped, Ped target);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_CHASE
0x3C08A8E30363B353
0x55634798
// TaskVehicleChase
void TASK_VEHICLE_CHASE(Ped driver, Entity targetEnt);
chases targetEnt fast and aggressively  
--  
Makes ped (needs to be in vehicle) chase targetEnt.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_DRIVE_TO_COORD
0xE2A2AA2F659D77A7
0xE4AC0387
// TaskVehicleDriveToCoord
void TASK_VEHICLE_DRIVE_TO_COORD(Ped ped, Vehicle vehicle, float x, float y, float z, float speed, Any p6, Hash vehicleModel, int drivingMode, float stopRange, float p10);
info about driving modes: HTTP://gtaforums.com/topic/822314-guide-driving-styles/  
---------------------------------------------------------------  
Passing P6 value as floating value didn't throw any errors, though unsure what is it exactly, looks like radius or something.  
P10 though, it is mentioned as float, however, I used bool and set it to true, that too worked.  
Here the e.g. code I used  
Function.Call(Hash.TASK_VEHICLE_DRIVE_TO_COORD, Ped, Vehicle, Cor X, Cor Y, Cor Z, 30f, 1f, Vehicle.GetHashCode(), 16777216, 1f, true); 

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_DRIVE_TO_COORD_LONGRANGE
0x158BB33F920D360C
0x1490182A
// TaskVehicleDriveToCoordLongrange
void TASK_VEHICLE_DRIVE_TO_COORD_LONGRANGE(Ped ped, Vehicle vehicle, float x, float y, float z, float speed, int driveMode, float stopRange);
Parameters:
ped: Ped id for the task.
vehicle: Vehicle entity id for the task.
x: Destination X coordinate.
y: Destination Y coordinate.
z: Destination Z coordinate.
speed: Speed of driving.
driveMode: More info can be found here
stopRange: Stops in the specific range near the destination. 20.0 works fine.
You can let your character drive to the destination at the speed and driving style you set. You can use map marks to set the destination.

Examples:

C#
// A short example showcasing how this native works with map marks.

// Get the map mark location.
Vector3 destination = GetBlipInfoIdCoord(GetFirstBlipInfoId(8));

// If no mark is set, return immediately.
if (destination == Vector3.Zero)
{
    return;
}

TaskVehicleDriveToCoordLongrange(Game.PlayerPed.Handle, Game.PlayerPed.CurrentVehicle.Handle, destination.X, destination.Y, destination.Z, 60f, 447, 20f);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_DRIVE_WANDER
0x480142959D337D00
0x36EC0EB0
// TaskVehicleDriveWander
void TASK_VEHICLE_DRIVE_WANDER(Ped ped, Vehicle vehicle, float speed, int drivingStyle);
Parameters:
ped: Ped id for the task.
vehicle: Vehicle entity id for the task.
speed: Speed of driving.
drivingStyle: More info can be found here
Drive randomly with no destination set.

Examples:

C#
TaskVehicleDriveWander(Game.PlayerPed.Handle, Game.PlayerPed.CurrentVehicle.Handle, 60f, 447);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_ESCORT
0x0FA6E4B75F302400
0x9FDCB250
// TaskVehicleEscort
void TASK_VEHICLE_ESCORT(Ped ped, Vehicle vehicle, Vehicle targetVehicle, int mode, float speed, int drivingStyle, float minDistance, int p7, float noRoadsDistance);
Makes a ped follow the targetVehicle with <minDistance> in between.  
note: minDistance is ignored if drivingstyle is avoiding traffic, but Rushed is fine.  
Mode: The mode defines the relative position to the targetVehicle. The ped will try to position its vehicle there.  
-1 = behind  
0 = ahead  
1 = left  
2 = right  
3 = back left  
4 = back right  
if the target is closer than noRoadsDistance, the driver will ignore pathing/roads and follow you directly.  
Driving Styles guide: gtaforums.com/topic/822314-guide-driving-styles/  

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_FOLLOW
0xFC545A9F0626E3B6
0xA8B917D7
// TaskVehicleFollow
void TASK_VEHICLE_FOLLOW(Ped driver, Vehicle vehicle, Entity targetEntity, float speed, int drivingStyle, int minDistance);
Makes a ped in a vehicle follow an entity (ped, vehicle, etc.)
drivingStyle: http://gtaforums.com/topic/822314-guide-driving-styles/
Old name: _TASK_VEHICLE_FOLLOW

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_FOLLOW_WAYPOINT_RECORDING
0x3123FAA6DB1CF7ED
0x959818B6
// TaskVehicleFollowWaypointRecording
void TASK_VEHICLE_FOLLOW_WAYPOINT_RECORDING(Ped ped, Vehicle vehicle, char* WPRecording, int p3, int p4, int p5, int p6, float p7, BOOL p8, float p9);
task_vehicle_follow_waypoint_recording(Ped p0, Vehicle p1, string p2, int p3, int p4, int p5, int p6, float.x p7, float.Y p8, float.Z p9, bool p10, int p11)
p2 = Waypoint recording string (found in update\update.rpf\x64\levels\gta5\waypointrec.rpf
p3 = 786468
p4 = 0
p5 = 16
p6 = -1 (angle?)
p7/8/9 = usually v3.zero
p10 = bool (repeat?)
p11 = 1073741824
-khorio

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_GOTO_NAVMESH
0x195AEEB13CEFE2EE
0x55CF3BCD
// TaskVehicleGotoNavmesh
void TASK_VEHICLE_GOTO_NAVMESH(Ped ped, Vehicle vehicle, float x, float y, float z, float speed, int behaviorFlag, float stoppingRange);
Differs from TASK_VEHICLE_DRIVE_TO_COORDS in that it will pick the shortest possible road route without taking one-way streets and other "road laws" into consideration.  
WARNING:  
A behaviorFlag value of 0 will result in a clunky, stupid driver!  
Recommended settings:  
speed = 30.0f,  
behaviorFlag = 156,   
stoppingRange = 5.0f;  
If you simply want to have your driver move to a fixed location, call it only once, or, when necessary in the event of interruption.   
If using this to continually follow a Ped who is on foot:  You will need to run this in a tick loop.  Call it in with the Ped's updated coordinates every 20 ticks or so and you will have one hell of a smart, fast-reacting NPC driver -- provided he doesn't get stuck.  If your update frequency is too fast, the Ped may not have enough time to figure his way out of being stuck, and thus, remain stuck.  One way around this would be to implement an "anti-stuck" mechanism, which allows the driver to realize he's stuck, temporarily pause the tick, unstuck, then resume the tick. 

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_HELI_PROTECT
0x1E09C32048FEFD1C
0x0CB415EE
// TaskVehicleHeliProtect
void TASK_VEHICLE_HELI_PROTECT(Ped pilot, Vehicle vehicle, Entity entityToFollow, float targetSpeed, int p4, float radius, int altitude, int p7);
pilot, vehicle and altitude are rather self-explanatory.  
p4: is unused variable in the function.  
entityToFollow: you can provide a Vehicle entity or a Ped entity, the heli will protect them.  
'targetSpeed':  The pilot will dip the nose AS MUCH AS POSSIBLE so as to reach this value AS FAST AS POSSIBLE.  As such, you'll want to modulate it as opposed to calling it via a hard-wired, constant #.  
'radius' isn't just "stop within radius of X of target" like with ground vehicles.  In this case, the pilot will fly an entire circle around 'radius' and continue to do so.  
NOT CONFIRMED:  p7 appears to be a FlyingStyle enum.  Still investigating it as of this writing, but playing around with values here appears to result in different -behavior- as opposed to offsetting coordinates, altitude, target speed, etc.  
NOTE: If the pilot finds enemies, it will engage them until it kills them, but will return to protect the ped/vehicle given shortly thereafter.  


TASK_VEHICLE_MISSION
0x659427E0EF36BCDE
0x20609E56
// TaskVehicleMission
void TASK_VEHICLE_MISSION(Ped driver, Vehicle vehicle, Vehicle vehicleTarget, int missionType, float p4, Any p5, float p6, float p7, BOOL DriveAgainstTraffic);
missionType: https://alloc8or.re/gta5/doc/enums/eVehicleMissionType.txt

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_MISSION_COORS_TARGET
0xF0AF20AA7731F8C3
0x6719C109
// TaskVehicleMissionCoorsTarget
void TASK_VEHICLE_MISSION_COORS_TARGET(Ped ped, Vehicle vehicle, float x, float y, float z, int p5, int p6, int p7, float p8, float p9, BOOL DriveAgainstTraffic);
See TASK_VEHICLE_MISSION.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_MISSION_PED_TARGET
0x9454528DF15D657A
0xC81C4677
// TaskVehicleMissionPedTarget
void TASK_VEHICLE_MISSION_PED_TARGET(Ped ped, Vehicle vehicle, Ped pedTarget, int missionType, float maxSpeed, int drivingStyle, float minDistance, float p7, BOOL DriveAgainstTraffic);
See TASK_VEHICLE_MISSION.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_PARK
0x0F3E34E968EA374E
0x5C85FF90
// TaskVehiclePark
void TASK_VEHICLE_PARK(Ped ped, Vehicle vehicle, float x, float y, float z, float heading, int mode, float radius, BOOL keepEngineOn);
Modes:  
0 - ignore heading  
1 - park forward  
2 - park backwards  
Depending on the angle of approach, the vehicle can park at the specified heading or at its exact opposite (-180) angle.  
Radius seems to define how close the vehicle has to be -after parking- to the position for this task considered completed. If the value is too small, the vehicle will try to park again until it's exactly where it should be. 20.0 Works well but lower values don't, like the radius is measured in centimeters or something.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_PLAY_ANIM
0x69F5C3BD0F3EBD89
0x2B28F598
// TaskVehiclePlayAnim
void TASK_VEHICLE_PLAY_ANIM(Vehicle vehicle, char* animationSet, char* animationName);
Most probably plays a specific animation on vehicle. For example getting chop out of van etc...
Here's how its used -
TASK::TASK_VEHICLE_PLAY_ANIM(l_325, "rcmnigel1b", "idle_speedo");
TASK::TASK_VEHICLE_PLAY_ANIM(l_556[0/*1*/], "missfra0_chop_drhome", "InCar_GetOutofBack_Speedo");
FYI : Speedo is the name of van in which chop was put in the mission.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_SHOOT_AT_COORD
0x5190796ED39C9B6D
0xA7AAA4D6
// TaskVehicleShootAtCoord
void TASK_VEHICLE_SHOOT_AT_COORD(Ped ped, float x, float y, float z, float p4);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_SHOOT_AT_PED
0x10AB107B887214D8
0x59677BA0
// TaskVehicleShootAtPed
void TASK_VEHICLE_SHOOT_AT_PED(Ped ped, Ped target, float p2);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

TASK_VEHICLE_TEMP_ACTION
0xC429DCEEB339E129
0x0679DFB8
// TaskVehicleTempAction
void TASK_VEHICLE_TEMP_ACTION(Ped driver, Vehicle vehicle, int action, int time);
'1 - brake
'3 - brake + reverse
'4 - turn left 90 + braking
'5 - turn right 90 + braking
'6 - brake strong (handbrake?) until time ends
'7 - turn left + accelerate
'7 - turn right + accelerate
'9 - weak acceleration
'10 - turn left + restore wheel pos to center in the end
'11 - turn right + restore wheel pos to center in the end
'13 - turn left + go reverse
'14 - turn left + go reverse
'16 - crash the game after like 2 seconds :)
'17 - keep actual state, game crashed after few tries
'18 - game crash
'19 - strong brake + turn left/right
'20 - weak brake + turn left then turn right
'21 - weak brake + turn right then turn left
'22 - brake + reverse
'23 - accelerate fast
'24 - brake
'25 - brake turning left then when almost stopping it turns left more
'26 - brake turning right then when almost stopping it turns right more
'27 - brake until car stop or until time ends
'28 - brake + strong reverse acceleration
'30 - performs a burnout (brake until stop + brake and accelerate)
'31 - accelerate + handbrake
'32 - accelerate very strong
Seems to be this:
Works on NPCs, but overrides their current task. If inside a task sequence (and not being the last task), "time" will work, otherwise the task will be performed forever until tasked with something else

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------