# 悬浮字API    
- 使用 悬浮字类 需要导入StaticFloatingText 或 DynamicFloatingText 模块    
- StaticFloatingText 静态悬浮类    
- DynamicFloatingText 动态悬浮字类    
# 导入示例：    
```javascript    
const { StaticFloatingText, DynamicFloatingText } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');    
```    
    
# 获取悬浮字    
### 创建静态悬浮字    
```javascript    
new StaticFloatingText(pos, text, papi = true)    
```    
- pos:`Pos`    
    生成坐标    
- text:`String`    
    显示文本    
- papi:`Boolean`    
    是否启用PAPI变量    
- 返回值类型：`StaticFloatingText`    
    
### 创建动态悬浮字    
```javascript    
new StaticFloatingText(pos,text, updateRate = 1, papi = true)    
```    
- pos:`Pos`    
    生成坐标    
- text:`String`    
    显示文本    
- updateRate:`Number`    
    更新频率    
- papi:`Boolean`    
    是否启用PAPI变量    
- 返回值类型：`StaticFloatingText`    
    
### 获取所有静态悬浮字    
- `StaticFloatingText.getAllFloatingTexts()`    
- 返回值类型：`Array<StaticFloatingText,StaticFloatingText,…>`    
    
### 获取所有动态悬浮字    
- `DynamicFloatingText.getAllFloatingTexts()`    
- 返回值类型：`Array<DynamicFloatingText,DynamicFloatingText,…>`    
    
### 通过runtimeId获取静态悬浮字    
- `StaticFloatingText.getFloatingText(runtimeId: Number)`    
- runtimeId : 悬浮字的mRuntimeId    
- 返回值类型：`StaticFloatingText` | `NULL`    
    
### 通过runtimeId获取动态悬浮字    
- `DynamicFloatingText.getFloatingText(runtimeId)`    
- runtimeId : 悬浮字的mRuntimeId    
- 返回值类型：`DynamicFloatingText` | `NULL`    
    
# 悬浮字对象-属性    
|   属性  |   含义  |   类型  |    
|:-------:|:-------:|:-------:|    
| ft.mPosition       | 悬浮字所在坐标    | FloatPos |    
| ft.mText           | 悬浮字显示文本    | String   |    
| ft.mPlaceholderAPI | 是否启用PAPI变量  | Boolean  |    
| ft.mRuntimeId      | 实体的runtimeId   | Number   |    
    
# 悬浮字通用函数    
### 给单个玩家发送悬浮字    
- `ft.sendToClient(player)`    
- player: `Player`    
    要发送的玩家对象    
- 返回值：是否发送成功    
- 返回值类型：`Boolean`    
    
### 给所有玩家发送悬浮字    
- `ft.sendToClients()`    
- 返回值：是否发送成功    
- 返回值类型：`Boolean`    
    
### 删除单个玩家悬浮字    
- `ft.removeFromClient(player)`    
- player: `Player`    
    要发送的玩家对象    
- 返回值：是否删除成功    
- 返回值类型：`Boolean`    
    
### 删除所有玩家悬浮字    
- `ft.removeFromClients()`    
- 返回值：是否删除成功    
- 返回值类型：`Boolean`    
    
### 更新单个玩家悬浮字    
- `ft.updateClient(player)`    
- player: `Player`    
    要发送的玩家对象    
- 返回值：是否更新成功    
- 返回值类型：`Boolean`    
    
### 更新所有玩家悬浮字    
- `ft.updateClients()`    
- 返回值：是否更新成功    
- 返回值类型：`Boolean`    
    
### 获取悬浮字实体的runtimeId    
- `ft.getRuntimeId()`    
- 返回值：实体的runtimeId    
- 返回值类型：`Number`    
    
### 获取悬浮字显示的文本    
- `ft.getText()`    
- 返回值：显示的文本    
- 返回值类型：`String`    
    
### 设置悬浮字显示的文本    
- `ft.setText(newText)`    
- newText: `String`    
    要显示的文本    
- 返回值：是否设置成功    
- 返回值：`Boolean`    
    
### 更新悬浮字    
- `ft.update()`    
- 返回值：是否更新成功    
- 返回值类型：`Boolean`    
    
### 更新悬浮字文本    
- `ft.updateText(newText)`    
- newText: `String`    
    要显示的文本    
- 返回值：是否更新成功    
- 返回值类型：`Boolean`    
    
### 获取悬浮字坐标    
- `ft.getPos()`    
- 返回值：悬浮字的坐标    
- 返回值类型：`FloatPos`    
    
### 删除悬浮字    
- `ft.destroy()`    
- 返回值：是否删除成功    
- 返回值类型：`Boolean`    
    
### 是否为动态悬浮字    
- `ft.isDynamic()`    
- 返回值类型：`Boolean`    
    
# 动态悬浮字拥有函数    
### 获取更新频率    
- `ft.getUpdateRate()`    
- 返回值：更新频率    
- 返回值类型：`Number`    
    
### 设置更新频率    
- `ft.setUpdateRate(updateRate = 1)`    
- updateRate:`Number`    
    要修改的更新频率    
- 返回值：更新频率    
- 返回值类型：`Number`    
    
### 开始更新悬浮字    
- `ft.startUpdate()`    
- 返回值：是否开始成功    
- 返回值类型：`Boolean`    
    
### 停止更新悬浮字    
- `ft.stopUpdate()`    
- 返回值：是否停止成功    
- 返回值类型：`Boolean`