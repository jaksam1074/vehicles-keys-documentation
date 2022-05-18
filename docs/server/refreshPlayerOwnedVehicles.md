# Refresh player owned vehicles

Using this export (from server side) will refresh the list of the player's owned vehicles (from owned_vehicles on ESX or player_vehicles on QBCore)

## Event
```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
```

## Parameters
# Give keys to identifier

| Name              | Data Type | Description                 |
| -                 | -         | -                 |
| `playerId`         | integer    | The player server ID |"other_player" |

## Example
```lua
RegisterNetEvent("vehicle_shop:playerBoughtVehicle", function(playerId, plate)
    -- This will refresh the player's owned vehicles after he buys a vehicle (just an example)

    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
end)
```