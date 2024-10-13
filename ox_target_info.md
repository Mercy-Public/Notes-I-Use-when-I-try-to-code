TargetOptions
All target actions are formated as an array containing objects with the following properties.

TargetOption
label: string
name?: string
An identifier used when removing an option.
icon?: string
Name of a Font Awesome icon.
iconColor?: string
distance?: number
The max distance to display the option.
bones?: string or string[]
A bone name or array of bone names (see GetEntityBoneIndexByName).
offset?: vector3
Offset the targetable area of an entity, relative to the model dimensions.
offsetAbsolute?: vector3
Offset the targetable area of an entity, relative to the entity's world coords.
offsetSize?: number
The radius of the targetable area for an entity offset.
groups?: string or string[] or table<string, number>
A group, array of groups, or pairs of groups-grades required to show the option.
Groups are framework dependent, and may refer to jobs, gangs, etc.
items?: string or string[] or table<string, number>
An item, array of items, or pairs of items-count required to show the option.
Items are framework dependent.
anyItem?: boolean
Only require a single item from the items table to exist.
canInteract?: function(entity, distance, coords, name, bone)
Options will always display if this is undefined.
menuName?: string
The option is only displayed when a menu has been set with openMenu.
openMenu?: string
Sets the current menu name, displaying only options for the menuName.
onSelect?: function(data)
export?: string
event?: string
serverEvent?: string
command?: string
Option Effects
When selecting an option it will trigger a single action, in order of priority:

onSelect function
export
event
server event
command

Client
All exports with the options argument expect a table with the targeting properties here.

For some examples you can refer to defaults.lua or debug.lua.

disableTargeting
Toggle the availability of the targeting menu.

exports.ox_target:disableTargeting(state)
state: boolean
Setting state to true will turn off the targeting eye if it is active and prevent it from reopening until state is set to false again.
addGlobalOption
Creates new targetable options which are displayed at all times.

exports.ox_target:addGlobalOption(options)
options: TargetOptions
removeGlobalOption
Removes all options from the global options list with the option names.

exports.ox_target:removeGlobalOption(optionNames)
optionNames: string or string[]
addGlobalObject
Creates new targetable options for all Object entity types.

exports.ox_target:addGlobalObject(options)
options: TargetOptions
removeGlobalObject
Removes all options from the global Object list with the option names.

exports.ox_target:removeGlobalObject(optionNames)
optionNames: string or string[]
addGlobalPed
Creates new targetable options for all Ped entity types (excluding players).

exports.ox_target:addGlobalPed(options)
options: TargetOptions
removeGlobalPed
Removes all options from the global Ped list with the option names.

exports.ox_target:removeGlobalPed(optionNames)
optionNames: string or string[]
addGlobalPlayer
Creates new targetable options for all Player entities.

exports.ox_target:addGlobalPlayer(options)
options: TargetOptions
removeGlobalPlayer
Removes all options from the global Player list with the option names.

exports.ox_target:removeGlobalPlayer(optionNames)
optionNames: string or string[]
addGlobalVehicle
Creates new targetable options for all Vehicle entity types.

exports.ox_target:addGlobalVehicle(options)
options: TargetOptions
removeGlobalVehicle
Removes all options from the global Vehicle list with the option names.

exports.ox_target:removeGlobalVehicle(optionNames)
optionNames: string or string[]
addModel
Creates new targetable options for a specific model or list of models.

exports.ox_target:addModel(models, options)
models: number or string or Array<number | string>
options: TargetOptions
removeModel
Removes all options from the models list with the option names.

exports.ox_target:removeModel(models, optionNames)
models: number or string or Array<number | string>
optionNames: string or string[]
addEntity
Creates new targetable options for a specific network id or list of network ids (see NetworkGetNetworkIdFromEntity).

exports.ox_target:addEntity(netIds, options)
netIds: number or number[]
options: TargetOptions
removeEntity
Removes all options from the networked entities list with the option names.

exports.ox_target:removeEntity(netIds, optionNames)
netIds: number or number[]
optionNames: string or string[]
addLocalEntity
Creates new targetable options for a specific entity handle or list of entity handles.

exports.ox_target:addLocalEntity(entities, options)
entities: number or number[]
options: TargetOptions
removeLocalEntity
Removes all options from the entities list with the option names.

exports.ox_target:removeLocalEntity(entities, optionNames)
entities: number or number[]
optionNames: string or string[]
addSphereZone
Creates a new targetable sphere zone.

exports.ox_target:addSphereZone(parameters)
parameters: table
coords: vector
radius?: number
debug?: boolean
drawSprite?: boolean
options: TargetOptions
Return:

id: number
addBoxZone
Creates a new targetable box zone.

exports.ox_target:addBoxZone(parameters)
parameters: table
coords: vector
size?: vector3
rotation?: number
debug?: boolean
drawSprite?: boolean
options: TargetOptions
Return:

id: number
addPolyZone
Creates a new targetable poly zone.

exports.ox_target:addPolyZone(parameters)
parameters: table
points: vector3[]
All z values must match
thickness?: number
debug?: boolean
drawSprite?: boolean
options: TargetOptions
Return:

id: number
removeZone
Removes a targetable zone with the given id (returned by addBoxZone/addSphereZone).

exports.ox_target:removeZone(id)
id: number or string
The number id that is returned by addSphereZone, addBoxZone, or addPolyZone
OR
The string name that can be specified by the user