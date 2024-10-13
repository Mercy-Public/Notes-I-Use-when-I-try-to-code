TextUI
lib.showTextUI
Show the TextUI window.

DO NOT run this function every tick, it's intended to be used as a toggle.

lib.showTextUI(text, options)
text: string
options?: table
position?: 'right-center' or 'left-center' or 'top-center' or 'bottom-center'
Default: 'right-center'
icon?: string or table (array)
iconColor?: string
iconAnimation?: 'spin' 'spinPulse' 'spinReverse' 'pulse' 'beat' 'fade' 'beatFade' 'bounce' 'shake'
style?: React.CSSProperties
alignIcon?: 'top' or 'center'
Default: 'center'
lib.hideTextUI
Hides the currently visible TextUI window

lib.hideTextUI()
lib.isTextUIOpen
Returns whether Text UI is opened or not. The currently displayed text is returned as the second value.

local isOpen, text = lib.isTextUIOpen()
Usage Example
Basic
lib.showTextUI('[E] - Fuel vehicle')
basic_example

Custom styling
lib.showTextUI('[E] - Pick apple', {
    position = "top-center",
    icon = 'hand',
    style = {
        borderRadius = 0,
        backgroundColor = '#48BB78',
        color = 'white'
    }
})