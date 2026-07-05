# LinkCatalog

LinkCatalog 是一个面向技术内容聚合与外部资源管理的开源链接汇总系统，专注于对分布式博客、技术文档与知识碎片进行结构化索引与持久化引用。本项目主要服务于技术内容创作者、知识库维护者以及信息检索研究人员，帮助其从大量零散的 URL 中建立可维护、可查询、可审计的外链资产库。

LinkCatalog 并不提供爬虫或内容抓取能力，而是作为外链元数据的管理中间层，提供标准化录入、标签分类、状态检测与批量导出能力。项目定位为技术团队内部的知识外链中台，也可作为个人技术写作素材库的基础设施。

## 功能概览

**多源链接统一录入**：支持从文本文件、CSV、JSON 等多种格式批量导入链接，自动解析 URL 结构并提取域名与路径特征。

**链接状态周期性检测**：对已收录链接进行 HTTP 状态码检查，自动标记失效、跳转或超时链接，并生成可视化报表。

**自定义标签与分类体系**：允许用户为每条链接添加多级标签，支持基于标签的快速筛选与聚合统计。

**全文检索与高级过滤**：基于链接标题、描述、标签、域名、收录时间等多维度条件进行组合检索，支持结果导出。

**收录时间线与版本快照**：记录每次链接变更的操作日志，支持回溯任意时间点的链接集合状态。

**批量导出与集成对接**：支持将链接列表导出为 Markdown、HTML、JSON 与 CSV 格式，便于嵌入文档或与其他系统集成。

**访问频率统计与热度分析**：统计链接被查看或引用的次数，辅助识别高频价值资源。

## 应用场景

技术博客写作素材管理。技术博主在撰写文章时需要引用大量外部资料，LinkCatalog 可帮助其集中保存待引用链接，并为每条链接添加主题标签与备注，避免写作时临时查找或遗忘出处。

团队知识库外链审计。企业内部 Wiki 或文档中心包含大量外部参考链接，随着时间推移部分链接可能失效。LinkCatalog 的周期性检测功能可定期扫描并生成失效报告，协助运维人员及时更新或替换链接。

技术调研与竞品分析归档。在进行技术选型或竞品研究时，调研人员需要收集数十甚至上百个相关链接。LinkCatalog 的批量导入与分类能力可快速建立调研资源池，并通过热度分析筛选出高频访问的核心参考源。

个人书签系统增强替代。对于希望脱离浏览器内置书签管理的高级用户，LinkCatalog 提供更强大的检索、分类与导出能力，可作为自托管书签系统的轻量替代方案。

## 快速开始

以下命令演示了从克隆代码到启动服务的完整流程。

