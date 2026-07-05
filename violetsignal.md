# WebLink Archive Aggregator

WebLink Archive Aggregator 是一个面向技术研究人员、内容聚合者与知识管理工程师的轻量级外链元数据采集与归档系统。该项目定位于对分散在多个博客子域名下的技术文章、案例分析和开发笔记进行集中式索引管理，通过统一的资源条目映射与状态追踪机制，解决多源链接分散、失效不可查、检索无门的技术债务问题。

本项目适用于需要长期维护技术外链池的团队、搭建个人知识库的开发者以及从事互联网内容分析的数据从业者。系统以纯静态资源聚合层为核心，不对原始内容做爬取或存储，仅提供结构化的引用清单与状态标记能力，便于与各类监控告警或自动化检测流水线集成。

## 功能概览

- **多源链接条目聚合**：支持按来源域名、路径格式、参数特征对大量外链进行归类与分组，输出标准化条目清单。
- **可扩展元数据标注**：每条链接可附加自定义标签、归属批次、添加时间、状态备注等字段，便于后期筛选与审计。
- **链接状态可视化仪表板**：内置简单的健康状态标记机制，可配合外部探测脚本展示可访问性、响应码等概览信息。
- **批量导入与导出**：支持通过 TSV、CSV 或纯文本列表批量新增链接条目，并支持导出为结构化文档或 JSON 格式用于下游处理。
- **基于批次的版本管理**：以批次为单位对链接集合进行快照式管理，当前批次为第 20/40 批，便于追溯增量变化与回溯历史状态。
- **轻量级部署与集成**：无需数据库或后端服务，生成静态索引页面即可运行，也可作为模块嵌入现有 Node.js/Python 项目作为数据源。
- **外链变更日志记录**：自动记录每次条目增删改的操作摘要，包含时间戳与操作类型，便于多人协作时保持可审计性。

## 应用场景

- **技术博客聚合与深度阅读队列管理**：开发者在日常浏览过程中积累大量待读或值得归档的技术文章链接，使用本系统可按域名、日期或主题分类存放，并定期清理失效条目，构建个人化的深度阅读 backlog。
- **团队知识库外链资产盘点**：技术团队在维护文档或 Wiki 时往往会引用大量外部资源，这些外链随时间推移容易失效。通过本系统的批次化索引与状态标注，团队可定期执行链接健康检查并更新文档引用，降低知识库腐化风险。
- **互联网内容趋势的样本采集**：数据分析师或行业观察者需要持续收集特定领域（如移动开发、前端框架、运维实践）的公开内容样本。本系统提供结构化的外链清单生成与导出能力，便于结合爬虫或 API 进行批量内容元数据分析。
- **开源项目 README 与文档的外部引用管理**：开源项目维护者需要在文档中引用大量第三方资源，但难以追踪每个链接的可访问性。使用本系统可生成标准化的资源列表章节，并配合 CI 流程自动检查链接状态，确保文档中的外链始终保持有效。

## 快速开始

以下指令适用于 Linux/macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-archive/aggregator.git
cd aggregator

# 安装依赖（使用 npm 或 yarn）
npm install

# 生成初始索引文档（包含示例条目与当前批次数据）
npm run build -- --batch=20 --total=40

# 启动本地预览服务（默认监听 3000 端口）
npm run serve
```

执行完成后，访问 `http://localhost:3000` 即可查看当前批次的资源索引面板。如需重新生成静态文件，可运行 `npm run build` 并指定输出目录。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，用于执行构建脚本与本地服务 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖 |
| git | 2.30 及以上 | 版本控制工具，用于克隆仓库与提交变更 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 推荐使用 Unix-like 环境以获得最佳性能 |
| 网络访问 | 外网可访问原始资源域名 | 用于验证链接可达性（可选功能，可离线运行） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速部署、配置批次参数、生成首批索引文件？ |
| 批次管理 | docs/batch-management.md | 如何创建新批次、切换当前批次、合并历史批次数据？ |
| 链接标注规范 | docs/annotation-spec.md | 支持哪些元数据字段、标签命名规则、状态值枚举定义是什么？ |
| 导出与集成 | docs/export-formats.md | 支持导出为哪些数据格式、如何与 CI/CD 或监控系统对接？ |

## 资源列表

