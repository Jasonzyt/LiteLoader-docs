# LiteXLoader - 事件 API
> 除了 **通用 API** 之外，还有这些在监听事件时需要额外使用到的功能  

## 监听 API
注册指定的监听函数。当事件发生时，监听函数将被引擎调用以供处理相关事件。  
- 新增监听器  
`listen(event,callback)`
    - 返回值：是否成功监听事件
    - 返回值类型：`Boolean`
    - 参数：
        - event : `String`  
        要监听的事件名（见下方监听事件列表）
        - callback : `Function`  
        注册的监听函数
<br>

---
## 监听事件列表
目前，LiteXLoader支持如下这些事件的监听。

- `"OnJoin"` - 玩家进入服务器
- `"OnLeft"`
- `"OnRespawn"`
- `"OnChangeDim"`
- `"OnPlayerCmd"`
- `"OnChat"`
- `"OnAttack"`
- `"OnUseItem"`
- `"OnTakeItem"`
- `"OnDropItem"`
- `"OnDestroyBlock"`
- `"OnPlaceBlock"`
- `"OnOpenChest"`
- `"OnCloseChest"`
- `"OnOpenBarrel"`
- `"OnCloseBarrel"`
- `"OnChangeSlot"`
- `"OnMobDie"`
- `"OnMobHurt"`
- `"OnExplode"`
- `"OnCmdBlockExecute"`
- `"OnServerStarted"`
- `"OnServerCmd"`