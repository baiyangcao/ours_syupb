# 数据抽取工具-DataTransfer

## 概述

数据抽取工具（DataTransfer）是用来将业务审批数据库（syupb）数据抽取到数据汇交库（syds）的定时抽取工具，运行在应用服务器10上，每天晚上执行抽取，抽取当天办结的各个事项的数据。  
  
最初只存在从业务审批抽取数据到数据汇交，省厅数据抽取到数据汇交功能，后又添加地价决策数据、综合监管数据、法院查询网数据抽取功能。  
  
## 目录结构

```
DataTransfer/
  |- Business/
  |    |- CGSJ/
  |    |- DJJC/
  |    |- FYCKW/
  |    |- STSJ/
  |    |- ZHJG/
  |    
  |- Common/
  |- Data/
  |    |- SyConfig.xml
  |
  |- DataBase/
  |- Web Reference/
```

抽取的各个表的业务逻辑在`Business`目录下，其下对应的目录为对应的不同库之间的抽取关系：

 - `CGSJ` —— 业务审批库（syupb）抽取到成果库（syds）的业务类，也包含部分抽取的综合监管的逻辑
 - `DJJC` —— 业务审批库（syupb）抽取到地价决策库（sydjjc）的业务类
 - `FYCKW` —— 业务审批库（syupb）抽取到法院查询库（fyckw，Oracle数据库）的业务类，其实也就只有一个土地数据抽取的业务类，抽取相关登记、抵押、查封的数据
 - `STSJ` —— 省厅数据抽取到成果库（syds）的业务类，其中省厅数据通过Web Service 接口获取，`Data/SyConfig.xml`配置文件中配置了接口返回字段与数据库字段的对应关系
 - `ZHJG` —— 成果库（syds）抽取到综合监管库（geobuns，Oracle数据库）的业务类


