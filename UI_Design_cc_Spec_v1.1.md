# ShuttleGo App — UI 设计规范文档
## UI Design Specification / UI 设计规格说明书

**版本 Version：** v1.1（色彩已同步官网源码）
**日期 Date：** 2026-04  
**平台 Platform：** iOS & Android  
**语言 Language：** 双语 English / 中文  

> **⚠️ 色彩来源说明：** 本文档第一章色彩系统（1.2节）中的所有色值，均直接提取自 `www.shuttlego.com.au` 官网 `index.html` CSS 变量，为官方品牌规范色，与网站保持完全一致。

---

## 一、全局设计系统 Global Design System

### 1.1 品牌定位 Brand Identity

| 项目 | 说明 |
|---|---|
| App 名称 | ShuttleGo |
| 定位 | 澳大利亚 & 新西兰羽毛球 / 匹克球综合门户平台 |
| 目标用户 | 运动爱好者、场馆管理员、俱乐部组织者 |
| 核心价值 | 本地化、社群化、便捷化 |

---

### 1.2 色彩系统 Color System

> ✅ 以下色值直接提取自 shuttlego.com.au 官网源代码 `index.html`，为官方品牌色，请严格遵守。

#### 品牌三原色 Brand Palette

| 名称 | 变量 | 色值 | 预览 | 用途 |
|---|---|---|---|---|
| **Brand Blue** | `--blue` | `#2391DC` | 🔵 | 主蓝色，主要按钮、链接、选中态、用户地图点 |
| **Brand Orange** | `--orange` | `#FE870A` | 🟠 | 强调橙色，Token、价格、高亮、Logo 字 |
| **Brand Green** | `--green` | `#B7DA28` | 🟡 | 点缀黄绿色，分割线、区块标签、badge |
| **Blue Dark** | `--blue-dark` | `#1A6FA8` | — | 蓝色悬停深化态 |
| **Orange Dark** | `--orange-dark` | `#D96E00` | — | 橙色悬停深化态 |

#### Light Mode（默认）

| 变量名 | 色值 | 用途 |
|---|---|---|
| `--text-dark` | `#1A1A2E` | 主标题、卡片标题 |
| `--text-mid` | `#3A3A5C` | 正文、导航链接 |
| `--text-light` | `#6B6B8A` | 说明文字、辅助信息 |
| `--bg-light` | `#FFF9F3` | 页面主背景（暖白） |
| `--bg-card` | `#FFFFFF` | 卡片背景 |
| `--bg-section` | `#FDF4EA` | 区块交替背景（淡橙暖色） |
| `--border` | `rgba(183,218,40,0.30)` | 卡片描边（品牌绿半透明） |
| `--shadow` | `0 8px 40px rgba(35,145,220,0.10)` | 卡片阴影（蓝色调） |
| `--page-bg-start` | `#FEF8F0` | 页面渐变背景起点（暖橙白） |
| `--page-bg-end` | `#F0F5EA` | 页面渐变背景终点（淡绿白） |

**导航栏背景：** `rgba(255,249,243,0.88)` + `backdrop-filter: blur(18px)`

#### Dark Mode（`[data-theme="dark"]`）

| 变量名 | 色值 | 用途 |
|---|---|---|
| `--text-dark` | `#F0F0FF` | 主文字（近白带蓝调） |
| `--text-mid` | `#C0C0E0` | 正文 |
| `--text-light` | `#A0A0C0` | 辅助文字 |
| `--bg-light` | `#1E1E3A` | 页面主背景（深蓝紫） |
| `--bg-card` | `#252545` | 卡片背景 |
| `--bg-section` | `#181830` | 区块交替背景 |
| `--border` | `rgba(183,218,40,0.25)` | 卡片描边（品牌绿半透明） |
| `--shadow` | `0 8px 40px rgba(0,0,0,0.30)` | 卡片阴影 |
| `--page-bg-start` | `#0F111A` | 页面渐变背景起点 |
| `--page-bg-end` | `#1A1A2E` | 页面渐变背景终点 |

**导航栏背景（Dark）：** `rgba(18,18,42,0.88)` + `backdrop-filter: blur(18px)`

#### 功能状态色（通用）

| 用途 | 色值 | 说明 |
|---|---|---|
| 成功 / Open | `#22C55E` | 场馆开放、报名成功 |
| 警告 / 待处理 | `#F59E0B` | 待付款状态 |
| 错误 / Closed | `#EF4444` | 场馆关闭、退款 |
| 用户地图蓝点 | `#2391DC`（同 `--blue`） | 地图上用户位置 |
| 活动地图 Pin | `#FE870A`（同 `--orange`） | 地图上活动标记点 |

#### 渐变规范

| 用途 | 渐变值 |
|---|---|
| 数字大标题 | `linear-gradient(135deg, #2391DC, #FE870A)` |
| Token 图标 | `linear-gradient(135deg, #FE870A, #2391DC)` |
| 邀请码背景 | `linear-gradient(135deg, rgba(35,145,220,0.10), rgba(183,218,40,0.10))` |
| 页面背景 | `linear-gradient(135deg, var(--page-bg-start), var(--page-bg-end))` |
| 分割线 | `linear-gradient(90deg, transparent, #B7DA28, transparent)` |

---

### 1.3 字体系统 Typography

> ✅ 字体与官网保持完全一致，通过 Google Fonts 加载：
> `Playfair Display`（展示/标题）+ `Montserrat`（正文/UI）

