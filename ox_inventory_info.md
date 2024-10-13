Config
Resource configuration is handled using convars.

### Shared
 
# Activate specific event handlers and functions (supported: ox, esx, qbx, nd)
setr inventory:framework "esx"
 
# Number of slots for player inventories
setr inventory:slots 50
 
# Maximum carry capacity for players, in grams (frameworks may override this)
setr inventory:weight 30000
 
# Integrated support for qtarget/ox_target stashes, shops, etc
# Note: qtarget is deprecated, a future update may drop support (ox_target only, or gated features)
setr inventory:target false
 
# Jobs with access to police armoury, evidence lockers, etc
setr inventory:police ["police", "sheriff"]
 
### Client
 
# The URL to load item images from
setr inventory:imagepath "nui://ox_inventory/web/images"
 
# Weapons will reload after reaching 0 ammo
setr inventory:autoreload false
 
# Blur the screen while accessing the inventory
setr inventory:screenblur true
 
# Default hotkeys to access primary and secondary inventories, and hotbar
setr inventory:keys ["F2", "K", "TAB"]
 
# Enable control action when inventory is open
setr inventory:enablekeys [249]
 
# Weapons must be aimed before shooting
setr inventory:aimedfiring false
 
# Show a list of all nearby players when giving items
setr inventory:giveplayerlist false
 
# Toggle weapon draw/holster animations
setr inventory:weaponanims true
 
# Toggle item notifications (add/remove)
setr inventory:itemnotify true
 
# Toggle weapon item notifications (equip/holster)
setr inventory:weaponnotify true
 
# Disable drop markers and spawn a prop instead
setr inventory:dropprops true
 
# Set the default model used for drop props
setr inventory:dropmodel "prop_med_bag_01b"
 
# Disarm the player if an unexpected weapon is in use (i.e. did not use the weapon item)
setr inventory:weaponmismatch true
 
# Ignore weapon mismatch checks for the given weapon type (e.g. ['WEAPON_SHOVEL', 'WEAPON_HANDCUFFS'])
setr inventory:ignoreweapons []
 
# Suppress weapon and ammo pickups
setr inventory:suppresspickups 1
 
### Server
 
# Compare current version to latest release on GitHub
set inventory:versioncheck true
 
# Stashes will be wiped after remaining unchanged for the given time
set inventory:clearstashes "6 MONTH"
 
# Discord webhook url, used for imageurl metadata content moderation (image embeds)
set inventory:webhook ""
 
# Logging via ox_lib (0: Disable, 1: Standard, 2: Include AddItem/RemoveItem, and all shop purchases)
set inventory:loglevel 1
 
# Item prices fluctuate in shops
set inventory:randomprices true
 
# Loot will randomly generate inside unowned vehicles and dumpsters
set inventory:randomloot true
 
# Minimum job grade to remove items from evidence lockers
set inventory:evidencegrade 2
 
# Trim whitespace from vehicle plates when checking owned vehicles
setr inventory:trimplate true
 
# Set the contents of randomly generated inventories
# [item name, minimum, maximum, loot chance]
set inventory:vehicleloot [
    ["cola", 1, 1],
    ["water", 1, 1],
    ["garbage", 1, 2, 50],
    ["panties", 1, 1, 5],
    ["money", 1, 50],
    ["money", 200, 400, 5],
    ["bandage", 1, 1]
]
 
set inventory:dumpsterloot [
    ["mustard", 1, 1],
    ["garbage", 1, 3],
    ["money", 1, 10],
    ["burger", 1, 1]
]
 
# Set items to sync with framework accounts
set inventory:accounts ["money"]
Framework incompatibilities
Any frameworks with their own built-in inventory, item, or weapon systems are expected to have compatibility issues.
Money as an item may conflict with banking/account systems.
You can sync these values with server.syncInventory.
Refer to issue #1297 for known compatibility issues.

Using an unsupported framework
If your framework does not have official support you'll have to implement it yourself.
If you're replacing an existing/built-in inventory system this may be complicated, but is a fairly simple task otherwise.

This setup is highly opinionated and rigid, so it's up to your own ability as a developer to make it work.

Setup a bridge submodule
You'll want to set the target framework first - this could be the name, an acronym, or just "custom".

setr inventory:framework "custom"
Copy the ox directory from the bridge directory and give it the name you used above.

The bare minimum functions and event handlers are added here, but you'll need to change them to match your framework; we can't provide any help here. You can refer to the other framework bridges if you need inspiration.

Setup database references
Take a look at the mysql module. You'll need to reference your player/vehicle tables and id columns.

elseif shared.framework == 'custom' then
    playerTable = 'characters' -- table storing player / character data
    playerColumn = 'charid'    -- primary key for identifying the character (i.e. identifier, citizenid, id)
    vehicleTable = 'vehicles'  -- table storing owned vehicle data
    vehicleColumn = 'id'       -- primary key for identifying the vehicle (i.e. plate, vin, id)
end

Common Issues
UI has not been built
Because the UI for inventory is written in React it can't run natively under FiveM so it must first be bundled into html/css/js.

We provide an easy way for you to do this by downloading a pre-bundled release, which you can get from here.
Make sure you download the ox_inventory.zip file as that one contains the bundled files and others are raw source code.

If in case you wanted to edit the inventory UI you would have to build these files yourself.
To do so please read our Installation guide.

No such export * in resource ox_inventory
There are several likely causes for this "issue".

An error occurred while starting ox_inventory or one of its dependencies (e.g. ox_lib).
The resource trying to use the export (e.g. esx_addoninventory) is being started before ox_inventory.
You're literally trying to call an export that does not exist, which is a you issue.
Stashes / trunks are not saved at server restart
Stopping a server or "restarting" it does not trigger any events or allow for saving.

Inventories are saved at a 5 minute interval.
txAdmin scheduled restarts and shutdowns will trigger a save.
The saveinv command can be used manually or triggered in the console.
All inventories are saved when the number of online players hits 0.

client events

Client
This is not a comprehensive list of events and is missing events intended for internal use only.

Event Triggers
These events are safe to trigger and handle in other scripts.

ox_inventory:disarm
Can be triggered to force the player to disarm.

TriggerClientEvent('ox_inventory:disarm', playerId, noAnim)
playerId: number
noAnim: boolean
If true, disarm animation will be skipped
Event Handlers
These events should not be triggered by any other scripts.

