# FastTurbulence

Distort _**sourceModule**_ using _FastNoise_. Larger _**power**_, more wavy/warping output. Larger _**frequency**_, more noisy output.

Ensure to use unique seed\_additive, unless you expect completely same noise with others.

## Parameters

### sourceModule

Choose which module to distort.

### frequency

Frequency of FastNoise used to distort.

### power

Amplitude of FastNoise used to distort.

### roughness

Octove count of FastNoise used to distort.

## Screenshot

Gray-scale elevation mapping: Black is -1, White is +1. Used Checkerboad as a sourceModule.

### Input:

![](/assets/FastTurbulence1.png)

### Output:

![](/assets/FastTurbulence2.png)

