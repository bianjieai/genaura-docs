# 文档链接引用问题 - 完整扫描报告

## 背景

项目使用 Mintlify 框架，`docs.json` 配置语言为 `zh`，页面路径以 `zh/` 开头。
线上 URL：`https://docs.genaura.bianjie.ai/zh/xxx`

**三种链接模式：**

* **模式 A**（会 404）：`](/how-to/02-brand-config)` → 解析为 `/how-to/02-brand-config`，缺少 `/zh/` 前缀

* **模式 B**（正确）：`](/zh/how-to/02-brand-config)` → 解析为 `/zh/how-to/02-brand-config`

* **模式 C**（能用但不推荐）：`](https://docs.genaura.bianjie.ai/zh/xxx)` → 完整域名，丧失 SPA 导航

* **模式 C-坏**（会 404）：`](https://docs.genaura.bianjie.ai/how-to/xxx)` → 完整域名但缺少 `/zh/`

**统一修复方案：全部改为模式 B** `](/zh/xxx)`

***

## 一、P0 断裂链接（完整域名缺少 `/zh/`，确定 404）

### 文件：`zh/faq.md`

| 行号  | 现有链接                                                                                             | 修复后链接                                |
| --- | ------------------------------------------------------------------------------------------------ | ------------------------------------ |
| 231 | `https://docs.genaura.bianjie.ai/how-to/13-article-publish#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98` | `/zh/how-to/13-article-publish#常见问题` |
| 266 | `https://docs.genaura.bianjie.ai/how-to/14-insight#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98`         | `/zh/how-to/14-insight#常见问题`         |

### 文件：`zh/reference/02-update-maintenance.md`

| 行号  | 现有链接                                                    | 修复后链接                       |
| --- | ------------------------------------------------------- | --------------------------- |
| 37  | `/how-to/09-file-editor`                                | `/zh/how-to/09-file-editor` |
| 219 | `https://docs.genaura.bianjie.ai/how-to/09-file-editor` | `/zh/how-to/09-file-editor` |

***

## 二、模式 A → 模式 B（缺少 `/zh/` 前缀，会 404）

### 文件：`zh/faq.md`（\~20 处模式 A + \~20 处模式 C）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 11  | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 12  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 13  | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 14  | `/glossary`                              | `/zh/glossary`                              |
| 41  | `/reference/02-update-maintenance`       | `/zh/reference/02-update-maintenance`       |
| 45  | `/reference/03-data-privacy`             | `/zh/reference/03-data-privacy`             |
| 53  | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 63  | `/getting-started/02-login-account#常见问题` | `/zh/getting-started/02-login-account#常见问题` |
| 87  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 87  | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 131 | `/how-to/04-messaging#常见问题`              | `/zh/how-to/04-messaging#常见问题`              |
| 153 | `/how-to/11-ai-platform-workflows`       | `/zh/how-to/11-ai-platform-workflows`       |
| 157 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 173 | `/how-to/10-browser#常见问题`                | `/zh/how-to/10-browser#常见问题`                |
| 185 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 195 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 203 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 207 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 219 | `/how-to/13-article-publish`             | `/zh/how-to/13-article-publish`             |
| 258 | `/how-to/14-insight#常见问题`                | `/zh/how-to/14-insight#常见问题`                |
| 270 | `/how-to/15-emotion-analysis`            | `/zh/how-to/15-emotion-analysis`            |
| 274 | `/how-to/15-emotion-analysis#常见问题`       | `/zh/how-to/15-emotion-analysis#常见问题`       |
| 278 | `/how-to/07-opportunities-risks`         | `/zh/how-to/07-opportunities-risks`         |
| 282 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |
| 290 | `/how-to/12-cron-tasks#常见问题`             | `/zh/how-to/12-cron-tasks#常见问题`             |
| 306 | `/reference/01-settings`                 | `/zh/reference/01-settings`                 |
| 310 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 317 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 318 | `/glossary`                              | `/zh/glossary`                              |
| 319 | `/getting-started/01-installation`       | `/zh/getting-started/01-installation`       |
| 319 | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 319 | `/getting-started/03-onboarding`         | `/zh/getting-started/03-onboarding`         |
| 319 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 320 | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 320 | `/concepts/02-workflow`                  | `/zh/concepts/02-workflow`                  |
| 320 | `/concepts/03-insight-data`              | `/zh/concepts/03-insight-data`              |
| 320 | `/concepts/04-ai-agent`                  | `/zh/concepts/04-ai-agent`                  |
| 320 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |
| 321 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 321 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 321 | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 321 | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 321 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 321 | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 321 | `/how-to/07-opportunities-risks`         | `/zh/how-to/07-opportunities-risks`         |
| 321 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 321 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 321 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 321 | `/how-to/11-ai-platform-workflows`       | `/zh/how-to/11-ai-platform-workflows`       |
| 321 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 321 | `/how-to/13-article-publish`             | `/zh/how-to/13-article-publish`             |
| 321 | `/how-to/14-insight`                     | `/zh/how-to/14-insight`                     |
| 321 | `/how-to/15-emotion-analysis`            | `/zh/how-to/15-emotion-analysis`            |
| 321 | `/how-to/16-preference-insight`          | `/zh/how-to/16-preference-insight`          |
| 322 | `/reference/01-settings`                 | `/zh/reference/01-settings`                 |
| 322 | `/reference/02-update-maintenance`       | `/zh/reference/02-update-maintenance`       |
| 322 | `/reference/03-data-privacy`             | `/zh/reference/03-data-privacy`             |

