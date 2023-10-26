# Core.IO Continued
Harmony implementation of IO entities placed in RustEdit for those who don't want to (or can't) use Oxide.Ext.RustEdit by k1lly0u.

This is a continuation of old bmgjet's Harmony mod to keep it compatible with modern Rust servers, and also implement a bunch of fixes and extra features. *As of 1.0.3, this fork also implements two new features:*
* **HBHF Sensors support**: now sensors output passthrough energy as expected. Energy output is no longer tied to current amount of detected entities, and instead provides a static amount of energy that is enough to power up anything in IO chain. This behaviour does not affect HBHF sensors deployed by a player.
* **Autoturret Interference immunity**: autoturrets placed through the editor are no longer affected by interference limitations. If your custom map has many autoturrets placed close to each other, they are no longer risking to become "jammed" regardless of your current server configuration. Player deployed autoturrets are still behaving as usual. 

# Download
Latest version is available in [Releases](https://github.com/WheatleyMF/Core.IO.Continued/releases). Please make sure to use latest version, previous versions may have some bugs. 

## Chat Commands
All commands listed here are admin-only. 

`/showiowires`   -   Will render simple ddraw lines showing connection between all custom IO entities<br>
`/reloaddoors`   -   Will respawn and repair all custom map doors that are missing on the map.<br>

## Permissions 
As an admin, you are able to pick up IO entities, authorize in turret, edit their contents and adjust the wiring. To activate this "edit mode", you should be in god mode and have noclip enabled. Players are not able to edit these entities. 

## Autoturrets
Custom autoturrets support all options you can select in RustEdit - `Peacekeeper Mode`, `Unlimited Ammo` and any weapon. Also they won't be affected by turret interference limitations added in October 2023 update. 

There are two ammo behaviour modes for autoturrets placed through the map editor:<br>
1. **Limited Ammo**: if you didn't check "Unlimited Ammo" in autoturret's config, autoturrets will spawn with a single clip of ammo loaded. Once they run out of ammo, new clip will be automatically added in 60 seconds.
2. **Unlimited Ammo**: autoturret's ammo will regenerate each tick and will pause attacking only when it has to reload.   

If you are an admin and have god & noclip modes enabled then autoturrets won't shoot you, but they will keep aiming at you.

## Custom Elevators
Elevators are fully supported and work as expected. Elevators placed through the editor will be re-generated on each server startup, and then destroyed on server shut down. If your server crashes and plugin doesn't clean up elevators, they will be removed on next server launch and regenerate. There's a chance that it won't work as expected, so do a proper server restart to ensure they are working correctly after a crash. 
  
## Installing
Copy `Core.IO.Continued.dll` to your `../<server root folder>/HarmonyMods` folder.

## Reloading
Please, do not reload this mod while server is running – otherwise you are risking to corrupt map saving process and make players lose recent progress. If you want to apply an update, just put the latest version in HarmonyMods folder and then restart the server. I am not sure what is causing this but I'm hoping to resolve this in future versions.
