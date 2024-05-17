# 实验性内容API
使用Experiments类需要导入Experiments模块
导入示例：
[JavaScript]
```javascript
const { Experiments } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');
```

> 注意：  
> 若无特殊说明，实验性内容相关API需要在 `onServerStarted` 之后调用。


### 获取实验启用状态

`Experiments.getExperimentEnabled(experiment_id: int)`

参数:

- experiment_id: 实验性ID。

返回值：Boolean(实验性是否启用)

[JavaScript]
```JavaScript
Experiments.getExperimentEnabled(6)
```

### 设置实验启用状态

`Experiments.setExperimentEnabled(experiment_id: int, value: bool)`

参数:

- experiment_id: 实验性ID。
- value: 是否启用。

返回值：Boolean(是否设置成功)

[JavaScript]
```JavaScript
Experiments.setExperimentEnabled(6, true)
```

> 注意：
> 请不要随意关闭实验性玩法，这可能导致错误
> 部分实验性玩法修改后需要重启服务器才能生效。

### 设置实验性依赖
如果插件需要某个实验性玩法，请直接设置依赖项，GMLIB会在开服前自动启用。

`Experiments.registerExperimentsRequire(experiment_id: id)`

参数:

- experiment_id: 实验性ID。

返回值：无

[JavaScript]
```JavaScript
Experiments.getExperimentEnabled(6)
```

> 注意：
> 此API请在 `onServerStarted` 之前调用。

### 获取实验ID列表

`Experiments.getAllExperiments()`


返回值：Array<Int> (一个包含所有实验性ID的数组)


### 获取实验性键名
将实验性ID转化为键名。  
如需翻译，请使用I18nAPI翻译为对应的可读语言。

`Experiments.getExperimentTranslateKey(experiment_id: id)`

参数:

- experiment_id: 实验性ID。

返回值：String（实验性键名）

[JavaScript]
```JavaScript
Experiments.getExperimentTranslateKey(6)
```

> 注意：
> 此API请在 `onServerStarted` 之前调用。


### 获取实验ID-译名映射表

`Experiments.getExperimentsMap()`

返回值：Object (实验性ID和译名的映射)