```bash
git clone https://github.com/yourorg/linkcatalog.git
cd linkcatalog
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

上述步骤将在本地启动开发服务器，默认监听 8000 端口。访问 http://localhost:8000 即可进入 LinkCatalog 的 Web 管理界面。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 |
| Django | 4.2 LTS | Web 框架与 ORM 层 |
| PostgreSQL | 14 及以上 | 生产环境推荐数据库，支持 JSONB 字段 |
| Redis | 6.0 及以上 | 用于缓存与异步任务队列 |
| Celery | 5.3 及以上 | 异步执行链接状态检测任务 |
| Node.js | 18 及以上 | 前端静态资源构建工具依赖 |
| Nginx | 1.24 及以上 | 生产环境反向代理与静态文件服务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/quickstart.md | 如何快速搭建开发环境并运行第一个实例 |
| 数据模型 | docs/models.md | 链接、标签、日志等核心表结构与字段说明 |
| 命令行工具 | docs/cli.md | 如何使用 manage.py 进行批量导入、导出与检测 |
| 部署运维 | docs/deployment.md | 生产环境配置、性能调优与监控方案 |

## 资源列表

- http://h5.blog.nzfnve.cn/Article/details/0343.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/33530.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/992011.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/93177.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6377.sHtML
- http://h5.blog.puhvjy.cn/Article/details/00521.sHtML
- http://h5.blog.nzfnve.cn/Article/details/79857.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/139215.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/13794.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/69863.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/665409.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/11924.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/520396.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7136415.sHtML
- http://h5.blog.nzfnve.cn/Article/details/153846.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/62601.sHtML
- http://h5.blog.puhvjy.cn/Article/details/44530.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/391561.sHtML
- http://h5.blog.puhvjy.cn/Article/details/246944.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/76918.sHtML
- http://h5.blog.puhvjy.cn/Article/details/190902.sHtML
- http://h5.blog.nzfnve.cn/Article/details/48503.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6421300.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/642086.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1232.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2612561.sHtML
- http://h5.blog.nzfnve.cn/Article/details/77374.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7315504.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6031.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8815776.sHtML
- http://h5.blog.nzfnve.cn/Article/details/69244.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/13327.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6109528.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9107190.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8121.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5725312.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9590412.sHtML
- http://h5.blog.nzfnve.cn/Article/details/633378.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/36845.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0958.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8796882.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/23914.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/268735.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6957.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/259400.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2504.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9507.sHtML
- http://h5.blog.nzfnve.cn/Article/details/42581.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6280.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/37940.sHtML
- http://h5.blog.puhvjy.cn/Article/details/88178.sHtML
- http://h5.blog.puhvjy.cn/Article/details/64784.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9070867.sHtML
- http://h5.blog.puhvjy.cn/Article/details/626940.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6751438.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9571565.sHtML
- http://h5.blog.nzfnve.cn/Article/details/989801.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0620266.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9231588.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8165260.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/567068.sHtML
- http://h5.blog.nzfnve.cn/Article/details/08299.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0581118.sHtML
- http://h5.blog.nzfnve.cn/Article/details/809002.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0356.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4691.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/007866.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2085.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7208750.sHtML
- http://h5.blog.puhvjy.cn/Article/details/40423.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/645426.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8105.sHtML
- http://h5.blog.puhvjy.cn/Article/details/110330.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6665.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/739772.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5311058.sHtML
- http://h5.blog.nzfnve.cn/Article/details/184394.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8364.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/461379.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/234577.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3423787.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2728.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/273215.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6868.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4718612.sHtML
- http://h5.blog.nzfnve.cn/Article/details/14110.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/17551.sHtML
- http://h5.blog.nzfnve.cn/Article/details/868906.sHtML
- http://h5.blog.puhvjy.cn/Article/details/119027.sHtML
- http://h5.blog.nzfnve.cn/Article/details/58978.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6445391.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/858518.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8304232.sHtML
- http://h5.blog.nzfnve.cn/Article/details/1947913.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/493465.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/641615.sHtML
- http://h5.blog.nzfnve.cn/Article/details/94338.sHtML
- http://h5.blog.nzfnve.cn/Article/details/84237.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5622842.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7495793.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5548083.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/17578.sHtML
- http://h5.blog.puhvjy.cn/Article/details/999956.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5703009.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/59973.sHtML
- http://h5.blog.nzfnve.cn/Article/details/10634.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/900249.sHtML
- http://h5.blog.puhvjy.cn/Article/details/37447.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/976663.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4025340.sHtML
- http://h5.blog.puhvjy.cn/Article/details/38965.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9299.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7765.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3451.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/601259.sHtML
- http://h5.blog.puhvjy.cn/Article/details/41546.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9388.sHtML
- http://h5.blog.nzfnve.cn/Article/details/819617.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4859.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/675028.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6341683.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/404398.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7806.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6700735.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4081504.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/382004.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3053218.sHtML
- http://h5.blog.puhvjy.cn/Article/details/16928.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1830.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2667.sHtML
- http://h5.blog.nzfnve.cn/Article/details/26748.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3801.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/64429.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/57467.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0802414.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/264793.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1320.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1184520.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/21021.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0636867.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2597448.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/179216.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2596.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3454.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3799850.sHtML
- http://h5.blog.nzfnve.cn/Article/details/35369.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/708616.sHtML
- http://h5.blog.puhvjy.cn/Article/details/611360.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/876041.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0989.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3765220.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3213900.sHtML
- http://h5.blog.puhvjy.cn/Article/details/99228.sHtML
- http://h5.blog.puhvjy.cn/Article/details/84101.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5555.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6611.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8523.sHtML
- http://h5.blog.nzfnve.cn/Article/details/910277.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4051.sHtML
- http://h5.blog.nzfnve.cn/Article/details/408895.sHtML
- http://h5.blog.nzfnve.cn/Article/details/126489.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8770.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2710.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2811.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9279295.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/09839.sHtML
- http://h5.blog.puhvjy.cn/Article/details/94614.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2508670.sHtML
- http://h5.blog.nzfnve.cn/Article/details/896902.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9428.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9820.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6196.sHtML
- http://h5.blog.nzfnve.cn/Article/details/529076.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/533907.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/980850.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/06536.sHtML
- http://h5.blog.puhvjy.cn/Article/details/17339.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6816808.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/63156.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/51418.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9444.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6968.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2754270.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0282.sHtML
- http://h5.blog.nzfnve.cn/Article/details/49431.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5530.sHtML
- http://h5.blog.nzfnve.cn/Article/details/09639.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6653.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7447.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/183292.sHtML
- http://h5.blog.puhvjy.cn/Article/details/200398.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/21769.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5274.sHtML
- http://h5.blog.nzfnve.cn/Article/details/65110.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/41482.sHtML
- http://h5.blog.puhvjy.cn/Article/details/749071.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5427729.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/272620.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/91877.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0803441.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9448.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0906681.sHtML
- http://h5.blog.puhvjy.cn/Article/details/36997.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/590709.sHtML
- http://h5.blog.nzfnve.cn/Article/details/29900.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8318.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8847.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3821084.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3093396.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7991.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3270.sHtML
- http://h5.blog.puhvjy.cn/Article/details/47129.sHtML
- http://h5.blog.nzfnve.cn/Article/details/497804.sHtML
- http://h5.blog.nzfnve.cn/Article/details/203085.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7321.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1650.sHtML
- http://h5.blog.puhvjy.cn/Article/details/710767.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/044990.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0684051.sHtML
- http://h5.blog.nzfnve.cn/Article/details/70890.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/483810.sHtML
- http://h5.blog.nzfnve.cn/Article/details/615223.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6565.sHtML
- http://h5.blog.puhvjy.cn/Article/details/818369.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2371.sHtML
- http://h5.blog.nzfnve.cn/Article/details/077626.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/635581.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/019199.sHtML
- http://h5.blog.nzfnve.cn/Article/details/657452.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0674.sHtML
- http://h5.blog.nzfnve.cn/Article/details/376349.sHtML
- http://h5.blog.nzfnve.cn/Article/details/22416.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7255623.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1211.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1786458.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4174.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7113545.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5950.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/27465.sHtML
- http://h5.blog.nzfnve.cn/Article/details/826238.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5355.sHtML
- http://h5.blog.puhvjy.cn/Article/details/56000.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4909261.sHtML
- http://h5.blog.puhvjy.cn/Article/details/76364.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1323.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4068.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/445460.sHtML
- http://h5.blog.nzfnve.cn/Article/details/275103.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8797287.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7300.sHtML

## 项目结构

```
linkcatalog/
├── manage.py                      # Django 项目管理入口
├── requirements.txt               # Python 依赖清单
├── config/                        # 项目全局配置目录
│   ├── settings.py               # 基础配置（数据库、中间件、应用）
│   ├── settings_prod.py          # 生产环境配置覆盖
│   └── celery.py                 # Celery 异步任务配置
├── apps/                          # 所有自定义应用存放目录
│   ├── links/                    # 链接核心数据模块
│   │   ├── models.py             # Link, Tag, StatusCheck 数据模型
│   │   ├── views.py              # 链接列表、详情、检索视图
│   │   ├── serializers.py        # DRF 序列化器
│   │   └── tasks.py              # 状态检测异步任务
│   ├── checks/                   # 链接健康检查模块
│   │   ├── http_checker.py       # HTTP 状态码检测逻辑
│   │   └── scheduler.py          # 定时调度配置
│   └── exports/                  # 数据导出模块
│       ├── markdown.py           # Markdown 格式导出器
│       ├── json_exporter.py      # JSON 格式导出器
│       └── csv_exporter.py       # CSV 格式导出器
├── static/                        # 静态资源文件
│   ├── css/                      # 样式表文件
│   └── js/                       # 前端 JavaScript 脚本
├── templates/                     # Django 模板文件
│   ├── base.html                 # 基础模板
│   └── links/                    # 链接相关页面模板
├── docs/                          # 项目文档目录
│   ├── quickstart.md             # 快速入门指南
│   ├── models.md                 # 数据模型详解
│   ├── cli.md                    # 命令行工具参考
│   └── deployment.md             # 部署运维文档
├── scripts/                       # 运维与辅助脚本
│   ├── import_csv.py             # CSV 批量导入脚本
│   └── export_all.py             # 全量导出脚本
└── tests/                         # 单元测试与集成测试
    ├── test_models.py            # 模型层测试
    └── test_api.py               # API 接口测试
