# WebArchive Link Aggregator

WebArchive Link Aggregator 是一个面向技术内容聚合与历史文章检索的开源外链管理工具，旨在帮助开发者、技术博主与内容研究者系统化地收集、分类和回溯分散在多个博客站点中的技术文章。项目本身不生产内容，而是通过结构化的链接索引机制，将来自多个域名下的海量文章条目统一归入可查询、可导出、可扩展的本地知识库。

本项目主要服务于需要长期维护技术资料库的研发团队、个人知识管理者以及内容运营人员。通过简单的命令行操作，用户可以将大批量分散的 URL 资源导入本地 SQLite 数据库，并利用内置的标签系统与全文检索功能快速定位历史文章。项目定位为轻量级、无外部依赖的外链数据中台，适用于每日处理数百条新增链接的中等规模使用场景。

## 功能概览

批量链接导入：支持从纯文本文件、CSV 或标准输入中一次性读取数百条 URL，自动去重并存入本地存储引擎。

域名自动归类：系统根据 URL 中的二级域名自动划分文章来源，生成按域名分组的统计视图，便于识别内容分布。

文章元数据抽取：对每条链接尝试发起 HEAD 请求以获取响应头信息，并提取内容类型、最后修改时间等基础元数据，丰富索引维度。

自定义标签系统：用户可为任意链接添加多个自定义标签，支持按标签组合筛选文章，实现跨域名的主题聚合。

全文检索：基于 SQLite FTS5 扩展构建的轻量级全文检索引擎，支持对文章标题、描述及备注字段进行模糊匹配查询。

数据导入导出：内置 JSON 与 CSV 格式的导入导出命令，便于与其他数据处理工具（如 Pandas、JQ）进行集成。

定期更新检测：通过计划任务或手动触发的方式，对已入库的链接进行可用性检查，标记失效链接并生成报告。

## 应用场景

技术博客归档整理：对于长期阅读多个技术博客的开发者，可以使用本工具将各博客平台的历史文章链接统一收集，并按编程语言、框架或主题打上标签，构建个人技术资料库。后续检索时无需逐一访问原站，直接通过本地查询即可获得目标文章链接。

内容运营选题分析：内容团队在策划新选题时，可将竞品博客或行业媒体的文章链接导入系统，通过域名统计与标签聚合功能快速了解近期热点话题分布情况，为选题方向提供数据参考。

知识库外部链接管理：企业或组织内部的知识库通常会引用大量外部技术文章，这些外部链接容易随站点改版而失效。本工具可定期对知识库中的所有外链进行可用性检测，及时通知维护人员更新或替换失效链接，保障知识库质量。

学术文献参考整理：研究人员在撰写综述或论文时，需要整理大量网络参考文献。本工具提供的批量导入与标签分类功能可协助快速建立参考链接索引，并在项目周期内持续跟踪链接状态，避免提交前发现大量引用链接无法访问。

## 快速开始

以下命令演示了从克隆仓库到完成首次链接导入的完整流程。请确保在执行前已安装 Git 与 Python 3.8 及以上版本。

```bash
git clone https://github.com/your-username/webarchive-link-aggregator.git
cd webarchive-link-aggregator
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python wla.py import --file samples/links.txt
```

首次运行时，系统会自动在当前目录下创建 `data/` 文件夹，并初始化 SQLite 数据库文件 `aggregator.db`。导入完成后，可通过 `python wla.py list --limit 20` 命令查看已导入的链接列表。如需从标准输入导入，可使用 `cat links.txt | python wla.py import --stdin`。

## 安装要求

本项目设计为无外部服务依赖的纯本地应用，所有数据均存储在本地文件系统中。以下表格列出了运行所需的基础环境与可选组件。

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8.0 及以上 | 核心运行环境，低于 3.8 版本将无法使用类型注解特性 |
| SQLite | 3.35.0 及以上 | 内置数据库引擎，FTS5 全文检索扩展需要该版本支持 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装 requirements.txt 中列出的依赖 |
| Git | 2.25.0 及以上 | 用于克隆仓库及后续版本更新，非运行时必需但建议安装 |
| curl | 7.68.0 及以上 | 可选组件，用于外部链接可用性检测，若无则使用 Python urllib 回退 |
| jq | 1.6 及以上 | 可选组件，用于命令行下对 JSON 导出结果进行格式化查看 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/usage/import.md | 如何批量导入链接、支持哪些输入格式、如何处理重复条目 |
| 用户手册 | docs/usage/search.md | 如何使用全文检索语法、标签筛选条件如何组合 |
| 用户手册 | docs/usage/export.md | 导出数据支持哪些格式、如何自定义导出字段 |
| 运维指南 | docs/ops/health-check.md | 如何配置定期链接检测、检测报告如何解读 |
| 开发指南 | docs/dev/architecture.md | 项目的模块划分、数据流向及扩展点设计 |
| 开发指南 | docs/dev/db-schema.md | 数据库表结构说明、索引设计及迁移策略 |
| 参考文档 | docs/ref/cli-commands.md | 所有命令行子命令的完整参数列表与示例 |

