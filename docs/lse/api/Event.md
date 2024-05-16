# 事件API
使用Event类需要导入Event模块
导入示例：
```javascript
const { Event } = require('./GMLIB-LegacyRemoteCallApi/lib/EventAPI-JS');
```

# 使用方法
- 类似LSE自带事件使用方法。但是此处使用Event类

使用示例：
```javascript
Event.listen("onMobPick", (entity, itemEntity) => {
    if (entity.type == "minecraft:zombie" && itemEntity.toItem().type == "minecraft:netherite_sword") {
        return false;
    }
});
// 监听生物捡起物品，如果是僵尸捡起下界合金键，则拦截此事件。
```

# 事件列表

### "onMobPick" - 生物捡起物品
- 监听函数原型：  
`function(entity, itemEntity)`
- entity: `Entity`  
  捡起物品的生物  
- itemEntity: `Entity`  
  被捡起的掉落物实体  
- 拦截事件： 返回 `false`  

注意： 该事件仅会被生物触发，玩家捡起物品不触发。

### "onClientLogin" - 客户端登录事件
- 监听函数原型：  
`function(realName, uuid, serverXuid, clientXuid)`  
- realName: `String`  
  玩家真实名称  
- uuid: `String`  
  玩家的UUID  
- serverXuid: `String`  
  玩家服务端的XUID  
- clientXuid: `String`  
  玩家客户端的XUID  
- 拦截事件： 不可以拦截

### "onWeatherChange" - 天气改变事件事件
- 监听函数原型：  
`function(lightningLevel, rainLevel, lightningLastTick, lainingLastTick)`  
- lightningLevel: `Number`  
  雷暴天气等级  
- rainLevel: `Number`  
  雨天天气等级  
- lightningLastTick: `Number`  
  雷暴持续时间（刻）  
- rainingLastTick: `Number`  
  雨天持续时间  
- 拦截事件： 返回 `false`  

### "onItemTrySpawn" - 掉落物尝试生成  
- 监听函数原型：  
`function(item, pos, entity)`  
- item: `Item`  
  掉落物物品对象  
- pos: `FloatPos`  
  生成坐标  
- entity: `Entity`  
  掉落物实体对象  
- 拦截事件： 返回 `false`  

### "onItemSpawned" - 掉落物生成完毕
- 监听函数原型：  
`function(item, entity, pos, spawnerEntity)`  
- item: `Item`  
  掉落物物品对象  
- entity: `Entity`  
  掉落物物品对象  
- pos: `FloatPos`  
  生成坐标  
- spawnerEntity: `Entity`  
  生成掉落物的实体对象  
- 拦截事件： 不可以拦截  

### "onEntityChangeDim" - 实体切换维度
- 监听函数原型：  
`function(entity, dimid)`  
- entity: `Entity`  
  实体对象  
- dimid: `Number`  
  前往的维度ID  
- 拦截事件： 返回 `false`

### "onLeaveBed" - 玩家下床事件
- 监听函数原型：  
`function(player)`  
- player: `Player`  
  玩家对象  
- 拦截事件： 返回 `false`

### "onDeathMessage" - 触发死亡信息
- 监听函数原型：  
`function(deathMsgKey,deathMsgParams,entity)`  
- deathMsgKey: `String`   
  死亡信息键名，请自行使用I18nAPI翻译
- deathMsgParams: `String[]`   
  死亡信息参数
- entity: `Entity`   
  死亡的实体对象
- 拦截事件： 不可以拦截

### "onMobHurted" - 实体受伤后事件(包括玩家)
- 监听函数原型：  
`function(entity,source,damage,cause)`  
- entity: `Entity`   
  受伤的实体对象
- source: `Entity`   
  伤害来源实体对象   
  请注意：即使来源是null也会传递实体对象
- damage: `Number`   
  受到的伤害
  请注意：伤害是负的
- cause: `DamageCause`
  伤害原因
- 拦截事件： 不可以拦截

### "onEndermanTake" - 末影人搬起方块事件
- 监听函数原型：  
`function(entity)`  
- entity: `Entity`   
  实体对象
- 拦截事件： 返回`false`