***

### 文件：`zh/how-to/01-brand-management.md`（17 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 9   | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 26  | `/getting-started/01-installation`       | `/zh/getting-started/01-installation`       |
| 27  | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 28  | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 52  | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 102 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 109 | `/tutorials/01-first-brand`              | `/zh/tutorials/01-first-brand`              |
| 125 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 148 | `/getting-started/01-installation`       | `/zh/getting-started/01-installation`       |
| 149 | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 150 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 152 | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 154 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 155 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 157 | `/tutorials/01-first-brand`              | `/zh/tutorials/01-first-brand`              |

***

### 文件：`zh/how-to/02-brand-config.md`（12 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 33  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 53  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 163 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 164 | `/how-to/14-insight`                     | `/zh/how-to/14-insight`                     |
| 165 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 200 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 201 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 203 | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 205 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 206 | `/how-to/14-insight`                     | `/zh/how-to/14-insight`                     |
| 207 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 209 | `/tutorials/01-first-brand`              | `/zh/tutorials/01-first-brand`              |
| 210 | `/tutorials/02-brand-monitoring`         | `/zh/tutorials/02-brand-monitoring`         |

***

### 文件：`zh/how-to/03-chat-management.md`（10 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 26  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 101 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 113 | `/how-to/07-opportunities-risks`         | `/zh/how-to/07-opportunities-risks`         |
| 137 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 148 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 149 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 151 | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 152 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 153 | `/how-to/07-opportunities-risks`         | `/zh/how-to/07-opportunities-risks`         |
| 154 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |

***

### 文件：`zh/how-to/04-messaging.md`（9 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 25  | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 42  | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 62  | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 98  | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 163 | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 164 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 166 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 167 | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 168 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |

***

### 文件：`zh/how-to/05-commands-mentions.md`（6 处）

| 行号  | 现有链接                         | 修复后链接                           |
| --- | ---------------------------- | ------------------------------- |
| 26  | `/how-to/03-chat-management` | `/zh/how-to/03-chat-management` |
| 28  | `/how-to/08-knowledge-base`  | `/zh/how-to/08-knowledge-base`  |
| 91  | `/how-to/08-knowledge-base`  | `/zh/how-to/08-knowledge-base`  |
| 137 | `/how-to/04-messaging`       | `/zh/how-to/04-messaging`       |
| 138 | `/how-to/03-chat-management` | `/zh/how-to/03-chat-management` |
| 140 | `/how-to/08-knowledge-base`  | `/zh/how-to/08-knowledge-base`  |
| 141 | `/how-to/02-brand-config`    | `/zh/how-to/02-brand-config`    |

***

### 文件：`zh/how-to/06-sub-agent-approval.md`（4 处）

