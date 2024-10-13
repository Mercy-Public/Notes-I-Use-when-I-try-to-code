-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_ENTITY_LOAD_COLLISION_FLAG
0x0DC7CABAB1E9B67E
0xC52F295B
// SetEntityLoadCollisionFlag
void SET_ENTITY_LOAD_COLLISION_FLAG(Entity entity, BOOL toggle);
Loads collision grid for an entity spawned outside of a player's loaded area. This allows peds to execute tasks rather than sit dormant because of a lack of a physics grid.

Certainly not the main usage of this native but when set to true for a Vehicle, it will prevent the vehicle to explode if it is spawned far away from the player.

NativeDB Added Parameter 3: Any p2


ADD_EXPLOSION
0xE3AD2BDBAEE269AC
0x10AF5258
// AddExplosion
void ADD_EXPLOSION(float x, float y, float z, int explosionType, float damageScale, BOOL isAudible, BOOL isInvisible, float cameraShake);
NativeDB Added Parameter 9: BOOL noDamage
BOOL isAudible = If explosion makes a sound.  
BOOL isInvisible = If the explosion is invisible or not.
BOOL noDamage = false: damage || nodamage = true: no damage
enum class eExplosionTag : uint32_t
{
    DONTCARE = 0xFFFFFFFF,
    GRENADE = 0,
    GRENADELAUNCHER = 1,
    STICKYBOMB = 2,
    MOLOTOV = 3,
    ROCKET = 4,
    TANKSHELL = 5,
    HI_OCTANE = 6,
    CAR = 7,
    PLANE = 8,
    PETROL_PUMP = 9,
    BIKE = 10,
    DIR_STEAM = 11,
    DIR_FLAME = 12,
    DIR_WATER_HYDRANT = 13,
    DIR_GAS_CANISTER = 14,
    BOAT = 15,
    SHIP_DESTROY = 16,
    TRUCK = 17,
    BULLET = 18,
    SMOKEGRENADELAUNCHER = 19,
    SMOKEGRENADE = 20,
    BZGAS = 21,
    FLARE = 22,
    GAS_CANISTER = 23,
    EXTINGUISHER = 24,
    _0x988620B8 = 25,
    EXP_TAG_TRAIN = 26,
    EXP_TAG_BARREL = 27,
    EXP_TAG_PROPANE = 28,
    EXP_TAG_BLIMP = 29,
    EXP_TAG_DIR_FLAME_EXPLODE = 30,
    EXP_TAG_TANKER = 31,
    PLANE_ROCKET = 32,
    EXP_TAG_VEHICLE_BULLET = 33,
    EXP_TAG_GAS_TANK = 34,
    EXP_TAG_BIRD_CRAP = 35,
    EXP_TAG_RAILGUN = 36,
    EXP_TAG_BLIMP2 = 37,
    EXP_TAG_FIREWORK = 38,
    EXP_TAG_SNOWBALL = 39,
    EXP_TAG_PROXMINE = 40,
    EXP_TAG_VALKYRIE_CANNON = 41,
    EXP_TAG_AIR_DEFENCE = 42,
    EXP_TAG_PIPEBOMB = 43,
    EXP_TAG_VEHICLEMINE = 44,
    EXP_TAG_EXPLOSIVEAMMO = 45,
    EXP_TAG_APCSHELL = 46,
    EXP_TAG_BOMB_CLUSTER = 47,
    EXP_TAG_BOMB_GAS = 48,
    EXP_TAG_BOMB_INCENDIARY = 49,
    EXP_TAG_BOMB_STANDARD = 50,
    EXP_TAG_TORPEDO = 51,
    EXP_TAG_TORPEDO_UNDERWATER = 52,
    EXP_TAG_BOMBUSHKA_CANNON = 53,
    EXP_TAG_BOMB_CLUSTER_SECONDARY = 54,
    EXP_TAG_HUNTER_BARRAGE = 55,
    EXP_TAG_HUNTER_CANNON = 56,
    EXP_TAG_ROGUE_CANNON = 57,
    EXP_TAG_MINE_UNDERWATER = 58,
    EXP_TAG_ORBITAL_CANNON = 59,
    EXP_TAG_BOMB_STANDARD_WIDE = 60,
    EXP_TAG_EXPLOSIVEAMMO_SHOTGUN = 61,
    EXP_TAG_OPPRESSOR2_CANNON = 62,
    EXP_TAG_MORTAR_KINETIC = 63,
    EXP_TAG_VEHICLEMINE_KINETIC = 64,
    EXP_TAG_VEHICLEMINE_EMP = 65,
    EXP_TAG_VEHICLEMINE_SPIKE = 66,
    EXP_TAG_VEHICLEMINE_SLICK = 67,
    EXP_TAG_VEHICLEMINE_TAR = 68,
    EXP_TAG_SCRIPT_DRONE = 69,
    EXP_TAG_RAYGUN = 70,
    EXP_TAG_BURIEDMINE = 71,
    EXP_TAG_SCRIPT_MISSILE = 72,
    EXP_TAG_RCTANK_ROCKET = 73,
    EXP_TAG_BOMB_WATER = 74,
    EXP_TAG_BOMB_WATER_SECONDARY = 75,
    _0xF728C4A9 = 76,
    _0xBAEC056F = 77,
    EXP_TAG_FLASHGRENADE = 78,
    EXP_TAG_STUNGRENADE = 79,
    _0x763D3B3B = 80,
    EXP_TAG_SCRIPT_MISSILE_LARGE = 81,
    EXP_TAG_SUBMARINE_BIG = 82,
};

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

