# Prerendered Background Tutorial

## Blender
1. Create level
2. Add cameras and keep note of the following properties for each camera. It's recommended to use whole numbers for location and rotation.
   1. FOV
   2. Screen ratio
   3. Location
   4. Rotation
3. Add a cone mesh to the exact same location and rotation of each camera
4. Export as FBX

## Unreal Engine
1. Import the FBX
2. Set all locations to origin (0,0,0). This should layout the level as seen in Blender.
3. Open the Player Character Blueprint and search for `tag`. Enter `Player`.
4. Open the project settings and search for `custom stencil`. Selected `enable with stencil`
5. Open the player and set the `custom stencil` to `1`
6. Open objects that would appear in front of the player and for capturing shadow. Set their `custom stencil` to `2`
7. Set the yaw controls to true in details
8. Create Game Mode `BP_GameModeTutorial`
9. Create Actor Blueprint `BP_Camera`
10. Create Actor Blueprint `BP_CameraSwitch`
11. Create Blueprint interface `BPI_SwitchCamera` and set the input as `BP_Camera`
12. Add `BPI_SwitchCamera` to game mode by accessing the Class Settings, then adding an implemented interface
13. Set up all blueprint nodes
14. In GameMode create functions SetPostProcessMaterial and EnablePostProcessMaterial
15. Create the post process material `M_Postprocess` and set the `Material Domain` to `post process` and `Blendable Location` to `Replacing the tonemapper`
16. Select all objects in level and disable `cast shadow`


### Camera conversion from Blender to Unreal Engine
#### Location
Blender x,y,z = UE x,-y,z


### Rotation
blender 90,0,0 / UI 0,0,-90