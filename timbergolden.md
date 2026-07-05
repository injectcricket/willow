# BlogMap 技术资源索引

BlogMap 是一个面向技术研究与内容聚合的轻量级外链资源汇总系统。项目定位于为开发者、技术博主及数据分析人员提供结构化、可检索的第三方文章与技术文档入口，通过统一的前端界面与标签体系，将散落在多个博客站点及内容平台上的高质量技术文章进行集中管理与快速导航。

项目本身不存储任何原始文章内容，仅维护指向外部资源的元数据索引，包括标题、摘要、分类标签、发布时间及源站信息。目标用户包括个人技术笔记维护者、小型团队内部知识库构建者，以及希望从特定域名聚合内容进行分析的研究人员。BlogMap 通过可扩展的采集与清洗流程，将原始 URL 列表转化为可浏览、可筛选、可搜索的资源导航页，降低技术信息过载带来的检索成本。

## 功能概览

- **多源 URL 聚合管理**：支持批量导入外部文章链接，系统自动解析域名、路径与扩展名，生成统一的资源条目，并保留原始地址作为跳转目标。

- **智能标签与分类引擎**：基于 URL 路径特征与预设规则库，自动为每条资源分配技术领域标签，并支持手动修正与补充，便于后续按主题筛选。

- **全文元数据检索**：针对资源标题、摘要、标签及来源域名构建倒排索引，提供毫秒级响应速度的站内搜索功能，支持模糊匹配与多条件过滤。

- **资源状态监控**：定期对已收录的 URL 进行可用性探测，标记失效链接，并在管理后台生成异常报告，帮助维护索引健康度。

- **批量导入与导出**：支持通过 CSV、JSON 或纯文本列表批量新增资源链接，同时支持按标签、域名或时间范围导出资源清单，便于备份或迁移。

- **响应式前端展示层**：基于 Bootstrap 构建的自适应页面框架，在桌面与移动设备上均能获得良好的浏览体验，资源卡片展示标题、来源、标签与更新时间。

- **权限分级管理**：内置管理员与普通访客两种角色，管理员可执行增删改操作，普通访客仅拥有查看与检索权限，适用于公开导航站或内部知识库场景。

## 应用场景

- **技术博客聚合导航**：个人开发者或技术社区可利用 BlogMap 将日常关注的数十个技术博客的优质单篇文章汇总到同一界面，避免频繁切换书签或依赖 RSS 阅读器的信息遗漏问题。

- **项目文档外部参考库**：在软件研发过程中，团队可将调研阶段查阅的第三方库文档、解决方案文章、性能测试报告等外链统一录入系统，形成项目专属的外部知识索引，方便新成员快速了解技术选型背景。

- **数据分析与爬虫资源整理**：数据采集工程师在爬取多个数据源时，可将各源头的样例页面、API 文档、数据结构说明等链接通过 BlogMap 集中管理，并结合标签体系按数据领域分类，减少重复检索时间。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境，要求系统已安装 Git、Node.js 与 npm。

```bash
# 克隆仓库到本地
git clone https://github.com/your-org/blogmap.git

# 进入项目目录
cd blogmap

# 安装项目依赖（包含后端 Express 与前端构建工具）
npm install

# 启动开发服务器（默认监听 3000 端口）
npm run dev
```

执行完毕后，在浏览器中访问 http://localhost:3000 即可看到 BlogMap 首页。首次启动时系统会自动创建示例资源数据，您可以通过管理后台（/admin）进行导入或手动添加。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.x 或 18.x LTS | 项目运行时环境，推荐使用 nvm 管理版本 |
| npm | 8.x 或 9.x | 依赖包管理器，随 Node.js 一并安装 |
| SQLite3 | 3.x（内置） | 系统默认使用 SQLite 作为元数据存储引擎，无需额外安装数据库服务 |
| Git | 2.30 及以上 | 用于克隆仓库及版本控制操作 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 前端界面需支持 ES6 语法及 CSS Grid 布局 |
| 网络连通性 | 外网可访问 | 资源状态监控功能需对收录 URL 发起 HTTP 请求，需确保网络可达 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/quick-start.md | 如何首次启动系统、导入资源链接、进行基础检索操作 |
| 用户手册 | docs/user-guide/bulk-import.md | 支持哪些批量导入格式、如何通过文本列表一次性新增 200 条以上资源 |
| 开发指南 | docs/developer/api-endpoints.md | 后端提供了哪些 RESTful API、请求参数与返回数据结构如何定义 |
| 运维手册 | docs/operator/health-check.md | 如何配置资源可用性探测的定时任务、如何查看异常链接报告 |

