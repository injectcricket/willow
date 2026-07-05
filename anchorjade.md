# WebIndex 技术资源聚合导航

WebIndex 是一个面向开发者、技术研究人员与信息分析人员的高密度外链资源聚合站。项目定位于对分散于多源技术博客、文档站点与知识库中的高质量文章进行结构化收录与导航，帮助用户在不依赖搜索引擎模糊召回的前提下，快速定位到特定主题的深度技术内容。本项目不生产内容，仅做索引与分类组织，适用于需要持续跟踪特定技术领域动态、进行文献回溯或构建个人知识图谱的群体。

## 功能概览

**多源异构数据统一索引**：支持对多个独立技术博客站点的文章级 URL 进行采集、去重与规范化存储，形成统一的资源视图。

**按文章 ID 与来源域名的精确检索**：用户可通过文章编号或源站域名快速定位目标资源，支持模糊匹配与精确查询两种模式。

**资源分类标签系统**：每一条收录链接均支持附加技术领域、难度等级、内容类型等标签，便于后续按主题筛选。

**批量导入与增量更新机制**：支持通过文本文件或 API 接口批量提交新链接，系统自动识别新增与变更，避免重复收录。

**访问状态健康检查**：定期对已收录的 URL 进行可用性探测，标记失效链接并生成报告，确保导航数据的有效性。

**数据导出与嵌入能力**：支持将资源列表导出为 CSV、JSON 或纯文本格式，便于嵌入其他文档系统或进行二次分析。

**轻量级管理面板**：提供基于命令行的交互式管理工具，支持添加、删除、搜索、统计等日常运维操作。

## 应用场景

技术团队内部知识库建设。团队可将日常阅读的优秀技术文章通过本系统统一收录，并按照项目或技术栈分类，新成员入职时可快速获得经过筛选的学习路径。

技术博客聚合阅读。独立博客作者或小型技术媒体可将自己的文章列表导入系统，生成对外公开的导航页面，提升历史内容的曝光率与可发现性。

技术调研与竞品分析。研究人员针对特定领域（如容器编排、前端框架、数据库引擎）收集大量参考链接，通过本系统进行集中管理，并定期导出为调研报告附件。

个人学习进度追踪。学习者将待读文章批量录入，系统记录阅读状态与标签，配合健康检查功能，可及时剔除已失效的参考链接。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex-core.git

# 进入项目目录
cd webindex-core

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 初始化本地数据库（SQLite）
python scripts/init_db.py

# 从示例数据文件导入首批链接
python scripts/import_urls.py --file samples/urls_32.txt

