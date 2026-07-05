# BlogLink Archive

一个面向技术内容聚合与历史文章回溯的轻量化外链管理工具。BlogLink Archive 定位于帮助开发者、技术博主与内容运营人员快速检索、归档和引用分散在多个博客站点上的历史文章，解决因站点迁移、链接失效或分类混乱导致的内容查找困难问题。该项目不提供爬虫或批量下载功能，仅作为结构化索引与本地化预览辅助工具，适用于小规模技术博客的链接整理与知识库构建。

## 功能概览

- **多源链接导入与去重**：支持从文本文件、剪贴板或直接录入方式批量导入文章 URL，自动识别重复条目并生成唯一标识。
- **自定义标签与分类体系**：允许用户为每一条链接添加自由标签（如“Python”、“架构”、“运维”），并支持多级分类树构建。
- **全文元数据提取**：通过可配置的解析器，从目标页面提取标题、发布时间、作者、简介等元信息，并以结构化字段存储。
- **模糊搜索与过滤**：基于标题、标签、域名、时间范围等多维度组合过滤，支持大小写不敏感的模糊匹配。
- **本地快照预览**：在配置本地缓存后，可存储文章的部分文本摘要或结构化大纲，便于离线浏览关键信息。
- **导入导出标准化**：支持 JSON、CSV、Markdown 表格三种导出格式，便于与其他知识管理工具或静态站点生成器对接。
- **链接可用性检查**：内置简单的 HTTP 状态检测功能，可标记失效链接并生成报告，辅助清理死链。

## 应用场景

- **技术博客归档整理**：当个人技术博客经过多次迁移或改版后，历史文章的原始链接可能分散在多个二级域名或子目录下。BlogLink Archive 可将这些链接统一录入，并通过标签和分类重建文章索引，方便后续检索与引用。
- **团队知识库外链管理**：在团队内部 Wiki 或文档平台中，经常需要引用外部技术资源。使用本工具可以对所有外链进行集中登记、定期检查可用性，并记录引用上下文，避免资源丢失后难以追溯。
- **技术资讯周报素材收集**：内容编辑或技术运营人员每周需要从大量博客中筛选优质文章。通过本工具的批量导入和标签过滤功能，可以快速构建周报候选链接池，并导出为 Markdown 列表直接用于稿件编写。
- **个人阅读列表与稍后读整理**：开发者日常浏览技术社区时会积累大量待读文章。本工具可作为轻量级“稍后读”索引，记录来源、添加个人备注，并按主题或优先级排序，取代零散的浏览器书签。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-username/bloglink-archive.git

# 进入项目目录
cd bloglink-archive

# 安装依赖（使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化本地数据库
python manage.py initdb

# 导入示例链接列表（将 URL 列表放入 data/links.txt 后执行）
python manage.py import --file data/links.txt --tags example

# 启动本地 Web 预览服务（默认端口 8000）
python manage.py serve --port 8000
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 或 3.11 长期支持版 |
| SQLite | 3.28 及以上 | 内置轻量级数据库，无需额外安装，用于存储链接索引与元数据 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装项目依赖库 |
| requests | 2.28.0 | 用于发送 HTTP 请求以获取页面元数据和检测链接状态 |
| beautifulsoup4 | 4.11.0 | HTML 解析库，用于从目标页面提取标题和摘要信息 |
| lxml | 4.9.0 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 的解析后端 |
| click | 8.1.0 | 命令行交互框架，提供子命令解析与参数校验能力 |
| rich | 13.0.0 | 终端美化输出，用于显示进度条、表格和彩色日志 |
| pytest | 7.0.0 | 单元测试框架，仅在开发环境中需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/import.md | 如何批量导入链接？支持哪些输入格式？如何处理重复项？ |
| 用户手册 | docs/user/search.md | 如何进行多条件组合搜索？搜索语法规则是什么？ |
| 用户手册 | docs/user/export.md | 导出数据有哪些格式可选？每种格式的适用场景是什么？ |
| 开发者指南 | docs/dev/api.md | 核心数据模型和解析器接口如何扩展？如何自定义元数据提取逻辑？ |
| 开发者指南 | docs/dev/testing.md | 如何运行单元测试？测试覆盖率要求是多少？如何添加新的测试用例？ |
| 运维参考 | docs/ops/deployment.md | 如何将服务部署到生产环境？如何处理数据库备份与迁移？ |
| 运维参考 | docs/ops/monitoring.md | 如何监控链接可用性检查任务的执行状态？日志如何配置与轮转？ |

