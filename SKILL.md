---
name: guoman-drama-director
description: Use when turning a story, novel, outline, screenplay, or existing generated shots into a polished, continuous 3D Chinese-animation-style short drama or comic drama, especially when character identity, spatial and action continuity, lip sync, voice consistency, pilot validation, generation retries, editing, subtitles, or delivery quality must be coordinated end to end.
license: MIT
metadata:
  version: 0.1.0
  language: zh-CN
---

# Guoman Drama Director

把故事变成精致、顺畅、连续的三维国漫质感短剧，并把每个结论落到可复核的项目文件、真实媒体或验收记录。

## 核心原则

- “三维国漫”默认是视觉质感，不等于交付可编辑三维模型、绑定或工程；若用户要求真正三维资产，先明确扩展管线。
- 默认采用“本地管理故事与资产 → 云端逐镜生成 → 本地剪辑、声音与质检”。不要因某个工具已安装就宣称它已投产。
- 先做 15–25 秒、3–5 个连续镜头的试片；未通过，不批量生成整集。
- 把文件生成成功、技术检测通过、创作质量通过视为三件不同的事。

## 路由到现有技能

先用 `short-drama` 初始化或恢复项目，再按阶段委派给唯一主责技能：

| 阶段 | 主责技能 |
|---|---|
| 长篇原著拆解 | `short-drama-novel-analyze` |
| 改编、分集、创作方向 | `short-drama-develop` |
| 可表演剧本 | `short-drama-write` |
| 人物、场景、道具、状态 | `short-drama-assets` |
| 定妆与参考图提示词 | `short-drama-image-prompts`，出图时再用 `imagegen` |
| 分镜与冻结关键帧 | `short-drama-storyboard` |
| 视频与时间线音乐意图 | `short-drama-video-prompts` |
| 经创作者确认后的媒体执行 | `short-drama-produce`；声音可用 `voice-generation`，音乐可用 `music-generation` / `media-use` |
| 剪辑、字幕与导出 | `short-drama-edit`；按需调用 `agent-caption`、`hyperframes`、`general-video`、`ffmpeg-skill` 或 `video-use`，但一版成片只设一个最终渲染入口 |
| 阶段或成片审查 | `short-drama-review` |

不要让多个总控技能同时改写同一项目事实。上游变更后，只重做受影响的下游资产。

## 执行门槛

1. **范围门**：确认改编边界、观众体验、画幅、语言、目标时长、预算与不可改内容。缺信息时标记假设，不把建议冒充用户决定。
2. **剧本门**：重要信息可见或可听；动作、对白、声音、退出状态明确；实测台词时长给反应留空间。
3. **资产门**：锁定角色身份锚点、服装状态、声音身份、场景地理和道具状态；真实参考图可用后才进入大量视频生成。
4. **预演门**：用锁定台词或试演声音完成整集低成本预演，确认因果、节奏和镜头职责。
5. **试片门**：连续试片必须包含脸部近景、转头或转身、人与物接触、中文对白、明确切镜。记录模型版本、参考版本、任务 ID、费用、可用区间和缺陷。
6. **量产门**：试片通过后才逐镜扩展；每镜限定尝试次数，整集限定成本。身份、表演关键镜先做，反应和环境镜后补。
7. **交付门**：技术测量、逐镜检查、手机尺寸全片正常速度观看全部完成；阻断与重大问题关闭后才能称为成片。

## 连续性规则

逐镜检查六条线：人物身份、空间、动作、状态、声音、剧情。详细字段和示例见 [pilot-and-continuity.md](references/pilot-and-continuity.md)。

- 普通切镜：为下一镜独立构图，共享角色、场景和状态参考；不要机械地把上一镜尾帧当下一镜首帧。
- 同镜延长：必须使用实际上一段视频、实际尾帧、未完成动作和连续声音；计划中的尾帧不算输入。
- 供应商已有任务 ID 而下载或轮询中断时，先取回原任务，避免重复提交和重复计费。
- 变脸、接触错误、方向错、口型错分别定位源头；超过重试上限就改镜头设计，不无限重抽。

## 输出与证据

维护五份创作文档：剧本、视觉设定、图片提示词、分镜、视频提示词。生产阶段另保留预演、真实媒体、剪辑单、字幕、任务与费用记录、质量问题及修复记录。密钥不得进入项目或交付包。

开始执行前读 [production-workflow.md](references/production-workflow.md)；准备试片读 [pilot-and-continuity.md](references/pilot-and-continuity.md)；接入生成服务读 [provider-boundaries.md](references/provider-boundaries.md)；准备交付读 [quality-gates.md](references/quality-gates.md)。
