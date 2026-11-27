# 制作项目与设计参考资源地图

本文件补充三个技能的可选资源。资源按“解决什么问题”组织，不按热度排序，也不把某个库、框架、题材或参数当成默认要求。先用技能中的方法拆解目标，再从对应类别选择最小的一组资源。

核对日期：2026-11-27。

## 先判断当前问题属于哪一类

| 当前问题 | 先使用的技能 | 主要参考类别 | 选择重点 |
| --- | --- | --- | --- |
| 页面任务、信息层级、组件状态或视觉规则不稳定 | `interface-design-process` | 设计规范、组件系统、界面案例 | 先解决任务和层级，再借鉴组件、排版和状态 |
| 点击、悬停、滚动、拖拽、时间线或素材联动说不清 | `web-interaction-and-motion` | 动效框架、滚动工具、逐帧与时间线工具 | 先写触发器、反应对象、变化机制、时间关系和恢复状态 |
| 需要空间层次、场景接续、主体一致性或沉浸式叙事 | `immersive-web-storytelling` | 2D/3D 渲染、时间线、素材和动效工具 | 先拆素材职责、遮挡、节奏和接续，再决定是否需要三维或视频 |

工具只是实现选项。简单的状态变化优先使用已有 CSS 或项目现有能力；只有当控制精度、时间组织、渲染方式或输出格式确实需要时，才引入额外依赖。

## GitHub 制作项目

### 界面结构与组件

