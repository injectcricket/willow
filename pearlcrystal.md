# MapBlog 外链聚合系统

MapBlog 是一个面向技术博客与知识库的外链资源聚合与结构化导航系统，专为技术内容创作者、开源文档维护者以及研发团队知识管理场景设计。项目定位于对分散于多个独立博客站点中的高质量技术文章、教程、案例与解决方案进行统一采集、归类与检索，解决技术资料碎片化、链接失效、检索效率低等长期存在的痛点。

MapBlog 并非简单的书签集合或导航页，而是一套具备版本追踪、来源标注、分类标签与全文检索能力的轻量级外链管理工具。项目目前已收录超过 250 条经过人工核验的技术外链，覆盖后端开发、前端工程、运维监控、数据库调优、算法与数据结构等多个领域，适用于日均处理 50 至 500 条外链资源的个人或团队知识库场景。项目采用纯静态生成方案，无外部数据库依赖，所有资源数据以结构化 Markdown 与 YAML Frontmatter 形式存储，可无缝集成至现有 CI/CD 工作流或静态站点生成器（如 Hugo、VuePress、Docusaurus）中。

## 功能概览

**多源异构数据采集** 支持从多个独立博客域名下批量拉取 Article 目录下的 HTML 页面，自动解析页面标题、发布时间、分类标签与正文摘要，形成标准化外链条目。

**智能去重与更新检测** 基于 URL 特征与内容哈希值对同一资源在不同时间点的抓取结果进行比对，自动识别内容更新与链接变更，避免重复收录。

**分类与标签体系** 内置一套可扩展的技术分类体系，默认包含后端架构、前端交互、性能优化、安全防护、容器化部署、数据库设计、算法思维、运维自动化等八个一级分类，用户可根据实际资源分布自定义标签。

**全文检索与过滤** 基于 Lunr.js 或 Minisearch 构建的客户端全文检索引擎，支持按标题关键词、域名来源、分类标签、发布时间区间等多维度组合过滤，检索结果毫秒级返回。

**资源状态监控** 自动对已收录链接进行可用性探测，标记 404、超时、重定向等异常状态，并生成周期性的资源健康报告，辅助管理员及时清理或更新失效外链。

**数据导出与嵌入** 支持将外链资源列表导出为 JSON、CSV 或 OPML 格式，便于迁移至其他知识管理工具或嵌入到团队内部 Wiki、Notion 数据库中。

**暗色主题与响应式布局** 前端界面同时适配桌面端与移动端浏览器，内置明暗两套配色方案，自动跟随操作系统主题偏好。

## 应用场景

技术博客精选聚合与日常阅读管理。技术团队或内容运营人员可将 MapBlog 作为内部技术雷达的基础设施，定期从关注的技术博客中采集最新文章，形成团队共享的阅读清单，避免重复订阅与信息过载。

开源项目文档的外链引用管理。开源项目的 README 或官方文档中通常需要引用大量外部资源，MapBlog 可对外链进行统一管理和版本记录，当外部资源变更或迁移时能够快速定位并批量更新文档中的链接。

研发团队入职培训知识库构建。新员工入职期间需要阅读大量内部与外部的技术资料，MapBlog 可将散落在不同站点中的精华文章按技术方向归类，形成结构化的培训阅读路径，缩短新人的上手周期。

技术社区内容运营的选题辅助。技术社区编辑或运营人员可通过 MapBlog 快速了解近期技术热点与高频讨论话题，基于收录文章的关键词分布与来源分析制定内容选题计划。

## 快速开始

以下步骤将指导您在本地环境中完成 MapBlog 的克隆、依赖安装与开发服务器启动。

```bash
git clone https://github.com/mapblog/mapblog-core.git
cd mapblog-core
npm install
npm run dev
```