| 用途 | 字体 | 字重 | 大小 |
|---|---|---|---|
| App 品牌名 Logo | `Playfair Display` | 700 Bold | 24px |
| 页面大标题 H1（Hero） | `Playfair Display` | 900 Black | `clamp(2.8rem, 7vw, 5.5rem)` |
| 区块标题 H2（Section） | `Playfair Display` | 700 Bold | `clamp(2rem, 4vw, 3.2rem)` |
| 数字统计大字 Stat | `Playfair Display` | 900 Black | `3rem` |
| 卡片标题 H3 | `Playfair Display` | 700 Bold | `1.4rem` |
| 正文 Body | `Montserrat` | 400 Regular | `14–16px` |
| 导航链接 Nav | `Montserrat` | 600 SemiBold | `0.82rem`，全大写 |
| 辅助说明 Caption | `Montserrat` | 400 Regular | `0.78rem` |
| 标签 Tag / Badge | `Montserrat` | 700 Bold | `0.68–0.72rem`，全大写 |
| 按钮文字 Button | `Montserrat` | 700 Bold | `0.88rem` |
| Slogan 副标题 | `Playfair Display` | 400 Italic | `clamp(1.1rem, 2.5vw, 1.6rem)` |

**Google Fonts 引入：**
```
Playfair Display: ital,wght@0,400;0,600;0,700;0,900;1,400;1,700
Montserrat: wght@300;400;500;600;700
```

中文字体 fallback 顺序：`PingFang SC` → `Noto Sans SC` → `sans-serif`

---

### 1.3-A 图标资源规范 Icon Assets

| 图标用途 | 资源来源 | 规格说明 |
|---|---|---|
| App 品牌 Logo（开屏、登录页） | `app.png`（官网同源） | 开屏 `96×96px`，登录页 `64×64px`，圆角 `border-radius: 22px / 16px` |
| 匹克球运动图标 | `pickleball-small-200.png` | 使用 `<img>` 替代 emoji，CSS class `.pb-icon`，尺寸 `1em×1em`（随字号缩放）；商品卡片大图区域使用 `64×64px` |
| 城市定位图标（Header） | 内联 SVG | 蓝色渐变水滴形 Pin，`16×20px`，渐变 `#55BBFF → #1A6FA8`，内含白色实心圆 |
| 地图视图切换图标（Map 按钮） | 内联 SVG | 细线轮廓水滴形 Pin，`13×16px`，stroke-only 无填充，内含小圆圈，使用 `currentColor` |

---

### 1.4 玻璃拟态规范 Glassmorphism Rules

> ✅ 官网使用玻璃导航栏 + 卡片阴影体系，App 在此基础上强化 backdrop-filter 应用范围。

**导航栏 / 底栏：**
```
background: rgba(255,249,243,0.88)        /* Light */
background: rgba(18,18,42,0.88)           /* Dark */
backdrop-filter: blur(18px)
border-bottom: 1.5px solid rgba(183,218,40,0.30)
```

**卡片 Card：**
```
background: var(--bg-card)                /* #FFFFFF / #252545 */
border: 1.5px solid var(--border)         /* rgba(183,218,40,0.30) */
border-radius: var(--radius)              /* 18px */
box-shadow: 0 8px 40px rgba(35,145,220,0.10)
```

**悬停 Hover 态卡片：**
```
transform: translateY(-5px) 或 translateY(-6px)
box-shadow: 0 20px 50px rgba(35,145,220,0.14~0.16)
```

**半屏弹窗 Sheet（App 扩展）：**
```
background: var(--bg-card)
backdrop-filter: blur(24px)
border-radius: 32px 32px 0 0
border-top: 1.5px solid var(--border)
box-shadow: 0 -8px 40px rgba(35,145,220,0.12)
```

---

### 1.5 圆角规范 Border Radius

> ✅ 官网定义 `--radius: 18px` 为基准，App 遵循此体系。

| 元素 | 圆角值 |
|---|---|
| 全屏半屏弹窗 | `32px`（顶部两角） |
| 主卡片 Card（`--radius`） | `18px` |
| 奖励/下载大卡片 | `24px` |
| 小卡片 / 时间选择 | `14px` |
| 按钮 Button（大/主要） | `50px`（胶囊形，官网一致） |
| Tag / Badge / Chip | `30px`（胶囊形） |
| 头像 Avatar | `50%`（圆形） |
| 输入框 Input | `12px` |
| 功能图标底座 | `14px` |
| 地图浮层卡片 | `24px`（顶部） |
| 地图气泡 Bubble | `10px` |

---

### 1.6 间距系统 Spacing

基础单位 4px，常用值：`4 / 8 / 12 / 16 / 20 / 24 / 32 / 40 / 48px`

- 屏幕左右边距：`16px`
- 卡片内边距：`16px`
- 卡片间距：`12px`
- 区块间距：`24px`

---

### 1.7 动效规范 Motion

> ✅ 官网定义 `--transition: 0.35s cubic-bezier(0.4,0,0.2,1)`，App 沿用此缓动曲线。

| 类型 | 参数 |
|---|---|
| 标准过渡（默认） | `0.35s cubic-bezier(0.4, 0, 0.2, 1)` |
| 页面切换（横向滑动） | `320ms cubic-bezier(0.4, 0, 0.2, 1)` |
| 半屏弹起 Sheet | `380ms cubic-bezier(0.34, 1.56, 0.64, 1)`（弹性） |
| 卡片悬停位移 | `translateY(-5px)，0.35s cubic-bezier(0.4,0,0.2,1)` |
| 卡片按压反馈 | `scale: 0.97, duration: 120ms` |
| 图标选中态 | `scale: 1.15, duration: 200ms` |
| 地图 Pin 弹出 | `translateY: 20px→0, opacity: 0→1, duration: 280ms` |
| 设置齿轮旋转 | `rotate(45deg)，0.35s cubic-bezier(0.4,0,0.2,1)` |
| 导航链接下划线 | `scaleX(0→1)，transform-origin: left，0.35s` |
| 用户地图蓝点脉冲 | `box-shadow 扩散 2s ease-in-out infinite`（见下） |
| 滚动出现动画 | `fade-up: opacity 0→1, translateY 40px→0, 0.7s ease` |
| 加载骨架屏 | shimmer 动画，周期 1.4s |

