Client
Mostly follows the format used by ESX and QBCore, with extra data such as damaged/missing props.
https://github.com/overextended/ox_lib/blob/master/resource/vehicleProperties/client.lua#L3

lib.getVehicleProperties
lib.getVehicleProperties(vehicle)
vehicle: number
vehicle handle of the vehicle to get the properties for
lib.getVehicleProperties(GetVehiclePedIsUsing(PlayerPedId()))
lib.setVehicleProperties
Sets properties on a vehicle (i.e. mods, plate text, etc.) and returns true if the client owns the entity.

lib.setVehicleProperties(vehicle, props)
vehicle: entity
props: table (object)
RegisterNetEvent('ox_lib:setVehicleProperties', function(netid, data)
    lib.setVehicleProperties(NetToVeh(netid), data)
end)
Returns:

isEntityOwner: boolean
Recommended Usage
The server should tell the owner of the entity to set properties, using the following trigger.

TriggerClientEvent('ox_lib:setVehicleProperties', entityOwner, vehNetId, data)
Vehicle Properties
model?: number
plate?: string
plateIndex?: number
bodyHealth?: number
engineHealth?: number
tankHealth?: number
fuelLevel?: number
oilLevel?: number
dirtLevel?: number
color1?: number or number[]
color2?: number or number[]
pearlescentColor?: number
interiorColor?: number
dashboardColor?: number
wheelColor?: number
wheelWidth?: number
wheelSize?: number
wheels?: number
windowTint?: number
xenonColor?: number
neonEnabled?: boolean[]
neonColor?: number or number[]
extras?: table<number | string, 0 | 1>
tyreSmokeColor?: number or number[]
modSpoilers?: number
modFrontBumper?: number
modRearBumper?: number
modSideSkirt?: number
modExhaust?: number
modFrame?: number
modGrille?: number
modHood?: number
modFender?: number
modRightFender?: number
modRoof?: number
modEngine?: number
modBrakes?: number
modTransmission?: number
modHorns?: number
modSuspension?: number
modArmor?: number
modNitrous?: number
modTurbo?: number
modSubwoofer?: boolean
modSmokeEnabled?: boolean
modHydraulics?: boolean
modXenon?: boolean
modFrontWheels?: number
modBackWheels?: number
modCustomTiresF?: boolean
modCustomTiresR?: boolean
modPlateHolder?: number
modVanityPlate?: number
modTrimA?: number
modOrnaments?: number
modDashboard?: number
modDial?: number
modDoorSpeaker?: number
modSeats?: number
modSteeringWheel?: number
modShifterLeavers?: number
modAPlate?: number
modSpeakers?: number
modTrunk?: number
modHydrolic?: number
modEngineBlock?: number
modAirFilter?: number
modStruts?: number
modArchCover?: number
modAerials?: number
modTrimB?: number
modTank?: number
modWindows?: number
modDoorR?: number
modLivery?: number
modRoofLivery?: number
modLightbar?: number
windows?: number[]
doors?: number[]
tyres?: table<number | string, 1 | 2>
bulletProofTyres?: boolean
