# Overview

## Module

Terrain generator is consist of functional **modules**.  
For now, there are 33 types of modules, which can be categorized in 3 classes by its purpose.

* **Base Module**
  Generate base of terrain by itself.
* **Modification Module**
  Make change of existing module.
* **Mixture Module**
  Mix 2 existing modules into 1 module.

## Sketch of terrain generation

Following image explains rough sketch of how terrain generation is processed.  
Any modules are start with base modules.  
Then, they are passed through modification modules & mixture module.  
Finally, mixture module make them into 1 module.  
These process is repeated again and again, until final output module is made.

![](/image/Sketch.png)