```

## 贡献指南

贡献者请先阅读本指南，并遵守项目行为准则。

第一，在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。创建新的功能分支，分支名称应反映本次修改的类型与内容，例如 feature/tag-filter 或 fix/export-encoding。

第二，编写或修改代码时，请确保所有新增或变更的代码均包含对应的单元测试，测试覆盖率不低于百分之八十。运行现有测试套件确保未引入回归缺陷。

第三，提交前执行代码格式化工具 black 与 flake8 检查，保持代码风格与项目现有代码一致。提交信息应遵循约定式提交规范，使用 fix、feat、docs、refactor 等前缀。

第四，发起 Pull Request 到 main 分支，在 PR 描述中清晰说明本次修改的目的、实现方式以及影响范围。项目维护者将在三个工作日内进行审查并反馈。

## 常见问题

问题：LinkCatalog 是否提供链接内容的全文搜索？

答：不提供。LinkCatalog 仅索引链接自身的元数据，包括 URL、标题、描述、标签、收录时间等，并不抓取或存储目标页面的正文内容。如需对链接指向的内容进行检索，建议配合专门的搜索引擎或文档管理系统使用。

问题：链接状态检测是否会频繁请求目标服务器？

答：检测频率由用户配置。默认情况下，系统每二十四小时对所有链接进行一次状态检查。检测请求头中设置了合理的 User-Agent 与超时时间，避免对目标服务器造成压力。用户可根据服务器负载情况调整检测间隔或禁用自动检测。

问题：如何迁移已收录的链接数据到另一台服务器？

答：使用内置的导出功能将链接数据导出为 JSON 或 CSV 格式，在新服务器上完成安装后通过导入命令即可恢复全部数据。导出与导入命令的详细用法请参考 docs/cli.md 文档。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
