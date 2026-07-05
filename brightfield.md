# WebLink Hub

WebLink Hub 是一个面向开发者、技术研究人员与内容聚合者的外链资源管理与导航系统。该项目定位于对分散在网络各处的高质量技术文章、教程、文档与工具链接进行结构化整理与索引，解决个人书签难以分类、团队共享不便、链接失效难以追踪等常见问题。通过统一的条目格式与批次化管理流程，WebLink Hub 能够将大量原始 URL 转化为可检索、可审计、可快速浏览的知识库。

本项目适用于需要长期维护大量外链资源的个人知识管理者、技术社区运营者以及企业内部的文档中心维护团队。第 13/40 批资源包含 250 个指向技术博客文章的外链，涵盖后端开发、前端工程、数据库运维、算法设计、系统架构等多个方向。

## 功能概览

**批次化管理**：每批资源独立编号，支持增量导入与版本追踪，便于多轮审核与逐步完善。

**原始链接保留**：系统强制保留用户提供的原始 URL 字符串，不做协议补全、域名规范化或路径改写，确保链接可追溯至最初来源。

**多维度分类**：每个资源条目可关联多个技术标签与场景标签，支持按编程语言、框架、难度等级、文章类型进行筛选。

**链接健康检查**：内置链接可达性检测模块，可定期扫描已收录资源的状态码与响应时间，标记失效或重定向链接。

**结构化导出**：支持将资源列表导出为 Markdown、JSON、CSV 等格式，方便嵌入文档、导入数据库或进行二次分析。

**全文检索**：基于资源标题、摘要、标签与来源域名的轻量级全文搜索，帮助用户快速定位特定主题的文章。

**审计日志**：记录每次资源新增、修改、删除操作的操作人、时间戳与变更摘要，满足团队协作场景下的合规要求。

## 应用场景

**技术团队内部知识库建设**：开发团队可将项目周报、技术调研报告、踩坑记录中引用的外部文章统一收录至 WebLink Hub，形成团队共享的技术参考库，避免重复查找与信息孤岛。

**开源项目文档的外链管理**：开源项目的 README 或 Wiki 中常需引用大量外部资源，使用 WebLink Hub 可对这些引用进行集中管理，在版本发布前统一检查链接有效性，减少文档中的死链。

**技术社区的内容聚合与推荐**：技术博客运营者或论坛版主可利用本系统收集投稿文章、优质回复或外部转载来源，按批次发布推荐列表，提升内容发现效率。

**个人技术阅读工作流优化**：开发者可将日常阅读中发现的优质文章快速存入待处理批次，利用周末集中添加标签与摘要，将碎片化阅读转化为结构化知识资产。

## 快速开始

以下命令演示如何在本地环境克隆项目、安装依赖并启动开发服务器。

```bash
git clone https://github.com/example/weblink-hub.git
cd weblink-hub
npm install
npm run dev
```

若使用 yarn 或 pnpm，请将 `npm install` 替换为对应包管理器的安装命令。启动成功后，访问 `http://localhost:3000` 即可进入资源管理界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 | 或 yarn >= 1.22、pnpm >= 8.0 |
| SQLite | >= 3.35 | 内嵌数据库，用于存储资源条目与元数据 |
| Git | >= 2.30 | 用于克隆仓库与版本管理 |
| 现代浏览器 | 最新两个版本 | 开发调试与界面预览，推荐 Chrome、Firefox 或 Edge |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速搭建开发环境、导入首批资源、理解核心数据模型 |
| 批次操作手册 | docs/batch-operations.md | 如何创建新批次、批量导入 URL、执行链接检查与状态更新 |
| API 参考 | docs/api-reference.md | 资源管理、检索、导出等 RESTful 接口的详细说明与示例 |
| 贡献规范 | docs/contributing.md | 提交资源增删改的流程、代码风格要求与 Pull Request 模板 |

## 资源列表

