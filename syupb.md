# SYUPB

本文主要讲述 SYUPB 相关的乱七八糟的配置选项

## 坐标导入配置

坐标导入作为一个单独页面使用，
在后台配置中为相应的案件配置对应的坐标导入按钮，
然后进行如下配置即可。

### 导入图层配置

坐标导入的图层参数配置位于 12/13 图形库，执行如下语句：

```
select 参数 from A00GIS_图形模块运行参数表 where 参数ID = '60201'
```

其中参数为 blob 类型的 xml 数据，在其中添加对应事项和图层的配置即可，如下：

```
<hbyd>划拨用地</hbyd>
```

表示 `hbyd` 事项坐标导入对应的图层为 `划拨用地`

### 导入属性配置

坐标导入的图形属性，在导入时一同导入，
具体的配置文件为 `D:\syupb\BPObject\Resource\CoorImportAttr.xml` ，
文件中用于配置导入时获取图形属性所用的 SQL 语句，
每一个 query 节点对应一个事项的 SQL 语句，属性如下：

 属性名称 | 说明 
 -------- | -------
 ProcAb | 案件编码，如：`hbyd`；可以使用正则表达式匹配，如 `.*` 表示匹配所有
 CaseType | 案件事项，如：`划拨用地`；可以使用这则表达式匹配
 ParentPage | 调用坐标导入页面的父页面名称，现可取： GeoTransactCase.aspx （业务审批）和 ResultCase.aspx （数据汇交）

> **注：** 这里会自上而下的遍历配置，并且取匹配到的第一个 query 配置，
> 故在配置的时候，通配的配置 `.*` 应该放在同类配置的最后面。

如，要在业务审批中划拨用地事项的页面上配置坐标导入功能，做如下配置：

```
<query ProcAb="hbyd" CaseType="划拨用地" ParentPage="GeoTransactCase.aspx">
    SELECT '{0}' 案件编号, 'HBYD' AS CaseCode, '划拨用地' AS CaseName, '{1}' AS UserID
</query>
```

上述中配置的 SQL 语句，获取的结果对应的列名为导入图层对应的字段名，
并且在执行查询时会注入两个变量， `{0} -> InstanceID`,`{1} -> UserOID`