| 行号  | 现有链接                           | 修复后链接                             |
| --- | ------------------------------ | --------------------------------- |
| 23  | `/how-to/04-messaging`         | `/zh/how-to/04-messaging`         |
| 149 | `/how-to/04-messaging`         | `/zh/how-to/04-messaging`         |
| 150 | `/concepts/04-ai-agent`        | `/zh/concepts/04-ai-agent`        |
| 152 | `/how-to/05-commands-mentions` | `/zh/how-to/05-commands-mentions` |
| 153 | `/how-to/08-knowledge-base`    | `/zh/how-to/08-knowledge-base`    |

***

### 文件：`zh/how-to/07-opportunities-risks.md`（9 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 26  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 28  | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 135 | `/concepts/04-ai-agent`                  | `/zh/concepts/04-ai-agent`                  |
| 135 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |
| 170 | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 171 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 173 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |
| 174 | `/concepts/04-ai-agent`                  | `/zh/concepts/04-ai-agent`                  |
| 176 | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 177 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |

***

### 文件：`zh/how-to/08-knowledge-base.md`（16 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 27  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 28  | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 51  | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 97  | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 152 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 250 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 259 | `/how-to/13-article-publish`             | `/zh/how-to/13-article-publish`             |
| 283 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 291 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 307 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 318 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 319 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 320 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 321 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 322 | `/how-to/13-article-publish`             | `/zh/how-to/13-article-publish`             |
| 323 | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |

***

### 文件：`zh/how-to/11-ai-platform-workflows.md`（2 处模式 A）

| 行号  | 现有链接                            | 修复后链接                              |
| --- | ------------------------------- | ---------------------------------- |
| 162 | `/how-to/14-insight`            | `/zh/how-to/14-insight`            |
| 162 | `/how-to/15-emotion-analysis`   | `/zh/how-to/15-emotion-analysis`   |
| 162 | `/how-to/16-preference-insight` | `/zh/how-to/16-preference-insight` |

***

### 文件：`zh/how-to/13-article-publish.md`（3 处模式 A）

| 行号  | 现有链接                            | 修复后链接                              |
| --- | ------------------------------- | ---------------------------------- |
| 22  | `/tutorials/03-content-publish` | `/zh/tutorials/03-content-publish` |
| 275 | `/tutorials/03-content-publish` | `/zh/tutorials/03-content-publish` |

***

### 文件：`zh/concepts/01-brand-model.md`（7 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 18  | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 19  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 19  | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 155 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 170 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 171 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 171 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 172 | `/concepts/02-workflow`                  | `/zh/concepts/02-workflow`                  |
| 172 | `/concepts/03-insight-data`              | `/zh/concepts/03-insight-data`              |
| 173 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |

***

### 文件：`zh/concepts/02-workflow.md`（8 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 18  | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 19  | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 119 | `/concepts/03-insight-data`              | `/zh/concepts/03-insight-data`              |
| 125 | `/how-to/11-ai-platform-workflows`       | `/zh/how-to/11-ai-platform-workflows`       |
| 126 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 130 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 152 | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 152 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 153 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 153 | `/how-to/11-ai-platform-workflows`       | `/zh/how-to/11-ai-platform-workflows`       |
| 153 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 154 | `/concepts/03-insight-data`              | `/zh/concepts/03-insight-data`              |
| 154 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |

***

### 文件：`zh/concepts/03-insight-data.md`（8 处）

| 行号  | 现有链接                               | 修复后链接                                 |
| --- | ---------------------------------- | ------------------------------------- |
| 20  | `/concepts/01-brand-model`         | `/zh/concepts/01-brand-model`         |
| 21  | `/concepts/02-workflow`            | `/zh/concepts/02-workflow`            |
| 136 | `/concepts/01-brand-model`         | `/zh/concepts/01-brand-model`         |
| 155 | `/concepts/01-brand-model`         | `/zh/concepts/01-brand-model`         |
| 155 | `/concepts/02-workflow`            | `/zh/concepts/02-workflow`            |
| 156 | `/how-to/14-insight`               | `/zh/how-to/14-insight`               |
| 156 | `/how-to/15-emotion-analysis`      | `/zh/how-to/15-emotion-analysis`      |
| 156 | `/how-to/16-preference-insight`    | `/zh/how-to/16-preference-insight`    |
| 156 | `/how-to/11-ai-platform-workflows` | `/zh/how-to/11-ai-platform-workflows` |
| 156 | `/how-to/12-cron-tasks`            | `/zh/how-to/12-cron-tasks`            |
| 157 | `/concepts/04-ai-agent`            | `/zh/concepts/04-ai-agent`            |
| 157 | `/concepts/05-opportunity-risk`    | `/zh/concepts/05-opportunity-risk`    |

