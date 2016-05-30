# Excel配置

---

## 节点说明

```
<output ...>
  <varmarkers>
    <varmarker name="" value="" />
    ...
  </varmarkers>
  <arraymarkers>
    <arraymarker name="" split="," value="" />
    ...
  </datasetsqls>
  <datatablemarkers>
    <datatablemarker name="" conn="" sql="" />
    ...
  </datatablemarker>
</output>
```

 - `varmarkers/varmarker`: 模板文件中单一变量对应的配置
 - `arraymarkers/arraymarker`: 模板文件中数组变量对应的配置
 - `datatablemarkers/datatablemarker`: 模板文件中表格数据对应的配置

---


## 单一变量配置

### 模板配置

在Excel的单元格中输入`&=$name`即可，其中的name为变量值，即在节点中配置的name值

### 节点配置

`varmarkers`下配置一个或多个`varmaker`节点，每个`varmarker`节点配置一个单一变量名和变量值

| 属性名称 | 默认值 | 属性说明 |
| ------- | ------ | ------- |
| name | 必填 | 单一变量名，对应模板中配置的`&=$name` |
| value | 必填 | 单一变量值，可以内嵌入数据源中的参数，以`${字段名}`的方式可以将数据源中对应的字段值替换到变量中 |

---


## 数组变量配置

### 模板配置

与单一变量配置相同，在单元格中输入`&=$name`即可，然后会将数组变量中的每一项依次向下填充，每一项一个单元格，在同一列

### 节点配置

`arraymarkers`下可以配置多个`arraymarker`节点，每个节点配置一个变量名和变量值，另外配置分隔符将变量值中的字符串分割成数组，同样可以在变量值中使用参数`${字段名}`格式化

| 属性名称 | 默认值 | 属性说明 |
| ------- | ------ | ------- |
| name | 必填 | 数组变量名，对应模板中配置的`&=$name` |
| split | `,` | 分隔符，用于将`value`值分割为数组 |
| value | 必填 | 数组变量值，可以内嵌入数据源中的参数，以`${字段名}`的方式可以将数据源中对应的字段值替换到变量中 |

---


## 表格配置

### 模板配置

同样是在模板中添加标识符，不过这里的标识符和变量的标识符不太一样，形如`&=[数据源].[字段名]`，其中的中括号`[`和`]`可以选择不加，`数据源`指节点配置中的`name`，`字段名`是指数据源中表格的列名

### 节点配置

| 属性名称 | 默认值 | 属性说明 |
| ------- | ------ | ------- |
| name | 必填 | 表格名称，对应模板中配置的`数据源` |
| sql | 必填 | 获取数据所用的sql语句名称，用SQLGetter.GetSqlByAttr方法获取具体的SQL语句 |
| conn | `conn` | 数据库连接字符串名称，指在Web.config或者App.config文件中配置的连接字符串名称，**默认值为从`output`节点中继承来的`conn`属性** |



