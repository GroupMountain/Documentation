# 玩家数据库API

使用UserCache类需要导入UserCache模块
导入示例：
```javascript
const { UserCache } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');
```

### 获取所有玩家
```javascript
UserCache.getAllPlayerInfo()
```
- 返回值：所有玩家信息
- 返回值类型：`Array<Object>`
    - 每个对象都含有以下属性：
        - Name：玩家名
        - Xuid：玩家的XUID
        - Uuid：玩家的UUID

### 通过XUID/UUID/NAME查玩家信息
```javascript
UserCache.getPlayerInfo(playerIdentifier)
```
- 返回值：玩家信息
- 返回值类型：`Array<Object>` | `NULL`
    - 含有以下属性：
        - Name：玩家名
        - Xuid：玩家的XUID
        - Uuid：玩家的UUID

### 通过XUID查UUID
```javascript
UserCache.getUuidByXuid()
```
- 返回值：玩家的UUID
- 返回值类型：`String`
    - 如果返回值为`Null`，则代表查询失败

### 通过名字查UUID
```javascript
UserCache.getUuidByName()
```
- 返回值：玩家的UUID
- 返回值类型：`String`
    - 如果返回值为`Null`，则代表查询失败

### 通过UUID查名字
```javascript
UserCache.getNameByUuid()
```
- 返回值：玩家的名字
- 返回值类型：`String`
    - 如果返回值为`Null`，则代表查询失败

### 通过XUID查名字
```javascript
UserCache.getNameByXuid()
```
- 返回值：玩家的名字
- 返回值类型：`String`
    - 如果返回值为`Null`，则代表查询失败

### 通过名字查XUID
```javascript
UserCache.getXuidByName()
```
- 返回值：玩家的XUID
- 返回值类型：`String`
    - 如果返回值为`Null`，则代表查询失败

### 通过UUID查XUID
```javascript
UserCache.getXuidByUuid()
```
- 返回值：玩家的XUID
- 返回值类型：`String`
    - 如果返回值为`Null`，则代表查询失败