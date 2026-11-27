# UI 与网页设计蒸馏技能

这个仓库从 `01_UI_and_Web_Design` 相关视频中提炼作者解决问题的过程、判断依据、协作方式和制作技巧，形成 3 个可迁移到不同项目的技能。每个技能包含 `SKILL.md` 和来源证据，方法带有视频时间戳引用。

使用时先代入当前项目的目标、对象、素材和工程环境，再选择相关方法。视频中的看板、壁画、人物、工具与参数保留为来源案例，实际题材和配置由当前需求决定。迁移方法尚未在所有列举场景中执行验证。

## 技能目录

### `interface-design-process`

组织新界面设计与已有界面的迭代：先明确任务和信息结构，再拆参考、建立稳定规则与风格变量，用真实内容发现问题，通过可定位的反馈、单项修改和回归检查持续完善。可用于网站、App、工具界面和交互页面。

主要来源：V02、V19；V06、V07、V08、V16、V17 作为展示参考。

### `web-interaction-and-motion`

把交互想法拆成输入、反应对象、变化机制、时间关系和结束状态，再按控制需求与工程环境选择实现方式。素材准备、逐帧转换、状态联动和时间同步都是按需分支；工具名与图集参数仅作为来源示例。

主要来源：V09、V11、V14；V08、V16、V17 作为展示参考。

### `immersive-web-storytelling`

把视觉体验目标转成制作方案：按用途拆分和筛选素材，通过试作诊断空间问题，安排层次、遮挡和接续，保持关键主体一致，分开控制外观与运动，先低成本验证再提高质量。可迁移到产品展示、品牌叙事、作品展示或交互故事，题材由项目决定。

主要来源：V13；V10、V12 作为展示参考。

## 如何迁移到当前项目

先说明当前目标和已有成果，再使用对应技能推进。例如：

- “用 `interface-design-process` 迭代我的预约 App，保留已有导航和主色，先检查任务路径与信息层级。”
- “用 `web-interaction-and-motion` 设计产品卡片展开与联动，沿用现有工程，先给出状态和时间关系。”
- “用 `immersive-web-storytelling` 规划一页产品发布体验，围绕产品本身拆素材、安排层次和转场，先做一段可检查的试作。”

这些是迁移用法示例。技能正文提供作者做法提炼出的判断与流程，`references/source-evidence.md` 保留原始案例、具体参数和不确定项。

## 相关项目与参考资源

新增的 [`references/resource-map.md`](references/resource-map.md) 按用途整理了可选资源：

- GitHub 制作项目：界面组件、状态与时间线、平滑滚动、视频与逐帧素材、二维与三维空间化视觉。
- 设计规范与组件系统：Apple Human Interface Guidelines、Material 3、WCAG 2.2、Carbon、Fluent 2、Polaris 和 Atlassian Design System。
- 审美与案例参考：Awwwards、Mobbin、Land-book、Godly、SiteInspire、Behance 和 Dribbble。

资源地图标注了每个资源解决的问题、适用边界和对应技能。规范用于建立规则与检查，组件系统用于借鉴行为和状态，案例网站用于提取审美与交互线索；具体工具仍按当前项目的控制精度、素材、性能和输出要求选择。

## 目录结构

```text
interface-design-process/
  SKILL.md
  references/source-evidence.md
web-interaction-and-motion/
  SKILL.md
  references/source-evidence.md
immersive-web-storytelling/
  SKILL.md
  references/source-evidence.md
references/
  resource-map.md
```

## 安装

如果已经安装 `video-to-skill`，可以使用它提供的安装脚本逐个安装：

```powershell
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\install_skill.py" .\interface-design-process --dest "$env:USERPROFILE\.codex\skills"
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\install_skill.py" .\web-interaction-and-motion --dest "$env:USERPROFILE\.codex\skills"
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\install_skill.py" .\immersive-web-storytelling --dest "$env:USERPROFILE\.codex\skills"
```

## 验证

```powershell
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\validate_skill.py" .\interface-design-process
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\validate_skill.py" .\web-interaction-and-motion
python "$env:USERPROFILE\.codex\skills\video-to-skill\scripts\validate_skill.py" .\immersive-web-storytelling
```

结构验证检查技能格式、名称、引用和文件链接，不代表已完成实际项目验证。来源视频使用 `Whisper small` 转写，并结合关键帧、联系表、时间线和全分辨率画面核对；展示类视频仅用于视觉参考。通用化归纳与具体迁移建议在正文中说明，来源没有展示的实现仍需在使用时验证。