- http://wap.blog.jnjpgf.cn/Article/details/2771694.sHtML
- http://wap.blog.nzfnve.cn/Article/details/8273897.sHtML
- http://wap.blog.nzfnve.cn/Article/details/666956.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1242.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/7675.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/616215.sHtML
- http://wap.blog.nzfnve.cn/Article/details/40406.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8960.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/693603.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5074.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3252764.sHtML
- http://wap.blog.puhvjy.cn/Article/details/841445.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/193694.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/0963.sHtML
- http://wap.blog.puhvjy.cn/Article/details/969703.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/2250784.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/0429.sHtML
- http://wap.blog.puhvjy.cn/Article/details/944893.sHtML
- http://wap.blog.nzfnve.cn/Article/details/135501.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7810809.sHtML
- http://wap.blog.puhvjy.cn/Article/details/7818.sHtML
- http://wap.blog.nzfnve.cn/Article/details/810448.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/662293.sHtML
- http://wap.blog.nzfnve.cn/Article/details/23111.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/2835625.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5018643.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1296700.sHtML
- http://wap.blog.nzfnve.cn/Article/details/602612.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/3661400.sHtML
- http://wap.blog.puhvjy.cn/Article/details/8072.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/157288.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/3105730.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/93144.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7611.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9862.sHtML
- http://wap.blog.puhvjy.cn/Article/details/891325.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/605442.sHtML
- http://wap.blog.nzfnve.cn/Article/details/1536355.sHtML
- http://wap.blog.puhvjy.cn/Article/details/078813.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/0979994.sHtML
- http://wap.blog.nzfnve.cn/Article/details/1671249.sHtML
- http://wap.blog.puhvjy.cn/Article/details/30740.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/6213.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5879.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/778298.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6927.sHtML
- http://wap.blog.nzfnve.cn/Article/details/47486.sHtML
- http://wap.blog.nzfnve.cn/Article/details/409721.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0258.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/687999.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/51423.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/181542.sHtML
- http://wap.blog.nzfnve.cn/Article/details/5302.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/791072.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/6934181.sHtML
- http://wap.blog.puhvjy.cn/Article/details/37532.sHtML
- http://wap.blog.nzfnve.cn/Article/details/979851.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/906141.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/4432008.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/4363.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/33289.sHtML
- http://wap.blog.nzfnve.cn/Article/details/1862.sHtML
- http://wap.blog.nzfnve.cn/Article/details/70572.sHtML
- http://wap.blog.nzfnve.cn/Article/details/8250.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/919001.sHtML
- http://wap.blog.puhvjy.cn/Article/details/4432.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/91289.sHtML
- http://wap.blog.nzfnve.cn/Article/details/866363.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5409623.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3438.sHtML
- http://wap.blog.puhvjy.cn/Article/details/3547.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9671.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/120920.sHtML
- http://wap.blog.nzfnve.cn/Article/details/366113.sHtML
- http://wap.blog.nzfnve.cn/Article/details/376175.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/555482.sHtML
- http://wap.blog.nzfnve.cn/Article/details/356237.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/02595.sHtML
- http://wap.blog.puhvjy.cn/Article/details/95217.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/4857994.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8711914.sHtML
- http://wap.blog.puhvjy.cn/Article/details/3194.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/1703.sHtML
- http://wap.blog.puhvjy.cn/Article/details/973518.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/79830.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/122414.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9649.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/42462.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/036597.sHtML
- http://wap.blog.nzfnve.cn/Article/details/59673.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/67450.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6796.sHtML
- http://wap.blog.puhvjy.cn/Article/details/744600.sHtML
- http://wap.blog.nzfnve.cn/Article/details/8630817.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5839.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6419219.sHtML
- http://wap.blog.nzfnve.cn/Article/details/21286.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/6992.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/4167364.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9891.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9566.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/3131.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/0065.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/8243955.sHtML
- http://wap.blog.puhvjy.cn/Article/details/37094.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6823721.sHtML
- http://wap.blog.nzfnve.cn/Article/details/49888.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/2789.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/92088.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/410832.sHtML
- http://wap.blog.puhvjy.cn/Article/details/0588731.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/6320059.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1740.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7962.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1549589.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3093978.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7517296.sHtML
- http://wap.blog.puhvjy.cn/Article/details/53223.sHtML
- http://wap.blog.puhvjy.cn/Article/details/763167.sHtML
- http://wap.blog.nzfnve.cn/Article/details/1322950.sHtML
- http://wap.blog.nzfnve.cn/Article/details/48084.sHtML
- http://wap.blog.nzfnve.cn/Article/details/469558.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/5232446.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/4757091.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3029499.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8996.sHtML
- http://wap.blog.puhvjy.cn/Article/details/273552.sHtML
- http://wap.blog.puhvjy.cn/Article/details/26421.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4683.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1139.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5574.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/181784.sHtML
- http://wap.blog.puhvjy.cn/Article/details/64667.sHtML
- http://wap.blog.puhvjy.cn/Article/details/66586.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0392.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/44579.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6351597.sHtML
- http://wap.blog.puhvjy.cn/Article/details/71224.sHtML
- http://wap.blog.nzfnve.cn/Article/details/776251.sHtML
- http://wap.blog.nzfnve.cn/Article/details/82670.sHtML
- http://wap.blog.puhvjy.cn/Article/details/46894.sHtML
- http://wap.blog.puhvjy.cn/Article/details/03879.sHtML
- http://wap.blog.puhvjy.cn/Article/details/2324.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/665467.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4012378.sHtML
- http://wap.blog.nzfnve.cn/Article/details/802154.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/007900.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9600064.sHtML
- http://wap.blog.nzfnve.cn/Article/details/19205.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3090.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6193238.sHtML
- http://wap.blog.nzfnve.cn/Article/details/5477826.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/47357.sHtML
- http://wap.blog.puhvjy.cn/Article/details/38003.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3661.sHtML
- http://wap.blog.puhvjy.cn/Article/details/0848680.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9099.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/890680.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/34041.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/857366.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9667.sHtML
- http://wap.blog.nzfnve.cn/Article/details/2755.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/254569.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/66203.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/182003.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/461056.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9060895.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3532416.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7016849.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5249493.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/269737.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7710528.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/215657.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7205.sHtML
- http://wap.blog.nzfnve.cn/Article/details/316707.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9296679.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7286055.sHtML
- http://wap.blog.puhvjy.cn/Article/details/60162.sHtML
- http://wap.blog.nzfnve.cn/Article/details/20231.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/838476.sHtML
- http://wap.blog.nzfnve.cn/Article/details/5955.sHtML
- http://wap.blog.puhvjy.cn/Article/details/84550.sHtML
- http://wap.blog.nzfnve.cn/Article/details/8562.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/18017.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/05298.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/8707.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/914607.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/453802.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/2333608.sHtML
- http://wap.blog.puhvjy.cn/Article/details/253592.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9666105.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7799627.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5408315.sHtML
- http://wap.blog.nzfnve.cn/Article/details/2980956.sHtML
- http://wap.blog.nzfnve.cn/Article/details/77337.sHtML
- http://wap.blog.puhvjy.cn/Article/details/98157.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/9235088.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8258.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/0338972.sHtML
- http://wap.blog.puhvjy.cn/Article/details/8928105.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9303.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3111.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3874.sHtML
- http://wap.blog.puhvjy.cn/Article/details/586135.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/59526.sHtML
- http://wap.blog.nzfnve.cn/Article/details/00984.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7536.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6072.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/678695.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/60161.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/204551.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/851391.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/6566265.sHtML
- http://wap.blog.puhvjy.cn/Article/details/2861167.sHtML
- http://wap.blog.nzfnve.cn/Article/details/397978.sHtML
- http://wap.blog.puhvjy.cn/Article/details/84524.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/111344.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/06259.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8598.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9904659.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/595383.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8051371.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7408389.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3596.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/886510.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/862911.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/9079041.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/2318.sHtML
- http://wap.blog.puhvjy.cn/Article/details/201138.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/0230340.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/9147749.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5810.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/7605583.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3363602.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5721659.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/00527.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9953.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/156704.sHtML
- http://wap.blog.puhvjy.cn/Article/details/367480.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/046385.sHtML
- http://wap.blog.puhvjy.cn/Article/details/32041.sHtML
- http://wap.blog.puhvjy.cn/Article/details/7723.sHtML
- http://wap.blog.nzfnve.cn/Article/details/50704.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8810257.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/44775.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4190.sHtML
- http://wap.blog.nzfnve.cn/Article/details/01156.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/7193.sHtML
- http://wap.blog.puhvjy.cn/Article/details/0698.sHtML
- http://wap.blog.puhvjy.cn/Article/details/973958.sHtML