**用户地图点脉冲动画：**
```css
@keyframes pulse-user {
  0%,100% { box-shadow: 0 0 0 6px rgba(35,145,220,0.20); }
  50%      { box-shadow: 0 0 0 14px rgba(35,145,220,0.08); }
}
```

---

### 1.8 全局底部导航栏 Global Footer Navigation

位置：固定在屏幕底部，高度 `83px`（含安全区），玻璃背景。

```
[图标1] 首页 Home          → 跳转 P03 首页
[图标2] 订单 Orders        → 跳转 P04 订单页
[图标3] +号 Publish        → 中央突出，圆形，不跳转页面（触发底部弹窗）
[图标4] 商城 Shop          → 跳转 P05 装备商城
[图标5] 账户 Account       → 跳转 P06 账户页
```

**+号按钮规格：**
- 圆形直径：`60px`
- 位置：底部导航栏垂直中心，向上突出 `16px`，即一半在 footer 内一半露出
- 背景：渐变 `linear-gradient(135deg, #2391DC 0%, #B7DA28 100%)`（品牌蓝→品牌绿，与官网三色体系一致）
- 图标：白色 `+` 号，`28px`
- 阴影：`0 4px 20px rgba(35,145,220,0.45)`
- 点击交互：触发向上弹出半屏卡片（见 P03 发布弹窗）

**选中态：** 对应图标橙色填充 + 文字变为 `--color-primary`，其余灰色  
**未选中态：** 图标线框风格，文字 `--color-text-secondary`

---

## 二、页面清单 Page Index

| 编号 | 页面名称 | 备注 |
|---|---|---|
| P00 | 开屏动画 Splash Screen | |
| P01 | 引导页 Onboarding | 3 屏 |
| P02 | 登录 / 注册 Login & Register | |
| P03 | 首页 Home | 含活动查找 & 场馆搜索 |
| P03-A | 首页 — 活动查找 List 模式 | |
| P03-B | 首页 — 活动查找 Map 模式 | |
| P03-C | 首页 — 场馆搜索 List 模式 | |
| P03-D | 首页 — 场馆搜索 Map 模式 | |
| P03-E | 城市选择弹窗 | |
| P03-F | 发布弹窗 Publish Sheet | |
| P04 | 订单 Orders | |
| P05 | 装备商城 Shop | |
| P06 | 账户 Account | |
| P06-A | 账户 — 个人资料 Profile | |
| P06-B | 账户 — 设置 Settings | |
| P06-C | 账户 — 俱乐部 & 群管理 | |

---

## 三、页面详细规范 Page Specifications

---

### P00 开屏动画 Splash Screen

**页面用途：** App 冷启动时展示品牌，缓冲数据加载时间。  
**总时长：** 2.8 秒  
**背景：** 全屏渐变 `linear-gradient(135deg, #FEF8F0, #F0F5EA)`（官网品牌背景色）

#### 时间轴

```
0.00s - 0.20s  黑屏过渡淡入背景渐变
0.20s - 0.80s  羽毛球/匹克球组合图标从中心 scale(0.4)→scale(1.05)，ease-out-back
0.80s - 0.90s  图标轻微回弹 scale(1.05)→scale(1.0)
0.90s - 1.40s  "ShuttleGo" wordmark 从下方 20px 位移+淡入
1.40s - 1.90s  "Play Together · Anywhere" tagline 逐字淡入
1.90s - 2.50s  持续展示，底部显示 loading dots（3颗橙色圆点脉冲动画）
2.50s - 2.80s  整体向上位移 30px 并淡出，转场至 P01 或 P03（已登录用户）
```

#### 可点击元素

无（无跳过按钮，时长短）

---

### P01 引导页 Onboarding（3 屏）

**页面用途：** 首次安装后介绍核心功能，引导用户注册。  
**样式：** 全屏插画 + 底部文字卡片，横向可滑动，玻璃底部卡片

#### 第 1 屏 — 发现活动 Find Activities

- 顶部插画区（60% 屏高）：运动员打羽毛球的扁平风插画，橙色主调
- 底部玻璃卡片：
  - 标题：`Discover Local Games` / `发现附近活动`
  - 说明：`Find badminton & pickleball sessions near you, anytime.` / `随时找到附近的羽毛球和匹克球活动`
  - 页码指示点：3个圆点，第1个橙色，其余灰色

#### 第 2 屏 — 加入俱乐部 Join Clubs

- 顶部插画区：团队集合插画，人物多样性体现
- 底部玻璃卡片：
  - 标题：`Join Clubs & Groups` / `加入俱乐部与群组`
  - 说明：`Connect with players of your skill level and play regularly.` / `与同水平球友联系，定期一起打球`

#### 第 3 屏 — 装备商城 Shop & Token

- 顶部插画区：装备陈列插画（球拍、球、配件）
- 底部玻璃卡片：
  - 标题：`Gear Up with Tokens` / `用 Token 换装备`
  - 说明：`Earn tokens through activities and redeem premium gear.` / `参与活动赚取 Token，兑换优质装备`
  - [点击1] 按钮「Get Started / 立即开始」→ 跳转 P02 注册页（**蓝色 `#2391DC` 填充大按钮**，胶囊形 `border-radius: 50px`，全宽）
  - [点击2] 文字链「Already have an account? Log in / 已有账户？登录」→ 跳转 P02 登录页

#### 全局可点击元素（3屏共有）

- [点击3] 右上角「Skip / 跳过」文字按钮 → 跳转 P02 登录页
- [点击4] 整屏左右滑动手势 → 切换引导页（前后屏）
- [点击5] 底部页码指示点（3个） → 点击直接跳到对应屏

---

### P02 登录 / 注册 Login & Register

**页面用途：** 用户身份验证入口。  
**布局：** 顶部品牌区 + 底部玻璃表单卡片，背景保持开屏渐变

#### 顶部区域

