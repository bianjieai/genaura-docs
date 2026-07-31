# GenAura 用户使用文档

> 本文档对应应用版本：v1.2.0

GenAura 是一款面向品牌 AI 洞察的桌面应用，帮助用户在多个 AI 平台上监测品牌表现、分析用户情感与偏好、管理知识库，并一键生成与发布内容。

本目录是面向**最终用户**的使用文档。文档采用 [Diátaxis](https://diataxis.fr/) 框架组织，按用户意图分为四类：**入门**（学习上手）、**教程**（端到端任务）、**操作指南**（功能模块操作）、**参考**（查阅型资料），并辅以**概念解释**帮助理解底层机制。

---

## 应用功能全景

GenAura 采用**三栏工作区**布局（见 `getting-started/04-interface-overview.md`）：

- **左侧导航**：品牌切换、对话列表、机会与风险跟踪、账户菜单（个人中心/订阅/主题/退出）
- **中间聊天区**：与 AI 多轮对话，支持命令、@提及知识库、附件、子代理与人工审批
- **右侧面板**：7 个功能 Tab —— 知识库 / AI 洞察 / AI 信源 / AI 情感 / 品牌配置 / 定时任务 / 浏览器

应用内嵌 5 个 AI 平台搜索工作流（DeepSeek、通义千问、豆包、Kimi、腾讯元宝），自动采集品牌在各平台的搜索结果与引用来源，生成洞察分析。

---

## 目录结构

```
app/docs/user-guide/
├── README.md                    # 本文件：总览与文档导航
├── glossary.md                  # 术语表（独立）
│
├── getting-started/             # 【入门】安装、登录、引导、界面
├── concepts/                    # 【概念】核心概念与工作原理
├── tutorials/                   # 【教程】端到端任务流程
├── how-to/                      # 【操作指南】各功能模块操作步骤（主体）
├── reference/                   # 【参考】设置、更新、隐私等查阅型资料
├── troubleshooting.md           # 【故障排查】按症状分类
└── faq.md                       # 【常见问题】
```

---

## 一、入门（getting-started/）

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `01-installation.md` | 系统要求（macOS/Windows）、下载、安装、首次启动、卸载 | `electron-builder.config.cjs`、`electron/main/index.ts` |
| `02-login-account.md` | 登录认证、账号体系、订阅状态、退出登录（账户菜单位于左下角，跳转外部 Web 控制台） | `src/pages/LoginPage.tsx`、`src/components/workspace/LeftNav.tsx`、`src/lib/auth-context.tsx` |
| `03-onboarding.md` | 8 步新用户引导流程（欢迎→输入框→知识库→AI 洞察→品牌配置→定时任务→机会→开始） | `src/components/onboarding/OnboardingGuide.tsx`、`steps.ts`、`SpotlightOverlay.tsx`、`OnboardingPopover.tsx`、`useOnboarding.ts` |
| `04-interface-overview.md` | 三栏布局认识、右侧 7 个 Tab、面板折叠/最大化、品牌头部 | `src/pages/BrandWorkspace.tsx`、`src/components/workspace/TabBar.tsx`、`RightPanel.tsx`、`LeftNav.tsx` |

---

## 二、概念解释（concepts/）

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `01-brand-model.md` | 品牌、产品、竞品、预设问题、关键词之间的关系模型；创建品牌与品牌配置的字段差异 | `src/components/workspace/brand-config/index.tsx`、`src/components/brand/AddBrandDialog.tsx`、`src/types/brand-config.ts` |
| `02-workflow.md` | 5 个 AI 平台工作流的运行机制、接管机制、为何需要登录态、异常检测（登录/验证码） | `electron/main/workflow/predefined-workflows.ts`、`executor.ts`、`types.ts` |
| `03-insight-data.md` | 洞察数据从何而来（AI 平台搜索结果）、品牌指数含义、数据更新频率、综合指标计算口径 | `electron/main/services/brand-index-service.ts`、`SearchResultAnalysisService.ts`、`emotion-service.ts` |
| `04-ai-agent.md` | 主 Agent、子代理、人工审批的协作模型；Agent 活动聚合（思考/工具调用折叠展示） | `src/components/workspace/SubAgentBlock.tsx`、`HumanApprovalDialog.tsx`、`agentActivity/AggregatedActivity.tsx` |
| `05-opportunity-risk.md` | 机会/风险如何被 AI 自动识别、状态流转（new/in_progress/completed/dismissed）、优先级（紧急优先级 / 高优先级 / 中优先级 / 低优先级） | `src/components/workspace/LeftNav.tsx`、`OpportunityRiskNavItem.tsx`、`src/lib/api/opportunity-risks.ts` |

---

## 三、教程（tutorials/）

| 文档 | 覆盖内容 | 串联模块 |
|---|---|---|
| `01-first-brand.md` | 从零配置首个品牌：安装→登录→创建品牌→配置基本信息/产品/竞品/预设问题→上传素材 | 入门 + 品牌管理 + 品牌配置 |
| `02-brand-monitoring.md` | 执行一次完整品牌监测：配置关键词→运行 AI 平台工作流→查看洞察→跟进机会 | 品牌配置 + 浏览器 + 洞察 + 机会 |
| `03-content-publish.md` | 从洞察到发布文章：基于洞察生成文章→编辑→一键发布→查看发布状态 | 洞察 + 对话 + 知识库 + 发布 |

---

## 四、操作指南（how-to/）

### 品牌与配置

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `01-brand-management.md` | 品牌创建（名称/Logo/链接/素材文件上传）、品牌切换、品牌删除、`__system__` 保留品牌说明 | `src/components/brand/AddBrandDialog.tsx`、`src/components/workspace/BrandSelector.tsx` |
| `02-brand-config.md` | 品牌配置 Tab 四个分区：①基本信息（官网/别名/关键词/描述）②产品配置 ③竞品配置 ④AI 平台跟踪；**问题矩阵**（品牌级/产品级预设问题管理） | `src/components/workspace/brand-config/index.tsx`、`BrandBasicInfoDialog.tsx`、`ProductDialog.tsx`、`CompetitorDialog.tsx`、`PlatformTracking.tsx`、`question-matrix/QuestionList.tsx` |

### 对话

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `03-chat-management.md` | 新建/重命名/删除/批量删除对话、对话列表与排序、新对话空状态欢迎界面 | `src/components/workspace/LeftNav.tsx`、`ChatArea.tsx`、`WelcomeGreeting.tsx` |
| `04-messaging.md` | 消息发送与渲染、消息操作（复制/删除）、附件上传 | `src/components/workspace/ChatArea.tsx`、`MessageRenderer.tsx`、`MessageActions.tsx`、`HumanMessageActions.tsx`、`Composer.tsx` |
| `05-commands-mentions.md` | `/`命令与快捷建议（品牌 GEO 诊断 / 生成 GEO 文章 / 优化品牌知识库）、@提及知识库文件 | `src/components/workspace/CommandPopover.tsx`、`MentionPopover.tsx`、`Composer/extensions/MentionChip.tsx`、`src/constants/chatSuggestions.ts` |
| `06-sub-agent-approval.md` | 子代理消息块、人工审批对话框、Agent 活动聚合（思考/工具调用折叠展示） | `src/components/workspace/SubAgentBlock.tsx`、`HumanApprovalDialog.tsx`、`agentActivity/AggregatedActivity.tsx` |

### 机会与风险

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `07-opportunities-risks.md` | 机会/风险的展示与排序（左侧导航仅显示 new/in_progress，最多各 5 条）、状态流转、优先级、完成/删除、与对话关联跳转 | `src/components/workspace/LeftNav.tsx`、`OpportunityRiskNavItem.tsx` |

### 内容生产

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `08-knowledge-base.md` | 知识库概览、系统目录结构（品牌画像/产品/竞品/GEO 内容等 7 个系统目录）、导入本地文件（**md/txt/docx/pdf**）、导入 URL、搜索检索、文件夹分类、发送到对话 | `src/components/workspace/knowledge-base/KnowledgeBaseManager/KnowledgeBaseManager.tsx`、`ImportDialog.tsx`、`KnowledgeSearchPanel.tsx`、`electron/main/services/KnowledgeService.ts`、`url-import-service.ts`、`src/constants/knowledge.ts` |
| `09-file-editor.md` | 统一文件编辑器、可编辑类型（md + 纯文本 txt/json/html/py/js/ts/yaml 等）、只预览类型（**csv/xlsx/xls**/pdf/docx/图片）、文档导出格式与下载、选中文本加入对话、草稿恢复与丢弃 | `src/components/editor/UnifiedFileEditor/index.tsx`、`download.ts`、`electron/main/services/document-export-service.ts` |
| `10-browser.md` | 内嵌浏览器 Tab、网址导航、前进/后退/刷新、登录态管理、**浏览器接管对话框**（Agent 控制时用户可接管） | `src/components/workspace/BrowserTab.tsx`、`WebviewLayer.tsx`、`RightPanel.tsx`（接管对话框）、`electron/main/browser-host.ts` |
| `11-ai-platform-workflows.md` | 5 个 AI 平台搜索工作流（DeepSeek/通义千问/豆包/Kimi/腾讯元宝）的运行、接管、结果（答案+引用来源） | `electron/main/workflow/predefined-workflows.ts`、`executor.ts` |
| `12-cron-tasks.md` | 定时任务概念、任务类型、执行频率/时间配置、启用/停用/编辑/删除、运行状态、与对话/工作流关联 | `src/components/workspace/CronPanel.tsx`、`ScheduleConfig.tsx`、`electron/main/cron/scheduler.ts` |
| `13-article-publish.md` | 一键发布入口、发布对话框、目标平台、发布流程与预览 URL、发布状态检查（进行中/成功/失败）、发布记录 | `src/components/workspace/knowledge-base/KnowledgeBaseManager/PublishDialog.tsx`、`electron/main/platform-publish/PlatformPublishService.ts`、`handlers.ts`、`electron/main/services/PublishStatusChecker.ts`、`ArticlePublishService.ts` |

### 数据洞察（右侧面板）

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `14-insight.md` | AI 洞察 Tab、综合分析全局指标卡（AI 对话总量/提及数/提及率/首位推荐率/前三推荐率）、提及记录表、行业竞品对比、时间/问题类型/平台筛选 | `src/components/workspace/geo/BrandInsight/index.tsx`（及子组件）、`electron/main/services/brand-index-service.ts` |
| `15-emotion-analysis.md` | 情感分析 Tab、情感概览、趋势图、关键词云、平台情感对比/分布、问答列表、问答详情 | `src/components/workspace/geo/EmotionAnalysis/index.tsx`（及子组件）、`electron/main/services/emotion-service.ts` |
| `16-preference-insight.md` | 偏好洞察 Tab、偏好概览、信源分布、信源排名、信源对比 | `src/components/workspace/geo/PreferenceInsight/index.tsx`（及子组件）、`electron/main/services/PreferenceInsightService.ts` |

---

## 五、参考（reference/）

| 文档 | 覆盖内容 | 主要代码依据 |
|---|---|---|
| `01-settings.md` | 通用设置、关于、主题切换、防系统休眠开关 | `src/components/settings/SettingsDialog.tsx`、`electron/main/power-save-manager.ts` |
| `02-update-maintenance.md` | 自动更新机制、检查更新/重启安装、磁盘空间告警、深链接协议 | `electron/main/update-manager.ts`、`deep-link.ts`、`DiskSpaceMonitorService.ts`、`src/hooks/useAppUpdate.ts` |
| `03-data-privacy.md` | 数据安全与隐私：品牌数据存储、AI 平台账号、知识库文件的本地化与权限 | `electron/main/security/`（audit-logger、token-store、csp 等） |
| `04-keyboard-shortcuts.md` | 快捷键参考（撰写时核读代码确认实际支持的快捷键） | 撰写时核读 `src/components/` 内键盘事件处理 |

---

## 六、故障排查与 FAQ

| 文档 | 覆盖内容 |
|---|---|
| `troubleshooting.md` | 按症状分类的故障排查：登录失败、工作流卡住、验证码/登录弹窗、知识库导入失败、发布失败、磁盘空间不足等 |
| `faq.md` | 高频问题解答 |

---

## 撰写规范

### 1. 每篇文档标准结构

```markdown
# {标题}

## 概述
（这一篇讲什么、读完能做什么）

## 前置条件
（需要先完成什么、需哪些权限/配置）

## 操作步骤
（编号步骤 + 截图）

## 进阶用法
（可选）

## 常见问题
（FAQ）

## 相关文档
（前置阅读 + 相关篇目 + 下一步）
```

### 2. 路径与引用
- 文档内的"代码依据"列出的源码路径均**相对于 `app/` 根目录**（如 `src/components/...`），供撰写者定位，不使用 `file:///` 绝对路径（跨机器不可用）。
- 文档之间的交叉引用使用**相对路径** markdown 链接（如 `[品牌配置](./how-to/02-brand-config.md)`）。

### 3. 截图与图示
- 每篇操作指南至少包含 1 张界面截图；流程类文档（工作流运行、发布流程、接管流程）配 Mermaid 流程图。
- 截图统一存放 `assets/{doc-slug}/` 目录，命名 `{seq}-{描述}.png`。

### 4. 事实核对
- 撰写每篇前**必须核读对应代码组件**，提取准确的按钮文案、字段名、交互步骤与限制条件。
- 已知关键事实（务必与代码保持一致）：
  - 创建品牌字段：**名称 / Logo / 链接(website_urls) / 素材文件上传**，素材支持 `md/txt/docx/pdf`，无"简介/行业"字段。
  - 知识库**导入**仅支持 `md/txt/docx/pdf`；csv/xlsx/xls/图片只能在文件编辑器中**预览**，不能导入。
  - 品牌配置 Tab 含四个分区：基本信息 / 产品配置 / 竞品配置 / AI 平台跟踪，且**问题矩阵**嵌在"基本信息"与"产品"分区内（品牌级 + 产品级）。
  - 左侧导航的机会/风险**仅显示 new/in_progress 状态**，最多各 5 条。

### 5. 版本对齐
- README 头部标注"本文档对应应用版本 vX.Y.Z"。
- 每篇文档底部标注"最后更新 / 对应版本"。
- 文档变更记录于 `CHANGELOG.md`（可选）。

### 6. 国际化
- 应用支持 i18n，文档默认中文撰写，预留 `en-US/` 子目录扩展位。
- 文档中的界面文案应与当前 i18n 中文文案一致。