## 资源列表

- http://h5.blog.jnjpgf.cn/Article/details/67652.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/29929.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7213.sHtML
- http://h5.blog.nzfnve.cn/Article/details/64490.sHtML
- http://h5.blog.puhvjy.cn/Article/details/56991.sHtML
- http://h5.blog.nzfnve.cn/Article/details/56346.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/032995.sHtML
- http://h5.blog.nzfnve.cn/Article/details/548136.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4626461.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4700.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7929.sHtML
- http://h5.blog.nzfnve.cn/Article/details/970983.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/95791.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/495991.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/630445.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2228.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/25602.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/317779.sHtML
- http://h5.blog.nzfnve.cn/Article/details/31367.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0053.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/802437.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/190624.sHtML
- http://h5.blog.nzfnve.cn/Article/details/135044.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/34432.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0744.sHtML
- http://h5.blog.puhvjy.cn/Article/details/24031.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2929.sHtML
- http://h5.blog.puhvjy.cn/Article/details/52406.sHtML
- http://h5.blog.nzfnve.cn/Article/details/19476.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2569765.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/121292.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8573.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/67311.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7629771.sHtML
- http://h5.blog.puhvjy.cn/Article/details/840951.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3444564.sHtML
- http://h5.blog.puhvjy.cn/Article/details/48520.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/96489.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9058690.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4009370.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5850645.sHtML
- http://h5.blog.nzfnve.cn/Article/details/87586.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/293676.sHtML
- http://h5.blog.nzfnve.cn/Article/details/39720.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/860727.sHtML
- http://h5.blog.puhvjy.cn/Article/details/08684.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8809075.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0139575.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0585.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5484117.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8366699.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9578.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/461232.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3518.sHtML
- http://h5.blog.nzfnve.cn/Article/details/60082.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3690482.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0959406.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5295.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2175.sHtML
- http://h5.blog.nzfnve.cn/Article/details/837076.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8214.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/652041.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6306.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8554.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/95354.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/205557.sHtML
- http://h5.blog.puhvjy.cn/Article/details/989591.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/62821.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/97606.sHtML
- http://h5.blog.nzfnve.cn/Article/details/196075.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0201.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/70712.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/48528.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1700404.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0819.sHtML
- http://h5.blog.nzfnve.cn/Article/details/14570.sHtML
- http://h5.blog.puhvjy.cn/Article/details/562598.sHtML
- http://h5.blog.puhvjy.cn/Article/details/907812.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8893665.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/381649.sHtML
- http://h5.blog.nzfnve.cn/Article/details/15207.sHtML
- http://h5.blog.nzfnve.cn/Article/details/309897.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7241.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/26926.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/67969.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5873949.sHtML
- http://h5.blog.nzfnve.cn/Article/details/04260.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8195141.sHtML
- http://h5.blog.puhvjy.cn/Article/details/755637.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2115.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8460562.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3858.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5916272.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2387193.sHtML
- http://h5.blog.nzfnve.cn/Article/details/94354.sHtML
- http://h5.blog.nzfnve.cn/Article/details/034125.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4300.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6669.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9089.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3783071.sHtML
- http://h5.blog.nzfnve.cn/Article/details/86037.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/529015.sHtML
- http://h5.blog.puhvjy.cn/Article/details/231558.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3842019.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3464836.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7305.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3158.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3621.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8877.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0136.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8565.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0264.sHtML
- http://h5.blog.nzfnve.cn/Article/details/765857.sHtML
- http://h5.blog.puhvjy.cn/Article/details/89761.sHtML
- http://h5.blog.puhvjy.cn/Article/details/74852.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9188706.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6346.sHtML
- http://h5.blog.nzfnve.cn/Article/details/283957.sHtML
- http://h5.blog.nzfnve.cn/Article/details/70393.sHtML
- http://h5.blog.nzfnve.cn/Article/details/99683.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2733376.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4570968.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6212920.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4539596.sHtML
- http://h5.blog.nzfnve.cn/Article/details/72371.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3121574.sHtML
- http://h5.blog.puhvjy.cn/Article/details/776727.sHtML
- http://h5.blog.puhvjy.cn/Article/details/835628.sHtML
- http://h5.blog.nzfnve.cn/Article/details/23141.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2308.sHtML
- http://h5.blog.puhvjy.cn/Article/details/38243.sHtML
- http://h5.blog.nzfnve.cn/Article/details/63286.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8346.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0046.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7015.sHtML
- http://h5.blog.puhvjy.cn/Article/details/623612.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/553636.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2592.sHtML
- http://h5.blog.puhvjy.cn/Article/details/955700.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/317861.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7037.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/205372.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/898243.sHtML
- http://h5.blog.puhvjy.cn/Article/details/73942.sHtML
- http://h5.blog.nzfnve.cn/Article/details/096456.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9178802.sHtML
- http://h5.blog.nzfnve.cn/Article/details/92681.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2744.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7672859.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9818812.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1198.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3416.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9278685.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6023462.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0662775.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8605.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2407.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/08418.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2937.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7721.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4424.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3571.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0699231.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9357.sHtML
- http://h5.blog.nzfnve.cn/Article/details/879102.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/513943.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/462595.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7067.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7906.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/70799.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/55265.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3243.sHtML
- http://h5.blog.nzfnve.cn/Article/details/94303.sHtML
- http://h5.blog.nzfnve.cn/Article/details/78816.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3290004.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/567132.sHtML
- http://h5.blog.puhvjy.cn/Article/details/438476.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0070954.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3331.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0767361.sHtML
- http://h5.blog.nzfnve.cn/Article/details/08679.sHtML
- http://h5.blog.nzfnve.cn/Article/details/587267.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2043695.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8979452.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4111018.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/496215.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1992.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/11015.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/79368.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5126.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0871610.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9260.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1939492.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/04310.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/030062.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/514531.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4159791.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/37427.sHtML
- http://h5.blog.nzfnve.cn/Article/details/43460.sHtML
- http://h5.blog.puhvjy.cn/Article/details/62216.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/66084.sHtML
- http://h5.blog.puhvjy.cn/Article/details/153562.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1755927.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3745.sHtML
- http://h5.blog.nzfnve.cn/Article/details/76782.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5870.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/064382.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3879977.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/41480.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/451394.sHtML
- http://h5.blog.puhvjy.cn/Article/details/63352.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/469564.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3057373.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0804.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6477271.sHtML
- http://h5.blog.nzfnve.cn/Article/details/020843.sHtML
- http://h5.blog.puhvjy.cn/Article/details/39985.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/571257.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/72512.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7584686.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/27728.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5329282.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/612604.sHtML
- http://h5.blog.puhvjy.cn/Article/details/625652.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7295930.sHtML
- http://h5.blog.puhvjy.cn/Article/details/08133.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4882799.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7608.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3994537.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/06558.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3368256.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0493.sHtML
- http://h5.blog.nzfnve.cn/Article/details/13684.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/016660.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3416.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5376.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9056139.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3419249.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4706.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7407.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0049587.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8940612.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/12050.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6079984.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5818.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/934659.sHtML
- http://h5.blog.puhvjy.cn/Article/details/537276.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5464.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/438234.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/33298.sHtML

