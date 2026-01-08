# Platform
## 平台简介
  本智能仓储管理系统（Warehouse Management System, WMS）是一种针对仓库管理流程进行优化和自动化的软件解决方案。
  适配多端：PC端、移动端、APP(安卓)。基于RuoYi-Vue-Plus框架打造多租户(sass)管理平台。

  | 业务菜单        | 主要功能                                                                                                               
  |-------------|-------------------------------------------------------------------------------------------------------------------
  | 仓库管理        | 仓库、库区、库位、容器位、货架
  | 物料管理        | 物料分类、物料档案、物料编码规则、物料属性、物料单位、精度单位
  | 出入库管理       | 出库、入库、调拨、库存初始化、解绑
  | 报表管理        | 单据明细、任务明细、作业记录明细
  | 统计报表管理        | 仓库即时库存、仓库实时库存、库区实时库存、库位实时库存、库位台账、库位明细
  | 盘点管理      | 盘点单据、盘点明细、盘点结果、盘盈盘亏
  | 策略管理        | 1.时间维度(先进先出,后进先出)、空间维度(高位优先、中位优先、低位优先)、库存维度(库存量多优先、库存量少优先)、批次维度(批次隔离) 2.任务策略、物料策略
  | 对接ERP单据业务类型 | 采购入库/退货、销售出库/退货、调拨出/入库、盘盈盘亏、其他出入库、上下架
  | 产品管理        | 产品分类、产品档案、产品编码规则、产品物料、产品BOM
  | 基础数据管理      | 供应商、客户、工厂
  | 系统管理        | 部门、用户、角色、权限、菜单、字典、三方授权
  | 任务调度        | 分布式调度: 即时库存、告警通知等

## 演示
> 项目代码、文档 均开源免费可商用 遵循开源协议在项目中保留开源协议文件即可<br>
活到老写到老 为兴趣而开源 为学习而开源 为让大家真正可以学到技术而开源

