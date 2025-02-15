Progress
lib.progressBar
Displays a running progress bar.

lib.progressBar(data)
duration: number
label: string
useWhileDead?: boolean
allowRagdoll?: boolean
allowSwimming?: boolean
allowCuffed?: boolean
allowFalling?: boolean
canCancel?: boolean
anim?: table (object)
dict?: string
Must specify either scenario or dict
clip: string
flag?: number
Default: 49
blendIn?: float
Default: 3.0
blendOut?: float
Default: 1.0
duration?: number
Default: -1
playbackRate?: number
Default: 0
lockX?: boolean
lockY?: boolean
lockZ?: boolean
scenario?: string
Must specify either scenario or dict
playEnter?: boolean
Default: true
prop?: table (object or array)
[ If you want to define multiple props, you can pass them as individual tables (array of objects) ]
model: hash
bone?: number
Default: 60309
pos: table
x: number
y: number
z: number
rot: table (object)
x: number
y: number
z: number
rotOrder?: number
The order in which yaw, pitch and roll is applied.
Default: 0
disable?: table (object)
move?: boolean
car?: boolean
combat?: boolean
mouse?: boolean
sprint?: boolean
Usage Example
if lib.progressBar({
    duration = 2000,
    label = 'Drinking water',
    useWhileDead = false,
    canCancel = true,
    disable = {
        car = true,
    },
    anim = {
        dict = 'mp_player_intdrink',
        clip = 'loop_bottle'
    },
    prop = {
        model = `prop_ld_flow_bottle`,
        pos = vec3(0.03, 0.03, 0.02),
        rot = vec3(0.0, 0.0, -1.5)
    },
}) then print('Do stuff when complete') else print('Do stuff when cancelled') end
progress_bar

lib.progressCircle
Similar to lib.progressBar except it displays a circle and you can define a position.

lib.progressCircle(data)
duration: number
label?: string
position?: 'middle' or 'bottom'
Default: 'middle'
useWhileDead?: boolean
allowRagdoll?: boolean
allowSwimming?: boolean
allowCuffed?: boolean
allowFalling?: boolean
canCancel?: boolean
anim?: table (object)
dict?: string
Must specify either scenario or dict
clip: string
flag?: number
Default: 49
blendIn?: float
Default: 3.0
blendOut?: float
Default: 1.0
duration?: number
Default: -1
playbackRate?: number
Default: 0
lockX?: boolean
lockY?: boolean
lockZ?: boolean
scenario?: string
Must specify either scenario or dict
playEnter?: boolean
Default: true
prop?: table (object or array)
[ If you want to define multiple props, you can pass them as individual tables (array of objects) ]
model: hash
bone?: number
Default: 60309
pos: table
x: number
y: number
z: number
rot: table (object)
x: number
y: number
z: number
rotOrder?: number
The order in which yaw, pitch and roll is applied.
Default: 0
disable?: table (object)
move?: boolean
car?: boolean
combat?: boolean
mouse?: boolean
sprint?: boolean
Usage Example
if lib.progressCircle({
    duration = 2000,
    position = 'bottom',
    useWhileDead = false,
    canCancel = true,
    disable = {
        car = true,
    },
    anim = {
        dict = 'mp_player_intdrink',
        clip = 'loop_bottle'
    },
    prop = {
        model = `prop_ld_flow_bottle`,
        pos = vec3(0.03, 0.03, 0.02),
        rot = vec3(0.0, 0.0, -1.5)
    },
}) then print('Do stuff when complete') else print('Do stuff when cancelled') end
progress_circle

lib.progressActive
Returns true if a progress bar is currently active.

lib.progressActive()
lib.cancelProgress
If there is a progress bar active and the progress bar can be cancelled then it cancels it.

lib.cancelProgress()