# 本机 Skill 冲突审计

核对日期：2026-11-27。

## 扫描范围和统计口径

本次检查了四个活动根：

- `D:\distills\distilled_skills`：规范源仓库；
- `C:\Users\leo\.codex\skills`：Codex 活动安装根；
- `C:\Users\leo\.agents\skills`：Agent 活动安装根；
- `C:\Users\leo\.claude\skills`：Claude 活动安装根，包含指向 `.agents\skills` 的 Junction。

清理前四个活动根共记录 36 个活动入口；清理后保留 22 个物理活动入口，并通过 `.claude\skills` 的 6 个 Junction 继续暴露 `.agents\skills` 中的统一副本。对 `C:\Users\leo` 做递归扫描得到 772 个 `SKILL.md`；其中包含插件缓存、VS Code 扩展、第三方工具包、旧备份和临时目录。它们不是同一层的活动安装，不纳入删除清单，也不因同名就判定为当前冲突。

统计时区分三类对象：规范源、活动安装副本、缓存/备份副本。规范源只在仓库维护；活动副本需要同步；缓存和备份只在确实确认归属后处理。

## 已处理的合并

以下四个入口承担同一类网页/UI 体验设计问题，已合并为 `web-experience-design`：

| 原入口 | 合并后的职责 |
| --- | --- |
| `interface-design-process` | 任务结构、信息架构、视觉规则和真实内容迭代 |
| `web-interaction-and-motion` | 触发器、输入映射、状态、时间线、动效和动态素材 |
| `immersive-web-storytelling` | 空间层次、遮挡、场景接续和跨场景主体一致性 |
| `oil-ui` | 视觉方向探索、多方案比较、真实截图评审、素材整理和滚动叙事工具链 |

统一入口使用“当前核心问题”分流：先解决任务和内容，再按需读取视觉、动效、素材、滚动、空间或评审参考。原 Oil UI 的脚本和资源已迁入统一 skill 的 `references/`、`scripts/` 和 `assets/`，并保留其 `LICENSE`；不再作为第二个通用入口。

仓库和活动安装根中的下列目录应移入回滚目录或删除：

- 仓库：`interface-design-process`、`web-interaction-and-motion`、`immersive-web-storytelling`；
- `.codex\skills`：上述三个目录、`oil-ui`；
- `.claude\skills`：`oil-ui`；
- 三个活动根同步新增：`web-experience-design`。

## 已处理的 KiCad 清理

用户明确不再需要 KiCad，因此整体移出活动安装根：

- `kicad-library`
- `kicad-manufacture`
- `kicad-pcb`
- `kicad-review`
- `kicad-schematic`
- `konnect`
- `pcb-revision-release`

`easyeda-api` 保留。它只针对 EasyEDA/嘉立创EDA 客户端、API、扩展和项目操作；不会因通用的 PCB、原理图或 EDA 词汇自动触发 KiCad 路由。

## 保留但收紧边界的相邻入口

### `presenton` 与 `slide-maker`

两者都会遇到演示文稿、PPTX、PDF 或 PNG，但用途不同：明确要求 Presenton、Presenton API、设计搜索或 HTML 导出时使用 `presenton`；普通演示文稿的内容组织、视觉设计、重做和评审使用 `slide-maker`。同一任务需要两者时，先由 `slide-maker` 确定内容和设计，再按用户要求交给 Presenton 导出。

### `rigs` 与 `openrig-skills`

用户在自己的 Codex/Claude 会话中安装、启动、更新、加入或重新连接 OpenRig 时使用 `rigs`；当前已经运行在 OpenRig 内，需要交接、恢复、唤醒、跨主机连接或队列处理时使用 `openrig-skills`。`.claude\skills` 中的旧物理副本改为指向 `.agents\skills` 的统一副本，旧内容先备份。

### `ast-grep-outline` 与 `ast-grep`

这是顺序关系，不是同义重复：先用 `ast-grep-outline` 输出低成本结构地图，再在确实需要复杂规则、条件匹配或重写时使用 `ast-grep`。

### `refocusing` 与 OpenRig 路由

`refocusing` 只在长任务、上下文压缩或跨边界后需要重新锚定产品结果时使用；它不是 OpenRig 安装、启动或普通项目探索入口。

## 备份和回滚

被移出活动根的目录先移动到：

```text
C:\Users\leo\.claude\skills-backup\removed-20261127\
```

备份包括原始路径、移动时间和清单。仓库旧目录按 Git 删除，提交前可从 Git 恢复；用户目录副本不直接覆盖，先保留备份后再同步统一 skill。

## 验证要求

1. 运行 `skill-creator/scripts/quick_validate.py` 检查 `web-experience-design` 的 frontmatter、命名和未完成脚手架。
2. 运行 `video-to-skill/scripts/validate_skill.py` 检查来源型资源和目录结构。
3. 检查 `SKILL.md` 中每个参考链接都能解析，且没有指向已删除入口的路由文本。
4. 对规范源和三个活动安装副本比较相对文件清单及 SHA-256。
5. 运行 `git diff --check`，再检查活动根中不再出现旧网页入口和 KiCad 入口。

结构验证只证明文件和路由一致，不证明真实项目视觉、交互、加载或独立评审已经完成；使用统一 skill 时仍要按项目实际环境取得对应证据。
