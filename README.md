# 旅行攻略与交互地图

[English documentation](README.en.md)

只给一个目的地也能开始。支持文字描述、截图或文件，兼容日期未定、单程或往返机票、有无酒店；逐步完成景点认识、方案比较、交通与拍照路线、美食筛选、交互地图和按需发布。

## 使用

将完整 planning-travel-maps 文件夹放入 Codex 的用户级 skills 目录（通常为 ~/.codex/skills），在新会话中使用：

> 使用 $planning-travel-maps 帮我规划旅行。我想去槟城，日期和酒店还没定，先给我建议。

也可以提供文字航班、已订酒店或订单截图。只有目的地时会先给带明确假设的草案；补齐信息后再更新，不会虚构已订安排。

## 内容

- SKILL.md：主入口和阶段流程。
- references/intake.md：不完整输入与各种预订组合。
- references/research-and-routing.md：事实核验、交通和拍照路线。
- references/food-selection.md：美食分类、评分、图片与地图交互。
- references/trip-data.md：数据结构和一致性。
- references/map-and-publishing.md：地图、验证、故障和分享。
- references/trial-scenarios.md：行为试用场景。
- agents/openai.yaml：Codex 展示信息。
- references/localization.md：完整中英文 HTML、状态保留与双语验收。

生成的旅行 HTML 默认提供中文 / English 切换，覆盖行程、景点、美食、地图弹窗、筛选和提示，不只是翻译菜单；同一套点位和路线保证两种语言一致。此仓库是生成指导，不含预制旅行网站，实际成品需逐次验证。

主入口会按任务读取所需指南，分享时请保留整个目录，不能只发送 SKILL.md。

## 能力边界

联网核验需要宿主提供浏览或搜索工具；HTML 生成需要文件操作能力，视觉测试需要浏览器。发布还需要可用托管平台及相应授权，本包不附带账号、凭证或在线地图服务额度。

本地 HTML 不等于完全离线地图；图片、底图、导航可能需要联网。Google 评分为核验快照，不是实时同步服务。技能不自动订票、订酒店、订餐或发布旅行信息，也不承诺永久可访问网址。

此包包含通用指导，不包含用户订单、餐厅数据、实际旅行地图或个人截图。回归场景是测试建议，不代表每一种组合都完成了端到端验证。
