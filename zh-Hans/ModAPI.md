## Mod API

- `Mod API` 提供更多了行为包的交互与补充API。
- 行为包目前要实现复杂的功能，需要很多曲线救国的方法，包括大量的mcfunction在tick.json里面运行，导致性能低下。
- 我们希望开发适用于BDS服务端的Mod，主要通过Addons接口的json接口，使用正常的数据驱动定义文件和`Molang`来实现基本功能，而复杂的功能交由LL进行实现，而非通过mcfunction和scripts。
- 开发适用于BDS的Mod应分为两部分，数据驱动行为包和插件功能。
> 由于模组开发复杂性和考虑性能问题，大型模组建议使用原生插件。

### 导入API

- `Mod API` 的导出命名空间为 `GMLib_ModAPI`
- 下文提到的函数名则为导出函数名。
- 以LLSE-js插件为例，使用 `ll.import("GMLib_ModAPI", "funtion_name")` 导入，其中 `funtion_name` 应替换为对应的导入函数。
- 你可以参考以下实例：
```javascript
const GMLib_Mod = {   
    //导入API                   
    registerShapedRecipe:ll.import("GMLib_ModAPI", "registerShapedRecipe"),
    registerShapelessRecipe:ll.import("GMLib_ModAPI", "registerShapelessRecipe")
};
//注册工作台有序合成配方
GMLib_Mod.registerShapedRecipe("groupmountain:reinforced_deepslate_recipe", ["ABA", "BBB", "ABA"], ["minecraft:echo_shard", "minecraft:deepslate"], "minecraft:reinforced_deepslate", 1, "AlwaysUnlocked");
//注册工作台无序合成配方
GMLib_Mod.registerShapelessRecipe("groupmountain:quartz_recipe", ["minecraft:quartz_block"], "minecraft:quartz", 9, "AlwaysUnlocked");
```
<br/>

- 为了方便介绍，以下文档均假定用上文中方式进行导入。
- 假定使用的导入函数名是和 `GMLIB` 导出的函数名相同的。

#### 注册实验性玩法依赖项

通过此函数，注册Mod所需的实验性玩法依赖，GMLIB会根据依赖项自动打开实验性玩法

`GMLib_Mod.registerExperimentsRequire(experimentId)`

- 参数：
  - experimentId : `Integer`  
    实验性玩法的ID
- 返回值：无

<br>

> 注意：
> 注册依赖项应在插件加载时就注册！

#### 获取实验性玩法启用情况

通过此函数，注册Mod所需的实验性玩法依赖，GMLIB会根据依赖项自动打开实验性玩法

`GMLib_Mod.getExperimentEnabled(experimentId)`

- 参数：
  - experimentId : `Integer`  
    实验性玩法的ID
- 返回值：实验性玩法是否启用
- 返回值类型： `Boolean`

> 注意：
> 获取实验性玩法应在 "onServerStarted" 之后获取

<br>

#### 修改实验性玩法

通过此函数，注册Mod所需的实验性玩法依赖，GMLIB会根据依赖项自动打开实验性玩法

`GMLib_Mod.getExperimentEnabled(experimentId, enabled)`

- 参数：
  - experimentId : `Integer`  
    实验性玩法的ID
  - enabled : `Boolean`  
    是否启用
- 返回值：无

> 注意：
> 修改实验性玩法应在 "onServerStarted" 之后修改

<br>

#### 实验性玩法ID表（1.20.30）
| 实验性名称           | ID  |
| ------------------- | --- |
| 假日创造者功能       | 6   |
| 自定义生物群系       | 7   |
| 即将推出的创作者功能  | 8  | 
| 测试版 API           | 9  | 
| Molang 功能         | 10  | 
| 实验相机            | 12  | 
| 村民交易再平衡       | 15  | 

> 注意：
> 修改实验性玩法ID每个版本均有修改，请注意版本时效性

#### 修改实验性玩法

通过此函数，注册Mod所需的实验性玩法依赖，GMLIB会根据依赖项自动打开实验性玩法

`GMLib_Mod.getExperimentEnabled(experimentId, enabled)`

- 参数：
  - experimentId : `Integer`  
    实验性玩法的ID
  - enabled : `Boolean`  
    是否启用
- 返回值：无

> 注意：
> 修改实验性玩法应在 "onServerStarted" 之后修改

<br>

#### 修复自定义亡灵生物特性

通过此函数，启用亡灵生物修复功能

`GMLib_Mod.setFixUndeadMobs()`

- 返回值：无

> 由于Addons API的限制，将生物的family添加undead之后，生物仅仅只是可以受到亡灵杀手的额外伤害。
> 但是亡灵生物还应该免疫再生和剧毒效果，伤害药水对其治疗，治疗药水对其伤害，执行此函数后修复此问题。

<br>

#### 启用错误方块移除

通过此函数，启用自动移除未知方块的功能

