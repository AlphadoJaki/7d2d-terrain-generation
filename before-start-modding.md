# Before start modding

In previous chapter, we saw how terrain is generated using 3 class modules.  
In next chapter, we will see brief description of typical modules, and finally generate terrain.  
But we need ready for comfortable terrain generation.  
In this chapter, we describe important tips and how to use _**RWG-Previewer**_.  
If you are used to modding and _RWG-Previewer_, you can skip this chapter.

## Take a nice editor for XML

Modifying terrain generation is completely done by XML coding.  
So highly recommended to use the editor that can do _highlight_ and _syntax check_.  
For Windows user, **notepad++** with **XML tools** plugin is good to start with.  
For Mac user, **XCode** is not bad to start with.  
Of course, _vimmer_ and _emacser_ can be with your favorite one. =P

## Disable hub generation

Hub generation is the most time consuming part of RWG.  
No reason to wait hub generation, if you want see only how terrain is generated.  
To disable hub generation, do following 5 steps.  

1. Find ***cell\_rule*** named **default** in rwgmixer.xml
1. Comment-out existing ***hub\_rule***, then insert a new rule, **empty**.
```xml
		<!--<hub_rule name="townSmall" prob="0.3"/>
			<hub_rule name="townLarge" prob="0.3"/>
			<hub_rule name="citySmall" prob="0.1"/>
			<hub_rule name="cityLarge" prob="0.1"/>
			<hub_rule name="rural" prob="0.3"/>-->
			<hub_rule name="empty" prob="1"/>
```
1. Go downward, and find the first ***hub\_rule*** named ruralSmall.
1. Insert new line between ***hub\_rule*** and ***hub\_rules***
1. Insert a new hub\_rule **empty**
```xml
		<hub_rule name="empty">
			<hub_type value="rural"/>
			<width value="250, 250" />
			<height value="250, 250" />
			<path_material value="asphalt" />
			<path_radius value="10" />

			<prefab_rule name="default"/>

			<street_gen level="4" length_multiplier="4">
				<axiom value="+"/>
				<rule char="X" replace_with="+"/>
				<alt_commands chars="X"/>
			</street_gen>
		</hub_rule>
```

That's all!
To enable hub-generation, comment out empty, and un-comment other hub\_rule-s.

## Be used to _RWG-Previewer_

RWG-Previewer is accessible by _**Editing Tools**_ on title menu.  
It is convenient for following reasons when we are messing with RWG.

1. Faster than actual world generation
1. Able to overview entire world
1. No need to reboot 7D2D for refreshing XML

After filling the seed and generation size, click circled arrow to generate.

### Operation guide

#### Mouse \(with Left-click\)

| Operation | Move |
| --- | --- |
| Go Up/Down | Go Up/Down |
| Go Left/Right | Go West/East |

#### Mouse \(with Right-click\)

| Operation | Move |
| --- | --- |
| Go Up/Down | Look Up/Down |
| Go Left/Right | Look Left/Right |

#### Keyboard

| Operation | Move |
| --- | --- |
| WASD | Move |
| Space | Go Upward |
| Ctrl | Go Downward |
| Scroll | Change Speed |
| Tab | Change Mode |
