# UCML工作流平台

## UCML更新基本流程

 1. 备份开发库(ucml_sys3)
 2. 到目标环境下还原开发库
 3. 修改UCML服务端（UCML_Srv）的配置
 4. 打开UCML客户端，连接服务端并设置目标数据库，数据库地址应该与服务端的开发库地址相同
 5. 导出工作流定义信息，报表定义信息等
 6. 更新WorkFlow.exe，DbLayer.dll，MoveConfig.xml等文件及相关代码
 7. 系统配置，登录系统设置流程相关的角色信息，工作流设置、工作流权限设置、工作流角色设置、工作流并联周期设置、证书编号设置及报表设置等

## 说明

本文档由张益达倾情提供，小生整编，阅前请默念三遍“感谢张益达欧巴”！！！