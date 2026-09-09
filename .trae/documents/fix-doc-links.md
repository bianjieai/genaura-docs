# 文档链接修复计划

## 目标

将所有文档中的内部链接统一为 `/zh/xxx` 格式，消除 404 和 SPA 导航问题。

## 修复策略

按 4 个批次顺序执行，每批完成后验证：

### 批次 1：修复 P0 断裂链接（3 处，手动）

逐个修复完整域名但缺少 `/zh/` 的链接：

| 文件 | 行号 | 搜索内容 | 替换为 |
|---|---|---|---|
| `zh/faq.md` | 231 | `https://docs.genaura.bianjie.ai/how-to/13-article-publish#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98` | `/zh/how-to/13-article-publish#常见问题` |
| `zh/faq.md` | 266 | `https://docs.genaura.bianjie.ai/how-to/14-insight#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98` | `/zh/how-to/14-insight#常见问题` |
| `zh/reference/02-update-maintenance.md` | 219 | `https://docs.genaura.bianjie.ai/how-to/09-file-editor` | `/zh/how-to/09-file-editor` |

### 批次 2：模式 C → B（完整域名 → 内部路径，~180 处）

对以下 10 个文件执行全局替换：
- 搜索：`https://docs.genaura.bianjie.ai/zh/`
- 替换为：`/zh/`

**文件列表：**
1. `zh/glossary.md`
2. `glossary.mdx`
3. `zh/tutorials/01-first-brand.md`
4. `zh/tutorials/02-brand-monitoring.md`
5. `zh/tutorials/03-content-publish.mdx`
6. `zh/reference/01-settings.md`
7. `zh/reference/02-update-maintenance.md`（第 216-220 行的模式 C 链接）
8. `zh/reference/04-keyboard-shortcuts.md`
9. `zh/reference/03-data-privacy.md`（第 242 行）
10. `zh/faq.md`（混合文件中的模式 C 部分）

### 批次 3：模式 A → B（缺少 `/zh/` 前缀，~280 处）

对以下 20+ 个文件执行替换：
- 搜索：`](/`（后跟非 `images/` 和非 `zh/` 的路径）
- 替换为：`](/zh/`

**执行方式：** 逐文件使用 SearchReplace 工具，将 `](/` 替换为 `](/zh/`，然后检查是否有误替换的 `](/zh/images/` 或 `](/zh/zh/` 并回退。

**文件列表（按目录分组）：**

**getting-started/（5 个文件）**
1. `zh/getting-started/01-installation.mdx`
2. `zh/getting-started/02-login-account.md`
3. `zh/getting-started/03-onboarding.md`
4. `zh/getting-started/04-interface-overview.md`
5. `zh/getting-started/01.md`（孤立文件，可选修复）

**concepts/（5 个文件）**
6. `zh/concepts/01-brand-model.md`
7. `zh/concepts/02-workflow.md`
8. `zh/concepts/03-insight-data.md`
9. `zh/concepts/04-ai-agent.md`
10. `zh/concepts/05-opportunity-risk.md`

**how-to/（8 个文件）**
11. `zh/how-to/01-brand-management.md`
12. `zh/how-to/02-brand-config.md`
13. `zh/how-to/03-chat-management.md`
14. `zh/how-to/04-messaging.md`
15. `zh/how-to/05-commands-mentions.md`
16. `zh/how-to/06-sub-agent-approval.md`
17. `zh/how-to/07-opportunities-risks.md`
18. `zh/how-to/08-knowledge-base.md`

**混合文件（同时有模式 A 和模式 C）**
19. `zh/faq.md`（批次 2 已修模式 C，此步修模式 A）
20. `zh/how-to/11-ai-platform-workflows.md`（3 处模式 A）
21. `zh/how-to/13-article-publish.md`（2 处模式 A）

**reference/（2 个文件）**
22. `zh/reference/03-data-privacy.md`（模式 A 部分）
23. `zh/reference/04-keyboard-shortcuts.md`（1 处模式 A）

**根目录 .mdx 文件**
24. `troubleshooting.mdx`
25. `faq.mdx`

### 批次 4：验证

对所有修改过的文件执行验证：
1. Grep 搜索残留的模式 A 链接：`](/` 后跟非 `images/` 和非 `zh/`
2. Grep 搜索残留的模式 C 链接：`https://docs.genaura.bianjie.ai`
3. 确认无 `](/zh/zh/` 或 `](/zh/images/` 误替换

## 注意事项

- 图片路径 `](/images/xxx)` 不修改
- 已正确的 `](/zh/xxx)` 不重复修改
- `zh/getting-started/01.md` 是孤立旧文件，可选修复
- `zh/how-to-2/` 目录是旧版副本，不在此次修复范围内