- http://www.blog.jnjpgf.cn/Article/details/67652.sHtML
- http://www.blog.jnjpgf.cn/Article/details/29929.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7213.sHtML
- http://www.blog.nzfnve.cn/Article/details/64490.sHtML
- http://www.blog.puhvjy.cn/Article/details/56991.sHtML
- http://www.blog.nzfnve.cn/Article/details/56346.sHtML
- http://www.blog.nwbbyt.cn/Article/details/032995.sHtML
- http://www.blog.nzfnve.cn/Article/details/548136.sHtML
- http://www.blog.puhvjy.cn/Article/details/4626461.sHtML
- http://www.blog.puhvjy.cn/Article/details/4700.sHtML
- http://www.blog.nzfnve.cn/Article/details/7929.sHtML
- http://www.blog.nzfnve.cn/Article/details/970983.sHtML
- http://www.blog.nwbbyt.cn/Article/details/95791.sHtML
- http://www.blog.jnjpgf.cn/Article/details/495991.sHtML
- http://www.blog.jnjpgf.cn/Article/details/630445.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2228.sHtML
- http://www.blog.nwbbyt.cn/Article/details/25602.sHtML
- http://www.blog.nwbbyt.cn/Article/details/317779.sHtML
- http://www.blog.nzfnve.cn/Article/details/31367.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0053.sHtML
- http://www.blog.jnjpgf.cn/Article/details/802437.sHtML
- http://www.blog.nwbbyt.cn/Article/details/190624.sHtML
- http://www.blog.nzfnve.cn/Article/details/135044.sHtML
- http://www.blog.jnjpgf.cn/Article/details/34432.sHtML
- http://www.blog.puhvjy.cn/Article/details/0744.sHtML
- http://www.blog.puhvjy.cn/Article/details/24031.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2929.sHtML
- http://www.blog.puhvjy.cn/Article/details/52406.sHtML
- http://www.blog.nzfnve.cn/Article/details/19476.sHtML
- http://www.blog.puhvjy.cn/Article/details/2569765.sHtML
- http://www.blog.jnjpgf.cn/Article/details/121292.sHtML
- http://www.blog.nzfnve.cn/Article/details/8573.sHtML
- http://www.blog.nwbbyt.cn/Article/details/67311.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7629771.sHtML
- http://www.blog.puhvjy.cn/Article/details/840951.sHtML
- http://www.blog.puhvjy.cn/Article/details/3444564.sHtML
- http://www.blog.puhvjy.cn/Article/details/48520.sHtML
- http://www.blog.nwbbyt.cn/Article/details/96489.sHtML
- http://www.blog.puhvjy.cn/Article/details/9058690.sHtML
- http://www.blog.nzfnve.cn/Article/details/4009370.sHtML
- http://www.blog.nzfnve.cn/Article/details/5850645.sHtML
- http://www.blog.nzfnve.cn/Article/details/87586.sHtML
- http://www.blog.jnjpgf.cn/Article/details/293676.sHtML
- http://www.blog.nzfnve.cn/Article/details/39720.sHtML
- http://www.blog.nwbbyt.cn/Article/details/860727.sHtML
- http://www.blog.puhvjy.cn/Article/details/08684.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8809075.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0139575.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0585.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5484117.sHtML
- http://www.blog.nzfnve.cn/Article/details/8366699.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9578.sHtML
- http://www.blog.nwbbyt.cn/Article/details/461232.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3518.sHtML
- http://www.blog.nzfnve.cn/Article/details/60082.sHtML
- http://www.blog.puhvjy.cn/Article/details/3690482.sHtML
- http://www.blog.puhvjy.cn/Article/details/0959406.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5295.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2175.sHtML
- http://www.blog.nzfnve.cn/Article/details/837076.sHtML
- http://www.blog.nzfnve.cn/Article/details/8214.sHtML
- http://www.blog.jnjpgf.cn/Article/details/652041.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6306.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8554.sHtML
- http://www.blog.jnjpgf.cn/Article/details/95354.sHtML
- http://www.blog.jnjpgf.cn/Article/details/205557.sHtML
- http://www.blog.puhvjy.cn/Article/details/989591.sHtML
- http://www.blog.nwbbyt.cn/Article/details/62821.sHtML
- http://www.blog.nwbbyt.cn/Article/details/97606.sHtML
- http://www.blog.nzfnve.cn/Article/details/196075.sHtML
- http://www.blog.nzfnve.cn/Article/details/0201.sHtML
- http://www.blog.nwbbyt.cn/Article/details/70712.sHtML
- http://www.blog.nwbbyt.cn/Article/details/48528.sHtML
- http://www.blog.puhvjy.cn/Article/details/1700404.sHtML
- http://www.blog.puhvjy.cn/Article/details/0819.sHtML
- http://www.blog.nzfnve.cn/Article/details/14570.sHtML
- http://www.blog.puhvjy.cn/Article/details/562598.sHtML
- http://www.blog.puhvjy.cn/Article/details/907812.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8893665.sHtML
- http://www.blog.jnjpgf.cn/Article/details/381649.sHtML
- http://www.blog.nzfnve.cn/Article/details/15207.sHtML
- http://www.blog.nzfnve.cn/Article/details/309897.sHtML
- http://www.blog.nzfnve.cn/Article/details/7241.sHtML
- http://www.blog.jnjpgf.cn/Article/details/26926.sHtML
- http://www.blog.jnjpgf.cn/Article/details/67969.sHtML
- http://www.blog.puhvjy.cn/Article/details/5873949.sHtML
- http://www.blog.nzfnve.cn/Article/details/04260.sHtML
- http://www.blog.puhvjy.cn/Article/details/8195141.sHtML
- http://www.blog.puhvjy.cn/Article/details/755637.sHtML
- http://www.blog.puhvjy.cn/Article/details/2115.sHtML
- http://www.blog.nzfnve.cn/Article/details/8460562.sHtML
- http://www.blog.nzfnve.cn/Article/details/3858.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5916272.sHtML
- http://www.blog.puhvjy.cn/Article/details/2387193.sHtML
- http://www.blog.nzfnve.cn/Article/details/94354.sHtML
- http://www.blog.nzfnve.cn/Article/details/034125.sHtML
- http://www.blog.nzfnve.cn/Article/details/4300.sHtML
- http://www.blog.nzfnve.cn/Article/details/6669.sHtML
- http://www.blog.nzfnve.cn/Article/details/9089.sHtML
- http://www.blog.puhvjy.cn/Article/details/3783071.sHtML
- http://www.blog.nzfnve.cn/Article/details/86037.sHtML
- http://www.blog.jnjpgf.cn/Article/details/529015.sHtML
- http://www.blog.puhvjy.cn/Article/details/231558.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3842019.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3464836.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7305.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3158.sHtML
- http://www.blog.puhvjy.cn/Article/details/3621.sHtML
- http://www.blog.puhvjy.cn/Article/details/8877.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0136.sHtML
- http://www.blog.puhvjy.cn/Article/details/8565.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0264.sHtML
- http://www.blog.nzfnve.cn/Article/details/765857.sHtML
- http://www.blog.puhvjy.cn/Article/details/89761.sHtML
- http://www.blog.puhvjy.cn/Article/details/74852.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9188706.sHtML
- http://www.blog.puhvjy.cn/Article/details/6346.sHtML
- http://www.blog.nzfnve.cn/Article/details/283957.sHtML
- http://www.blog.nzfnve.cn/Article/details/70393.sHtML
- http://www.blog.nzfnve.cn/Article/details/99683.sHtML
- http://www.blog.puhvjy.cn/Article/details/2733376.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4570968.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6212920.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4539596.sHtML
- http://www.blog.nzfnve.cn/Article/details/72371.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3121574.sHtML
- http://www.blog.puhvjy.cn/Article/details/776727.sHtML
- http://www.blog.puhvjy.cn/Article/details/835628.sHtML
- http://www.blog.nzfnve.cn/Article/details/23141.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2308.sHtML
- http://www.blog.puhvjy.cn/Article/details/38243.sHtML
- http://www.blog.nzfnve.cn/Article/details/63286.sHtML
- http://www.blog.puhvjy.cn/Article/details/8346.sHtML
- http://www.blog.nzfnve.cn/Article/details/0046.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7015.sHtML
- http://www.blog.puhvjy.cn/Article/details/623612.sHtML
- http://www.blog.jnjpgf.cn/Article/details/553636.sHtML
- http://www.blog.puhvjy.cn/Article/details/2592.sHtML
- http://www.blog.puhvjy.cn/Article/details/955700.sHtML
- http://www.blog.jnjpgf.cn/Article/details/317861.sHtML
- http://www.blog.puhvjy.cn/Article/details/7037.sHtML
- http://www.blog.nwbbyt.cn/Article/details/205372.sHtML
- http://www.blog.nwbbyt.cn/Article/details/898243.sHtML
- http://www.blog.puhvjy.cn/Article/details/73942.sHtML
- http://www.blog.nzfnve.cn/Article/details/096456.sHtML
- http://www.blog.nzfnve.cn/Article/details/9178802.sHtML
- http://www.blog.nzfnve.cn/Article/details/92681.sHtML
- http://www.blog.nzfnve.cn/Article/details/2744.sHtML
- http://www.blog.puhvjy.cn/Article/details/7672859.sHtML
- http://www.blog.puhvjy.cn/Article/details/9818812.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1198.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3416.sHtML
- http://www.blog.nzfnve.cn/Article/details/9278685.sHtML
- http://www.blog.nzfnve.cn/Article/details/6023462.sHtML
- http://www.blog.nzfnve.cn/Article/details/0662775.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8605.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2407.sHtML
- http://www.blog.jnjpgf.cn/Article/details/08418.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2937.sHtML
- http://www.blog.puhvjy.cn/Article/details/7721.sHtML
- http://www.blog.nzfnve.cn/Article/details/4424.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3571.sHtML
- http://www.blog.nzfnve.cn/Article/details/0699231.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9357.sHtML
- http://www.blog.nzfnve.cn/Article/details/879102.sHtML
- http://www.blog.nwbbyt.cn/Article/details/513943.sHtML
- http://www.blog.jnjpgf.cn/Article/details/462595.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7067.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7906.sHtML
- http://www.blog.nwbbyt.cn/Article/details/70799.sHtML
- http://www.blog.nwbbyt.cn/Article/details/55265.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3243.sHtML
- http://www.blog.nzfnve.cn/Article/details/94303.sHtML
- http://www.blog.nzfnve.cn/Article/details/78816.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3290004.sHtML
- http://www.blog.jnjpgf.cn/Article/details/567132.sHtML
- http://www.blog.puhvjy.cn/Article/details/438476.sHtML
- http://www.blog.nzfnve.cn/Article/details/0070954.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3331.sHtML
- http://www.blog.puhvjy.cn/Article/details/0767361.sHtML
- http://www.blog.nzfnve.cn/Article/details/08679.sHtML
- http://www.blog.nzfnve.cn/Article/details/587267.sHtML
- http://www.blog.nzfnve.cn/Article/details/2043695.sHtML
- http://www.blog.nzfnve.cn/Article/details/8979452.sHtML
- http://www.blog.puhvjy.cn/Article/details/4111018.sHtML
- http://www.blog.jnjpgf.cn/Article/details/496215.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1992.sHtML
- http://www.blog.nwbbyt.cn/Article/details/11015.sHtML
- http://www.blog.nwbbyt.cn/Article/details/79368.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5126.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0871610.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9260.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1939492.sHtML
- http://www.blog.nwbbyt.cn/Article/details/04310.sHtML
- http://www.blog.jnjpgf.cn/Article/details/030062.sHtML
- http://www.blog.nwbbyt.cn/Article/details/514531.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4159791.sHtML
- http://www.blog.jnjpgf.cn/Article/details/37427.sHtML
- http://www.blog.nzfnve.cn/Article/details/43460.sHtML
- http://www.blog.puhvjy.cn/Article/details/62216.sHtML
- http://www.blog.jnjpgf.cn/Article/details/66084.sHtML
- http://www.blog.puhvjy.cn/Article/details/153562.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1755927.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3745.sHtML
- http://www.blog.nzfnve.cn/Article/details/76782.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5870.sHtML
- http://www.blog.jnjpgf.cn/Article/details/064382.sHtML
- http://www.blog.puhvjy.cn/Article/details/3879977.sHtML
- http://www.blog.nwbbyt.cn/Article/details/41480.sHtML
- http://www.blog.nwbbyt.cn/Article/details/451394.sHtML
- http://www.blog.puhvjy.cn/Article/details/63352.sHtML
- http://www.blog.jnjpgf.cn/Article/details/469564.sHtML
- http://www.blog.nzfnve.cn/Article/details/3057373.sHtML
- http://www.blog.nzfnve.cn/Article/details/0804.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6477271.sHtML
- http://www.blog.nzfnve.cn/Article/details/020843.sHtML
- http://www.blog.puhvjy.cn/Article/details/39985.sHtML
- http://www.blog.jnjpgf.cn/Article/details/571257.sHtML
- http://www.blog.jnjpgf.cn/Article/details/72512.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7584686.sHtML
- http://www.blog.nwbbyt.cn/Article/details/27728.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5329282.sHtML
- http://www.blog.nwbbyt.cn/Article/details/612604.sHtML
- http://www.blog.puhvjy.cn/Article/details/625652.sHtML
- http://www.blog.puhvjy.cn/Article/details/7295930.sHtML
- http://www.blog.puhvjy.cn/Article/details/08133.sHtML
- http://www.blog.nzfnve.cn/Article/details/4882799.sHtML
- http://www.blog.nzfnve.cn/Article/details/7608.sHtML
- http://www.blog.nzfnve.cn/Article/details/3994537.sHtML
- http://www.blog.jnjpgf.cn/Article/details/06558.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3368256.sHtML
- http://www.blog.puhvjy.cn/Article/details/0493.sHtML
- http://www.blog.nzfnve.cn/Article/details/13684.sHtML
- http://www.blog.nwbbyt.cn/Article/details/016660.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3416.sHtML
- http://www.blog.nzfnve.cn/Article/details/5376.sHtML
- http://www.blog.puhvjy.cn/Article/details/9056139.sHtML
- http://www.blog.nzfnve.cn/Article/details/3419249.sHtML
- http://www.blog.nzfnve.cn/Article/details/4706.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7407.sHtML
- http://www.blog.puhvjy.cn/Article/details/0049587.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8940612.sHtML
- http://www.blog.nwbbyt.cn/Article/details/12050.sHtML
- http://www.blog.puhvjy.cn/Article/details/6079984.sHtML
- http://www.blog.nzfnve.cn/Article/details/5818.sHtML
- http://www.blog.jnjpgf.cn/Article/details/934659.sHtML
- http://www.blog.puhvjy.cn/Article/details/537276.sHtML
- http://www.blog.nzfnve.cn/Article/details/5464.sHtML
- http://www.blog.jnjpgf.cn/Article/details/438234.sHtML
- http://www.blog.jnjpgf.cn/Article/details/33298.sHtML

