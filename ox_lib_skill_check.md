Skill Check
lib.skillCheck
Runs a skill check with the defined difficulty.

lib.skillCheck(difficulty, inputs)
difficulty: 'easy' or 'medium' or 'hard' or table
Preset difficulties:
'easy' - { areaSize: 50, speedMultiplier: 1 }
'medium' - { areaSize: 40, speedMultiplier: 1.5 }
'hard' - { areaSize: 25, speedMultiplier: 1.75 }
Custom difficulties can be set by sending an object instead of one of the preset strings above
areaSize: number
Size of the success area in degrees
speedMultiplier: number
Multiplier for the speed of the indicator
inputs?: string[]
A random key will be picked from the inputs table for each skill check
If no inputs are defined the key is defaulted to e
lib.skillCheckActive
Returns true if a skill check is currently active.

lib.skillCheckActive()
lib.cancelSkillCheck
Cancels the currently ongoing skill check.

lib.cancelSkillCheck()
Usage Example
local success = lib.skillCheck({'easy', 'easy', {areaSize = 60, speedMultiplier = 2}, 'hard'}, {'w', 'a', 's', 'd'})