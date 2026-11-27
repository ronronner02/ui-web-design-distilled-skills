# 本机 Skill 冲突审计

核对日期：2026-11-27。

扫描范围：

- `D:\distills\distilled_skills`
- `C:\Users\leo\.codex\skills`
- `C:\Users\leo\.agents\skills`

扫描到 31 个 `SKILL.md`（包含 `.system`、视频技能示例和两个本地技能目录）。以下结论只描述触发路由和职责边界，不代表所有技能正文都需要同时加载。

## 重复副本

下面三个技能在仓库与 `C:\Users\leo\.codex\skills` 中各有一份内容完全相同的副本：

| 规范源 | 安装副本 | 处理决定 |
| --- | --- | --- |
| `interface-design-process/SKILL.md` | `C:\Users\leo\.codex\skills\interface-design-process\SKILL.md` | 仓库作为唯一编辑源；用 `install_skill.py --dest` 同步 |
| `web-interaction-and-motion/SKILL.md` | `C:\Users\leo\.codex\skills\web-interaction-and-motion\SKILL.md` | 同上 |
| `immersive-web-storytelling/SKILL.md` | `C:\Users\leo\.codex\skills\immersive-web-storytelling\SKILL.md` | 同上 |

同名目录不是三个不同技能。两处都保留会造成维护漂移，但不应把安装副本再当成第二个源修改。

## 已确认的触发重叠

### UI、网页和视觉体验

| 技能 | 原重叠点 | 处理后的路由 |
| --- | --- | --- |
| `oil-ui` | 覆盖网站、App、后台、组件设计和界面优化 | 负责探索视觉方向、多风格对比页、截图驱动的设计评审；改法已明确的日常小改动不触发 |
| `interface-design-process` | 同时覆盖新界面和已有界面视觉迭代 | 负责任务、信息架构、视觉规则和真实内容迭代；不负责独立动效工程或沉浸式空间叙事 |
| `web-interaction-and-motion` | 同时出现网页、动效、素材和工具选择 | 只有当输入响应、状态、时间线或动态素材是核心问题时触发 |
| `immersive-web-storytelling` | 同时出现网页、动效、素材、滚动和三维 | 只有当空间层次、场景接续、主体一致性或沉浸式叙事是核心问题时触发 |

选择顺序：视觉方向和多方案探索先看 `oil-ui`；页面任务和信息层级先看 `interface-design-process`；独立交互行为先看 `web-interaction-and-motion`；空间叙事先看 `immersive-web-storytelling`。

### 演示文稿与导出文件

`presenton` 和 `slide-maker` 都会被 PowerPoint、deck、presentation、PDF 或 PNG 请求触发。处理规则：

- 用户明确要求使用 Presenton、Presenton API、设计搜索或其导出流程时，使用 `presenton`。
- 普通演示文稿的内容组织、视觉设计、重做和评审使用 `slide-maker`。
- 同一任务需要两者时，先用 `slide-maker` 确定内容与设计，再在明确要求 Presenton 导出时调用 `presenton`。

### KiCad、PCB 与 EDA

这组不是“谁覆盖谁”，而是需要分层：

- `konnect` 是所有 KiCad 项目的底层完整性和写入通道规则；涉及 KiCad 时始终优先读取。
- `kicad-schematic`、`kicad-pcb`、`kicad-library`、`kicad-review`、`kicad-manufacture` 按具体操作选择，并通过 Konnect MCP 执行。
- `pcb-revision-release` 负责产品级需求、选型、整板或改版范围；涉及 KiCad 的具体修改、检查和导出仍交给 `konnect` 与对应 `kicad-*` 技能。
- `easyeda-api` 只用于 EasyEDA/嘉立创EDA 客户端、API、扩展和项目操作；不要因出现通用词 `PCB`、`schematic` 或 `EDA` 自动触发。

### AST 搜索

- `ast-grep-outline` 先输出低成本结构地图，用于探索和缩小阅读范围。
- `ast-grep` 用于需要编写结构规则、复杂匹配或按 AST 条件搜索的任务。
- “先 outline，再复杂 ast-grep”是顺序关系，不是同时加载要求。

### OpenRig

- 用户在自己的 Codex/Claude 会话中安装、启动、更新、加入或重新连接 OpenRig：使用 `rigs`。
- 当前已经运行在 OpenRig 内，需要交接、恢复、唤醒、跨主机连接或队列处理：使用 `openrig-skills`。

## 没有发现硬冲突的技能

`create-statusline`、`imagegen`、`openai-docs`、`skill-creator`、`skill-installer`、`python-venv-requests`、`refocusing`、`karpathy-guidelines` 是基础能力、工具专用或上下文维护技能；本轮没有发现需要改写触发描述的直接冲突。

## 维护规则

1. 新技能的 `description` 只写用途、触发条件和必要边界，不把相邻技能的全部能力复制进去。
2. 任务跨两个技能时，选择一个主技能；另一个只在主技能明确需要时加载。
3. 修改仓库源后重新运行两个验证器，再用 `install_skill.py --dest "$env:USERPROFILE\.codex\skills"` 同步安装副本。
4. 同步后比较 SHA-256；发现安装副本与规范源不同，先判断是否是未安装的新版本，再决定是否覆盖。