## 资源列表

- http://h5.blog.nzfnve.cn/Article/details/3606.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9614.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5962756.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/809531.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6438737.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1104.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2774.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/774211.sHtML
- http://h5.blog.nzfnve.cn/Article/details/284724.sHtML
- http://h5.blog.puhvjy.cn/Article/details/13906.sHtML
- http://h5.blog.nzfnve.cn/Article/details/370062.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/924611.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9003269.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1195849.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3616267.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8988487.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7286988.sHtML
- http://h5.blog.nzfnve.cn/Article/details/34069.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5834.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3767.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6839.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/63944.sHtML
- http://h5.blog.nzfnve.cn/Article/details/34129.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3941937.sHtML
- http://h5.blog.nzfnve.cn/Article/details/634380.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/25996.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/336300.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9990.sHtML
- http://h5.blog.puhvjy.cn/Article/details/315086.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9884.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0533720.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6236.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/240675.sHtML
- http://h5.blog.puhvjy.cn/Article/details/06463.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2950.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6187.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7737833.sHtML
- http://h5.blog.puhvjy.cn/Article/details/24254.sHtML
- http://h5.blog.nzfnve.cn/Article/details/68714.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/615839.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4739.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/141579.sHtML
- http://h5.blog.nzfnve.cn/Article/details/21240.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7063356.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/255642.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/729336.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3258.sHtML
- http://h5.blog.puhvjy.cn/Article/details/563292.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3420013.sHtML
- http://h5.blog.nzfnve.cn/Article/details/69124.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8104135.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/525853.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5074891.sHtML
- http://h5.blog.nzfnve.cn/Article/details/577328.sHtML
- http://h5.blog.nzfnve.cn/Article/details/44712.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/257654.sHtML
- http://h5.blog.nzfnve.cn/Article/details/42967.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0952.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/121119.sHtML
- http://h5.blog.nzfnve.cn/Article/details/76007.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4343.sHtML
- http://h5.blog.nzfnve.cn/Article/details/79365.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7617705.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/99157.sHtML
- http://h5.blog.puhvjy.cn/Article/details/467067.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1623.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6555.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4500522.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6597.sHtML
- http://h5.blog.nzfnve.cn/Article/details/847990.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2425.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9641.sHtML
- http://h5.blog.nzfnve.cn/Article/details/029112.sHtML
- http://h5.blog.nzfnve.cn/Article/details/88452.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/00883.sHtML
- http://h5.blog.nzfnve.cn/Article/details/22831.sHtML
- http://h5.blog.nzfnve.cn/Article/details/858978.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5233524.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2718.sHtML
- http://h5.blog.nzfnve.cn/Article/details/852429.sHtML
- http://h5.blog.puhvjy.cn/Article/details/057864.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/959920.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6298966.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/70500.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/737125.sHtML
- http://h5.blog.puhvjy.cn/Article/details/600293.sHtML
- http://h5.blog.nzfnve.cn/Article/details/1416.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3470346.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0046120.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4211750.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7671037.sHtML
- http://h5.blog.puhvjy.cn/Article/details/190791.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/300210.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0529.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9889782.sHtML
- http://h5.blog.puhvjy.cn/Article/details/098412.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1412004.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1510.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/04651.sHtML
- http://h5.blog.nzfnve.cn/Article/details/212560.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7060.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/880093.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4860.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/316810.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/460695.sHtML
- http://h5.blog.puhvjy.cn/Article/details/535272.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3293028.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4150457.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5589113.sHtML
- http://h5.blog.puhvjy.cn/Article/details/044936.sHtML
- http://h5.blog.nzfnve.cn/Article/details/036901.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5279.sHtML
- http://h5.blog.puhvjy.cn/Article/details/56257.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/191809.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/449662.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3672089.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/06726.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/885184.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6727.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/75025.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1787.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4113.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1426960.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6712.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4969.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9264956.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2049.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2781.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5812585.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/76620.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0264.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/95539.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4293392.sHtML
- http://h5.blog.puhvjy.cn/Article/details/519139.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5500348.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7113086.sHtML
- http://h5.blog.nzfnve.cn/Article/details/808140.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/474094.sHtML
- http://h5.blog.puhvjy.cn/Article/details/03952.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/38202.sHtML
- http://h5.blog.puhvjy.cn/Article/details/59044.sHtML
- http://h5.blog.puhvjy.cn/Article/details/854377.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8283498.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2927749.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/130576.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0541.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8276181.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7295.sHtML
- http://h5.blog.puhvjy.cn/Article/details/049990.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3560.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7981263.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0911918.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2751.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/33045.sHtML
- http://h5.blog.puhvjy.cn/Article/details/79908.sHtML
- http://h5.blog.nzfnve.cn/Article/details/73240.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2559260.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4853863.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1973.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0125301.sHtML
- http://h5.blog.nzfnve.cn/Article/details/085527.sHtML
- http://h5.blog.nzfnve.cn/Article/details/038143.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0029169.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8796865.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3777472.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6170640.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0658.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1033.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1603132.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9801.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0615190.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5775038.sHtML
- http://h5.blog.puhvjy.cn/Article/details/86556.sHtML
- http://h5.blog.nzfnve.cn/Article/details/95265.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7877572.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5883.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9479231.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/79106.sHtML
- http://h5.blog.nzfnve.cn/Article/details/69982.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/24033.sHtML
- http://h5.blog.puhvjy.cn/Article/details/287357.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4146874.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/58496.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/03945.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5785134.sHtML
- http://h5.blog.puhvjy.cn/Article/details/628795.sHtML
- http://h5.blog.puhvjy.cn/Article/details/29721.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0299412.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9659302.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/698603.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1385292.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1185288.sHtML
- http://h5.blog.puhvjy.cn/Article/details/104952.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5923628.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2087014.sHtML
- http://h5.blog.nzfnve.cn/Article/details/982082.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7645357.sHtML
- http://h5.blog.puhvjy.cn/Article/details/48658.sHtML
- http://h5.blog.puhvjy.cn/Article/details/557672.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9384.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3238096.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/90229.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5551838.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7960.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4246006.sHtML
- http://h5.blog.nzfnve.cn/Article/details/077482.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/58636.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9051.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/99004.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/90014.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6839.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/34936.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/051107.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7931.sHtML
- http://h5.blog.nzfnve.cn/Article/details/131258.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4161167.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/21073.sHtML
- http://h5.blog.puhvjy.cn/Article/details/460508.sHtML
- http://h5.blog.nzfnve.cn/Article/details/09689.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/15071.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7396027.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9308.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8948.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3864057.sHtML
- http://h5.blog.nzfnve.cn/Article/details/77462.sHtML
- http://h5.blog.nzfnve.cn/Article/details/87923.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6428.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/13614.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0571.sHtML
- http://h5.blog.puhvjy.cn/Article/details/368109.sHtML
- http://h5.blog.nzfnve.cn/Article/details/113995.sHtML
- http://h5.blog.nzfnve.cn/Article/details/68338.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7257461.sHtML
- http://h5.blog.nzfnve.cn/Article/details/312950.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1280.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5367.sHtML
- http://h5.blog.puhvjy.cn/Article/details/34298.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/866493.sHtML
- http://h5.blog.puhvjy.cn/Article/details/04096.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/89395.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3528.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/747180.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/272904.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6493.sHtML
- http://h5.blog.nzfnve.cn/Article/details/405409.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/91026.sHtML
- http://h5.blog.puhvjy.cn/Article/details/21243.sHtML
- http://h5.blog.puhvjy.cn/Article/details/551949.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4097.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2915491.sHtML