***

### 文件：`zh/concepts/04-ai-agent.md`（6 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 17  | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 18  | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 18  | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 152 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 153 | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 153 | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 153 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 154 | `/concepts/02-workflow`                  | `/zh/concepts/02-workflow`                  |
| 154 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |

***

### 文件：`zh/concepts/05-opportunity-risk.md`（7 处）

| 行号  | 现有链接                             | 修复后链接                               |
| --- | -------------------------------- | ----------------------------------- |
| 18  | `/concepts/02-workflow`          | `/zh/concepts/02-workflow`          |
| 19  | `/concepts/03-insight-data`      | `/zh/concepts/03-insight-data`      |
| 20  | `/how-to/07-opportunities-risks` | `/zh/how-to/07-opportunities-risks` |
| 162 | `/concepts/02-workflow`          | `/zh/concepts/02-workflow`          |
| 162 | `/concepts/03-insight-data`      | `/zh/concepts/03-insight-data`      |
| 163 | `/how-to/07-opportunities-risks` | `/zh/how-to/07-opportunities-risks` |
| 163 | `/how-to/04-messaging`           | `/zh/how-to/04-messaging`           |
| 164 | `/concepts/04-ai-agent`          | `/zh/concepts/04-ai-agent`          |
| 164 | `/concepts/01-brand-model`       | `/zh/concepts/01-brand-model`       |

***

### 文件：`zh/getting-started/01-installation.mdx`（\~10 处模式 A）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 71  | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 73  | `/getting-started/03-onboarding`         | `/zh/getting-started/03-onboarding`         |
| 132 | `/reference/02-update-maintenance`       | `/zh/reference/02-update-maintenance`       |
| 152 | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 153 | `/getting-started/03-onboarding`         | `/zh/getting-started/03-onboarding`         |
| 154 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 155 | `/reference/02-update-maintenance`       | `/zh/reference/02-update-maintenance`       |
| 156 | `/reference/03-data-privacy`             | `/zh/reference/03-data-privacy`             |

***

### 文件：`zh/getting-started/02-login-account.md`（待确认，需扫描）

### 文件：`zh/getting-started/03-onboarding.md`（\~15 处）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 19  | `/getting-started/01-installation`       | `/zh/getting-started/01-installation`       |
| 19  | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 165 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 173 | `/tutorials/01-first-brand`              | `/zh/tutorials/01-first-brand`              |
| 193 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 200 | `/reference/01-settings`                 | `/zh/reference/01-settings`                 |
| 205 | `/tutorials/01-first-brand`              | `/zh/tutorials/01-first-brand`              |
| 209 | `/getting-started/01-installation`       | `/zh/getting-started/01-installation`       |
| 210 | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 211 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 212 | `/tutorials/01-first-brand`              | `/zh/tutorials/01-first-brand`              |
| 213 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 214 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |

***

### 文件：`zh/getting-started/04-interface-overview.md`（\~20 处）

