## LLMoney
### Description
File Name: `LLMoney.dll`  
Language Pack: `landpack/money.json`  
Config File: `config/money.json`  
Database(sqlite): `data/money.db` 

### Functions
economy plugin with turnover function, storage by sqlite, support multipe server sync

### Commands
`/money query [player]` query own balance or others  
`/money hist [player]` query own turnover or others  
such as:`/money query`  
`/money hist steve`

`/money pay <player> <count>` pay for a player  
`/money set <player> <count>` set up player's balance(only OP)  
`/money add <player> <count>` add player's balance(only OP)  
`/money reduce <player> <count>` reduce player's balance(only op)  
`/money purge [seconds]` clear turnover a few seconds ago, if not specified all turnover will be cleared  

<u>playername case insensitive</u>  

<u>`/money reduce` can be used in commands block</u>

### Config File
```
{
"def_money":0, //balance by default
"pay_tax":0.0 //pay tax, tax=count*pay_tax
}
```