# G4-Super-3D-Targeting-System

# Screenshot

<img width="959" alt="G4GOD" src="https://user-images.githubusercontent.com/1403194/156693680-37d2f916-1555-4421-9e2a-129d865f1d27.png">

This is the 3D targeting system's demo project for Godot 4 game engine.

This tool is based on [3D-Targeting-Syetem-Ultimate](https://github.com/kreaninw/3D-Targeting-Syetem-Ultimate) for Godot 3.

# Usage
1. Open the demo project in Godot game engine. There are 3 scripts: **player.vs**, **Look.vs**, and **Camera.vs**. Each of them can be used independently.
- **player.vs**
  - is intended for demonstration purposes. You don't actually need this in your project.
- **Look.vs**
  - is the main logic for targeting.
- **Camera.vs**
  - is also intended for demonstration purposes. However, you can make use of it in any way you like. It's a basic camera's movement by mouse input like you see in a lot of FPS shooter games.

2. After getting familiar with the demo project, attach the script to your node in your project, then set all the options in the inspector tab. The options in each script are as follows:
- **player.vs**: 
  - **Demo Mode**: this will turn on or off the input for player control in the demo, allowing you to implement your player control.
  - **Camera Lock Keys**: you can specify as many keys as you want here. It will allow you to lock the camera to the target (disable mouse input).
  - **Camera Status Text**: message to show when the camera locked to the target.
  - **Camera Status**: disable it if you don't need to show your camera status.
  - **Camera Script**: disable it if you don't need to control the camera targeting script.
- **Look.vs**:
  - **Mode**: there are 5 targeting modes like the original system.
  - **Mode Keys**: you can set the keys to toggle between modes.
  - **Mode Display**: disable it if you don't want to show a message telling which mode you're in.
  - **Action Status**: disable it if you don't want to show the target locked status at the center of your screen. It's mainly for demonstration purposes.
  - **Pick Mode**: _Random_ = randomly choose a target inside a specified target group (like the original system). _Area Random_ = randomly choose a target inside the detection area. _Area Closest_ = choose the target closest to the player inside the detection area. _Manual_ = targeting based on your logic. See comments in the code for more detail.
  - **Targeting Area Random**: this will delay the logic for the Area Random pick mode. If it's set to 1, whichever target entered the detection area first will be picked as a target, hence not really random. The default is set to 3, so at least it will randomly choose between 3 entered targets.
  - **Entered Target Group**: specify the node's group you consider to be a target.
  - **Auto Retargeting**: only relevant in the area pick modes. With this option turned on, as soon as there's a new target entered the detection area, it will automatically recalculate and pick a new target according to the selected pick mode.
  - **Targeting Area Distance**: specified your targeting area scale.
  - **Mesh Structure**: since there are ways to arrange a mesh and its collision, some people make a mesh as a parent node, some make it a child. Therefore, please choose this option accordingly. It's important in the area's pick modes since the engine will only detect body_entered with the collision nodes.
  - **Target Manual Demo**: this is for demonstration purposes where you can press Z, X, C, V, B, N, M, G, H, J, K, L to choose between 12 targets in the scene manually. You can disable it in your project.
  - **Target Material** and **Change Target Material**: are for demonstration purposes. It's a good thing to have when debugging since you can easily see which target you are targeting.
  - **Targeting Speed**: 100 means 100%, 200 means 200% or 2 times, and so on.
- **Camera.vs**
  - **Mouse Mode**: as the name suggested.
  - **Toggle Mouse Input**: you can turn this off or you don't need to attach this script.

3. Don't forget to add required node as the name suggested in the inspector tab.

# Known Issues
1. Due to [godotengine/godot issue #44152](https://github.com/godotengine/godot/issues/44152), it's currently impossible to categorize or group the script options. Therefore, the script options will appear randomly in order.
2. Due to [godotengine/godot issue #58158](https://github.com/godotengine/godot/issues/58158), the variables in Visual Script are always exported. Therefore, your inspector tab will be spawned with many unrelated items. However, don't worry as they has no effect at all unless you export them in the script.
3. At the time of this writing (Godot 4 alpha 3), the variables won't be sorted by their name like it used to be. However, the fix has been merged [godotengine/godot PR ##58510](https://github.com/godotengine/godot/pull/58510). Therefore, you can wait for alpha 4 or [build the engine from source](https://docs.godotengine.org/en/latest/development/compiling/index.html).
4. Due to [godotengine/godot issue #58035](https://github.com/godotengine/godot/issues/58035), if you want to edit the script, it will be hard! As the variables from members' window doesn't get its type updated correctly in the Visual Script canvas. Let's hope it will be fixed soon.
5. Due to [godotengine/godot issue #54065](https://github.com/godotengine/godot/issues/54065), you need to setup a script at the main scene to make your project fullscreen. I already added the script into this repository.

For all Visual Script's regression from Godot 3, you can see a full list [here](https://github.com/godotengine/godot/issues?q=is%3Aopen+is%3Aissue+label%3Atopic%3Avisualscript+label%3Aregression).

All feedbacks are welcome.
