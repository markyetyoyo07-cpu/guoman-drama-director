# guoman-drama-director

一个面向 Codex 的制作总控 Skill：把故事、小说、梗概、剧本或已有镜头，组织成精致、顺畅、连续的三维国漫质感短剧。

它不会假装“一键生成”已经解决角色一致性和口型，而是用明确关口协调剧本、资产、分镜、配音、试片、逐镜生成、剪辑、字幕和成片验收。关键设计包括：

- 15–25 秒、3–5 连续镜头的量产前试片；
- 人物、空间、动作、状态、声音、剧情六轴连续性；
- 普通切镜与真正同镜续接的不同处理；
- 任务 ID 恢复、重试上限和成本记录；
- 技术检测、逐镜检查、全片正常速度观看三重验收。

## 安装

```bash
npx skills add markyetyoyo07-cpu/guoman-drama-director
```

或将仓库目录复制到 Codex 的 skills 目录后重启 Codex。

## 使用

```text
使用 $guoman-drama-director，把这个故事做成中文、9:16、60–90 秒的三维国漫短剧。先完成剧本、视觉资产与带声音预演，再做连续试片；试片通过前不要批量生成。
```

本 Skill 会路由到 `short-drama` 系列技能，并按需配合 `imagegen`、`voice-generation`、`music-generation`、`agent-caption`、HyperFrames、FFmpeg 等媒体能力。实际生产前仍需验证你所选生成服务的当前模型、账号、价格和输入能力。

## 致谢与许可

工作流与已安装的短剧子技能协同使用，参考 [zenstory-ai/drama-skills](https://github.com/zenstory-ai/drama-skills) 的 creator-first 文档结构；相关第三方技能保留各自许可。本仓库自身内容采用 MIT License。
