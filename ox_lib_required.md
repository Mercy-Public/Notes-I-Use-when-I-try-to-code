Shared
This module is always loaded by default.

require
Loads the given module. The function starts by indexing the loaded table to determine whether modname is already loaded. If it is, then require returns the value stored at loaded[modname].

Module names are the path to a file relative to the resource.
The module name must point to a .lua file.
Use . to separate directories in a path.
Modules can be loaded from external resources using @resource.modname.
require 'modname'
Client modules must be defined in the file section of the resource manifest.

fxmanifest.lua
file 'modname.lua'
-- or
files {
  'modname.lua'
}
Usage Example
- resources/
  - mylib/
    - import.lua
    - data/
      - events.lua
  - myresource/
    - server.lua
mylib/import.lua
local mylib = {
  events = require 'data.events'
}
 
print('Loaded mylib')
 
return mylib
mylib/data/events.lua
return {
  disconnect = 'onPlayerDropped',
}
myresource/server.lua
local mylib = require '@mylib.import'
print(mylib.events.disconnect)
lib.load
Loads and runs a Lua file at the given path. Unlike require, the chunk is not cached for future use.

lib.load(filePath, env)
filePath: string
A path to the Lua file, using the same rules as require.
env?: table
A table to use as the global environment, defaulting to _ENV.
Usage Example
myresource/import.lua
local events = lib.load('data.events')
 
print('Loaded events')
myresource/data/events.lua
return {
  disconnect = 'onPlayerDropped',
}
lib.loadJson
Loads a JSON file at the given path and decodes it as a table.

lib.loadJson(filePath)
filePath: string
A path to the Lua file, using the same rules as require.
Usage Example
myresource/import.lua
local events = lib.loadJson('data.events')
 
print('Loaded events')
myresource/data/events.json
{
  "disconnect": "onPlayerDropped"
}