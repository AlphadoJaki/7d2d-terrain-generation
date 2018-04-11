# Select
Mix 2 sourceModules into an output. "controlModule" & "bounds" determines which sourceModule appears. By default, transition is abrupt. For smooth transition, use "edgeFallOff". Higher value smooth more.

## Parameters
### controlModule
Module determines which sourceModule appears, using with bounds.

### sourceModule1
The module appears where controlModule is outside of bounds.

### sourceModule2
The module appears where controlModule is inside of bounds.

### bounds
Choose 2 numbers to set a bounds.

### edgeFallOff
Determines transition area for both side of each bound. Larger number means more smooth transition