- ShuttleGo Logo（图标+文字）居中
- 副标题：`Australia & New Zealand's #1 Racket Sports Community` / `澳新地区第一羽毛球匹克球社区平台`

#### Tab 切换区

- [点击1] Tab「Login / 登录」→ 显示登录表单
- [点击2] Tab「Register / 注册」→ 显示注册表单

#### 登录表单字段

- Email 输入框
- Password 输入框（带显示/隐藏密码切换图标）
- [点击3] 「Forgot Password? / 忘记密码？」文字链 → 跳转找回密码页
- [点击4] 「Log In / 登录」主按钮（橙色填充） → 验证成功跳转 P03

#### 注册表单字段

- Full Name / 全名 输入框
- Email 输入框
- Password 输入框
- Confirm Password 输入框
- [点击5] 「Register / 注册」主按钮 → 发送验证邮件，提示确认

#### 第三方登录区

- [点击6] 「Continue with Apple / 使用 Apple 登录」按钮
- [点击7] 「Continue with Google / 使用 Google 登录」按钮
- [点击8] 「Continue with WeChat / 使用微信登录」按钮（面向中文用户）

#### 状态

- 输入框聚焦态：border 变为橙色，轻微阴影
- 输入框错误态：border 红色，下方显示错误说明文字
- 按钮 Loading 态：按钮内显示旋转圆圈，禁用点击

---

### P03 首页 Home

**页面用途：** App 主入口，集合活动查找与场馆搜索两大核心功能。  
**布局：** 顶部固定功能区 + 内容滚动区 + 底部导航栏

---

#### 顶部固定区域（不随滚动移动）

**第一行：城市 + 搜索 + 运动选择**

左侧 — 城市选择器：
- 左侧前缀：蓝色渐变水滴形定位 SVG 图标（非 emoji，品牌蓝渐变 `#55BBFF → #1A6FA8`，内含白色实心圆）
- 仅显示城市名（如 `Sydney`），**不显示国家名或国旗**
- 右侧跟随向下箭头图标 `⌄`
- `flex-shrink: 0`，不随布局压缩
- [点击1] 城市选择器（图标+文字+箭头整体可点击）→ 弹出 P03-E 城市选择弹窗

中间 — 搜索胶囊（紧凑态）：
- `flex: 1`，撑满城市选择器与运动选择之间的剩余空间
- 样式：左侧 🔍 图标 + placeholder 文字（根据当前 Tab 变化）
- placeholder 文字超出时显示 `…`（`text-overflow: ellipsis`）
- [点击2] 搜索胶囊 → 弹出全屏搜索栏（见下方「搜索展开态」说明）

右侧 — 运动类型下拉菜单（Dropdown）：
- 样式：橙色半透明胶囊形（`background: rgba(254,135,10,0.12)`，`border: 1.5px solid rgba(254,135,10,0.35)`），右侧自定义 `▼` 箭头
- `flex-shrink: 0`，不随布局压缩
- 默认选中：`🏸 Badminton / 羽毛球`
- 选项列表（可扩展）：
  - `🏸 Badminton / 羽毛球`（默认）
  - `🏓 Pickleball / 匹克球`（匹克球图标使用 `pickleball-small-200.png`，非 emoji）
  - `All Sports / 全部运动`
- [点击3] 下拉菜单 → 展开选项列表，选择后实时过滤内容（见「运动类型筛选联动」）

> **搜索展开态：**  
> - 触发：点击搜索胶囊  
> - 样式：从顶部 `52px` 处居中弹出，宽度 `90%`，圆角 `14px`，蓝色边框 `1.5px solid #2391DC`，玻璃背景  
> - 动画：`opacity 0→1 + translateY(-10px→0)`，`0.25s cubic-bezier(0.34,1.56,0.64,1)`  
> - 背景遮罩：`rgba(0,0,0,0.45)` + `backdrop-filter: blur(2px)`  
> - 右侧 `✕` 关闭按钮，点击遮罩或按 `Escape` 键均可关闭  
> - placeholder 文字与当前 Tab 保持同步

> **运动类型筛选联动：**  
> - 选择 `羽毛球`：仅展示 `data-sport="badminton"` 及 `data-sport="both"` 的活动卡片、场馆卡片、地图 Pin  
> - 选择 `匹克球`：仅展示 `data-sport="pickleball"` 及 `data-sport="both"` 的活动卡片、场馆卡片、地图 Pin  
> - 选择 `全部`：展示所有内容  
> - 每张活动卡片、场馆卡片、地图 Pin 均需标注 `data-sport` 属性（`badminton` / `pickleball` / `both`）

**第二行：主 Tab（活动查找 / 场馆搜索）**

- [点击4] `Activities / 活动查找`（默认选中）→ 显示活动查找内容
- [点击5] `Venues / 场馆搜索`→ 显示场馆搜索内容
- 选中态：下方橙色底线 `2px`，文字橙色加粗；未选中：灰色文字
- Tab 切换带横向滑动过渡动画

**第三行：时间筛选卡片 + 过滤图标**（活动查找与场馆搜索 Tab 下均显示）

时间卡片区（横向排列，4个卡片 + 1个过滤图标）：
- [点击6] 时间卡片「Today / 今天」+ 日期（如 `Apr 19`）→ 选中态橙色背景白字
- [点击7] 时间卡片「Tomorrow / 明天」+ 日期（如 `Apr 20`）
- [点击8] 时间卡片「Day After / 后天」+ 日期（如 `Apr 21`）
- [点击9] 时间卡片「Later / 三天后」+ 日期（如 `Apr 22+`）
- [点击10] 过滤图标按钮（`⚙`）→ 弹出过滤器半屏弹窗（技能等级、费用范围、开放名额等）
- 卡片规格：宽约 72px，高 52px，圆角 12px，玻璃背景；上方小字日期，下方文字今天/明天等

**第四行：视图切换（List / Map）**