## 项目结构

```
weblink-hub/
├── src/
│   ├── core/                         # 核心数据模型与业务逻辑
│   │   ├── resource.ts               # 资源条目实体定义与校验
│   │   ├── batch.ts                  # 批次管理逻辑
│   │   └── health-check.ts           # 链接健康检查调度器
│   ├── api/                          # RESTful API 路由层
│   │   ├── resources/                # 资源增删改查接口
│   │   ├── batches/                  # 批次管理接口
│   │   └── search/                   # 全文检索接口
│   ├── cli/                          # 命令行工具入口
│   │   ├── import.ts                 # 批量导入原始 URL 列表
│   │   ├── export.ts                 # 导出为多种格式
│   │   └── scan.ts                   # 手动触发链接扫描
│   ├── db/                           # 数据库迁移与连接
│   │   ├── migrations/               # SQLite 迁移脚本
│   │   └── schema.sql                # 初始表结构
│   ├── web/                          # 管理界面前端资源
│   │   ├── pages/                    # 页面组件
│   │   ├── components/               # 可复用 UI 组件
│   │   └── styles/                   # 全局样式与主题变量
│   └── utils/                        # 通用工具函数
│       ├── url-parser.ts             # URL 规范化与解析
│       └── logger.ts                 # 结构化日志输出
├── tests/                            # 单元测试与集成测试
│   ├── unit/                         # 核心模块单元测试
│   └── integration/                  # API 端到端测试
├── docs/                             # 完整文档源文件
├── config/                           # 环境配置文件
│   ├── default.json                  # 默认配置
│   └── production.json               # 生产环境覆盖
├── scripts/                          # 辅助开发脚本
│   ├── seed-demo.js                  # 填充演示数据
│   └── validate-links.js             # 批量验证链接格式
├── package.json                      # 项目清单与依赖声明
├── tsconfig.json                     # TypeScript 编译配置
├── .eslintrc.js                      # 代码风格检查规则
└── README.md                         # 项目说明文档
```

