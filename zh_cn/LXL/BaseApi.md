# LiteXLoader - 通用 API
除了拥有灵活可扩展性强的跨语言兼容能力之外，LiteXLoader的设计思想同样  

## 对象指针
为了最大化地提升引擎的工作效率，对于游戏元素的索引，我们使用类似C++语言中的`指针`思想，称其为`对象指针`。  
在多数 API 接口中，你们都会见到类似于`方块指针`、`玩家指针`这样的参数。在脚本语言中，这里的`指针`变量其实只是一个整数。引擎使用这个整数来定位相关的游戏元素。  
<br>

## 数据类型
> 接下来，我们熟悉几种在使用 API 过程中会频繁用到的 数据类型

### 通用数据类型
由于LiteXLoader支持多种不同的脚本语言，为了方便起见，给一些通用的数据类型以统一的称呼。  
- `Null` - 空（未定义，不存在等等）
- `Number` - 数字（可以是整数 / 浮点数，视具体情况）
- `String` - 字符串
- `Boolean` - 布尔型
- `Function` - 函数
- `Array` - 数组 / 列表
- `Object` - 对象
- `Pointer` - 上文提到的对象指针

### Vec4对象
在游戏中，数量众多的 API 都需要提供位置坐标。于是引擎采用Vec4类型的对象来标示坐标。  
对于 `Vec4` 类型变量 v：  
- `v.x` - x坐标  
- `v.y` - y坐标  
- `v.z` - z坐标  
- `v.dim` - 维度（0主世界，1下界，2末地）

---
## 通用 API
> 这些是在编写脚本过程中到处需要使用到的 API  
> 下文中的 `对象` 为统称，如果没有特指，可以指代 方块，实体，玩家 等等各种游戏元素 

- 获取指定对象名字  
`getName(pointer)`
    - 返回值：对象名字
    - 返回值类型： `String` 
        - 如返回值为 空字符串 则表示获取Xuid失败
    - 参数：
        - pointer : `Pointer`  
        待查询的对象指针  
<br>

- 获取指定对象坐标  
`getPos(pointer)`
    - 返回值：对象位置
    - 返回值类型：`Vec4` 
        - 如返回值为 `Null` 则表示获取位置失败
    - 参数：
        - pointer : `Pointer`  
        待查询的对象指针
<br>

- 执行一条后台指令  
`runCmd(cmd)`
    - 返回值：是否执行成功
    - 返回值类型： `Boolean` 
    - 参数：
        - cmd : `String`  
        待执行的命令
<br>

- 执行一条后台指令（强化版）  
`runCmdEx(cmd)`
    - 返回值：
    - 返回值类型： `` 
    - 参数：
        - cmd : `String`  
        待执行的命令
<br>

- 设置服务器Motd  
`setServerMotd(motd)`
    - 返回值：是否设置成功
    - 返回值类型：`Boolean`
    - 参数：
        - motd : `String`  
        目标Motd字符串
<br>

---
## 辅助 API
> 这些是在编写脚本过程中到处需要使用到的 API  

- 推迟一段时间执行函数  
`setTimeout(func,msec)`
    - 返回值：启动的定时器ID
    - 返回值类型：`Number` 
    - 参数：
        - func : `Function`  
        待执行的函数
        - msec : `Number`  
        推迟的时间（毫秒）
<br>

- 设置周期执行函数  
`setInterval(func,msec)`
    - 返回值：启动的定时器ID
    - 返回值类型： `Number` 
    - 参数：
        - func : `Function`  
        待执行的函数
        - msec : `Number`  
        执行间隔周期（毫秒）
<br>

- 取消延期执行或周期执行函数  
`cancelTimeout(timerid)`
    - 返回值：是否取消成功
    - 返回值类型： `Boolean` 
    - 参数：
        - timerid : `Number`  
        由前两个函数返回的定时器ID
<br>
