---
name: rembrandt-motion-portrait
description: Edit a user-provided portrait into a realistic cinematic Rembrandt-lighting image with one strong side key lighting only half of the face, deep shadow elsewhere, a pure black background, and horizontal motion-blur trails behind the subject. Use when the user asks for 伦勃朗拖影人像、伦勃朗光、伦勃朗光影、半脸强光、暗调电影人像、横向动态拖影、速度感人像, Rembrandt lighting, chiaroscuro portrait lighting, or the same established photo treatment on an uploaded image.
---

# 伦勃朗拖影人像

把用户提供的照片编辑为写实原生摄影质感的暗调电影人像。以人物身份一致性为第一优先级，以单束半脸强光、深邃阴影、纯黑背景和人物后方横向速度拖影为固定视觉语言。

## 调用方式

上传照片后，可以直接说：

> 用伦勃朗光处理这张照片

## 工作流程

1. 先查看原图，判断主体、脸部朝向、原始光向、画幅和可用于拖影的空间。
2. 有原图时始终执行图像编辑，不从零重绘人物。若目标图片无法随请求传入，要求用户重新附图。
3. 默认选择最符合原图、最有利于保留人物辨识度的一侧作为受光侧；用户指定左侧或右侧时严格服从。
4. 使用图像生成/编辑工具一次性施加完整效果。不要用 Python 或普通图像脚本代替生成式图像编辑。
5. 查看成片并逐项检查。若身份漂移、脸部被拖糊、背景不纯黑、阴影不够深、出现多余光源，或拖影侵蚀了主体边缘，继续编辑同一结果以修正，不改变已正确的区域。
6. 交付最终图时简要说明已采用此风格。尽可能呈现清晰、自然的细节，分辨率以实际输出为准；未核实像素尺寸时，不宣称具体分辨率。

## 固定视觉规范

### 人物与构图

- 尽量保留原图人物的辨识度、五官特征、脸型、年龄感、肤色、发型、表情、姿态和服装，减少不必要的变化；默认沿用原图构图。人物相似度作为编辑目标，不承诺与原图完全一致。
- 保持眼睛、睫毛、皮肤纹理和受光侧轮廓清晰。允许景深，但不要把主体面部做成运动模糊。
- 多人画面默认把效果施加于视觉主角；主角无法判断时才询问。

### 伦勃朗光

- 只使用一束强烈、集中的侧上方主光，约从人物侧前方 45°、略高于眼睛的位置照入。
- 仅打亮约半张脸及少量相邻轮廓；另一半脸、身体与画面其他区域沉入深邃阴影。
- 保持强烈明暗对比、深黑阴影和受控高光。允许阴影侧颧部出现很小的经典伦勃朗三角光，但不得把阴影侧整体提亮。
- 禁止补光、轮廓灯、顶灯、环境光、霓虹光或第二光源。高光不得大面积过曝，暗部不得发灰。

### 背景与速度拖影

- 将背景处理为均匀纯黑，不保留场景、纹理、渐变、光斑或杂物。
- 按固定图层关系构图：最底层为纯黑背景；中间层为水平错位的半透明模糊残影；最上层为完整、不透明、清晰的原始主体。
- 在人物身后生成一层或数层与主体轮廓相关的独立模糊影子。将影子沿水平方向明显错开，形成可辨认的延迟曝光残影，并让其透明度由近到远逐层降低。
- 只模糊中间层的影子副本。禁止直接模糊、拉伸、擦除、羽化、透明化或溶解最上层主体的任何边缘与身体区域。
- 让前景主体遮挡位于其后的残影；残影不得透过主体身体。主体外轮廓从头到脚必须连续、完整、锐利且保持实心，不得呈现“消散一半”的效果。
- 让拖影方向一致并始终位于主体之后。主体当前脸部必须保持唯一且清晰；不要让残影穿过眼睛或覆盖面部，不要生成清晰的第二张脸、多余肢体、实体分身或放射状缩放模糊。

### 摄影质感

- 采用写实原生摄影风格：真实皮肤毛孔、自然细小瑕疵、准确毛发、真实镜头成像与克制的电影调色。
- 追求电影级暗调、自然细节与丰富明暗层次，同时避免 HDR 光晕、过锐、蜡像皮肤、磨皮和生成式塑料感。
- 默认保留原图的画幅比例与摄影视角。若用户未指定色调，使用自然肤色、轻微暖色主光和中性偏冷的黑色阴影。

## 编辑提示词骨架

根据原图实际人物和构图补全方括号内容，并把所有约束写进同一次编辑请求：

> Edit the supplied photo, aiming to retain the subject's recognizable likeness, facial features, age, skin tone, hairstyle, expression, pose, clothing, camera angle, and original aspect ratio while minimizing unnecessary changes. Create a photorealistic native-camera cinematic portrait. Use exactly one strong, focused Rembrandt-style key light from [chosen side], slightly above eye level, illuminating only about half of the face and a minimal adjacent contour. Let the other half of the face, the body, and all remaining areas fall into profound shadow. Keep highlights controlled and blacks deep; no fill light, rim light, ambient light, or secondary source. Replace the entire background with uniform pure black. Use this strict layer order: pure-black background at the back; one or more horizontally offset, semi-transparent blurred shadow silhouettes in the middle; the complete original subject, fully opaque and tack-sharp, in the foreground. The rear shadows must be distinct delayed-exposure echoes positioned behind the subject. Apply directional blur only to those rear shadow copies. Do not blur, smear, stretch, feather, fade, dissolve, erase, or make transparent any part or edge of the foreground subject. The foreground subject must occlude every overlapping rear shadow and retain one continuous, solid, crisp silhouette from head to toe. Keep the main face and eyes unique, unobscured, and anatomically natural. Real skin pores, individual hair detail, authentic lens rendering, cinematic contrast, restrained color grade, rich micro-detail, clear natural detail at the available output resolution. Minimize changes to the subject's likeness. Avoid facial motion blur, disappearing body edge, duplicate clear face, extra limbs, painterly look, CGI, plastic skin, beauty filter, gray background, texture, glow, text, or watermark.

## 成片验收

确认以下条件全部成立：

- 人物保有原图的主要辨识特征，五官无明显偏移，面部清晰且没有被拖影覆盖；如有可见差异，交付时如实说明。
- 画面只有一个明确主光源，受光范围约为半张脸，其余区域足够深暗。
- 背景视觉上为纯黑，没有可见环境信息或灰雾。
- 主体本人位于最前层，轮廓完整、实心、连续且锐利，没有任何边缘被模糊、羽化、透明化或消散。
- 横向拖影是位于人物身后的独立模糊影子，存在清楚的水平错位和透明度衰减；拖影被前景主体正确遮挡，主体本人没有糊掉或复制成实体分身。
- 最终效果是写实摄影而非插画、油画、3D 渲染或重度磨皮。
- 输出具备电影级对比与丰富细节；对实际分辨率的描述真实准确。
