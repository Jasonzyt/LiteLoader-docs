# 预加载插件
在`plugins\`文件夹内创建`preload.conf`并在文件中填写需要预加载的插件的相对路径（一行一个—），例如:
```
plugins\\preload\\BDSNetRunner.dll
```
在LiteLoader初次加载时，如果`plugins\`文件夹内含有`BDSNetRunner.dll`，则会自动将此插件加入`preload.conf`
若您遇到BDSNetRunner无法加载的情况，请删除`plugins\preload.conf`