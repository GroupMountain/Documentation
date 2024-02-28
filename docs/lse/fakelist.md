# 虚拟在线玩家 API

### 获取所有虚拟在线玩家

方法: `GMLIB_API.getAllFakeNames()`

- 返回参数类型 : `array`

[JavaScript]

```JavaScript
var fakenames = GMLIB_API.getAllFakeNames();
```

### 添加虚拟在线玩家:

方法: `GMLIB_API.addFakeList(name: string, xuid: string)`

- 参数:
  - name: 玩家名字
  - xuid: 玩家 XUID
- 返回值: 操作是否成功。
- 返回值类型:
  `bool`

[JavaScript]

```JavaScript
var success = GMLIB_API.addFakeList("FakePlayer", "233")
```

### 移除虚拟在线玩家:

方法: `GMLIB_API.removeFakeList(nameOrXuid: string)`

- 参数:
  - nameOrXuid: 玩家名字或 XUID
    返回值: 操作是否成功。
- 返回值类型: `bool`

```JavaScript
var success = GMLIB_API.removeFakeList("FakePlayer")
```

### 移除所有虚拟在线玩家:

方法: `GMLIB_API.removeAllFakeLists()`

[JavaScript]

```JavaScript
GMLIB_API.removeAllFakeLists()
```

### 检查虚拟在线玩家是否存在:

方法: `GMLIB_API.checkFakeListExistsName(name: string)`

- 参数:
  - name: 玩家名字
    返回值: 是否存在。
- 返回值类型: `bool`

[JavaScript]

```JavaScript
var exists = GMLIB_API.checkFakeListExistsName("FakePlayer")
```

### 检查虚拟在线玩家和 XUID 是否存在:

方法: `GMLIB_API.checkFakeListExists(name: string, xuid:string)`

- 参数:
  - name: 玩家名字
  - xuid: 玩家 XUID
    返回值: 是否存在。
- 返回值类型: `bool`

[JavaScript]

```JavaScript
var exists = GMLIB_API.checkFakeListExists("FakePlayer", "fakeXUID123")
```
<font color=Red>设置真实名字和虚拟在线玩家对应关系[未通过测试]:

方法: `GMLIB_API.setListName(realName: string, fakeName:string)`

- 参数:
  - realName: 真实玩家名字
  - fakeName: 虚拟在线玩家名字

[JavaScript]

```JavaScript
GMLIB_API.setListName("RealPlayer", "FakePlayer")
```
</font>
<font color=Red>重置真实名字和虚拟在线玩家对应关系[未通过测试]:

方法: GMLIB_API.resetListName(realName: string)

- 参数:
  - realName: 真实玩家名字

[JavaScript]

```JavaScript
GMLIB_API.resetListName("RealPlayer")
```
</font>
### 设置模拟玩家列表优化状态:

方法: `GMLIB_API.setSimulatedPlayerListOptimizeEnabled(value: bool)`

- 参数:
  - value: 是否启用优化 :

[JavaScript]

```JavaScript
GMLIB_API.setSimulatedPlayerListOptimizeEnabled(true)
```

### 获取模拟玩家列表优化状态:

方法: `GMLIB_API.getSimulatedPlayerListOptimizeEnabled()`

- 返回值类型: `bool`

[JavaScript]

```JavaScript
var isEnabled = GMLIB_API.getSimulatedPlayerListOptimizeEnabled()
```
