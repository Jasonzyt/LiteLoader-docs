# LiteXLoader - 划时代 x 跨语言脚本插件加载器
[![GitHub license](https://img.shields.io/github/license/LiteLDev/LiteXLoader)](https://github.com/LiteLDev/LiteXLoader/blob/main/LICENSE)
[![Build](https://img.shields.io/badge/build-passing-brightgreen)](#)
![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/LiteLDev/LiteXLoader?include_prereleases)
## 🎨 简介
`LiteXLoader`是一个基岩版官方服务端`Bedrock Delicated Server`（以下简称**BDS**）插件框架，提供强大的跨语言脚本支持能力和很好的兼容能力。  
由`LiteLoader`插件加载器加载并提供部分基础API支持。  
使用脚本开发**BDS**插件具有上手容易、便于维护的优点。同时脚本插件不需要随着**BDS**版本更新而重新适配，仅需加载器适配即可，给开发者们带来极大便利。  

## 🎁 特点
1. **跨语言**脚本支持  
基于开源`ScriptX`框架开发，借助其强大的抽象能力，支持多种不同脚本语言编写的插件同时运行，且底层仅需一层统一的C++ API接口，维护和适配都比较方便。  
目前已支持语言：`JavaScript`，`Lua`  
即将支持的语言：`Python`，`Ruby`，`C#`

2. **开源** & **永久免费**  
项目采用`GPL-3.0`开源许可证，保证永远不会收费或者推出商业版。  
希望社区可以贡献更多的力量共同维护和建设  

## 🔨 Compiling
1. Install **Microsoft Visual Studio** with standard C++ building suite
2. Install the newest version of Windows SDK
3. Install CMake and add it to `PATH`
4. Run the building batch below

#### Build & Link
- `BuildJs.bat`&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;Build LiteXRunner for Js
- `BuildLua.bat`&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;Build LiteLuaRunner for Lua
- `BuildAll.bat`&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;Build All targets above

#### Clean everything generated & Rebuild & Link
- `ReBuildJs.bat`&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;ReBuild LiteXRunner for Js
- `ReBuildLua.bat`&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;ReBuild LiteXRunner for Lua
- `ReBuildAll.bat`&nbsp;&nbsp;&nbsp;-&nbsp;&nbsp;&nbsp;ReBuild All targets above

##### After building, DLLs will generate at `Release` directory.  

## 💻 安装
项目主要发布于**MineBBS**，请[移步MineBBS]()下载
1. 正确安装`LiteLoader`插件加载器
2. 下载`LiteXLoader`，解压，把全部内容复制到**BDS**的`plugins`目录中。如果有冲突，选择覆盖即可。
3. 开服

## 🎉 加载插件
1. 将需要加载的脚本插件直接放置到`plugins`目录中
2. 开服

> 你没看错，就这么简单 =w=

`LiteXLoader`的配置文件位于`BDS根目录/plugins/LiteXLoader/config.ini`，可以修改相关配置。

## 📕 开发文档
请[移步文档站](http://docs.litetitle.com/#/zh_cn/LXL/README)查看详细的API文档  
如果有修订需求或者有新增API的需要，欢迎联系作者或者发布Issue  

## 🧬 兼容性与可扩展性
兼容`旧LiteLuaRunner`、`.NetJsRunner`、`IronLuaRunner`的大部分插件。  
部分API并未适配，仅作为方便开发者而设计兼容层。  
请[移步文档站](http://docs.litetitle.com/#/zh_cn/LXL/BaseLib)查看详细的分析  

## 📡 实时调试
在BDS后台控制台执行
- `jsdebug`  
进入Js实时调试模式
- `luadebug`  
进入Lua实时调试模式

实时调试模式下，标准输入会被当做对应类型的脚本语言执行，并实时输出结果。  
再次输入对应的`jsdebug`或`luadebug`将退出实时调试模式。

## 📍 许可证声明
在使用我们的产品的时候，我们默认您已经承认并遵守了[Mojang Studios EULA](https://account.mojang.com/documents/minecraft_eula)协议。  
这意味着你不能对本项目进行任何违反EULA的商业性使用。违反EULA协议造成的一切后果由违反者自行承担。  
另外，您需要遵守本项目的`GPL-3.0`开源许可证条款，以及下列提到的各关联项目的开源许可证条款

[LiteLoader](https://github.com/LiteLDev/LiteLoader) GPLv3 with extra restrictions&exceptions    
[BedrockX](https://github.com/Sysca11/BedrockX) GPLv3 with extra restrictions&exceptions  
[ElementZero](https://github.com/Element-0/ElementZero) GPL v3  
[ChakraCore](https://github.com/chakra-core/ChakraCore) MIT  
[OpenSSL](https://github.com/openssl/openssl) Apache-2.0 License  

#### Extra Restrictions & Exceptions
If you provides a server hosting service,you can use this framework for free,but you SHOULD NOT make PRIVATE changes to this framework as a selling point. If you fixed or tweaked the code, please pull request, instead of making it private for commercial use. 
> Do not do evil.

Although we expected to build an open-source community, but forcing everything open-source will ruin this community.
So you can write plugins based on `LiteXLoader` with ANY open-source license or even dont publish your source code.
but if you modified the framework, or write a new framework based on this framework, you MUST open-source it.

## 🏆 鸣谢
开源[ScriptX](https://github.com/Tencent/ScriptX)项目提供的跨语言引擎支持  
[LiteLoader](https://github.com/LiteLDev/LiteLoaderBDS)项目提供的加载服务与基础API  
旧[LiteLuaLoader](#)项目提供的部分底层接口实现

## 📧 联系我们
LiteXLoader交流群：850517473 [点击加入](https://jq.qq.com/?_wv=1027&k=zeUbrETH)  
LiteLoader交流群：656669024 [点击加入](https://jq.qq.com/?_wv=1027&k=lagwtrfh)  
Telegram电报频道：#LiteLoader [点击加入](https://t.me/LiteLoader)  
欢迎反馈崩溃和版本适配问题。务必准备好详细的情况描述，过于简略的提问不予作答。  

## 💕赞助作者💕
项目已接入爱发电 [点击此处](https://afdian.net/@LiteXLoader?tab=home)   
给我们不断继续下去的鼓励！  