Server

Registers commands and simplifies argument validation, permissions, and chat suggestions.

lib.addCommand(commandName, properties, cb)
commandName: string or string[]
properties: table or false
help?: string
restricted?: boolean or string or string[]
params?: table[]
name: string
help?: string
type?: 'number' or 'playerId' or 'string' or 'longString'
optional?: boolean
lib.addCommand('giveitem', {
    help = 'Gives an item to a player',
    params = {
        {
            name = 'target',
            type = 'playerId',
            help = 'Target player\'s server id',
        },
        {
            name = 'item',
            type = 'string',
            help = 'Name of the item to give',
        },
        {
            name = 'count',
            type = 'number',
            help = 'Amount of the item to give, or blank to give 1',
            optional = true,
        },
        {
            name = 'metatype',
            help = 'Sets the item\'s "metadata.type"',
            optional = true,
        },
    },
    restricted = 'group.admin'
}, function(source, args, raw)
    local item = Items(args.item)
 
    if item then
        Inventory.AddItem(args.target, item.name, args.count or 1, args.metatype)
    end
end)

Server
Wrapper around the built-in ACL system. Handles lib.addCommand and ox_groups permissions.
Refer to Basic Aces & Principals overview/guide for more information.

lib.addAce
Assigns the ace permission to a principal. Third parameter defaults to 'allow', while passing false sets the permission to 'deny'.

lib.addAce(principal, ace, allow)
 
lib.addAce('group.admin', 'command.say')
principal: string
ace: string
allow: boolean
lib.removeAce
Removes the ace permission from a principal. Third parameter defaults to 'allow', while passing false sets the permission to 'deny'.

lib.removeAce(principal, ace, allow)
 
lib.removeAce('group.admin', 'command.say')
principal: string
ace: string
allow: boolean
lib.addPrincipal
Assigns a principal to a parent principal. Children inherit permissions from the parent.

lib.addPrincipal(child, parent)
 
lib.addPrincipal('player.1', 'group.moderator')
child: string
parent: string
lib.removePrincipal
Removes a principal from a parent principal.

lib.removePrincipal(child, parent)
 
lib.removePrincipal('player.1', 'group.moderator')
child: string
parent: string