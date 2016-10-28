# 成果管理系统

## 抽取配置说明

### 命令行参数

抽取工具CreateProjectTree可以执行三个任务：项目树抽取，重点项目抽取，生成全文索引；默认情况下执行全部的三个项目，也可以通过命令行指定执行一个任务（需求sy/syams#2），p/project代表项目树抽取任务，k/key代表重点项目抽取任务，i/index代表生成全文索引任务，如：

```
// 仅执行项目树抽取任务
C:\> CreateProjectTree.exe project
```

### Config.xml文件配置

root/item节点属性如下：
 1. **sqlconn**: ctype和ztype分别代表项目树抽取和重点项目抽取配置项
 2. **ctype**: 抽取类型，取值如下
    - all: 全部抽取，配置此值时LastDate属性无效，抽取全部项目
    - part: 增量抽取，抽取录入时间在LastDate到当前时间间的项目
    - case: 仅对于项目树抽取可用，抽取指定项目，具体见value配置
 3. **LastDate**: 上次抽结束时间，**每次抽取后自动更新为当前时间**
 4. **value**: 当ctype为case时有效，json字符串，形式如下
```
    *{[TYPECODE]:[INSTANCEIDS],...}*
```

    其中*[TYPECODE]*代表要抽取的事项，可取值为：  
       type_ydys   type_pcbp   type_tdcb   type_tdjy  
       type_tddj   type_tdgy   xz          yd         
       jy          jf          js          sf  
       ss  
      *[INSTANCEIDS]*代表要抽取项目的InstanceID，  
           多个用英文逗号","隔开，若为空则按照LastDate查询增量的项目  
   例如，如下抽取了一个供地项目和所有的选址项目  
```
   {type_tdgy:7185EB8F-995A-4D67-8BF0-53958D783710,xz:}
```