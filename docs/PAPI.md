# BEPlaceholderAPI
- 在 LL2 的独立版 `BEPlaceholderAPI` 插件已经不会再更新，原 `BEPlaceholderAPI` 已和 `GMLIB` 合并。
- 存在于 `GMLIB` 中的 `PlaceholderAPI` 相关接口均为 `BEPlaceholderAPI` 接口的官方迁移版本。

# API变化通知
- 为保留LSE插件兼容性，一切RemoteCall接口的函数的导出名和命名空间均没有变化。
- 但是现在注册和翻译玩家PAPI不再使用xuid，现在直接使用玩家对象。

# LSE插件适配与迁移
- 将require路径改为`const { PAPI } = require('./GMLIB-LegacyRemoteCallApi/lib/BEPlaceholderAPI-JS');`
- 将原来的关于玩家PAPI注册和翻译参数里面的xuid直接改为玩家对象。

# API接口
- 请参阅开发指南