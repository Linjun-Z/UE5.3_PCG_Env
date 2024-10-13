

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

### 1.4. Assets pack list

|               Asset Name               | No.  | Style                                       | Index                                                        | Publisher    | Source                                                       | GitHub       |
| :------------------------------------: | ---- | ------------------------------------------- | ------------------------------------------------------------ | ------------ | ------------------------------------------------------------ | ------------ |
|         City Sample Buildings          | \    | PCG_Building_XXX_S_XX                       | /All/Game/CitySampleBuildings                                | Epic         | https://www.unrealengine.com/marketplace/en-US/learn/city-sample-buildings | Not included |
|          Modular Building Set          | \    | PCG_Building_X & PCG_Building_X_S_XX        | /All/Game/CitySampleBuildings/PCG_Env/PCG_Building_Assets/ModularBuildingSet | PurePolygons | https://www.unrealengine.com/marketplace/en-US/product/modular-building-set | Not included |
|            Bridge 3D Assets            | \    | PCG_Building_X_S_XX & PCG_Building_XXX_S_XX | /All/Game/Megascans                                          | Quixel       | Build-in Plugin                                              | Not included |
|          Bike_Stand_uhcgehnfa          | 0    | ^                                           | /All/Game/Megascans/3D_Assets/Bike_Stand_uhcgehnfa           | ^            | ^                                                            | Not included |
|         Fire_Hydrant_uiohdaofa         | 1    | ^                                           | /All/Game/Megascans/3D_Assets/Fire_Hydrant_uiohdaofa         | ^            | ^                                                            | Not included |
|         Fire_Hydrant_uiuhbegfa         | 2    | ^                                           | /All/Game/Megascans/3D_Assets/Fire_Hydrant_uiuhbegfa         | ^            | ^                                                            | Not included |
|           Mailbox_ujijbfhba            | 3    | ^                                           | /All/Game/Megascans/3D_Assets/Mailbox_ujijbfhba              | ^            | ^                                                            | Not included |
|        Metal_Bollard_uiohdggfa         | 4    | ^                                           | /All/Game/Megascans/3D_Assets/Metal_Bollard_uiohdggfa        | ^            | ^                                                            | Not included |
|        Metal_Bollard_uiyhfisga         | 5    | ^                                           | /All/Game/Megascans/3D_Assets/Metal_Bollard_uiyhfisga        | ^            | ^                                                            | Not included |
|        Metal_Bollard_uiyjbcega         | 6    | ^                                           | /All/Game/Megascans/3D_Assets/Metal_Bollard_uiyjbcega        | ^            | ^                                                            | Not included |
|     Metal_Manhole_Cover_wdlmdgebw      | 7    | ^                                           | /All/Game/Megascans/3D_Assets/Metal_Manhole_Cover_wdlmdgebw  | ^            | ^                                                            | Not included |
|  Modular_Building_Roof_Kit_wdhkcccdw   | 8    | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Building_Roof_Kit_wdhkcccdw | ^            | ^                                                            | Not included |
| Modular_Building_Roof_Window_wdetbiodw | 9    | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Building_Roof_Window_wdetbiodw | ^            | ^                                                            | Not included |
| Modular_Concrete_Median_Kit_vdqoedxdw  | 10   | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Concrete_Median_Kit_vdqoedxdw | ^            | ^                                                            | Not included |
|       Modular_Curb_Kit_vckoejddw       | 11   | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Curb_Kit_vckoejddw     | ^            | ^                                                            | Not included |
|   Modular_Plastic_Pipe_Kit_vghoacydw   | 12   | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Plastic_Pipe_Kit_vghoacydw | ^            | ^                                                            | Not included |
|   Modular_Sidewalk_Corner_uiksdjydw    | 13   | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Sidewalk_Corner_uiksdjydw | ^            | ^                                                            | Not included |
|   Modular_Sidewalk_Corner_uiksea2dw    | 14   | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Sidewalk_Corner_uiksea2dw | ^            | ^                                                            | Not included |
|   Modular_Sidewalk_Corner_uiswcahdw    | 15   | ^                                           | /All/Game/Megascans/3D_Assets/Modular_Sidewalk_Corner_uiswcahdw | ^            | ^                                                            | Not included |
|        Parking_Meter_ujyvbgofa         | 16   | ^                                           | /All/Game/Megascans/3D_Assets/Parking_Meter_ujyvbgofa        | ^            | ^                                                            | Not included |
|          Trash_Can_uhrgdbffa           | 17   | ^                                           | /All/Game/Megascans/3D_Assets/Trash_Can_uhrgdbffa            | ^            | ^                                                            | Not included |



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