NETWORK_EXPLODE_HELI
0x2A5E0621DD815A9A
0x955B31BF
// NetworkExplodeHeli
void NETWORK_EXPLODE_HELI(Vehicle heli, BOOL isAudible, BOOL isInvisible, int netScriptEntityId);
Parameters:
heli: Heli to explode
isAudible:
isInvisible:
netScriptEntityId:

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

NETWORK_EXPLODE_VEHICLE
0x301A42153C9AD707
0x0E1B38AE
// NetworkExplodeVehicle
void NETWORK_EXPLODE_VEHICLE(Vehicle vehicle, BOOL isAudible, BOOL isInvisible, BOOL p3);
In the console script dumps, this is only referenced once.   
NETWORK::NETWORK_EXPLODE_VEHICLE(vehicle, 1, 0, 0);  
^^^^^ That must be PC script dumps? In X360 Script Dumps it is reference a few times with 2 differences in the parameters.  
Which as you see below is 1, 0, 0 + 1, 1, 0 + 1, 0, and a *param?  
am_plane_takedown.c   
network_explode_vehicle(net_to_veh(Local_40.imm_2), 1, 1, 0);  
armenian2.c   
network_explode_vehicle(Local_80[6 <2>], 1, 0, 0);  
fm_horde_controler.c  
network_explode_vehicle(net_to_veh(*uParam0), 1, 0, *uParam0);  
fm_mission_controller.c, has 6 hits so not going to list them.  
Side note, setting the first parameter to 0 seems to mute sound or so?  
Seems it's like ADD_EXPLOSION, etc. the first 2 params. The 3rd atm no need to worry since it always seems to be 0.  

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

EXPLODE_PED_HEAD
0x2D05CED3A38D0F3A
0x05CC1380
// ExplodePedHead
void EXPLODE_PED_HEAD(Ped ped, Hash weaponHash);
Parameters:
ped: The ped to lethally injure.
weaponHash: The weapon to attribute the damage to.
Applies lethal damage (FLT_MAX) to the SKEL_Head bone of the specified ped using the weapon passed, leading to the ped's untimely demise.

The naming of the native is a legacy leftover (formerly EXPLODE_CHAR_HEAD in GTA3) as in the early 3D GTA games, lethal damage to a ped head would 'explode' it.

Do note that this native function does not work in multiplayer/network environment.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

EXPLODE_VEHICLE
0xBA71116ADF5B514C
0xBEDEACEB
// ExplodeVehicle
void EXPLODE_VEHICLE(Vehicle vehicle, BOOL isAudible, BOOL isInvisible);
Explodes a selected vehicle.  
Vehicle vehicle = Vehicle you want to explode.  
BOOL isAudible = If explosion makes a sound.  
BOOL isInvisible = If the explosion is invisible or not.  
First BOOL does not give any visual explosion, the vehicle just falls apart completely but slowly and starts to burn. 

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

EXPLODE_VEHICLE_IN_CUTSCENE
0x786A4EB67B01BF0B
0xA85207B5
// ExplodeVehicleInCutscene
void EXPLODE_VEHICLE_IN_CUTSCENE(Vehicle vehicle, BOOL p1);

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_DISABLE_EXPLODE_FROM_BODY_DAMAGE_ON_COLLISION
0x26E13D440E7F6064
// SetDisableExplodeFromBodyDamageOnCollision
void SET_DISABLE_EXPLODE_FROM_BODY_DAMAGE_ON_COLLISION(Vehicle vehicle, BOOL disableExplode);
Parameters:
vehicle: The vehicle to apply this setting to.
disableExplode: true to disable explosion from body damage on collision; false to allow explosions as normal.
Prevents a vehicle from exploding upon sustaining body damage from physical collisions. This can be used to increase the durability of vehicles in high-impact scenarios, such as races or combat situations, by preventing them from being destroyed due to collision-induced body damage.

