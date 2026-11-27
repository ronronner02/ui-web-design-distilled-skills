# 网页体验设计蒸馏技能

这个仓库是 `web-experience-design` 的规范源（canonical source）。它把原来的界面设计、网页交互与动效、沉浸式网页叙事以及 Oil UI 的视觉探索流程合并为一个入口，覆盖任务结构、真实内容、视觉规则、交互状态、动态素材、空间关系和截图驱动评审。

仓库中的 `web-experience-design/` 是唯一编辑源；`C:\Users\leo\.codex\skills`、`C:\Users\leo\.agents\skills` 和 `C:\Users\leo\.claude\skills` 中的同名目录是同步安装副本。不要在安装目录直接改正文，修改后从本仓库重新同步。

## 统一入口

### `web-experience-design`

用于网站、App、工具界面和沉浸式网页体验的整体设计判断：

- 先写用户任务、真实内容、主角、主动作和信息结构；
- 把参考拆成稳定规则与主题变量；
- 用交互契约描述触发器、反应对象、变化机制、时间关系和恢复状态；
- 按用途组织素材，控制层次、遮挡、接续和跨场景主体一致性；
- 依据控制精度选择 CSS、JavaScript、Motion、GSAP、Canvas、Three.js、逐帧或视频；
- 用低成本真实内容试作，逐轮修改并保留回滚点；
- 在真实视口检查内容、交互、加载和未验证项。

原 Oil UI 的方向探索、风格对比页、真实截图评审、素材整理和滚动叙事资源已内置到 `web-experience-design/references/` 与 `web-experience-design/scripts/`，不再作为单独入口。

## 如何使用

先说明当前目标、真实内容、既有成果、设备和技术约束，再按本轮范围进入统一 skill：

- 已明确的小改动直接改指定元素；
- 新界面或整体改版先做任务、主视口灰度和一个推荐方向；
- 用户明确要求多方向时读取 `references/task-explore.md`；
- 需要视觉语言、素材、动效、滚动叙事或独立评审时只读取对应参考；
- 只读评审读取 `references/task-review.md`，不自动修改代码。

来源证据、时间戳和方法边界见 [`web-experience-design/references/source-evidence.md`](web-experience-design/references/source-evidence.md)。完整活动根冲突、重复副本和删除决定见 [`references/conflict-audit.md`](references/conflict-audit.md)。

## 资源结构

```text
web-experience-design/
  LICENSE
  SKILL.md
  references/
    source-evidence.md
    design-direction.md
    visual-language.md
    media.md
    motion.md
    scroll-narrative.md
    task-explore.md
    task-review.md
    visual-review.md
    ux-review.md
    ...
  scripts/
    build_explorer.py
    shoot.mjs
    curate-media.mjs
    prep-image.mjs
    ...
  assets/
    style-explorer.html
    ...
```

资源按需读取。过程截图、对比页和评审记录放在项目任务目录，不写进 skill 安装目录。

## 安装与同步

仓库作为规范源，安装目录作为副本。同步前先把被替换的活动目录移动到 `C:\Users\leo\.claude\skills-backup\removed-20261127`，以便回滚。统一 skill 需要同步到三个活动根：

```powershell
$source = 'D:\distills\distilled_skills\web-experience-design'
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\install_skill.py" $source --dest "$env:USERPROFILE\.codex\skills"
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\install_skill.py" $source --dest "$env:USERPROFILE\.agents\skills"
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\install_skill.py" $source --dest "$env:USERPROFILE\.claude\skills"
```

如果安装脚本不接受已经存在的目录，先完成备份和移除，再运行同样的命令。同步后比较 `SKILL.md` 及所有资源的 SHA-256；安装副本只应与规范源内容不同于路径。

## 验证

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" .\web-experience-design
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\validate_skill.py" .\web-experience-design
git diff --check
```

结构验证不等于真实项目视觉验收。使用统一 skill 时仍需在目标视口运行、检查实际状态，并明确记录未验证部分。

## 活动安装范围与清理边界

本轮扫描了四个活动根：仓库、`.codex\skills`、`.agents\skills` 和 `.claude\skills`，清理前共记录 36 个活动入口；清理后保留 22 个物理活动入口，并通过 `.claude\skills` 的 6 个 Junction 继续暴露 `.agents\skills` 中的统一副本；递归扫描用户目录得到 772 个 `SKILL.md`，其中大量是插件缓存、VS Code 扩展、临时目录和旧备份，不把它们当作当前已加载 skill，也不直接删除。

按用户要求，KiCad 相关 skill（`kicad-*`、`konnect`、`pcb-revision-release`）整体移出活动安装根；`easyeda-api` 保留，它只处理 EasyEDA/嘉立创EDA。`presenton` 与 `slide-maker` 仍按工具边界分工，`rigs` 与 `openrig-skills` 仍按“会话外安装/运行中恢复”分工，`ast-grep-outline` 与 `ast-grep` 仍按“先结构地图、后复杂规则”分层。
