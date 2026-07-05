# MapBlog 外链资源聚合系统

MapBlog 是一个面向技术内容创作者与开发者的外链资源聚合与导航平台，专注于将分散在多个博客子域名下的技术文章、教程笔记与工程实践文档进行统一收录、分类索引与快速检索。项目目标用户包括全栈工程师、运维工程师、技术博主以及开源项目维护者，帮助他们从海量的历史博文链接中快速定位所需的技术参考资料，避免重复造轮子，提升信息检索效率。

本项目并非一个传统的博客前端展示系统，而是一个外链元数据管理工具集。它提供了一套标准化的链接采集、标签分类、有效性检查与批量导出流程，特别适用于维护超过 200 条以上技术外链的中大型知识库。通过 MapBlog，你可以将原本散落在 map.blog.jnjpgf.cn、map.blog.nzfnve.cn、map.blog.puhvjy.cn、map.blog.nwbbyt.cn 等子域名下的技术文章链接，整合为一个可检索、可审计、可分享的结构化资源清单。

## 功能概览

**批量链接导入**：支持从 CSV、JSON 或纯文本列表中批量导入技术外链，自动解析 URL 中的域名、路径与文件扩展名。

**智能去重与冲突检测**：基于 URL 全文与文章标题的相似度算法，自动标记重复或高度相似的链接，避免资源冗余。

**域名分组索引**：按照链接来源域名（如 jnjpgf.cn、nzfnve.cn、puhvjy.cn、nwbbyt.cn）自动建立分组索引，便于按站点浏览。

**链接可达性巡检**：内置 HTTP 状态码检查器，可定时巡检所有链接的有效性，返回 404 或超时的链接将被标记为失效并移至待修复区。

**标签与全文检索**：为每条链接生成基于 URL 路径语义的自动标签（如 Article/details/xxx），并支持标题与路径关键词的模糊搜索。

**结构化导出**：支持将资源列表导出为 Markdown 表格、HTML 目录页或纯文本清单，方便嵌入项目文档或 Wiki。

**历史快照对比**：每次导入或更新时自动保存资源快照，支持对比两个时间点之间的链接增删变化，便于审计。

## 应用场景

技术博客迁移与整合：当多个技术子博客需要合并或迁移时，MapBlog 可快速梳理所有历史文章的外链，生成完整的迁移清单，避免遗漏重要内容。

项目文档外链审计：开源项目维护者可使用 MapBlog 定期检查 README、Wiki 中引用的所有外部链接是否仍然可访问，确保文档质量。

技术周报素材收集：技术编辑或社区运营人员可将分散在多个博客站点的优质文章链接统一收录，按主题分类后生成每周技术资源推荐列表。

个人知识库外链管理：工程师可将自己在多个技术博客上收藏或发布的文章链接集中管理，配合标签与检索功能，快速回忆与引用过往技术决策。

## 快速开始

以下命令将在本地克隆 MapBlog 仓库，安装依赖并启动开发服务。

