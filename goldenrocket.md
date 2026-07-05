# MapBlog 外链资源聚合站

MapBlog 是一个面向技术内容聚合与结构化外链管理的开源静态站点生成工具，定位于帮助开发者、技术博主、研究团队以及个人知识管理者将分散在多个博客站点、内容平台、技术社区中的高质量外链资源进行统一抓取、分类归档与全文检索。与传统的书签管理工具或网络收藏夹不同，MapBlog 不仅提供链接存储功能，还内置了基于内容指纹的重复检测、失效链接巡检、访问热度分析以及按域名、时间、内容类型等多维度聚合视图，使得原本孤立的外部链接转化为可持续利用的知识资产。

本项目适用于每日需要处理大量技术资讯的研发工程师、维护技术周报或行业动态的运营人员、从事文献调研与竞品分析的研究型岗位，以及希望构建个人知识体系并对外输出技术资源导航页的独立开发者。MapBlog 不依赖任何外部数据库或云服务，完全基于本地文件系统与纯文本配置运行，既可作为个人桌面工具使用，也可部署为公开的技术资源导航网站。通过本项目的资源列表机制，用户可以定义任意数量的外链集合，系统自动生成分类索引、标签云和时序归档页面，最终输出为高度可定制的静态 HTML 页面集合，方便托管至任意 Web 服务器或 CDN 服务。

## 功能概览

**多源外链批量导入**：支持从 CSV、JSON、Markdown 列表及纯文本行格式批量导入外链记录，自动解析 URL、标题、来源域名与时间戳，同时保留原始 URL 的大小写、协议类型与路径结构，确保重定向与大小写敏感场景下的访问准确性。

**内容指纹去重与增量更新**：基于 URL 规范化与页面摘要哈希的双重去重策略，在导入新批次链接时自动识别已存在记录，避免重复收录；支持增量追加模式，适用于持续订阅的资讯源或定期更新的技术动态列表。

**失效链接巡检与状态标注**：内置异步 HTTP 探测模块，支持配置请求超时、重试次数与状态码白名单，定期对已收录链接进行可达性检查，将异常链接标记为失效并生成巡检报告，便于维护者及时清理或更新。

**多维度分类与标签系统**：每条外链可归属至项目、主题、来源站点、内容类型等多个独立分类维度，系统自动生成按分类筛选的索引页面；支持自由标签附加，标签云根据使用频次自动调整权重。

**时序归档与变更日志**：按收录日期、更新日期和访问次数生成时间轴视图，支持按月、周、日聚合并展示新增趋势；所有导入、删除、状态变更操作均记录至本地变更日志文件，便于追溯与回滚。

**全文检索与快速定位**：针对 URL、标题、描述文本及扩展备注构建轻量级倒排索引，支持布尔表达式与通配符查询，检索结果按相关度与时间权重混合排序，帮助用户在海量外链中迅速定位目标资源。

**静态站点生成与主题切换**：将全部外链数据与元信息渲染为独立静态 HTML 页面，内置多套响应式布局主题，支持自定义 CSS 与模板变量；输出目录结构清晰，可直接部署至 Nginx、Apache、GitHub Pages 或 CloudFlare Pages。

## 应用场景

技术文档团队维护对外参考链接库。技术文档编写过程中需要引用大量外部规范、标准文档、开源项目地址与社区讨论帖，MapBlog 可作为团队内部的统一外链登记系统，文档撰写者可通过分类索引快速获取准确参考链接，同时避免同一链接在不同文档中被重复引用或版本不一致。

研发工程师构建个人技术雷达。每天浏览技术资讯、GitHub 趋势、论文预印本与开发者博客后，可将有价值的外链录入 MapBlog 并标记所属技术领域、阅读状态与重要程度，定期回顾已收录链接，形成个人技术视野的持续积累与迭代。