| 行号  | 现有链接                                | 修复后链接                                  |
| --- | ----------------------------------- | -------------------------------------- |
| 21  | `/getting-started/01-installation`  | `/zh/getting-started/01-installation`  |
| 21  | `/getting-started/02-login-account` | `/zh/getting-started/02-login-account` |
| 23  | `/getting-started/03-onboarding`    | `/zh/getting-started/03-onboarding`    |
| 55  | `/how-to/01-brand-management`       | `/zh/how-to/01-brand-management`       |
| 60  | `/how-to/07-opportunities-risks`    | `/zh/how-to/07-opportunities-risks`    |
| 77  | `/getting-started/02-login-account` | `/zh/getting-started/02-login-account` |
| 90  | `/how-to/04-messaging`              | `/zh/how-to/04-messaging`              |
| 90  | `/how-to/05-commands-mentions`      | `/zh/how-to/05-commands-mentions`      |
| 120 | `/how-to/11-ai-platform-workflows`  | `/zh/how-to/11-ai-platform-workflows`  |
| 122 | `/how-to/10-browser`                | `/zh/how-to/10-browser`                |
| 182 | `/how-to/01-brand-management`       | `/zh/how-to/01-brand-management`       |
| 226 | `/how-to/07-opportunities-risks`    | `/zh/how-to/07-opportunities-risks`    |
| 241 | `/getting-started/01-installation`  | `/zh/getting-started/01-installation`  |
| 242 | `/getting-started/02-login-account` | `/zh/getting-started/02-login-account` |
| 243 | `/getting-started/03-onboarding`    | `/zh/getting-started/03-onboarding`    |
| 244 | `/tutorials/01-first-brand`         | `/zh/tutorials/01-first-brand`         |
| 245 | `/how-to/01-brand-management`       | `/zh/how-to/01-brand-management`       |
| 246 | `/how-to/03-chat-management`        | `/zh/how-to/03-chat-management`        |
| 247 | `/how-to/07-opportunities-risks`    | `/zh/how-to/07-opportunities-risks`    |
| 248 | `/reference/01-settings`            | `/zh/reference/01-settings`            |

***

### 文件：`zh/reference/03-data-privacy.md`（\~12 处）

| 行号  | 现有链接                                | 修复后链接                                  |
| --- | ----------------------------------- | -------------------------------------- |
| 59  | `/how-to/01-brand-management`       | `/zh/how-to/01-brand-management`       |
| 79  | `/how-to/10-browser`                | `/zh/how-to/10-browser`                |
| 139 | `/how-to/08-knowledge-base`         | `/zh/how-to/08-knowledge-base`         |
| 150 | `/how-to/09-file-editor`            | `/zh/how-to/09-file-editor`            |
| 209 | `/how-to/01-brand-management`       | `/zh/how-to/01-brand-management`       |
| 239 | `/reference/01-settings`            | `/zh/reference/01-settings`            |
| 240 | `/reference/02-update-maintenance`  | `/zh/reference/02-update-maintenance`  |
| 241 | `/getting-started/02-login-account` | `/zh/getting-started/02-login-account` |
| 243 | `/how-to/09-file-editor`            | `/zh/how-to/09-file-editor`            |
| 244 | `/how-to/10-browser`                | `/zh/how-to/10-browser`                |
| 245 | `/how-to/11-ai-platform-workflows`  | `/zh/how-to/11-ai-platform-workflows`  |
| 246 | `/how-to/01-brand-management`       | `/zh/how-to/01-brand-management`       |

***

### 文件：`zh/reference/04-keyboard-shortcuts.md`（2 处模式 A）

| 行号  | 现有链接                     | 修复后链接                       |
| --- | ------------------------ | --------------------------- |
| 212 | `/how-to/09-file-editor` | `/zh/how-to/09-file-editor` |

***

### 文件：`troubleshooting.mdx`（根目录，\~25 处模式 A）

