# 合成表API
使用Recipes类需要导入Recipes模块
导入示例：
[JavaScript]
```javascript
const { Recipes } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');
```

> 注意：
> 若无特殊说明，注册合成表的API需要在 `onServerStarted` 之后调用。

### 注册无序合成表

`Recipes.registerShapelessRecipe(
recipe_id: string,
ingredients: array<string>,
result: string,
count: int,
unlock: string
)`

参数:

- recipe_id: 合成表的唯一标识符。
- ingredients: 合成原料，所需合成原料的物品id。
- result: 合成结果。
- count: 合成结果的数量。
- unlock: 解锁条件（可填"AlwaysUnlocked", "PlayerHasManyItems", "PlayerInWater", "None"或者解锁需要的物品ID）

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerShapelessRecipe("groupmountain:quartz_recipe", ["minecraft:quartz_block"], "minecraft:quartz", 9, "AlwaysUnlocked");
```

### 注册有序合成表

`Recipes.registerShapedRecipe(
recipe_id: string,
shape: array<string>,
ingredients: array<string>,
result: string,
count: int,
unlock: string
)`

参数:

- recipe_id: 合成表的唯一标识符。
- shape: 合成表摆放方式，数组元素为字符串。
- ingredients: 材料数组，形如 `["ABA", "BBB", "ABA"]`。
- result: 合成结果。
- count: 合成结果的数量。
- unlock: 解锁条件，例如 "AlwaysUnlocked"。

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerShapedRecipe("groupmountain:reinforced_deepslate_recipe", ["ABA", "BBB", "ABA"], ["minecraft:echo_shard", "minecraft:deepslate"], "minecraft:reinforced_deepslate", 1, "AlwaysUnlocked");
```

### 注册熔炉合成表

`Recipes.registerFurnaceRecipe(
recipe_id: string,
input: string,
output: string,
tags: array<string>
)`

参数:

- recipe_id : 合成表的唯一标识符。
- input : 输入材料。
- output : 合成结果。
- tags (array<string>): 材料的标签数组。(支持"furnace", "blast_furnace", "smoker", "campfire", "soul_campfire")

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerFurnaceRecipe("recipe_id", "input", "output", ["tag1", "tag2"])
```

### 注册酿造混合表

`Recipes.registerBrewingMixRecipe(
recipe_id: string,
input: string,
output: string,
reagent: string
)`

参数:

- recipe_id : 合成表的唯一标识符。
- input : 输入物品（必须是原版药水物品id）。
- output : 合成结果（必须是原版药水物品id）。
- reagent : 酿造物品。

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerBrewingMixRecipe("recipe_id", "input", "output", "reagent")
```

### 注册酿造容器表

`Recipes.registerBrewingContainerRecipe(
recipe_id: string,
input: string（可以是任意物品）,
output: string（可以是任意物品）,
reagent: string
)`

参数:

- recipe_id : 合成表的唯一标识符。
- input : 输入物品。
- output : 合成结果。
- reagent : 酿造物品。

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerBrewingContainerRecipe("recipe_id", "input", "output", "reagent")
```

### 注册锻造配方合成表

`Recipes.registerSmithingTransformRecipe(
recipe_id: string,
smithing_template: string,
base: string,
addition: string,
result: string
)`

参数:

- recipe_id : 合成表的唯一标识符。
- smithing_template : 锻造模板。
- base : 基础物品。
- addition : 升级材料。
- result : 合成结果。

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerSmithingTransformRecipe("recipe_id", "template", "base", "addition", "result")
```

### 注册锻造纹饰合成表

`Recipes.registerSmithingTrimRecipe(
recipe_id: string,
smithing_template: string,
base: string,
addition: string
)`

参数:

- recipe_id : 合成表的唯一标识符。
- smithing_template : 锻造模板。
- base : 基础物品。
- addition : 纹饰材料。

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerSmithingTrimRecipe("recipe_id", "template", "base", "addition")
```

### 注册切石机合成表

`Recipes.registerStoneCutterRecipe(
recipe_id: string,
input: string,
input_data: int,
output: string,
output_data: int,
output_count: int
)`

参数:

- recipe_id : 合成表的唯一标识符。
- input : 输入物品。
- input_data: 输入物品的额外数据。
- output : 合成结果。
- output_data: 合成结果的额外数据。
- output_count: 合成结果的数量。

返回值：Boolean (合成表是否注册成功)

[JavaScript]
```JavaScript
Recipes.registerStoneCutterRecipe("recipe_id", "input", 0, "output", 0, 1)
```