技术社区或资讯平台运营方搭建资源导航页。运营人员可将优质投稿、合作方内容、历史精选文章及外部工具整理为多个主题导航页面，通过 MapBlog 自动生成分类聚合视图，降低手动维护 HTML 模板的工作量，同时使资源展示形式统一、更新流程标准化。

## 快速开始

以下命令演示了从 GitHub 克隆 MapBlog 仓库、安装 Python 依赖并执行首次导入与站点生成的完整流程。请确保系统已安装 Python 3.9 及以上版本与 Git。

```bash
git clone https://github.com/mapblog/mapblog-core.git
cd mapblog-core
pip install -r requirements.txt
cp config.example.yaml config.yaml
python mapblog.py import --source resources/batch_28.txt --tag "batch-28"
python mapblog.py check --timeout 5 --retry 2
python mapblog.py build --output ./public
```

执行上述命令后，`resources/batch_28.txt` 中的全部外链将被导入系统，经过失效探测后渲染至 `public` 目录，用户可通过本地 HTTP 服务器预览生成结果。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 核心运行环境，用于执行导入、检查、构建与检索逻辑 |
| pip | 22.0 及以上 | Python 包管理器，用于安装 requirements.txt 中声明的第三方库 |
| Git | 2.25 及以上 | 用于克隆仓库及后续拉取上游更新，非运行强制依赖但推荐安装 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端库，用于并发执行外链可达性探测 |
| pyyaml | 6.0.0 及以上 | YAML 配置文件解析器，用于读取站点元数据与分类映射规则 |
| jinja2 | 3.1.0 及以上 | 模板渲染引擎，用于将外链数据与 HTML 模板结合生成静态页面 |
| markdown | 3.5.0 及以上 | 可选依赖，用于将外链描述中的 Markdown 文本转换为 HTML 富文本 |
| watchdog | 3.0.0 及以上 | 可选依赖，用于开发模式下监听资源文件变更并自动重新构建 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何在三分钟内完成首次外链导入并生成静态站点；配置文件中最少需要定义哪些字段 |
| 导入与格式 | docs/import-formats.md | 支持哪些外链输入格式；如何处理带有查询参数和锚点的复杂 URL；批量导入时如何避免重复 |
| 分类与标签 | docs/taxonomy.md | 如何自定义分类层级；标签云的计算逻辑是什么；能否为不同分类指定不同的输出模板 |
| 巡检与维护 | docs/health-check.md | 失效链接的检测频率如何配置；检测结果如何导出；如何忽略特定域名的超时错误 |
| 站点定制 | docs/customization.md | 如何替换内置主题；模板变量完整列表在哪里；如何添加自定义元数据字段并在页面中展示 |
| API 参考 | docs/api-reference.md | 核心模块的函数签名与参数说明；如何通过命令行参数覆盖配置文件中的选项 |

## 资源列表

