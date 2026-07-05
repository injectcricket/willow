# BlogLink Archive

BlogLink Archive 是一个面向技术研究者、内容聚合者和信息分析人员的结构化博客文章外链汇总系统。该项目旨在解决分散于多个个人技术博客平台中的优质文章难以被统一检索、批量引用和长期存档的问题。通过将来自多个独立博客域名的文章链接按照统一的条目格式进行归集，BlogLink Archive 为后续的数据分析、内容推荐、知识图谱构建以及学术引用提供了干净、可扩展的数据基础。

本项目定位为技术资源与元数据汇总站，不直接存储文章内容，而是专注于链接的规范化整理与版本管理。目标用户包括从事网络信息分析的研究人员、需要批量获取技术文章元数据的开发者、以及希望建立个人知识库索引的技术爱好者。通过本项目提供的结构化链接清单，用户可以快速识别不同博客站点的文章发布规律、ID 分布特征，并基于这些外链进行二次开发，例如构建自定义的爬虫调度器、文章更新监控服务或内容质量评估工具。

## 功能概览

- 多源异构链接归一化采集：系统接受来自多个独立博客域名下的文章链接，自动识别 URL 结构差异，将不同域名、不同路径格式的文章链接统一纳入归档体系，确保数据采集的完整性与一致性。

- 批量链接条目化管理：每条链接均作为独立条目存储在归档系统中，支持按域名、按文章 ID 范围、按采集批次进行多维度筛选与导出，方便用户对特定来源或特定时间段内的文章进行集中处理。

- 原始链接严格保真输出：系统在输出环节强制遵循原始 URL 的完整性与原样性规则，不自动补全协议头，不修改域名大小写，不添加或删除尾部斜杠，确保每条外链均可被原始服务器正确解析，避免因格式篡改导致的链接失效问题。

- 批次化数据组织与版本追踪：项目按批次对链接进行分组管理，每批次包含固定数量的链接条目，并记录批次导入时间、来源分布统计等元信息。用户可通过批次标识追溯数据引入历史，便于进行增量更新与差异对比。

- 轻量级依赖与低运维成本：系统核心功能基于纯文本与静态表格实现，无需复杂的数据库配置或持续运行的后台服务。用户只需具备基本的命令行执行环境即可完成数据的拉取、安装与本地运行，适合个人开发者或小规模团队快速部署使用。

- 可扩展的数据输出接口：除提供标准的 Markdown 文档输出外，系统预留了 JSON、CSV 等结构化数据格式的导出扩展点，方便用户将链接数据导入数据分析流水线、可视化工具或自定义的前端展示页面。

## 应用场景

- 技术博客资源归档与检索：研究人员或开发者可利用本项目的链接列表，快速获取来自 nwbbyt.cn、puhvjy.cn、nzfnve.cn、jnjpgf.cn 等多个博客站点的历史文章入口，将分散的文章链接汇总到单一目录下，便于后续进行关键词检索、主题分类或引用统计。

- 外链有效性监控与维护：站点管理员或 SEO 运维人员可基于本项目提供的链接清单，定期发起批量 HTTP 请求，检测各文章链接的可达性、响应状态码及重定向情况，及时发现并处理失效链接，保障站点外链生态的健康度。

- 第三方内容聚合平台的初始数据灌入：正在开发技术内容聚合平台或个性化阅读器的开发者，可将本项目的链接列表作为初始种子数据，通过批量抓取文章标题、发布时间、作者等信息，快速构建平台的内容索引库，缩短平台上线前的数据准备周期。

## 快速开始

以下命令演示了如何将本项目克隆至本地环境、安装必要依赖并执行初始运行流程。请确保在执行前已正确配置网络代理或镜像源以加速依赖下载。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/bloglink-archive.git

# 进入项目根目录
cd bloglink-archive

# 安装依赖（基于 Python 3.10+ 环境，使用 pip 安装解析与校验工具）
pip install -r requirements.txt

