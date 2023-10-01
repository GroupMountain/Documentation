## Server API

`Server API` 提供更多了插件开发所需的API

- `Server API` 的导出命名空间为 `GMLib_ServerAPI`

#### 悬浮字相关API

通过此API，注册优雅的仅发包悬浮字，GMLIB会通过假数据包生成仅客户端看得见的悬浮字，不会对服务端生物ai造成任何影响

`GMLib_Server.sendAddFloatingTextPacket(text,pos,dimid)`

- 参数：
  - text : `String`  
    悬浮字的展示内容
  - pos : `Vec3`  
    悬浮字的展示位置
  - dimid : `Integer`
    悬浮字的展示维度
- 返回值：`Integer`
  悬浮字的id

> 注意：
> 创建悬浮字应在 "onServerStarted" 之后开始

通过此函数，你可以移除一个先前创建的悬浮字
`GMLib_Server.sendDeleteFloatingTextPacket(id)`

- 参数：
  - id : `Integer`
    悬浮字的id
- 返回值:无

通过此函数，你可以修改先前创建的悬浮字内容
`GMLib_Server.sendUpdateFloatingTextPacket(id,newtext)`

- 参数：
  - newtext : `String`  
    悬浮字的更新展示内容
  - id : `Integer`
    悬浮字的id
- 返回值：无
