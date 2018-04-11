## Base Module

Following modules generates independent terrain base  No source module is required  
Any generators consists of modified or mixed base modules.  
Any modules starts with base modules.

FastNoise

* Make a combined sin wave. 

Perlin

* Make a combined perlin wave.
* This module is **NOT** available for now. I wonder why they disabled.

FastBillow

* Make a upper side of FastNoise.

Billow

* Make a upper side of Perlin.

FastRidgedMultifractal

* Make a combined ridged sin wave.

RidgedMultifractal

* Make a combined ridged perlin wave.

Checkerboard

* Make a checkerboard.
* The squares whose elevation is 1 and ones to -1 appear alternatingly
* Each of square is 512x512.

Constant

* Make a completely flat board.
* "constant" is the elevation of this module.

Cylinders

* Make a ripple oscillating between -1 to 1.
* This module start at 0,0 with 1 elevation.
* Distance between each peak is 512

Spheres

* Make a Cylinders for 3d axis.
* I doubt this can work with current 7D2D.

Voronoi

* Make a voronoi diagram.
* If distanceEnable is true, the elevation changes from center to edge gradually.

## Modification Module

Following modules receive an existing module, and make some modification with it.

ScaleInput

* Shrink / Extend "sourceModule" toward X, Z axis.
  * Or, you can understand as a reassignment of frequency.
* You can do toward Y axis, but it isn't what you may imagine.

ScaleOutput

* Extend / Shrink "sourceModule" toward elevation axis.

TranslateInput

* Shifts "sourceModule" toward X, Z axis.
* You can do toward Y axis, but it isn't what you may imagine.

BiasOutput

* Shifts "sourceModule" toward elevation axis.

RotateInput

* Rotate "sourceModule" on Y axis.
* You can do on X, Z axis, but it isn't what you may imagine.
* Integer value is only valid, although this uses radian to rotate.

ScaleBiasOutput

* The combination of ScaleOutput and BiasOutput.
  * At 1st, ScaleOutput process, next, BiasOutput process.

AbsoluteOutput

* Output the absolute value of elevation.

InvertInput

* Invert "sourceModule" toward X & Z axis.

InvertOutput

* Invert "sourceModule" toward elevation axis.

ClampOutput

* Set a limit on elevation between "bounds".
* Exceeded value is replaced with closer bound.

FastTurbulence

* Distort "sourceModule" with FastNoise.
* Larger power, more wavy output.
* Larger frequency, more noisy output.

Turbulence

* Distort "sourceModule" with Perlin.
* "seed\_additive" is NOT working.

DisplaceInput

* Distort "sourceModule" with existing modules.

ExponentialOutput

* Remap "sourceModule" with exponent of "base".

Terrace

* Make "sourceModule" like stairs \(terrace\).

CurveOutput

* Map the elevation from "sourceModule" on to user-defined curve.
* This module provides curve using 4 "curvePoints" around the value.

## Mixture Module

Following modules receive two or more modules, and make them into the new mixed module.

Add

* Simply add 2 modules into output module.

Blend

* Mix 2 modules gradually.
* As "controlModule" goes for -1, "sourceModule1" emerges,
  as "controlModule" goes for+1, "sourceModule2" emerges.
* It is better to regularize "controlModule" into -1 to +1 bounds.

Select

* Mix 2 modules gradually. More customizable than Blend.

LargerOutput

* Simply output the module whose elevation is larger at each coordinate.

SmallerOutput

* Simply output the module whose elevation is smaller at each coordinate.

Multiply

* Simply multiply 2 module into output module.

Power

* Simply make power of base module into output module.