# 执行本地运行脚本，生成当前批次的链接归档文档
python archive_builder.py --batch 11 --total 250 --output README.md
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.10 及以上 | 核心运行环境，用于执行链接解析、格式校验与文档生成脚本 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装 requirements.txt 中声明的第三方库 |
| Git | 2.30 及以上 | 版本控制工具，用于克隆仓库及管理项目代码历史 |
| Markdown 解析库 (markdown-it-py) | 2.2.0 及以上 | 用于在构建过程中对生成的 Markdown 结构进行语法校验 |
| 网络连接 (HTTP/HTTPS) | 无特定版本要求 | 用于在运行测试用例时验证外链的域名解析与基础连通性（可选） |
| 操作系统 | Linux / macOS / Windows (WSL2 推荐) | 跨平台支持，但建议在类 Unix 环境下进行开发测试以保证路径兼容性 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/quickstart.md | 如何在一分钟内完成项目配置并生成第一份链接归档文档 |
| 数据格式规范 | docs/data-format.md | 链接条目的字段定义是什么，URL 保留规则的具体约束有哪些 |
| 批次管理说明 | docs/batch-management.md | 批次编号规则是什么，如何新增批次或对已有批次进行增量更新 |
| 贡献者操作手册 | docs/contributing.md | 贡献者如何提交新的链接数据，代码审查流程与测试要求是什么 |

## 资源列表

