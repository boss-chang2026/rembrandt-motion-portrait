# 伦勃朗拖影人像

**Rembrandt Motion Portrait**

把普通人像照片，变成带有半脸侧光、深邃阴影、纯黑背景与横向拖影的电影感人像。

这是一套供 AI 助手使用的图片编辑 Skill，包含编辑流程、视觉规范、英文提示词和成片检查要点。上传原图后，让具备图片编辑能力的 AI 按这套规则处理照片。

## 效果示例

效果对比图放在 [examples](examples/) 文件夹，命名为 `编号-before` 与 `编号-after`。示例图仅用于展示风格，实际结果取决于原图和所用图片模型。

## 效果特点

- **半脸侧光**：以侧上方主光塑造人物，形成鲜明的明暗对比。
- **纯黑背景**：去掉背景杂物，让注意力集中到人物上。
- **后景拖影**：在人物身后形成横向错位、逐渐变淡的模糊残影。
- **清晰主体**：以保留面部清晰度和完整轮廓为目标，尽量避免拖影覆盖五官或让身体边缘消散。
- **自然质感**：尽量保留人物辨识度、皮肤纹理与自然细节，减少不必要的外貌变化。

本 Skill 将伦勃朗风格光影与横向拖影结合，纯黑背景和拖影是这套风格的固定组成部分。

## 使用前需要什么

1. 一张准备编辑的人像照片。
2. 能读取 Skill 指令的 AI 助手，或可以接收完整编辑提示词的图片编辑工具。
3. 能基于上传原图进行生成式编辑的图片工具。

Skill 本身只提供指令，不包含图片模型、工具账号或调用额度。能否直接执行取决于所用 AI 助手实际接入的图片编辑能力。

## 安装与使用

本 Skill 只有 Markdown 文本，不依赖任何脚本、路径或操作系统，Windows、macOS、Linux 都可以使用。任何能读取文件或接收粘贴文本的 AI 都能按它工作，只要该 AI 能基于上传原图做生成式图片编辑。

按所用 AI 是否支持"技能目录"，选下面任一方式：

### 方式一：安装为 Skill

适用于支持本地技能目录的 AI 编程助手或 Agent 工具（例如 Claude Code、Codex、OpenClaw 及其他兼容 Agent Skills 格式的工具）。

将本仓库下载为文件夹，文件夹名称保持为 `rembrandt-motion-portrait`，并保留下面的结构：

```text
rembrandt-motion-portrait/
├── SKILL.md
├── README.md
├── LICENSE
├── agents/
│   └── openai.yaml
└── examples/
```

把整个文件夹复制进所用工具的技能目录，按该工具的方式刷新技能列表或开始新对话。不同工具的安装位置和发现方式不同，请以该工具的说明为准。

也可以把文件夹交给具备本地文件管理能力的 AI 助手，并告诉它：

> 请先检查这套 Skill 是否适用于当前环境。如果适用，把它安装到你的技能目录；如果已存在同名版本，先告诉我，不要覆盖。

安装后上传照片，直接说：

> 用伦勃朗光处理这张照片

也可以使用完整的技能名称：

> 用伦勃朗拖影人像处理这张照片，尽量保留我的长相和原图构图。

部分工具支持显式点名调用，写法各不相同，例如有的用 `/rembrandt-motion-portrait`，有的用 `$rembrandt-motion-portrait`，按所用工具的习惯写即可。

### 方式二：直接当提示词用

适用于没有技能目录的对话式 AI，例如豆包、通义、Kimi、ChatGPT、Gemini 等网页或 App，以及各类 AI 修图工具。

1. 打开 [SKILL.md](SKILL.md)，把全文复制下来；或者把 SKILL.md 文件本身作为附件上传。
2. 连同人像原图一起发给 AI，并说明：

> 请按这份说明处理我上传的这张照片。

如果该工具只接收一段提示词，可以只取 SKILL.md 中的"编辑提示词骨架"，把 `[chosen side]` 替换为 `the left` 或 `the right`，连同原图一起提交。

无论哪种方式，能否出片取决于所用 AI 是否接入了基于原图编辑的图片模型。

## 更多使用示例

**默认风格**

> 把这张照片处理成伦勃朗拖影人像，黑色背景，半脸侧光，人物后面有横向拖影。

**指定光向**

> 用伦勃朗拖影人像处理这张图，主光从画面右侧照入，保持原图比例和姿态。

**修正拖影**

> 这张图的拖影盖住了脸。请保留已经合适的光影，把拖影放回人物后方，让主体边缘保持完整。

## 工作流程

查看原图 → 选择合适光向 → 基于原图编辑 → 检查人物、光影和拖影 → 按需要修正 → 交付图片。

## 效果边界

- 人物相似度是编辑目标，不保证五官与原图完全一致；结果受原图和图片模型影响。
- 清晰度与分辨率以实际输出为准，不承诺固定像素尺寸。
- 文件中的图层顺序用于描述视觉关系，不表示会交付可分层编辑的工程文件。
- 不同模型对光向、背景和拖影的理解可能不同，部分图片需要多轮修正。

## 文件说明

| 文件 | 用途 |
| --- | --- |
| `SKILL.md` | 技能名称、触发条件、编辑流程、视觉规范与英文提示词 |
| `agents/openai.yaml` | 可选配置，仅供支持该格式的工具读取显示名称与默认调用提示，其他工具可忽略 |
| `README.md` | 项目介绍与使用说明 |
| `examples/` | 效果对比图 |
| `LICENSE` | MIT 许可证 |

核心编辑说明不绑定某个图片模型；其他 AI 工具能否加载 Skill 或使用附带配置，需以实际支持情况为准。

## English overview

Rembrandt Motion Portrait is an AI image-editing skill for creating cinematic portraits with Rembrandt-style side lighting, deep shadows, a pure black background, and horizontal motion echoes behind the subject.

It includes an editing workflow, visual constraints, an English prompt template, and review criteria. It aims to preserve recognizable facial features and a sharp foreground subject while keeping blurred echoes behind the portrait. Likeness and output resolution depend on the source image and editing model.

It is plain Markdown with no scripts or OS-specific parts, so it works on Windows, macOS and Linux. Install it as a skill in any agent that supports a skills directory, or paste SKILL.md (or attach the file) together with the photo into any chat-based AI that can edit images. An image-editing tool that accepts a reference photo is required. This repository provides instructions, not an image model or API access.