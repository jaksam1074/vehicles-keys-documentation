# Vehicle window broken

## Event
```lua
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(vehicle)

end)
```

### Parameters

| Name              | Data Type | Description                 |
| -                 | -         | -                 |
| `vehicle`         | integer (vehicle)    | The vehicle handle |

## Example
```lua
RegisterNetEvent("vehicles_keys:vehicleWindowBroken", function(vehicle)
    print("The window of vehicle " .. vehicle .. " has been broken")
end)
```