# Unreal Shader Compiler Project
A ue4ss blueprint mod that allows users to compile shaders for materials and Niagara effects in (almost every ) packaged unreal game, and how a unreal developer could easily implement it.


Currently under construction , 1 game has mod files posted, framework and more mods for more titles coming soon. 




System Shock 2023 setup :

1 : Download UE4SS and install it into the system shock binaries folder ( where the exe is )

i used the newest experimental version at time of writing **https://github.com/UE4SS-RE/RE-UE4SS/releases/download/experimental-latest/UE4SS_v3.0.1-603-g07f4b8f.zip**

You must set the version in UE4SS-settings.ini , for system shock it is as follows :

[EngineVersionOverride]

MajorVersion = 4

MinorVersion = 27

2 : Unzip the SystemShock.zip into the main folder of the game, the folder stucture should end up like so :
System Shock Remake\SystemShock\Content\Paks\LogicMods\ShaderCompliation.pak

3 : while in game ( not the pause menu for now ) you can press f8 , or left bumper + right bumper + dpad down on a gamepad , to engage the shader compilation. the widget will take up the whole screen until complation is complete. (there is also a button to engage the shader compiler in the ue4ss GUI console )

shader complation is complete. you can now play the game
