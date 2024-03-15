# PlaceholderAPI
使用PAPI类需要导入PlaceholderAPI模块
导入示例：
```javascript
const { PAPI } = require('./GMLIB-LegacyRemoteCallApi/lib/BEPlaceholderAPI-JS');
```

> 注意：
> 若无特殊说明，PlaceholderAPI相关API需要可在任意时间调用。


### 注册玩家PAPI
`PAPI.registerPlayerPlaceholder(func: function, pluginName: string, PAPIName: string)`

参数：
- func: 获取玩家相关信息的一个函数。此函数的传入参数必须为玩家对象，返回值必须为String。
- pluginName: 你的插件的名字，用于检索对应插件注册的PAPI.
- PAPIName: 注册的PlaceholderAPI的名字，注意不要用 `%` 包裹

[JavaScript]
```JavaScript
function getPlayerUuid(pl) {
    return pl.uuid;
}

PAPI.registerPlayerPlaceholder(getPlayerUuid, "MyPlugin", "pl_uuid");

// 这样就注册了一个PAPI，为 "%pl_uuid%"
```