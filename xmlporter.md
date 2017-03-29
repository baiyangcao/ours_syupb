# 多规合一数据交互说明

## 基本字段要求

为与之前所定义的接口一致，此次进行交互的数据字段与之前定义的相同，
仅仅是将数据表中的每一条记录以 xml 的格式进行交互。

## 基本格式要求

数据以 xml 形式的方式交互，**但保存到文件中的 xml 数据需要
使用 base64 格式编码后存储**，并且，对于数据库中的附件数据，
将其二进制数据取出后，以 base64 编码的方式进行编码。

## 数据导入格式[新点提供]

导入数据的 xml 数据基本格式如下：

```xml
<root>
  <import key="dghy">
    <table name="ghjqzk.dbo.exfront_attach">
      <attachguid>84764f36-ff6e-4b11-b98a-01021b42bc68</attachguid>
      <attachname>高拍仪上传20170324095915</attachname>
      ...
    </table>
    ...
  </import>
</root>
```

 - 其中的根节点 `<root>`{.xml} 与 `<import key="dghy">`{.xml} 为固定格式节点
 - `<import key="dghy">`{.xml} 下为多个 `<table>`{.xml} 节点，每条记录对应一个 `<table name="">`{.xml} 节点，其中 `name` 属性为数据表的名称，**注：这里数据表名称需要加上数据库前缀 `ghjqzk.dbo.` **
 - `<table>`{.xml} 下为字段节点，每个字段节点以 `<fieldname>fieldvalue</fieldname>`{.xml} 的格式存储，
 **注：日期格式字段以 `yyyy-MM-dd hh:mm:ss` 形式存储，
 Image 格式数据（附件）以 base64 编码的字符串形式存储**。

### 数据导入样例

 - 编码前： 详情见附件 `import.xml`
 - 编码后： 详情见附件 `import.encoded.xml`

## 数据导出格式[吉奥提供]

数据导出与导入格式类似，只不过将 `<import>`{.xml} 节点转换为 
`<export>`{.xml} 节点，并且导出的 `<table>`{.xml} 节点中，
`name` 属性并没有数据库前缀 `ghjqzk.dbo`

### 数据导出样例

 - 编码前： 详情见附件 `export.xml`
 - 编码后： 详情见附件 `export.encoded.xml`