| 行号  | 现有链接                                      | 修复后链接                                        |
| --- | ----------------------------------------- | -------------------------------------------- |
| 26  | `/faq`                                    | `/zh/faq`                                    |
| 30  | `/getting-started/01-installation`        | `/zh/getting-started/01-installation`        |
| 31  | `/getting-started/02-login-account`       | `/zh/getting-started/02-login-account`       |
| 33  | `/how-to/10-browser`                      | `/zh/how-to/10-browser`                      |
| 103 | `/getting-started/02-login-account#常见问题`  | `/zh/getting-started/02-login-account#常见问题`  |
| 167 | `/how-to/11-ai-platform-workflows`        | `/zh/how-to/11-ai-platform-workflows`        |
| 167 | `/concepts/02-workflow`                   | `/zh/concepts/02-workflow`                   |
| 215 | `/how-to/10-browser`                      | `/zh/how-to/10-browser`                      |
| 217 | `/how-to/10-browser`                      | `/zh/how-to/10-browser`                      |
| 217 | `/concepts/02-workflow#接管机制`              | `/zh/concepts/02-workflow#接管机制`              |
| 239 | `/how-to/09-file-editor`                  | `/zh/how-to/09-file-editor`                  |
| 310 | `/how-to/08-knowledge-base`               | `/zh/how-to/08-knowledge-base`               |
| 372 | `/how-to/13-article-publish`              | `/zh/how-to/13-article-publish`              |
| 417 | `/reference/02-update-maintenance#磁盘空间告警` | `/zh/reference/02-update-maintenance#磁盘空间告警` |
| 453 | `/getting-started/01-installation#常见问题`   | `/zh/getting-started/01-installation#常见问题`   |
| 526 | `/how-to/04-messaging#常见问题`               | `/zh/how-to/04-messaging#常见问题`               |
| 533 | `/zh/getting-started/01-installation`     | （已正确，无需修改）                                   |
| 534 | `/getting-started/02-login-account`       | `/zh/getting-started/02-login-account`       |
| 535 | `/getting-started/04-interface-overview`  | `/zh/getting-started/04-interface-overview`  |
| 537 | `/concepts/02-workflow`                   | `/zh/concepts/02-workflow`                   |
| 538 | `/concepts/04-ai-agent`                   | `/zh/concepts/04-ai-agent`                   |
| 540 | `/how-to/08-knowledge-base`               | `/zh/how-to/08-knowledge-base`               |
| 541 | `/how-to/09-file-editor`                  | `/zh/how-to/09-file-editor`                  |
| 542 | `/how-to/10-browser`                      | `/zh/how-to/10-browser`                      |
| 543 | `/how-to/11-ai-platform-workflows`        | `/zh/how-to/11-ai-platform-workflows`        |
| 544 | `/how-to/12-cron-tasks`                   | `/zh/how-to/12-cron-tasks`                   |
| 545 | `/how-to/13-article-publish`              | `/zh/how-to/13-article-publish`              |
| 547 | `/reference/01-settings`                  | `/zh/reference/01-settings`                  |
| 548 | `/reference/02-update-maintenance`        | `/zh/reference/02-update-maintenance`        |
| 549 | `/reference/03-data-privacy`              | `/zh/reference/03-data-privacy`              |
| 550 | `/faq`                                    | `/zh/faq`                                    |

***

### 文件：`faq.mdx`（根目录，\~40 处模式 A）