## 贡献指南

欢迎通过提交 Issue 或 Pull Request 参与本项目开发。请遵循以下步骤：

1. 在 GitHub 仓库的 Issue 列表中查找或新建一个与您要处理的问题相关的议题，获得社区反馈后再开始编码。

2. 从主分支检出新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。

3. 提交代码前运行 `npm run lint` 与 `npm run test` 确保代码风格与测试用例全部通过。新增功能需附带对应的单元测试。

4. 提交 Pull Request 时请参照项目中的 PR 模板填写变更摘要、测试覆盖范围以及相关 Issue 编号。

5. 资源列表的增删改请通过 `src/cli/import.ts` 或管理界面进行，不要直接编辑 Markdown 文件中的资源列表章节，以避免格式冲突。

## 常见问题

**问：为什么资源列表中有些 URL 使用的是 HTTP 协议而不是 HTTPS？**

答：本项目规定所有资源条目必须保留用户提供的原始 URL 字符串，不做任何协议升级或降级处理。这是为了保证链接的可追溯性，避免因自动改写导致源站无法访问或重定向链断裂。用户可在导入后通过链接健康检查功能获知各资源的实际可达状态，并手动决定是否更新为 HTTPS 版本。

**问：如何验证本批次 250 个链接是否全部有效？**

答：可使用内置的 `npm run scan` 命令，该命令会并发检查所有资源的状态码并生成健康报告。对于返回 4xx 或 5xx 的链接，报告会标注具体错误码，您可根据报告结果决定是否保留、更新或移除对应条目。

**问：能否将资源列表直接嵌入到其他项目的 README 中？**

答：可以。本项目支持通过 CLI 命令 `npm run export -- --format=markdown` 将当前所有资源导出为标准 Markdown 列表，您可直接复制该输出内容。但请注意，导出的列表会包含所有批次，若只需特定批次，请使用 `--batch=13` 参数过滤。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