## 项目结构

项目采用模块化分层设计，核心逻辑与命令行入口分离，便于单元测试与功能扩展。以下为项目根目录下的主要目录与文件布局：

```
webarchive-link-aggregator/
├── wla.py                         # 命令行主入口，注册所有子命令
├── requirements.txt               # Python 依赖列表 (requests, click, python-dotenv)
├── setup.py                       # 打包安装配置文件
├── data/                          # 数据存储目录 (运行时自动生成)
│   ├── aggregator.db              # SQLite 主数据库文件
│   └── cache/                     # HTTP 请求缓存目录
├── src/                           # 核心源码包
│   ├── __init__.py
│   ├── cli/                       # 命令行子命令模块
│   │   ├── import_cmd.py          # 导入命令实现
│   │   ├── export_cmd.py          # 导出命令实现
│   │   ├── search_cmd.py          # 搜索命令实现
│   │   └── health_cmd.py          # 健康检查命令实现
│   ├── core/                      # 核心业务逻辑
│   │   ├── engine.py              # 数据库引擎与连接管理
│   │   ├── link.py                # 链接实体类与验证逻辑
│   │   ├── indexer.py             # 全文索引构建与查询
│   │   └── fetcher.py             # HTTP 元数据抓取器
│   └── utils/                     # 通用工具函数
│       ├── logger.py              # 日志配置与格式化输出
│       ├── validator.py           # URL 格式校验与域名提取
│       └── dedup.py               # 基于内容特征的去重算法
├── tests/                         # 单元测试与集成测试
│   ├── test_engine.py
│   ├── test_link.py
│   └── fixtures/                  # 测试用数据固件
├── docs/                          # 完整文档目录
│   ├── usage/                     # 用户手册
│   ├── ops/                       # 运维指南
│   ├── dev/                       # 开发指南
│   └── ref/                       # 参考文档
└── samples/                       # 示例数据文件
    ├── links.txt                  # 纯文本链接示例
    └── sample_import.csv          # CSV 格式导入示例
```