## 资源列表

- http://map.blog.nzfnve.cn/Article/details/0343.sHtML
- http://map.blog.nwbbyt.cn/Article/details/33530.sHtML
- http://map.blog.nwbbyt.cn/Article/details/992011.sHtML
- http://map.blog.nwbbyt.cn/Article/details/93177.sHtML
- http://map.blog.nzfnve.cn/Article/details/6377.sHtML
- http://map.blog.puhvjy.cn/Article/details/00521.sHtML
- http://map.blog.nzfnve.cn/Article/details/79857.sHtML
- http://map.blog.jnjpgf.cn/Article/details/139215.sHtML
- http://map.blog.jnjpgf.cn/Article/details/13794.sHtML
- http://map.blog.nwbbyt.cn/Article/details/69863.sHtML
- http://map.blog.nwbbyt.cn/Article/details/665409.sHtML
- http://map.blog.jnjpgf.cn/Article/details/11924.sHtML
- http://map.blog.nwbbyt.cn/Article/details/520396.sHtML
- http://map.blog.nzfnve.cn/Article/details/7136415.sHtML
- http://map.blog.nzfnve.cn/Article/details/153846.sHtML
- http://map.blog.nwbbyt.cn/Article/details/62601.sHtML
- http://map.blog.puhvjy.cn/Article/details/44530.sHtML
- http://map.blog.jnjpgf.cn/Article/details/391561.sHtML
- http://map.blog.puhvjy.cn/Article/details/246944.sHtML
- http://map.blog.jnjpgf.cn/Article/details/76918.sHtML
- http://map.blog.puhvjy.cn/Article/details/190902.sHtML
- http://map.blog.nzfnve.cn/Article/details/48503.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6421300.sHtML
- http://map.blog.nwbbyt.cn/Article/details/642086.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1232.sHtML
- http://map.blog.puhvjy.cn/Article/details/2612561.sHtML
- http://map.blog.nzfnve.cn/Article/details/77374.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7315504.sHtML
- http://map.blog.nzfnve.cn/Article/details/6031.sHtML
- http://map.blog.nzfnve.cn/Article/details/8815776.sHtML
- http://map.blog.nzfnve.cn/Article/details/69244.sHtML
- http://map.blog.nwbbyt.cn/Article/details/13327.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6109528.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9107190.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8121.sHtML
- http://map.blog.puhvjy.cn/Article/details/5725312.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9590412.sHtML
- http://map.blog.nzfnve.cn/Article/details/633378.sHtML
- http://map.blog.jnjpgf.cn/Article/details/36845.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0958.sHtML
- http://map.blog.puhvjy.cn/Article/details/8796882.sHtML
- http://map.blog.jnjpgf.cn/Article/details/23914.sHtML
- http://map.blog.jnjpgf.cn/Article/details/268735.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6957.sHtML
- http://map.blog.jnjpgf.cn/Article/details/259400.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2504.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9507.sHtML
- http://map.blog.nzfnve.cn/Article/details/42581.sHtML
- http://map.blog.nzfnve.cn/Article/details/6280.sHtML
- http://map.blog.jnjpgf.cn/Article/details/37940.sHtML
- http://map.blog.puhvjy.cn/Article/details/88178.sHtML
- http://map.blog.puhvjy.cn/Article/details/64784.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9070867.sHtML
- http://map.blog.puhvjy.cn/Article/details/626940.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6751438.sHtML
- http://map.blog.puhvjy.cn/Article/details/9571565.sHtML
- http://map.blog.nzfnve.cn/Article/details/989801.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0620266.sHtML
- http://map.blog.puhvjy.cn/Article/details/9231588.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8165260.sHtML
- http://map.blog.jnjpgf.cn/Article/details/567068.sHtML
- http://map.blog.nzfnve.cn/Article/details/08299.sHtML
- http://map.blog.puhvjy.cn/Article/details/0581118.sHtML
- http://map.blog.nzfnve.cn/Article/details/809002.sHtML
- http://map.blog.nzfnve.cn/Article/details/0356.sHtML
- http://map.blog.nzfnve.cn/Article/details/4691.sHtML
- http://map.blog.nwbbyt.cn/Article/details/007866.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2085.sHtML
- http://map.blog.puhvjy.cn/Article/details/7208750.sHtML
- http://map.blog.puhvjy.cn/Article/details/40423.sHtML
- http://map.blog.nwbbyt.cn/Article/details/645426.sHtML
- http://map.blog.nzfnve.cn/Article/details/8105.sHtML
- http://map.blog.puhvjy.cn/Article/details/110330.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6665.sHtML
- http://map.blog.jnjpgf.cn/Article/details/739772.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5311058.sHtML
- http://map.blog.nzfnve.cn/Article/details/184394.sHtML
- http://map.blog.nzfnve.cn/Article/details/8364.sHtML
- http://map.blog.nwbbyt.cn/Article/details/461379.sHtML
- http://map.blog.jnjpgf.cn/Article/details/234577.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3423787.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2728.sHtML
- http://map.blog.nwbbyt.cn/Article/details/273215.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6868.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4718612.sHtML
- http://map.blog.nzfnve.cn/Article/details/14110.sHtML
- http://map.blog.jnjpgf.cn/Article/details/17551.sHtML
- http://map.blog.nzfnve.cn/Article/details/868906.sHtML
- http://map.blog.puhvjy.cn/Article/details/119027.sHtML
- http://map.blog.nzfnve.cn/Article/details/58978.sHtML
- http://map.blog.nzfnve.cn/Article/details/6445391.sHtML
- http://map.blog.jnjpgf.cn/Article/details/858518.sHtML
- http://map.blog.puhvjy.cn/Article/details/8304232.sHtML
- http://map.blog.nzfnve.cn/Article/details/1947913.sHtML
- http://map.blog.jnjpgf.cn/Article/details/493465.sHtML
- http://map.blog.jnjpgf.cn/Article/details/641615.sHtML
- http://map.blog.nzfnve.cn/Article/details/94338.sHtML
- http://map.blog.nzfnve.cn/Article/details/84237.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5622842.sHtML
- http://map.blog.puhvjy.cn/Article/details/7495793.sHtML
- http://map.blog.puhvjy.cn/Article/details/5548083.sHtML
- http://map.blog.nwbbyt.cn/Article/details/17578.sHtML
- http://map.blog.puhvjy.cn/Article/details/999956.sHtML
- http://map.blog.puhvjy.cn/Article/details/5703009.sHtML
- http://map.blog.jnjpgf.cn/Article/details/59973.sHtML
- http://map.blog.nzfnve.cn/Article/details/10634.sHtML
- http://map.blog.nwbbyt.cn/Article/details/900249.sHtML
- http://map.blog.puhvjy.cn/Article/details/37447.sHtML
- http://map.blog.jnjpgf.cn/Article/details/976663.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4025340.sHtML
- http://map.blog.puhvjy.cn/Article/details/38965.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9299.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7765.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3451.sHtML
- http://map.blog.jnjpgf.cn/Article/details/601259.sHtML
- http://map.blog.puhvjy.cn/Article/details/41546.sHtML
- http://map.blog.nzfnve.cn/Article/details/9388.sHtML
- http://map.blog.nzfnve.cn/Article/details/819617.sHtML
- http://map.blog.nzfnve.cn/Article/details/4859.sHtML
- http://map.blog.nwbbyt.cn/Article/details/675028.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6341683.sHtML
- http://map.blog.nwbbyt.cn/Article/details/404398.sHtML
- http://map.blog.nzfnve.cn/Article/details/7806.sHtML
- http://map.blog.nzfnve.cn/Article/details/6700735.sHtML
- http://map.blog.nzfnve.cn/Article/details/4081504.sHtML
- http://map.blog.jnjpgf.cn/Article/details/382004.sHtML
- http://map.blog.puhvjy.cn/Article/details/3053218.sHtML
- http://map.blog.puhvjy.cn/Article/details/16928.sHtML
- http://map.blog.puhvjy.cn/Article/details/1830.sHtML
- http://map.blog.nzfnve.cn/Article/details/2667.sHtML
- http://map.blog.nzfnve.cn/Article/details/26748.sHtML
- http://map.blog.nzfnve.cn/Article/details/3801.sHtML
- http://map.blog.jnjpgf.cn/Article/details/64429.sHtML
- http://map.blog.nwbbyt.cn/Article/details/57467.sHtML
- http://map.blog.puhvjy.cn/Article/details/0802414.sHtML
- http://map.blog.nwbbyt.cn/Article/details/264793.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1320.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1184520.sHtML
- http://map.blog.nwbbyt.cn/Article/details/21021.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0636867.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2597448.sHtML
- http://map.blog.nwbbyt.cn/Article/details/179216.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2596.sHtML
- http://map.blog.puhvjy.cn/Article/details/3454.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3799850.sHtML
- http://map.blog.nzfnve.cn/Article/details/35369.sHtML
- http://map.blog.nwbbyt.cn/Article/details/708616.sHtML
- http://map.blog.puhvjy.cn/Article/details/611360.sHtML
- http://map.blog.jnjpgf.cn/Article/details/876041.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0989.sHtML
- http://map.blog.nzfnve.cn/Article/details/3765220.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3213900.sHtML
- http://map.blog.puhvjy.cn/Article/details/99228.sHtML
- http://map.blog.puhvjy.cn/Article/details/84101.sHtML
- http://map.blog.puhvjy.cn/Article/details/5555.sHtML
- http://map.blog.nzfnve.cn/Article/details/6611.sHtML
- http://map.blog.nzfnve.cn/Article/details/8523.sHtML
- http://map.blog.nzfnve.cn/Article/details/910277.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4051.sHtML
- http://map.blog.nzfnve.cn/Article/details/408895.sHtML
- http://map.blog.nzfnve.cn/Article/details/126489.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8770.sHtML
- http://map.blog.nzfnve.cn/Article/details/2710.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2811.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9279295.sHtML
- http://map.blog.jnjpgf.cn/Article/details/09839.sHtML
- http://map.blog.puhvjy.cn/Article/details/94614.sHtML
- http://map.blog.puhvjy.cn/Article/details/2508670.sHtML
- http://map.blog.nzfnve.cn/Article/details/896902.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9428.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9820.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6196.sHtML
- http://map.blog.nzfnve.cn/Article/details/529076.sHtML
- http://map.blog.jnjpgf.cn/Article/details/533907.sHtML
- http://map.blog.jnjpgf.cn/Article/details/980850.sHtML
- http://map.blog.jnjpgf.cn/Article/details/06536.sHtML
- http://map.blog.puhvjy.cn/Article/details/17339.sHtML
- http://map.blog.puhvjy.cn/Article/details/6816808.sHtML
- http://map.blog.jnjpgf.cn/Article/details/63156.sHtML
- http://map.blog.nwbbyt.cn/Article/details/51418.sHtML
- http://map.blog.puhvjy.cn/Article/details/9444.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6968.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2754270.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0282.sHtML
- http://map.blog.nzfnve.cn/Article/details/49431.sHtML
- http://map.blog.puhvjy.cn/Article/details/5530.sHtML
- http://map.blog.nzfnve.cn/Article/details/09639.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6653.sHtML
- http://map.blog.puhvjy.cn/Article/details/7447.sHtML
- http://map.blog.jnjpgf.cn/Article/details/183292.sHtML
- http://map.blog.puhvjy.cn/Article/details/200398.sHtML
- http://map.blog.jnjpgf.cn/Article/details/21769.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5274.sHtML
- http://map.blog.nzfnve.cn/Article/details/65110.sHtML
- http://map.blog.jnjpgf.cn/Article/details/41482.sHtML
- http://map.blog.puhvjy.cn/Article/details/749071.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5427729.sHtML
- http://map.blog.nwbbyt.cn/Article/details/272620.sHtML
- http://map.blog.jnjpgf.cn/Article/details/91877.sHtML
- http://map.blog.puhvjy.cn/Article/details/0803441.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9448.sHtML
- http://map.blog.nzfnve.cn/Article/details/0906681.sHtML
- http://map.blog.puhvjy.cn/Article/details/36997.sHtML
- http://map.blog.jnjpgf.cn/Article/details/590709.sHtML
- http://map.blog.nzfnve.cn/Article/details/29900.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8318.sHtML
- http://map.blog.puhvjy.cn/Article/details/8847.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3821084.sHtML
- http://map.blog.nzfnve.cn/Article/details/3093396.sHtML
- http://map.blog.puhvjy.cn/Article/details/7991.sHtML
- http://map.blog.nzfnve.cn/Article/details/3270.sHtML
- http://map.blog.puhvjy.cn/Article/details/47129.sHtML
- http://map.blog.nzfnve.cn/Article/details/497804.sHtML
- http://map.blog.nzfnve.cn/Article/details/203085.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7321.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1650.sHtML
- http://map.blog.puhvjy.cn/Article/details/710767.sHtML
- http://map.blog.jnjpgf.cn/Article/details/044990.sHtML
- http://map.blog.nzfnve.cn/Article/details/0684051.sHtML
- http://map.blog.nzfnve.cn/Article/details/70890.sHtML
- http://map.blog.jnjpgf.cn/Article/details/483810.sHtML
- http://map.blog.nzfnve.cn/Article/details/615223.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6565.sHtML
- http://map.blog.puhvjy.cn/Article/details/818369.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2371.sHtML
- http://map.blog.nzfnve.cn/Article/details/077626.sHtML
- http://map.blog.jnjpgf.cn/Article/details/635581.sHtML
- http://map.blog.nwbbyt.cn/Article/details/019199.sHtML
- http://map.blog.nzfnve.cn/Article/details/657452.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0674.sHtML
- http://map.blog.nzfnve.cn/Article/details/376349.sHtML
- http://map.blog.nzfnve.cn/Article/details/22416.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7255623.sHtML
- http://map.blog.puhvjy.cn/Article/details/1211.sHtML
- http://map.blog.puhvjy.cn/Article/details/1786458.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4174.sHtML
- http://map.blog.nzfnve.cn/Article/details/7113545.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5950.sHtML
- http://map.blog.nwbbyt.cn/Article/details/27465.sHtML
- http://map.blog.nzfnve.cn/Article/details/826238.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5355.sHtML
- http://map.blog.puhvjy.cn/Article/details/56000.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4909261.sHtML
- http://map.blog.puhvjy.cn/Article/details/76364.sHtML
- http://map.blog.puhvjy.cn/Article/details/1323.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4068.sHtML
- http://map.blog.nwbbyt.cn/Article/details/445460.sHtML
- http://map.blog.nzfnve.cn/Article/details/275103.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8797287.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7300.sHtML

