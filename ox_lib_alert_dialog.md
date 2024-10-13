-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

Alert Dialog
Simple alert dialog that can display a message to the player.
Returns whether the player pressed the confirm button or canceled the dialog.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

lib.alertDialog

Client

lib.alertDialog(data)
data: table (object)
header: string
Dialog title.
content: string
Dialog body content, supports markdown.
centered?: boolean
Centers the dialog vertically and horizontally.
cancel?: boolean
Displays a cancel button (ESC is still available if this is not defined).
size?: 'xs' or 'sm' or 'md' or 'lg' or 'xl'
overflow?: boolean
labels?: table
Allows you to define the displayed labels for cancel and/or confirm buttons.
cancel?: string
confirm?: string
Returns 'confirm' if the player pressed the confirm button, otherwise if the player pressed the cancel button or has exited the dialog with ESC the return will be 'cancel'.

server

TriggerClientEvent('ox_lib:alertDialog', source, data)
data: table (object)
header: string
Dialog title.
content: string
Dialog body content, supports markdown.
centered?: boolean
Centers the dialog vertically and horizontally.
cancel?: boolean
Displays a cancel button (ESC is still available if this is not defined).
size?: 'xs' or 'sm' or 'md' or 'lg' or 'xl'
overflow?: boolean
labels?: table
Allows you to define the displayed labels for cancel and/or confirm buttons.
cancel?: string
confirm?: string
Returns 'confirm' if the player pressed the confirm button, otherwise if the player pressed the cancel button or has exited the dialog with ESC the return will be 'cancel'.

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------

lib.closeAlertDialog

lib.closeAlertDialog()

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------


Example

local alert = lib.alertDialog({
    header = 'Hello there',
    content = 'General Kenobi  \n Markdown support!',
    centered = true,
    cancel = true
})
 
print(alert)

-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------------------------------------------------------