## 贡献指南

本项目的成长依赖于社区的参与。无论是报告缺陷、提交代码还是完善文档，我们都欢迎各类形式的贡献。请遵循以下步骤开始您的贡献之旅。

1. 查阅现有议题与开发路线图：在提交新功能或修复之前，请先访问 GitHub Issues 页面查看是否存在相关的讨论或正在进行的工作，避免重复劳动。对于较大规模的功能变更，建议先创建一个议题进行设计讨论。

2. 派生仓库并创建特性分支：从主仓库派生一份代码到您的个人账户下，然后基于 main 分支创建一个新的特性分支，分支命名建议使用 `feat/功能简述` 或 `fix/问题简述` 格式，以便于识别。

3. 编写代码与单元测试：所有新功能必须包含对应的单元测试，测试覆盖率不应低于 80%。代码风格遵循 PEP 8 规范，提交前请运行 `make lint` 进行静态检查。对于涉及数据库操作的变更，请同时编写数据库迁移脚本。

4. 提交变更并签署开发者原产地证书：提交信息采用约定式提交格式，例如 `feat: 添加按域名过滤导出功能`。在 Pull Request 描述中详细说明变更动机、实现方式及测试结果，并确认已签署 DCO。

5. 发起拉取请求并参与代码评审：将特性分支推送到您的派生仓库后，向主仓库的 main 分支发起 Pull Request。项目维护者会在 48 小时内进行首次评审，请及时响应评审意见并修改代码。合并后您的贡献将被列入下一版本的发布说明中。

## 常见问题

项目安装时提示 SQLite 版本过低，如何升级？

SQLite 版本检查是项目启动时的必要步骤。如果系统自带的 SQLite 版本低于 3.35.0，您可以通过以下方式之一解决：在 Linux 系统下使用包管理器安装更新版本，如 `sudo apt-get install sqlite3`（Ubuntu/Debian）或 `sudo yum install sqlite`（RHEL/CentOS）；在 macOS 下使用 Homebrew 安装 `brew install sqlite3` 并确保其位于 PATH 首位；或者使用 Python 的 `pysqlite3` 包作为替代，并在项目配置中指定使用该包。

导入大批量链接时出现内存占用过高怎么办？

对于单次导入超过 5000 条链接的场景，建议使用 `--batch-size` 参数控制每批提交的记录数，默认值为 500。同时可使用 `--no-verify` 选项跳过对链接的实时可用性检测，以降低内存和网络开销。导入完成后，再通过单独的 `health` 命令进行批量检测，该命令采用流式处理方式，不会将全部链接同时载入内存。

如何迁移数据库到另一台机器？

本项目的数据库为单文件 SQLite 格式，迁移时只需将 `data/aggregator.db` 文件复制到目标机器的相同相对路径下即可。如果目标机器的文件系统路径与源机器不同，需要在迁移后修改项目配置文件中的 `DATA_DIR` 环境变量。对于需要跨操作系统迁移的情况（如从 Windows 迁移到 Linux），建议先使用 `export` 命令将数据导出为 JSON 或 CSV 格式，再在目标机器上使用 `import` 命令重新导入，以避免因底层 SQLite 页面大小差异导致的兼容性问题。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
