lib.showContext
Opens a registered context menu by its id.

lib.showContext(id)
id: string
lib.hideContext
Hides any currently visible context menu.

lib.hideContext(onExit)
onExit: boolean
Defines whether the onExit function for the menu should be ran or not.
lib.getOpenContextMenu
Returns the id of the currently open context menu.

If no context menu is open returns nil.

lib.getOpenContextMenu()
Usage Example
First we register the menu with our specified options then we call the show function in the command.

Avoid constantly re-registering a menu that does not depend on any outside values (A.K.A a static menu).

lib.registerContext({
  id = 'some_menu',
  title = 'Some context menu',
  options = {
    {
      title = 'Empty button',
    },
    {
      title = 'Disabled button',
      description = 'This button is disabled',
      icon = 'hand',
      disabled = true
    },
    {
      title = 'Example button',
      description = 'Example button description',
      icon = 'circle',
      onSelect = function()
        print("Pressed the button!")
      end,
      metadata = {
        {label = 'Value 1', value = 'Some value'},
        {label = 'Value 2', value = 300}
      },
    },
    {
      title = 'Menu button',
      description = 'Takes you to another menu!',
      menu = 'other_menu',
      icon = 'bars'
    },
    {
      title = 'Event button',
      description = 'Open a menu from the event and send event data',
      icon = 'check',
      event = 'test_event',
      arrow = true,
      args = {
        someValue = 500
      }
    }
  }
})
Then we can also register our second menu called other_menu

lib.registerContext({
  id = 'other_menu',
  title = 'Other context menu',
  menu = 'some_menu',
  onBack = function()
    print('Went back!')
  end,
  options = {
    {
      title = 'Nothing here'
    }
  }
})
And the event that we are going to run from the some_menu menu, which is going to open another menu.

RegisterNetEvent('test_event', function(args)
  lib.registerContext({
    id = 'event_menu',
    title = 'Event menu',
    menu = 'some_menu',
    options = {
      {
        title = 'Event value: '..args.someValue,
      }
    }
  })
 
  lib.showContext('event_menu')
end)
Lastly we register a test command to show the some_menu menu.

RegisterCommand('testcontext', function()
  lib.showContext('some_menu')
end)
The data from the args table in the menu is passed as a first argument to the event you register.

Using this event we also register a new context menu with it's own options.

By defining a menu param to be the id of the first menu we can get the back arrow button next to the menu title that will take us back.