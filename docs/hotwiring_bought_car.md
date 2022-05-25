# Fix hotwiring bought car
If after you purchase a vehicle you have to hotwire it, you only have to add [this simple line of code](client/refreshMineOwnedVehicles.md) 

Otherwise, there are some common scripts solutions below:

## esx_vehicleshop

### First step

Go to `esx_vehicleshop/server/main.lua` and search for the following code:

![esx_vehicleshop before](images_dealership_scripts/esx_vehicleshop_setVehicleOwnedPlayerId_before.png)

And add this line 
```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(playerId)
```

![esx_vehicleshop before](images_dealership_scripts/esx_vehicleshop_setVehicleOwnedPlayerId_after.png)

### Second step

Go to `esx_vehicleshop/server/main.lua` (the same file as before) and search for the following code:

![esx_vehicleshop before](images_dealership_scripts/esx_vehicleshop_buyVehicle_before.png)

And add this line 
```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(source)
```

![esx_vehicleshop before](images_dealership_scripts/esx_vehicleshop_buyVehicle_after.png)

## esx_advancedvehicleshop
Go to `esx_advancedvehicleshop/server/main.lua` and search for the following code:

![esx_advancedvehicleshop before](images_dealership_scripts/esx_advancedvehicleshop_before.png)

And add this line 
```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(source)
```


![esx_advancedvehicleshop after](images_dealership_scripts/esx_advancedvehicleshop_after.png)

## qb-vehicleshop

### First step

Go to `qb-vehicleshop/server.lua` and you will have to add the following code after **all** `exports.oxmysql:insert` 

In the example, it will be shown only one time, but you have to add it multiple times

![qb-vehicleshop before](images_dealership_scripts/qb-vehicleshop_before.png)

And add the following code

```lua
SetTimeout(1000, function() 
    exports["vehicles_keys"]:refreshPlayerOwnedVehicles( pData.PlayerData.source )
end)
```

In certain parts, you will have to replace `pData` with something else, here it will show where to add the code and on what `pData` depends

![qb-vehicleshop after](images_dealership_scripts/qb-vehicleshop_after.png)

**Note**: the green circles showed in the screenshot must match, so if the first one is for example `targetPlayer`, the second one must be `targetPlayer` as well

### Second step

Go to `qb-vehicleshop/server.lua` (the same file as before) and replace all these events (they are at the bottom of the file)
```lua
TriggerClientEvent('vehiclekeys:client:SetOwner', buyerId, plate)
``` 

with the following code

```lua
SetTimeout(1000, function() 
    exports["vehicles_keys"]:refreshPlayerOwnedVehicles(buyerId)
end)
```


## okokVehicleShop

Go to `okokVehicleShop/sv_utils.lua` and search for the following code:

![okokVehicleShop before](images_dealership_scripts/okokVehicleShop_before.png)

And add this line 
```lua
exports["vehicles_keys"]:refreshPlayerOwnedVehicles(_source)
```

![okokVehicleShop before](images_dealership_scripts/okokVehicleShop_after.png)