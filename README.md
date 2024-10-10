

# UE5.3_PCG_Environment

> This is an environment preset tool using the Procedural Content Generation plugin built-in UE5.3, using the blueprint to generate and customize environment.

## 1. Getting started

### 1.1. Before adding this tool to your project

- #### Check your Unreal Engine version


It should be version 5.3.X, which may not function in a higher or lower version.



- #### Install the PCG plugin


Go to the Edit > Plugins > search "PCG" in the bar and install.

Procedural Content Generation Framework and other two related plugins

This install will restart your project.

If you copy the tool to your project before install the plugin, it will find file lost.

### 1.2. Quick start from GitHub

Download the project and add it to the content folder of your project.

> Then follow the same way start from the UE project.



### 1.3. Quick start from the UE project

1. Open the UE project and you will find the `PCG_Env` folder in the content folder.

2. Open the `PCG_Building` folder.

3. Drag the Blueprint such as `BP_PCG_Building` to the game scene, there should be a building generated at the point of the Blueprint's actor. If nothing happens, Please go chapter`3. issue fixing`.

4. Click the actor you just drag in the `Outliner` panel, you will see the layout in the `details`.

5. First thing in the details panel is a list that contains all elements in that actor, you will see the actor structure like that:

```
└── BP_PCG_Building
    ├── DefaultSceneRoot
    |   └──XXXXX(generated instances)
    └── PCG
```

6. Click the PCG node, you will see the tabs `PCG` , there are three buttons: `Generate` `Cleanup` `Clean PCG Link`.

7. Use `Generate` and `Cleanup` to fix the issue that the actor not automatically change when you edit it or finding unknown instance under the `DefaultSceneRoot` node. 

8. Click the `Clean PCG Link` to set new PCG graph file, you can also change the Graph in `Instance` tab, finding new PCG preset file to generate new style. Go to 2.2 for more detail.

## 2. Customization

### 2.1. Understand the file

you will see `PCG_Env` folder and there are subfolders inside.

#### 2.1.1. Subfolders

`PCG_Building` is where the preset blueprint files generate the actors of the PCG buildings.

- `PCG_BuildingStyle` contain building style PCG graph files.
- `Sub_PCG_Part` contain the sub PCG script files. These files make up the PCG graph files.

`PCG_Building_Assets` is the folder where the using assets related, there are some asset packs inside.

`PCG_Pipe` folder is where the the preset PCG files generate the actors of the pipes.

### 2.2. Add new graph to the Actor

Finding new style graph files in folder `PCG_Env` >> `PCG_Building` >> `PCG_BuildingStyle`

#### 2.2.1. Note the file extensions

Style graph files have different suffix match different blueprint actor:

Blueprint - PCG Graph

`BP_PCG_Building` - `PCG_Building_X`

`BP_PCG_BuildingAndSidewalk` - `PCG_Building_X_S_XX`

`BP_PCG_BuildingAndSidewalk_Mix` - `PCG_Building_XXX_S_XX`

#### 2.3. customize the layer

Drag a `BP_PCG_BuildingAndSidewalk_Mix` file in to the level, you will find parameter after click the details list `BP_PCG_BuildingAndSidewalk_Mix (self)`.

```
└── BP_PCG_BuildingAndSidewalk_Mix (self)
    ├── DefaultSceneRoot
    |   ├──SideWalk_Box_Layout
    |   ├──Building_Part_Layout_01
    |   ├──Building_Part_Layout_02
    |   ├──Spline
    |   └──XXXXX(generated instances)
    └── PCG
```

under the list after clicking `BP_PCG_BuildingAndSidewalk_Mix (self)`:

```
├── Transform [Building's location and rotation control]
|   ├──Location
|   ├──Rotation
|   └──Scale
├── PCG Building outline [control the width and Length of the building]
|   ├──Width
|   └──Length
├── PCG Building Roof
|   └──Roof Decorative Height [adjust the height of the roof surface]
├── PCG Building Style 03
|   └──Number Of Layers of Style 03 [adjust the number of layer of the heighest walls]
├── PCG Building Style 02
|   └──Number Of Layers of Style 02 [adjust the number of layer of the middle walls]
├── PCG Building Style 01(Base)
|   └──Number Of Layers of Style 01 [adjust the number of layer of the base walls]
├── PCG Building Sidewalk
|   └──Side Walk Adjust [adjust the height of the sidewalk to fit the ground]
...
```

#### Replace the meshes in the PCG generation

if you go to the PCG Graph file in the `PCG` tap, you will find a window open that looks like a blueprint. Go to the right side of those nodes, there is a comment zone called `meshes`, here you can find all the meshes used in the PCG generation, you can replace them with the mesh you want. you can choose the node and press `E` on your keyboard to enable and stop the node functioning. This will help you find the place of this meshes position in the generation.

#### Change items' position in the PCG generation

in the `meshes` comment zone, there is a transform point on the left side of each mesh node. clicking it and you will find the adjusted panel of the meshes. it changes the point's position data. To better understand, there might be multiple points pathing the same nodes, the nodes give each node a different transform randomly by your order. but if you tap the same number to both the max and min blank, it will make a certain transformation as you wish.

#### Edit the items that you want

Zoom out to see all comment zones, you will find many zones across the `meshes` horizontally, which means different groups of the PCG generation. such as the fire ladder and different styles of layers of the building.

## 3. Guide

> how to use the PCG plugin for more creation

#### What is it

The **Procedural Content Generation Framework (PCG)** is a toolset for creating your own procedural content and tools inside Unreal Engine. PCG provides technical artists, designers, and programmers with the ability to build fast, iterative tools and content of any complexity, ranging from Asset utilities, such as buildings or biome generation, up to entire worlds.

For more official document:

https://dev.epicgames.com/documentation/en-us/unreal-engine/pcg-development-guides?application_version=5.3

#### How to use it

Left click the folder you want to place the PCG graph, chose the PCG tab and go to create a new PCG graph.

In our tool, we using buleprint actor to set the PCG parameter.

## 4. Issue fixing

Not generate when drag the blueprint file in.

Lost levels of the building.

Lost the roof of the building.

Not able to see the node data after press "a".







