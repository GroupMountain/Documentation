# 安装前置库
- 如需在LSE里面使用 `GMLIB` 的功能，首先需要导入 `GMLIB` 的库。
- 请确保你已经正确安装了 `GMLIB` 和 `GMLIB-LegacyRemoteCallApi`，并检查目录 `./plugins/GMLIB-LegacyRemoteCallApi/lib/` 目录下存在以下文件：

> GMLIB_API-JS.js

> EventAPI-JS.js

> BEPlaceholderAPI-JS.js

- 目前仅支持 QuickJs 和 NodeJs，其它语言暂未提供快捷导入方式，可自行使用 `RemoteCall` 接口导入

> 注意：
> 若无特殊说明，一切API均需要在 `onServerStarted` 之后调用


# 导入你所需要的类

### 目前 `GMLIB-LegacyRemoteCallApi` 提供了以下类
- PAPI
- Event
- StaticFloatingText
- DynamicFloatingText
- Minecraft
- Recipes
- Experiments
- GMLIB

### 你可以使用以下方式进行导入
- `const { PAPI } = require('./GMLIB-LegacyRemoteCallApi/lib/BEPlaceholderAPI-JS');`
- `const { Event } = require('./GMLIB-LegacyRemoteCallApi/lib/EventAPI-JS');`
- `const { StaticFloatingText } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');`
- `const { DynamicFloatingText } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');`
- `const { Minecraft } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');`
- `const { Recipes } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');`
- `const { Experiments } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');`
- `const { GMLIB } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');`