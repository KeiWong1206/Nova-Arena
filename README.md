# Nova-Arena

# 🚀 Nova-Arena (星云竞技场) - 高并发场馆票务与 SaaS 管理平台

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Spring Cloud Alibaba](https://img.shields.io/badge/Spring%20Cloud%20Alibaba-2022.x-blue.svg)](https://github.com/alibaba/spring-cloud-alibaba)
[![Redis](https://img.shields.io/badge/Redis-Cluster-red.svg)](https://redis.io/)
[![RocketMQ](https://img.shields.io/badge/RocketMQ-5.x-orange.svg)](https://rocketmq.apache.org/)

## 📖 项目简介
**Nova-Arena** 是一套面向全国大型体育场馆、演唱会及赛事中心的“高并发票务预订”与“多租户 SaaS 商业管理”综合平台。
本项目旨在解决场馆黄金时间段**瞬时高并发抢票（秒杀）**带来的系统雪崩、库存超卖问题，同时为入驻的千万家场馆商户提供**绝对隔离的 SaaS 多租户数据管理**能力。

项目采用微服务架构设计，基于前沿的 Spring Cloud Alibaba 生态构建，是探索大型分布式系统高可用、高性能、高可扩展性的最佳工程实践。

---

## 🏗️ 核心模块划分 (Project Modules)

整个微服务生态采用标准的 Maven 多模块聚合工程构建：

```text
nova-arena
├── nova-dependencies     # 全局依赖版本管理 (BOM)
├── nova-common           # 全局公共组件 (全局异常、结果集、工具类、Redis配置)
├── nova-gateway          # 统一 API 网关 (流量入口、全局鉴权、Sentinel限流)
├── nova-auth             # 统一认证授权中心 (OAuth2.0 / JWT)
├── nova-modules          # 核心业务微服务群
│   ├── nova-biz-tenant   # 【B端】多租户与商户服务 (场馆入驻、员工权限、资金对账)
│   ├── nova-biz-ticket   # 【C端】票务与场次服务 (高并发抢票、库存扣减、秒杀引擎)
│   ├── nova-biz-order    # 【C端】订单与交易服务 (订单状态机、分布式事务处理)
│   └── nova-biz-user     # 【C端】用户中心服务 (用户画像、积分、会员等级)
└── docker                # 容器化部署脚本 (docker-compose 一键拉起中间件)
