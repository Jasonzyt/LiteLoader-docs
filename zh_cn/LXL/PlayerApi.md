# LiteXLoader - 玩家 API
> 对于实体对象，除了可以使用 **通用API** 和 **生物API** 之外，还有这些额外的功能  

- 获取指定玩家的玩家指针  
`getPlayer(info)`
    - 返回值：玩家指针  
    - 返回值类型：`Pointer` 
        - 如返回值为 0 则表示获取玩家失败
    - 参数：
        - info : `String`  
        玩家的名字或者Xuid  
<br>

- 获取玩家名字  
`getName(player)`
    - 返回值：目标玩家的名字
    - 返回值类型： `String` 
        - 如返回值为 空字符串 则表示获取名字失败
    - 参数：
        - target : `Pointer`  
        待查询的玩家指针  
<br>

- 获取玩家Xuid  
`getXuid(player)`
    - 返回值：玩家的Xuid  
    - 返回值类型：`String` 
        - 如返回值为 空字符串 则表示获取Xuid失败
    - 参数：
        - player : `Pointer`  
        玩家指针  
<br>

- 获取玩家坐标  
`getPos(player)`
    - 返回值：目标玩家的位置
    - 返回值类型：`Vec4` （详见 [通用API](BaseApi.md) ）
        - 如返回值为 `Null` 则表示获取位置失败
    - 参数：
        - target : `Pointer`  
        待查询的玩家指针  
<br>

- 获取玩家真实名字（无法被篡改）  
`getRealName(player)`
    - 返回值：目标玩家的真实名字
    - 返回值类型： `String` 
        - 如返回值为 空字符串 则表示获取名字失败
    - 参数：
        - target : `Pointer`  
        待查询的玩家指针  
<br>

- 判断玩家是否为OP  
`isOP(player)`
    - 返回值：是否为OP
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        待查询的玩家指针  
<br>

- 获取在线玩家列表  
`getOnlinePlayers()`
    - 返回值：在线的玩家列表（一个由玩家指针组成的数组）
    - 返回值类型：`Array<Pointer,Pointer,...>`
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

- 发送一个原始文本给玩家  
`tellraw(player,msg)`
    - 返回值：是否成功发送
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        玩家指针
        - msg : `String`  
        待发送的rawjson文本  
<br>

- 传送玩家至指定位置  
`teleport(player,pos)`
    - 返回值：是否成功传送
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        玩家指针
        - pos : `Vec4`  
        目标位置对象（详见 [通用API](BaseApi.md) ）  
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

- 重命名玩家  
`renamePlayer(player,newname)`
    - 返回值：是否重命名成功
    - 返回值类型：`Boolean`
    - 参数：
        - player : `Pointer`  
        玩家指针
        - newname : `String`  
        玩家的新名字  
<br>
