# seedance-2.5 API 中文文档（seedance2.5）：价格、参数与调用示例

<p align="center">
  <img src="hero.jpg" width="820" alt="sample output">
</p>

> **每秒 $0.0961 起（480P）**，按生成秒数计费，$1 起充，同一个 OpenAI 兼容接口。

**[查看模型页](https://go.apimart.ai/k-a32dd1)** · **[实时价格](https://go.apimart.ai/k-8e8c58)** · **[获取 API Key](https://go.apimart.ai/k-1064a0)**

本文覆盖 Seedance 2.5（也写作 seedance2.5、seedance 2.5）的模型 ID、**按秒计费的价格**、分辨率档位与调用方式，通过 API 中转网关 `https://api.apimart.ai/v1` 调用。

## 价格（实测，快照 2026-09-24）

| 档位 | 每秒单价 |
| --- | --- |
| `480P` | $0.0961 |
| `720P` | $0.216 |
| `1080P` | $0.3849 |

按秒计费、按量付费，**$1 起充**，没有订阅与免费额度。每次任务响应里返回 `cost` / `credits_cost`，可逐条核对。

## 调用方式

```bash
export APIMART_API_KEY="<token>"
curl --request POST --url https://api.apimart.ai/v1/videos/generations \
  --header "Authorization: Bearer $APIMART_API_KEY" --header 'Content-Type: application/json' \
  --data '{"model":"seedance-2.5","prompt":"海边悬崖上的现代别墅，黄昏，缓慢推镜","size":"16:9","resolution":"720p","duration":5}'
```

提交后拿 `task_id`，轮询 `GET /v1/tasks/{id}` 直到 `completed`。

## 常见问题

**计费单位？** 视频按秒、图像按张、语言模型按百万 token，价格见上表。
**支持哪些分辨率？** 480P, 720P, 1080P。
**中转站和官方有什么区别？** 同一个 OpenAI 兼容接口，价格与结算方式不同，以平台账单为准。

## 披露

本仓库为第三方中转服务 APIMart 的接入说明，与模型提供方无隶属关系。价格以标注快照为准。