- [点击11] `☰ List`（列表视图）→ 切换至列表模式，选中橙色
- [点击12] `[定位Pin图标] Map`（地图视图）→ 切换至地图模式，选中橙色  
  Map 图标：细线轮廓水滴形 SVG Pin（stroke-only，无填充，内含小圆圈，使用 `currentColor` 继承选中/未选中颜色）
- 两个按钮右对齐，胶囊形切换控件

---

### P03-A 活动查找 — List 模式

**内容区：** 可垂直滚动的卡片列表，距顶部固定区高度留出间距

#### 活动卡片结构（每张卡片包含以下元素）

```
┌─────────────────────────────────────┐
│ [运动图标] [活动名称]        [距离标签] │
│ 🗓 日期时间   📍 场馆名称             │
│ ──────────────────────────────────  │
│ 💰 费用      👥 已报名/总人数          │
│ 🎯 技能等级   🟢 剩余名额 X spots     │
│                          [报名按钮] │
└─────────────────────────────────────┘
```

**字段说明：**

| 字段 | 内容示例 | 说明 |
|---|---|---|
| 运动图标 | 🏸 / 🏓 | 羽毛球或匹克球 |
| 活动名称 | `Sunday Casual Badminton` | H3 字号 |
| 距离标签 | `1.2 km` | 橙色胶囊 badge |
| 日期时间 | `Apr 19 · 9:00 AM – 11:00 AM` | 灰色小字 |
| 场馆名称 | `Ryde Aquatic Centre` | 灰色小字，可点击 |
| 费用 | `$8 / person` | |
| 报名人数 | `12 / 16 joined` | 进度条可视化 |
| 技能等级 | `All Levels / Intermediate` | 灰色胶囊 |
| 剩余名额 | `4 spots left` | 绿色（>5）/ 橙色（1-4）/ 红色（0 已满） |
| 报名按钮 | `Join / 报名` | 橙色小圆角按钮，已满变灰色「Full」 |

**可点击元素：**

- [点击1] 整张卡片 → 跳转活动详情页
- [点击2] 场馆名称文字链 → 跳转场馆详情页
- [点击3] `Join / 报名` 按钮 → 弹出报名确认弹窗（显示费用、场次、Token 可抵扣提示）
- [点击4] 卡片右上角收藏图标 ♡ → 切换收藏状态（灰色轮廓 ↔ 橙色实心）

**列表状态：**

- 加载中：显示 3 张骨架屏卡片（灰色 shimmer 动画）
- 空状态：居中插画 + `No activities found. Try adjusting filters. / 暂无活动，试试调整筛选条件`
- 下拉刷新：顶部橙色圆圈 loading 动画

---

### P03-B 活动查找 — Map 模式

**布局：** 全屏真实地图（MapKit / Google Maps）作为背景，顶部固定区叠加在地图上方（玻璃背景），底部地图控制浮层

**地图要求：**

- 使用真实地图（Apple Maps / Google Maps），地图样式：浅色（Light Mode 对应）/ 深色（Dark Mode 对应）
- **不显示任何 POI（餐厅、商店等兴趣点）**，保持地图干净清爽
- 仅显示道路、地名、区域边界

**地图元素：**

| 元素 | 描述 |
|---|---|
| 用户位置 | 蓝色实心圆点 `12px`，外圈蓝色半透明光晕，脉冲动画 |
| 活动 Pin | 橙色圆角方形（类似 iOS 地图 pin），内含🏸或🏓图标，大小 `36px` |
| 多个活动密集区 | 聚合 Cluster：橙色圆形 badge 显示数量，如 `5` |

**可点击元素：**

- [点击1] 活动 Pin → 地图下方弹出活动卡片（半屏，高度约 180px）

**活动卡片（地图模式底部）：**

```
┌────────────────────────────────────┐ ← 圆角顶部，玻璃背景
│ [🏸] Sunday Casual Badminton       │
│ Apr 19 · 9:00 AM   📍 1.2 km away  │
│ $8/person · 4 spots left           │
│                    [Join / 报名 →]  │
└────────────────────────────────────┘
```

- [点击2] 活动卡片整体 → 跳转活动详情页
- [点击3] `Join / 报名` 按钮 → 报名确认弹窗
- [点击4] 卡片外任意地图区域 → 关闭卡片，恢复正常地图视图
- [点击5] Cluster 圆形 badge → 地图缩放放大，展开聚合的活动 pins

> ~~右下角定位按钮已移除~~（已删除，不再显示）

---

### P03-C 场馆搜索 — List 模式

**切换方式：** 在顶部 Tab 点击「Venues / 场馆搜索」后，列表内容切换为场馆卡片。时间筛选卡片行**保持显示**（与活动查找 Tab 一致）。

#### 场馆卡片结构

```
┌─────────────────────────────────────┐
│ [场馆图片缩略图 72×72]  [场馆名称]     │
│                        [距离标签]   │
│                  🟢 Open · Closes 9PM│
│                  📍 场馆地址         │
│ ──────────────────────────────────  │
│ 🏸 8 courts   🏓 4 courts            │
│ ✅ 场地空余: 3 courts available       │
│ ⏰ 开放时间: Mon-Fri 7AM-10PM         │
└─────────────────────────────────────┘
```

**字段说明：**

| 字段 | 内容示例 |
|---|---|
| 场馆图片 | 缩略图，圆角 `12px` |
| 场馆名称 | `Ryde Aquatic Leisure Centre` |
| 距离 | `1.2 km`（橙色胶囊） |
| 当前状态 | 🟢 `Open`（绿色）/ 🔴 `Closed`（红色） |
| 关闭/开放时间 | `Closes 9:00 PM` / `Opens 8:00 AM` |
| 场地类型数量 | 羽毛球场 N 块 / 匹克球场 N 块 |
| 场地空余情况 | `3 courts available`（绿色）/ `Full`（红色） |
| 开放时间 | 完整每日时间段 |
| 场馆地址 | 完整地址字符串 |

