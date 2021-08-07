# 注册指令
## 注册指令基础
LiteLoader内置了真正的指令注册Api  
以下内容需要包含下列头文件：  
`mc/Command.h` `mc/CommandReg.h` `api/regCommandHelper`  
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
        outp.addMessage(std::to_string(str2.val()));
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
## 使用枚举类型注册指令
如果您想要您的插件也能注册像`/scoreboard`那样有参数提示的命令，那么需要使用枚举  
首先，让我们写一个枚举类型（必须从`1`开始而不是从默认的`0`开始） 
```cpp
enum class CMDEnum {
    Add = 1,
    Set = 2,
    Query = 3
};
```
在回调函数中，枚举类型的参数应使用`MyEnum<>`类型(可作选项参数):
```cpp
int score; // Global
bool onCmdScore(CommandOrigin const& ori, CommandOutput& outp, MyEnum<CMDEnum>& op, optional<int>& val) {
    switch (op.val) {
        case CMDEnum::Add:
	score++;
	break;
        case CMDEnum::Set: 
	if (val.set) score = val.val();
	break;
	case CMDEnum::Query:
	outp.addMessage(u8"当前分数: " + std::to_string(score));
	break;
    }
    return true;
}
```
接着，监听注册命令事件注册命令，注册含有枚举参数的命令需要先定义`CEnum`  
```cpp
Event::addEventListener([](RegCmdEV ev) {
    CMDREG::SetCommandRegistry(ev.CMDRg);
    //CEnum _c1("此参数的名字", {"枚举选项的名字(必须与枚举成员数量相同)",...});
    CEnum _c1("Operation", {"add","set","query"});
    MakeCommand("score", "Enum Command Example", CommandPermissionLevel::Normal/*==0*/);
    CmdOverload(score, onCmdScore, "op", "score");
});
```
## `optional`模板类的使用
`optional`模板类并不是标准库中的`std::optional`，这个类定义于`stl/optional.h`  
它是命令注册的一部分，作为游戏中命令的可选参数(在游戏内表现为`/cmd [xx: xx]`),并且在上面的样例中已多次使用  
`optional`后的尖括号中可以填入任意命令注册API支持的类型，如`int bool std::string MyEnum<> CommandSelector<>`等等  
- 成员函数`val()`&`value()`
  返回值: `T` 可选参数的值  
  请注意,在调用`val()`之前一定要确保`Set()`的返回值为真，否则会抛出异常!
- 成员函数`Set()`
  返回值: `bool` 此可选参数是否已被设置
## `CommandSelector`模板类的使用
`CommandSelector`，顾名思义，即游戏中的目标选择器，可以快捷方便的选择多个玩家或实体  
`CommandSelector`类的模板只接受一下两种类型: `Actor`&`Player`  
前者表示选取任何实体，后者只选取玩家  
- 成员函数`results(CommandOrigin const& ori)`
  返回值：`CommandSelectorResults<T>` 目标选择器的结果   
  参数`ori`: `CommandOrigin const&` 即命令回调函数的参数1
## `CommandSelectorResults`模板类的使用
`CommandSelectorResults`，顾名思义，即目标选择器选择的结果  
- 成员函数`begin()`: 
  返回值: `vector<T>::iterator` 用于遍历结果的迭代器(起始位置)
- 成员函数`end()`: 
  返回值: `vector<T>::iterator` 用于遍历结果的迭代器(结束位置)
- 成员函数`count()`:
  返回值: `size_t` 结果的数量
- 成员函数`empty()`:
  返回值: `bool` 结果是否为空
下面举一个很简单的选择器例子: 
```cpp
bool onCmdTest(CommandOrigin const& ori, CommandOutput& outp, CommandSelector<Player>& cs) {
    auto res = cs.results();
    if (!res.empty()){
        outp.addMessage("找到了以下玩家: ");
	for (auto it = res.begin(); it != res.end(); it++){
	    outp.addMessage((*it)->getNameTag());
	}
	return true;
    }
    outp.addMessage("没有找到玩家");
    return true;
}
```
