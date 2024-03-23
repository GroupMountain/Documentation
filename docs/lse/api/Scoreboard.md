# 计分板API
使用Scoreboard类需要导入Scoreboard模块
导入示例：
```javascript
const { Scoreboard } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');
```

> 注意：
> 若无特殊说明，Scoreboard相关API需要再 `onServerStarted` 之后调用。


### 获取计分板追踪的全部对象
`Scoreboard.getAllTrackedEntities()`

- 返回值：`Array<Object>`  
  计分板追踪的全部对象，可分为 `Player`、`Entity` 和 `FakePlayer`。


### 获取计分板追踪的全部玩家
`Scoreboard.getAllTrackedPlayers()`

- 返回值：`Array<String>`  
  计分板追踪的玩家的UUID。


### 获取计分板追踪的全部非玩家实体
`Scoreboard.getAllTrackedEntities()`

- 返回值：`Array<String>`  
  计分板追踪的实体的UniqueId。


### 获取计分板追踪的全部字符串
`Scoreboard.getAllScoreboardFakePlayers()`

- 返回值：`Array<String>`  
  计分板追踪的字符串。


### 创建一个计分板
`Scoreboard.addObjective(name[, displayName])`

参数：  

- name：`String`  
  计分板的名字
- displayName：`String`（可选参数）  
  计分板的显示名称

- 返回值：`Boolean`  
  是否创建成功。


### 删除一个计分板
`Scoreboard.removeObjective(name)`

参数：  

- name：`String`  
  计分板的名字

- 返回值：`Boolean`  
  是否删除成功。


### 获取所有计分板名称
`Scoreboard.getAllObjectives()`

- 返回值：`Array<String>`  
  全部计分板的名称。


### 获取计分板显示名称
`Scoreboard.getDisplayName(objective)`

参数：  

- objective：`String`  
  计分板的名字

- 返回值：`String`  
  计分板的显示名称


### 设置计分板显示名称
`Scoreboard.setDisplayName(objective, displayName)`

参数：  

- objective：`String`  
  计分板的名字
- displayName：`String`  
  计分板的显示名称

- 返回值：`Boolean`  
  是否删除成功。


### 设置计分板显示
`Scoreboard.setDisplay(objective, slot[, order])`

参数：  

- objective：`String`  
  计分板的名字
- slot：`String`  
  计分板的显示位置，可以为`list`、`sidebar`和`belowname`  
- order：`Integer`（可选参数）  
  计分板的排序方式，可以写 `0` 或 `1`

- 返回值：`Boolean`  
  是否设置成功。


### 清除计分板显示
`Scoreboard.clearDisplay(slot)`

参数：  

- slot：`String`  
  需要清除的显示位置

- 返回值：`Boolean`  
  是否设置成功。


### 获取计分板的分数
`Scoreboard.getPlayerScore(uuid, objective)`  
`Scoreboard.getFakePlayerScore(name, objective)`  
`Scoreboard.getEntityScore(uniqueId, objective)`

参数：  

- uuid / name / uniqueId：`String`  
  玩家的UUID / 追踪的字符串 / 实体的UniqueId
- objective：`String`  
  计分板的名字

- 返回值：`Integer`  
  计分板的分数。如果计分板没有分数则返回`null`。

> 注意：  
> 1. 如果计分板不存在，则会自带创建计分板。  
> 2. 此API可离线添加分数，无需玩家在线/实体加载。


### 添加计分板的分数
`Scoreboard.addPlayerScore(uuid, objective, value)`
`Scoreboard.addFakePlayerScore(name, objective, value)`
`Scoreboard.addEntityScore(uniqueId, objective, value)`

参数：  

- uuid / name / uniqueId：`String`  
  玩家的UUID / 追踪的字符串 / 实体的UniqueId
- objective：`String`  
  计分板的名字
- value：`Integer`  
  添加的分数

- 返回值：`Boolean`  
  是否操作成功。

> 注意：  
> 1. 如果计分板不存在，则会自带创建计分板。  
> 2. 此API可离线添加分数，无需玩家在线/实体加载。


### 减少计分板的分数
`Scoreboard.reducePlayerScore(uuid, objective, value)`
`Scoreboard.reduceFakePlayerScore(name, objective, value)`
`Scoreboard.reduceEntityScore(uniqueId, objective, value)`

参数：  

- uuid / name / uniqueId：`String`  
  玩家的UUID / 追踪的字符串 / 实体的UniqueId
- objective：`String`  
  计分板的名字
- value：`Integer`  
  减少的分数

- 返回值：`Boolean`  
  是否操作成功。

> 注意：  
> 1. 如果计分板不存在，则会自带创建计分板。  
> 2. 此API可离线减少分数，无需玩家在线/实体加载。


### 设置计分板的分数
`Scoreboard.setPlayerScore(uuid, objective, value)`
`Scoreboard.setFakePlayerScore(name, objective, value)`
`Scoreboard.setEntityScore(uniqueId, objective, value)`

参数：  

- uuid / name / uniqueId：`String`  
  玩家的UUID / 追踪的字符串 / 实体的UniqueId
- objective：`String`  
  计分板的名字
- value：`Integer`  
  设置的分数

- 返回值：`Boolean`  
  是否操作成功。

> 注意：  
> 1. 如果计分板不存在，则会自带创建计分板。  
> 2. 此API可离线设置分数，无需玩家在线/实体加载。


### 重置计分板的分数
`Scoreboard.resetPlayerScore(uuid, objective)`  
`Scoreboard.resetFakePlayerScore(name, objective)`  
`Scoreboard.resetEntityScore(uniqueId, objective)`

参数：  

- uuid / name / uniqueId：`String`  
  玩家的UUID / 追踪的字符串 / 实体的UniqueId
- objective：`String`  
  计分板的名字

- 返回值：`Boolean`  
  是否操作成功。

> 注意：  
> 1. 如果计分板不存在，则会自带创建计分板。  
> 2. 此API可离线重置分数，无需玩家在线/实体加载。


### 重置一个对象全部计分板的分数
`Scoreboard.resetPlayerScores(uuid)`  
`Scoreboard.resetFakePlayerScores(name)`  
`Scoreboard.resetEntityScores(uniqueId)`

参数：  

- uuid / name / uniqueId：`String`  
  玩家的UUID / 追踪的字符串 / 实体的UniqueId

- 返回值：`Boolean`  
  是否操作成功。

> 注意：  
> 1. 如果计分板不存在，则会自带创建计分板。  
> 2. 此API可离线重置分数，无需玩家在线/实体加载。