**可点击元素：**

- [点击1] 整张卡片 → 跳转场馆详情页（显示全部场地、预订入口、历史活动等）
- [点击2] 收藏图标 ♡ → 切换收藏状态

---

### P03-D 场馆搜索 — Map 模式

与 P03-B 结构相似，差异如下：

- Pin 图标：建筑/场馆图标（非羽毛球图标），颜色为橙色（Open）/ 灰色（Closed）
- 底部浮出卡片内容为场馆信息：

```
┌─────────────────────────────────────┐
│ [场馆图] Ryde Aquatic Centre         │
│ 🟢 Open · Closes 9PM   📍 1.2 km    │
│ 🏸 8 courts  ✅ 3 available          │
│                    [View / 查看 →]  │
└─────────────────────────────────────┘
```

**可点击元素：**

- [点击1] 场馆 Pin → 底部弹出场馆卡片
- [点击2] 场馆卡片整体 → 跳转场馆详情页
- [点击3] `View / 查看` 按钮 → 同上
- [点击4] 卡片外地图区域 → 关闭卡片

> ~~右下角定位按钮已移除~~（已删除，不再显示）

---

### P03-E 城市选择弹窗 City Selector Sheet

**触发：** 点击顶部城市选择器  
**样式：** 从屏幕底部弹起的半屏弹窗，玻璃背景，圆角顶部

**内容：**

- 顶部拖拽条（`40px × 4px` 灰色圆角）
- 标题：`Select City / 选择城市`
- 搜索框（搜索城市名）
- 城市分组列表：

  **澳大利亚 Australia：**
  - Sydney / 悉尼
  - Melbourne / 墨尔本
  - Brisbane / 布里斯班
  - Perth / 珀斯
  - Adelaide / 阿德莱德
  - Gold Coast / 黄金海岸
  - Canberra / 堪培拉

  **新西兰 New Zealand：**
  - Auckland / 奥克兰
  - Wellington / 惠灵顿
  - Christchurch / 基督城

- 当前城市高亮（橙色文字 + 右侧勾选图标）
- 底部「Use Current Location / 使用当前位置」按钮（需位置权限）

**可点击元素：**

- [点击1] 任意城市列表项 → 选中城市，关闭弹窗，顶部城市名更新（**仅显示城市名，不含国旗或国家缩写**，例：选择「Sydney 🇦🇺」后顶部显示 `Sydney`）
- [点击2] 搜索框 → 过滤城市列表
- [点击3] 「Use Current Location」按钮 → 请求 GPS 权限，自动匹配最近城市
- [点击4] 弹窗外区域 / 向下滑动拖拽 → 关闭弹窗

---

### P03-F 发布弹窗 Publish Activity Sheet

**触发：** 点击底部导航栏中央 `+` 号按钮  
**样式：** 从底部弹起的小卡片（高度约 220px），玻璃背景，圆角顶部

**内容：**

- 顶部拖拽条
- 标题：`What would you like to publish? / 你想发布什么？`
- 两个选项按钮（大卡片按钮，左图标右文字）：

```
┌──────────────────────────────────┐
│  🏆  Club Activity / 俱乐部活动   │  ← 需要先是俱乐部组织者
│      Post an official club session│
└──────────────────────────────────┘

┌──────────────────────────────────┐
│  👥  Group Activity / 群组活动    │
│      Organize a casual group game │
└──────────────────────────────────┘
```

**可点击元素：**

- [点击1] `Club Activity / 俱乐部活动` → 跳转发布俱乐部活动页（需验证是否为俱乐部组织者）
- [点击2] `Group Activity / 群组活动` → 跳转发布群组活动页
- [点击3] 弹窗外区域 / 向下拖拽 → 关闭弹窗

**发布活动表单字段（进入后的完整页面）：**

- 运动类型：羽毛球 / 匹克球（选择器）
- 活动名称（输入框）
- 活动地点（地图搜索选择，自动填充地址）
- 日期（日期选择器）
- 开始时间 / 结束时间（时间选择器）
- 参与人数上限（数字输入）
- 技术水平要求（多选：All / Beginner / Intermediate / Advanced）
- 场地数量（数字输入）
- 价格（费用 / 免费切换，输入费用金额）
- 活动说明（多行文本输入框）
- [点击] `Publish / 发布` 按钮（橙色填充，全宽）

---

### P04 订单页 Orders

**页面用途：** 用户查看所有活动报名订单记录。  
**布局：** 顶部标题 + Tab 过滤 + 列表

#### 顶部区域

- 页面标题：`Orders / 我的订单`
- [点击1] 过滤图标（漏斗）→ 弹出过滤弹窗（日期范围、运动类型）

#### Tab 过滤（横向可滑动）

- [点击2] `All / 全部`（默认选中）
- [点击3] `Pending Payment / 待付款`
- [点击4] `Upcoming / 待消费`
- [点击5] `Completed / 已消费`
- [点击6] `Refunded / 退款`

选中 Tab 下方橙色底线，横向可滑动以显示更多 Tab。

#### 订单卡片结构

```
┌─────────────────────────────────────┐
│ [🏸] 活动名称              [状态标签] │
│ 🗓 日期时间   📍 场馆名称             │
│ ──────────────────────────────────  │
│ 订单编号：#SG-20240419-001           │
│ 金额：$8.00  Token 抵扣：-$2.00      │
│                    [查看详情 →]      │
└─────────────────────────────────────┘
```

状态标签颜色：
- `Pending Payment / 待付款`：橙色
- `Upcoming / 待消费`：蓝色
- `Completed / 已消费`：绿色
- `Refunded / 退款`：灰色

**可点击元素：**

- [点击7] 订单卡片整体 / 「查看详情」按钮 → 跳转订单详情页
- [点击8] 订单详情页内「申请退款」按钮 → 弹出退款确认弹窗
- [点击9] 订单详情页内「联系组织者」按钮 → 跳转消息页