# 启动本地 Web 服务（默认端口 8080）
python app.py --port 8080
```

访问 http://localhost:8080 即可查看已收录资源列表，支持按域名、关键词筛选。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，推荐 3.11 |
| SQLite | 3.35 及以上 | 本地轻量级数据库，无需额外安装 |
| requests | 2.28.0 及以上 | 用于 HTTP 健康检查与资源探测 |
| beautifulsoup4 | 4.11.0 及以上 | 可选，用于解析 HTML 摘要信息 |
| flask | 2.2.0 及以上 | 仅当启动 Web 服务时需要 |
| pytest | 7.0.0 及以上 | 仅开发测试时需要 |
| black | 22.0.0 及以上 | 仅代码格式化时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、如何搜索、如何导出结果 |
| 运维手册 | docs/operations.md | 健康检查如何配置、数据库如何备份 |
| 开发者指南 | docs/development.md | 项目架构、新增数据源适配器的方法 |
| API 参考 | docs/api-reference.md | RESTful 接口定义、请求示例与返回字段 |
| 常见问题 | docs/faq.md | 收录失败原因、标签体系设计思路 |
| 版本历史 | CHANGELOG.md | 每个版本的更新内容与兼容性变动 |

## 资源列表

- http://map.blog.nzfnve.cn/Article/details/3606.sHtML
- http://map.blog.puhvjy.cn/Article/details/9614.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5962756.sHtML
- http://map.blog.jnjpgf.cn/Article/details/809531.sHtML
- http://map.blog.puhvjy.cn/Article/details/6438737.sHtML
- http://map.blog.puhvjy.cn/Article/details/1104.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2774.sHtML
- http://map.blog.nwbbyt.cn/Article/details/774211.sHtML
- http://map.blog.nzfnve.cn/Article/details/284724.sHtML
- http://map.blog.puhvjy.cn/Article/details/13906.sHtML
- http://map.blog.nzfnve.cn/Article/details/370062.sHtML
- http://map.blog.nwbbyt.cn/Article/details/924611.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9003269.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1195849.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3616267.sHtML
- http://map.blog.puhvjy.cn/Article/details/8988487.sHtML
- http://map.blog.nzfnve.cn/Article/details/7286988.sHtML
- http://map.blog.nzfnve.cn/Article/details/34069.sHtML
- http://map.blog.nzfnve.cn/Article/details/5834.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3767.sHtML
- http://map.blog.puhvjy.cn/Article/details/6839.sHtML
- http://map.blog.jnjpgf.cn/Article/details/63944.sHtML
- http://map.blog.nzfnve.cn/Article/details/34129.sHtML
- http://map.blog.puhvjy.cn/Article/details/3941937.sHtML
- http://map.blog.nzfnve.cn/Article/details/634380.sHtML
- http://map.blog.jnjpgf.cn/Article/details/25996.sHtML
- http://map.blog.jnjpgf.cn/Article/details/336300.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9990.sHtML
- http://map.blog.puhvjy.cn/Article/details/315086.sHtML
- http://map.blog.nzfnve.cn/Article/details/9884.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0533720.sHtML
- http://map.blog.nzfnve.cn/Article/details/6236.sHtML
- http://map.blog.nwbbyt.cn/Article/details/240675.sHtML
- http://map.blog.puhvjy.cn/Article/details/06463.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2950.sHtML
- http://map.blog.nzfnve.cn/Article/details/6187.sHtML
- http://map.blog.puhvjy.cn/Article/details/7737833.sHtML
- http://map.blog.puhvjy.cn/Article/details/24254.sHtML
- http://map.blog.nzfnve.cn/Article/details/68714.sHtML
- http://map.blog.nwbbyt.cn/Article/details/615839.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4739.sHtML
- http://map.blog.jnjpgf.cn/Article/details/141579.sHtML
- http://map.blog.nzfnve.cn/Article/details/21240.sHtML
- http://map.blog.nzfnve.cn/Article/details/7063356.sHtML
- http://map.blog.nwbbyt.cn/Article/details/255642.sHtML
- http://map.blog.jnjpgf.cn/Article/details/729336.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3258.sHtML
- http://map.blog.puhvjy.cn/Article/details/563292.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3420013.sHtML
- http://map.blog.nzfnve.cn/Article/details/69124.sHtML
- http://map.blog.puhvjy.cn/Article/details/8104135.sHtML
- http://map.blog.nwbbyt.cn/Article/details/525853.sHtML
- http://map.blog.puhvjy.cn/Article/details/5074891.sHtML
- http://map.blog.nzfnve.cn/Article/details/577328.sHtML
- http://map.blog.nzfnve.cn/Article/details/44712.sHtML
- http://map.blog.nwbbyt.cn/Article/details/257654.sHtML
- http://map.blog.nzfnve.cn/Article/details/42967.sHtML
- http://map.blog.nzfnve.cn/Article/details/0952.sHtML
- http://map.blog.jnjpgf.cn/Article/details/121119.sHtML
- http://map.blog.nzfnve.cn/Article/details/76007.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4343.sHtML
- http://map.blog.nzfnve.cn/Article/details/79365.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7617705.sHtML
- http://map.blog.nwbbyt.cn/Article/details/99157.sHtML
- http://map.blog.puhvjy.cn/Article/details/467067.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1623.sHtML
- http://map.blog.nzfnve.cn/Article/details/6555.sHtML
- http://map.blog.nzfnve.cn/Article/details/4500522.sHtML
- http://map.blog.puhvjy.cn/Article/details/6597.sHtML
- http://map.blog.nzfnve.cn/Article/details/847990.sHtML
- http://map.blog.nzfnve.cn/Article/details/2425.sHtML
- http://map.blog.nzfnve.cn/Article/details/9641.sHtML
- http://map.blog.nzfnve.cn/Article/details/029112.sHtML
- http://map.blog.nzfnve.cn/Article/details/88452.sHtML
- http://map.blog.nwbbyt.cn/Article/details/00883.sHtML
- http://map.blog.nzfnve.cn/Article/details/22831.sHtML
- http://map.blog.nzfnve.cn/Article/details/858978.sHtML
- http://map.blog.puhvjy.cn/Article/details/5233524.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2718.sHtML
- http://map.blog.nzfnve.cn/Article/details/852429.sHtML
- http://map.blog.puhvjy.cn/Article/details/057864.sHtML
- http://map.blog.jnjpgf.cn/Article/details/959920.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6298966.sHtML
- http://map.blog.nwbbyt.cn/Article/details/70500.sHtML
- http://map.blog.nwbbyt.cn/Article/details/737125.sHtML
- http://map.blog.puhvjy.cn/Article/details/600293.sHtML
- http://map.blog.nzfnve.cn/Article/details/1416.sHtML
- http://map.blog.nzfnve.cn/Article/details/3470346.sHtML
- http://map.blog.nzfnve.cn/Article/details/0046120.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4211750.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7671037.sHtML
- http://map.blog.puhvjy.cn/Article/details/190791.sHtML
- http://map.blog.nwbbyt.cn/Article/details/300210.sHtML
- http://map.blog.puhvjy.cn/Article/details/0529.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9889782.sHtML
- http://map.blog.puhvjy.cn/Article/details/098412.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1412004.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1510.sHtML
- http://map.blog.jnjpgf.cn/Article/details/04651.sHtML
- http://map.blog.nzfnve.cn/Article/details/212560.sHtML
- http://map.blog.nzfnve.cn/Article/details/7060.sHtML
- http://map.blog.jnjpgf.cn/Article/details/880093.sHtML
- http://map.blog.puhvjy.cn/Article/details/4860.sHtML
- http://map.blog.nwbbyt.cn/Article/details/316810.sHtML
- http://map.blog.nwbbyt.cn/Article/details/460695.sHtML
- http://map.blog.puhvjy.cn/Article/details/535272.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3293028.sHtML
- http://map.blog.nzfnve.cn/Article/details/4150457.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5589113.sHtML
- http://map.blog.puhvjy.cn/Article/details/044936.sHtML
- http://map.blog.nzfnve.cn/Article/details/036901.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5279.sHtML
- http://map.blog.puhvjy.cn/Article/details/56257.sHtML
- http://map.blog.nwbbyt.cn/Article/details/191809.sHtML
- http://map.blog.jnjpgf.cn/Article/details/449662.sHtML
- http://map.blog.puhvjy.cn/Article/details/3672089.sHtML
- http://map.blog.nwbbyt.cn/Article/details/06726.sHtML
- http://map.blog.nwbbyt.cn/Article/details/885184.sHtML
- http://map.blog.nzfnve.cn/Article/details/6727.sHtML
- http://map.blog.nwbbyt.cn/Article/details/75025.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1787.sHtML
- http://map.blog.nzfnve.cn/Article/details/4113.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1426960.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6712.sHtML
- http://map.blog.puhvjy.cn/Article/details/4969.sHtML
- http://map.blog.puhvjy.cn/Article/details/9264956.sHtML
- http://map.blog.puhvjy.cn/Article/details/2049.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2781.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5812585.sHtML
- http://map.blog.nwbbyt.cn/Article/details/76620.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0264.sHtML
- http://map.blog.nwbbyt.cn/Article/details/95539.sHtML
- http://map.blog.nzfnve.cn/Article/details/4293392.sHtML
- http://map.blog.puhvjy.cn/Article/details/519139.sHtML
- http://map.blog.puhvjy.cn/Article/details/5500348.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7113086.sHtML
- http://map.blog.nzfnve.cn/Article/details/808140.sHtML
- http://map.blog.nwbbyt.cn/Article/details/474094.sHtML
- http://map.blog.puhvjy.cn/Article/details/03952.sHtML
- http://map.blog.nwbbyt.cn/Article/details/38202.sHtML
- http://map.blog.puhvjy.cn/Article/details/59044.sHtML
- http://map.blog.puhvjy.cn/Article/details/854377.sHtML
- http://map.blog.nzfnve.cn/Article/details/8283498.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2927749.sHtML
- http://map.blog.nwbbyt.cn/Article/details/130576.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0541.sHtML
- http://map.blog.nzfnve.cn/Article/details/8276181.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7295.sHtML
- http://map.blog.puhvjy.cn/Article/details/049990.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3560.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7981263.sHtML
- http://map.blog.nzfnve.cn/Article/details/0911918.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2751.sHtML
- http://map.blog.jnjpgf.cn/Article/details/33045.sHtML
- http://map.blog.puhvjy.cn/Article/details/79908.sHtML
- http://map.blog.nzfnve.cn/Article/details/73240.sHtML
- http://map.blog.puhvjy.cn/Article/details/2559260.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4853863.sHtML
- http://map.blog.puhvjy.cn/Article/details/1973.sHtML
- http://map.blog.nzfnve.cn/Article/details/0125301.sHtML
- http://map.blog.nzfnve.cn/Article/details/085527.sHtML
- http://map.blog.nzfnve.cn/Article/details/038143.sHtML
- http://map.blog.nzfnve.cn/Article/details/0029169.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8796865.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3777472.sHtML
- http://map.blog.puhvjy.cn/Article/details/6170640.sHtML
- http://map.blog.puhvjy.cn/Article/details/0658.sHtML
- http://map.blog.puhvjy.cn/Article/details/1033.sHtML
- http://map.blog.puhvjy.cn/Article/details/1603132.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9801.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0615190.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5775038.sHtML
- http://map.blog.puhvjy.cn/Article/details/86556.sHtML
- http://map.blog.nzfnve.cn/Article/details/95265.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7877572.sHtML
- http://map.blog.puhvjy.cn/Article/details/5883.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9479231.sHtML
- http://map.blog.jnjpgf.cn/Article/details/79106.sHtML
- http://map.blog.nzfnve.cn/Article/details/69982.sHtML
- http://map.blog.nwbbyt.cn/Article/details/24033.sHtML
- http://map.blog.puhvjy.cn/Article/details/287357.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4146874.sHtML
- http://map.blog.nwbbyt.cn/Article/details/58496.sHtML
- http://map.blog.jnjpgf.cn/Article/details/03945.sHtML
- http://map.blog.nzfnve.cn/Article/details/5785134.sHtML
- http://map.blog.puhvjy.cn/Article/details/628795.sHtML
- http://map.blog.puhvjy.cn/Article/details/29721.sHtML
- http://map.blog.puhvjy.cn/Article/details/0299412.sHtML
- http://map.blog.puhvjy.cn/Article/details/9659302.sHtML
- http://map.blog.nwbbyt.cn/Article/details/698603.sHtML
- http://map.blog.puhvjy.cn/Article/details/1385292.sHtML
- http://map.blog.puhvjy.cn/Article/details/1185288.sHtML
- http://map.blog.puhvjy.cn/Article/details/104952.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5923628.sHtML
- http://map.blog.puhvjy.cn/Article/details/2087014.sHtML
- http://map.blog.nzfnve.cn/Article/details/982082.sHtML
- http://map.blog.puhvjy.cn/Article/details/7645357.sHtML
- http://map.blog.puhvjy.cn/Article/details/48658.sHtML
- http://map.blog.puhvjy.cn/Article/details/557672.sHtML
- http://map.blog.nzfnve.cn/Article/details/9384.sHtML
- http://map.blog.nzfnve.cn/Article/details/3238096.sHtML
- http://map.blog.nwbbyt.cn/Article/details/90229.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5551838.sHtML
- http://map.blog.puhvjy.cn/Article/details/7960.sHtML
- http://map.blog.puhvjy.cn/Article/details/4246006.sHtML
- http://map.blog.nzfnve.cn/Article/details/077482.sHtML
- http://map.blog.nwbbyt.cn/Article/details/58636.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9051.sHtML
- http://map.blog.nwbbyt.cn/Article/details/99004.sHtML
- http://map.blog.jnjpgf.cn/Article/details/90014.sHtML
- http://map.blog.nzfnve.cn/Article/details/6839.sHtML
- http://map.blog.jnjpgf.cn/Article/details/34936.sHtML
- http://map.blog.jnjpgf.cn/Article/details/051107.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7931.sHtML
- http://map.blog.nzfnve.cn/Article/details/131258.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4161167.sHtML
- http://map.blog.nwbbyt.cn/Article/details/21073.sHtML
- http://map.blog.puhvjy.cn/Article/details/460508.sHtML
- http://map.blog.nzfnve.cn/Article/details/09689.sHtML
- http://map.blog.jnjpgf.cn/Article/details/15071.sHtML
- http://map.blog.puhvjy.cn/Article/details/7396027.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9308.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8948.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3864057.sHtML
- http://map.blog.nzfnve.cn/Article/details/77462.sHtML
- http://map.blog.nzfnve.cn/Article/details/87923.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6428.sHtML
- http://map.blog.nwbbyt.cn/Article/details/13614.sHtML
- http://map.blog.nzfnve.cn/Article/details/0571.sHtML
- http://map.blog.puhvjy.cn/Article/details/368109.sHtML
- http://map.blog.nzfnve.cn/Article/details/113995.sHtML
- http://map.blog.nzfnve.cn/Article/details/68338.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7257461.sHtML
- http://map.blog.nzfnve.cn/Article/details/312950.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1280.sHtML
- http://map.blog.nzfnve.cn/Article/details/5367.sHtML
- http://map.blog.puhvjy.cn/Article/details/34298.sHtML
- http://map.blog.jnjpgf.cn/Article/details/866493.sHtML
- http://map.blog.puhvjy.cn/Article/details/04096.sHtML
- http://map.blog.nwbbyt.cn/Article/details/89395.sHtML
- http://map.blog.nzfnve.cn/Article/details/3528.sHtML
- http://map.blog.jnjpgf.cn/Article/details/747180.sHtML
- http://map.blog.nwbbyt.cn/Article/details/272904.sHtML
- http://map.blog.nzfnve.cn/Article/details/6493.sHtML
- http://map.blog.nzfnve.cn/Article/details/405409.sHtML
- http://map.blog.jnjpgf.cn/Article/details/91026.sHtML
- http://map.blog.puhvjy.cn/Article/details/21243.sHtML
- http://map.blog.puhvjy.cn/Article/details/551949.sHtML
- http://map.blog.puhvjy.cn/Article/details/4097.sHtML
- http://map.blog.puhvjy.cn/Article/details/2915491.sHtML

## 项目结构

```
webindex-core/
├── app.py                      # Web 服务入口，包含路由与启动逻辑
├── config/
│   ├── default.yaml            # 默认配置（端口、数据库路径、检查间隔）
│   └── production.yaml         # 生产环境覆盖配置（示例）
├── core/
│   ├── __init__.py
│   ├── indexer.py              # 核心索引引擎，负责 URL 规范化与存储
│   ├── health.py               # 健康检查子模块，支持并发探测
│   ├── parser.py               # 可选的内容摘要解析器（基于 BeautifulSoup）
│   └── tags.py                 # 标签管理与分类逻辑
├── data/
│   ├── urls_32.txt             # 第 32 批次原始链接列表（当前收录批次）
│   ├── urls_33.txt             # 下一批次待处理列表（模板）
│   └── archive/                # 历史批次归档目录
├── scripts/
│   ├── init_db.py              # 初始化 SQLite 数据表结构
│   ├── import_urls.py          # 从文本文件批量导入链接
│   ├── export_csv.py           # 导出当前全量数据为 CSV
│   └── check_all.py            # 手动触发全量健康检查
├── tests/
│   ├── test_indexer.py         # 索引模块单元测试
│   ├── test_health.py          # 健康检查模块测试（含 mock）
│   └── fixtures/               # 测试用固定数据集
├── docs/                       # 完整文档目录（详见文档导航）
├── requirements.txt            # 生产依赖列表
├── requirements-dev.txt        # 开发额外依赖
└── README.md                   # 本文件
```

## 贡献指南

1. 阅读项目文档与代码风格规范（docs/development.md 与 .black 配置文件），确保对项目架构有基本了解。

2. 在 GitHub Issues 中查找或新建一个待处理任务，说明意图（新增数据源适配器、改进健康检查效率、修复特定 Bug 等），等待维护者确认。

3. Fork 主仓库，创建特性分支（如 feature/add-new-parser），在该分支上进行修改，并确保所有现有测试通过，新增功能需附带对应测试用例。

4. 提交前运行 black 与 pytest 进行格式化和回归测试，确保无风格警告与测试失败。

5. 发起 Pull Request，描述修改内容、影响范围以及测试覆盖情况，等待 Code Review 与合并。

## 常见问题

Q: 导入链接时遇到大量重复记录如何处理？
系统在导入时会自动基于 URL 完整字符串进行去重，同时支持基于域名加文章 ID 的二次去重策略。若仍需手动处理，可使用 scripts/deduplicate.py 工具进行清理，或通过管理面板的“合并重复项”功能操作。

Q: 健康检查显示部分链接不可达，但浏览器可以正常访问，是什么原因？
健康检查模块默认使用 requests 库的默认超时（3 秒）与 User-Agent。部分站点可能对非浏览器 UA 有访问限制或响应较慢。建议在配置文件中调整 timeout 参数，或启用 cookies 与 headers 模拟。若仍失败，可尝试手动将该链接加入白名单排除检查。

Q: 如何从当前数据中筛选出特定域名的所有文章？
可使用命令行工具 scripts/filter_by_domain.py 并指定域名参数，例如 python scripts/filter_by_domain.py --domain map.blog.nwbbyt.cn --output result.txt。在 Web 界面中也可通过搜索框输入 domain:map.blog.nwbbyt.cn 进行快速筛选。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