### 2.3. customize the layer

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

Go to the `BP_PCG_BuildingAndSidewalk_Mix (self) ` >> `DefaultSceneRoot` >>`SideWalk_Box_Layout`

Press `R` to use scale tool to adjust the sidewalk size. Under the list choose Box Extent to adjust the sidewalk width and length by detail. 

### 2.4. Override PCG sittings

Go to the `BP_PCG_BuildingAndSidewalk_Mix (self) ` >> `PCG` 

Under the `Instance` tab there are `Parameters Overrides` and `Settings`

In `Parameters Overrides` , you can change the size of each cell part like different height of each layer's style to fit the assets. 

> Not recommend to change that because it is already preset for current assets, unless you want to replace different size assets.

 `Settings` have a `seed` parameter, you can change that to randomly set some items. This parameter does not work in many situations and also does not often lead to the expected result, The best way is to find the node that currently controls the generation, you can identify the item's comment zone label name to find all nodes. Please go to `Frequently use nodes` to find the `PCG_RandomPointSelector` node for more detail.

### 2.5. Replace the meshes in the PCG generation

if you go to the PCG Graph file in the `PCG` tap, you will find a window open that looks like a blueprint. Go to the right side of those nodes, there is a comment zone called `Mesh Data`, here you can find node type `Static Mesh Spawner` , all the meshes used in the PCG generation are in the panel Settings >> Mesh Entries >> Index >> Descriptor >> Static Mesh, you can replace them with the mesh you want. you can choose the node and press button `E` to enable and disable the mesh node. This will help you identify meshes position in the generation.

### 2.6. Change items' position in the PCG generation

in the `Mesh Data` comment zone, there is a `transform point` node on the left side of each mesh node. clicking it and you will find the adjust panel of the meshes. it changes the point's position data. To better understand, there might be multiple points pathing the same nodes, the nodes give each node a different transform randomly by your sitting. but if you tap the same number to both the offset max and min, it will make a certain transformation as you wish, same as Rotation and Scale.

### 2.7. Edit the items that you want

Zoom out to see all comment zones, you will find many zones across the `Mesh Data` horizontally, which means different groups of the PCG generation. such as the fire ladder and different styles of layers of the building. Use the `E` button to enable and disable them.

### 2.8. How to debug

> It important to understand the data contain in a node, both input and output

Press `A` to see node data, Press `D` to debug.

> Before doing this make sure you have chose the right object in the bar, this bar is under the PCG graph file Tab, there are buttons like `save the assets` and `Graph Settings` around it. In default open, there should be [No debug object selected] show in the bar.

When there is no mesh at the node's point, change in the right panel Debug >> Scale Method, from `Relative` to `Absolute`. You will see cubes at point.

### 2.9. Frequently use nodes

#### `Point Filter`

> This node is for filter the points, you can find points with different tags, like `wall` and `corner`, you can also find different sides of the building, all square building contain `Front`,`Back`,`SideL`,`SideR`. 

```
└── Setting
    ├── Operator[It is worth mentioning that the string type can identify 
    |   |                        a part and classify the excess part as >]
    |   ├── = or !=
    |   ├── >= or <=
    |   └── > or <
    ├── Target Attribute [Only explain frequently use type]
    |   ├── Position [Generally used to remove all points above a certain height]
    |   ├── Index [Retrieving a point in data list using an integer]
    |   ├── Wall [Use string to find points that match the label]
    |   └── Floor [Retrieving a point in floor list using an integer]
    └── Using Constant Threshold
        |   ├── True [Searching by specific parameters]
        |   └── Type [Only explain frequently use type]
        |       ├── String
        |       |    └── String value [Can identify part of the name]
        |       └── Interger 32
        |            └── Int32 Value 
        |                [Integers are generally used for floor and list numbers.]
        └── False [Compare with another parameter in the data list]
            ├── True
            └── Type [same as the first one]
```

in `Target Attribute` press the `+` button and select `Position` you will see `$Position` in the bar