- http://www.blog.nwbbyt.cn/Article/details/251631.sHtML
- http://www.blog.nwbbyt.cn/Article/details/37056.sHtML
- http://www.blog.puhvjy.cn/Article/details/8667891.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8711.sHtML
- http://www.blog.nzfnve.cn/Article/details/1411.sHtML
- http://www.blog.puhvjy.cn/Article/details/3831906.sHtML
- http://www.blog.puhvjy.cn/Article/details/323281.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9480.sHtML
- http://www.blog.nzfnve.cn/Article/details/9735599.sHtML
- http://www.blog.nzfnve.cn/Article/details/888295.sHtML
- http://www.blog.jnjpgf.cn/Article/details/811082.sHtML
- http://www.blog.jnjpgf.cn/Article/details/873016.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4893.sHtML
- http://www.blog.nzfnve.cn/Article/details/7457.sHtML
- http://www.blog.nzfnve.cn/Article/details/456423.sHtML
- http://www.blog.nzfnve.cn/Article/details/37357.sHtML
- http://www.blog.nzfnve.cn/Article/details/3093.sHtML
- http://www.blog.nzfnve.cn/Article/details/99998.sHtML
- http://www.blog.nwbbyt.cn/Article/details/78331.sHtML
- http://www.blog.puhvjy.cn/Article/details/7888893.sHtML
- http://www.blog.nzfnve.cn/Article/details/5308987.sHtML
- http://www.blog.puhvjy.cn/Article/details/2739410.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9818.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8132377.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1131.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7695.sHtML
- http://www.blog.puhvjy.cn/Article/details/931577.sHtML
- http://www.blog.puhvjy.cn/Article/details/994078.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5804983.sHtML
- http://www.blog.nzfnve.cn/Article/details/99189.sHtML
- http://www.blog.puhvjy.cn/Article/details/78412.sHtML
- http://www.blog.jnjpgf.cn/Article/details/19318.sHtML
- http://www.blog.jnjpgf.cn/Article/details/04937.sHtML
- http://www.blog.nzfnve.cn/Article/details/5430164.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4629.sHtML
- http://www.blog.nwbbyt.cn/Article/details/675680.sHtML
- http://www.blog.jnjpgf.cn/Article/details/727622.sHtML
- http://www.blog.nzfnve.cn/Article/details/4627377.sHtML
- http://www.blog.puhvjy.cn/Article/details/4848.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9915165.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9409965.sHtML
- http://www.blog.jnjpgf.cn/Article/details/060569.sHtML
- http://www.blog.puhvjy.cn/Article/details/8255903.sHtML
- http://www.blog.puhvjy.cn/Article/details/6744167.sHtML
- http://www.blog.puhvjy.cn/Article/details/15288.sHtML
- http://www.blog.puhvjy.cn/Article/details/07188.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3949784.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9105.sHtML
- http://www.blog.puhvjy.cn/Article/details/3032.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3550.sHtML
- http://www.blog.nzfnve.cn/Article/details/06027.sHtML
- http://www.blog.nzfnve.cn/Article/details/8584.sHtML
- http://www.blog.nzfnve.cn/Article/details/4787.sHtML
- http://www.blog.nzfnve.cn/Article/details/1712517.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0798209.sHtML
- http://www.blog.puhvjy.cn/Article/details/9362.sHtML
- http://www.blog.nwbbyt.cn/Article/details/48171.sHtML
- http://www.blog.nzfnve.cn/Article/details/816117.sHtML
- http://www.blog.nzfnve.cn/Article/details/786053.sHtML
- http://www.blog.puhvjy.cn/Article/details/701461.sHtML
- http://www.blog.nzfnve.cn/Article/details/4504.sHtML
- http://www.blog.nwbbyt.cn/Article/details/56036.sHtML
- http://www.blog.jnjpgf.cn/Article/details/33651.sHtML
- http://www.blog.puhvjy.cn/Article/details/4450588.sHtML
- http://www.blog.nwbbyt.cn/Article/details/24106.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6620155.sHtML
- http://www.blog.puhvjy.cn/Article/details/133415.sHtML
- http://www.blog.nwbbyt.cn/Article/details/17322.sHtML
- http://www.blog.nzfnve.cn/Article/details/9856.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3062896.sHtML
- http://www.blog.puhvjy.cn/Article/details/384763.sHtML
- http://www.blog.puhvjy.cn/Article/details/156965.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1682.sHtML
- http://www.blog.nzfnve.cn/Article/details/56853.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4467715.sHtML
- http://www.blog.jnjpgf.cn/Article/details/10442.sHtML
- http://www.blog.nwbbyt.cn/Article/details/35501.sHtML
- http://www.blog.jnjpgf.cn/Article/details/32387.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8546.sHtML
- http://www.blog.puhvjy.cn/Article/details/68731.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4557882.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0307221.sHtML
- http://www.blog.jnjpgf.cn/Article/details/595431.sHtML
- http://www.blog.puhvjy.cn/Article/details/1801.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5118.sHtML
- http://www.blog.nzfnve.cn/Article/details/92557.sHtML
- http://www.blog.jnjpgf.cn/Article/details/951086.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2293.sHtML
- http://www.blog.nzfnve.cn/Article/details/08204.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2312.sHtML
- http://www.blog.puhvjy.cn/Article/details/369220.sHtML
- http://www.blog.nzfnve.cn/Article/details/1356.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1482.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1580826.sHtML
- http://www.blog.nzfnve.cn/Article/details/63660.sHtML
- http://www.blog.jnjpgf.cn/Article/details/95196.sHtML
- http://www.blog.nzfnve.cn/Article/details/20552.sHtML
- http://www.blog.jnjpgf.cn/Article/details/098880.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9485.sHtML
- http://www.blog.puhvjy.cn/Article/details/950881.sHtML
- http://www.blog.nwbbyt.cn/Article/details/09672.sHtML
- http://www.blog.puhvjy.cn/Article/details/3958306.sHtML
- http://www.blog.nzfnve.cn/Article/details/4559711.sHtML
- http://www.blog.nwbbyt.cn/Article/details/069526.sHtML
- http://www.blog.nzfnve.cn/Article/details/87113.sHtML
- http://www.blog.nwbbyt.cn/Article/details/852130.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3403422.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8701906.sHtML
- http://www.blog.jnjpgf.cn/Article/details/07327.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5663.sHtML
- http://www.blog.nzfnve.cn/Article/details/9017328.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4262377.sHtML
- http://www.blog.nwbbyt.cn/Article/details/501290.sHtML
- http://www.blog.nwbbyt.cn/Article/details/079393.sHtML
- http://www.blog.puhvjy.cn/Article/details/6318112.sHtML
- http://www.blog.jnjpgf.cn/Article/details/76680.sHtML
- http://www.blog.puhvjy.cn/Article/details/26533.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2822102.sHtML
- http://www.blog.puhvjy.cn/Article/details/9418474.sHtML
- http://www.blog.nwbbyt.cn/Article/details/239909.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6539.sHtML
- http://www.blog.puhvjy.cn/Article/details/098408.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4649.sHtML
- http://www.blog.jnjpgf.cn/Article/details/15753.sHtML
- http://www.blog.puhvjy.cn/Article/details/759948.sHtML
- http://www.blog.nwbbyt.cn/Article/details/922734.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6213927.sHtML
- http://www.blog.nzfnve.cn/Article/details/8529.sHtML
- http://www.blog.nzfnve.cn/Article/details/7106734.sHtML
- http://www.blog.nzfnve.cn/Article/details/8453.sHtML
- http://www.blog.nwbbyt.cn/Article/details/174505.sHtML
- http://www.blog.nzfnve.cn/Article/details/3309986.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3881.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8027579.sHtML
- http://www.blog.puhvjy.cn/Article/details/2780.sHtML
- http://www.blog.nzfnve.cn/Article/details/98217.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4145786.sHtML
- http://www.blog.nzfnve.cn/Article/details/3542.sHtML
- http://www.blog.puhvjy.cn/Article/details/7191097.sHtML
- http://www.blog.puhvjy.cn/Article/details/6878926.sHtML
- http://www.blog.puhvjy.cn/Article/details/330321.sHtML
- http://www.blog.jnjpgf.cn/Article/details/12782.sHtML
- http://www.blog.nwbbyt.cn/Article/details/125396.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3514862.sHtML
- http://www.blog.nzfnve.cn/Article/details/7565553.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3422.sHtML
- http://www.blog.nzfnve.cn/Article/details/0544.sHtML
- http://www.blog.puhvjy.cn/Article/details/3679006.sHtML
- http://www.blog.nwbbyt.cn/Article/details/77256.sHtML
- http://www.blog.puhvjy.cn/Article/details/2862661.sHtML
- http://www.blog.puhvjy.cn/Article/details/234996.sHtML
- http://www.blog.nzfnve.cn/Article/details/64113.sHtML
- http://www.blog.nzfnve.cn/Article/details/58069.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2748019.sHtML
- http://www.blog.nwbbyt.cn/Article/details/35782.sHtML
- http://www.blog.nwbbyt.cn/Article/details/61940.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4952505.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3066.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5411599.sHtML
- http://www.blog.nwbbyt.cn/Article/details/236685.sHtML
- http://www.blog.nzfnve.cn/Article/details/10622.sHtML
- http://www.blog.nzfnve.cn/Article/details/1277749.sHtML
- http://www.blog.nzfnve.cn/Article/details/60285.sHtML
- http://www.blog.jnjpgf.cn/Article/details/392223.sHtML
- http://www.blog.nzfnve.cn/Article/details/9249.sHtML
- http://www.blog.nwbbyt.cn/Article/details/975293.sHtML
- http://www.blog.nzfnve.cn/Article/details/3997.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9546212.sHtML
- http://www.blog.puhvjy.cn/Article/details/5068244.sHtML
- http://www.blog.nwbbyt.cn/Article/details/261435.sHtML
- http://www.blog.nwbbyt.cn/Article/details/847190.sHtML
- http://www.blog.nwbbyt.cn/Article/details/685701.sHtML
- http://www.blog.nzfnve.cn/Article/details/6177711.sHtML
- http://www.blog.nwbbyt.cn/Article/details/778205.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7788.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2955238.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5220454.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1486605.sHtML
- http://www.blog.puhvjy.cn/Article/details/24240.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4663493.sHtML
- http://www.blog.nwbbyt.cn/Article/details/844415.sHtML
- http://www.blog.nwbbyt.cn/Article/details/241052.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2200348.sHtML
- http://www.blog.nzfnve.cn/Article/details/42647.sHtML
- http://www.blog.nwbbyt.cn/Article/details/36393.sHtML
- http://www.blog.nzfnve.cn/Article/details/1804385.sHtML
- http://www.blog.jnjpgf.cn/Article/details/236263.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2316.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6740499.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0134476.sHtML
- http://www.blog.puhvjy.cn/Article/details/3505612.sHtML
- http://www.blog.puhvjy.cn/Article/details/689981.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1712.sHtML
- http://www.blog.nwbbyt.cn/Article/details/96100.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5916580.sHtML
- http://www.blog.nwbbyt.cn/Article/details/48052.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8566.sHtML
- http://www.blog.nzfnve.cn/Article/details/5066.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3450183.sHtML
- http://www.blog.puhvjy.cn/Article/details/9896056.sHtML
- http://www.blog.puhvjy.cn/Article/details/5812190.sHtML
- http://www.blog.nzfnve.cn/Article/details/287873.sHtML
- http://www.blog.jnjpgf.cn/Article/details/62389.sHtML
- http://www.blog.nzfnve.cn/Article/details/16591.sHtML
- http://www.blog.nwbbyt.cn/Article/details/75925.sHtML
- http://www.blog.puhvjy.cn/Article/details/73441.sHtML
- http://www.blog.nwbbyt.cn/Article/details/999178.sHtML
- http://www.blog.jnjpgf.cn/Article/details/275509.sHtML
- http://www.blog.puhvjy.cn/Article/details/564324.sHtML
- http://www.blog.jnjpgf.cn/Article/details/284487.sHtML
- http://www.blog.puhvjy.cn/Article/details/7876805.sHtML
- http://www.blog.puhvjy.cn/Article/details/441748.sHtML
- http://www.blog.puhvjy.cn/Article/details/3414.sHtML
- http://www.blog.nzfnve.cn/Article/details/573831.sHtML
- http://www.blog.nzfnve.cn/Article/details/8599.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3942.sHtML
- http://www.blog.puhvjy.cn/Article/details/97813.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3917.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6725.sHtML
- http://www.blog.nwbbyt.cn/Article/details/404079.sHtML
- http://www.blog.nzfnve.cn/Article/details/9852.sHtML
- http://www.blog.puhvjy.cn/Article/details/933887.sHtML
- http://www.blog.nwbbyt.cn/Article/details/38952.sHtML
- http://www.blog.puhvjy.cn/Article/details/23064.sHtML
- http://www.blog.nwbbyt.cn/Article/details/53403.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0194492.sHtML
- http://www.blog.nzfnve.cn/Article/details/57212.sHtML
- http://www.blog.nzfnve.cn/Article/details/02897.sHtML
- http://www.blog.nwbbyt.cn/Article/details/23487.sHtML
- http://www.blog.puhvjy.cn/Article/details/489579.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5274541.sHtML
- http://www.blog.jnjpgf.cn/Article/details/10994.sHtML
- http://www.blog.nzfnve.cn/Article/details/0030942.sHtML
- http://www.blog.nzfnve.cn/Article/details/72434.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3977605.sHtML
- http://www.blog.puhvjy.cn/Article/details/2382002.sHtML
- http://www.blog.nwbbyt.cn/Article/details/40980.sHtML
- http://www.blog.nzfnve.cn/Article/details/103011.sHtML
- http://www.blog.nwbbyt.cn/Article/details/105351.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2465.sHtML
- http://www.blog.puhvjy.cn/Article/details/76403.sHtML
- http://www.blog.nzfnve.cn/Article/details/540518.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6402680.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1134591.sHtML
- http://www.blog.puhvjy.cn/Article/details/40299.sHtML
- http://www.blog.nzfnve.cn/Article/details/20021.sHtML
- http://www.blog.nzfnve.cn/Article/details/70407.sHtML
- http://www.blog.nwbbyt.cn/Article/details/81024.sHtML
- http://www.blog.nzfnve.cn/Article/details/8385563.sHtML
- http://www.blog.nzfnve.cn/Article/details/033910.sHtML