For helicopters, you might want to check SET_DISABLE_HELI_EXPLODE_FROM_BODY_DAMAGE instead.

NativeDB Introduced: v1290
Examples:

Lua
javascript
csharp
-- Retrieve the player ped
local playerPed = PlayerPedId()

-- Retrieve the vehicle the player is currently in
local vehicle = GetVehiclePedIsIn(playerPed, false)

-- Disable explosion from body damage on collision for the vehicle
SetDisableExplodeFromBodyDamageOnCollision(vehicle, true)

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_DISABLE_HELI_EXPLODE_FROM_BODY_DAMAGE
0xEDBC8405B3895CC9
// SetDisableHeliExplodeFromBodyDamage
void SET_DISABLE_HELI_EXPLODE_FROM_BODY_DAMAGE(Vehicle helicopter, BOOL disableExplode);
Parameters:
helicopter: The helicopter to apply this setting to.
disableExplode: true to disable explosion from body damage on collision; false to allow explosions as normal.
Prevents a helicopter from exploding due to relatively minor body damage. This native can be particularly useful in gameplay scenarios or missions where helicopters are subject to damage that would not realistically cause an explosion, ensuring they remain operational unless subjected to more significant damage.

NativeDB Introduced: v1103
Examples:

Lua
javascript
csharp
-- Retrieve the player ped.
local playerPed = PlayerPedId()

-- Retrieve the helicopter the player is currently in.
local helicopter = GetVehiclePedIsIn(playerPed, false)

-- If the player is not in a helicopter, or the vehicle is not a helicopter, return.
if (helicopter == 0) or (not IsThisModelAHeli(GetEntityModel(helicopter))) then return end

-- Disable explosion from body damage for the helicopter.
SetDisableHeliExplodeFromBodyDamage(helicopter, true)

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_HELI_TAIL_EXPLODE_THROW_DASHBOARD
0x3EC8BF18AA453FE9
0x2916D69B
// SetHeliTailExplodeThrowDashboard
void SET_HELI_TAIL_EXPLODE_THROW_DASHBOARD(Vehicle vehicle, BOOL p1);
Old name: WAS_COUNTER_ACTIVATED

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_VEHICLE_DROPS_MONEY_WHEN_BLOWN_UP
0x068F64F2470F9656
0x4BB5605D
// SetVehicleDropsMoneyWhenBlownUp
void SET_VEHICLE_DROPS_MONEY_WHEN_BLOWN_UP(Vehicle vehicle, BOOL toggle);
Money pickups are created around cars when they explode. Only works when the vehicle model is a car. A single pickup is between 1 and 18 dollars in size. All car models seem to give the same amount of money.
youtu.be/3arlUxzHl5Y
i.imgur.com/WrNpYFs.jpg
Old name: _SET_VEHICLE_CREATES_MONEY_PICKUPS_WHEN_EXPLODED

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_VEHICLE_EXPLODES_ON_HIGH_EXPLOSION_DAMAGE
0x71B0892EC081D60A
0x38CC692B
// SetVehicleExplodesOnHighExplosionDamage
void SET_VEHICLE_EXPLODES_ON_HIGH_EXPLOSION_DAMAGE(Vehicle vehicle, BOOL toggle);
Sets a vehicle to be strongly resistant to explosions. p0 is the vehicle; set p1 to false to toggle the effect on/off. 

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

SET_VEHICLE_OUT_OF_CONTROL
0xF19D095E42D430CC
0x3764D734
// SetVehicleOutOfControl
void SET_VEHICLE_OUT_OF_CONTROL(Vehicle vehicle, BOOL killDriver, BOOL explodeOnImpact);
Tested on the player's current vehicle. Unless you kill the driver, the vehicle doesn't loose control, however, if enabled, explodeOnImpact is still active. The moment you crash, boom. 

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

EXPLODE_PROJECTILES
0xFC4BD125DE7611E4
0x35A0B955
// ExplodeProjectiles
void EXPLODE_PROJECTILES(Ped ped, Hash weaponHash, BOOL p2);
WEAPON::EXPLODE_PROJECTILES(PLAYER::PLAYER_PED_ID(), func_221(0x00000003), 0x00000001); 

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

REMOVE_ALL_PROJECTILES_OF_TYPE
0xFC52E0F37E446528
0xA5F89919
// RemoveAllProjectilesOfType
void REMOVE_ALL_PROJECTILES_OF_TYPE(Hash weaponHash, BOOL explode);
If explode true, then removal is done through exploding the projectile. Basically the same as EXPLODE_PROJECTILES but without defining the owner ped.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------


