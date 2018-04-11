# Billow

Outputs the billowy noise. High quality version of _FastBillow_. Most of information is same with FastNoise, see FastNoise for further information.

Most part of FastBillow is in the -1 to 1 bound.

## Parameters

### octaveCount

### frequency

### persistence

### lacunarity

### noiseQuality

## Difference with un-Fast module

FastBillow module is the optimized version of Billow module. Mostly good, but sometime contour lines generates un-natural squares. Frequency for Billow is about 5 times as frequent as one for FastBillow. Be careful when you use the other.

## Screenshot

Gray-scale elevation mapping: Black is -1, White is +1. Red area is out of -1 to +1 bound.

![](/assets/BoundCheck_Billow.png)