**空状态：** 对应 Tab 下无订单时显示插画 + `No orders yet. / 暂无订单`

---

### P05 装备商城 Shop

**页面用途：** 销售羽毛球、匹克球相关装备与服务，支持 Token 抵扣。  
**布局：** 顶部搜索 + 分类 Tab + 商品列表

#### 顶部区域

- 页面标题：`Shop / 装备商城`
- 副标题：`Premium Gear for Badminton & Pickleball / 优质装备与服务`
- Token 余额展示（右上角）：`🪙 Token: 88`（金色，可点击）
- [点击1] Token 余额 → 跳转 Token 明细页（显示获取记录、消费记录）
- 搜索框：`Search gear & services… / 搜索装备和服务…`
- [点击2] 搜索框 → 进入搜索结果

#### 分类 Tab（横向可滑动）

- [点击3] `All / 全部`
- [点击4] `Rackets / 球拍`
- [点击5] `Shuttlecocks / 羽毛球`
- [点击6] `Pickleballs / 匹克球`
- [点击7] `Shoes / 球鞋`
- [点击8] `Accessories / 配件`
- [点击9] `Services / 服务`（如穿线服务）

#### 商品卡片结构（2列网格布局）

```
┌─────────────────┐
│ [商品图片]       │
│ 商品名称         │
│ $XX.00          │
│ 🪙 最多抵 N Token│
│ [加入购物车]     │
└─────────────────┘
```

**Token 抵扣规则展示（卡片上）：**

- 灰色小字：`Up to X Token redeemable / 最多可用 X Token 抵扣`
- 示例：穿线服务 → `Up to 10 Token`；SG-50 羽毛球 → `Up to 15 Token`

**可点击元素：**

- [点击10] 商品卡片整体 → 跳转商品详情页
- [点击11] 「Add to Cart / 加入购物车」按钮 → 加入购物车，右上角购物车图标数量 +1
- [点击12] 右上角购物车图标 → 跳转购物车页

#### 商品详情页（独立页面）

- 商品图片轮播（可左右滑动）
- 商品名称、价格
- Token 抵扣设置：
  - 显示：`You have 88 Token · Max redeemable: 15 Token = -$1.50`
  - [点击13] Token 滑块或输入框 → 调整使用 Token 数量（0 ~ N，不超过后台上限）
- 实付金额实时计算显示
- 商品描述（多行文字）
- [点击14] 「Buy Now / 立即购买」橙色大按钮 → 跳转结算页
- [点击15] 「Add to Cart / 加入购物车」边框按钮

---

### P06 账户页 Account

**页面用途：** 用户个人中心入口，包含资料、设置、俱乐部管理。  
**布局：** 顶部用户信息 Banner + 功能菜单列表

#### 顶部用户信息 Banner（玻璃卡片，橙色渐变背景）

- 头像（圆形，72px，右下角可点击编辑铅笔图标）
- 显示名称（Nickname，大字）
- 真实姓名
- Email
- Token 余额：`🪙 88 Tokens`
- 所属俱乐部标签（如：`Sydney Shuttlers Club`）

**可点击元素：**

- [点击1] 头像区域 → 跳转 P06-A 个人资料编辑页
- [点击2] Token 余额 → 跳转 Token 明细页

#### 菜单列表区域（每行为「图标 + 文字 + 右箭头」格式）

**我的内容 My Content：**
- [点击3] `My Activities / 我的活动` → 历史参与的活动列表
- [点击4] `My Bookings / 我的预订` → 场馆预订记录
- [点击5] `Saved / 我的收藏` → 收藏的活动和场馆

**管理 Management：**
- [点击6] `Clubs & Groups / 俱乐部 & 群组` → 跳转 P06-C
- [点击7] `Token History / Token 明细` → Token 获取与消费记录

**设置 Settings：**
- [点击8] `Settings / 设置` → 跳转 P06-B 设置页

**其他 Others：**
- [点击9] `Help & Support / 帮助与支持` → 帮助中心页
- [点击10] `About ShuttleGo / 关于` → 版本信息、服务条款、隐私政策
- [点击11] `Log Out / 退出登录` → 弹出确认弹窗（确认后清除登录状态，跳转 P02）

---

### P06-A 个人资料编辑 Profile Edit

**页面用途：** 编辑用户个人信息。  
**布局：** 可滚动表单页

#### 字段列表（可编辑）

| 字段 | 类型 | 说明 |
|---|---|---|
| 头像 Avatar | 图片选择 | 点击弹出相册/拍照选择 |
| Full Name / 全名 | 文本输入框 | |
| Display Name / 显示名称 | 文本输入框 | 社区中显示的名称 |
| Email | 文本输入框 | 需验证新邮箱 |
| Phone / 电话 | 电话输入框 | 带区号选择 |
| Date of Birth / 生日 | 日期选择器 | |
| Gender / 性别 | 选择器（Male/Female/Other） | |
| Skill Level / 技能等级 | 选择器 | Beginner / Intermediate / Advanced |
| Preferred Sport / 偏好运动 | 多选 | Badminton / Pickleball / Both |

**可点击元素：**

- [点击1] 头像区域 → 弹出相册 / 拍照选择
- [点击2] 各输入字段 → 激活键盘
- [点击3] 底部「Save / 保存」橙色大按钮 → 保存更改，返回上一页

---

### P06-B 设置页 Settings

**页面用途：** App 个性化配置。  
**布局：** 分组设置列表

#### 设置项列表

**语言 Language：**
- [点击1] `Language / 语言` → 弹出选择：`English` / `中文`；当前选中项右侧显示勾选

**通知 Notifications：**
- [点击2] `Activity Reminders / 活动提醒` → Toggle 开关（默认开）
- [点击3] `New Messages / 新消息提醒` → Toggle 开关（默认开）
- [点击4] `Order Updates / 订单更新` → Toggle 开关（默认开）
- [点击5] `Promotions / 促销推送` → Toggle 开关（默认关）

