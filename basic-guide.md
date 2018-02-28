# Basic Guide

In this chapter, we describe typical modules frequently used, and show example code for terrain generation.  
However, let we note some technical terms and rules to understand the terrain generation.

## Terms of modules

At first, start with a few technical terms used in modules.  
Here we give an example code of module.

```xml
    <module name="exampleModule1" type="FastNoise" no_seed="false" seed_additive="1" >
        <property name="frequency" value="0.5" />
    </module>
```

Let's see one by one.

### name

Yeah, this is the name of module shortly.  
Formally, this is the ID for a module you made.  
You can use any names as you like as long as XML syntax is valid.  
Duplicate with existing name is prohibited.

### type

Predefined type of module. There is 33 types available for now.

### no\_seed

Choose whether this module refers the seed of world \(name of one\).  
If you set it _**true**_, the module generates completely SAME terrain as long as you use same _property_ and _seed\_additive_ \(see next\).  
_true_ or _false_ is valid and _**false**_ is default.

### seed\_additive

Shortly, this is _**the SEED for the SEED**_.  
Theoretically, the modules, whose _type_ and _property_ are same, generate a completely same result even if their names are different.  
So, using same seed\_additive is no way in the most cases.  
\(You can use existing module.\)  
If you don't set seed\_additive, 0 is set.

NOTE:  
no\_seed & seed\_additive are available only for FastNoise, Perlin, FastBillow, Billow, FastRidgedMultifractal and FastTurbulence. \(Not working for Turbulence\)

## Rule for terrain generation

Generation process has several rules.  
It is not essential to know following rules, but be useful if you go deeper modding.  
You can be back here when need them.

### Actual elevation

Although we can generate terrain via rwgmixer.xml, the elevation in XML and the one in actual game-play have some gap.  
If you made super-flat terrain at 0 via XML, you will see -26 in game.

### Generation bound

The elevation of the world is limited to -30 ~ 190. \(Elevation in XML, not in-game\)  
If some area is higher or lower than the restriction, that area is inverted to stay in it.  
You can skip this restriction, though had better not do.

### Water generation

The pits generated below 0 \(XML\) is filled with the **water**.  
We are not saying about the _water biome_, but the _**water block**_.  
Even if you change the water biome distribution, this rule can't be changed.  
This can be changed via setting **base\_height** attribute in **terrain\_generator** element, but this is like a testing feature.

## Typical Module

We will see the basic modules frequently used.  
There are 33 type modules are available, though following 7 modules are important especially.

### Base Module

#### FastNoise

Make a combined smooth sin wave within -1.5 ~ 1.5 and most of them stay in -1.0 ~1.0.  
Property frequency controls how frequently peaks of wave emerge.  
Nice to use as controModule in Blend module or as base of terrain.

```xml
    <module name="foo" type="FastNoise" seed_additive="0" no_seed="false">
        <property name="frequency" value="1.0"/>
    </module>
```

This is the 2D image of generated FastNoise.

![](/image/FastNoise.png)

#### FastBillow

Make a billowy terrain within -1.0 ~ 2.0 and most of them stay in -1.0 ~ 1.0.  
For property frequency, see FastNoise module.  
Nice to use as base of terrain, which sometime produce lowland in line.

```xml
    <module name="bar" type="FastBillow" seed_additive="1" no_seed="false">
        <property name="frequency" value="1.0"/>
    </module>
```

This is the image of generated FastBillow.

![](/image/FastBillow.png)

#### FastRidgedMultifractal

Make a ridged \(peaks are in line\) terrain within -1.0 ~ 1.3 and most of them stay in -0.75 ~ 1.0.  
For property frequency, see FastNoise.  
Perfect to use as mountain area.

```xml
    <module name="blah" type="FastRidgedMultifractal" seed_additive="2" no_seed="false">
        <property name="frequency" value="1.0"/>
    </module>
```

### Modification Module

#### ScaleBiasOutput

Multiply "sourceModule" with scale property, and then add with bias property.  
In other word, this extend / shrink sourceModule and then shift toward elevation axis.

```xml
    <module name="mambo" type="ScaleBiasOutput">
        <property name="sourceModule" value="blah"/>
        <property name="scale" value="50.0"/>
        <property name="bias" value="50.0"/>
    </module>
```

#### ClampOutput

Set a limit of sourceModule on elevation between "bounds".  
Exceeded value is replaced with ther closer “bounds”.

```xml
    <module name="jumbo" type="ClampOutput">
        <property name="sourceModule" value="bar"/>
        <property name="bounds" value="-1.0, 1.5"/>
    </module>
```

This is the image of how ClampOutput works.

![](/image/Clamp.png)

#### FastTurbulence

Distort "sourceModule" with FastNoise.  
Larger power, more wavy output.  
Larger frequency, more noisy output.

```xml
    <module name="abla" type="FastTurbulence" seed_additive="3" no_seed="false">
        <property name="sourceModule" value="mambo"/>
        <property name="frequency" value="0.2"/>
        <property name="power" value="3"/>
    </module>
```

### Mixture Module

#### Blend

Mix 2 modules gradually.  
As "controlModule" goes for -1, "sourceModule1" emerges.  
As "controlModule" goes for +1, "sourceModule2" emerges.

```xml
    <module name="catabla" type="Blend">
        <property name="sourceModule1" value="jumbo"/>
        <property name="sourceModule2" value="abla"/>
        <property name="controlModule" value="foo"/>
    </module>
```

This is the image of how Blend works.

![](/image/Blend.png)

## Example

Finally, here we show simple example code of terrain generation.  
Find terrain\_generators and replace with following code.  
Nice terrain will be generated with only these 8 modules.

**TODO** : explanation of this generator.

```xml
    <terrain_generators>
        <terrain_generator name="vanilla" use_old_final="false">

            <module name="landBase" type="FastBillow" seed_additive="0" no_seed="true">
                <property name="frequency" value="0.2"/>
            </module>
            <module name="landScaled" type="ScaleBiasOutput">
                <property name="sourceModule" value="landBase"/>
                <property name="scale" value="20"/>
                <property name="bias" value="0"/>
            </module>

            <module name="mountainBase" type="FastRidgedMultifractal" seed_additive="1" no_seed="true">
                <property name="frequency" value="0.4"/>
            </module>
            <module name="mountainWavy" type="FastTurbulence" seed_additive="2" no_seed="true">
                <property name="sourceModule" value="mountainBase"/>
                <property name="frequency" value="0.2"/>
                <property name="power" value="1"/>
            </module>
            <module name="mountainScaled" type="ScaleBiasOutput">
                <property name="sourceModule" value="mountainWavy"/>
                <property name="scale" value="100"/>
                <property name="bias" value="75"/>
            </module>

            <module name="controllerBase" type="FastNoise" seed_additive="3" no_seed="true">
                <property name="frequency" value="0.3"/>
            </module>
            <module name="controllerClamped" type="ClampOutput">
                <property name="sourceModule" value="controllerBase"/>
                <property name="bounds" value="-1.0, 1.0"/>
            </module>

            <module name="worldOutput" type="Blend">
                <property name="sourceModule1" value="mountainScaled"/>
                <property name="sourceModule2" value="landScaled"/>
                <property name="controlModule" value="controllerClamped"/>
            </module>

            <output module="worldOutput"/>

        </terrain_generator>
    </terrain_generators>
```

This is generated terrain in RWG-Previewer

![](/image/BasicExample.png)

