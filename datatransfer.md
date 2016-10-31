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

