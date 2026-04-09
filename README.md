# Unreal Shader Compiler Project

This is a series of mods and unreal projects to fix unreal shader compilation stuttering.

Scroll to the bottom if you are just interested in the ready to use Mods!

At its core, this is a set of unreal blueprints and assets that can be loaded as a mod via ue4ss ( see compiled mods list ) , or if the mod is not on the list the user can make one via the unreal project itself for each version of the engine, or incorporated into the game itself by a developer. 

It allows users to compile shaders for materials and Niagara effects in (almost every , pending ue4ss support ) packaged unreal game, or natively in their own developed games (ue4ss not required).

There are 6 parts to this project. The main blueprint, the customized forEachLoop , the MeshAndFx (mesh, skeleton, niagara system), the loading widget, the complete widget, and the VR loading screen texture.

<img width="649" height="213" alt="content" src="https://github.com/user-attachments/assets/01403046-ad0b-4977-84dd-23d3ca362652" />

The main blueprint is shown here ( Unreal 4.26 and 4.27 ) : 

<img width="7720" height="1240" alt="ShaderGraph" src="https://github.com/user-attachments/assets/6bd356a9-b54b-4ba8-825d-2f899450e62e" />
it waits for user input, then shows a UI widget or a VR loading screen. It gathers all materials and loads them one at a time onto a blank built in engine mesh and skeleton. It then moves onto Niagara Effects. It uses a slightly customized for each loop (ForeachLoopWithDelay) that takes a float and has a bool , so that it can wait for each load to be complete before moving onto the next one. 

<br>

<br>



<details>
<summary>
  How to use this to make shader mods / setting up the project files in unreal : </summary>

You must find out two things to make a shader mod: the version of unreal the game was built on and the name of the folder that contains the content folder

Lets use SystemShock as a example: 

1: First browse to the game you want to generate shaders. If you hover over the exe (either the bootstrap launcher or the binary itself, see picture below) you will see its version (some games need you to look harder, but most will show it here)  : 

<img width="1390" height="240" alt="hoverr" src="https://github.com/user-attachments/assets/d930551e-2c2d-4d59-9542-f9c9d20346a8" />

in this case, system shock is using unreal 4.27

2 : Download and instal the same unreal version from the epic games launcher

3 : Download the project zip here for the engine version that matches it, in this case 4.27

4 : Install the C++ and unreal build tools from visual studio installer . (there are lots of tutorials on how to setup unreal to make packaged builds ) you can create a blank project and package it for windows to see if your system is ready to build. 

5 : Download RENOM **https://github.com/UnrealisticDev/Renom**  to rename the downloaded project to the Exact same name as the one that contains the content folder of the game you are modding. In the example this will be SystemShock , you can see the stucture here, it "FOLDERNAME" > Content and it will contain the Paks folder 

6 : use renom , place it somewhere, use CMD to CD to it, and use the command renom wizard 
it will walk you through renaming. you will give it a source folder, unreal427 in this case, and a new name , SystemShock in this case . Open this unreal project after renaming.

<img width="706" height="172" alt="containspakfolder" src="https://github.com/user-attachments/assets/45356d8d-53e2-420e-a3ef-414c93abef40" />

7 : Package the build for windows ,  the folder name does not matter here.

8 : once built , navagate to the paks folder of the packaged build. Rename the pak file pakchunk32-WindowsNoEditor.pak to ShaderCompilation.pak

9 : Create a folder called LogicMopds in SystemShock > Content > Paks 

10 : Place the renamed ShaderCompilation.pak in the Logicmods folder: 

<img width="795" height="129" alt="logic" src="https://github.com/user-attachments/assets/234af834-a020-417f-9f64-e10cba82c0c9" />

11 : Download and install UE4SS for system shock. i use the Experimental version as its installation is cleaner.

12 : You must set the version in UE4SS-settings.ini , in the ue4ss folder you just installed  :

<img width="1193" height="399" alt="version string" src="https://github.com/user-attachments/assets/44c0ff0e-3573-49e1-8685-1e98e8d9e6df" />


for system shock it is as follows :


[EngineVersionOverride]

MajorVersion = 4

MinorVersion = 27



11 : you can run the game and press f8 , the shader compliation screen will show up


</details>

<br>
<br>
<br>

**COMPILED MODS :**

<details>

<summary>System Shock 2023</summary>

1 : 
Download UE4SS and install it into the system shock binaries folder ( where the exe is )

<img width="711" height="1339" alt="systemshocklocation" src="https://github.com/user-attachments/assets/cfc2494d-ebd6-4c8d-bbb7-50be9f2bf2f7" />


i used the newest experimental version at time of writing, it has a dll and a folder as shown in the picture above **https://github.com/UE4SS-RE/RE-UE4SS/releases**


2 :You must set the version in UE4SS-settings.ini , in the ue4ss folder you just installed  :

<img width="1193" height="399" alt="version string" src="https://github.com/user-attachments/assets/44c0ff0e-3573-49e1-8685-1e98e8d9e6df" />


for system shock it is as follows :


[EngineVersionOverride]

MajorVersion = 4

MinorVersion = 27


3 : 
Unzip the SystemShock.zip into the main folder of the game, the folder stucture should end up like so :
System Shock Remake\SystemShock\Content\Paks\LogicMods\ShaderCompilation.pak

<img width="798" height="122" alt="logicmods" src="https://github.com/user-attachments/assets/7182cfd0-e413-447c-9242-0007a22d59c5" />


4 : 
while in game or the main menu you can press f8 to engage the shader compilation. the widget will take up the whole screen until compilation is complete. Alternatively there is also a button to engage the shader compiler in the ue4ss GUI console 



shader compilation is complete. you can now play the game

5:
If you are using Dx12 launch command for system shock 2023 (which makes the game run great with UEVR) , encountering the railgun muzzle flash (more than once) will crash the game. This is not the fault of the mod but the effect itself is bad in Dx12 , i have provided a blank niagara effect as a in a pak file to stop this from happening . (SystemShockDx12CrashFix.zip > SystemShock-Windows_p.pak) . this file goes with the other pak files for the game, in "System Shock Remake\SystemShock\Content\Paks"

<img width="747" height="146" alt="patch" src="https://github.com/user-attachments/assets/55967661-b917-442d-b593-736fcf108b75" />
</details>

<details>

<summary>Tetris Effect</summary>


coming very soon

</details>

<details>

<summary>The Walking Dead</summary>


coming very soon

</details>

<details>

<summary>Psychonaughts2</summary>


coming very soon

</details>

<details>

<summary>Sprawl</summary>


coming very soon

</details>

<details>

<summary>Stray</summary>


tetris

</details>


Liscense : Feel free to use this for whatever project, no strings attached. Learn from it, the less shader stutter in the world the better! 
