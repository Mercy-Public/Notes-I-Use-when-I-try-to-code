Client
Trigger Server Callback
lib.callback
The response is handled in a separate coroutine.

lib.callback(name, delay, cb, ...)
name: string
delay: number or false
Amount of time until this callback can be triggered again
cb: function
...: any
lib.callback('ox_inventory:getItemCount', false, function(count)
    print(count)
end, 'water', {type = 'fresh'})
lib.callback.await
The current coroutine is yielded until a response is received.

lib.callback.await(name, delay, ...)
name: string
delay: number or false
Amount of time until this callback can be triggered again
...: any
local count = lib.callback.await('ox_inventory:getItemCount', false, 'water', {type = 'fresh'})
print(count)
Register Client Callback
lib.callback.register
Register an event handler for responding to server requests.

lib.callback.register(name, cb)
name: string
cb: function
lib.callback.register('ox:getNearbyVehicles', function(radius)
    local nearbyVehicles = lib.getNearbyVehicles(GetEntityCoords(cache.ped), radius, true)
    return nearbyVehicles
end)


Server
Trigger Client Callback
lib.callback
The response is handled in a separate coroutine.

lib.callback(name, playerId, cb, ...)
name: string
playerId: number
cb: function
...: any
lib.callback('ox:getNearbyVehicles', source, function(vehicles)
    for i = 1, #vehicles do
        DeleteEntity(entity)
    end
end, args.radius)
lib.callback.await
The current coroutine is yielded until a response is received.

lib.callback.await(name, playerId, ...)
name: string
playerId: number
...: any
local vehicles = lib.callback.await('ox:getNearbyVehicles', source, args.radius)
 
for i = 1, #vehicles do
    DeleteEntity(entity)
end
Register Server Callback
lib.callback.register
Register an event handler for responding to client requests.

lib.callback.register(name, cb)
name: string
cb: function
lib.callback.register('ox_inventory:getItemCount', function(source, item, metadata, target)
    local inventory = target and Inventory(target) or Inventory(source)
    return (inventory and Inventory.GetItem(inventory, item, metadata, true)) or 0
end)