| 行号  | 现有链接                                     | 修复后链接                                       |
| --- | ---------------------------------------- | ------------------------------------------- |
| 41  | `/reference/02-update-maintenance`       | `/zh/reference/02-update-maintenance`       |
| 45  | `/reference/03-data-privacy`             | `/zh/reference/03-data-privacy`             |
| 53  | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 87  | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 87  | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 107 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 111 | `/how-to/02-brand-config#常见问题`           | `/zh/how-to/02-brand-config#常见问题`           |
| 119 | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 123 | `/how-to/05-commands-mentions#常见问题`      | `/zh/how-to/05-commands-mentions#常见问题`      |
| 127 | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 127 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 131 | `/how-to/04-messaging#常见问题`              | `/zh/how-to/04-messaging#常见问题`              |
| 135 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 139 | `/how-to/06-sub-agent-approval#常见问题`     | `/zh/how-to/06-sub-agent-approval#常见问题`     |
| 143 | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 153 | `/how-to/11-ai-platform-workflows`       | `/zh/how-to/11-ai-platform-workflows`       |
| 157 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 161 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 165 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 169 | `/concepts/02-workflow`                  | `/zh/concepts/02-workflow`                  |
| 173 | `/how-to/10-browser#常见问题`                | `/zh/how-to/10-browser#常见问题`                |
| 185 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 195 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 199 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 203 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 207 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 219 | `/how-to/13-article-publish`             | `/zh/how-to/13-article-publish`             |
| 227 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 231 | `/how-to/13-article-publish#常见问题`        | `/zh/how-to/13-article-publish#常见问题`        |
| 258 | `/concepts/03-insight-data`              | `/zh/concepts/03-insight-data`              |
| 258 | `/how-to/14-insight#常见问题`                | `/zh/how-to/14-insight#常见问题`                |
| 266 | `/how-to/14-insight#常见问题`                | `/zh/how-to/14-insight#常见问题`                |
| 270 | `/how-to/15-emotion-analysis`            | `/zh/how-to/15-emotion-analysis`            |
| 274 | `/how-to/15-emotion-analysis#常见问题`       | `/zh/how-to/15-emotion-analysis#常见问题`       |
| 278 | `/how-to/07-opportunities-risks`         | `/zh/how-to/07-opportunities-risks`         |
| 282 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |
| 290 | `/how-to/12-cron-tasks#常见问题`             | `/zh/how-to/12-cron-tasks#常见问题`             |
| 306 | `/reference/01-settings`                 | `/zh/reference/01-settings`                 |
| 310 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 317 | `/troubleshooting`                       | `/zh/troubleshooting`                       |
| 318 | `/glossary`                              | `/zh/glossary`                              |
| 319 | `/getting-started/01-installation`       | `/zh/getting-started/01-installation`       |
| 319 | `/getting-started/02-login-account`      | `/zh/getting-started/02-login-account`      |
| 319 | `/getting-started/03-onboarding`         | `/zh/getting-started/03-onboarding`         |
| 319 | `/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 320 | `/concepts/01-brand-model`               | `/zh/concepts/01-brand-model`               |
| 320 | `/concepts/02-workflow`                  | `/zh/concepts/02-workflow`                  |
| 320 | `/concepts/03-insight-data`              | `/zh/concepts/03-insight-data`              |
| 320 | `/concepts/04-ai-agent`                  | `/zh/concepts/04-ai-agent`                  |
| 320 | `/concepts/05-opportunity-risk`          | `/zh/concepts/05-opportunity-risk`          |
| 321 | `/how-to/01-brand-management`            | `/zh/how-to/01-brand-management`            |
| 321 | `/how-to/02-brand-config`                | `/zh/how-to/02-brand-config`                |
| 321 | `/how-to/03-chat-management`             | `/zh/how-to/03-chat-management`             |
| 321 | `/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 321 | `/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 321 | `/how-to/06-sub-agent-approval`          | `/zh/how-to/06-sub-agent-approval`          |
| 321 | `/how-to/07-opportunities-risks`         | `/zh/how-to/07-opportunities-risks`         |
| 321 | `/how-to/08-knowledge-base`              | `/zh/how-to/08-knowledge-base`              |
| 321 | `/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 321 | `/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 321 | `/how-to/11-ai-platform-workflows`       | `/zh/how-to/11-ai-platform-workflows`       |
| 321 | `/how-to/12-cron-tasks`                  | `/zh/how-to/12-cron-tasks`                  |
| 321 | `/how-to/13-article-publish`             | `/zh/how-to/13-article-publish`             |
| 321 | `/how-to/14-insight`                     | `/zh/how-to/14-insight`                     |
| 321 | `/how-to/15-emotion-analysis`            | `/zh/how-to/15-emotion-analysis`            |
| 321 | `/how-to/16-preference-insight`          | `/zh/how-to/16-preference-insight`          |
| 322 | `/reference/01-settings`                 | `/zh/reference/01-settings`                 |
| 322 | `/reference/02-update-maintenance`       | `/zh/reference/02-update-maintenance`       |
| 322 | `/reference/03-data-privacy`             | `/zh/reference/03-data-privacy`             |

***

## 三、模式 C → 模式 B（完整域名 → 内部路径）

以下文件中的 `https://docs.genaura.bianjie.ai/zh/xxx` 需改为 `/zh/xxx`：

### 文件：`zh/glossary.md`（\~57 处）

所有链接均使用 `https://docs.genaura.bianjie.ai/zh/...` 格式，需批量替换为 `/zh/...`。

### 文件：`glossary.mdx`（根目录，\~57 处）

同上，所有链接均使用完整域名格式。

### 文件：`zh/tutorials/01-first-brand.md`（\~15 处）

所有链接均使用 `https://docs.genaura.bianjie.ai/zh/...` 格式。

### 文件：`zh/tutorials/02-brand-monitoring.md`（\~20 处）

所有链接均使用 `https://docs.genaura.bianjie.ai/zh/...` 格式。