## 项目结构

```
blogmap/
├── backend/                         # 后端服务模块（Node.js + Express）
│   ├── controllers/                 # 路由控制器，处理资源增删改查及搜索请求
│   ├── models/                      # 数据模型定义，包含资源条目、标签、日志等
│   ├── routes/                      # RESTful API 路由注册文件
│   ├── services/                    # 业务逻辑层，含标签引擎、URL 解析器、状态检测服务
│   ├── utils/                       # 工具函数集，含日志格式化、字符串处理、日期转换
│   └── app.js                       # 应用入口，中间件及数据库连接初始化
├── frontend/                        # 前端静态资源（基于 Bootstrap + vanilla JS）
│   ├── assets/                      # 图片、字体、CSS 主题文件
│   ├── css/                         # 自定义样式表，响应式布局覆盖
│   ├── js/                          # 前端交互逻辑，含检索、分页、标签筛选
│   └── index.html                   # 首页模板，资源卡片渲染容器
├── docs/                            # 项目文档目录
│   ├── user-guide/                  # 用户手册（快速开始、批量导入、搜索技巧）
│   ├── developer/                   # 开发者文档（API 文档、插件扩展说明）
│   └── operator/                    # 运维手册（部署指南、健康检查、数据备份）
├── scripts/                         # 辅助脚本
│   ├── import-batch.js              # 批量导入命令行工具，支持 txt / csv / json
│   ├── health-check.js              # 资源可用性探测定时任务脚本
│   └── migrate-db.js                # 数据库结构迁移与升级脚本
├── config/                          # 配置文件目录
│   ├── default.json                 # 默认配置（端口、数据库路径、日志级别）
│   ├── production.json              # 生产环境覆盖配置
│   └── development.json             # 开发环境覆盖配置
├── data/                            # 数据存储目录
│   └── blogmap.db                   # SQLite 数据库文件（首次启动自动生成）
├── logs/                            # 日志文件目录（按日期滚动）
│   ├── access.log                   # HTTP 访问日志
│   └── error.log                    # 错误与异常日志
├── tests/                           # 单元测试与集成测试
│   ├── unit/                        # 模型与工具函数单元测试
│   └── integration/                 # API 接口集成测试
├── .env.example                     # 环境变量示例文件
├── .gitignore                       # Git 忽略规则
├── package.json                     # npm 项目配置及依赖声明
├── package-lock.json                # 依赖版本锁定文件
└── README.md                        # 项目说明文档
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账号，并克隆到本地开发环境。建议在 dev 分支上基于最新 main 分支创建特性分支，命名格式为 `feature/功能描述` 或 `fix/问题简述`。

2. 本地启动开发服务器，完成代码修改后确保所有现有单元测试通过，并为新增功能补充对应的测试用例。测试文件存放于 `tests/` 目录下，使用 Mocha 或 Jest 框架运行。

3. 提交代码前运行 `npm run lint` 进行代码风格检查，项目统一使用 ESLint 配置（基于 Airbnb 规范），并执行 `npm run format` 自动格式化。提交信息需遵循 Conventional Commits 规范，格式为 `<type>(scope): <subject>`。

4. 推送特性分支到个人远程仓库，随后向本仓库的 main 分支发起 Pull Request。PR 描述中需清晰说明改动目的、影响范围及测试结果，至少一位项目维护者审查通过后方可合并。

5. 如发现资源列表中的失效链接或希望新增功能模块，可通过 Issues 提交反馈，标记为 `bug` 或 `enhancement`，并附上复现步骤或需求背景说明。

## 常见问题

**Q：资源列表中的 URL 在导入后显示为无效链接，但浏览器中可以直接访问，是什么原因？**

A：BlogMap 的健康检查模块默认采用 HEAD 请求探测资源可用性，部分站点可能不支持 HEAD 方法或对非浏览器 User-Agent 返回非 200 状态码。您可以在管理后台的检测配置中将请求方式切换为 GET，或调整超时时间与重试次数。此外，检查服务器防火墙或代理设置是否拦截了出口请求。若问题持续，可暂时将对应条目标记为「忽略检测」状态，等待后续版本优化探测逻辑。

**Q：批量导入 200 条以上 URL 时，系统响应变慢甚至超时，该如何优化？**

A：对于大规模导入任务，建议使用命令行脚本 `scripts/import-batch.js` 而非 Web 界面上传，该脚本采用流式处理与分批写入数据库的方式，避免一次性加载全部数据到内存。同时，您可在配置文件中调整 `batchSize` 参数（默认 50），降低单次事务提交的记录数。若数据库体积持续增长，可考虑迁移至 PostgreSQL 或 MySQL 以获得更高的写入吞吐量。

**Q：系统是否支持自定义标签体系，还是只能使用系统预设标签？**

A：系统预设标签仅作为初始分类参考，您完全可以在管理后台的「标签管理」模块中新增、编辑或删除任意标签。新增标签后，在编辑资源条目时即可从下拉列表中选用。同时，系统支持基于 URL 路径特征的自动标签规则配置，您可在 `config/tag-rules.json` 中维护正则表达式与标签的映射关系，实现批量资源的自动归类。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
