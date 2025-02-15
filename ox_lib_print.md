Shared
Prints to console conditionally based on convars set. Different level prints are colored and labeled. Resource name is always included.

lib.print
lib.print.error(...)
lib.print.warn(...)
lib.print.info(...)
lib.print.verbose(...)
lib.print.debug(...)
vararg: any
What to print in console. Converts tables into a pretty-print format.
Example
lib.print.warn("query latency high: ", latency)
Levels
Error

Indicates a failure in the system.
Warn

Warns of an unexpected condition, or a state which is likely to cause an error in the future.
Info

Information about high-level, successful operations.
Verbose

More detailed information containing intermediate steps of high-level, operations
Debug

Used by developers to understand the system and may contain detailed trace information. Should generally not be turned on when not debugging.
Config
Use the following convars to set your print level. Prints less severe than the current level will not be executed. For example, a level of info will print error, warn, and info, but not verbose nor debug. Defaults to info if not set. Resource specific print levels override the global convar.

set ox:printlevel "info"
set ox:printlevel:ox_inventory "warn"
set ox:printlevel:<resourceName> "<level>"