```bash
git clone https://github.com/mapblog/mapblog-core.git
cd mapblog-core
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

访问本地 8000 端口即可进入外链管理仪表盘。首次启动时，系统会自动创建默认的管理员账户（admin / admin123），请登录后立即修改密码。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，低于 3.9 会导致异步 IO 模块异常 |
| Django | 4.2 LTS | Web 管理后台与 ORM 基础框架 |
| SQLite | 3.35 及以上 | 默认内置数据库，用于存储链接索引与元数据 |
| requests | 2.28 及以上 | 用于发送 HTTP 请求进行链接可达性检查 |
| beautifulsoup4 | 4.11 及以上 | 用于解析部分链接对应的页面标题与摘要信息 |
| tqdm | 4.64 及以上 | 批量导入与巡检任务中的进度条显示支持 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/import.md | 如何批量导入外链、支持哪些格式、去重规则是什么 |
| 用户手册 | /docs/user-guide/health-check.md | 如何配置定时巡检、如何查看失效链接报告 |
| 开发者指南 | /docs/dev/api-endpoints.md | 后端提供了哪些 REST API 用于外部系统集成 |
| 开发者指南 | /docs/dev/custom-tagging.md | 如何编写自定义标签生成规则以适配不同域名路径结构 |
| 运维手册 | /docs/ops/deployment.md | 生产环境部署方案（Gunicorn + Nginx + PostgreSQL） |
| 运维手册 | /docs/ops/migration.md | 从旧版 SQLite 迁移至 PostgreSQL 的完整步骤 |

## 资源列表

- http://map.blog.jnjpgf.cn/Article/details/67652.sHtML
- http://map.blog.jnjpgf.cn/Article/details/29929.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7213.sHtML
- http://map.blog.nzfnve.cn/Article/details/64490.sHtML
- http://map.blog.puhvjy.cn/Article/details/56991.sHtML
- http://map.blog.nzfnve.cn/Article/details/56346.sHtML
- http://map.blog.nwbbyt.cn/Article/details/032995.sHtML
- http://map.blog.nzfnve.cn/Article/details/548136.sHtML
- http://map.blog.puhvjy.cn/Article/details/4626461.sHtML
- http://map.blog.puhvjy.cn/Article/details/4700.sHtML
- http://map.blog.nzfnve.cn/Article/details/7929.sHtML
- http://map.blog.nzfnve.cn/Article/details/970983.sHtML
- http://map.blog.nwbbyt.cn/Article/details/95791.sHtML
- http://map.blog.jnjpgf.cn/Article/details/495991.sHtML
- http://map.blog.jnjpgf.cn/Article/details/630445.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2228.sHtML
- http://map.blog.nwbbyt.cn/Article/details/25602.sHtML
- http://map.blog.nwbbyt.cn/Article/details/317779.sHtML
- http://map.blog.nzfnve.cn/Article/details/31367.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0053.sHtML
- http://map.blog.jnjpgf.cn/Article/details/802437.sHtML
- http://map.blog.nwbbyt.cn/Article/details/190624.sHtML
- http://map.blog.nzfnve.cn/Article/details/135044.sHtML
- http://map.blog.jnjpgf.cn/Article/details/34432.sHtML
- http://map.blog.puhvjy.cn/Article/details/0744.sHtML
- http://map.blog.puhvjy.cn/Article/details/24031.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2929.sHtML
- http://map.blog.puhvjy.cn/Article/details/52406.sHtML
- http://map.blog.nzfnve.cn/Article/details/19476.sHtML
- http://map.blog.puhvjy.cn/Article/details/2569765.sHtML
- http://map.blog.jnjpgf.cn/Article/details/121292.sHtML
- http://map.blog.nzfnve.cn/Article/details/8573.sHtML
- http://map.blog.nwbbyt.cn/Article/details/67311.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7629771.sHtML
- http://map.blog.puhvjy.cn/Article/details/840951.sHtML
- http://map.blog.puhvjy.cn/Article/details/3444564.sHtML
- http://map.blog.puhvjy.cn/Article/details/48520.sHtML
- http://map.blog.nwbbyt.cn/Article/details/96489.sHtML
- http://map.blog.puhvjy.cn/Article/details/9058690.sHtML
- http://map.blog.nzfnve.cn/Article/details/4009370.sHtML
- http://map.blog.nzfnve.cn/Article/details/5850645.sHtML
- http://map.blog.nzfnve.cn/Article/details/87586.sHtML
- http://map.blog.jnjpgf.cn/Article/details/293676.sHtML
- http://map.blog.nzfnve.cn/Article/details/39720.sHtML
- http://map.blog.nwbbyt.cn/Article/details/860727.sHtML
- http://map.blog.puhvjy.cn/Article/details/08684.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8809075.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0139575.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0585.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5484117.sHtML
- http://map.blog.nzfnve.cn/Article/details/8366699.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9578.sHtML
- http://map.blog.nwbbyt.cn/Article/details/461232.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3518.sHtML
- http://map.blog.nzfnve.cn/Article/details/60082.sHtML
- http://map.blog.puhvjy.cn/Article/details/3690482.sHtML
- http://map.blog.puhvjy.cn/Article/details/0959406.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5295.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2175.sHtML
- http://map.blog.nzfnve.cn/Article/details/837076.sHtML
- http://map.blog.nzfnve.cn/Article/details/8214.sHtML
- http://map.blog.jnjpgf.cn/Article/details/652041.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6306.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8554.sHtML
- http://map.blog.jnjpgf.cn/Article/details/95354.sHtML
- http://map.blog.jnjpgf.cn/Article/details/205557.sHtML
- http://map.blog.puhvjy.cn/Article/details/989591.sHtML
- http://map.blog.nwbbyt.cn/Article/details/62821.sHtML
- http://map.blog.nwbbyt.cn/Article/details/97606.sHtML
- http://map.blog.nzfnve.cn/Article/details/196075.sHtML
- http://map.blog.nzfnve.cn/Article/details/0201.sHtML
- http://map.blog.nwbbyt.cn/Article/details/70712.sHtML
- http://map.blog.nwbbyt.cn/Article/details/48528.sHtML
- http://map.blog.puhvjy.cn/Article/details/1700404.sHtML
- http://map.blog.puhvjy.cn/Article/details/0819.sHtML
- http://map.blog.nzfnve.cn/Article/details/14570.sHtML
- http://map.blog.puhvjy.cn/Article/details/562598.sHtML
- http://map.blog.puhvjy.cn/Article/details/907812.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8893665.sHtML
- http://map.blog.jnjpgf.cn/Article/details/381649.sHtML
- http://map.blog.nzfnve.cn/Article/details/15207.sHtML
- http://map.blog.nzfnve.cn/Article/details/309897.sHtML
- http://map.blog.nzfnve.cn/Article/details/7241.sHtML
- http://map.blog.jnjpgf.cn/Article/details/26926.sHtML
- http://map.blog.jnjpgf.cn/Article/details/67969.sHtML
- http://map.blog.puhvjy.cn/Article/details/5873949.sHtML
- http://map.blog.nzfnve.cn/Article/details/04260.sHtML
- http://map.blog.puhvjy.cn/Article/details/8195141.sHtML
- http://map.blog.puhvjy.cn/Article/details/755637.sHtML
- http://map.blog.puhvjy.cn/Article/details/2115.sHtML
- http://map.blog.nzfnve.cn/Article/details/8460562.sHtML
- http://map.blog.nzfnve.cn/Article/details/3858.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5916272.sHtML
- http://map.blog.puhvjy.cn/Article/details/2387193.sHtML
- http://map.blog.nzfnve.cn/Article/details/94354.sHtML
- http://map.blog.nzfnve.cn/Article/details/034125.sHtML
- http://map.blog.nzfnve.cn/Article/details/4300.sHtML
- http://map.blog.nzfnve.cn/Article/details/6669.sHtML
- http://map.blog.nzfnve.cn/Article/details/9089.sHtML
- http://map.blog.puhvjy.cn/Article/details/3783071.sHtML
- http://map.blog.nzfnve.cn/Article/details/86037.sHtML
- http://map.blog.jnjpgf.cn/Article/details/529015.sHtML
- http://map.blog.puhvjy.cn/Article/details/231558.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3842019.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3464836.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7305.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3158.sHtML
- http://map.blog.puhvjy.cn/Article/details/3621.sHtML
- http://map.blog.puhvjy.cn/Article/details/8877.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0136.sHtML
- http://map.blog.puhvjy.cn/Article/details/8565.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0264.sHtML
- http://map.blog.nzfnve.cn/Article/details/765857.sHtML
- http://map.blog.puhvjy.cn/Article/details/89761.sHtML
- http://map.blog.puhvjy.cn/Article/details/74852.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9188706.sHtML
- http://map.blog.puhvjy.cn/Article/details/6346.sHtML
- http://map.blog.nzfnve.cn/Article/details/283957.sHtML
- http://map.blog.nzfnve.cn/Article/details/70393.sHtML
- http://map.blog.nzfnve.cn/Article/details/99683.sHtML
- http://map.blog.puhvjy.cn/Article/details/2733376.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4570968.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6212920.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4539596.sHtML
- http://map.blog.nzfnve.cn/Article/details/72371.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3121574.sHtML
- http://map.blog.puhvjy.cn/Article/details/776727.sHtML
- http://map.blog.puhvjy.cn/Article/details/835628.sHtML
- http://map.blog.nzfnve.cn/Article/details/23141.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2308.sHtML
- http://map.blog.puhvjy.cn/Article/details/38243.sHtML
- http://map.blog.nzfnve.cn/Article/details/63286.sHtML
- http://map.blog.puhvjy.cn/Article/details/8346.sHtML
- http://map.blog.nzfnve.cn/Article/details/0046.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7015.sHtML
- http://map.blog.puhvjy.cn/Article/details/623612.sHtML
- http://map.blog.jnjpgf.cn/Article/details/553636.sHtML
- http://map.blog.puhvjy.cn/Article/details/2592.sHtML
- http://map.blog.puhvjy.cn/Article/details/955700.sHtML
- http://map.blog.jnjpgf.cn/Article/details/317861.sHtML
- http://map.blog.puhvjy.cn/Article/details/7037.sHtML
- http://map.blog.nwbbyt.cn/Article/details/205372.sHtML
- http://map.blog.nwbbyt.cn/Article/details/898243.sHtML
- http://map.blog.puhvjy.cn/Article/details/73942.sHtML
- http://map.blog.nzfnve.cn/Article/details/096456.sHtML
- http://map.blog.nzfnve.cn/Article/details/9178802.sHtML
- http://map.blog.nzfnve.cn/Article/details/92681.sHtML
- http://map.blog.nzfnve.cn/Article/details/2744.sHtML
- http://map.blog.puhvjy.cn/Article/details/7672859.sHtML
- http://map.blog.puhvjy.cn/Article/details/9818812.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1198.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3416.sHtML
- http://map.blog.nzfnve.cn/Article/details/9278685.sHtML
- http://map.blog.nzfnve.cn/Article/details/6023462.sHtML
- http://map.blog.nzfnve.cn/Article/details/0662775.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8605.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2407.sHtML
- http://map.blog.jnjpgf.cn/Article/details/08418.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2937.sHtML
- http://map.blog.puhvjy.cn/Article/details/7721.sHtML
- http://map.blog.nzfnve.cn/Article/details/4424.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3571.sHtML
- http://map.blog.nzfnve.cn/Article/details/0699231.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9357.sHtML
- http://map.blog.nzfnve.cn/Article/details/879102.sHtML
- http://map.blog.nwbbyt.cn/Article/details/513943.sHtML
- http://map.blog.jnjpgf.cn/Article/details/462595.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7067.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7906.sHtML
- http://map.blog.nwbbyt.cn/Article/details/70799.sHtML
- http://map.blog.nwbbyt.cn/Article/details/55265.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3243.sHtML
- http://map.blog.nzfnve.cn/Article/details/94303.sHtML
- http://map.blog.nzfnve.cn/Article/details/78816.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3290004.sHtML
- http://map.blog.jnjpgf.cn/Article/details/567132.sHtML
- http://map.blog.puhvjy.cn/Article/details/438476.sHtML
- http://map.blog.nzfnve.cn/Article/details/0070954.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3331.sHtML
- http://map.blog.puhvjy.cn/Article/details/0767361.sHtML
- http://map.blog.nzfnve.cn/Article/details/08679.sHtML
- http://map.blog.nzfnve.cn/Article/details/587267.sHtML
- http://map.blog.nzfnve.cn/Article/details/2043695.sHtML
- http://map.blog.nzfnve.cn/Article/details/8979452.sHtML
- http://map.blog.puhvjy.cn/Article/details/4111018.sHtML
- http://map.blog.jnjpgf.cn/Article/details/496215.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1992.sHtML
- http://map.blog.nwbbyt.cn/Article/details/11015.sHtML
- http://map.blog.nwbbyt.cn/Article/details/79368.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5126.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0871610.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9260.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1939492.sHtML
- http://map.blog.nwbbyt.cn/Article/details/04310.sHtML
- http://map.blog.jnjpgf.cn/Article/details/030062.sHtML
- http://map.blog.nwbbyt.cn/Article/details/514531.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4159791.sHtML
- http://map.blog.jnjpgf.cn/Article/details/37427.sHtML
- http://map.blog.nzfnve.cn/Article/details/43460.sHtML
- http://map.blog.puhvjy.cn/Article/details/62216.sHtML
- http://map.blog.jnjpgf.cn/Article/details/66084.sHtML
- http://map.blog.puhvjy.cn/Article/details/153562.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1755927.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3745.sHtML
- http://map.blog.nzfnve.cn/Article/details/76782.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5870.sHtML
- http://map.blog.jnjpgf.cn/Article/details/064382.sHtML
- http://map.blog.puhvjy.cn/Article/details/3879977.sHtML
- http://map.blog.nwbbyt.cn/Article/details/41480.sHtML
- http://map.blog.nwbbyt.cn/Article/details/451394.sHtML
- http://map.blog.puhvjy.cn/Article/details/63352.sHtML
- http://map.blog.jnjpgf.cn/Article/details/469564.sHtML
- http://map.blog.nzfnve.cn/Article/details/3057373.sHtML
- http://map.blog.nzfnve.cn/Article/details/0804.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6477271.sHtML
- http://map.blog.nzfnve.cn/Article/details/020843.sHtML
- http://map.blog.puhvjy.cn/Article/details/39985.sHtML
- http://map.blog.jnjpgf.cn/Article/details/571257.sHtML
- http://map.blog.jnjpgf.cn/Article/details/72512.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7584686.sHtML
- http://map.blog.nwbbyt.cn/Article/details/27728.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5329282.sHtML
- http://map.blog.nwbbyt.cn/Article/details/612604.sHtML
- http://map.blog.puhvjy.cn/Article/details/625652.sHtML
- http://map.blog.puhvjy.cn/Article/details/7295930.sHtML
- http://map.blog.puhvjy.cn/Article/details/08133.sHtML
- http://map.blog.nzfnve.cn/Article/details/4882799.sHtML
- http://map.blog.nzfnve.cn/Article/details/7608.sHtML
- http://map.blog.nzfnve.cn/Article/details/3994537.sHtML
- http://map.blog.jnjpgf.cn/Article/details/06558.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3368256.sHtML
- http://map.blog.puhvjy.cn/Article/details/0493.sHtML
- http://map.blog.nzfnve.cn/Article/details/13684.sHtML
- http://map.blog.nwbbyt.cn/Article/details/016660.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3416.sHtML
- http://map.blog.nzfnve.cn/Article/details/5376.sHtML
- http://map.blog.puhvjy.cn/Article/details/9056139.sHtML
- http://map.blog.nzfnve.cn/Article/details/3419249.sHtML
- http://map.blog.nzfnve.cn/Article/details/4706.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7407.sHtML
- http://map.blog.puhvjy.cn/Article/details/0049587.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8940612.sHtML
- http://map.blog.nwbbyt.cn/Article/details/12050.sHtML
- http://map.blog.puhvjy.cn/Article/details/6079984.sHtML
- http://map.blog.nzfnve.cn/Article/details/5818.sHtML
- http://map.blog.jnjpgf.cn/Article/details/934659.sHtML
- http://map.blog.puhvjy.cn/Article/details/537276.sHtML
- http://map.blog.nzfnve.cn/Article/details/5464.sHtML
- http://map.blog.jnjpgf.cn/Article/details/438234.sHtML
- http://map.blog.jnjpgf.cn/Article/details/33298.sHtML

## 项目结构

```
mapblog-core/
├── manage.py                 # Django 项目管理入口
├── requirements.txt          # Python 依赖声明文件
├── .env.example              # 环境变量配置模板（含数据库连接、巡检间隔）
├── src/
│   ├── core/                 # 核心配置模块
│   │   ├── settings/         # 多环境配置（base, dev, prod）
│   │   ├── urls.py           # 主路由注册
│   │   └── wsgi.py           # 生产入口
│   ├── apps/                 # 所有功能应用
│   │   ├── links/            # 链接管理主应用（模型、视图、序列化器）
│   │   │   ├── models.py     # Link, DomainGroup, Tag 数据模型
│   │   │   ├── importer.py   # CSV/JSON/纯文本导入器
│   │   │   ├── checker.py    # HTTP 状态码巡检器
│   │   │   └── filters.py    # 去重与冲突检测逻辑
│   │   ├── api/              # RESTful API 应用
│   │   │   ├── views.py      # 资源列表、巡检、导出接口
│   │   │   └── serializers.py# 链接与分组序列化器
│   │   └── dashboard/        # 管理后台前端应用（Django 模板）
│   │       ├── templates/    # HTML 页面模板
│   │       └── static/       # CSS/JS 静态资源
│   ├── libs/                 # 通用工具库
│   │   ├── http_client.py    # 带重试与超时控制的 HTTP 客户端封装
│   │   └── url_parser.py     # URL 域名、路径、参数解析工具
│   └── scripts/              # 运维与数据迁移脚本
│       ├── batch_import.py   # 批量导入命令行脚本
│       └── health_report.py  # 生成链接健康度报告
├── tests/                    # 单元测试与集成测试
│   ├── test_importer.py
│   └── test_checker.py
├── docs/                     # 完整文档目录（用户手册、开发指南、运维手册）
└── data/                     # 示例数据与导入导出临时目录
    └── samples/
        └── example_links.csv # 示例外链清单
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆至本地开发环境。确保你的 Python 版本为 3.9 或以上，并已安装 virtualenv 或 conda。