- http://map.blog.jnjpgf.cn/Article/details/2771694.sHtML
- http://map.blog.nzfnve.cn/Article/details/8273897.sHtML
- http://map.blog.nzfnve.cn/Article/details/666956.sHtML
- http://map.blog.puhvjy.cn/Article/details/1242.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7675.sHtML
- http://map.blog.jnjpgf.cn/Article/details/616215.sHtML
- http://map.blog.nzfnve.cn/Article/details/40406.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8960.sHtML
- http://map.blog.nwbbyt.cn/Article/details/693603.sHtML
- http://map.blog.puhvjy.cn/Article/details/5074.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3252764.sHtML
- http://map.blog.puhvjy.cn/Article/details/841445.sHtML
- http://map.blog.jnjpgf.cn/Article/details/193694.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0963.sHtML
- http://map.blog.puhvjy.cn/Article/details/969703.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2250784.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0429.sHtML
- http://map.blog.puhvjy.cn/Article/details/944893.sHtML
- http://map.blog.nzfnve.cn/Article/details/135501.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7810809.sHtML
- http://map.blog.puhvjy.cn/Article/details/7818.sHtML
- http://map.blog.nzfnve.cn/Article/details/810448.sHtML
- http://map.blog.jnjpgf.cn/Article/details/662293.sHtML
- http://map.blog.nzfnve.cn/Article/details/23111.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2835625.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5018643.sHtML
- http://map.blog.puhvjy.cn/Article/details/1296700.sHtML
- http://map.blog.nzfnve.cn/Article/details/602612.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3661400.sHtML
- http://map.blog.puhvjy.cn/Article/details/8072.sHtML
- http://map.blog.jnjpgf.cn/Article/details/157288.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3105730.sHtML
- http://map.blog.jnjpgf.cn/Article/details/93144.sHtML
- http://map.blog.nzfnve.cn/Article/details/7611.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9862.sHtML
- http://map.blog.puhvjy.cn/Article/details/891325.sHtML
- http://map.blog.nwbbyt.cn/Article/details/605442.sHtML
- http://map.blog.nzfnve.cn/Article/details/1536355.sHtML
- http://map.blog.puhvjy.cn/Article/details/078813.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0979994.sHtML
- http://map.blog.nzfnve.cn/Article/details/1671249.sHtML
- http://map.blog.puhvjy.cn/Article/details/30740.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6213.sHtML
- http://map.blog.puhvjy.cn/Article/details/5879.sHtML
- http://map.blog.jnjpgf.cn/Article/details/778298.sHtML
- http://map.blog.puhvjy.cn/Article/details/6927.sHtML
- http://map.blog.nzfnve.cn/Article/details/47486.sHtML
- http://map.blog.nzfnve.cn/Article/details/409721.sHtML
- http://map.blog.nzfnve.cn/Article/details/0258.sHtML
- http://map.blog.nwbbyt.cn/Article/details/687999.sHtML
- http://map.blog.jnjpgf.cn/Article/details/51423.sHtML
- http://map.blog.nwbbyt.cn/Article/details/181542.sHtML
- http://map.blog.nzfnve.cn/Article/details/5302.sHtML
- http://map.blog.nwbbyt.cn/Article/details/791072.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6934181.sHtML
- http://map.blog.puhvjy.cn/Article/details/37532.sHtML
- http://map.blog.nzfnve.cn/Article/details/979851.sHtML
- http://map.blog.jnjpgf.cn/Article/details/906141.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4432008.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4363.sHtML
- http://map.blog.jnjpgf.cn/Article/details/33289.sHtML
- http://map.blog.nzfnve.cn/Article/details/1862.sHtML
- http://map.blog.nzfnve.cn/Article/details/70572.sHtML
- http://map.blog.nzfnve.cn/Article/details/8250.sHtML
- http://map.blog.jnjpgf.cn/Article/details/919001.sHtML
- http://map.blog.puhvjy.cn/Article/details/4432.sHtML
- http://map.blog.nwbbyt.cn/Article/details/91289.sHtML
- http://map.blog.nzfnve.cn/Article/details/866363.sHtML
- http://map.blog.puhvjy.cn/Article/details/5409623.sHtML
- http://map.blog.nzfnve.cn/Article/details/3438.sHtML
- http://map.blog.puhvjy.cn/Article/details/3547.sHtML
- http://map.blog.nzfnve.cn/Article/details/9671.sHtML
- http://map.blog.jnjpgf.cn/Article/details/120920.sHtML
- http://map.blog.nzfnve.cn/Article/details/366113.sHtML
- http://map.blog.nzfnve.cn/Article/details/376175.sHtML
- http://map.blog.jnjpgf.cn/Article/details/555482.sHtML
- http://map.blog.nzfnve.cn/Article/details/356237.sHtML
- http://map.blog.nwbbyt.cn/Article/details/02595.sHtML
- http://map.blog.puhvjy.cn/Article/details/95217.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4857994.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8711914.sHtML
- http://map.blog.puhvjy.cn/Article/details/3194.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1703.sHtML
- http://map.blog.puhvjy.cn/Article/details/973518.sHtML
- http://map.blog.jnjpgf.cn/Article/details/79830.sHtML
- http://map.blog.jnjpgf.cn/Article/details/122414.sHtML
- http://map.blog.puhvjy.cn/Article/details/9649.sHtML
- http://map.blog.jnjpgf.cn/Article/details/42462.sHtML
- http://map.blog.nwbbyt.cn/Article/details/036597.sHtML
- http://map.blog.nzfnve.cn/Article/details/59673.sHtML
- http://map.blog.jnjpgf.cn/Article/details/67450.sHtML
- http://map.blog.puhvjy.cn/Article/details/6796.sHtML
- http://map.blog.puhvjy.cn/Article/details/744600.sHtML
- http://map.blog.nzfnve.cn/Article/details/8630817.sHtML
- http://map.blog.puhvjy.cn/Article/details/5839.sHtML
- http://map.blog.puhvjy.cn/Article/details/6419219.sHtML
- http://map.blog.nzfnve.cn/Article/details/21286.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6992.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4167364.sHtML
- http://map.blog.nzfnve.cn/Article/details/9891.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9566.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3131.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0065.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8243955.sHtML
- http://map.blog.puhvjy.cn/Article/details/37094.sHtML
- http://map.blog.puhvjy.cn/Article/details/6823721.sHtML
- http://map.blog.nzfnve.cn/Article/details/49888.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2789.sHtML
- http://map.blog.nwbbyt.cn/Article/details/92088.sHtML
- http://map.blog.nwbbyt.cn/Article/details/410832.sHtML
- http://map.blog.puhvjy.cn/Article/details/0588731.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6320059.sHtML
- http://map.blog.puhvjy.cn/Article/details/1740.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7962.sHtML
- http://map.blog.puhvjy.cn/Article/details/1549589.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3093978.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7517296.sHtML
- http://map.blog.puhvjy.cn/Article/details/53223.sHtML
- http://map.blog.puhvjy.cn/Article/details/763167.sHtML
- http://map.blog.nzfnve.cn/Article/details/1322950.sHtML
- http://map.blog.nzfnve.cn/Article/details/48084.sHtML
- http://map.blog.nzfnve.cn/Article/details/469558.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5232446.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4757091.sHtML
- http://map.blog.nzfnve.cn/Article/details/3029499.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8996.sHtML
- http://map.blog.puhvjy.cn/Article/details/273552.sHtML
- http://map.blog.puhvjy.cn/Article/details/26421.sHtML
- http://map.blog.nzfnve.cn/Article/details/4683.sHtML
- http://map.blog.puhvjy.cn/Article/details/1139.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5574.sHtML
- http://map.blog.nwbbyt.cn/Article/details/181784.sHtML
- http://map.blog.puhvjy.cn/Article/details/64667.sHtML
- http://map.blog.puhvjy.cn/Article/details/66586.sHtML
- http://map.blog.nzfnve.cn/Article/details/0392.sHtML
- http://map.blog.jnjpgf.cn/Article/details/44579.sHtML
- http://map.blog.puhvjy.cn/Article/details/6351597.sHtML
- http://map.blog.puhvjy.cn/Article/details/71224.sHtML
- http://map.blog.nzfnve.cn/Article/details/776251.sHtML
- http://map.blog.nzfnve.cn/Article/details/82670.sHtML
- http://map.blog.puhvjy.cn/Article/details/46894.sHtML
- http://map.blog.puhvjy.cn/Article/details/03879.sHtML
- http://map.blog.puhvjy.cn/Article/details/2324.sHtML
- http://map.blog.jnjpgf.cn/Article/details/665467.sHtML
- http://map.blog.nzfnve.cn/Article/details/4012378.sHtML
- http://map.blog.nzfnve.cn/Article/details/802154.sHtML
- http://map.blog.nwbbyt.cn/Article/details/007900.sHtML
- http://map.blog.nzfnve.cn/Article/details/9600064.sHtML
- http://map.blog.nzfnve.cn/Article/details/19205.sHtML
- http://map.blog.nzfnve.cn/Article/details/3090.sHtML
- http://map.blog.nzfnve.cn/Article/details/6193238.sHtML
- http://map.blog.nzfnve.cn/Article/details/5477826.sHtML
- http://map.blog.nwbbyt.cn/Article/details/47357.sHtML
- http://map.blog.puhvjy.cn/Article/details/38003.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3661.sHtML
- http://map.blog.puhvjy.cn/Article/details/0848680.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9099.sHtML
- http://map.blog.jnjpgf.cn/Article/details/890680.sHtML
- http://map.blog.jnjpgf.cn/Article/details/34041.sHtML
- http://map.blog.nwbbyt.cn/Article/details/857366.sHtML
- http://map.blog.puhvjy.cn/Article/details/9667.sHtML
- http://map.blog.nzfnve.cn/Article/details/2755.sHtML
- http://map.blog.nwbbyt.cn/Article/details/254569.sHtML
- http://map.blog.nwbbyt.cn/Article/details/66203.sHtML
- http://map.blog.nwbbyt.cn/Article/details/182003.sHtML
- http://map.blog.jnjpgf.cn/Article/details/461056.sHtML
- http://map.blog.nzfnve.cn/Article/details/9060895.sHtML
- http://map.blog.nzfnve.cn/Article/details/3532416.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7016849.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5249493.sHtML
- http://map.blog.jnjpgf.cn/Article/details/269737.sHtML
- http://map.blog.nzfnve.cn/Article/details/7710528.sHtML
- http://map.blog.nwbbyt.cn/Article/details/215657.sHtML
- http://map.blog.nzfnve.cn/Article/details/7205.sHtML
- http://map.blog.nzfnve.cn/Article/details/316707.sHtML
- http://map.blog.puhvjy.cn/Article/details/9296679.sHtML
- http://map.blog.nzfnve.cn/Article/details/7286055.sHtML
- http://map.blog.puhvjy.cn/Article/details/60162.sHtML
- http://map.blog.nzfnve.cn/Article/details/20231.sHtML
- http://map.blog.nwbbyt.cn/Article/details/838476.sHtML
- http://map.blog.nzfnve.cn/Article/details/5955.sHtML
- http://map.blog.puhvjy.cn/Article/details/84550.sHtML
- http://map.blog.nzfnve.cn/Article/details/8562.sHtML
- http://map.blog.nwbbyt.cn/Article/details/18017.sHtML
- http://map.blog.jnjpgf.cn/Article/details/05298.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8707.sHtML
- http://map.blog.jnjpgf.cn/Article/details/914607.sHtML
- http://map.blog.jnjpgf.cn/Article/details/453802.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2333608.sHtML
- http://map.blog.puhvjy.cn/Article/details/253592.sHtML
- http://map.blog.puhvjy.cn/Article/details/9666105.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7799627.sHtML
- http://map.blog.puhvjy.cn/Article/details/5408315.sHtML
- http://map.blog.nzfnve.cn/Article/details/2980956.sHtML
- http://map.blog.nzfnve.cn/Article/details/77337.sHtML
- http://map.blog.puhvjy.cn/Article/details/98157.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9235088.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8258.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0338972.sHtML
- http://map.blog.puhvjy.cn/Article/details/8928105.sHtML
- http://map.blog.nzfnve.cn/Article/details/9303.sHtML
- http://map.blog.nzfnve.cn/Article/details/3111.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3874.sHtML
- http://map.blog.puhvjy.cn/Article/details/586135.sHtML
- http://map.blog.jnjpgf.cn/Article/details/59526.sHtML
- http://map.blog.nzfnve.cn/Article/details/00984.sHtML
- http://map.blog.nzfnve.cn/Article/details/7536.sHtML
- http://map.blog.nzfnve.cn/Article/details/6072.sHtML
- http://map.blog.jnjpgf.cn/Article/details/678695.sHtML
- http://map.blog.jnjpgf.cn/Article/details/60161.sHtML
- http://map.blog.nwbbyt.cn/Article/details/204551.sHtML
- http://map.blog.jnjpgf.cn/Article/details/851391.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6566265.sHtML
- http://map.blog.puhvjy.cn/Article/details/2861167.sHtML
- http://map.blog.nzfnve.cn/Article/details/397978.sHtML
- http://map.blog.puhvjy.cn/Article/details/84524.sHtML
- http://map.blog.jnjpgf.cn/Article/details/111344.sHtML
- http://map.blog.nwbbyt.cn/Article/details/06259.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8598.sHtML
- http://map.blog.nzfnve.cn/Article/details/9904659.sHtML
- http://map.blog.jnjpgf.cn/Article/details/595383.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8051371.sHtML
- http://map.blog.nzfnve.cn/Article/details/7408389.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3596.sHtML
- http://map.blog.nwbbyt.cn/Article/details/886510.sHtML
- http://map.blog.jnjpgf.cn/Article/details/862911.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9079041.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2318.sHtML
- http://map.blog.puhvjy.cn/Article/details/201138.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0230340.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9147749.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5810.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7605583.sHtML
- http://map.blog.nzfnve.cn/Article/details/3363602.sHtML
- http://map.blog.puhvjy.cn/Article/details/5721659.sHtML
- http://map.blog.jnjpgf.cn/Article/details/00527.sHtML
- http://map.blog.nzfnve.cn/Article/details/9953.sHtML
- http://map.blog.nwbbyt.cn/Article/details/156704.sHtML
- http://map.blog.puhvjy.cn/Article/details/367480.sHtML
- http://map.blog.jnjpgf.cn/Article/details/046385.sHtML
- http://map.blog.puhvjy.cn/Article/details/32041.sHtML
- http://map.blog.puhvjy.cn/Article/details/7723.sHtML
- http://map.blog.nzfnve.cn/Article/details/50704.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8810257.sHtML
- http://map.blog.nwbbyt.cn/Article/details/44775.sHtML
- http://map.blog.nzfnve.cn/Article/details/4190.sHtML
- http://map.blog.nzfnve.cn/Article/details/01156.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7193.sHtML
- http://map.blog.puhvjy.cn/Article/details/0698.sHtML
- http://map.blog.puhvjy.cn/Article/details/973958.sHtML