执行完上述命令后，打开浏览器访问 http://localhost:3000 即可查看 MapBlog 的本地运行实例。生产环境构建请使用 `npm run build` 命令，构建产物默认输出至 `dist` 目录，可部署至任意静态托管服务。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理器，随 Node.js 一同安装 |
| Git | 2.30 及以上 | 用于克隆仓库与版本管理 |
| Python | 3.9 及以上 | 仅当启用外链健康检查脚本时需要（可选） |
| curl | 7.68 及以上 | 用于部分采集脚本的网络请求（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何快速搭建 MapBlog 实例并进行基础配置 |
| 采集配置 | /docs/collection.md | 如何添加新的博客源、调整采集频率与过滤规则 |
| 分类体系 | /docs/taxonomy.md | 现有分类与标签的定义说明，以及自定义分类的方法 |
| API 参考 | /docs/api.md | 静态数据接口与前端检索 API 的调用方式与参数说明 |

## 资源列表

- http://map.blog.nwbbyt.cn/Article/details/3959755.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8814.sHtML
- http://map.blog.puhvjy.cn/Article/details/6841.sHtML
- http://map.blog.nwbbyt.cn/Article/details/89508.sHtML
- http://map.blog.puhvjy.cn/Article/details/4075.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2494.sHtML
- http://map.blog.nzfnve.cn/Article/details/09375.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1183.sHtML
- http://map.blog.puhvjy.cn/Article/details/1375468.sHtML
- http://map.blog.puhvjy.cn/Article/details/46854.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7756.sHtML
- http://map.blog.nzfnve.cn/Article/details/5021995.sHtML
- http://map.blog.nzfnve.cn/Article/details/0979.sHtML
- http://map.blog.nzfnve.cn/Article/details/8666.sHtML
- http://map.blog.puhvjy.cn/Article/details/5762261.sHtML
- http://map.blog.nzfnve.cn/Article/details/6489435.sHtML
- http://map.blog.puhvjy.cn/Article/details/772872.sHtML
- http://map.blog.nwbbyt.cn/Article/details/41519.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1421.sHtML
- http://map.blog.nwbbyt.cn/Article/details/71629.sHtML
- http://map.blog.puhvjy.cn/Article/details/529195.sHtML
- http://map.blog.nwbbyt.cn/Article/details/182312.sHtML
- http://map.blog.nwbbyt.cn/Article/details/714687.sHtML
- http://map.blog.nwbbyt.cn/Article/details/262821.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5685541.sHtML
- http://map.blog.puhvjy.cn/Article/details/405006.sHtML
- http://map.blog.nwbbyt.cn/Article/details/90537.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7836.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8520755.sHtML
- http://map.blog.nwbbyt.cn/Article/details/287848.sHtML
- http://map.blog.puhvjy.cn/Article/details/68575.sHtML
- http://map.blog.nzfnve.cn/Article/details/346908.sHtML
- http://map.blog.nzfnve.cn/Article/details/0376966.sHtML
- http://map.blog.nzfnve.cn/Article/details/4543.sHtML
- http://map.blog.nzfnve.cn/Article/details/5427476.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5987.sHtML
- http://map.blog.puhvjy.cn/Article/details/4470795.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7647625.sHtML
- http://map.blog.nwbbyt.cn/Article/details/076033.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4908.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0723053.sHtML
- http://map.blog.jnjpgf.cn/Article/details/76491.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5422.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9934.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6815584.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3794472.sHtML
- http://map.blog.puhvjy.cn/Article/details/251907.sHtML
- http://map.blog.puhvjy.cn/Article/details/0621.sHtML
- http://map.blog.puhvjy.cn/Article/details/801026.sHtML
- http://map.blog.nzfnve.cn/Article/details/21412.sHtML
- http://map.blog.nzfnve.cn/Article/details/18785.sHtML
- http://map.blog.puhvjy.cn/Article/details/2363.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4971121.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6295.sHtML
- http://map.blog.nzfnve.cn/Article/details/9255500.sHtML
- http://map.blog.nzfnve.cn/Article/details/853965.sHtML
- http://map.blog.puhvjy.cn/Article/details/3725712.sHtML
- http://map.blog.nzfnve.cn/Article/details/942992.sHtML
- http://map.blog.jnjpgf.cn/Article/details/502275.sHtML
- http://map.blog.nzfnve.cn/Article/details/2209285.sHtML
- http://map.blog.puhvjy.cn/Article/details/7199.sHtML
- http://map.blog.nzfnve.cn/Article/details/98142.sHtML
- http://map.blog.puhvjy.cn/Article/details/219658.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6626535.sHtML
- http://map.blog.nzfnve.cn/Article/details/01170.sHtML
- http://map.blog.nzfnve.cn/Article/details/8373.sHtML
- http://map.blog.puhvjy.cn/Article/details/68287.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9629463.sHtML
- http://map.blog.nzfnve.cn/Article/details/2698.sHtML
- http://map.blog.nzfnve.cn/Article/details/5616.sHtML
- http://map.blog.nzfnve.cn/Article/details/2070304.sHtML
- http://map.blog.puhvjy.cn/Article/details/6305210.sHtML
- http://map.blog.puhvjy.cn/Article/details/018024.sHtML
- http://map.blog.puhvjy.cn/Article/details/40785.sHtML
- http://map.blog.nzfnve.cn/Article/details/6579.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5885.sHtML
- http://map.blog.puhvjy.cn/Article/details/9275.sHtML
- http://map.blog.jnjpgf.cn/Article/details/854694.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3245545.sHtML
- http://map.blog.nzfnve.cn/Article/details/3976954.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2104033.sHtML
- http://map.blog.puhvjy.cn/Article/details/1348888.sHtML
- http://map.blog.puhvjy.cn/Article/details/3498.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3965100.sHtML
- http://map.blog.puhvjy.cn/Article/details/41351.sHtML
- http://map.blog.puhvjy.cn/Article/details/93097.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8277076.sHtML
- http://map.blog.puhvjy.cn/Article/details/651354.sHtML
- http://map.blog.jnjpgf.cn/Article/details/83578.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1646.sHtML
- http://map.blog.nzfnve.cn/Article/details/483986.sHtML
- http://map.blog.puhvjy.cn/Article/details/326835.sHtML
- http://map.blog.puhvjy.cn/Article/details/3800512.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3805245.sHtML
- http://map.blog.nzfnve.cn/Article/details/7086858.sHtML
- http://map.blog.nzfnve.cn/Article/details/5464652.sHtML
- http://map.blog.nzfnve.cn/Article/details/3033.sHtML
- http://map.blog.puhvjy.cn/Article/details/225163.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5353.sHtML
- http://map.blog.puhvjy.cn/Article/details/8441412.sHtML
- http://map.blog.nzfnve.cn/Article/details/5093.sHtML
- http://map.blog.puhvjy.cn/Article/details/706867.sHtML
- http://map.blog.nzfnve.cn/Article/details/139217.sHtML
- http://map.blog.jnjpgf.cn/Article/details/690696.sHtML
- http://map.blog.puhvjy.cn/Article/details/9418653.sHtML
- http://map.blog.nzfnve.cn/Article/details/82275.sHtML
- http://map.blog.nwbbyt.cn/Article/details/455039.sHtML
- http://map.blog.nzfnve.cn/Article/details/9656377.sHtML
- http://map.blog.jnjpgf.cn/Article/details/790901.sHtML
- http://map.blog.jnjpgf.cn/Article/details/228963.sHtML
- http://map.blog.nzfnve.cn/Article/details/898656.sHtML
- http://map.blog.puhvjy.cn/Article/details/890337.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4724.sHtML
- http://map.blog.puhvjy.cn/Article/details/4295318.sHtML
- http://map.blog.nzfnve.cn/Article/details/3226936.sHtML
- http://map.blog.nwbbyt.cn/Article/details/83604.sHtML
- http://map.blog.jnjpgf.cn/Article/details/517554.sHtML
- http://map.blog.nwbbyt.cn/Article/details/97382.sHtML
- http://map.blog.nzfnve.cn/Article/details/67636.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6374.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9272.sHtML
- http://map.blog.nwbbyt.cn/Article/details/96456.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4850.sHtML
- http://map.blog.puhvjy.cn/Article/details/707151.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7943.sHtML
- http://map.blog.jnjpgf.cn/Article/details/824453.sHtML
- http://map.blog.jnjpgf.cn/Article/details/84840.sHtML
- http://map.blog.nzfnve.cn/Article/details/06825.sHtML
- http://map.blog.puhvjy.cn/Article/details/443710.sHtML
- http://map.blog.jnjpgf.cn/Article/details/408832.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5811783.sHtML
- http://map.blog.puhvjy.cn/Article/details/607492.sHtML
- http://map.blog.nzfnve.cn/Article/details/340926.sHtML
- http://map.blog.nzfnve.cn/Article/details/850421.sHtML
- http://map.blog.nzfnve.cn/Article/details/960089.sHtML
- http://map.blog.puhvjy.cn/Article/details/21222.sHtML
- http://map.blog.nzfnve.cn/Article/details/59345.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8549537.sHtML
- http://map.blog.puhvjy.cn/Article/details/494541.sHtML
- http://map.blog.puhvjy.cn/Article/details/6123.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0938099.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8920.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7069.sHtML
- http://map.blog.jnjpgf.cn/Article/details/67358.sHtML
- http://map.blog.nwbbyt.cn/Article/details/711376.sHtML
- http://map.blog.nwbbyt.cn/Article/details/50195.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4268.sHtML
- http://map.blog.puhvjy.cn/Article/details/3340273.sHtML
- http://map.blog.nzfnve.cn/Article/details/2360381.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3333.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6826681.sHtML
- http://map.blog.puhvjy.cn/Article/details/4425828.sHtML
- http://map.blog.nzfnve.cn/Article/details/7559665.sHtML
- http://map.blog.puhvjy.cn/Article/details/97294.sHtML
- http://map.blog.jnjpgf.cn/Article/details/233225.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3837870.sHtML
- http://map.blog.nwbbyt.cn/Article/details/162060.sHtML
- http://map.blog.nzfnve.cn/Article/details/5758.sHtML
- http://map.blog.puhvjy.cn/Article/details/9681261.sHtML
- http://map.blog.puhvjy.cn/Article/details/280206.sHtML
- http://map.blog.nwbbyt.cn/Article/details/448197.sHtML
- http://map.blog.jnjpgf.cn/Article/details/973938.sHtML
- http://map.blog.puhvjy.cn/Article/details/7602881.sHtML
- http://map.blog.jnjpgf.cn/Article/details/513573.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9926.sHtML
- http://map.blog.puhvjy.cn/Article/details/05628.sHtML
- http://map.blog.jnjpgf.cn/Article/details/081907.sHtML
- http://map.blog.puhvjy.cn/Article/details/0684723.sHtML
- http://map.blog.jnjpgf.cn/Article/details/395291.sHtML
- http://map.blog.nzfnve.cn/Article/details/7928891.sHtML
- http://map.blog.nzfnve.cn/Article/details/0530.sHtML
- http://map.blog.nzfnve.cn/Article/details/56375.sHtML
- http://map.blog.nzfnve.cn/Article/details/45325.sHtML
- http://map.blog.puhvjy.cn/Article/details/29210.sHtML
- http://map.blog.jnjpgf.cn/Article/details/416704.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9842387.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7307.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9650.sHtML
- http://map.blog.nzfnve.cn/Article/details/4189.sHtML
- http://map.blog.nwbbyt.cn/Article/details/171129.sHtML
- http://map.blog.nzfnve.cn/Article/details/9476.sHtML
- http://map.blog.nwbbyt.cn/Article/details/822263.sHtML
- http://map.blog.nzfnve.cn/Article/details/2233.sHtML
- http://map.blog.nzfnve.cn/Article/details/47454.sHtML
- http://map.blog.nzfnve.cn/Article/details/10992.sHtML
- http://map.blog.puhvjy.cn/Article/details/02332.sHtML
- http://map.blog.puhvjy.cn/Article/details/6108.sHtML
- http://map.blog.nzfnve.cn/Article/details/403748.sHtML
- http://map.blog.nwbbyt.cn/Article/details/95807.sHtML
- http://map.blog.puhvjy.cn/Article/details/41150.sHtML
- http://map.blog.nwbbyt.cn/Article/details/01445.sHtML
- http://map.blog.jnjpgf.cn/Article/details/558790.sHtML
- http://map.blog.nzfnve.cn/Article/details/8296189.sHtML
- http://map.blog.nwbbyt.cn/Article/details/791825.sHtML
- http://map.blog.jnjpgf.cn/Article/details/287508.sHtML
- http://map.blog.puhvjy.cn/Article/details/8611.sHtML
- http://map.blog.jnjpgf.cn/Article/details/76854.sHtML
- http://map.blog.puhvjy.cn/Article/details/880204.sHtML
- http://map.blog.jnjpgf.cn/Article/details/380818.sHtML
- http://map.blog.jnjpgf.cn/Article/details/65998.sHtML
- http://map.blog.puhvjy.cn/Article/details/73815.sHtML
- http://map.blog.puhvjy.cn/Article/details/57047.sHtML
- http://map.blog.nzfnve.cn/Article/details/7108.sHtML
- http://map.blog.nwbbyt.cn/Article/details/670052.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7152166.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2939.sHtML
- http://map.blog.puhvjy.cn/Article/details/178025.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2604662.sHtML
- http://map.blog.jnjpgf.cn/Article/details/012888.sHtML
- http://map.blog.nzfnve.cn/Article/details/77147.sHtML
- http://map.blog.puhvjy.cn/Article/details/8061676.sHtML
- http://map.blog.nzfnve.cn/Article/details/5701708.sHtML
- http://map.blog.puhvjy.cn/Article/details/638233.sHtML
- http://map.blog.jnjpgf.cn/Article/details/12113.sHtML
- http://map.blog.nzfnve.cn/Article/details/224293.sHtML
- http://map.blog.nzfnve.cn/Article/details/2936.sHtML
- http://map.blog.nzfnve.cn/Article/details/3423746.sHtML
- http://map.blog.nzfnve.cn/Article/details/3693.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3695.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4825.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2114.sHtML
- http://map.blog.puhvjy.cn/Article/details/53840.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3031.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5319658.sHtML
- http://map.blog.puhvjy.cn/Article/details/957560.sHtML
- http://map.blog.jnjpgf.cn/Article/details/687909.sHtML
- http://map.blog.nzfnve.cn/Article/details/6581726.sHtML
- http://map.blog.puhvjy.cn/Article/details/05783.sHtML
- http://map.blog.nzfnve.cn/Article/details/51195.sHtML
- http://map.blog.jnjpgf.cn/Article/details/673858.sHtML
- http://map.blog.nwbbyt.cn/Article/details/09158.sHtML
- http://map.blog.puhvjy.cn/Article/details/3192.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5066.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5303.sHtML
- http://map.blog.nwbbyt.cn/Article/details/67129.sHtML
- http://map.blog.nzfnve.cn/Article/details/5534.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1539153.sHtML
- http://map.blog.nzfnve.cn/Article/details/5498163.sHtML
- http://map.blog.puhvjy.cn/Article/details/142427.sHtML
- http://map.blog.jnjpgf.cn/Article/details/885204.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1159699.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0206744.sHtML
- http://map.blog.nzfnve.cn/Article/details/1610364.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7058.sHtML
- http://map.blog.nwbbyt.cn/Article/details/73957.sHtML
- http://map.blog.jnjpgf.cn/Article/details/02220.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9002556.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6601923.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4859.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2342146.sHtML

