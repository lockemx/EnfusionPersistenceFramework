# Game mode setup
The following setup can be seen implemented in the unit test project as an example. Open the [`TestWorld`](https://enfusionengine.com/api/redirect?to=enfusion://WorldEditor/Worlds/TestWorld/TestWorld.ent) to have a look.

1. Add the [`EPF_PersistenceManagerComponent`](https://enfusionengine.com/api/redirect?to=enfusion://ScriptEditor/Scripts/Game/EPF_PersistenceManagerComponent.c;26) to your [`SCR_BaseGameMode`](https://enfusionengine.com/api/redirect?to=enfusion://ScriptEditor/Scripts/Game/GameMode/SCR_BaseGameMode.c;105) inherited game-mode entity. If your game mode does not inherit from it, you will to reimplement the functionality of the component and hook up the events it uses, so the persistence manager is setup correctly.
2. Go into the component attributes and add a `Connection Info` instance to something like [`EDF_JsonFileDbConnectionInfo`](https://enfusionengine.com/api/redirect?to=enfusion://ScriptEditor/Scripts/Game/Drivers/LocalFile/EDF_JsonFileDbDriver.c;2) and enter a `Database Name` like `MyGamemodeDatabase`. For more info on the available database types please [read this](https://github.com/Arkensor/EnfusionDatabaseFramework/blob/armareforger/docs/drivers/index.md).
3. Decide what kind of respawn process you need. Until Arma Reforger version 0.9.9 the framework does not offer any finished respawn system which integrates into the vanilla loadout selection out of the box. Instead either connect the current vanilla system yourself or use the system used in the test project. It spawns players with exactly one loadout configured through the `Default Prefab` attribute on the [`EPF_RespawnSytemComponent`](https://enfusionengine.com/api/redirect?to=enfusion://ScriptEditor/Scripts/Game/RespawnSystem/EPF_RespawnSytemComponent.c;9) which is also added to the game mode alongside the [`EPF_RespawnHandlerComponent`](https://enfusionengine.com/api/redirect?to=enfusion://ScriptEditor/Scripts/Game/RespawnSystem/EPF_RespawnHandlerComponent.c;6). Fruther re-useable classes for the (re-)spawn system and a configurable integration into the vanilla (re)-spawn system will be added in future versions.
4. [Setup any entity prefabs](persistence-component.md) that are not already configured through a common vanilla base class (`Item_Base.et`, `Weapon_Base.et`, `XXX_Base.et`, etc).
5. Add save-data classes for your [custom components](custom-component.md) and [scripted states](scripted-states.md).
6. Profit.