# GMLIB文档

[![Build](https://img.shields.io/github/actions/workflow/status/GroupMountain/GMLIB/cmake_repo.yml?style=for-the-badge)](https://github.com/GroupMountain/GMLIB/actions)
[![Latest Tag](https://img.shields.io/github/v/tag/GroupMountain/GMLIB?label=LATEST%20TAG&style=for-the-badge)](https://github.com/GroupMountain/GMLIB/releases/latest)
[![Downloads@Latest](https://img.shields.io/github/downloads/GroupMountain/GMLIB/latest/total?style=for-the-badge)](https://github.com/GroupMountain/GMLIB/releases/latest)

## 什么是GMLIB？

**GMLIB**是一个用于**适用于 LiteLoaderBDS 插件加载器的插件开发前置库** 提供为开发者更多封装好的API。

👉[点击此处](https://github.com/GroupMountain/GMLIB/blob/main/README.md)👈 查看更详细的介绍。

## 如何安装和使用GMLIB作为前置开发插件？

#### 原生插件（`C++`）
1. 添加头文件
2. 添加动态库
3. 编写插件
> 当然在原生插件里面你也可以使用 `RemoteCall` 接口导入API。

#### 非原生插件
1. 使用 `RemoteCall` 接口导入你需要的API
2. 编写你的插件
- 以下为JavaScript的导入API和编写插件的示例
```javascript
const GMLib = {   
    //导入API                   
    registerShapedRecipe:ll.import("GMLib_ModAPI", "registerShapedRecipe"),
    registerShapelessRecipe:ll.import("GMLib_ModAPI", "registerShapelessRecipe")
};
//注册工作台有序合成配方
GMLib.registerShapedRecipe("groupmountain:reinforced_deepslate_recipe", ["ABA", "BBB", "ABA"], ["minecraft:echo_shard", "minecraft:deepslate"], "minecraft:reinforced_deepslate", 1, "AlwaysUnlocked");
//注册工作台无序合成配方
GMLib.registerShapelessRecipe("groupmountain:quartz_recipe", ["minecraft:quartz_block"], "minecraft:quartz", 9, "AlwaysUnlocked");
```
<br/>

## API文档
> 对于原生插件，可直接参考头文件中注释
> 此处提供非原生插件的API文档

- 👉[EventAPI](/EventAPI.md)👈 事件监听API。
- 👉[ServerAPI](/Server.md)👈 插件开发API。
- 👉[ModAPI](/ModAPI.md)👈 Mod开发API。

## 常见问题

👉[点击此处](/FAQ.md)👈 查看常见问题与解决方法。

## 如何参与GMLIB维护和开发？

1. 如果你发现了API存在问题或者希望有更多API加入，你可以在 `Github` 提交 `Issue`
2. 如果你发现了问题并且你知道如何修复，或者你希望添加新功能，你可以提交 `Pull Request`