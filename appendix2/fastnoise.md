# FastNoise

Outputs the perlin noise, which is the sum of gradient coherent noises. Each of coherent noises has decreasing amplitude and increasing frequency.

Most part of FastNoise is in the -1 to 1 bound.

Ensure to use unique seed\_additive, unless you expect completely same noise with others.

## Parameters

### octaveCount

Property which decides output noise detail. Integer value 1 to 30 is valid. This count is the number of coherent noise to sum up. Later noises decrease amplitude and increase frequency.

### frequency

Oscillating frequency of the first noise. \(Second noise: frequency x lacunarity\)

### persistence

Property which decides output noise roughness. Larger persistence, rougher noise outputs. This is multiplied with the amplitude when next coherent noise is added. \(If you set persistence=0.5, 1st noise:-1 to 1, 2nd noise:-0.5 to 0.5,....\)

### lacunarity

Lacunarity is multiplied with frequency, when next coherent noise is added.

### noiseQuality

Property which decides quality of base noises. 0 is linear, 1 is square, 2 is cubic quality.

## Difference with un-Fast module

FastNoise module is the optimized version of Perlin module. Mostly good, but sometime contour lines generates un-natural squares. Frequency for Perlin is about 5 times as frequent as one for FastNoise. Be careful when you use the other.

## Screenshot

Gray-scale elevation mapping: Black is -1, White is +1. Red area is out of -1 to +1 bound.

![](/assets/BoundCheck_FastNoise.png)

