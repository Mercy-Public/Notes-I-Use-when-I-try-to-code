Menu
Keyboard navigation menu with specific event functions.

lib.registerMenu
Registers and caches a menu under the specified id.

lib.registerMenu(data, cb)
data: table (object)
id: string
title: string
options: table (array)
label: string
progress?: number
colorScheme?: string
icon?: string
FontAwesome icon that will be displayed on the left side, works the same as notification and textui icons.
Also supports image urls, png and webp files but are not recommend to use over font awesome icons.
iconColor?: string
iconAnimation?: 'spin' 'spinPulse' 'spinReverse' 'pulse' 'beat' 'fade' 'beatFade' 'bounce' 'shake'
values?: string[] or { label: string, description: string }[]
If provided creates a side scrollable list.
When using object and setting description, the set description will be displayed in the menu tooltip.
checked?: boolean
Setting either true or false will make the button a checkbox, if values is also provided the button will be a scrollable list.
description?: string
Displays tooltip below menu on hovered item with provided description.
defaultIndex?: number
Sets the current index for the list to specified number.
args?: {[string]: any}
Allows you to pass any arguments through the button.
If the button has values then isScroll is automatically passed.
If the button has checked to either true or false then isCheck is automatically passed.
close?: boolean
If set to false, it won't close the menu upon interacting with this option.
position?: 'top-left' or 'top-right' or 'bottom-left' or 'bottom-right'
Default: 'top-left'
disableInput?: boolean
Default: false
canClose: boolean
If set to false the user won't be able to exit the menu without pressing one of the buttons.
onClose: function(keyPressed?: 'Escape' | 'Backspace')
Function that runs when the menu is exited via ESC/Backspace.
onSelected: function(selected: number, secondary: number | boolean, args: {[string]: any})
Function being ran when the selected button in the menu changes.
onSideScroll: function(selected: number, scrollIndex: number, args: {[string]: any})
Function ran whenever a scroll list item is changed.
onCheck: function(selected: number, checked: boolean, args: {[string]: any})
Function ran whenever a checkbox is toggled.
cb: function(selected: number, scrollIndex: number, args: {[string]: any})
Callback function when the menu item is pressed.
lib.showMenu
Displays the menu with the provided id.

lib.showMenu(id)
id: string
lib.hideMenu
lib.hideMenu(onExit)
onExit?: boolean
If true runs the menu's onClose function.
lib.getOpenMenu
Returns the id of the currently open menu.

lib.getOpenMenu()
lib.setMenuOptions
lib.setMenuOptions(id, options, index)
id: string
options: table (object or array)
index?: number
If specified only sets the options table on the specified options index.
Example:
Replaces the 3rd index option of the specified menu

lib.setMenuOptions('some_menu_id', {label = 'New option', icon = 'plus'}, 3)
Usage Example
First we register the menu with our specified options then we call the show function in the command.

Avoid constantly re-registering a menu that does not depend on any outside values (A.K.A a static menu).

lib.registerMenu({
    id = 'some_menu_id',
    title = 'Menu title',
    position = 'top-right',
    onSideScroll = function(selected, scrollIndex, args)
        print("Scroll: ", selected, scrollIndex, args)
    end,
    onSelected = function(selected, secondary, args)
        if not secondary then
            print("Normal button")
        else
            if args.isCheck then
                print("Check button")
            end
 
            if args.isScroll then
                print("Scroll button")
            end
        end
        print(selected, secondary, json.encode(args, {indent=true}))
    end,
    onCheck = function(selected, checked, args)
        print("Check: ", selected, checked, args)
    end,
    onClose = function(keyPressed)
        print('Menu closed')
        if keyPressed then
            print(('Pressed %s to close the menu'):format(keyPressed))
        end
    end,
    options = {
        {label = 'Simple button', description = 'It has a description!'},
        {label = 'Checkbox button', checked = true},
        {label = 'Scroll button with icon', icon = 'arrows-up-down-left-right', values={'hello', 'there'}},
        {label = 'Button with args', args = {someArg = 'nice_button'}},
        {label = 'List button', values = {'You', 'can', 'side', 'scroll', 'this'}, description = 'It also has a description!'},
        {label = 'List button with default index', values = {'You', 'can', 'side', 'scroll', 'this'}, defaultIndex = 5},
        {label = 'List button with args', values = {'You', 'can', 'side', 'scroll', 'this'}, args = {someValue = 3, otherValue = 'value'}},
    }
}, function(selected, scrollIndex, args)
    print(selected, scrollIndex, args)
end)
 
RegisterCommand('testmenu', function()
    lib.showMenu('some_menu_id')
end)