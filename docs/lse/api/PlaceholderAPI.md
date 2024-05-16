# PlaceholderAPI
使用PAPI类需要导入PlaceholderAPI模块
导入示例：
```javascript
const { PAPI } = require('./GMLIB-LegacyRemoteCallApi/lib/BEPlaceholderAPI-JS');
```

> 注意：  
> 若无特殊说明，PlaceholderAPI相关API需要可在任意时间调用。


### 注册玩家PAPI
`PAPI.registerPlayerPlaceholder(func: function, pluginName: String, PAPIName: String)`

参数：

- func: 获取玩家相关信息的一个函数。此函数的传入参数必须为玩家对象，返回值必须为String。
- pluginName: 你的插件的名字，用于检索对应插件注册的PAPI.
- PAPIName: 注册的PlaceholderAPI的名字，注意不要用 `%` 包裹

返回值：`Boolean`（是否注册成功）

[JavaScript]
```JavaScript
function getPlayerUuid(pl) {
    return pl.uuid;
}

PAPI.registerPlayerPlaceholder(getPlayerUuid, "MyPlugin", "pl_uuid");

// 这样就注册了一个PAPI，为 "%pl_uuid%"
```

### 注册服务器PAPI
`PAPI.registerServerPlaceholder(func: function, pluginName: String, PAPIName: String)`

参数：

- func: 获取不包含特定玩家相关信息的一个函数。此函数没有传入参数，返回值必须为String。
- pluginName: 你的插件的名字，用于检索对应插件注册的PAPI.
- PAPIName: 注册的PlaceholderAPI的名字，注意不要用 `%` 包裹

返回值：`Boolean`（是否注册成功）

[JavaScript]
```JavaScript
function getOnlinePlayersCount() {
    return mc.getAllPlayers().length.toString();
}

PAPI.registerServerPlaceholder(getOnlinePlayersCount, "MyPlugin", "server_online_players");

// 这样就注册了一个PAPI，为 "%server_online_players%"
```

### 翻译包含PAPI的字符串
`PAPI.translateString(str: String [, pl：Player])`

参数：

- str: 需要翻译的字符串，里面可以包含不止一个PAPI，可以有其他无关内容
- pl: 玩家对象，选填。如果填写了玩家对象，这个字符串里面的关于该玩家对象的变量也会被翻译。

返回值：`String`（翻译了全部PAPI变量的字符串）

[JavaScript]
```JavaScript
let result1 = PAPI.translateString("服务器mspt：%server_mspt%, 服务器TPS：%server_tps%");
// 这样就得到的result1就是翻译了全部PAPI的语句。例如 服务器mspt：1.919810, 服务器TPS：20.000000

let result2 = PAPI.translateString("服务器mspt：%server_mspt%, 玩家名：%player_name%", pl);
// 这样就得到的result2就是翻译了全部PAPI的语句。例如 服务器mspt：1.919810, 玩家名：蔡徐坤
```

### 获取已注册的全部PAPI
`PAPI.getAllPAPI()`

返回值：`List<String>`（一个包含全部PAPI的数组）

[JavaScript]
```JavaScript
let All_PAPI = PAPI.getAllPAPI();
```

### 注销一个PAPI
`PAPI.unRegisterPlaceholder(papi: String)`

参数：

- papi: 需要注销的PAPI（不要带`%`包裹）

返回值：`Boolean`（是否注销成功）

[JavaScript]
```JavaScript
PAPI.unRegisterPlaceholder("server_mspt")
```

### 获取一个非玩家PAPI变量的值（不建议使用）
`PAPI.getValue(papi: String)`

参数：

- papi: 需要翻译的PAPI（不要带`%`包裹）

返回值：`String`（翻译后的PAPI）

[JavaScript]
```JavaScript
PAPI.PAPI.getValue("server_mspt");
```

> 注意：
> 不建议单独使用此API，你可以使用PAPI.translateString()一次性翻译全部PAPI

### 获取一个玩家PAPI变量的值（不建议使用）
`PAPI.getValueByPlayer(papi: String, pl: Player)`

参数：

- papi: 需要翻译的PAPI（不要带`%`包裹）
- pl: 玩家对象

返回值：`String`（翻译后的PAPI）

[JavaScript]
```JavaScript
PAPI.getValueByPlayer("player_name", pl);
```

> 注意：
> 不建议单独使用此API，你可以使用PAPI.translateString()一次性翻译全部PAPI