# LiteXLoader - 通用 API
除了拥有灵活可扩展性强的跨语言兼容能力之外，LiteXLoader的设计思想同样  

## 数据类型
> 接下来，我们熟悉几种在使用 API 过程中会频繁用到的数据类型

### 通用数据类型
由于LiteXLoader支持多种不同的脚本语言，为了方便起见，给一些通用的数据类型以统一的称呼。  
- `Null` - 空（未定义，不存在等等）
- `Number` - 数字（可以是整数 / 浮点数，视具体情况）
- `String` - 字符串
- `ByteBuffer` - 字节串 / 字符缓冲区 / 字符数组
- `Boolean` - 布尔型
- `Function` - 函数
- `Array` - 数组 / 列表
- `Object` - 对象
- `Pointer` - 下面提到的对象指针
- `Vec4` - 下面提到的位置坐标对象
<br>

### 对象指针
为了最大化地提升引擎的工作效率，对于游戏元素的索引，我们在脚本中使用一个专门类型的变量来跟踪每一个游戏元素，并称其为「对象指针」。你可以将其理解元素的唯一标识符。  
在大量的 API 接口中，你会见到类似于`方块指针`、`玩家指针`这样的参数。  
<br>

### Vec4对象
在游戏中，数量众多的 API 都需要提供位置坐标。引擎采用Vec4类型的对象来标示坐标。  
对于 `Vec4` 类型变量 v：  
- `v.x` - x坐标  
- `v.y` - y坐标  
- `v.z` - z坐标  
- `v.dim` - 维度（0主世界，1下界，2末地）

---

## 通用 API
这些是在编写脚本过程中到处需要使用到的 API  
> 下文中的 `对象指针` 为统称，可以传入 方块指针，实体指针，玩家指针 等等各种元素指针 

- 获取指定对象名字  
`getName(target)`
    - 参数：
        - target : `Pointer`  
        待查询的对象指针  
    - 返回值：目标对象的名字
    - 返回值类型： `String` 
        - 如返回值为 空字符串 则表示获取名字失败  
<br>

- 获取指定对象坐标  
`getPos(target)`
    - 参数：
        - target : `Pointer`  
        待查询的对象指针  
    - 返回值：目标对象的位置
    - 返回值类型：`Vec4` 
        - 如返回值为 `Null` 则表示获取位置失败  
<br>

- 执行一条后台命令  
`runCmd(cmd)`
    - 参数：
        - cmd : `String`  
        待执行的命令  
    - 返回值：是否执行成功
    - 返回值类型： `Boolean`  
<br>

- 执行一条后台命令（强化版）  
`runCmdEx(cmd)`
    - 参数：
        - cmd : `String`  
        待执行的命令  
    - 返回值：结果`Object`  
    成员 result 为`Boolean`型，表示是否执行成功  
    成员 output 为`String`型，返回BDS执行命令后的输出结果  
    - 返回值类型： `Object<Boolean,String>`   
<br>

- 注册一个命令  
`registerCmd(cmd,description)`
    - 参数：
        - cmd : `String`
        待注册命令
        - description : `String`
        命令描述文本  
    - 返回值：是否成功注册
    - 返回值类型：`Boolean`  
<br>

- 设置服务器Motd  
`setServerMotd(motd)`
    - 参数：
        - motd : `String`  
        目标Motd字符串  
    - 返回值：是否设置成功
    - 返回值类型：`Boolean`  
<br>

---
## 辅助 API
这些是在编写脚本过程中到处需要使用到的，起辅助作用的 API  

- 输出到控制台  
`log(data1,data2,...)`
    - 参数：
        - data : `任意类型`  
        待输出的变量或者数据  
        可以是任意类型，参数数量可以是任意个  
    - 返回值：无  
<br>


- 推迟一段时间执行函数  
`setTimeout(func,msec)`
    - 参数：
        - func : `Function`  
        待执行的函数
        - msec : `Number`  
        推迟执行的时间（毫秒）  
    - 返回值：此任务ID
    - 返回值类型：`Number`   
<br>

- 设置周期执行函数  
`setInterval(func,msec)`
    - 参数：
        - func : `Function`  
        待执行的函数
        - msec : `Number`  
        执行间隔周期（毫秒）  
    - 返回值：此任务ID
    - 返回值类型： `Number`   
<br>

- 取消延期执行或周期执行函数  
`cancelTimeTask(taskid)`
    - 参数：
        - timerid : `Number`  
        由前两个函数返回的任务ID  
    - 返回值：是否取消成功
    - 返回值类型： `Boolean`   
<br>

- 启动一个新的脚本插件
(仅用于运行时动态加载插件，若要导入外部代码请用各自语言的import或者require)  
`loadPlugin(path)`
    - 参数：
        - path : `String`  
        要加载的插件文件路径（如`addplugin.js`)  
    - 返回值：是否启动成功
    - 返回值类型： `Boolean`   
<br>

- 获取LiteXLoader加载器版本
`getVersion()`
    - 参数：
        - 无
    - 返回值：