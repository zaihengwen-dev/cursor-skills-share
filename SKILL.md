---
name: bujue-design-system
description: Applies 不觉 design rules across 平板/手机/Web with 白版/黑板 themes. Use when the user provides UI 规范/设计系统/Token，或要求按不觉规范实现 Figma/前端样式。
---

# 不觉设计系统（多平台 + 白版/黑板）

## 总则（优先级）

- **本技能是最高优先级视觉规范**：当用户要求“按不觉规范/规则”时，优先使用这里的 tokens 与约定。
- **用户新增/修订优先**：用户后续提供的新规则覆盖同名条目。

## 颜色使用原则（重要）

- **主视觉以黑白灰为主**：除非用户明确要求，否则不要引入彩色做“主色/强调色”。
- **红色 `#E60023` 仅用于错误/危险语义**：如报错提示、危险操作（删除/不可逆）确认、校验错误状态。
- 其他颜色（如紫菜星球/盘八斗主色）**默认不用于该软件主流程 UI**，只有在用户明确指定业务场景需要时才使用。

## 适用范围（平台 + 主题）

### 平台（端）

- **平板**：文字样式见“文字样式（平板）”。圆角常用 **4**。
- **手机**：文字样式见“文字样式（手机）”。圆角常用 **4**。
- **Web**：文字样式见“文字样式（Web）”。圆角常用 **8**。

### 主题（白版/黑板）

白版 = 亮色主题；黑板 = 暗色主题。两者共用同一套语义命名，但具体颜色值/透明度不同。

使用约定：
- 需要同时支持两套主题时：**同一语义 token 在白版/黑板各取对应值**。
- 若只做单主题：按用户指定主题（默认白版）。

## 圆角规则（跨平台）

- **平板**：常用 `4`
- **手机**：常用 `4`
- **Web**：常用 `8`

> 若组件明确为胶囊/圆形头像：使用 `大圆角100`（与平台无关）。

## 字体家族（跨平台）

- 字体：**Source Han Sans CN**（Regular / Medium / Normal）
- 默认：`letterSpacing = 0%`（除非用户另行规定）

## 颜色 Tokens（语义名 → 值）

### 白版

- `白版/文字 #333`: `#333333` + `#000000 @20%`
- `白版/文字 #666`: `#666666`
- `白版/文字 #999`: `#999999`
- `白版/错误色 #E60023`: `#e60023`（仅错误/危险语义）
- `白版/禁用色 #ccc`: `#cccccc`
- `白版/白色 #FFF`: `#ffffff`
- `白版/背景色1级`: `#fafafa`
- `白版/背景色2级 #F5F5F5`: `#f5f5f5`
- `白版/背景色3级`: `#f1f1f1`
- `白版/背景色4级 EDEDED`: `#ededed`
- `白版/背景色5级 #E2E2E2`: `#e2e2e2`
- `白版/线框色1级 #EBEBEB`: `#ebebeb`
- `白版/线框色2级 #DBDBDB`: `#dbdbdb`
- `白版/选中色浅 #FDE6E9`: `#fde6e9`
- `白版/APP导航栏底部透明度 #FFF 80%`: `#ffffff @80%`

### 黑板

- `黑板/文字 #FFF 85%`: `#ffffff @85%`
- `黑板/文字 #FFF 65%`: `#ffffff @65%`
- `黑板/文字 #FFF 45%`: `#ffffff @45%`
- `黑板/禁用色  #FFF 25%`: `#ffffff @25%`
- `黑板/线框色 #FFF 15%`: `#ffffff @15%`
- `黑板/背景色1 #000`: `#000000`
- `黑板/背景色2 #151515`: `#151515`
- `黑板/图片底部图片预览色`: `#1f1f1f`
- `黑板/背景色3 #2A2A2A`: `#2a2a2a`
- `黑板/背景色4 #454545`: `#454545`
- `黑板/标签黑底#000 30%`: `#000000 @30%`

### 其他品牌色（默认不使用）

- `紫菜星球`: `#8864de`
- `盘八斗主色`: `#3a7bff`

### 透明度写法（重要）

- `#RRGGBB @xx%` 表示 alpha。
- 生成代码时：
  - **CSS**：优先用 `rgba(r,g,b,a)` 或 `#RRGGBBAA`
  - **Figma**：用颜色 + opacity/alpha

## 效果样式/阴影/模糊

- `白底阴影`: DROP_SHADOW `x=0 y=0 blur=12` `#000000@6%`
- `灰底阴影`: DROP_SHADOW `x=0 y=0 blur=12` `#000000@4%`
- `悬浮框阴影`: DROP_SHADOW `x=0 y=0 blur=12` `#000000@8%`
- `APP模糊+悬浮窗`: DROP_SHADOW `#000000@8%` + BACKGROUND_BLUR `80px`
- `APP导航栏模糊`: BACKGROUND_BLUR `80px`