## 项目结构

```
bloglink-archive/
├── archive_builder.py          # 核心构建脚本，负责读取链接源文件、执行校验并生成 Markdown 文档
├── requirements.txt            # Python 依赖声明文件，包含 markdown-it-py、requests 等库
├── config.yaml                 # 项目配置文件，定义批次编号、输出路径、域名白名单等参数
├── data/
│   ├── raw/                    # 原始链接数据存放目录，按批次接收外部输入的 URL 列表
│   │   └── batch_11.txt        # 第 11 批次的原始链接清单文件（纯文本，每行一个 URL）
│   ├── parsed/                 # 解析后的结构化数据缓存目录，用于加速重复构建
│   │   └── batch_11_parsed.json
│   └── schemas/                # 数据格式规范定义目录，包含 JSON Schema 校验文件
│       └── link_entry_schema.json
├── docs/                       # 项目文档目录，包含快速入门、数据格式、批次管理等说明
│   ├── quickstart.md
│   ├── data-format.md
│   ├── batch-management.md
│   └── contributing.md
├── tests/                      # 单元测试与集成测试目录
│   ├── test_parser.py          # 测试 URL 解析函数的正确性
│   ├── test_validator.py       # 测试链接格式校验逻辑
│   └── fixtures/               # 测试用例固定数据目录
│       └── sample_urls.txt
├── scripts/                    # 辅助运维脚本目录
│   ├── check_links.sh          # 批量检查链接可达性的 Shell 脚本
│   └── generate_stats.py       # 生成链接来源分布统计报告的 Python 脚本
└── output/                     # 最终生成的文档输出目录
    └── README.md               # 当前批次生成的完整 Markdown 归档文档
```