you can add the `.X` behind, to make it `$Position.X`. This means only the x-axis data.  Same to Y, Z and you can try all data types in the data table shown below after press `A`.

#### `PCG_RandomPointSelector`

> This node is using `Random Seed` to filter the point randomly
>
> There are two default imports, `Point Filter In` is for the point collection you want to filter. `Select Point in` is the input you want to select. select point do not need to be part of the point collection if there is no match, it will return null.
>
> There are two output, `Point Filter inside Filter` and `Point Filter outside Filter` . The set of two outputs is the `Point Filter In`.

#### `PCG_SideWallFilter`

> This node is use after filter the `Corner` from the `Wall` Type. This node need a input of all wall point to the `Point Input` input and also the `Corner` to the `Corner`  input.
>
> The logic of this node is to output the wall point by three ways. When you face the wall, the point at the right side and the left side go to the `Right` and `Left` output, the rest points in the middle go to the `Middle` output. `Conner` output the original input for more convenient use in mesh adding.
>
> This node is a supplement to the point generation defect and avoids identification errors at wall connections caused by rotation.

#### `PCG_SubLevel`

> `PCG_SubLevel` and its variants `PCG_SubRoof` and `PCG_SubLevel_Mix` is placed on each style to generate all the layers contained in that style.
>
> For example, a building consists of shops on the ground floor, offices on the middle floor, apartments on the upper floor, and rooftop eaves. Then it will be divided into four styles of floors, among which the shops on the ground floor and the rooftop eaves are only single-story, while the exterior walls of the office building and apartment in the middle will be stacked according to the number of floors to form the entire building.
>
> `PCG_SubLevel` have 5  necessary input. three of them `Wall` `Floor` `Conner` are from the node `PCG_SubWall`, which help calculate and generate the wall, different settings of layout of the building need different `PCG_SubWall` to be the copy template. Some buildings with a stepped style require multiple `PCG_SubWall` .
>
> Input `From Lower Level` need to get the `To Heigher Level` output. In some early version it need the out put from `PCG_SubLevelMaker` or directly use the out put of node `Get actor Data`. It should be a point data to be the position of the total generation.
>
> `Cell Height` is the height of the single level, used to customize for different height assets.
>
> Output `Wall` and `Corner` always link to `PCG_SideWallFilter`‘s  `Point Input`  and `Corner` .
>
> This node only generates a single floor.

#### `PCG_SubRoof`

> Basically the same as `PCG_SubLevel`, do not have `To Heigher Level` output. If it is used as an intermediate platform, please obtain `To Heigher Level`  from the upper floor below.

#### `PCG_SubLevel_Mix`

> Upgraded `PCG_SubLevel`, input the number of layer to generate Multi-layer with same style.

#### `PCG_SubWall`

> Input `Width` `Length` `Cellsize`  to generate single-layer grids, and roughly classify them.

#### `PCG_SubLevelMaker`

> In some early versions of the style, it will output the position point of each layer. It will also give all points the Floor attribute. Then copy `PCG_SubWall` to each layer position point through the `copy point` node to generate each layer. It also output the last layer's position point to next style's `PCG_SubLevel`or`PCG_SubRoof` node.



## 3. Guide

> how to use the PCG plugin for more creation

### What is it

The **Procedural Content Generation Framework (PCG)** is a toolset for creating your own procedural content and tools inside Unreal Engine. PCG provides technical artists, designers, and programmers with the ability to build fast, iterative tools and content of any complexity, ranging from Asset utilities, such as buildings or biome generation, up to entire worlds.

For more official document:

https://dev.epicgames.com/documentation/en-us/unreal-engine/pcg-development-guides?application_version=5.3

### How to use it

Left click the folder you want to place the PCG graph, chose the PCG tab and go to create a new PCG graph.

In our tool, we using buleprint actor to set the PCG parameter.

## 4. Issue fixing

### Not generate when drag the blueprint file in.

Assets may lost, please check the `Assets pack list`.

### Lost levels of the building.

Check the PCG graph and find the style comment zone. Check all the input and output data.

### Lost the roof of the building.

Finding the `PCG_SubRoof` nodes and debug. 

### Not able to see the node data after press "A".

There might be bugs to see some node's input data, please go to the output node to see the output data.