2. 创建新的功能分支（如 feature/add-custom-tag-rule），所有开发工作应在独立分支上进行，禁止直接向 main 分支提交。

3. 编写或修改代码后，请运行 tests 目录下的全部单元测试，确保不影响现有功能。新增功能需附带对应的测试用例。

4. 更新 docs 目录下的相关文档，特别是用户手册中涉及的操作步骤或开发者指南中的 API 变更说明。

5. 提交 Pull Request 时请详细描述改动内容、测试覆盖情况以及是否涉及数据库迁移。PR 需至少一名项目维护者审核通过后方可合并。

## 常见问题

**Q: 批量导入时提示 "URL 格式不合法"，但我的链接明明可以在浏览器中打开。**
A: 请检查 URL 中是否包含未转义的特殊字符（如中文空格、尖括号等）。MapBlog 的 URL 解析器严格遵循 RFC 3986 标准，建议对所有非 ASCII 字符进行百分号编码。另外，请注意本系统默认仅支持 http 和 https 协议，不支持 ftp 或 file 协议。

**Q: 链接巡检任务执行非常缓慢，如何处理？**
A: 默认巡检器使用单线程顺序请求，对于超过 200 条链接的列表，建议在 settings 中启用并发巡检模式（设置 `LINK_CHECK_CONCURRENCY = 10`）。同时，请确保网络环境稳定，部分境外域名可能需要配置代理或增加超时时间（`LINK_CHECK_TIMEOUT = 15` 秒）。

**Q: 我能否将 MapBlog 作为静态站点生成器来使用，直接输出一个包含所有链接的 HTML 页面？**
A: 可以。项目提供了 `export_static.py` 脚本（位于 src/scripts/ 目录），该脚本会读取数据库中的所有链接，并按域名分组生成一个可直接部署的静态 HTML 目录页。你可以在生产环境中将此页面作为团队内部的技术资源导航入口。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