## 项目结构

```
mapblog-core/
├── src/                                 # 核心源代码目录
│   ├── collector/                       # 数据采集模块
│   │   ├── fetcher.ts                   # 基于 axios 的 HTTP 请求封装，含重试与超时控制
│   │   ├── parser.ts                    # HTML 解析器，基于 cheerio 提取标题/分类/正文
│   │   └── deduper.ts                   # 基于 URL 与内容哈希的去重算法实现
│   ├── storage/                         # 数据存储与读写模块
│   │   ├── index.ts                     # 统一的数据读写接口，支持 JSON/YAML 格式
│   │   └── schema.ts                    # 外链条目数据结构定义（TypeScript 接口）
│   ├── search/                          # 全文检索模块
│   │   ├── indexer.ts                   # 索引构建器，将资源列表转换为倒排索引
│   │   └── query.ts                     # 查询解析器，支持多字段组合检索
│   ├── monitor/                         # 资源健康监控模块
│   │   ├── checker.ts                   # 基于 head 请求的可用性探测
│   │   └── reporter.ts                  # 生成 Markdown 格式的健康报告
│   ├── ui/                              # 前端界面组件
│   │   ├── pages/                       # 页面级组件（首页、列表页、详情页）
│   │   ├── components/                  # 可复用 UI 组件（搜索框、标签筛选、分页器）
│   │   └── styles/                      # 基于 CSS 变量的主题配置（明暗切换）
│   └── main.ts                          # 应用入口，整合采集、存储、检索与监控流程
├── config/                              # 配置文件目录
│   ├── sources.json                     # 博客源列表（域名、采集间隔、是否启用）
│   └── taxonomy.yaml                    # 分类与标签体系定义
├── data/                                # 数据存储目录（运行时生成）
│   ├── resources.json                   # 所有已收录外链的主数据文件
│   └── index.json                       # 全文检索引擎的索引快照
├── docs/                                # 项目文档目录
│   ├── getting-started.md               # 入门指南
│   ├── collection.md                    # 采集配置说明
│   ├── taxonomy.md                      # 分类体系文档
│   └── api.md                           # API 参考手册
├── scripts/                             # 辅助脚本目录
│   ├── health-check.py                  # Python 实现的外链健康检查脚本（可选）
│   └── import-csv.ts                    # 从 CSV 批量导入外链的工具脚本
├── tests/                               # 单元测试与集成测试
│   ├── collector.test.ts                # 采集模块测试用例
│   └── search.test.ts                   # 检索引擎测试用例
├── .gitignore                           # Git 版本控制忽略规则
├── package.json                         # npm 包清单与依赖声明
├── tsconfig.json                        # TypeScript 编译配置
├── vite.config.ts                       # Vite 构建工具配置
└── README.md                            # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎并鼓励开发者以多种形式参与 MapBlog 项目的建设与改进。请遵循以下步骤提交贡献。

第一，在 GitHub 上 Fork 本仓库至个人账户，并将 Fork 后的仓库克隆至本地开发环境。请确保本地 Git 全局配置了正确的用户名与邮箱。

第二，新建一个以 `feature/` 或 `fix/` 为前缀的功能分支，例如 `feature/add-new-source` 或 `fix/deduper-issue`，避免在主分支上直接修改。

第三，按照项目已有的代码风格与 TypeScript 类型规范进行开发。提交代码前请运行 `npm run lint` 与 `npm run test` 确保代码质量与现有测试用例全部通过。若新增功能模块，需同步补充对应的单元测试。

第四，提交 Pull Request 至本仓库的 `main` 分支，并在 PR 描述中清晰说明改动内容、关联的 Issue 编号以及测试覆盖情况。PR 将由项目维护者进行 Code Review，通过后合并。

第五，文档更新与示例补充同样被视为有效贡献。若修改了用户可见的功能，请同步更新 `docs/` 目录下对应的文档文件。

## 常见问题

Q：MapBlog 是否支持从需要登录或带有反爬机制的站点采集数据？

A：当前版本仅支持对公开可访问的静态 HTML 页面进行采集。对于需要登录或带有复杂反爬机制的站点，建议用户自行在 `fetcher.ts` 中扩展 Cookie 注入或代理配置。项目本身不提供绕过登录或反爬策略的功能，请遵守目标站点的 robots.txt 规定。

Q：采集过程中出现大量 404 或超时错误，应如何排查？

A：首先检查网络环境是否能够正常访问目标域名，可使用 `curl -I` 命令手动测试。其次检查 `config/sources.json` 中的域名配置是否正确，注意不要包含多余的路径前缀。若目标站点存在访问频率限制，可在 `fetcher.ts` 中调整请求间隔与重试次数参数。日志文件默认输出至 `logs/` 目录，可从中获取详细的错误堆栈信息。

Q：如何将 MapBlog 部署到生产环境，并实现每日自动采集更新？

A：生产部署推荐使用 `npm run build` 生成静态文件，然后将 `dist/` 目录托管至 Nginx、Caddy 或云对象存储（如 AWS S3、阿里云 OSS）。自动采集可通过系统 crontab 或 GitHub Actions 的定时任务实现，例如每日凌晨 2 点执行 `npm run collect` 脚本更新 `data/resources.json`，再执行 `npm run build` 重新生成静态页面。注意在定时任务中配置好正确的环境变量与工作目录。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
