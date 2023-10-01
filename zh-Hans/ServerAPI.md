## Server API

`Server API` 提供更多了插件开发所需的API

### 导入API

- `Mod API` 的导出命名空间为 `GMLib_ServerAPI`
- 下文提到的函数名则为导出函数名。
- 以LLSE-js插件为例，使用 `ll.import("Server_ModAPI", "funtion_name")` 导入，其中 `funtion_name` 应替换为对应的导入函数。

## 生成一个实体

通过此函数，你可以生成一个实体。（不同于 `mc.spawnMob` ，此函数可以生成任意实体，不限于生物）

`GMLib_Server.spawnEntity(pos, dimid, name)`

- 参数：
  - pos : `FloatPos`  
    生成的坐标
  - dimid : `Integer`
    生成的维度ID（由于底层函数坐标原型为`Vec3`，因此不会传入维度，维度信息需要单独传入）
  - pos : `String`  
    生成的实体ID
- 返回值：`Entity`
  生成的实体对象，如果为`null`则表示生成失败

  <br>

## 将玩家对象转化为实体对象

通过此函数，将一个玩家对象转化为实体对象（由于部分函数底层要求传入实体，故需要转化）

`GMLib_Server.PlayerToEntity(player)`

- 参数：
  - player : `Player`  
    需要转化的玩家对象
- 返回值：`Entity`
  生成的实体对象，如果为`null`则表示转化失败

<br>

## 让实体发射一个弹射物

通过此函数，可以让一个实体发射一个弹射物（类似于射箭，但是可以发射任意实体，甚至发射一个苦力怕）

`GMLib_Server.shootProjectile(entity, name, speed, offset)`

- 参数：
  - entity : `Entity`  
    发射弹射物的实体
  - name : `String`
    发射的弹射物
  - speed : `Number`  
    弹射物的速度，数字越大速度越快，必须大于0
  - offset : `Number`  
    弹射物随机角度偏移量，设置为0表示无偏移，必须大于等于0
- 返回值：`Entity`
  生成的弹射物的实体对象，如果为`null`则表示生成失败

<br>

## 让实体投掷一个实体

通过此函数，可以让一个实体投掷一个实体作为弹射物（类似于射箭，但是可以发射任意实体，甚至发射一个苦力怕）

`GMLib_Server.shootProjectile(entity1, entity2, speed, offset)`

- 参数：
  - entity1 : `Entity`  
    投掷弹射物的实体
  - entity2 : `Entity`  
    被投掷的实体
  - speed : `Number`  
    投掷弹射物的速度，数字越大速度越快，必须大于0
  - offset : `Number`  
    投掷弹射物随机角度偏移量，设置为0表示无偏移，必须大于等于0
- 返回值：`Boolean`
  是否投掷成功

<br>

## 悬浮字API
#### 发送一个悬浮字给全部玩家

通过此API，注册优雅的仅发包悬浮字，GMLIB会通过假数据包生成仅客户端看得见的悬浮字，不会对服务端生物ai造成任何影响

`GMLib_Server.sendAddFloatingTextPacket(text, pos, dimid)`

- 参数：
  - text : `String`  
    悬浮字的展示内容
  - pos : `Vec3`  
    悬浮字的展示位置
  - dimid : `Integer`
    悬浮字的展示维度ID（由于底层函数坐标原型为`Vec3`，因此不会传入维度，维度信息需要单独传入）
- 返回值：`Integer`
  悬浮字的id，如果为`-1`则表示生成失败

<br>

#### 发送一个悬浮字给单个玩家

`GMLib_Server.sendAddFloatingTextPacketToPlayer(text, pos, dimid, player)`

- 参数：
  - text : `String`  
    悬浮字的展示内容
  - pos : `Vec3`  
    悬浮字的展示位置
  - dimid : `Integer`
    悬浮字的展示维度ID（由于底层函数坐标原型为`Vec3`，因此不会传入维度，维度信息需要单独传入）
  - player : `Player`
    能看见悬浮字的玩家
- 返回值：`Integer`
  悬浮字的id，如果为`-1`则表示生成失败

> 注意：
> 创建悬浮字应在 "onServerStarted" 之后开始

<br>

#### 移除一个悬浮字

通过此函数，你可以移除一个先前创建的悬浮字

`GMLib_Server.sendDeleteFloatingTextPacket(id)`

- 参数：
  - id : `Integer`
    悬浮字的id
- 返回值:无

<br>

#### 修改一个已存在的悬浮字

通过此函数，你可以修改先前创建的悬浮字内容

`GMLib_Server.sendUpdateFloatingTextPacket(id, newtext)`

- 参数：
  - newtext : `String`  
    悬浮字的更新展示内容
  - id : `Integer`
    悬浮字的id
- 返回值：无

<br>

## 设置存档假种子

通过此函数，可以设置假种子来隐藏真实种子

`GMLib_Server.setFakeSeed(seed)`

- 参数：
  - seed : `Integer`  
    假种子的值
- 返回值：无

> 注意：
> 多次设置假种子以最后设置的那一个生效

<br>

## 获取存档名

通过此函数，获取存档名

`GMLib_Server.getLevelName()`

- 返回值：`String`
  存档名

<br>

## 修改存档名

通过此函数，可以修改存档名称

`GMLib_Server.getLevelName(name)`

- 参数：
  - name : `String`  
    假种子的值
- 返回值：无

> 注意：
> 多次设置假种子以最后设置的那一个生效

<br>

## 注册/ability命令

通过此函数，可以在未开启教育版的情况下强制注册/ability命令。GMLIB如果已经开启教育版，则不会注册。

`GMLib_Server.registerAbilityCommand()`

- 返回值：无

> 注意：
> 请在插件初始化的时候就注册此命令

<br>

## 开启/关闭教育版

通过此函数，可以开启/关闭教育版功能。

`GMLib_Server.setEducationFeatureEnabled(enable)`
- 参数：
  - enable : `Boolean`  
    是否启用教育版

- 返回值：无

> 注意：
> 这不同于强开，此函数开关教育版后是直接修改存档设置，即使卸载插件依旧保留设置

<br>

## 强行启用Xbox成就

通过此函数，可以强行启用Xbox成就

`GMLib_Server.setEnableAchievement()`

- 返回值：无

> 注意：
> Xbox成就仅能在未启用作弊的情况下获取，此功能会禁用作弊。

<br>

<br>

## 强制信任皮肤

通过此函数，可以强制信任皮肤，服务器玩家可以看见他人自定义皮肤

`GMLib_Server.setForceTrustSkins()`

- 返回值：无

<br>

## 强制资源包双端共存

通过此函数，可以在强制使用服务器资源包的情况下，允许客户端叠加自己的资源包

`GMLib_Server.enableCoResourcePack()`

- 返回值：无

<br>