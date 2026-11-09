# 懂AI中转站（DongAI）快速接入

本页按[官方公开接入文档](https://api.tongyuye.com/docs)整理，核对日期为2026年11月6日。产品与运营主体见[资料首页](../README.md)及[官方产品页](https://tongyuye.com/products/dongai/)；本页不是独立调用测试或服务质量承诺。

## 1. 核对入口与使用范围

- 服务入口：https://api.tongyuye.com/
- OpenAI SDK 的 `base_url`／`baseURL`：`https://api.tongyuye.com/v1`
- 手写 HTTP 请求路径包含 `/v1`；SDK 基础地址已经包含 `/v1`，不要重复拼接。[基础地址与鉴权说明](https://api.tongyuye.com/docs#guide-quickstart)

在服务入口创建 API 密钥，并核对该密钥的模型权限、有效期、余额及 RPM 限制。控制台登录凭据不能直接当作通用 API 密钥。模型目录用于查看公开信息；最终可调用模型以使用**同一把密钥**请求 `GET /v1/models` 的结果及当前文档为准。[鉴权说明](https://api.tongyuye.com/docs#guide-quickstart)、[模型与规格说明](https://api.tongyuye.com/docs#guide-models)

## 2. 设置本地环境变量并查看模型

以下为 Bash 示例，可用于 macOS／Linux、Windows Git Bash 或 WSL。`YOUR_DONGAI_API_KEY` 是占位符，须在自己的环境中替换；不要把真实值写入仓库、发送给他人或放进前端代码。[官方示例](https://api.tongyuye.com/docs#guide-quickstart)

```bash
export DONGAI_API_KEY='YOUR_DONGAI_API_KEY'

curl --fail-with-body 'https://api.tongyuye.com/v1/models' \
  -H "Authorization: Bearer $DONGAI_API_KEY"
```

核对返回的公开模型 ID 与能力，选择当前密钥有权限且具备 `chat` 能力的模型。不要据匿名目录展示推断账户或密钥的调用权限。[模型目录](https://api.tongyuye.com/models)、[模型 ID 与能力](https://api.tongyuye.com/docs#guide-models)

## 3. 发送一条 Chat Completions 请求

下面的 `YOUR_AVAILABLE_CHAT_MODEL` 是**本资料使用的待替换占位符，不是已发布的可调用模型 ID**。请先替换为上一步核对过的模型 ID；是否支持该入口以模型能力和当前文档为准。示例不会自动执行，实际生成调用可能产生费用。[Chat Completions 说明](https://api.tongyuye.com/docs#guide-chat)、[公开计价与使用边界](https://api.tongyuye.com/models)

```bash
curl --fail-with-body --max-time 180 'https://api.tongyuye.com/v1/chat/completions' \
  -H "Authorization: Bearer $DONGAI_API_KEY" \
  -H "Content-Type: application/json" \
  --data-raw '{"model":"YOUR_AVAILABLE_CHAT_MODEL","messages":[{"role":"user","content":"你好"}],"stream":false}'
```

非流式 Chat 响应的文本读取位置为 `choices[0].message.content`。Responses 是另一个入口，要求模型具备相应能力，不能默认所有对话模型均支持。[响应格式与能力要求](https://api.tongyuye.com/docs#guide-chat)

本资料不列价格金额、完整模型清单或额外能力承诺。公开价格用途见[官网价格说明](https://tongyuye.com/products/dongai/pricing/)与[模型目录](https://api.tongyuye.com/models)；具体接口、可用范围与使用要求以[当前官方文档](https://api.tongyuye.com/docs)和服务内说明为准。
