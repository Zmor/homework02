# 作业二：分布式事务专项练习



## 实现思路
通过business-service发起下单，使用OpenFeign实现远程调用，调用orderFeignClient.insertOrder创建订单，调用accountFeignClient.insertPointRecord调用账户服务，支付订单，通过seata的AT模式在业务主服务中使用@GlobalTransactional注解来启动全局事务。




## 技术选型

- 数据库：MySQL
- 缓存中间件：Redis
- 消息中间件：RocketMQ
- 服务发现：Nacos
- 服务调用：OpenFeign
- 分布式事务框架：Seata



## 工程结构

```
├── common                       # 公共模块
├── business-service             # 业务主服务
├── order-service                # 订单服务
├── account-service              # 用户账户服务
├
├── docker-compose               # 运行环境的docker-compose配置
└── sql                          # 数据库相关sql
```



## 数据库表结构

```
├── account                  # 用户库
│   └── t_user               # 用户表
│   └── t_point_record       # 积分变更记录
│   └── undo_log             # undo_log
├── order                    # 订单库
│   └── t_order              # 订单表
│   └── undo_log             # undo_log
```



## 运行环境

除了Java服务，其余环境都在docker-compose.yml中配置

```bash
cd ./docker-compose
docker-compose up -d
```







