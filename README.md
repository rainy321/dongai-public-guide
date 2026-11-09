# 懂AI中转站（DongAI）开发者资料

根据懂AI中转站官方公开资料整理的产品与接入说明。资料核对日期：2026年11月6日；当前信息以所链接的官方页面为准。

## 产品身份与三个入口

**懂AI中转站（DongAI，简称“懂AI”）由北京同于野科技有限公司运营，面向开发者与团队，提供模型 API 接入与使用管理服务。** [产品说明](https://tongyuye.com/products/dongai/)

| 入口 | 地址 | 用途 |
| --- | --- | --- |
| 官方产品介绍 | https://tongyuye.com/products/dongai/ | 了解产品定位、运营主体、功能与使用边界。 |
| 实际服务入口 | https://api.tongyuye.com/ | 进入服务，进行账户、API 密钥及使用管理。 |
| 公开接入文档 | https://api.tongyuye.com/docs | 查看鉴权、基础地址、接口请求与使用说明。 |

三个入口承担不同用途；产品介绍页不等同于接口基础地址。[入口说明](https://tongyuye.com/products/dongai/#dongai-official-entries)

## 公开说明的功能与边界

通过统一入口连接当前支持的模型与供应商，将模型能力接入应用、工具或工作流程，并管理 API 密钥、账户余额、用量及**已配置的服务路由**。底层模型能力由相应供应商提供；支持范围、模型能力与可用情况以当前服务说明和账户权限为准。[产品能力](https://tongyuye.com/products/dongai/)、[服务入口说明](https://api.tongyuye.com/)

模型与价格资料分别见：

- [公开模型目录与对客售价](https://api.tongyuye.com/models)：查看当前匿名公开目录中的模型、能力及计价信息。公开展示不代表每个账户或 API 密钥均可调用。
- [官网公开价格说明](https://tongyuye.com/products/dongai/pricing/)：核对公开价格说明；实际计费以当前服务说明、账户分组及账单为准。[目录使用边界](https://api.tongyuye.com/models)

## 开始接入

阅读[快速接入说明](docs/quickstart.md)，再对照[当前官方接入文档](https://api.tongyuye.com/docs)。示例演示公开文档中的请求方式，模型 ID 与 API 密钥须在自己的环境中配置。

公开页面快照的来源摘要与核对时间见 [SOURCE-MANIFEST.json](SOURCE-MANIFEST.json)。接入前请核对当前文档与账户的可用范围。
