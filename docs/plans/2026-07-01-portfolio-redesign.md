# kali-portfolio 网站优化设计稿

> 日期：2026-07-01
> 定位：能力展示型个人简历网站（非作品集）
> 域名：https://kali.superkali.online
> 技术架构：纯静态多页面 HTML + CSS + JS，Cloudflare Pages 部署

---

## 一、现有站点分析

### 当前状态
- 单文件 `index.html`（997行，26KB）
- 终端绿色极简风格（Bento Grid Terminal Green Minimalist）
- 色彩：白底 + 绿色强调色 `#00E676`
- 字体：Space Grotesk (display) / Inter (body) / JetBrains Mono (mono)
- 12列 Bento Grid 布局

### 现有模块
1. Hero — 个人介绍 + 状态
2. Status — 位置、时区、经验等系统状态卡
3. Work × 3 — AI小说 / Hermes Agent / Enterprise SaaS（笼统）
4. Skills — 技术栈标签（前端/后端/DevOps/AI）
5. Timeline — 职业时间线（4个节点）
6. Contact — 联系表单

### 问题
- 项目太少且笼统（Enterprise SaaS Suite 无实际链接）
- 没有按能力维度分模块展示
- 缺少 LUMINA CMS 等已上线产品
- 无法体现 AI / RPA / 飞书生态 / DevOps 等多维度能力
- 没有工作经验独立页面

---

## 二、目标结构

### 页面规划
```
kali-portfolio/
├── index.html          ← 主页（6模块能力展示）
├── experience.html     ← 工作经验子页面（待用户提供简历后填充）
├── assets/
│   └── (如有需要，图片等静态资源)
└── (Cloudflare Pages 自动部署)
```

### 导航栏变化
```
当前:  work | skills | timeline | contact
改后:  products | ai | rpa | knowledge | devops | experience | contact
```
导航项锚定到主页对应模块区域，`experience` 跳转独立页面。

---

## 三、主页模块设计

### 模块布局（Bento Grid 12列）

```
┌──────────────────────────────────┬──────────────┐
│           HERO (col-8)           │  STATUS      │
│  卡力 / Kali                      │  (col-4)     │
│  全栈开发者 & SaaS技术顾问          │              │
│  GitHub / Email 链接               │              │
├──────────────────────────────────┴──────────────┤
│                                                  │
│  ① 在线产品 PRODUCTS (col-12)                     │
│  ┌──────────────────┐  ┌──────────────────┐     │
│  │ AI小说写作助手     │  │ LUMINA CMS       │     │
│  │ 在线链接 ↗        │  │ 在线链接 ↗        │     │
│  └──────────────────┘  └──────────────────┘     │
│                                                  │
├──────────────────────────────────────────────────┤
│                                                  │
│  ② AI开发能力 AI_DEV (col-8)  │  ③ RPA & 自动化  │
│  ┌────────────────────────┐  │  (col-4)        │
│  │ Hermes Agent 智能体框架  │  │  影刀RPA项目集   │
│  │ • 多模型调度            │  │  • 天猫退款RPA   │
│  │ • 技能系统              │  │  • 金蝶ERP同步   │
│  │ • 自我进化              │  │  • 商品材料生成  │
│  │ • MCP协议               │  │  • 自动化工作流  │
│  │ GitHub ↗               │  │                 │
│  └────────────────────────┘  │                 │
│                              │                 │
├──────────────────────────────┴─────────────────┤
│                                                 │
│  ④ 知识库 & 飞书生态 (col-6)  │  ⑤ 基础设施 & DevOps │
│  ┌────────────────────────┐ │  (col-6)           │
│  │ 飞书多维表知识库体系     │ │  ┌────────────────┐ │
│  │ • 6大分类×23项元数据    │ │  │ Cloudflare全栈  │ │
│  │ • 8自动化流程           │ │  │ 部署体系         │ │
│  │ • 飞书API集成           │ │  │ • Pages + Tunnel│ │
│  │ • 文档自动化            │ │  │ 权限管理框架     │ │
│  │                        │ │  │ • 多层Hook联动   │ │
│  │                        │ │  │ 服务器运维       │ │
│  └────────────────────────┘ │  └────────────────┘ │
│                             │                    │
├─────────────────────────────┴────────────────────┤
│                                                  │
│  ⑥ 工作经验 EXPERIENCE (col-12)                   │
│  ┌──────────────────────────────────────────┐    │
│  │ → 点击进入独立页面查看完整工作经历           │    │
│  │    （待上传简历后填充）                      │    │
│  └──────────────────────────────────────────┘    │
│                                                  │
├──────────────────────────────────────────────────┤
│  CONTACT (col-12)                                │
└──────────────────────────────────────────────────┘
```

---

## 四、各模块详细内容

### ① 在线产品 (Products)
> 标签：`products` | 占位：col-12 | 内部布局：2列卡片

| 卡片 | 标题 | 描述 | 链接 | 技术标签 |
|------|------|------|------|----------|
| 1 | AI 小说写作助手 | 面向长篇小说创作的 AI Native 系统，支持 Agent 驱动、世界观构建、RAG 增强、整本生产工作流 | https://novel.superkali.online | React, Node.js, LLM, Cloudflare |
| 2 | LUMINA CMS | AI 驱动的智能协作内容管理平台，支持 AI 辅助写作、自动化工作流、企业级权限管理 | https://lumina-cms.superkali.online | Vue, Flask, Cloudflare, RAG |

**交互**：卡片整体可点击，hover 时边框变绿 + 箭头微移，右上角小角标标注 "live" 状态点。

