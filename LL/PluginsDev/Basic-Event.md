# Basic events
The built-in basic event system of LiteLoader saves developers the trouble of finding symbols  
To reference the built-in Api of LiteLoader, you need to add **LiteLoader.lib** to the project  
Right-click the project, select **Add->Existing Item**, then find **LiteLoader.lib** in the lib folder under the project directory, and click Add  
![1](../../../images/Basic-Event-1.png)
![2](../../../images/Basic-Event-2.png)

First you need to add these code to `pch.h` for including event system and `Player` class  
```cpp
#include <api/Basic_Event.h>
#include <mc/Player.h>
```
Then add the following sample code in the `entry` function:  
```cpp
Event::addEventListener([](PlayerDestroyEV ev) {
        string name = ev.Player->getNameTag();
        string pos = std::to_string(ev.blkpos.x) + "," +  std::to_string(ev.blkpos.y) + "," +  std::to_string(ev.blkpos.z);
        std::cout << name << "destroyed a block at " << pos << "\n";
        });
```
In this way, the plug-in listens to the player's block destruction event and outputs information on the console when the event is triggered  
You can also choose not to use lambda expressions:  
```cpp
void entry() {
    Event::addEventListener(playerDestroy);
}

void playerDestory(PlayerDestroyEV ev) {
    string name = ev.Player->getNameTag();
    string pos = std::to_string(ev.blkpos.x) + "," +  std::to_string(ev.blkpos.y) + "," +  std::to_string(ev.blkpos.z);
    std::cout << name << "destroyed a block at " << pos << "\n";
}
```
Currently the events that can be listened are  
```cpp
namespace Event {
LIAPI inline void addEventListener(function<void(JoinEV)> callback);//When a player joined server
LIAPI inline void addEventListener(function<void(LeftEV)> callback);//When a player left server
LIAPI inline void addEventListener(function<bool(ChatEV)> callback);//When a player sent a message
LIAPI inline void addEventListener(function<void(ChangeDimEV)> callback);//When a player changed dimension
LIAPI inline void addEventListener(function<void(ServerStartedEV)> callback);//When server started
LIAPI inline void addEventListener(function<bool(PlayerUseCmdEV)> callback);//While a player using a command
LIAPI inline void addEventListener(function<bool(CmdBlockExeEV)> callback);//While a command block is running
LIAPI inline void addEventListener(function<void(RegCmdEV)> callback);//While server is registering commands
LIAPI inline void addEventListener(function<void(PlayerDeathEV)> callback);//When a player died
LIAPI inline void addEventListener(function<void(PlayerDestroyEV)> callback);//When a player destroyed a block
LIAPI inline void addEventListener(function<void(PlayerUseItemOnEV)> callback);//When a player used an item on a block
LIAPI inline void addEventListener(function<void(MobHurtedEV)> callback);//When a mob be attacked
LIAPI inline void addEventListener(function<void(PlayerUseItemEV)> callback);//When a player used an item
LIAPI inline void addEventListener(function<void(PostInitEV)> callback);//While LiteLoader is loading
LIAPI inline void addEventListener(function<void(MobDieEV)> callback);//When a mob died
LIAPI inline void addEventListener(function<void(PreJoinEV)> callback);//While a player is connecting to server
};  // namespace Event
```
