`Chakra.dll`:LiteLoader的劫持库，通过加持Chakra来加载LiteLoader本体  
`ChakraCore.dll`:微软开源库[ChakraCore](https://github.com/microsoft/ChakraCore)，用于替代Windows10自带的`Chakra.dll`  
`LiteLoader.dll`:LiteLoader本体  
`RoDB.exe`:符号数据库生成器，需要在初次安装及版本更新后运行  
`bedrock_server.symdb`:符号数据库，用于动态符号查找  
`bedrock_server.symdef`:动态符号数据库生成时的缓存，生成后可删除  
`plugins\`:插件/插件数据存放目录  
`plugins\LiteLoader\`:LiteLoader数据存放目录