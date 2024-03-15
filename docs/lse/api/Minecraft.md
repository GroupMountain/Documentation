# 实验性内容API
使用Minecraft类需要导入Minecraft模块
导入示例：
```javascript
const { Minecraft } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');
```

> 注意：
> 若无特殊说明，实验性内容相关API需要在 `onServerStarted` 之后调用。

### 启用错误方块清理
启用后，GMLIB会在区块加载时清理未知方块。

`Minecraft.setUnknownBlockCleaner()`

[JavaScript]
```JavaScript
Minecraft.setUnknownBlockCleaner()
```

> 此API可在任意时间调用