## 项目结构

```
aggregator/
├── build/                          # 构建输出目录，包含生成的静态索引页面
│   ├── index.html                  # 主索引面板，展示当前批次全部条目
│   └── assets/                     # 样式表与前端脚本
├── src/
│   ├── core/                       # 核心逻辑模块
│   │   ├── entry.js                # 链接条目模型与校验
│   │   ├── batch.js               # 批次管理（创建、切换、合并）
│   │   └── registry.js            # 条目注册表与持久化接口
│   ├── parsers/                    # 输入解析器
│   │   ├── text-list.js           # 纯文本列表解析（每行一个 URL）
│   │   └── tsv-importer.js        # TSV/CSV 批量导入
│   ├── exporters/                  # 输出导出器
│   │   ├── json.js                # JSON 格式导出
│   │   └── markdown.js            # Markdown 列表格式导出（用于 README）
│   ├── cli/                        # 命令行入口
│   │   └── commands.js            # build / serve / export 命令实现
│   └── server/                     # 本地预览服务
│       └── dev-server.js           # 基于 Express 的轻量级静态服务
├── docs/                           # 完整文档目录
│   ├── getting-started.md
│   ├── batch-management.md
│   ├── annotation-spec.md
│   └── export-formats.md
├── tests/                          # 单元测试与集成测试
│   ├── core/                       # 核心模块测试
│   └── fixtures/                   # 测试用固定数据集
├── config/                         # 配置文件
│   ├── default.json               # 默认运行参数（端口、输出路径等）
│   └── schema.json                # 配置项 JSON Schema
├── logs/                           # 操作日志存储目录（按日期滚动）
│   └── 2026-07-06.log
├── package.json                    # npm 依赖与脚本定义
├── README.md                       # 项目说明文档（本文件）
└── LICENSE                         # MIT 许可证文本
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并 clone 到本地开发环境。确保使用 Node.js 20 LTS 版本，运行 `npm install` 安装全部开发依赖。
2. 创建功能分支，分支命名遵循 `feature/简要描述` 或 `fix/问题编号` 格式。所有代码修改需包含对应的单元测试，测试用例放置在 `tests/` 目录下对应子文件夹中。
3. 提交代码前运行 `npm run lint` 和 `npm run test` 确保代码风格一致且所有测试通过。新增导出格式或解析器时，需同步更新 `docs/` 下对应文档。
4. 发起 Pull Request 到主仓库的 `main` 分支，PR 描述中需清晰说明变更目的、影响范围以及是否涉及批次数据结构的兼容性变动。核心维护者将在 3 个工作日内完成 review。
5. 若涉及批次管理逻辑的改动（如批次版本号规则、条目状态枚举值），需在 PR 中附带迁移指南，确保历史批次数据可平滑升级。

## 常见问题

**Q：当前批次中的链接如果失效了怎么办？系统会自动检测吗？**  
A：本系统本身不包含自动探测功能，但项目提供了可选的链接健康检查脚本（位于 `tools/check-links.js`），用户可手动运行或配置到 CI 流水线中定期执行。检查结果会以标注形式记录在条目元数据的 `status` 字段中，支持 `active`、`timeout`、`unreachable` 等状态值。建议每周运行一次检查并更新索引。

**Q：如何将其他格式的外链列表导入到系统中？**  
A：项目支持多种输入格式。纯文本列表（每行一个 URL）可直接使用 `npm run import -- --format=text --input=links.txt` 导入。若使用 TSV 格式，需包含 `url`、`tag`、`remark` 三列，运行 `npm run import -- --format=tsv --input=data.tsv` 即可。导入后系统会自动去重并分配批次编号。

**Q：生成的索引文档能否直接嵌入到其他项目的 README 中？**  
A：可以。项目提供了 Markdown 导出器，运行 `npm run export -- --format=markdown --output=resources.md` 即可生成标准的资源列表章节。该导出器会按照当前批次数据生成与本文档「资源列表」格式一致的条目清单，方便直接复制到其他项目的文档中。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
