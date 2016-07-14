

# Service配置

## 节点说明

```
<output type="service" ... >
  <service name=""
           location=""
           method="GET"
           timeout="100000">
    <parameter name="" valuetype="" type="" value="" sqlname="" />
  </service>
</output>
```

### `service`节点配置

`service`节点配置请求服务地址、方法、超时时间等

| 属性名称 | 默认值 | 属性说明 |
| :--- | :--- | :--- |
| name | `null` | 服务名称，用于在日志中标识服务名 |
| location | 必填 | 调用服务的地址 |
| method | `GET` | 请求方式，`GET`或`POST` |
| timeout | `100000` | 请求超时时间 |

### `parameter`节点配置

`parameter`节点配置发起请求时的请求参数，若请求为`method="GET"`则将请求参数作为URL参数拼接在`location`中，若为`method="POST"`则将请求参数作为`RequestBody`发送

| 属性名称 | 默认值 | 属性说明 |
| :--- | :--- | :--- |
| name | `null` | 参数名称 |
| valuetype | `raw` | 参数类型，可取`raw`或`sql`，当为`raw`时直接取`value`属性值作为参数值；当为`sql`时取`value`值作为SQL语句名去查询数据，取查询结果中的第一列为参数值，若结果有多行则用`,`拼接结果 |
| value | `valuetype=raw`必填 | 参数值，可以使用格式化参数`${field}` |
| sqlname | `valuetype=sql`必填 | SQL语句名称 |

