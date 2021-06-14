# 注册指令
LiteLoader内置了真正的指令注册Api  
要为您的插件注册指令，需要在插件的`entry`函数中监听`RegCmdEv`，示例代码：  
```cpp
Event::addEventListener([](RegCmdEV ev) {
		CMDREG::SetCommandRegistry(ev.CMDRg);
		MakeCommand("wow", "awesome", 0);//注册指令
		CmdOverload(wow, oncmd_wow, "input", "optinal");//重载指令
		});
```
示例代码中，`MakeCommand`函数有三个参数，分别为**指令**、**指令说明**、**权限等级**  
`CmdOverload`具有三个参数，分别为**指令**、**使用指令后调用的函数**、**指令参数**，其中，指令参数是可选的，如果您想要注册的指令不需要参数，就可以省略指令参数；如果您需要注册有多个参数的指令，您可以直接向后添加更多指令参数  
在监听完指令注册事件后，您还需要声明一个bool类型的函数，示例代码：  
```cpp
bool oncmd_wow(CommandOrigin const& ori, CommandOutput& outp, string const& str, optional<int>& str2) {
    if (str2.set) {
        outp.addMessage(str2);
    }
    outp.addMessage(str);
    return true;
}
```
`oncmd_wow`的第三个参数就是被注册指令的第一个参数，第四个参数就是被注册指令的第二个参数；第四个参数`optional<string>&`意味着这个参数可以在指令使用时被省略  
在做完这些只后，如果指令注册成功，控制台就会输出这样一条消息：`RegisteringCommand > wow`，这代表指令wow已经成功地被注册  
您可以在游戏或控制台中输入`wow ILoveChina`，使用指令后将服务器就会输出`ILoveChina`；若您输入`wow ILoveChina HelloWorld`，则服务器就会输出
```
HelloWorld
ILoveChina
```