## 贡献指南

1.  Fork 本仓库至个人账户，并在本地克隆 Fork 后的副本。新建一个以 `batch-<批次号>-<贡献者标识>` 命名的特性分支，用于存放本次贡献的链接数据或代码改动。

2.  在 `data/raw/` 目录下按照已有批次文件的格式，新增或追加对应批次的原始链接列表。确保每行仅包含一个完整的 URL，且严格遵循原始来源的协议、域名与路径大小写。

3.  执行本地构建脚本 `python archive_builder.py --batch <批次号>`，验证生成的 Markdown 文档中资源列表章节是否完整无误，且所有 URL 均保持原样未被格式化工具擅自修改。

4.  编写或更新对应的单元测试用例，覆盖新增的解析逻辑或校验规则。运行 `pytest tests/` 确保全部测试用例通过，且代码覆盖率不低于百分之九十。

5.  提交包含清晰注释的 Commit，推送到特性分支后发起 Pull Request。在 PR 描述中说明本次贡献的链接数量、来源域名分布以及任何可能影响现有功能的配置变更。

## 常见问题

问：项目是否会对原始链接进行内容抓取或缓存？

答：本项目仅作为链接元数据的归档汇总工具，不主动发起对原始文章内容的抓取请求，也不在本地存储任何文章正文数据。所有链接均以原始 URL 形式保留，用户访问或处理这些链接时需自行承担与目标服务器之间的网络交互责任。

问：如果原始博客站点变更了域名或路径规则，项目中的链接是否会失效？

答：项目严格遵守原始 URL 原样输出原则，不进行任何自动化的域名替换或路径重写。若上游站点发生结构变更，已归档的历史链接可能会变为无效地址。届时用户可通过提交新的批次数据来更新链接列表，或自行利用外部重定向检测工具对存量链接进行校验与修正。

问：如何获取其他批次的链接数据？

答：本项目按照批次进行数据组织，每个批次对应一份独立的 README 文档或数据文件。用户可通过切换 Git 分支或查看 `data/raw/` 目录下的历史批次文件来获取其他批次的原始链接列表。如需生成完整汇总文档，可修改构建脚本的批次参数后重新执行生成流程。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