> 系统演示地址: [传送门](http://115.190.29.11:181/login)
> 账号&密码: sthelms st654321


# 技术栈

| 功能          | 技术栈                                                                                                               
|-------------|-------------------------------------------------------------------------------------------------------------------
| 前端项目        | 采用 Vue3 + TS + ElementPlus,pinia,vxe-table等                                                                                    
| 后端项目结构      | 采用插件化 + 扩展包形式 结构解耦 易于扩展                                                                               
| 后端代码风格      | 严格遵守Alibaba规范与项目统一配置的代码格式化                                                                                 
| Web容器       | 采用 Undertow 基于 XNIO 的高性能容器                                                                                      
| 权限认证        | 采用 Sa-Token、Jwt 静态使用功能齐全 低耦合 高扩展                                                                        
| 权限注解        | 采用 Sa-Token 支持注解 登录校验、角色校验、权限校验、二级认证校验、HttpBasic校验、忽略校验<br/>角色与权限校验支持多种条件 如 `AND` `OR` 或 `权限 OR 角色` 等复杂表达式        
| 关系数据库支持     | 原生支持 MySQL、Oracle、PostgreSQL、SQLServer<br/>可同时使用异构切换(支持其他 mybatis-plus 支持的所有数据库 只需要增加jdbc依赖即可使用 达梦金仓等均有成功案例)      
| 缓存数据库       | 支持 Redis 5-7 支持大部分新功能特性 如 分布式限流、分布式队列                                                                                                                                   
| Redis客户端    | 采用 Redisson Redis官方推荐 基于Netty的客户端工具<br/>支持Redis 90%以上的命令 底层优化规避很多不正确的用法 例如: keys被转换为scan<br/>支持单机、哨兵、单主集群、多主集群等模式 
| 缓存注解        | 采用 Spring-Cache 注解 对其扩展了实现支持了更多功能<br/>例如 过期时间 最大空闲时间 组最大长度等 只需一个注解即可完成数据自动缓存                                      
| ORM框架       | 采用 Mybatis-Plus 基于对象几乎不用写SQL全java操作 功能强大插件众多<br/>例如多租户插件 分页插件 乐观锁插件等等                                        
| SQL监控       | 采用 p6spy 可输出完整SQL与执行时间监控                                                                                                               
| 数据分页        | 采用 Mybatis-Plus 分页插件<br/>框架对其进行了扩展 对象化分页对象 支持多种方式传参 支持前端多排序 复杂排序                                        
| 数据权限        | 采用 Mybatis-Plus 插件 自行分析拼接SQL 无感式过滤<br/>只需为Mapper设置好注解条件 支持多种自定义 不限于部门角色                                          
| 数据脱敏        | 采用 注解 + jackson 序列化期间脱敏 支持不同模块不同的脱敏条件<br/>支持多种策略 如身份证、手机号、地址、邮箱、银行卡等 可自行扩展                                    
| 数据加解密       | 采用 注解 + mybatis 拦截器 对存取数据期间自动加解密<br/>支持多种策略 如BASE64、AES、RSA、SM2、SM4等                                                         
| 接口传输加密      | 采用 动态 AES + RSA 加密请求 body 每一次请求秘钥都不同大幅度降低可破解性                                                                                    
| 数据翻译        | 采用 注解 + jackson 序列化期间动态修改数据 数据进行翻译<br/>支持多种模式: `映射翻译` `直接翻译` `其他扩展条件翻译` 接口化两步即可完成自定义扩展 内置多种翻译实现             
| 多数据源框架      | 采用 dynamic-datasource 支持市面大部分数据库<br/>通过yml配置即可动态管理异构不同种类的数据库 也可通过前端页面添加数据源<br/>支持spel表达式从请求头参数等条件切换数据源                                  
| 多数据源事务      | 采用 dynamic-datasource 支持多数据源不同种类的数据库事务回滚                                                                      
| 数据库连接池      | 采用 HikariCP Spring官方内置连接池 配置简单 以性能与稳定性闻名天下                                                                             
| 数据库主键       | 采用 雪花ID 基于时间戳的 有序增长 唯一ID 再也不用为分库分表 数据合并主键冲突重复而发愁                                                                                            
| 序列化         | 采用 Jackson Spring官方内置序列化 靠谱!!!                                                                                   
| 分布式幂等       | 参考美团GTIS防重系统简化实现(细节可看文档)                                                                                         
| 分布式锁        | 采用 Lock4j 底层基于 Redisson                                                                                          
| 分布式任务调度     | 采用 xxl-job 天生支持分布式 统一的管理中心 支持多种数据库 支持分片重试DAG任务流等                                                                                 
| 文件存储        | 采用 Minio 分布式文件存储 天生支持多机、多硬盘、多分片、多副本存储<br/>支持权限管理 安全可靠 文件可加密存储                                                                                       
| 云存储         | 采用 AWS S3 协议客户端 支持 七牛、阿里、腾讯 等一切支持S3协议的厂家                                                                                                                             
| 短信          | 采用 sms4j 短信融合包 支持数十种短信厂家 只需在yml配置好厂家密钥即可使用 可多厂家共用                       
| 邮件          | 采用 mail-api 通用协议支持大部分邮件厂商                                                                                                                                               
| 接口文档        | 采用 SpringDoc、javadoc 无注解零入侵基于java注释<br/>只需把注释写好 无需再写一大堆的文档注解了                                                                                  
| 校验框架        | 采用 Validation 支持注解与工具类校验 注解支持国际化                                                                                                                                
| Excel框架     | 采用  EasyExcel 基于插件化<br/>框架对其增加了很多功能 例如 自动合并相同内容 自动排列布局 字典翻译等                                                                                                
| 工具类框架       | 采用 Hutool、Lombok 上百种工具覆盖90%的使用需求 基于注解自动生成 get set 等简化框架大量代码                                                                                             
| 监控框架        | 采用 SpringBoot-Admin 基于SpringBoot官方 actuator 探针机制<br/>实时监控服务状态 框架还为其扩展了在线日志查看监控                                                                     
| 代码生成器       | 只需设计好表结构 一键生成所有crud代码与页面<br/>降低80%的开发量 把精力都投入到业务设计上<br/>框架为其适配MP、SpringDoc规范化代码 同时支持动态多数据源代码生成                     
| 部署方式        | 支持 Docker 编排 一键搭建所有环境 让开发人员从此不再为搭建环境而烦恼                                                                             

## 分支说明

- master分支(稳定发布主分支 生产可用)
- dev分支(开发分支 开发过程中使用)

## 前端运行

```bash
# 安装依赖
npm install --registry=https://registry.npmmirror.com

# 启动服务
npm run dev

# 构建生产环境
npm run build:prod

# 前端访问地址 http://localhost:80
```

## 演示图例
主要功能,详细去演示环境中查看

|                                                                                      |                                                                                       |
|--------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|
| PC                                                                                   |                                                                                       |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/dl.png) '登录页'       | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/sy.png) '首页'         |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/ckgl.png) '仓库管理'    | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/ckfb.png) '仓库分布'     |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/rkgl.png) '入库管理'    | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/ckgl2.png) '出库管理'    |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/zyzd.png) '作业终端'    | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wms/sckb.png) '生产看板'     |
| PDA                                                                                  |                                                                                       |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/pda/pdadl.png) '登录'     | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/pda/pdarkgl.png) '入库管理'  |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/pda/pdackgl.png) '出库管理' | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/pda/pdapddb.png) '盘点&调拨' |
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/pda/pdahome.png) 'Home' | ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/pda/pdajieh.png) '借还&库存' |


## 联系作者
> 加入群聊讨论【Platfrom-Wms】
> 请备注：Platform-Wms

>后端：加群联系群主

|                                                                                               | 
|-----------------------------------------------------------------------------------------------|
| ![输入图片说明](https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/wxInfo/platform-wms-qq.png) 

[//]: # (## 捐献作者)

[//]: # (作者为兼职做开源,平时还需要工作,如果帮到了您可以请作者吃个盒饭  )

[//]: # (<img src="https://gitee.com/hesl183/platform-wms-ui/raw/master/src/assets/demo/zfb/zfbskm.png" width="300px" height="450px" />)
