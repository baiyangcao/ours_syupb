# Service配置

## 节点说明

```
<output type="service" ... >
  <service name=""
           location=""
           method="GET"
           timeout="100000">
    <parameter name="" valuetype="" type="" />
  </service>
</output>
```

### `service`节点配置

`service`节点配置请求服务地址、方法、超时时间等

| 属性名称 | 默认值 | 属性说明 |
| ------- | ------ | ------- |
| name | `null` | 服务名称，用于在日志中标识服务名 |
| location | 必填 | 调用服务的地址 |
| method | `GET` | 请求方式，`GET`或`POST` |
| timeout | `100000` | 请求超时时间 |

### `parameter`节点配置

`parameter`节点配置发起请求时的请求参数，若请求为`method="GET"`则将请求参数作为URL参数拼接在`location`中，若为`method="POST"`则将请求参数作为`RequestBody`发送  

| 属性名称 | 默认值 | 属性说明 |
| ------- | ----- | -------- |
| name | `null` | 参数名称 |
| valuetype | `raw` | 参数类型，可取`raw`或`sql`，当
