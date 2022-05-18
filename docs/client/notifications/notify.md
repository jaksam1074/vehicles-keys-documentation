# Replace default notifications

Triggered after notifying player client side

## Event
``` lua
AddEventHandler("vehicles_keys:notify", function(message, uncoloredMessage)

end)
```

### Parameters

| Name              | Data Type | Description                 |
| -                 | -         | -                             |
| `message`         | string    | Message of the notification  |
| `uncoloredMessage`         | string    | Message of the notification but without ~r~, ~g~, etc.  |

## Example (you can place it in the folder integrations/cl_integrations.lua of the script)
``` lua
RegisterNetEvent("vehicles_keys:framework:ready", function() 
    -- Disables the default script notification (otherwise there would be 2 notifications)
    exports["vehicles_keys"]:disableScriptEvent("vehicles_keys:notify")
end)

RegisterNetEvent("vehicles_keys:notify", function(message, uncoloredMessage)
    TriggerEvent("external_script:notify", message)
end)
```