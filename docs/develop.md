# 原生插件开发（C++）
- 导入静态库和头文件
往xmake.lua里面添加对应的库，并克隆SDK-GMLIB作为子模块。
> 这里直接建议使用我们提供的插件模板，一切工作均已就绪，无需手动操作。
> [CPP 插件开发模板](https://github.com/GroupMountain/GMLIB-Plugin-Template)
- 编写并测试你的插件
> API功能请参照命名。如有问题可在交流群交流。

# 脚本插件开发（LSE）
- `GMLIB` 本身并不提供脚本插件API，你需要安装扩展模块 `GMLIB-LegacyRemoteCallApi`
- 安装完前置模块后，正常创建插件并导入API

使用示例：
```javascript
const { Minecraft } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');
```
- 编写并测试你的插件