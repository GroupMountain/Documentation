# 主页

快去创建一个你的原生插件开发模板！
# [CPP 插件开发模板](https://github.com/GroupMountain/GMLIB-Plugin-Template)

## 如何在 GMLIB-Plugin-Template 中使用 SDK？
CPP文档大概只需要告诉有什么

请在你的插件项目根目录中输入指令
```shell
git clone https://github.com/GroupMountain/SDK-GMLIB
```

# LSE 开发
### 导入API
- 导出需要的命名空间，如下列导出的命名空间为 `GMLib_ModAPI`
- 解析： `ll.import("需要导出的命名空间", "funtion_name")` 导入，其中 `funtion_name` 应替换为对应的导入函数。

示例：
```javascript
const GMLib_Mod = {   
    //导入命名空间GMLib_ModAPI 以及对应的函数->注册工作台有序合成配方                  
    registerShapedRecipe:ll.import("GMLib_ModAPI", "registerShapedRecipe"),
    //导入命名空间GMLib_ModAPI 以及对应的函数->注册工作台无序合成配方                  
    registerShapelessRecipe:ll.import("GMLib_ModAPI", "registerShapelessRecipe")
};
//注册工作台有序合成配方
GMLib_Mod.registerShapedRecipe("groupmountain:reinforced_deepslate_recipe", ["ABA", "BBB", "ABA"], ["minecraft:echo_shard", "minecraft:deepslate"], "minecraft:reinforced_deepslate", 1, "AlwaysUnlocked");
//注册工作台无序合成配方
GMLib_Mod.registerShapelessRecipe("groupmountain:quartz_recipe", ["minecraft:quartz_block"], "minecraft:quartz", 9, "AlwaysUnlocked");
```
