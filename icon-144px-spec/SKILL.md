---
name: icon-144px-spec
description: 按 144px 图标视觉规范创建或修正 Icons(细) 图标组件集。用于“画一个新 icon”“按规范重画 icon”“修正线宽/重心/keyline”“补齐颜色与禁用态变体”等场景。默认操作 Untitled 的 ◉  Icons(细）画布，并与 figma-use 联动执行。
---

# Icon 144px Spec

## 适用场景
- 用户说“按规范画 icon / 再画一个 icon / 重画 icon / 这个 icon 不符合规范”。
- 用户提供 icon 视觉规范（144px 体系、keyline、描边、圆角、视觉重心）。
- 需要在 Figma 中新增 icon 组件集和颜色变体。

## 前置要求
1. 先加载 `figma-use` skill，再调用 `use_figma`。
2. 默认仅操作 `Untitled` 的 `◉  Icons(细）` 画布。
3. 未经用户确认，不修改已有命名体系（如 `Property 1=xxx-黑/666/...`）。

## 输入约定
每次执行前尽量确认以下参数（若用户未给，按默认值）：
- `iconName`：例如 `水杯(细）`
- `keylineType`：`circle80` / `square72` / `horizontal84x64` / `vertical64x84`
- `variantPalette`：默认 `黑, 666, 999, 白, 红, 禁用-亮, 禁用-暗, 紫`
- `themeScope`：默认 `Icons(细)`
- `needOutlineStroke`：默认 `false`（仅导出前才 true）

## 硬性规范（必须遵守）
- 画布基准：每个 variant 使用 `144 x 144`。
- Keyline：
  - Circle: `80 x 80`
  - Square: `72 x 72`
  - Horizontal: `84 x 64`
  - Vertical: `64 x 84`
- 描边：`strokeWeight = 6`。
- 描边对齐：`Inside`。
- 端点样式：统一 `Round Cap`。
- 转角样式：统一 `Round Join`。
- 视觉重心：允许沿垂直方向微调 `2-4px`。
- 复杂图标：允许整体缩小 `5%-10%`，但要说明原因。

## 标准工作流
1. **定位画布**
   - 切到 `◉  Icons(细）` 页面。
   - 在现有内容右侧创建新分组 frame（避免覆盖旧内容）。

2. **创建组件结构**
   - 分组 frame 名：`{iconName}-规范`（或用户指定名）。
   - 每个变体建立 `COMPONENT`（144x144）。
   - 组合为 `COMPONENT_SET`，名称使用 `{iconName}`。

3. **绘制图形**
   - 先放 keyline（可隐藏）再画图形。
   - 使用 6px inside stroke、round cap/join。
   - 根据图形复杂度做必要的重心/缩放调整。

4. **生成变体**
   - 变体命名保持现有规则：`Property 1={iconName}-{颜色或状态}`。
   - 默认生成：黑/666/999/白/红/禁用-亮/禁用-暗/紫。

5. **质量检查**
   - 图形是否在 keyline 内（考虑 inside stroke）。
   - 线宽、端点、圆角是否统一。
   - 复杂图标是否说明了缩放策略。

6. **导出前检查（仅当用户要求）**
   - Outline Stroke
   - 清理隐藏层与多余点

## 返回结果格式
每次执行后返回：
- `componentSetId`
- `createdNodeIds`
- `mutatedNodeIds`
- `keylineType`
- `strokeSpec`（6px inside + round cap/join）
- `opticalAdjustment`（是否做 2-4px 微调）
- `scaleAdjustment`（是否做 5%-10% 缩放）

## 常见修正规则
- **图标看起来偏小**：先检查是否误用 24px/96px 逻辑尺寸，改回 144 体系 keyline。
- **图标“掉下去”**：整体上移 2-4px。
- **复杂图标发糊/拥挤**：在 keyline 内整体缩小 5%-10%。
- **跨主题颜色不清晰**：保持变体命名不变，仅替换对应颜色值。

## 示例指令
- “按 icon-144px-spec 画一个 `水杯(细）`，keyline 用 `vertical64x84`。”
- “按 icon-144px-spec 把这个 icon 重画成 6px inside stroke，保留原命名。”
- “按 icon-144px-spec 给 `搜索(细)` 补齐禁用亮/禁用暗变体。”
