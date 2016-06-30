# Q&A

## 局长退回案件在办箱丢件

> `Q:` 案件由分管局长（审定环节）提交到局长手（批准环节），分管局长和局长都能看到这个件，但是局长将这个案件退回到分管局长手时，分管局长能够看到，但是局长的在办箱却没有案件了，流程也正常。。。  
>   
> `A:` 这个原因应该是审定环节没有配置对应的“扩展人”，因为在局长将案件退回到分管局长手时，局长对于当前环节来说，角色是扩展人，若是没有配置则没有对应的分配（AssignTask）记录，可以在`系统配置->工作流权限配置`中为相应的环节（审定）添加扩展人角色，再次退回案件，局长在办箱也可以看到相应的案件  

## 入库更新系统`Network I/O error`

> `Q:` 勘测院入库更新系统在进行数据检查时报错`Network I/O error`，而且在ArcCatalog 10.0中预览500地形图中的图层，来回切换，也会出现`Network I/O error[SDE.GDB_UserMetaData]`错误  
>   
> `A:` 这个是由于数据库里数据有问题导致的错误，将数据库里的要素类拷贝到本地GDB文件地理数据库中，执行ArcToolbox中`数据管理工具--要素--修复几何`工具对每一个图层进行修复，会删除要素类中有问题的数据，如：图形为空的数据等，之后再将修复完成的数据拷贝回数据库中即可
  
## 案件报建人、报建单位查询

> `Q:` 报建人、报建单位与案件`InstanceID`的关联关系是怎样的？怎样使用`InstanceID`获取到报建单位电话和报建人电话  
>   
> `A:` 关联关系如下：
> ```
> GeoGGFlowInstance b
>   on b.InstanceID = a.序号
> left join GeoGGProject c
>   on c.InstanceID = b.FolderID
> left join GeoGGProjBuildCo d
>   on d.InstanceID = b.FolderID
> left join GeoExterUnit e
>   on e.GeoExterUnitOID = d.GeoExterUnit_FKOID
> left join ApplyPersonInfo f
>   on f.GeoGGProYDBaseInfoTableOID = c.GeoGGProjectOID
> left join GeoPersonInfo g
>   on g.IDCard = f.IDCard
> ```