## 项目结构

```
bloglink-archive/
├── README.md                     # 项目概述与快速入门
├── LICENSE                       # MIT 许可证文件
├── requirements.txt              # 生产环境依赖列表
├── requirements-dev.txt          # 开发与测试额外依赖
├── pyproject.toml                # 项目元数据与构建配置
│
├── src/                          # 核心源代码目录
│   ├── __init__.py               # 包入口
│   ├── cli/                      # 命令行接口子模块
│   │   ├── __init__.py
│   │   ├── main.py               # 主命令路由
│   │   ├── import_cmd.py         # 导入子命令实现
│   │   ├── export_cmd.py         # 导出子命令实现
│   │   └── serve_cmd.py          # 本地预览服务子命令
│   ├── core/                     # 核心业务逻辑
│   │   ├── __init__.py
│   │   ├── models.py             # 数据模型（链接、标签、分类）
│   │   ├── parser.py             # 页面元数据提取器
│   │   ├── checker.py            # 链接状态检测器
│   │   └── indexer.py            # 索引构建与搜索实现
│   ├── storage/                  # 持久化层
│   │   ├── __init__.py
│   │   ├── database.py           # SQLite 连接与表初始化
│   │   ├── repository.py         # CRUD 操作抽象
│   │   └── migrations/           # 数据库迁移脚本
│   └── utils/                    # 工具函数集
│       ├── __init__.py
│       ├── logger.py             # 日志配置与格式化
│       ├── validators.py         # URL 校验与规范化
│       └── exporters.py          # JSON / CSV / Markdown 导出
│
├── tests/                        # 单元测试与集成测试
│   ├── conftest.py               # pytest 共享 fixtures
│   ├── test_models.py            # 数据模型测试
│   ├── test_parser.py            # 解析器测试
│   ├── test_checker.py           # 链接检测测试
│   └── test_cli/                 # CLI 子命令测试
│       ├── test_import.py
│       └── test_export.py
│
├── docs/                         # 完整文档
│   ├── user/                     # 用户手册
│   │   ├── import.md
│   │   ├── search.md
│   │   └── export.md
│   ├── dev/                      # 开发者指南
│   │   ├── api.md
│   │   └── testing.md
│   └── ops/                      # 运维参考
│       ├── deployment.md
│       └── monitoring.md
│
├── data/                         # 用户数据存储目录（运行时生成）
│   ├── links.db                  # SQLite 数据库文件
│   └── snapshots/                # 本地快照缓存
│
├── scripts/                      # 辅助脚本
│   ├── initdb.sh                 # 数据库初始化脚本
│   └── sample_import.sh          # 示例导入脚本
│
└── .github/                      # GitHub 社区文件
    └── ISSUE_TEMPLATE/           # 问题反馈模板
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。确保使用 Python 3.8 及以上版本，并安装开发依赖 `pip install -r requirements-dev.txt`。

2. 新建功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。提交前请运行 `pytest tests/` 确保所有既有测试通过，并为新增功能或修复补充对应的测试用例。

3. 代码风格遵循 PEP 8 规范，使用 Black 格式化工具（版本 22.3.0）进行统一格式化，行长度限制为 88 字符。提交前运行 `black src/ tests/` 自动调整格式。

4. 提交信息采用 Conventional Commits 规范，格式为 `<类型>: <简短描述>`，类型包括 feat、fix、docs、style、refactor、test、chore 等。提交前请确保无遗漏的调试输出或注释代码。

5. 发起 Pull Request 到主仓库的 main 分支，在 PR 描述中清晰说明改动目的、影响范围以及测试覆盖情况。PR 合并前需要至少一名维护者审核通过。

## 常见问题

**问：导入大量链接时，如何避免重复条目？**

答：导入命令默认启用去重检测，会基于 URL 的规范化字符串进行精确匹配。如果链接带有不同的大小写或尾部斜杠，系统会自动规范化后再比较。您也可以通过 `--strict` 参数强制要求完全字符匹配。重复条目会被记录到日志中，但不会中止导入过程。

**问：元数据提取失败或超时怎么办？**

答：元数据提取依赖于目标站点的可用性和响应速度。默认超时时间为 10 秒，您可以在配置文件中调整 `parser_timeout` 参数。提取失败时，系统会保留原始 URL 并标记元数据状态为“未解析”，您可以稍后使用 `retry` 子命令重新尝试。对于反爬机制严格的站点，建议配置 `User-Agent` 或 `Referer` 头信息。

**问：如何迁移数据库到另一台机器？**

答：本项目使用 SQLite 数据库，所有数据存储在 `data/links.db` 文件中。迁移时只需复制该文件到目标机器的相同相对路径下即可。如果您使用了快照缓存目录，建议一并打包 `data/snapshots/` 文件夹。跨平台迁移时，请注意 SQLite 版本兼容性，建议目标机器 SQLite 版本不低于 3.28。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
