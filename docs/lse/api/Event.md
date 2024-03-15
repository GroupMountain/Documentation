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