## 项目结构

```
mapblog-core/
├── mapblog/                          # 核心 Python 包目录
│   ├── __init__.py                   # 包版本声明与导出接口
│   ├── cli.py                        # 命令行入口，注册子命令与参数解析
│   ├── config.py                     # 配置加载器，读取 YAML 并合并默认值
│   ├── importer/                     # 外链导入子模块
│   │   ├── __init__.py
│   │   ├── base.py                   # 导入器抽象基类，定义规范与校验接口
│   │   ├── csv_reader.py             # CSV 格式解析器，支持自定义分隔符与列映射
│   │   └── text_reader.py            # 纯文本行格式解析器，每行视为一个 URL
│   ├── dedup/                        # 去重与指纹计算子模块
│   │   ├── __init__.py
│   │   ├── fingerprint.py            # 生成 URL 规范化哈希与内容摘要
│   │   └── store.py                  # 基于 SQLite 的已收录指纹存储与查询
│   ├── health/                       # 链接健康检查子模块
│   │   ├── __init__.py
│   │   ├── checker.py                # 异步 HTTP 探测主逻辑，支持并发与限流
│   │   └── reporter.py               # 生成巡检报告 Markdown 文件
│   ├── index/                        # 倒排索引与检索子模块
│   │   ├── __init__.py
│   │   ├── builder.py                # 从外链元数据构建倒排索引
│   │   └── searcher.py               # 执行查询并返回排序后的匹配记录
│   ├── render/                       # 静态站点渲染子模块
│   │   ├── __init__.py
│   │   ├── engine.py                 # Jinja2 模板引擎封装与主题加载
│   │   ├── pages.py                  # 分类、标签、时序等聚合页生成器
│   │   └── assets.py                 # 静态资源复制与路径重写
│   ├── models/                       # 数据模型定义
│   │   ├── __init__.py
│   │   ├── entry.py                  # 外链条目数据结构，包含 URL、标题、标签等字段
│   │   └── manifest.py               # 批次清单与变更日志序列化
│   └── utils/                        # 工具函数集合
│       ├── __init__.py
│       ├── url.py                    # URL 规范化、解析与域名提取
│       └── time.py                   # 时间戳格式化与时区转换辅助函数
├── config.example.yaml               # 示例配置文件，包含所有可调参数与默认值
├── requirements.txt                  # 生产环境依赖列表，固定版本号
├── requirements-dev.txt              # 开发环境额外依赖，包含测试与代码检查工具
├── setup.py                          # 包安装脚本，声明入口点与元数据
├── README.md                         # 项目说明文档（即本文档）
├── CHANGELOG.md                      # 版本变更历史记录
├── LICENSE                           # MIT 许可证全文
├── tests/                            # 单元测试与集成测试目录
│   ├── test_importer.py
│   ├── test_dedup.py
│   └── test_health.py
├── docs/                             # 完整文档目录
│   ├── quickstart.md
│   ├── import-formats.md
│   ├── taxonomy.md
│   ├── health-check.md
│   ├── customization.md
│   └── api-reference.md
└── themes/                           # 内置主题资源
    ├── default/                      # 默认响应式主题
    │   ├── templates/                # Jinja2 模板文件
    │   └── static/                   # CSS、JavaScript 与字体文件
    └── compact/                      # 紧凑型主题，适用于高密度信息展示
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账户，随后将 Fork 后的仓库克隆至本地开发环境，并配置上游远程分支以便同步主仓库的更新。

2. 创建新的功能分支，分支命名遵循 `feature/简要描述` 或 `fix/问题编号` 的格式，确保分支名清晰反映本次变更的目的，避免在主分支上直接提交。

3. 编写或修改代码后，请确保所有现有单元测试通过，并为新增功能补充对应的测试用例，测试代码需放置于 `tests/` 目录下相应文件中，保持测试覆盖率不低于百分之八十。

4. 提交变更前运行代码格式检查工具与静态分析工具，本项目使用 black 进行统一格式化，使用 flake8 进行风格检查，使用 mypy 进行类型注解校验，所有检查必须通过方可提交。

5. 提交 Pull Request 至主仓库的 develop 分支，在 PR 描述中详细说明变更动机、实现方案以及影响范围，并关联相关 Issue 编号。核心维护者会在三个工作日内进行审查与反馈。

## 常见问题

问：导入外链时提示 URL 格式无效，但该链接在浏览器中可以正常打开，原因是什么？

答：MapBlog 默认对 URL 进行严格格式校验，要求包含协议头且域名部分符合标准规范。部分浏览器会自动补全缺失的协议头，但系统不会自动添加。请检查原始 URL 是否以 http:// 或 https:// 开头，且路径中不存在未转义的空格或中文标点符号。若链接地址中包含特殊字符，建议先进行百分号编码后再导入。

问：失效链接巡检结果中出现了大量超时错误，但手动访问这些链接是正常的，如何调整检测参数？

答：默认的巡检超时时间为 3 秒，对于响应较慢的源站可能触发误报。您可以在 `config.yaml` 中调整 `health_check.timeout` 参数至 10 秒或更高，同时可增加 `health_check.retry` 重试次数。若某个域名始终响应缓慢，可在 `health_check.ignore

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
