# UI 与网页设计蒸馏技能

这个仓库收录了从 `01_UI_and_Web_Design` 相关视频中蒸馏出的 3 个可复用技能。每个技能都包含一个 `SKILL.md` 和一份来源证据，方法步骤带有视频时间戳引用。

## 技能目录

### `interface-design-process`

用于把 AI 生成的界面从“功能都有但不好看”打磨成可持续迭代的产品界面，覆盖功能框架、参考拆解、主题变量、逐轮反馈和回归检查。

主要来源：V02、V19；V06、V07、V08、V16、V17 作为展示参考。

### `web-interaction-and-motion`

用于把网页动效需求翻译成可执行的交互语言，并在生成式素材、CSS、原生 JavaScript、Motion、GSAP、Canvas、Three.js 和逐帧精灵图之间做选择。

主要来源：V09、V11、V14；V08、V16、V17 作为展示参考。

### `immersive-web-storytelling`

用于把壁画、插画或文化故事拆成可进入的沉浸式网页，覆盖空间分层、透明 PNG、灰度蒙版、角色一致性、动态素材合成和动作参考。

主要来源：V13；V10、V12 作为展示参考。

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

三个技能均已通过验证。来源视频使用 `Whisper small` 转写，并结合关键帧、联系表、时间线和全分辨率画面核对；展示类视频仅用于视觉参考，没有补写未展示的实现步骤。
