Shared
Adds additional functions alongside the standard table library.

lib.table.contains
Checks if table contains the given value. Only intended for simple values and unnested tables.

lib.table.contains(tbl, value)
tbl: table
value: any
Return:

isContained: boolean
lib.table.matches
Compares if two values are equal, iterating over tables and matching both keys and values.

lib.table.matches(tableOne, tableTwo)
tableOne: table
tableTwo: table
Return:

matches: boolean
lib.table.deepclone
Recursively clones a table to ensure no table references remain.

lib.table.deepclone(tbl)
tbl: table
Return:

clonedTable: table
lib.table.merge
Merges two tables together. Duplicate keys will be added together if they are numbers, otherwise tableTwo's value will be used.

lib.table.merge(tableOne, tableTwo)
tableOne: table
tableTwo: table
Return:

tableOne: table
lib.table.freeze
Makes a table read-only, preventing further modification. Unfrozen tables stored within table are still mutable.

lib.table.freeze(tbl)
tbl: table
Return:

frozenTable: table
lib.table.isFrozen
Returns true if tbl is set as read-only.

lib.table.isFrozen(tbl)
tbl: table
Return:

isFrozen: boolean