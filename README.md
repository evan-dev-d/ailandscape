# AI 全景图 2026 · 教程版

面向非技术读者的 AI 科普静态网页：4 步入门 → 20 家公司排行 → 按需求挑智能体 → 注册/下载。
浅色教程风默认，右上角可切换深色；单文件、无需服务器。

## 打开方式

双击 `index.html` 即可。

## 页面结构（课程式教程）

- **课程封面**：左侧标题 + 学习目标与阅读时间；右侧「本课目录」（4 节 + 每节预计时间）；顶部有阅读进度条。
1. **第 1 节 · 基础概念**：大模型 / Token / 智能体 / 编程智能体 / 办公智能体，并用一张关系图串起「模型公司 → 大模型 → Token → 智能体 → 任务」。
2. **第 2 节 · 公司排行**：20 家公司按主力模型智力水平排 1–20 名（T1 8 家 / T2 7 家 / T3 5 家）。
   每行 = 排名 + Logo + 公司 + 国家队徽 + 梯队 + 一句话强项 + 3 个主力模型 + 编程/办公智能体 + 注册 / 下载 / 官网。
   支持「全部 / 🇨🇳 国内 / 🌍 海外」筛选。
3. **第 3 节 · 工具选择**：想写代码 / 想办公提效 / 想开源部署，三个清单直接点开官方入口。
4. **第 4 节 · 上手使用**：国内 / 海外 / 编程智能体各一条上手提示。
5. **排行依据**：数据口径、快照日期、榜单链接与免责说明。

每节末尾有「下一节」链接，可按顺序读，也可直接跳到感兴趣的一节。

## 数据快照

- **2026-10-29**（Asia/Shanghai）
- 依据：Artificial Analysis Intelligence Index **v5**（2026-10-27 升级，旧版 v4.3 分数作废）、LMArena（10-22）、Terminal-Bench 4.0、OpenRouter 周用量（10/19–10/25）、OpenCompass 司南（26-07 期）、SuperCLUE（2026 年 7 月期）。
- 三梯队为编辑综合公开榜单后的判断，非机构官方排名；页面内已注明。

## 文件结构

```
ai-landscape/
├─ index.html          # 交付页（教程版，单文件）
├─ README.md
├─ archive/
│  └─ v1-dark.html     # 第一版（深色仪表盘风）备份
└─ research/           # 调研底稿（可追溯来源）
   ├─ oct-updates.md   # 2026-10 榜单快照 + 20 家证据表 + 梯队建议
   ├─ cn-a.md / cn-b.md
   └─ intl-a.md / intl-b.md
```

## 怎么更新数据

1. 在 `index.html` 中搜索 `const DATA = [`。
2. 每家公司一个对象：
   - 基础：`cn` / `en` / `camp`（`cn` 国内、`intl` 海外）/ `tier`（1–3）/ `tierRank`（梯队内序号）
   - 展示：`domain`（favicon 域名）/ `icon`（可选图标直链）/ `mark`（Logo 失败时的文字）/ `tagline`
   - 模型：`model{name,date,desc,stats}` + `alt[]`（备选模型）
   - 智能体：`agents[]`（`type` 为 `coding` 或 `office`，含 `name/form/desc/url`）
   - 入口：`links{signup,download,site}`
3. 排行榜中显示的模型名单在 `const MODELS = {...}` 里单独维护（便于控制展示哪 2–3 个）。
4. 一句话强项在 `const SHORT = {...}`；长智能体名的短显示在 `const AGENT_NAME = {...}`。
5. 改完刷新即可；名次、梯队数量、统计数字都由数据自动生成。

## 部署发布

- `dist/index.html`：发布用文件（和根目录 `index.html` 内容一致）。
- `ai-landscape-deploy.zip`：可直接拖到 Netlify Drop 的压缩包。
- `deploy/部署指南.md`：Netlify / Vercel / Cloudflare Pages / GitHub Pages / 阿里云 OSS / 腾讯云 COS / 局域网分享的完整步骤与检查清单。
- `github-pages/`：**已初始化并提交的 GitHub Pages 发布仓库**（只含页面文件）。
- `deploy/GitHub-Pages-发布步骤.md`：GitHub Pages 逐步发布说明。
- `deploy/一键推送-GitHub.command`：双击运行的推送脚本（已预填 `evan-dev-d / ailandscape`）。

> 发布目标：<https://github.com/evan-dev-d/ailandscape>
> ✅ 已上线：<https://evan-dev-d.github.io/ailandscape/>（2026-11-01，Pages 构建完成，直连 HTTP 200）

> 页面是纯静态单文件，任何静态托管都能放；国内受众优先用国内对象存储 + CDN。

## 说明与已知限制

- **Logo**：优先加载官网 favicon / 指定图标；失败自动显示文字图标，离线也能完整阅读。
- **外链**：均为各公司官方入口；部分域名在特定网络环境下不可达（不是链接失效）。
- **排名会变**：这是 2026 年 10 月快照。下次更新重点复核 AA 指数版本（v5）、LMArena 周榜、国内两榜（更新较慢）。
- **部署**：单文件静态页，可直接放 GitHub Pages / Vercel / 对象存储 / Nginx；上线前建议再跑一遍外链体检。