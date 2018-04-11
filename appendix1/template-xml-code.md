# Template XML Code

Following code is template for each module.
You can use those replacing each attributes as you like.
Commented out modules and property isn't working correctly.

```xml
<!--
     **************************************************
                         Base Module
     **************************************************
-->
    <module name="" type="FastNoise" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="lacunarity" value="FLOAT"/>
    <!--<property name="noiseQuality" value="INT 0-2"/>-->
        <property name="octaveCount" value="INT 1-29"/>
        <property name="persistence" value="FLOAT"/>
    </module>

    <module name="" type="FastBillow" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="lacunarity" value="FLOAT"/>
    <!--<property name="noiseQuality" value="INT 0-2"/>
        <property name="noise_quality" value="INT 0-2"/>-->
        <property name="octaveCount" value="INT 1-29"/>
        <property name="persistence" value="FLOAT"/>
    </module>

<!--<module name="" type="FastNoise" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="lacunarity" value="FLOAT"/>
        <property name="noiseQuality" value="INT 0-2"/>
        <property name="octaveCount" value="INT 1-29"/>
        <property name="persistence" value="FLOAT"/>
    </module>-->

    <module name="" type="Billow" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="lacunarity" value="FLOAT"/>
    <!--<property name="noiseQuality" value="INT 0-2"/>
        <property name="noise_quality" value="INT 0-2"/>-->
        <property name="octaveCount" value="INT 1-29"/>
        <property name="persistence" value="FLOAT"/>
    </module>

    <module name="" type="FastRidgedMultifractal" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="lacunarity" value="FLOAT"/>
    <!--<property name="noiseQuality" value="INT 0-2"/>-->
        <property name="octaveCount" value="INT 1-29"/>
    </module>

    <module name="" type="RidgedMultifractal" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="lacunarity" value="FLOAT"/>
    <!--<property name="noiseQuality" value="INT 0-2"/>
        <property name="noise_quality" value="INT 0-2"/>-->
        <property name="octaveCount" value="INT 1-29"/>
    </module>

    <module name="" type="Checkerboard"/>

    <module name="" type="Constant">
        <property name="constant" value="FLOAT"/>
    </module>

    <module name="" type="Cylinders">
        <property name="frequency" value="FLOAT"/>
    </module>

    <module name="" type="Spheres">
        <property name="frequency" value="FLOAT"/>
    </module>

    <module name="" type="Voronoi" seed_additive="INT" no_seed="BOOL">
        <property name="frequency" value="FLOAT"/>
        <property name="displacement" value="FLOAT"/>
        <property name="distanceEnabled" value="BOOL"/>
    </module>

<!--
     **************************************************
                 Modification Module
     **************************************************
-->

    <module name="" type="ScaleInput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="x" value="FLOAT"/>
        <property name="y" value="FLOAT"/>
        <property name="z" value="FLOAT"/>
    </module>

    <module name="" type="ScaleOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="scale" value="FLOAT"/>
    </module>

    <module name="" type="TranslateInput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="x" value="FLOAT"/>
        <property name="y" value="FLOAT"/>
        <property name="z" value="FLOAT"/>
    </module>

    <module name="" type="BiasOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="bias" value="FLOAT"/>
    </module>

    <module name="" type="RotateInput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="xAngle" value="INT"/>
        <property name="yAngle" value="INT"/>
        <property name="zAngle" value="INT"/>
    </module>

    <module name="" type="ScaleBiasOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="scale" value="FLOAT"/>
        <property name="bias" value="FLOAT"/>
    </module>

    <module name="" type="AbsoluteOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
    </module>

    <module name="" type="InvertInput">
        <property name="sourceModule" value="MODULE_NAME"/>
    </module>

    <module name="" type="InvertOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
    </module>

    <module name="" type="ClampOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="bounds" value="DOUBLE, DOUBLE"/>
    </module>

    <module name="" type="FastTurbulence" seed_additive="INT" no_seed="BOOL">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="frequency" value="FLOAT"/>
        <property name="power" value="FLOAT"/>
        <property name="roughness" value="INT 1-29"/>
    </module>

    <module name="" type="Turbulence">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="frequency" value="FLOAT"/>
        <property name="power" value="FLOAT"/>
        <property name="roughness" value="INT 1-29"/>
    </module>

    <module name="" type="DisplaceInput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="xDisplaceModule" value="MODULE_NAME"/>
        <property name="yDisplaceModule" value="MODULE_NAME"/>
        <property name="zDisplaceModule" value="MODULE_NAME"/>
    </module>

    <module name="" type="ExponentialOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="exponent" value="FLOAT"/>
    </module>

    <module name="" type="Terrace">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="invertTerraces" value="BOOL"/>
    <!--<property name="controlPoints" value="2.0, 23.0, 44.0, 65.0, 86.0, 107.0"/>-->
        <!-- 2 or more controlPoints -->
    </module>

    <module name="" type="CurveOutput">
        <property name="sourceModule" value="MODULE_NAME"/>
        <property name="source_module1" value="MODULE_NAME"/><!-- !must match with sourceModule! -->
        <property name="controlPoints" value="in1,out1;....;inX,outX"/>
        <!-- 4 or more controlPoints -->
    </module>

<!--
     **************************************************
                      Mixture Module
     **************************************************
-->
    <module name="" type="Add">
        <property name="sourceModule1" value="MODULE_NAME"/>
        <property name="sourceModule2" value="MODULE_NAME"/>
    </module>

    <module name="" type="Blend">
        <property name="sourceModule1" value="MODULE_NAME"/>
        <property name="sourceModule2" value="MODULE_NAME"/>
        <property name="controlModule" value="MODULE_NAME"/>
    </module>

    <module name="" type="Select">
        <property name="sourceModule1" value="MODULE_NAME"/>
        <property name="sourceModule2" value="MODULE_NAME"/>
        <property name="controlModule" value="MODULE_NAME"/>
        <property name="bounds" value="DOUBLE, DOUBLE"/>
        <property name="edgeFalloff" value="FLOAT"/>
    </module>

    <module name="" type="LargerOutput">
        <property name="sourceModule1" value="MODULE_NAME"/>
        <property name="sourceModule2" value="MODULE_NAME"/>
    </module>

    <module name="" type="SmallerOutput">
        <property name="sourceModule1" value="MODULE_NAME"/>
        <property name="sourceModule2" value="MODULE_NAME"/>
    </module>

    <module name="" type="Multiply">
        <property name="sourceModule1" value="MODULE_NAME"/>
        <property name="sourceModule2" value="MODULE_NAME"/>
    </module>

    <module name="" type="Power">
        <property name="baseModule" value="MODULE_NAME"/>
        <property name="powerModule" value="MODULE_NAME"/>
    </module>
```