### 文件：`zh/tutorials/03-content-publish.mdx`（\~10 处）

所有链接均使用 `https://docs.genaura.bianjie.ai/zh/...` 格式。

### 文件：`zh/reference/01-settings.md`（\~8 处）

所有链接均使用 `https://docs.genaura.bianjie.ai/zh/...` 格式。

### 文件：`zh/reference/04-keyboard-shortcuts.md`（\~7 处模式 C）

| 行号  | 现有链接                                                                       | 修复后链接                                       |
| --- | -------------------------------------------------------------------------- | ------------------------------------------- |
| 225 | `https://docs.genaura.bianjie.ai/zh/getting-started/04-interface-overview` | `/zh/getting-started/04-interface-overview` |
| 226 | `https://docs.genaura.bianjie.ai/zh/how-to/04-messaging`                   | `/zh/how-to/04-messaging`                   |
| 227 | `https://docs.genaura.bianjie.ai/zh/how-to/05-commands-mentions`           | `/zh/how-to/05-commands-mentions`           |
| 228 | `https://docs.genaura.bianjie.ai/zh/how-to/09-file-editor`                 | `/zh/how-to/09-file-editor`                 |
| 229 | `https://docs.genaura.bianjie.ai/zh/how-to/10-browser`                     | `/zh/how-to/10-browser`                     |
| 230 | `https://docs.genaura.bianjie.ai/zh/getting-started/03-onboarding`         | `/zh/getting-started/03-onboarding`         |
| 231 | `https://docs.genaura.bianjie.ai/zh/reference/01-settings`                 | `/zh/reference/01-settings`                 |

### 文件：`zh/reference/02-update-maintenance.md`（3 处模式 C）

| 行号  | 现有链接                                                                  | 修复后链接                                  |
| --- | --------------------------------------------------------------------- | -------------------------------------- |
| 216 | `https://docs.genaura.bianjie.ai/zh/reference/01-settings`            | `/zh/reference/01-settings`            |
| 217 | `https://docs.genaura.bianjie.ai/zh/getting-started/01-installation`  | `/zh/getting-started/01-installation`  |
| 218 | `https://docs.genaura.bianjie.ai/zh/getting-started/02-login-account` | `/zh/getting-started/02-login-account` |
| 220 | `https://docs.genaura.bianjie.ai/zh/reference/03-data-privacy`        | `/zh/reference/03-data-privacy`        |

### 文件：`zh/reference/03-data-privacy.md`（1 处模式 C）

| 行号  | 现有链接                                                          | 修复后链接                          |
| --- | ------------------------------------------------------------- | ------------------------------ |
| 242 | `https://docs.genaura.bianjie.ai/zh/how-to/08-knowledge-base` | `/zh/how-to/08-knowledge-base` |

***

## 四、统计汇总

| 问题类型                     | 文件数          | 链接数（约）        |
| ------------------------ | ------------ | ------------- |
| P0：完整域名缺少 `/zh/`（确定 404） | 2            | 3             |
| 模式 A → B（缺少 `/zh/` 前缀）   | 20+          | \~280         |
| 模式 C → B（完整域名 → 内部路径）    | 10           | \~180         |
| **合计**                   | **\~25 个文件** | **\~463 处链接** |

***

## 五、修复策略

**批量替换规则（按优先级执行）：**

1. **先修 P0**：手动修复 3 处确定性 404 链接
2. **模式 C → B**：`https://docs.genaura.bianjie.ai/zh/` → `/zh/`（全局替换）
3. **模式 C-坏 → B**：`https://docs.genaura.bianjie.ai/how-to/` → `/zh/how-to/` 等（逐个修复）
4. **模式 A → B**：对每个文件，将 `](/` 替换为 `](/zh/`（注意排除 `](/images/` 和已有的 `](/zh/`）

**注意：**

* 图片路径 `](/images/xxx)` 不需要修改

* 已经是 `](/zh/xxx)` 的链接不要重复修改（避免变成 `](/zh/zh/xxx)`）

* 根目录的 `faq.mdx`、`glossary.mdx`、`troubleshooting.mdx` 虽不在 docs.json 导航中，但也需修复

