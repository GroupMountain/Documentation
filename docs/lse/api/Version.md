# 版本信息API   
   
使用Version类需要导入Version模块   
导入示例：   
```javascript   
const { Version } = require('./GMLIB-LegacyRemoteCallApi/lib/GMLIB_API-JS');   
```   
   
# 关于插件版本   
### GMLIB和LRCA版本获取   
```javascript   
/** 获取GMLIB-LegacyRemoteCallApi版本 */   
Version.getLrcaVersion()   
/** 获取GMLIB版本 */   
Version.getGmlibVersion()   
```   
- 返回值类型：`Version`   
   
### 判断LRCA是否大于或等于某版本   
```javascript   
Version.isPluginVersionMatched(version)   
```   
- version：`Version`   
    要判断的版本   
- 返回值：是否大于或等于传入的版本   
- 返回值类型：`Boolean`   
   
# Version类创建   
### 直接创建   
```javascript   
new Version(major, minor, patch)   
```   
- major：`Number`   
    主版本号   
- minor：`Number`   
    次版本号   
- patch：`Number`   
    修订版本号   
   
### 从版本字符串转换   
```javascript   
Version.fromString(version)   
```   
- version：`String`   
    版本字符串   
    - 如 v1.0.0 , 1.0.0   
- 返回值类型：`Version`   
   
### 从版本数组转换   
```javascript   
Version.fromArray(version)   
```   
- version：`[Number,Number,Number]`   
    版本数组   
    - 如 [1,0,0] , [1,0,0]   
- 返回值类型：`Version`   
   
# Version拥有属性   
|   属性  |   含义  |   类型  |   
|:-------:|:-------:|:-------:|   
| v.mMajor | 主版本号   | Number |   
| v.mMinor | 次版本号   | Number |   
| v.mPatch | 修订版本号 | Number |   
   
# Version拥有函数   
### Version类转字符串   
```javascript   
Version.toString(prefix = true)   
```   
- prefix：`Boolean`   
    是否附带“v”前缀   
- 返回值类型：`String`   
   
### Version类转数组   
```javascript   
Version.toArray()   
```   
- 返回值类型：`Array<Number,Number,Number>`   
   
### 获取Version的值(用来比较版本)   
```javascript   
Version.valueOf()   
```   
- 返回值类型：`Number`