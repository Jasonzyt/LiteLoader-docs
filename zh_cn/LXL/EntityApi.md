# LiteXLoader - 实体 API
> 对于实体对象，除了可以使用 **通用API** 之外，还有这些额外的功能  

## 生物 API
- 

## 玩家 API
> 对于玩家对象，除了可以使用 **通用API** 和 **生物API** 之外，还有这些额外的功能

- 获取指定玩家的玩家指针  
`getPlayer(info)`
    - 返回值：玩家指针  
    - 返回值类型：`Pointer` 
        - 如返回值为 0 则表示获取玩家失败
    - 参数：
        - info : `String`  
        玩家的名字或者Xuid
<br>

- 根据玩家指针获取其Xuid  
`getXuid(player)`
    - 返回值：玩家的Xuid  
    - 返回值类型：`String` 
        - 如返回值为 空字符串 则表示获取Xuid失败
    - 参数：
        - player : `Pointer`  
        玩家指针
<br>

- 获取在线玩家列表  
`getOnLinePlayers()`
    - 返回值：在线的玩家列表（一个由玩家指针组成的数组）
    - 返回值类型：`Array<Pointer>`
    - 参数：
        - 无
<br>

- 断开指定玩家连接  
`kickPlayer(player)`
    - 返回值：是否成功断开连接
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        玩家指针
<br>

- 发送一个原始显示文本给玩家  
`sendText(player,msg)`
    - 返回值：是否成功发送
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        玩家指针
        - msg : `String`  
        待发送的文本 / rawjson文本
<br>

- 传送玩家至指定位置  
`teleport(player,pos)`
    - 返回值：是否成功传送
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        玩家指针
        - pos : `Vec4`  
        目标位置对象（详见 [通用API](zh_cn/LXL/BaseApi) ）
<br>

- 以指定玩家身份执行一条指令  
`runCmdAs(cmd,player)`
    - 返回值：是否执行成功
    - 返回值类型： `Boolean` 
    - 参数：
        - cmd : `String`  
        待执行的命令
        - player : `Pointer`  
        玩家指针
<br>