| 项目 | 解决什么问题 | 适合怎么用 | 对接技能 |
| --- | --- | --- | --- |
| [shadcn/ui](https://github.com/shadcn-ui/ui) | 可复制、可修改的界面组件与样式起点 | 需要快速建立一套可由项目掌控的组件基础时，先挑少量组件并改成项目规则 | `interface-design-process` |
| [Radix Primitives](https://github.com/radix-ui/primitives) | 无样式或低样式的可访问交互原语 | 需要对弹窗、菜单、选项卡等行为有稳定控制，同时自行决定视觉表现时 | `interface-design-process`、`web-interaction-and-motion` |
| [Headless UI](https://github.com/tailwindlabs/headlessui) | 与 Tailwind 配合的无样式交互组件 | 已使用 Tailwind，且希望把组件状态与视觉主题分开维护时 | `interface-design-process` |
| [MUI](https://github.com/mui/material-ui) | 完整的 React 组件系统和主题能力 | 需要成熟的表单、数据展示和后台组件时，先按任务删减，不要直接照搬整套视觉 | `interface-design-process` |

这些项目提供的是组件行为、状态或起始结构。最终的模块关系、内容密度、品牌变量和修改范围，仍按 `interface-design-process` 的流程确定。

### 动效、状态与时间线

| 项目 | 解决什么问题 | 适合怎么用 | 对接技能 |
| --- | --- | --- | --- |
| [GSAP](https://github.com/greensock/GSAP) | 多对象时间线、顺序、并行、缓动和进度控制 | 动作有明确先后关系，或需要把多个对象编排成一条可调时间线时 | `web-interaction-and-motion`、`immersive-web-storytelling` |
| [Motion](https://github.com/motiondivision/motion) | Web 和 React 中的状态过渡、布局变化与手势动画 | 页面状态、布局联动或手势反馈比复杂时间线更重要时 | `web-interaction-and-motion`、`interface-design-process` |
| [Theatre.js](https://github.com/theatre-js/theatre) | 可视化的时间线和场景编排 | 需要反复调节镜头、对象和节奏，并希望把时间关系显式保存时 | `web-interaction-and-motion`、`immersive-web-storytelling` |
| [Lenis](https://github.com/darkroomengineering/lenis) | 平滑滚动和滚动进度管理 | 需要滚动作为连续输入，再把进度交给页面或场景动画时 | `web-interaction-and-motion`、`immersive-web-storytelling` |
| [anime.js](https://github.com/juliangarnier/anime) | 轻量的 DOM、CSS、SVG、Canvas 和 JavaScript 动画 | 需要少量对象、较轻依赖和直接的时间控制时 | `web-interaction-and-motion` |

选择顺序：少量状态先用现有样式过渡；连续输入先确认输入与恢复行为；多个对象需要同步时再引入时间线工具。平滑滚动本身不是体验目标，必须能说明它为哪些滚动驱动内容服务。

### 视频、逐帧和可复用动态素材

| 项目 | 解决什么问题 | 适合怎么用 | 对接技能 |
| --- | --- | --- | --- |
| [Remotion](https://github.com/remotion-dev/remotion) | 用 React、样式和帧号生成可重复的视频或动画模板 | 需要批量替换文字、图片、时间和数据，或需要导出视频时 | `web-interaction-and-motion` |
| [Lottie Web](https://github.com/airbnb/lottie-web) | 在网页中播放 After Effects 导出的 JSON 动画 | 动画需要轻量播放、可暂停或按进度控制，且已有 Lottie 资产时 | `web-interaction-and-motion`、`interface-design-process` |
| [Rive Web runtime](https://github.com/rive-app/rive-wasm) | 面向交互的矢量动画、状态机和 Web 运行时 | 动画需要根据状态、输入或用户操作持续响应时；编辑仍在 Rive 工作流中完成 | `web-interaction-and-motion`、`interface-design-process` |

逐帧图集、视频、Lottie 和 Rive 的选择由素材来源、交互精度、加载预算和导出要求决定。不要因为案例中使用了某种素材，就把它作为所有项目的前置步骤。

### 二维、三维和空间化视觉

| 项目 | 解决什么问题 | 适合怎么用 | 对接技能 |
| --- | --- | --- | --- |
| [Three.js](https://github.com/mrdoob/three.js) | WebGL/WebGPU 三维场景、相机、材质、灯光和几何 | 目标体验确实依赖真实三维关系、自由视角或空间光照时 | `immersive-web-storytelling`、`web-interaction-and-motion` |
| [React Three Fiber](https://github.com/pmndrs/react-three-fiber) | 用 React 组织 Three.js 场景和对象 | 项目本身是 React，且需要把三维对象与页面状态连接时 | `immersive-web-storytelling`、`web-interaction-and-motion` |
| [Drei](https://github.com/pmndrs/drei) | React Three Fiber 的常用辅助组件 | 需要相机、控制器、环境光、加载器等通用场景部件时 | `immersive-web-storytelling` |

如果二维分层、蒙版或普通 CSS 已经能够表达目标，就先用低成本方式验证构图、遮挡和接续。三维工具用于解决真实的空间关系，而不是自动提升审美。

## 设计规范与组件系统

这些资源用于建立规则、检查状态和理解平台惯例。它们的视觉语汇有适用边界，不应直接覆盖项目自身的任务、品牌和内容。

| 资源 | 适合观察什么 | 使用边界 | 对接技能 |
| --- | --- | --- | --- |
| [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/) | Apple 平台的层级、导航、反馈、动效、可访问性和平台惯例 | 主要面向 Apple 生态；网页项目借鉴原则时要重新映射到浏览器和产品目标 | `interface-design-process`、`web-interaction-and-motion` |
| [Material Design 3](https://m3.material.io/) | 色彩、排版、组件、主题、响应式布局和动效规则 | Material 语汇不是所有品牌的默认风格，适合作为规则样本 | `interface-design-process`、`web-interaction-and-motion` |
| [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/) | 对比度、键盘操作、焦点、替代文本、时间限制等可访问性要求 | 它是可访问性标准，不是审美图库；用来检查基本可用性与包容性 | 三个技能共同使用 |
| [IBM Carbon](https://carbondesignsystem.com/) | 企业级网格、数据密度、主题、组件状态和内容规范 | 更接近 B2B、数据型和复杂工作流产品 | `interface-design-process` |
| [Microsoft Fluent 2](https://fluent2.microsoft.design/) | 跨平台布局、组件、主题、动效和无障碍 | 更适合作为 Microsoft 生态或跨平台产品的参考 | `interface-design-process`、`web-interaction-and-motion` |
| [Shopify Polaris](https://polaris.shopify.com/) | 后台信息架构、表单、表格、内容语气和状态反馈 | 电商后台语境明显，借鉴结构时要替换业务语境 | `interface-design-process` |
| [Atlassian Design System](https://atlassian.design/) | 复杂工作流、协作产品、组件状态、内容和可访问性 | 更接近企业协作产品；不要把其默认密度当作通用答案 | `interface-design-process` |

使用顺序建议：先选与平台、用户和产品类型最接近的一套规范；抽取需要的规则，写入项目自己的风格表；再用真实内容检查规则是否成立。多套规范可以用于比较，但不要把互相冲突的默认值全部叠加。

## 审美、案例和交互参考网站

这些网站适合发现方向、拆解案例和建立 moodboard。它们展示的是成品或案例，不等于实现教程，也不自动证明可访问性、性能或代码质量。

| 网站 | 适合观察什么 | 适合接入的步骤 |
| --- | --- | --- |
| [Awwwards](https://www.awwwards.com/) | 网站视觉方向、页面叙事、转场和获奖案例 | 用于收集方向，再按配色、布局、字体、材质和动效六个维度拆解 |
| [Mobbin](https://mobbin.com/) | 移动端真实页面、用户流程和状态组合 | 用于检查任务路径、页面层级和组件状态；部分内容可能需要登录 |
| [Land-book](https://land-book.com/) | 落地页结构、首屏构图、排版和品牌表达 | 用于比较页面节奏和信息密度，不直接复制布局 |
| [Godly](https://godly.website/) | 前端网站视觉与交互动效案例 | 用于给动效命名、识别触发器和拆解运动机制 |
| [SiteInspire](https://www.siteinspire.com/) | 按风格和类型筛选的网站视觉案例 | 用于建立 moodboard 和比较页面构图 |
| [Behance](https://www.behance.net/) | 品牌、界面、动效和视觉过程展示 | 用于观察方案过程、视觉系统和成品呈现；需要自行核验可实现性 |
| [Dribbble](https://dribbble.com/) | 界面概念、组件细节和视觉方向 | 用于找局部视觉线索；必须用真实内容补做完整任务流程 |

参考网站的正确产出不是“找一个像的页面”，而是记录可迁移规则：哪些层级关系值得保留、哪些颜色承担强调、哪些动作对应什么输入、哪些构图依赖特定素材。随后把规则转写为项目自己的结构、变量和检查项。

## 按三个技能组织资源的使用路径

### `interface-design-process`

1. 先写核心任务、信息结构和已有成果。
2. 选择一套平台或产品语境接近的规范，例如 Apple HIG、Material 3、Carbon、Fluent、Polaris 或 Atlassian。
3. 用 Mobbin、Land-book、SiteInspire、Awwwards 或 Behance 收集少量参考。
4. 按配色、布局与留白、字体与层级、形状与比例、材质与光影、动效六个维度拆解参考。
5. 把稳定规则和主题变量写进项目风格表，再用真实内容逐轮检查。
6. 组件行为需要现成基础时，再比较 shadcn/ui、Radix、Headless UI 或 MUI。

### `web-interaction-and-motion`

1. 先写触发器、反应对象、变化机制、时间关系和结束或恢复状态。
2. 简单状态使用现有 CSS 或工程能力；布局和手势联动可考虑 Motion。
3. 多对象先后、并行或进度同步可考虑 GSAP；需要可视化场景编排可考虑 Theatre.js。
4. 滚动是连续输入时再考虑 Lenis，并把滚动进度映射到明确的对象和状态。
5. 需要视频模板或导出时考虑 Remotion；已有交互动画资产时比较 Lottie 和 Rive；只需要轻量 DOM/SVG 动画时也可比较 anime.js。
6. 需要二维分层时先比较 Canvas、SVG、CSS 和逐帧素材；确有相机、灯光、几何关系时再进入 Three.js 或 React Three Fiber。
7. 在真实运行环境检查方向、接缝、恢复、键盘操作和加载成本。

### `immersive-web-storytelling`

1. 先写体验目标、观看推进、空间关系、内容接续和稳定特征。
2. 按环境、空间边界、过渡层、关键对象等职责拆素材，并记录缺口。
3. 用低成本二维分层或短片段试作检查构图、遮挡、节奏和接续。
4. 需要页面滚动推进时，可组合 Lenis 与现有动画控制；需要真实空间关系时比较 Three.js、React Three Fiber 和 Drei。
5. 需要镜头、对象和时间线反复调整时考虑 Theatre.js 或 GSAP。
6. 动态素材内部运动和页面中的位置变化分别控制；逐帧、Lottie、Rive 或视频按交互精度和加载预算选择。
7. 通过试作确认体验成立后，再提高分辨率、素材质量和实现复杂度。

## 资源选择记录模板

```text
目标体验或任务：<当前项目要解决什么>
使用技能：<interface-design-process / web-interaction-and-motion / immersive-web-storytelling>
参考规范：<选择的规范及其适用理由>
视觉参考：<案例网站及提取出的规则>
制作工具：<选择的库或框架及其解决的问题>
不采用的方案：<为什么当前需求不需要其他工具>
验证方式：<真实内容、交互状态、截图、性能或输出检查>
待验证项：<仍未在当前项目执行的部分>
```
