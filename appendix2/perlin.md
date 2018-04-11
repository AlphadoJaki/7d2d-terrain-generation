# ~~Perlin~~

Outputs the perlin noise. High quality version of _FastNoise_. Most of information is same with FastNoise, see FastNoise for further information.

This module is **UN-AVAILABLE** for now.

## Parameters

### octaveCount

### frequency

### persistence

### lacunarity

### noiseQuality

## Difference with un-Fast module

FastNoise module is the optimized version of Perlin module. Mostly good, but sometime contour lines generates un-natural squares. Frequency for Perlin is about 5 times as frequent as one for FastNoise. Be careful when you use the other.

## Screenshot

Gray-scale elevation mapping: Black is -1, White is +1. Red area is out of -1 to +1 bound.

![](/assets/BoundCheck_Perlin.png)