### ② AI 开发能力 (AI Dev)
> 标签：`ai_dev` | 占位：col-8

**内容结构**：
- 主项目：Hermes Agent 智能体框架
  - 一句话：自研智能体框架，支持多模型调度、技能系统、定时任务、消息平台网关、自我进化
  - 能力清单（带 terminal 风格前缀 `▸`）：
    - ▸ 多模型调度（火山引擎/MiniMax/OpenAI兼容）
    - ▸ 技能系统（100+ 可复用技能，MCP 协议支持）
    - ▸ 定时任务 & 消息平台网关（微信/飞书/Discord/Telegram）
    - ▸ 自我进化（DSPy 驱动的提示词优化）
    - ▸ 多用户隔离 & 权限管控
  - 链接：GitHub → kali-artist
  - 技术标签：Python, LLM, MCP, Agent, DSPy

**视觉**：能力清单用 mono 字体，每行带 `▸` 前缀，hover 高亮。

### ③ RPA & 自动化 (Automation)
> 标签：`automation` | 占位：col-4

**内容结构**：
- 标题：RPA & 流程自动化
- 项目列表（紧凑排列）：
  - 天猫退货退款自动处理 RPA
  - 金蝶 ERP 订单同步飞书多维表
  - 商品材料自动生成与发布
  - AI+RPA 标杆客户共创专项
- 能力标签：影刀 RPA, 飞书 API, 自动化工作流设计

**视觉**：项目列表用小字号，每项前缀 `▸`，整体紧凑。

### ④ 知识库 & 飞书生态 (Knowledge)
> 标签：`knowledge` | 占位：col-6

**内容结构**：
- 标题：知识库 & 飞书生态集成
- 能力描述：
  - 飞书多维表知识库体系（6大分类 × 23项元数据 × 8自动化流程）
  - 飞书 API 全链路集成（文档/多维表/消息/权限）
  - 文档自动化（飞书 Doc 自动创建、归档、权限管理）
  - 企业信息智能查询系统
- 技术标签：飞书 API, 多维表, 文档自动化, Python

### ⑤ 基础设施 & DevOps (Infra)
> 标签：`infrastructure` | 占位：col-6

**内容结构**：
- 标题：基础设施 & DevOps
- 能力描述：
  - Cloudflare 全栈部署体系（Pages + Tunnel，隐藏源站 IP）
  - 多层 Hook 联动权限管理框架
  - 服务器运维 & 健康监控
  - CI/CD 自动化部署流水线
- 技术标签：Cloudflare, Linux, systemd, Nginx, Docker

### ⑥ 工作经验 (Experience)
> 标签：`experience` | 占位：col-12

**主页展示**：一个引导卡片，点击跳转到 `experience.html`
- 卡片内容："查看完整工作经历 →"
- 视觉：占满一行，居中引导，带箭头动效
- 子页面待用户提供简历后填充

### 保留模块
- **Hero** — 保持现有设计，微调 tagline
- **Status** — 保持，更新 focus 字段
- **Skills** — 保持，更新标签（加入 Cloudflare Tunnel、飞书 API、RPA、MCP 等）
- **Timeline** — 移动到 experience.html 子页面
- **Contact** — 保持

---

## 五、设计系统

### 色彩（保持现有）
```css
--bg: #FFFFFF
--bg-subtle: #FAFAFA
--text-primary: #1A1A1A
--text-secondary: #555555
--text-tertiary: #999999
--border: #E5E5E5
--accent: #00E676       /* 终端绿 */
--accent-dim: #00C853
--accent-soft: rgba(0, 230, 118, 0.06)
```

### 字体（保持现有）
- Display: Space Grotesk（标题）
- Body: Inter（正文）
- Mono: JetBrains Mono（代码/标签/状态）

### 模块分隔
- 每个模块区域用 `card-label` 标注模块名（如 `products`、`ai_dev`）
- 模块之间用 Bento Grid 的 gap 自然分隔
- 大模块（col-12）内部用嵌套 grid 做卡片排列

### 响应式
- ≤900px：所有 col-8/col-6/col-4 变为 col-12
- ≤640px：导航栏隐藏链接（增加汉堡菜单或简化），卡片 padding 缩小

---

## 六、交互设计

1. **模块入场动画**：保持现有 fadeInUp，增加更多卡片的 delay 层级
2. **产品卡片 hover**：边框变绿 + 阴影微浮 + 箭头右移
3. **能力清单 hover**：`▸` 前缀变绿色高亮
4. **工作经验入口**：整卡片 hover 时背景微变 + 箭头动效，点击跳转
5. **导航栏**：滚动时高亮当前模块（IntersectionObserver）
6. **移动端**：导航简化为模块首字母或图标

---

## 七、文件改动计划

| 文件 | 操作 | 说明 |
|------|------|------|
| `index.html` | 重构 | 从单页面项目展示改为6模块能力展示 |
| `experience.html` | 新建 | 工作经验独立子页面（先建框架，待内容） |

### 不改动的部分
- 设计系统（色彩、字体、间距）
- 导航栏基础样式
- Hero / Status / Skills / Contact 基础结构
- Footer
- Contact 表单 JS

---

## 八、待确认项

1. **工作经验子页面**：先建空白框架页（统一风格），等你上传简历后再填充内容
2. **Skills 标签更新**：我会根据实际项目补充新标签，你最后审阅
3. **Timeline**：从主页移到 experience.html，主页不再展示时间线
4. **内容文案**：各模块的描述文案我基于项目信息撰写，你审阅后可调整