ox_inventory:updateInventory
Triggered after inventory slots have been updated, included on load.
Changes is a table containing all updated slot data indexed by slotId. Empty slots are false.

AddEventHandler('ox_inventory:updateInventory', function(changes) end)
changes: table<number, table | false>
ox_inventory:currentWeapon
Triggered when a weapon is equipped or its metadata is altered.

AddEventHandler('ox_inventory:currentWeapon', function(weapon) end)
weapon?: table
ox_inventory:itemCount
Triggered when the amount of an item in the player's inventory is changed.
Note: Not available for ESX, use esx:addInventoryItem or esx:removeInventoryItem.

AddEventHandler('ox_inventory:itemCount', function(itemName, totalCount) end)
itemName: string
totalCount: number
ox_inventory:updateWeaponComponent
AddEventHandler('ox_inventory:updateWeaponComponent', function(action, componentHash, componentItem) end)
action: 'added' | 'removed'
componentHash: number
componentItem: string
ox_inventory:usedItem
AddEventHandler('ox_inventory:usedItem', function(name, slotId, metadata) end)
name: string
slotId: number
metadata?: table

server Events


Server
This is not a comprehensive list of events and is missing events intended for internal use only.

Handlers
These events should not be triggered by any other scripts.

ox_inventory:openedInventory
Triggered after an inventory is opened by a player.

AddEventHandler('ox_inventory:openedInventory', function(playerId, inventoryId) end)
playerId: number
inventoryId: string
ox_inventory:closedInventory
Triggered after an inventory is closed by a player.

AddEventHandler('ox_inventory:closedInventory', function(playerId, inventoryId) end)
ox_inventory:usedItem
AddEventHandler('ox_inventory:usedItem', function(playerId, name, slotId, metadata) end)
playerId: number
name: string
slotId: number
metadata?: table


functions client

Client
openInventory
Opens an inventory using the passed data.

exports.ox_inventory:openInventory(invType, data)
invType: string
'player'
'shop'
'stash'
'crafting'
'container'
'drop'
'glovebox'
'trunk'
'dumpster'
data: number or string or table

Examples
Open the target player's inventory.

exports.ox_inventory:openInventory('player', 3)
openNearbyInventory
If possible opens the nearby player's inventory.

The player trying to open the inventory must be able to open their own and if the player does not have a police job, the target player must be fatally injured or playing one of the death anims.

exports.ox_inventory:openNearbyInventory()
closeInventory
Closes the player's inventory.

exports.ox_inventory:closeInventory()
Items
Returns a table of all registered items. The format is as defined in data/items.lua.

Optionally takes the name of an item, returning only data for that item (getting all data is not recommended).

exports.ox_inventory:Items(itemName)
itemName?: string
The following snippet can be used in crafting resources such as okokCrafting or core_crafting, rather than retrieving information from the server.

local itemNames = {}
 
for item, data in pairs(exports.ox_inventory:Items()) do
    itemNames[item] = data.label
end
useItem
Uses the passed item, then triggers the callback function.
Should be calling during item callbacks to utilise the builtin methods (server checks, progress bar, etc.).

exports.ox_inventory:useItem(data, cb)
data: table
cb?: function
exports('bandage', function(data, slot)
    local playerPed = PlayerPedId()
    local maxHealth = GetEntityMaxHealth(playerPed)
    local health = GetEntityHealth(playerPed)
 
    -- Does the ped need to heal?
    if health < maxHealth then
        -- Use the bandage
        exports.ox_inventory:useItem(data, function(data)
            -- The item has been used, so trigger the effects
            if data then
                SetEntityHealth(playerPed, math.min(maxHealth, math.floor(health + maxHealth / 16)))
                lib.notify({description = 'You feel better already'})
            end
        end)
    else
        -- Don't use the item
        lib.notify({type = 'error', description = 'You don\'t need a bandage right now'})
    end
end)
useSlot
Uses the item in the given inventory slot.

exports.ox_inventory:useSlot(slot)
slot: number
setStashTarget
Forces the secondary-inventory key to open the passed inventory. Can be useful to enable inventory access while standing inside a marker.

exports.ox_inventory:setStashTarget(id, owner)
id: string or number
Stash id.
owner?: string or number

Example
exports.ox_inventory:setStashTarget('motel5', 'bobsmith')
getCurrentWeapon
Get data for the currently equipped weapon.

exports.ox_inventory:getCurrentWeapon()
You can also listen for changes to the current weapon using an event handler.

AddEventHandler('ox_inventory:currentWeapon', function(currentWeapon)
	CurrentWeapon = currentWeapon
end)
currentWeapon?: table
ammo?: string Name of the item used as ammo.
hash: number
label: string
melee: boolean
metadata: table
ammo?: number Amount of ammo loaded into the weapon.
components?: table Array of component item names, used to apply weapon components.
durability?: number
registered?: string Name of the player that bought the weapon at a shop.
serial?: string
name: string Name of the item.
slot: number
weight: number
displayMetadata
Sets a metadata property to display in the tooltip.