`GMLib_Mod.setUnknownBlockCleaner()`

- 返回值：无

> 删除带有自定义方块的Addon之后会残留未知方块。
> 执行此函数后启用未知方块移除，在区块开始加载时移除区块内全部未知方块。

<br>

#### 注册盔甲韧性

通过此函数，注册自定义护甲的盔甲韧性

`GMLib_Mod.setArmorToughness(itemType, value)`

- 参数：
  - itemType : `String`  
    物品的ID
  - value : `Number`  
    盔甲韧性
- 返回值：无

> 由于Addons API的限制，无法给自定义护甲注册盔甲韧性属性。
> 此函数定义一个物品的盔甲韧性。如果应用给原版物品，会覆盖原版物品盔甲韧性值。

<br>

#### 注册抗火物品

通过此函数，注册抗火物品

`GMLib_Mod.addFireImmuneItem(itemType)`

- 参数：
  - itemType : `String`  
    物品的ID
- 返回值：无

> 由于Addons API的限制，无法给自定义物品抗火属性。
> 此函数定义一个物品抗火后，物品掉落物形式和下界合金一样，不会被火焰摧毁。

<br>

#### 注册防爆物品

通过此函数，注册防爆物品

`GMLib_Mod.addExplosionImmuneItem(itemType)`

- 参数：
  - itemType : `String`  
    物品的ID
- 返回值：无

> 由于Addons API的限制，无法给自定义物品防爆属性。
> 此函数定义一个物品防爆后，物品掉落物形式和下界之星一样，不会被爆炸摧毁。

<br>

#### 注册工作台有序合成表

通过此函数，注册工作台有序合成表

`GMLib_Mod.registerShapedRecipe(recipe_id, patten, ingredients, result, count, unlock)`

- 参数：
  - recipe_id : `String`  
    合成表的ID，不可重复。格式为 `命名空间：配方名称`， 例如 `groupmountain:quartz_recipe`
  - patten : `Array[String]`  
    摆放方式，请依次使用字母 A,B,C,D,E 等。 格式形如 `["AAB", "A B", " A "]`
  - ingredients : `Array[String]`  
    数组，写合成材料的ID
  - result : `String`  
    合成产品的ID
  - count : `Integer`  
    合成产品数量
  - unlock : `String`  
    解锁配方所需的物品ID
- 返回值：无

> 注意
> 解锁配方的物品ID处也可以填 "AlwaysUnlocked", "PlayerHasManyItems", "PlayerInWater", "None" 几个参数
<br>

#### 注册工作台无序合成表

通过此函数，注册工作台有序合成表

`GMLib_Mod.registerShapelessRecipe(recipe_id, ingredients, result, count, unlock)`

- 参数：
  - recipe_id : `String`  
    合成表的ID，不可重复。格式为 `命名空间：配方名称`， 例如 `groupmountain:quartz_recipe`
  - ingredients : `Array[String]`  
    数组，写合成材料的ID
  - result : `String`  
    合成产品的ID
  - count : `Integer`  
    合成产品数量
  - unlock : `String`  
    解锁配方所需的物品ID
- 返回值：无

<br>

#### 注册切石机合成表

通过此函数，注册切石机合成表

`GMLib_Mod.registerStoneCutterRecipe(recipe_id, input, input_data, output, output_data, count)`

- 参数：
  - recipe_id : `String`  
    合成表的ID，不可重复。格式为 `命名空间：配方名称`， 例如 `groupmountain:quartz_recipe`
  - input : `String`  
    输入材料的ID
  - input_data : `Integer`  
    输入材料的数据组
  - output : `String`  
    输出材料的ID
  - output_data : `Integer`  
    输出材料的数据组
  - count : `Integer`  
    输出材料的数量
- 返回值：无

<br>

#### 注册熔炉/营火合成表

通过此函数，注册熔炉/营火合成表

`GMLib_Mod.registerFurnaceRecipe(recipe_id, input, output, tags)`

- 参数：
  - recipe_id : `String`  
    合成表的ID，不可重复。格式为 `命名空间：配方名称`， 例如 `groupmountain:quartz_recipe`
  - input : `String`  
    输入材料的ID
  - output : `String`  
    输出材料的ID
  - tags : `Array[String]`  
    可使用熔炉/营火的tag，可填 `"furnace", "blast_furnace", "smoker", "campfire", "soul_campfire"`
- 返回值：无

<br>

#### 注册药水酿造合成表

通过此函数，注册药水酿造合成表

`GMLib_Mod.registerBrewingMixRecipe(recipe_id, input, output, reagent)`

- 参数：
  - recipe_id : `String`  
    合成表的ID，不可重复。格式为 `命名空间：配方名称`， 例如 `groupmountain:quartz_recipe`
  - input : `String`  
    输入材料的ID
  - output : `String`  
    输出材料的ID
  - reagent : `String`  
    酿造原料的ID
- 返回值：无

<br>
