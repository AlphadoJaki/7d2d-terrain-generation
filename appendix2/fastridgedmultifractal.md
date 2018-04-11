# FastRidgedMultifractal

Outputs the ridged multifractal noise. Most of information is same with FastNoise, excepting this module generates complex ridge.

Most part of FastRidgedMultifractal is in the -1 to 1 bound, and never go lower than -1. If you set octaveCount as 1, most part is in -1 to 0. Use 4 or higher to generate well grown noise.

## Parameters

### octaveCount

### frequency

### ~~persistence~~

This module has no persistence parameter. This uses a reciprocal number of lacunarity, instead.

### lacunarity

### noiseQuality

## Difference with un-Fast module

FastRidgedMultifractal module is the optimized version of RidgedMultifractal module. Mostly good, but sometime contour lines generates un-natural squares. Frequency for RidgedMultifractal is about 5 times as frequent as one for FastRidgedMultifractal. Be careful when you use the other.

## Screenshot

Gray-scale elevation mapping: Black is -1, White is +1. Red area is out of -1 to +1 bound.

![](/assets/BoundCheck_FastRidgedMultifractal.png)