**主题 Theme：**
- [点击6] `Appearance / 外观模式` → 弹出 3 选项：`Light / 浅色` / `Dark / 深色` / `System / 跟随系统`；当前选中项右侧显示勾选，勾选橙色

**隐私 Privacy：**
- [点击7] `Location Services / 位置服务` → 跳转系统位置权限设置
- [点击8] `Privacy Policy / 隐私政策` → Webview 内嵌页

**账户 Account：**
- [点击9] `Change Password / 修改密码` → 跳转密码修改页
- [点击10] `Delete Account / 注销账户` → 弹出二次确认弹窗（高危操作，红色按钮）

---

### P06-C 俱乐部 & 群管理 Clubs & Groups

**页面用途：** 用户创建、管理俱乐部或群组，以及查看已加入的组织。  
**布局：** 两个 Tab（Clubs / Groups）+ 列表 + 创建入口

#### 顶部 Tab

- [点击1] `Clubs / 俱乐部`（默认）
- [点击2] `Groups / 群组`

#### 列表区域（以 Clubs Tab 为例）

**我管理的俱乐部 My Clubs：**

俱乐部卡片：
- 俱乐部 Logo（圆形头像）
- 俱乐部名称
- 成员数量：`24 members`
- 创建日期
- [点击3] 「Manage / 管理」按钮 → 跳转俱乐部管理详情页

**我加入的俱乐部 Joined Clubs：**

- 同卡片格式，按钮改为「View / 查看」

- [点击4] 右上角「+创建」按钮 → 跳转创建俱乐部/群组表单页

#### 创建俱乐部/群组表单字段

| 字段 | 类型 |
|---|---|
| 名称 Name | 文本输入框 |
| Logo / 头像 | 图片选择 |
| 运动类型 Sport | 选择器（羽毛球/匹克球/两者） |
| 城市 City | 城市选择器 |
| 描述 Description | 多行文本 |
| 公开/私密 Visibility | Toggle（Public / Private） |

- [点击5] 「Create / 创建」按钮 → 提交创建

#### 俱乐部管理详情页

**成员管理 Members：**
- 成员列表：头像 + 显示名称 + 技能等级 + 角色（Admin / Member）
- [点击6] 单个成员行 → 弹出操作菜单：设置显示名称、设置技能等级、移除成员、设为管理员
- [点击7] 「+ Add Member / 添加成员」按钮 → 搜索并邀请用户

**活动管理 Activities：**
- 该俱乐部发布的历史活动列表
- [点击8] 「Publish Activity / 发布活动」橙色按钮 → 跳转发布活动表单

**发布活动表单字段（完整版）：**

| 字段 | 类型 |
|---|---|
| 运动类型 | 选择器 |
| 活动名称 | 文本输入框 |
| 活动地点 | 地图搜索选择（支持模糊输入） |
| 日期 Date | 日期选择器 |
| 开始时间 | 时间选择器 |
| 结束时间 | 时间选择器 |
| 人数上限 Max Players | 数字输入 |
| 技术水平要求 | 多选：All / Beginner / Intermediate / Advanced |
| 场地数量 Courts | 数字输入 |
| 价格 Price | 切换「Free / Paid」，Paid 时显示金额输入 |
| 活动说明 Description | 多行文本 |
| 封面图片 Cover Image | 可选，图片选择 |

- [点击9] 「Preview / 预览」按钮 → 以报名用户视角预览活动卡片
- [点击10] 「Publish / 发布」橙色大按钮 → 提交发布，成功后跳回活动列表

---

## 四、通用组件规范 Shared Components

### 4.1 Toast 提示条

- 位置：屏幕顶部，安全区下方 `16px`
- 样式：玻璃背景，圆角 `12px`，左侧彩色指示条
- 类型：✅ 成功（绿）/ ⚠️ 警告（橙）/ ❌ 错误（红）/ ℹ️ 信息（蓝）
- 自动消失：`3秒`

### 4.2 空状态 Empty State

- 居中插画（线条风，橙色主色调）
- 说明文字（主 + 副）
- 可选操作按钮（如「发现活动 / Discover Activities」）

### 4.3 加载状态 Loading

- 骨架屏：灰色 shimmer 动画，形状与内容卡片匹配
- 全页 Loading：中心橙色圆圈旋转动画

### 4.4 确认弹窗 Confirm Dialog

- 居中弹窗（非全屏），圆角 `20px`，玻璃背景
- 标题 + 说明文字
- 两个按钮：取消（边框）+ 确认（填充）
- 高危操作确认按钮使用红色

### 4.5 权限请求卡片 Permission Request

- 触发：访问位置、推送通知等需要权限时
- 从底部弹起，展示权限用途说明
- 两个按钮：`Not Now / 暂不` + `Allow / 允许`

---

## 五、双语规范 Bilingual Rules

- 默认语言根据设备系统语言自动判断
- 英文地区（AU/NZ）默认英文，中文系统默认中文
- 用户可在「设置」中手动切换语言
- 所有 UI 文案均有英文和中文两版
- 日期格式：英文版 `Apr 19, 2024`；中文版 `2024年4月19日`
- 货币：统一显示 `$`（AUD 或 NZD 按用户城市自动切换）

---

## 六、无障碍设计 Accessibility

- 所有交互元素最小点击区域：`44×44pt`
- 颜色对比度满足 WCAG AA 标准（4.5:1）
- 支持系统字体大小缩放（Dynamic Type）
- 所有图标配有 `accessibilityLabel` 文案
- 地图模式提供列表备选视图（无障碍友好）

---

*文档结束 End of Document*  
*本文档供 UI 设计与前端开发使用，所有页面编号与可点击元素编号为唯一标识，请逐页按序实现。*
