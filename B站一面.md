- Mysql
- 微服务
- redis
- kafka和rocketMQ rabbitMQ
- Go



步韵聆康

- **user_detail** 存储用户基础信息，年龄性别和身高体重 ，记录有无身体残缺，提供个性化的数据录入服务
- **UserBaseConsultation **记录用户的基础问诊记录

- **user_info** 存储和账户相关的信息，vip钱币等，以及紧急联系人等重要信息
- **userProConsultaion** vip分析，充值分析
- **userPrediction** 记录分析结果
- **userRechargedRecord**记录充值信息

用户服务、医生端服务、大模型对话服务，OpenPose解析服务，

订单创建时，同时发往队列1，基础解析和创建订单

解析完后放入队列2，进行base分析

订单消费时，同时发往队列3，进行pro分析和账户扣减