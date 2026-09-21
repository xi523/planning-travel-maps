# 行程数据约定

维护项目内一份 JSON 作为事实和路线的主数据。保留稳定 ID；展示名称变化不应打断引用。下列字段按阶段逐步补齐，未知值用 null 或空数组，不用猜测值占位。

## 建议结构

```json
{
  "schemaVersion": 1,
  "trip": {
    "id": "holiday-trip",
    "title": "假期旅行",
    "year": null,
    "startDate": null,
    "endDate": null,
    "origin": null,
    "destinations": [],
    "travelers": {"count": null, "needs": []},
    "budget": {"amount": null, "currency": "CNY", "scope": null},
    "preferences": [],
    "avoid": []
  },
  "assumptions": [],
  "openQuestions": [],
  "sources": [],
  "places": [],
  "commitments": [],
  "options": [],
  "selectedOptionId": null,
  "revision": {"updatedAt": null, "changes": []}
}
```

### 来源 sources

每项包含 `id`、`title`、`url`、`publisher`、`checkedAt`（带时区的日期时间）、`supports`（它支持什么事实）。官方与非官方来源分别标注；搜索摘要不是已读原文。预约事实可记录 `kind: user` 和用户确认内容，不必上传原始截图。

### 地点 places

每项包含 `id`、`name`、`localName`、`type`（attraction/hotel/station/event/restaurant/photo/pickup/dropoff）、`region`、`coordinates: {lat, lng}`、`coordinatePrecision`（entrance/approximate）、`sourceIds`。

按需增加：介绍、代表景观、`visitMinutes`、开放规则、预约要求、步行强度、遮阴、`photoSpots`、图片来源、官方地图、外部导航 URL。详细机位需要独立地图标记时用独立地点 ID 和 `parentPlaceId`。

未核实坐标保持 null，显示在待定位列表，不能把城市中心冒充入口。图片包含来源页面、图片 URL、说明、核验结果；有使用限制时保留链接而非重新托管。

### 硬约束 commitments

每项包含 `id`、`type`、`status`、`placeId`（可空）、`startLocal`、`endLocal`、`timezone`、`confirmationBasis`（用户文字/实际订单/候选页面）、`sourceIds`。

跨时区交通分别记录起终点的当地时间和 IANA 时区，再换算持续时间。不能把航班展示的当地时间直接相减。可加入到场提前量、预订/取消截止和返程限制。

`status` 限于 confirmed、tentative、candidate、unknown。订单号、联系方式、凭证二维码不属于地图必要字段。

### 方案 options

每项包含 `id`、`title`、`tradeoffs`、`intensity`、`estimatedCost`（说明币种、计价人数和范围）、`days`。

每个 day 包含 `date`、`timezone`、`title`、`stops`、`legs`、`fallbacks`。stop 包含 `placeId`、`arrival`、`departure`、`priority`、可选 `commitmentId` 和 `photoCode`。同一酒店可在不同时间重复作为 stop，不能简单去重抹掉返程。

日期未知时 day.date 为 null，增加 dayIndex（从 1 开始），显示 Day 1 等相对日期；不要填写虚构日历日期。没有酒店时可使用 type: area 的住宿区域参考点，标明 approximate 与 candidate，不当作已订酒店。仅有单程机票时只保存已知航段，返程和旅行结束日期保持 null；方案天数放在 options，不当作用户事实。

leg 包含 `fromStopIndex`、`toStopIndex`、`mode`（walk/taxi/rail/bus/ferry/flight）、`durationMinutes`、`bufferMinutes`、`timeBasis`（estimate/verified_schedule）、上下车信息、`navigationUrl`、`sourceIds` 和 `geometryKind`（schematic/routed）。无真实路线几何时使用 schematic。

## 一致性检查

- 所有 ID 引用存在；当天 stops 按时间排序，交通和缓冲不能晚于下一场预约。
- 已确认安排都纳入主方案，或明确列出无法兼容的冲突，不能静默删除。
- 经纬度数值有效且接近目标地区；纬度经度顺序依地图 API 显式转换。
- 选定方案、酒店、日期和编号在数据、文字、地图中一致。
- 来源只支持其实际核实的内容；预估耗时不伪装成时刻表。
- 变更后记录简短 revision，保留用户未变更的决定。