## 文字样式（平板）

（你最早给的那套：32/48、20/30、18/27、14/21、12/19、10/15 等）

- `标题/超大标题Medium`: Medium; `32px`; `lineHeight=48px`
- `标题/大标题Regular`: Medium; `20px`; `lineHeight=30px`
- `标题/中标题Regular`: Medium; `18px`; `lineHeight=27px`
- `标题/小标题Medium`: Medium; `14px`; `lineHeight=21px`
- `标题/小标题Regular`: Regular; `14px`; `lineHeight=21px`
- `正文/正文大/常态Normal`: Normal; `14px`; `lineHeight=21px`
- `正文/正文大/输入Normal`: Normal; `14px`; `lineHeight=24px`
- `正文/正文中/常态Normal`: Normal; `12px`; `lineHeight=19px`
- `正文/正文中/多行Normal`: Normal; `12px`; `lineHeight=21px`
- `正文/正文中/输入Normal`: Normal; `12px`; `lineHeight=24px`
- `正文/正文小/常态Normal`: Normal; `10px`; `lineHeight=15px`

## 文字样式（Web）

（来自你截图的右侧 Text styles）

### 大标题

- `超大标题`: Medium; `40px`; `lineHeight=60px`
- `大标题`: Medium; `20px`; `lineHeight=30px`
- `大标题两行`: Medium; `20px`; `lineHeight=36px`

### 弹窗标题

- `弹窗标题 Medium`: Medium; `16px`; `lineHeight=24px`
- `弹窗标题 Regular`: Regular; `16px`; `lineHeight=24px`
- `弹窗标题 Normal`: Normal; `16px`; `lineHeight=24px`

### 正文常规14

- `正文常规14 Medium`: Medium; `14px`; `lineHeight=21px`
- `正文常规14 Regular`: Regular; `14px`; `lineHeight=21px`
- `正文常规14 Normal`: Normal; `14px`; `lineHeight=21px`

### 正文常规12

- `正文常规12 Normal`: Normal; `12px`; `lineHeight=19px`
- `正文常规12 Medium`: Medium; `12px`; `lineHeight=19px`

### 辅助信息10

- `辅助信息 Normal`: Normal; `10px`; `lineHeight=15px`
- `辅助信息 Regular`: Regular; `10px`; `lineHeight=15px`

### 特殊

- `特殊`: Regular; `8px`; `lineHeight=12px`

## 文字样式（手机）

（来自你截图的右侧 Text styles）

### 标题&导航栏 / 常态

- `标题超大 Regular`: Regular; `20px`; `lineHeight=30px`
- `标题大 Regular`: Regular; `16px`; `lineHeight=24px`
- `标题 Regular`: Regular; `14px`; `lineHeight=21px`
- `标题 Normal`: Normal; `14px`; `lineHeight=21px`
- `标题小 Normal`: Normal; `12px`; `lineHeight=19px`
- `标题备注 Normal`: Normal; `10px`; `lineHeight=15px`

### 标题&导航栏 / TAB

- `TAB 选中`: Medium; `14px`; `lineHeight=21px`
- `TAB 未选中`: Normal; `14px`; `lineHeight=21px`

### 正文 / 正文大

- `正文大 常态`: Normal; `14px`; `lineHeight=21px`
- `正文大 输入`: Normal; `14px`; `lineHeight=24px`

### 正文 / 正文中

- `正文中 常态 Medium`: Medium; `12px`; `lineHeight=19px`
- `正文中 常态 Normal`: Normal; `12px`; `lineHeight=19px`
- `正文中 多行 Normal`: Normal; `12px`; `lineHeight=21px`
- `正文中 输入`: Normal; `12px`; `lineHeight=24px`

### 正文 / 正文小

- `正文小 常态10`: Normal; `10px`; `lineHeight=15px`
- `正文小 分类卡片`: Regular; `10px`; `lineHeight=13px`
- `正文小 常态8`: Normal; `8px`; `lineHeight=12px`

## 变量集合（Figma Variables）

- Collection：模式包含 `4一级圆角`、`2二级圆角`、`大圆角100`（变量数=4）

## 命名约定（组件/变体）

- 组件：`业务前缀-组件名`（例：`创意版-素材卡`）
- 变体属性：中文业务语义（例：`状态`、`尺寸`、`类型`）
- 变体值：中文（例：`默认`、`添加`、`禁用`、`选中`）