exports.ox_inventory:displayMetadata(metadata, value)
metadata: string or table<string, string> or { [string], [string] }
If metadata is a string then it's the metadata property you want to display, value is not optional then.
Can be a table of key-value pairs, key being the metadata property and value being the label for that property.
Can be an array of string arrays, i.e. { {'key', 'label' }, {'key2', 'label2' } to set the display order.
value?: string
Label for the string metadata property to be displayed.

Example
exports.ox_inventory:displayMetadata('mustard', 'Mustard')
exports.ox_inventory:displayMetadata({
    mustard = 'Mustard',
    ketchup = 'Ketchup'
})
giveItemToTarget
Gives an item from the player's inventory to another player.

exports.ox_inventory:giveItemToTarget(serverId, slotId, count)
serverId: number
The serverId of the target player.
slotId: number
The slotId of the item to give.
count?: number
The amount of the item to give, with nil, 0 or a value above the slot count giving the entire stack away.
weaponWheel
Enables the weapon wheel, but disables the use of inventory weapons.

Mostly used for weaponised vehicles, though could be called for "minigames"

local exports.ox_inventory:weaponWheel(state)
state: boolean
Search
Searches the inventory for an item, or list of items, with the result varying based on the first argument.

exports.ox_inventory:Search(search, item, metadata)
search: 'slots' or 'count'
'slots' returns a table of slots where the item was found at.
'count' returns the count of the specified item in player's inventory. If searching for multiple items returns key-value pairs of itemName = count.
item: table or string
Can be a single item name or array of item names.
metadata?: table or string
If metadata is provided as a string it will search the item's metadata.type property.
Count
local count = exports.ox_inventory:Search('count', 'water')
print('You have '..count.. ' water')
Slots
local water = exports.ox_inventory:Search('slots', 'water')
local count = 0
 
for _, v in pairs(water) do
    print(v.slot..' contains '..v.count..' water '..json.encode(v.metadata))
    count = count + v.count
end
 
print('You have '..count..' water')
GetItemCount
Get the total item count for all items in the player's inventory with the given name and metadata.

exports.ox_inventory:GetItemCount(itemName, metadata, strict)
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

count: number
GetPlayerItems
Get all items in the player's inventory.

exports.ox_inventory:GetPlayerItems()
Return:

items: table
GetPlayerWeight
Get the total weight of all items in the player's inventory.

exports.ox_inventory:GetPlayerWeight()
Return:

totalWeight: number
GetPlayerMaxWeight
Get the maximum carry weight of the player's inventory.

exports.ox_inventory:GetPlayerMaxWeight()
Return:

maxWeight: number
GetSlotIdWithItem
Get a slot id in the player's inventory matching the given name and metadata.

exports.ox_inventory:GetSlotIdWithItem(itemName, metadata, strict)
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotId: number?
GetSlotsIdWithItem
Get all slot ids in the player's inventory matching the given name and metadata.

exports.ox_inventory:GetSlotIdsWithItem(itemName, metadata, strict)
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotIds: number[]?
GetSlotWithItem
Get data for a slot in the player's inventory matching the given name and metadata.

exports.ox_inventory:GetSlotWithItem(itemName, metadata, strict)
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotData: table?
GetSlotsWithItem
Get data all slots in the player's inventory matching the given name and metadata.

exports.ox_inventory:GetSlotsWithItem(itemName, metadata, strict)
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotsData: table[]?
Statebags
invBusy
Returns whether the player's inventory is currently running an action (i.e. using an item).
Can be set to true to disable opening the inventory.

invBusy: boolean
local invBusy = LocalPlayer.state.invBusy
 
if invBusy then
    -- Do stuff when busy
else
    -- Do stuff when not busy
end
Disable opening inventory
LocalPlayer.state.invBusy = true
invHotkeys
Allows you to enable/disable a player's access to inventory hotkeys.

invHotkeys: boolean
LocalPlayer.state.invHotkeys = false
invOpen
Returns whether the player's inventory is currently open or not.

invOpen: boolean
local invOpen = LocalPlayer.state.invOpen
 
if invOpen then
    -- Do stuff when open
else
    -- Do stuff when closed
end
canUseWeapons
Allows you to enable/disable the use of weapons for a player.

LocalPlayer.state.canUseWeapons = false


functions server

Server
setPlayerInventory
Creates and sets the player's inventory.

exports.ox_inventory:setPlayerInventory(player, data)
player: table
source: number
identifier: string
name: string
groups?: table
sex?: string
dateofbirth?: string
data?: table
If not provided will load player's inventory data from the db.
forceOpenInventory
Opens an inventory using the passed data. Forces a player to open an inventory, without usual security checks (groups, coords).

exports.ox_inventory:forceOpenInventory(playerId, invType, data)
playerId: number
invType: string
'player'
'stash'
'container'
'drop'
'glovebox'
'trunk'
'dumpster'
data: number or string or table
Open the target player's inventory.

exports.ox_inventory:forceOpenInventory(1, 'player', 3)
Admin command to open a player's inventory.

RegisterCommand('openplayerinv', function(source, args)
    exports.ox_inventory:forceOpenInventory(source, 'player', tonumber(args[1]))
end, true)
UpdateVehicle
Update the internal reference to vehicle stashes, without triggering a save or updating the database.

exports.ox_inventory:UpdateVehicle(oldPlate, newPlate)
oldPlate: string
newPlate: string
Items
Returns a table of all registered items. The format is as defined in data/items.lua.

Optionally takes the name of an item, returning only data for that item (getting all data is not recommended).

exports.ox_inventory:Items(itemName)
itemName?: string
The following snippet can be used in crafting resources such as okokCrafting or core_crafting, rather than querying the database.

local itemNames
 
ESX.RegisterServerCallback('crafting:itemNames', function(source, cb)
    if not itemNames then
        itemNames = {}
        for item, data in pairs(exports.ox_inventory:Items()) do
            itemNames[item] = data.label
        end
    end
    cb(itemNames)
end)
AddItem
Adds an item into the specified inventory.

Should be used alongside CanCarryItem otherwise, the maximum weight may be exceeded.

exports.ox_inventory:AddItem(inv, item, count, metadata, slot, cb)
inv: table or string or number
The inventory's unique id, or a table with the id and owner.
playerId: 1
inventoryId: gloveVGH283
{ id = 'personallocker', owner = 'license:xxxxxx'}
item: string
The name of the item to add to the target.
count: number
The number of items to add.
metadata?: table or string
A table of unique data to attach to the item object. A string will create a table with the "type" field.
slot?: number
A specific slot to add the item to. If the slot is invalid, the first available slot will be used instead.
cb?: function(success: boolean, response?: string)
If used for glovebox, trunk or stash you must first check the inventory is loaded with GetInventory

Returns success, response if cb is undefined, otherwise they are used in the callback only.

Possible value of the "response" argument, on failure:

"invalid_item": the item doesn't exist
"invalid_inventory": the inventory doesn't exist
"inventory_full": no free slots

Example
local success, response = exports.ox_inventory:AddItem('gloveVGH283', 'bread', 4)
 
if not success then
    -- if no slots are available, the value will be "inventory_full"
    return print(response)
end
 
print(json.encode(response, {indent=true}))
--[[
    {
        "metadata": [],
        "label": "Bread",
        "slot": 1,
        "stack": true,
        "close": true,
        "name": "bread",
        "count": 1,
        "weight": 150
    }
]]
RemoveItem
Removes the specified item from the specified inventory.

exports.ox_inventory:RemoveItem(inv, item, count, metadata, slot, ignoreTotal)
inv: table or string or number
The inventory's unique id, or a table with the id and owner.
playerId: 1
inventoryId: gloveVGH283
{ id = 'personallocker', owner = 'license:xxxxxx'}
item: string
The name of the item to remove from the target.
count: number
The number of items to remove.
metadata?: table or string
Only remove items with matching metadata properties.
slot?: number
A specific slot to remove the item from. If the slot is invalid, the first available slot will be used instead.
ignoreTotal?: boolean
Removes as many items as possible up to count.
Returns success: boolean, response: string?.

Possible values of "response" on failure:

"invalid_item": the item doesn't exist
"invalid_inventory": the inventory doesn't exist
"not_enough_items": inventory did not contain enough of the given item

Example
-- Removes 2 water from the glovebox for the given plate.
local success = exports.ox_inventory:RemoveItem('gloveVGH283', 'water', 2)
GetItem
Returns generic item data from the specified inventory, with the total count.

exports.ox_inventory:GetItem(inv, item, metadata, returnsCount)
inv: table or string or number
item: table or string
Can be items array.
metadata?: any
Only returns the count of items that strictly match the given metadata.
returnsCount?: boolean
If returnsCount is set to true, the returned value will be the count based on how many times the item was found. Otherwise returns the data related to the item and its total count found in the inventory.


Example
local item = ox_inventory:GetItem(source, 'water', nil, false)
 
print(json.encode(item, {indent=true}))
--[[
    {
        "consume": 1,
        "count": 15,
        "stack": true,
        "name": "water",
        "weight": 500,
        "label": "Water",
        "close": true
    }
]]
ConvertItems
Takes traditional item data and updates it to support ox_inventory.

exports.ox_inventory:ConvertItems(playerId, items)
playerId: number
items: table

Data Conversion Example
Old: [{"cola":1, "bread":3}]
New: [{"slot":1,"name":"cola","count":1},
{"slot":2,"name":"bread","count":3}]
CanCarryItem
Returns true or false depending if the inventory can carry the specified item.

The function checks for inventory weight and available slots.

exports.ox_inventory:CanCarryItem(inv, item, count, metadata)
inv: table or string or number
item table or string
Can be array of items.
count: number
metadata?: table or string
If metadata is passed as string then metadata.type will be checked.

Example
-- Checks if the player calling the event can carry 3 water items
if exports.ox_inventory:CanCarryItem(source, 'water', 3) then
    -- Do stuff if can carry
else
    -- Do stuff if can't carry
end
CanCarryAmount
Returns the amount a player can hold based on available weight.

exports.ox_inventory:CanCarryAmount(inv, item)
inv: table or string or number
item: table or string
Can be array to check multiple items.

Example
-- Checks how much you can carry
amountToAdd = exports.ox_inventory:CanCarryAmount(inv, 'stone')
-- Adds the amount
exports.ox_inventory:AddItem(inv, 'stone', amountToAdd)
CanCarryWeight
Returns if inventory can carry specified weight and free inventory weight.

exports.ox_inventory:CanCarryWeight(inv, weight)
inv: table or string or number
weight: number

Example
-- Checks if player can carry 1000 grams.
local fillAmount = 1000
local canCarryWeight, freeWeight = ox_inventory:CanCarryWeight(playerId, fillAmount)
 
if freeWeight == 0 then
  -- Player can't carry weight.
  return
elseif not canCarryWeight then
  -- Modify fillAmount, because inventory can't carry specified weight
  fillAmount = freeWeight
end
 
-- Do something
SetMaxWeight
Sets the maximum weight available for an inventory.

exports.ox_inventory:SetMaxWeight(inv, maxWeight)
inv: table or string or number
maxWeight: number

Example
local ox_inventory = exports.ox_inventory
 
-- Set the max weight for player 1's inventory to 20kg.
ox_inventory:SetMaxWeight(1, 20000)
CanSwapItem
Returns true if the item swap is possible based on inventory weight.

exports.ox_inventory:CanSwapItem(inv, firstItem, firstItemCount, testItem, testItemCount)
inv: table or string or number
firstItem: string
firstItemCount: number
testItem: string
testItemCount: number
GetItemCount
Get the total item count for all items in an inventory with the given name and metadata.

exports.ox_inventory:GetItemCount(inv, itemName, metadata, strict)
inv: table or string or number
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

itemCount: number
GetItemSlots
Returns the number of slots the specified item is in, the item's total count and the remaining empty slots.

exports.ox_inventory:GetItemSlots(inv, item, metadata)
inv: table or string or number
item: table or string
metadata?: table
GetSlot
Returns the specified slot data as a table.

 
exports.ox_inventory:GetSlot(inv, slot)
inv: table or string or number
slot: number

Example
local slot = exports.ox_inventory:GetSlot(source, 1)
 
print(json.encode(slot, {indent=true}))
--[[
    {
        "weight": 2000,
        "name": "water",
        "metadata": [],
        "slot": 1,
        "label": "Water",
        "close": true,
        "stack": true,
        "count: 4
    }
]]
GetSlotForItem
Get the slot id of an existing item matching the given data, or an empty slot.

exports.ox_inventory:GetSlotForItem(inv, itemName, metadata)
inv: table or string or number
itemName: string
metadata: table?
Return:

slotId: number?
GetSlotIdWithItem
Get a slot id in an inventory matching the given item name and metadata.

exports.ox_inventory:GetSlotIdWithItem(inv, itemName, metadata, strict)
inv: table or string or number
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotId: number?
GetSlotIdsWithItem
Get all slot ids in an inventory matching the given name and metadata.

exports.ox_inventory:GetSlotIdsWithItem(inv, itemName, metadata, strict)
inv: table or string or number
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotIds: number[]?
GetSlotWithItem
Get data for a slot in an inventory matching the given name and metadata.

exports.ox_inventory:GetSlotWithItem(inv, itemName, metadata, strict)
inv: table or string or number
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotData: table?
GetSlotsWithItem
Get data all slots in an inventory matching the given name and metadata.

exports.ox_inventory:GetSlotsWithItem(inv, itemName, metadata, strict)
inv: table or string or number
itemName: string
metadata?: table
strict?: boolean
Strictly match metadata properties, otherwise use partial matching.
Return:

slotsData: table[]?
GetEmptySlot
Get the first available empty slot in an inventory.

exports.ox_inventory:GetEmptySlot(inv)
inv: table or string or number
Return:

slotId: number?
GetContainerFromSlot
Returns the inventory associated with the container linked in the slot of the given inventory.

exports.ox_inventory:GetContainerFromSlot(inv, slotId)
inv: table or string or number
slotId: number
Return:

containerData: table?
SetSlotCount
Sets the number of slots available for an inventory.

exports.ox_inventory:SetSlotCount(inv, slots)
inv: table or string or number
slots: number

Example
local ox_inventory = exports.ox_inventory
 
-- Set the slot count for player 1's inventory to 10.
ox_inventory:SetSlotCount(1, 10)
GetInventory
Returns the inventory associated with the ID (and owner if defined). Otherwise returns null.

exports.ox_inventory:GetInventory(inv, owner)
inv: number or table
owner?: string or boolean

Example
local inventory = exports.ox_inventory:GetInventory('example_stash', false)
print(json.encode(inventory, {indent = true}))
--[[
    {
        "id": "example_stash,
        "label": "Police Stash",
        "type": "stash,
        "slots": 50,
        "weight": 0,
        "maxWeight": 100000,
        "owner": false,
        ...
    }
]]
GetInventoryItems
Returns all slots with items in a inventory.

exports.ox_inventory:GetInventoryItems(inv, owner)
inv: number or table
owner?: string or boolean

Example
local playerItems = exports.ox_inventory:GetInventoryItems(source)
InspectInventory
Inspect the player their inventory. You will not be able to modify the inventory.

exports.ox_inventory:InspectInventory(target, source)
target: number
source: number
ConfiscateInventory
Clears a player's inventory and saves it to a stash.

Use ReturnInventory to return the confiscated inventory back to the player.

exports.ox_inventory:ConfiscateInventory(source)
source: number
ReturnInventory
Returns the confiscated inventory back to the player.

Use it alongside ConfiscateInventory.

exports.ox_inventory:ReturnInventory(source)
source: number
ClearInventory
Clears the specified inventory. The keep argument is either a string or an array of strings containing the name(s) of the item(s) to keep in the inventory after clearing.

exports.ox_inventory:ClearInventory(inv, keep)
inv: table or string or number
keep?: string or string[]
Search
Searches an inventory for a specified item.

exports.ox_inventory:Search(inv, search, item, metadata)
inv: table or string or number
search: string
item: table or string
metadata?: table or string
search can be either 'slots' or 'count', where slots will return a table of data and count will return the found amount of the specified item.

RegisterStash
Creates a new custom stash.

exports.ox_inventory:RegisterStash(id, label, slots, maxWeight, owner, groups, coords)
id: string or number
Stash identifier when loading from the database.
label: string
Display name when inventory is open.
slots: number
maxWeight: number
owner: string or boolean or nil
string: Can only access the stash linked to the owner.
true: Each player has a unique stash but can request other player's stashes.
nil: Always shared.
groups: table
Table of player groups (jobs) able to access the stash.
Table of group names where the numeric value is the minimum grade required.
{['police'] = 0, ['ambulance'] = 2}
coords?: vector3 or vector3[]
This function needs to be triggered before a player can open the stash.


Example
For a use case example on this function check out the written Guide for it.

CreateTemporaryStash
Creates a temporary stash which will be removed after some time.

exports.ox_inventory:CreateTemporaryStash(properties)
properties: table
label: string
slots: number
maxWeight: number
owner?: string number or boolean
string: Can only access the stash linked to the owner.
true: Each player has a unique stash but can request other player's stashes.
The inventory is always shared if false or nil.
groups?: table<string, number>
Table of group names (e.g. jobs) where the numeric value is the minimum grade required.
{['police'] = 0, ['ambulance'] = 2}
coords?: vector3
Stash can only be accessed while nearby.
items?: { [number]: string, [number]: number, [number]?: table }[]
An array of tables, containing a sequence of itemName, count, metadata.
Return:

inventoryId: string

Example
local mystash = exports.ox_inventory:CreateTemporaryStash({
    label = 'mystash',
    slots = 5,
    maxWeight = 5000,
    items = {
        { 'WEAPON_MINISMG', 1 },
        { 'ammo-9', 69 },
        { 'water', 2, { label = 'Mineral water' } }
    }
})
 
TriggerClientEvent('ox_inventory:openInventory', 1, 'stash', mystash)
CustomDrop
Drops can be created from other resources, containing a variety of items and utilising a custom label (instead of 'Drop 32648').

exports.ox_inventory:CustomDrop(prefix, items, coords, slots, maxWeight, instance, model)
prefix: string
items: table
name: string
count: number
metadata?: table
coords: vector3
slots?: number
maxWeight?: number
instance?: string or number
model?: number
-- Create a generic drop with a marker
exports.ox_inventory:CustomDrop('Carcass', {
    {'meat', 5, { grade = 2, type = 'deer' }},
    {'hide', 5, { grade = 2, type = 'deer' }}
}, coords)
 
-- Create a drop with an entity
exports.ox_inventory:CustomDrop('SMG', {
    { 'WEAPON_MINISMG', 1 },
    { 'ammo-9', 69 },
}, GetEntityCoords(GetPlayerPed(1)), 5, 10000, nil, `w_sb_minismg`)
CreateDropFromPlayer
Creates a new drop with the contents of a player's inventory.

exports.ox_inventory:CreateDropFromPlayer(playerId)
playerId: number
Return:

dropId: string

Example
local dropId = exports.ox_inventory:CreateDropFromPlayer(1)
GetCurrentWeapon
Returns the player's currently equipped weapon as a table.

-- inv: string or number
exports.ox_inventory:GetCurrentWeapon(inv)
inv: table or string or number
SetDurability
Sets durability onto the specified slot.

Can be used for repairing weapons.

exports.ox_inventory:SetDurability(inv, slot, durability)
inv: table or string or number
slot: number
durability: number

Example
local ox_inventory = exports.ox_inventory
 
-- Set the durability of the item in slot 3 of source player's inventory to 100
ox_inventory:SetDurability(source, 3, 100)
 
-- Set the durability of the source player's current weapon to 100
local weapon = ox_inventory:GetCurrentWeapon(source)
 
if weapon then
    ox_inventory:SetDurability(source, weapon.slot, 100)
end
SetMetadata
Sets metadata on the specified slot.

ox_inventory:SetMetadata(inv, slot, metadata)
inv: table or string or number
slot: number
metadata: table

Example
local ox_inventory = exports.ox_inventory
 
local water = ox_inventory:Search(source, 1, 'water')
for k, v in pairs(water) do
    print('\n______________'..'\n- index '..k)
    print(v.name, 'slot: '..v.slot, 'metadata: '..json.encode(v.metadata))
    water = v
    break
end
 
water.metadata.type = 'clean'
ox_inventory:SetMetadata(source, water.slot, water.metadata)
print(('modified %sx water in slot %s with new metadata'):format(water.count, water.slot))



hooks

Hooks
Event hooks allow 3rd party resources to define new behaviour without modifying the inventory code directly.

registerHook
exports.ox_inventory:registerHook(eventName, function(payload) end, options)
eventName: string
payload: table
options?: table
print?: boolean
Print to the console when triggering the event.
itemFilter?: { [string]: true }
The event will only trigger for items defined as keys in a set.
inventoryFilter?: string[]
The event will only trigger for inventories that match one of the patterns in the array.
typeFilter?: { [string]: true }
The event will only trigger for inventories with one of the provided types (e.g. 'player', 'stash')
Return:

hookId: number
swapItems
Triggered when moving any item from one slot to another, or when "giving" an item.
By returning false, you can cancel the action and revert the inventory state.

Payload: table
source: number
action: 'move' or 'stack' or 'swap' or 'give'
fromInventory: table or string or number
toInventory: table or string or number
fromType: string
toType: string
fromSlot: table
toSlot?: table or number
count: number
Example

Blacklists "water" from being moved into or from gloveboxes and trunks.

local hookId = exports.ox_inventory:registerHook('swapItems', function(payload)
    print(json.encode(payload, { indent = true }))
    return false
end, {
    print = true,
    itemFilter = {
        water = true,
    },
    inventoryFilter = {
        '^glove[%w]+',
        '^trunk[%w]+',
    }
})
openInventory
Payload: table
source: number
inventoryId: number or string
inventoryType: string
Triggered when a player tries to open a secondary inventory.
By returning false, you can cancel the action and keep the player's inventory closed.

Example

Disables gloveboxes and trunks.

local hookId = exports.ox_inventory:registerHook('openInventory', function(payload)
    print(json.encode(payload, { indent = true }))
    return false
end, {
    print = true,
    inventoryFilter = {
        '^glove[%w]+',
        '^trunk[%w]+',
    }
})
createItem
Payload: table
inventoryId?: number or string
metadata: table
item: table
count: number
Triggered when an item is created, either by buying it, using AddItem, or when converting inventory data.
By returning a table you can modify or replace the metadata given to an item.

Example

Sets the label for "water" to "Mineral Water".

local hookId = exports.ox_inventory:registerHook('createItem', function(payload)
    print(json.encode(payload, { indent = true }))
    local metadata = payload.metadata
    metadata.label = 'Mineral Water'
    return metadata
end, {
    print = true,
    itemFilter = {
        water = true
    }
})
buyItem
Payload: table
source: number
shopType: string
shopId: number
toInventory: number
toSlot: number
itemName: string
metadata: table
count: number
price: number
totalPrice: number
currency?: string
Triggered when an item is about to be purchased and can return false to prevent the transaction.

Example

Prevents players from purchasing items at General stores.

local hookId = exports.ox_inventory:registerHook('buyItem', function(payload)
    print(json.encode(payload, { indent = true, sort_keys = true }))
    return false
end, {
    print = true,
    itemFilter = {
        water = true
	  },
})
 
craftItem
Payload: table
source: number
benchId: number
benchIndex: number
recipe: table
count: number
duration: number
ingredients: table<string, number>
name: string
slot: number
weight: number
toInventory: number
toSlot: number
Example

Prevent lockpicks from being crafted by players.

local hookId = exports.ox_inventory:registerHook('craftItem', function(payload)
    print(json.encode(payload, { indent = true, sort_keys = true }))
    return false
end, {
    print = true,
	itemFilter = {
		lockpick = true
	},
})
 
removeHooks
Removes a hook created by the invoking resource with the the specified id.
If no id is specified then all hooks registered by the resource are removed.

exports.ox_inventory:removeHooks(id)
id?: number


Crafting
Crafting locations, items and their ingredients are defined in data/crafting.lua.

Crafting definition
{
    items = {
        {
            name = 'lockpick',
            ingredients = {
            garbage = 3,
            WEAPON_HAMMER = 0.1
            },
            duration = 5000,
            count = 3,
            metadata = { durability = 20 }
        },
        {
            name = 'garbage',
            ingredients = {
            cola = 1
            },
            metadata = { description = 'An empty soda can.', weight = 20, image = 'trash_can' }
        },
    },
    points = {
        vec3(-1147.083008, -2002.662109, 13.180260),
        },
    zones = {
        {
            coords = vec3(-1146.2, -2002.05, 13.2),
            size = vec3(3.8, 1.05, 0.15),
            distance = 1.5,
            rotation = 315.0,
        },
    },
    blip = { id = 566, colour = 31, scale = 0.8 },
},
items: table
name: string
ingredients: table
Item ingredients can be seen in the item tooltip.
Key-value pairs of item name and consume count
key - Item name.
value - If 1 or above it's the consume count, if below 1 and above 0 it's the durability consume amount, if set to 0 then the item is required but not consumed.
duration: number
Crafting duration in milliseconds.
count: number or table (min, max)
Item amount received upon crafting.
If set it to table it requires two number first one is minimum number and second one is maximum, it will generate a random number between those two numbers to add the crafted item to player.
metadata: table
Metadata applied to the item being crafted.
points: vector3[]
Interaction locations that will open the crafting inventory.
groups: table
Key-value pairs of job name and minimum grade to access the crafting location.
{["police"] = 0, ["ambulance"] = 2}
zones: table
ox_lib targeting zones used for ox_target.
coords: vector3
size: vector3
distance: number
rotation: number
blip: table
id: number
Blip sprite number.
colour: number
scale: number

Creating Items
Defining item data
Before being able to see or use an item in game it must first be defined.

All of the items are defined in the /data/items.lua file with key, value pairs. Key is the name (not the label) of an item and the value is a table containing the options for the item.

Item options: table
label: string
weight?: number
stack?: boolean
If set to false will not allow the item to be stacked.
degrade?: number
Amount of time in minutes the item will degrade after.
decay?: boolean
If true the item will be deleted when durability reaches 0 (not instant for degraded items).
close?: boolean
If set to false does not close the inventory on item use.
description?: string
Item description that will be shown in the tooltip
consume?: number
Item count needed and removed use.
Default: 1
If set to a decimal will consume durability instead (0.2 = 20%).
allowArmed?: boolean
If set to true will allow use of item while armed with a weapon.
server?: table
export?: string
client?: table
export?: string
Export to be triggered after item use.
event?: string
Event to be triggered after item use.
status?: table
Adjust esx_status values after use.
anim?: table
Animation that will be played during the progress bar.
dict: string
clip: string
prop?: table
Attached prop that will be displayed during the progress bar.
model: string or hash
pos: table (x, y, z)
rot: table (x, y, z)
bone?: number
rotOrder?: number
disable?: table
Actions to be disabled during the progress bar.
move?: boolean
car?: boolean
combat?: boolean
mouse?: boolean
sprint?: boolean
usetime?: number
cancel?: boolean
If set to true the player canc cancel item use.
add?: function(total: number)
Function that triggers when receiving an item
Returns total item count as total
remove?: function(total: number)
Function that triggers when removing an item
Returns total item count as total
buttons?: table
label: string
action: function(slot: number)
Callback function when button is clicked in context menu, returns item slot.
Examples
['burger'] = {
    label = 'Burger',
    weight = 220,
    stack = true,
    close = true,
    client = {
        status = { hunger = 200000 },
        anim = { dict = 'mp_player_inteat@burger', clip = 'mp_player_int_eat_burger_fp' },
        prop = {
            model = 'prop_cs_burger_01',
            pos = { x = 0.02, y = 0.02, y = -0.02},
            rot = { x = 0.0, y = 0.0, y = 0.0}
        },
        usetime = 2500,
    }
}
Making the item usable
If you are using ESX, you can continue using ESX.RegisterUsableItem.
If you are using QBox, you can continue using exports.qbx_core:CreateUseableItem.
Using the built-in system is more secure and provides much more functionality.

Client callbacks
Item callbacks can be added by defining an export (recommended), or by adding it to items/client.lua.

When defining item data, adding client.export will trigger an event on item use. The correct formatting is export = resourceName.exportName.

exports('bandage', function(data, slot)
    local playerPed = PlayerPedId()
    local maxHealth = GetEntityMaxHealth(playerPed)
    local health = GetEntityHealth(playerPed)
 
    -- Does the ped need to heal? We can cancel the item from being used.
    if health < maxHealth then
        -- Triggers internal-code to correctly use items.
        -- This adds security, removes the item on use, adds progressbar support, and is necessary for server callbacks.
        exports.ox_inventory:useItem(data, function(data)
            -- The server has verified the item can be used.
            if data then
                SetEntityHealth(playerPed, math.min(maxHealth, math.floor(health + maxHealth / 16)))
                lib.notify({description = 'You feel better already'})
            end
        end)
    else
        -- Don't use the item
        lib.notify({type = 'error', description = 'You don\'t need a bandage right now'})
    end
end)
Server callbacks
A callback function can be defined on the server to handle several events (usingItem, usedItem, buyItem). This can either be an export (recommended), or added to the bottom of items/server.lua. When defining item data, adding server.export will trigger an event for the actions above. The correct formatting is export = resourceName.exportName.

exports('bandage', function(event, item, inventory, slot, data)
    -- Player is attempting to use the item.
    if event == 'usingItem' then
        local playerPed = GetPlayerPed(inventory.id)
        local maxHealth = GetEntityMaxHealth(playerPed)
        local health = GetEntityHealth(playerPed)
 
        -- Check if the player needs to be healed.
        if health >= maxHealth then
            TriggerClientEvent('ox_lib:notify', inventory.id, {type = 'error', description = 'You don\'t need a bandage right now'})
 
            -- Returning 'false' will prevent the item from being used
            return false
        end
 
        return
    end
 
    -- Player has finished using the item.
    if event == 'usedItem' then
        return TriggerClientEvent('ox_lib:notify', inventory.id, {description = 'You feel better already'})
    end
 
    -- Player is attempting to purchase the item.
    if event == 'buying' then
        return TriggerClientEvent('ox_lib:notify', inventory.id, {type = 'success', description = 'You bought a bandage'})
    end
end)
Creating container items
Like with other items the item must first be registered.

When registered you can define the item as a container in /modules/items/containers.lua The key for the container is the name you gave it when registering the item. You can also define the number of slots, the maximum weight, blacklist and whitelist items.

itemName:
slots: number
The number represents the amount of slots
maxWeight: number
The number represents the maximum weight within the container
blacklist:
Supports single and multiple items
{ 'testburger', 'testburger2' }
whitelist:
Supports single and multiple items
{ 'testburger', 'testburger2' }
Example
Register Example
['paperbag'] = {
    label = 'Paper Bag',
    weight = 1,
    stack = false,
    close = false,
    consume = 0
},
Properties Example
setContainerProperties('paperbag', {
	slots = 5,
	maxWeight = 1000,
	blacklist = { 'testburger' }
})



Creating Shops
Builtin shops are defined in data/shops.lua, and more can be added here to benefit from the built-in markers or zones support.

Shop definition
{
    General = {
        name = 'Shop',
        blip = {
          id = 59,
          colour = 69,
          scale = 0.8
        },
        inventory = {
            { name = 'burger', price = 10 },
            { name = 'water', price = 10 },
            { name = 'cola', price = 10 },
        },
        locations = {
            vec3(25.7, -1347.3, 29.49),
        },
        targets = {
            -- Shop using a BoxZone
            {
                loc = vec3(25.06, -1347.32, 29.5),
                length = 0.7,
                width = 0.5,
                heading = 0.0,
                minZ = 29.5,
                maxZ = 29.9,
                distance = 1.5
            },
            -- Shop using a ped
            {
                ped = `mp_m_shopkeep_01`,
                scenario = 'WORLD_HUMAN_AA_COFFEE',
                loc = vec3(24.407, -1347.283, 28.497),
                heading = 270.311,
            },
        }
    }
}
name: string
The label to display when the shop is open.
blip?: table
Creates a blip with the given settings. Leave it undefined for no blip to be created.
id: number
colour: number
scale: number
groups?: table
Key-value pairs of job name and minimum grade to access the shop.
{["police"] = 0, ["ambulance"] = 2}
inventory: table
name: string
price: number
currency?: string
Item to be used as currency.
count?: number
Amount of the item in the stock.
license?: string
License required to purchase the item.
metadata?: table
grade?: number | number[]
Minimal grade required to purchase the item.
locations?: vector3[]
An array of coordinates to create unique instances of the shop archetype at, using markers.
targets?: table[]
An array of target settings to create unique instances of the shop archetype at, using peds or BoxZones (PolyZone data structure).
model?: number[]
An array of models that can be targetted to open a shop. Used for vending machines.
Targets and model are only available when using a targeting resource like ox_target.

Register during runtime
Shops can be added using exports.ox_inventory:RegisterShop on the server, however they cannot utilise any client-only features.

Blips, markers, and zones will not be created.
Must use "locations" and not "targets" to define each shop using the archetype.
Example
exports.ox_inventory:RegisterShop('TestShop', {
    name = 'Test shop',
    inventory = {
        { name = 'burger', price = 10 },
        { name = 'water', price = 10 },
        { name = 'cola', price = 10 },
    },
    locations = {
        vec3(223.832962, -792.619751, 30.695190),
    },
    groups = {
        police = 0
    },
})

Custom Stashes
We can set up custom stashes from outside the resource utilising the exported RegisterStash function.

Firstly, we need to define the stashes properties.

Stash properties
id: string
Unique name to identify the stash in the database.
label: string
Display name when viewing the stash.
slots: number
Number of slots the stash will have.
weight: number
Maximum weight of the stash inventory.
owner?: string or boolean
true: Each player has their own unique stash, but can request to open the stash of another player
false: Only a single stash exists and is shared between all players
string: The stash explicitly belongs to the given owner, usually a player identifier
groups?: table
Key-value pairs of job name and minimum grade to be able to access the stash. ({["police"] = 0, ["ambulance"] = 2})
name: string
grade: number
coords?: vector3 or table
You can set the stash coordinates to prevent the stash from being opened if the player isn't close enough.
Vector or table containing the coordinates of the stash.
Example
Below the value is hardset, but it could be loaded from the database (especially if there are unknown fields, i.e. owner)

-- Server
local stash = {
    id = '42wallabyway',
    label = '42 Wallaby Way',
    slots = 50,
    weight = 100000,
    owner = 'char1:license'
}
 
AddEventHandler('onServerResourceStart', function(resourceName)
    if resourceName == 'ox_inventory' or resourceName == GetCurrentResourceName() then
        exports.ox_inventory:RegisterStash(stash.id, stash.label, stash.slots, stash.weight, stash.owner)
    end
end)
 
-- Client
exports.ox_inventory:openInventory('stash', {id='42wallabyway', owner=property.owner})
The following sample is based on esx_property's db data.

-- Server
local properties
 
MySQL.query('SELECT * FROM `properties`', {}, function(result)
    properties = result
end)
 
RegisterNetEvent('ox:loadStashes', function(id)
local stash = properties[id]
    if stash then
        -- id: 1, name: WhispymoundDrive, label: 2677 Whispymound Drive, coords: {"x":118.748,"y":566.573,"z":175.697}
        ox_inventory:RegisterStash(stash.name, stash.label, 50, 100000, true, false, json.encode(stash.room_menu))
    end
end)
 
-- Client
local ox_inventory = exports.ox_inventory
 
if ox_inventory:openInventory('stash', property.id) == false then
    TriggerServerEvent('ox:loadStashes')
    ox_inventory:openInventory('stash', property.id)
end
Example Resource
We put together an example resource showcasing how to properly utilise the stash API:

Ox Inventory Examples


Metadata
Item metadata is a very powerful tool that can be used to create multiple different items out of a single item.

In this guide we'll use pokemon cards as an example, but you can find an already integrated example in the inventory with the garbage item.

Creating the base item
First of all we need to create a base item that we'll use to apply metadata to.

/data/items.lua
['pokemon_card'] = {
    label = 'Pokemon card',
    weight = 10,
    consume = 0,
    server = {
        export = 'pokemon.pokemon_card'
    }
}
In this case we define the label and the weight as well since we are going to have all the cards weigh the same, but if you do not want them all to weigh the same you can leave it out and apply weight through metadata.

We'll also make the item usable by calling the pokemon_card export in the pokemon resource.

pokemon/server.lua
exports('pokemon_card', function(event, item, inventory, slot, data)
    if event == 'usingItem' then
        local itemSlot = exports.ox_inventory:GetSlot(inventory.id, slot)
        print(json.encode(itemSlot.metadata, {indent=true}))
    end
end)
Special metadata properties
You can define any metadata property with any value you want it to have, but there are a couple metadata properties that have special use cases.

These properties are:

label: string
Display name of the item
weight: number
Amount the item will weigh
description: string
Description of the item that will be displayed in the tooltip
image: string
Image inside the image path that the item will use
imageurl: string
Url to the image that the item will use
type: any
Item type that is displayed in top right of the tooltip
We'll use these properties to create our pokemon cards out of the pokemon_card item that we created earlier.

Creating metadata items
We can easily create metadata items by defining a hook using createItem and adding it to a shop as well.

/data/shops.lua
inventory = {
    {name = 'pokemon_card', price = 300, metadata = {
        label = 'Charizard',
        description = 'It is said that Charizard’s fire burns hotter if it has experienced harsh battles.',
        image = 'panties',
        type = 'Fire',
        hp = 78,
        attack = 84,
        defense = 78
    }}
}
pokemon/server.lua
local pokemonMetadata = {
    charizard = {
        label = 'Charizard',
        description = 'It is said that Charizard’s fire burns hotter if it has experienced harsh battles.',
        image = 'panties',
        type = 'Fire',
        hp = 78,
        attack = 84,
        defense = 78
    }
}
 
local hookId = exports.ox_inventory:registerHook('createItem', function(payload)
    local pokemon = pokemonMetadata[payload.metadata.type]
    if not pokemon then return end
    return pokemon
end, {
    itemFilter = {
        pokemon_card = true
    }
})
As seen above when our item is usable, the metadata properties are all there and accessible through the slot.

Displaying custom metadata properties
We can display our custom metadata we set on our charizard card by either using string concatenation and adding them to the description or by using the displayMetadata client function.

exports.ox_inventory:displayMetadata({
    hp = 'HP',
    attack = 'ATK',
    defense = 'DEF'
})



