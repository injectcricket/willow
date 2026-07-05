# WebLink Harvest

WebLink Harvest 是一个面向技术研究者和内容聚合场景的分布式外链资源归集系统。该项目旨在解决技术博客、教程站点与知识库中零散外部链接难以统一管理、检索与追溯的问题。通过结构化的 URL 收容与分类机制，WebLink Harvest 将原始散落的文章链接转化为可批量处理、可版本追踪、可导入下游工具链的标准化资源清单。

本项目主要服务于技术内容运营者、知识库维护者以及自动化爬虫调度系统。WebLink Harvest 不提供内容缓存或代理访问功能，仅以纯文本形态维护链接索引，保障原始来源的完整性。每批次处理 250 个资源链接，并输出符合规范的可读文档，便于人工审核与机器解析。

## 功能概览

- 批量链接归集：支持将大批量异构 URL 导入统一索引表，单批次容量上限为 500 条，覆盖常见博客平台与文章详情页结构。

- 原始格式保真：所有 URL 均按照原始协议、原始域名、原始大小写及原始路径原样收录，杜绝自动补全协议或大小写转换造成的目标地址偏移。

- 分类与标签占位：每个链接条目可关联多级分类标签，便于后续按域名、日期、内容类型进行二次筛选。

- 重复检测与告警：内置链接去重校验机制，对完全相同的 URL 在录入阶段进行标记，避免索引冗余。

- Markdown 友好导出：所有资源列表以标准无序列表格式呈现，每行单条 URL，不包含额外超链接标记或内嵌样式，可直接嵌入技术文档或静态站点生成器。

- 批次状态追踪：记录批次编号、导入时间、链接总数与有效通过率，方便运营者掌握数据流转进度。

## 应用场景

1. 技术博客精选合辑归档：内容编辑每周从多个技术博客站采集高质量文章链接，使用 WebLink Harvest 将分散的详情页地址归入月度资源包，同步至团队内部知识库进行统一评审。

2. 开源项目外部依赖追溯：开源项目维护者通过 WebLink Harvest 记录项目文档中引用的所有外部参考链接，在版本迭代时可快速检查链接可用性，及时更新失效引用。

3. 自动化采集管道输入准备：数据工程团队将 WebLink Harvest 导出的纯链接列表作为下游分布式爬虫的种子队列，按批次调度抓取任务，避免因格式不规范导致解析器异常。

4. 合规审查与链接审计：法务或合规部门利用分批导出的资源清单进行外部链接内容审查，逐条核对目标站点是否在允许访问名单内，并生成审计报告。

5. 社区贡献资源整合：开源社区通过 WebLink Harvest 收集成员提交的教程、案例与工具推荐链接，经审核后合并至主仓库的资源索引页，形成可检索的外部参考网络。

## 快速开始

以下步骤适用于首次部署 WebLink Harvest 索引维护环境。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-harvest/weblink-harvest.git

# 进入项目根目录
cd weblink-harvest

# 安装基础依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 执行批次导入脚本，加载第14批次原始链接
python scripts/import_batch.py --batch 14 --input ./data/batch_14_raw.txt

# 生成当前批次 Markdown 文档
python scripts/export_docs.py --batch 14 --output ./docs/batch_14.md
```

执行上述命令后，系统将在 ./docs/batch_14.md 生成包含资源列表、统计信息与元数据的文档。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心脚本运行环境，需确保 pip 可用 |
| Git | 2.25 及以上 | 用于克隆仓库及版本管理 |
| Markdown 解析库 | markdown-it-py 2.2.0 | 用于导出文档的格式校验 |
| 字符编码库 | chardet 5.0.0 | 自动检测原始输入文件的编码格式 |
| 网络请求库 | requests 2.28.0 | 仅用于链接可达性校验（可选功能） |
| 日志组件 | logging 标准库 | 记录导入过程及异常事件 |
| 测试框架 | pytest 7.1.0 | 运行单元测试和集成测试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何安装、配置和运行基础导入导出流程 |
| 批次规范 | docs/batch_specification.md | 批次编号规则、原始数据格式、提交文件结构 |
| 贡献指南 | CONTRIBUTING.md | 如何提交新的批次数据、修复链接或改进文档 |
| API 参考 | docs/api_reference.md | 脚本命令行参数、返回值及可扩展接口说明 |
| 常见问题 | docs/faq.md | 解决导入失败、编码异常、链接数量校验不通过等高频问题 |
| 变更日志 | CHANGELOG.md | 记录每个版本的功能新增、修复和破坏性更改 |

## 资源列表

- http://www.blog.nwbbyt.cn/Article/details/3959755.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8814.sHtML
- http://www.blog.puhvjy.cn/Article/details/6841.sHtML
- http://www.blog.nwbbyt.cn/Article/details/89508.sHtML
- http://www.blog.puhvjy.cn/Article/details/4075.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2494.sHtML
- http://www.blog.nzfnve.cn/Article/details/09375.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1183.sHtML
- http://www.blog.puhvjy.cn/Article/details/1375468.sHtML
- http://www.blog.puhvjy.cn/Article/details/46854.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7756.sHtML
- http://www.blog.nzfnve.cn/Article/details/5021995.sHtML
- http://www.blog.nzfnve.cn/Article/details/0979.sHtML
- http://www.blog.nzfnve.cn/Article/details/8666.sHtML
- http://www.blog.puhvjy.cn/Article/details/5762261.sHtML
- http://www.blog.nzfnve.cn/Article/details/6489435.sHtML
- http://www.blog.puhvjy.cn/Article/details/772872.sHtML
- http://www.blog.nwbbyt.cn/Article/details/41519.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1421.sHtML
- http://www.blog.nwbbyt.cn/Article/details/71629.sHtML
- http://www.blog.puhvjy.cn/Article/details/529195.sHtML
- http://www.blog.nwbbyt.cn/Article/details/182312.sHtML
- http://www.blog.nwbbyt.cn/Article/details/714687.sHtML
- http://www.blog.nwbbyt.cn/Article/details/262821.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5685541.sHtML
- http://www.blog.puhvjy.cn/Article/details/405006.sHtML
- http://www.blog.nwbbyt.cn/Article/details/90537.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7836.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8520755.sHtML
- http://www.blog.nwbbyt.cn/Article/details/287848.sHtML
- http://www.blog.puhvjy.cn/Article/details/68575.sHtML
- http://www.blog.nzfnve.cn/Article/details/346908.sHtML
- http://www.blog.nzfnve.cn/Article/details/0376966.sHtML
- http://www.blog.nzfnve.cn/Article/details/4543.sHtML
- http://www.blog.nzfnve.cn/Article/details/5427476.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5987.sHtML
- http://www.blog.puhvjy.cn/Article/details/4470795.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7647625.sHtML
- http://www.blog.nwbbyt.cn/Article/details/076033.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4908.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0723053.sHtML
- http://www.blog.jnjpgf.cn/Article/details/76491.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5422.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9934.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6815584.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3794472.sHtML
- http://www.blog.puhvjy.cn/Article/details/251907.sHtML
- http://www.blog.puhvjy.cn/Article/details/0621.sHtML
- http://www.blog.puhvjy.cn/Article/details/801026.sHtML
- http://www.blog.nzfnve.cn/Article/details/21412.sHtML
- http://www.blog.nzfnve.cn/Article/details/18785.sHtML
- http://www.blog.puhvjy.cn/Article/details/2363.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4971121.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6295.sHtML
- http://www.blog.nzfnve.cn/Article/details/9255500.sHtML
- http://www.blog.nzfnve.cn/Article/details/853965.sHtML
- http://www.blog.puhvjy.cn/Article/details/3725712.sHtML
- http://www.blog.nzfnve.cn/Article/details/942992.sHtML
- http://www.blog.jnjpgf.cn/Article/details/502275.sHtML
- http://www.blog.nzfnve.cn/Article/details/2209285.sHtML
- http://www.blog.puhvjy.cn/Article/details/7199.sHtML
- http://www.blog.nzfnve.cn/Article/details/98142.sHtML
- http://www.blog.puhvjy.cn/Article/details/219658.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6626535.sHtML
- http://www.blog.nzfnve.cn/Article/details/01170.sHtML
- http://www.blog.nzfnve.cn/Article/details/8373.sHtML
- http://www.blog.puhvjy.cn/Article/details/68287.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9629463.sHtML
- http://www.blog.nzfnve.cn/Article/details/2698.sHtML
- http://www.blog.nzfnve.cn/Article/details/5616.sHtML
- http://www.blog.nzfnve.cn/Article/details/2070304.sHtML
- http://www.blog.puhvjy.cn/Article/details/6305210.sHtML
- http://www.blog.puhvjy.cn/Article/details/018024.sHtML
- http://www.blog.puhvjy.cn/Article/details/40785.sHtML
- http://www.blog.nzfnve.cn/Article/details/6579.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5885.sHtML
- http://www.blog.puhvjy.cn/Article/details/9275.sHtML
- http://www.blog.jnjpgf.cn/Article/details/854694.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3245545.sHtML
- http://www.blog.nzfnve.cn/Article/details/3976954.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2104033.sHtML
- http://www.blog.puhvjy.cn/Article/details/1348888.sHtML
- http://www.blog.puhvjy.cn/Article/details/3498.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3965100.sHtML
- http://www.blog.puhvjy.cn/Article/details/41351.sHtML
- http://www.blog.puhvjy.cn/Article/details/93097.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8277076.sHtML
- http://www.blog.puhvjy.cn/Article/details/651354.sHtML
- http://www.blog.jnjpgf.cn/Article/details/83578.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1646.sHtML
- http://www.blog.nzfnve.cn/Article/details/483986.sHtML
- http://www.blog.puhvjy.cn/Article/details/326835.sHtML
- http://www.blog.puhvjy.cn/Article/details/3800512.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3805245.sHtML
- http://www.blog.nzfnve.cn/Article/details/7086858.sHtML
- http://www.blog.nzfnve.cn/Article/details/5464652.sHtML
- http://www.blog.nzfnve.cn/Article/details/3033.sHtML
- http://www.blog.puhvjy.cn/Article/details/225163.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5353.sHtML
- http://www.blog.puhvjy.cn/Article/details/8441412.sHtML
- http://www.blog.nzfnve.cn/Article/details/5093.sHtML
- http://www.blog.puhvjy.cn/Article/details/706867.sHtML
- http://www.blog.nzfnve.cn/Article/details/139217.sHtML
- http://www.blog.jnjpgf.cn/Article/details/690696.sHtML
- http://www.blog.puhvjy.cn/Article/details/9418653.sHtML
- http://www.blog.nzfnve.cn/Article/details/82275.sHtML
- http://www.blog.nwbbyt.cn/Article/details/455039.sHtML
- http://www.blog.nzfnve.cn/Article/details/9656377.sHtML
- http://www.blog.jnjpgf.cn/Article/details/790901.sHtML
- http://www.blog.jnjpgf.cn/Article/details/228963.sHtML
- http://www.blog.nzfnve.cn/Article/details/898656.sHtML
- http://www.blog.puhvjy.cn/Article/details/890337.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4724.sHtML
- http://www.blog.puhvjy.cn/Article/details/4295318.sHtML
- http://www.blog.nzfnve.cn/Article/details/3226936.sHtML
- http://www.blog.nwbbyt.cn/Article/details/83604.sHtML
- http://www.blog.jnjpgf.cn/Article/details/517554.sHtML
- http://www.blog.nwbbyt.cn/Article/details/97382.sHtML
- http://www.blog.nzfnve.cn/Article/details/67636.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6374.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9272.sHtML
- http://www.blog.nwbbyt.cn/Article/details/96456.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4850.sHtML
- http://www.blog.puhvjy.cn/Article/details/707151.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7943.sHtML
- http://www.blog.jnjpgf.cn/Article/details/824453.sHtML
- http://www.blog.jnjpgf.cn/Article/details/84840.sHtML
- http://www.blog.nzfnve.cn/Article/details/06825.sHtML
- http://www.blog.puhvjy.cn/Article/details/443710.sHtML
- http://www.blog.jnjpgf.cn/Article/details/408832.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5811783.sHtML
- http://www.blog.puhvjy.cn/Article/details/607492.sHtML
- http://www.blog.nzfnve.cn/Article/details/340926.sHtML
- http://www.blog.nzfnve.cn/Article/details/850421.sHtML
- http://www.blog.nzfnve.cn/Article/details/960089.sHtML
- http://www.blog.puhvjy.cn/Article/details/21222.sHtML
- http://www.blog.nzfnve.cn/Article/details/59345.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8549537.sHtML
- http://www.blog.puhvjy.cn/Article/details/494541.sHtML
- http://www.blog.puhvjy.cn/Article/details/6123.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0938099.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8920.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7069.sHtML
- http://www.blog.jnjpgf.cn/Article/details/67358.sHtML
- http://www.blog.nwbbyt.cn/Article/details/711376.sHtML
- http://www.blog.nwbbyt.cn/Article/details/50195.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4268.sHtML
- http://www.blog.puhvjy.cn/Article/details/3340273.sHtML
- http://www.blog.nzfnve.cn/Article/details/2360381.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3333.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6826681.sHtML
- http://www.blog.puhvjy.cn/Article/details/4425828.sHtML
- http://www.blog.nzfnve.cn/Article/details/7559665.sHtML
- http://www.blog.puhvjy.cn/Article/details/97294.sHtML
- http://www.blog.jnjpgf.cn/Article/details/233225.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3837870.sHtML
- http://www.blog.nwbbyt.cn/Article/details/162060.sHtML
- http://www.blog.nzfnve.cn/Article/details/5758.sHtML
- http://www.blog.puhvjy.cn/Article/details/9681261.sHtML
- http://www.blog.puhvjy.cn/Article/details/280206.sHtML
- http://www.blog.nwbbyt.cn/Article/details/448197.sHtML
- http://www.blog.jnjpgf.cn/Article/details/973938.sHtML
- http://www.blog.puhvjy.cn/Article/details/7602881.sHtML
- http://www.blog.jnjpgf.cn/Article/details/513573.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9926.sHtML
- http://www.blog.puhvjy.cn/Article/details/05628.sHtML
- http://www.blog.jnjpgf.cn/Article/details/081907.sHtML
- http://www.blog.puhvjy.cn/Article/details/0684723.sHtML
- http://www.blog.jnjpgf.cn/Article/details/395291.sHtML
- http://www.blog.nzfnve.cn/Article/details/7928891.sHtML
- http://www.blog.nzfnve.cn/Article/details/0530.sHtML
- http://www.blog.nzfnve.cn/Article/details/56375.sHtML
- http://www.blog.nzfnve.cn/Article/details/45325.sHtML
- http://www.blog.puhvjy.cn/Article/details/29210.sHtML
- http://www.blog.jnjpgf.cn/Article/details/416704.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9842387.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7307.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9650.sHtML
- http://www.blog.nzfnve.cn/Article/details/4189.sHtML
- http://www.blog.nwbbyt.cn/Article/details/171129.sHtML
- http://www.blog.nzfnve.cn/Article/details/9476.sHtML
- http://www.blog.nwbbyt.cn/Article/details/822263.sHtML
- http://www.blog.nzfnve.cn/Article/details/2233.sHtML
- http://www.blog.nzfnve.cn/Article/details/47454.sHtML
- http://www.blog.nzfnve.cn/Article/details/10992.sHtML
- http://www.blog.puhvjy.cn/Article/details/02332.sHtML
- http://www.blog.puhvjy.cn/Article/details/6108.sHtML
- http://www.blog.nzfnve.cn/Article/details/403748.sHtML
- http://www.blog.nwbbyt.cn/Article/details/95807.sHtML
- http://www.blog.puhvjy.cn/Article/details/41150.sHtML
- http://www.blog.nwbbyt.cn/Article/details/01445.sHtML
- http://www.blog.jnjpgf.cn/Article/details/558790.sHtML
- http://www.blog.nzfnve.cn/Article/details/8296189.sHtML
- http://www.blog.nwbbyt.cn/Article/details/791825.sHtML
- http://www.blog.jnjpgf.cn/Article/details/287508.sHtML
- http://www.blog.puhvjy.cn/Article/details/8611.sHtML
- http://www.blog.jnjpgf.cn/Article/details/76854.sHtML
- http://www.blog.puhvjy.cn/Article/details/880204.sHtML
- http://www.blog.jnjpgf.cn/Article/details/380818.sHtML
- http://www.blog.jnjpgf.cn/Article/details/65998.sHtML
- http://www.blog.puhvjy.cn/Article/details/73815.sHtML
- http://www.blog.puhvjy.cn/Article/details/57047.sHtML
- http://www.blog.nzfnve.cn/Article/details/7108.sHtML
- http://www.blog.nwbbyt.cn/Article/details/670052.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7152166.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2939.sHtML
- http://www.blog.puhvjy.cn/Article/details/178025.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2604662.sHtML
- http://www.blog.jnjpgf.cn/Article/details/012888.sHtML
- http://www.blog.nzfnve.cn/Article/details/77147.sHtML
- http://www.blog.puhvjy.cn/Article/details/8061676.sHtML
- http://www.blog.nzfnve.cn/Article/details/5701708.sHtML
- http://www.blog.puhvjy.cn/Article/details/638233.sHtML
- http://www.blog.jnjpgf.cn/Article/details/12113.sHtML
- http://www.blog.nzfnve.cn/Article/details/224293.sHtML
- http://www.blog.nzfnve.cn/Article/details/2936.sHtML
- http://www.blog.nzfnve.cn/Article/details/3423746.sHtML
- http://www.blog.nzfnve.cn/Article/details/3693.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3695.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4825.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2114.sHtML
- http://www.blog.puhvjy.cn/Article/details/53840.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3031.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5319658.sHtML
- http://www.blog.puhvjy.cn/Article/details/957560.sHtML
- http://www.blog.jnjpgf.cn/Article/details/687909.sHtML
- http://www.blog.nzfnve.cn/Article/details/6581726.sHtML
- http://www.blog.puhvjy.cn/Article/details/05783.sHtML
- http://www.blog.nzfnve.cn/Article/details/51195.sHtML
- http://www.blog.jnjpgf.cn/Article/details/673858.sHtML
- http://www.blog.nwbbyt.cn/Article/details/09158.sHtML
- http://www.blog.puhvjy.cn/Article/details/3192.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5066.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5303.sHtML
- http://www.blog.nwbbyt.cn/Article/details/67129.sHtML
- http://www.blog.nzfnve.cn/Article/details/5534.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1539153.sHtML
- http://www.blog.nzfnve.cn/Article/details/5498163.sHtML
- http://www.blog.puhvjy.cn/Article/details/142427.sHtML
- http://www.blog.jnjpgf.cn/Article/details/885204.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1159699.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0206744.sHtML
- http://www.blog.nzfnve.cn/Article/details/1610364.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7058.sHtML
- http://www.blog.nwbbyt.cn/Article/details/73957.sHtML
- http://www.blog.jnjpgf.cn/Article/details/02220.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9002556.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6601923.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4859.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2342146.sHtML

## 项目结构

```
weblink-harvest/
├── batch_14/                              # 第14批次工作目录
│   ├── raw/                               # 原始输入文件存放处
│   │   └── batch_14_raw.txt               # 本次导入的250条原始链接
│   ├── parsed/                            # 解析后结构化数据
│   │   └── batch_14_parsed.json           # 包含链接、域名、提取时间等字段
│   └── output/                            # 导出文档及报告
│       └── batch_14_doc.md                # 最终生成的Markdown文档
├── scripts/                               # 可执行脚本集合
│   ├── import_batch.py                    # 批量导入主程序
│   ├── export_docs.py                     # 文档导出生成器
│   └── validator.py                       # 链接格式与重复性校验
├── tests/                                 # 单元测试与集成测试
│   ├── test_import.py                     # 导入逻辑测试用例
│   └── test_export.py                     # 导出格式测试用例
├── config/                                # 全局配置文件
│   ├── settings.yaml                      # 批次大小、输出模板路径等
│   └── logging.conf                       # 日志级别与输出目标配置
├── docs/                                  # 用户文档与维护手册
│   ├── user_guide.md                      # 完整使用指引
│   └── batch_specification.md             # 批次数据规范说明
├── requirements.txt                       # Python依赖声明
├── CONTRIBUTING.md                        # 贡献者操作流程
├── CHANGELOG.md                           # 版本变更历史
└── README.md                              # 项目首页文档（当前文件）
```

## 贡献指南

1. 提交新批次数据前，请先阅读 docs/batch_specification.md 确认原始文件格式要求，确保每行一条URL且无多余空白字符。将待导入链接存放于 batch_{批次号}/raw 目录下。

2. 运行校验脚本验证链接格式合法性：执行 python scripts/validator.py --input ./batch_{批次号}/raw/raw.txt，确认输出结果中不包含格式异常或重复条目。

3. 执行导入脚本生成结构化 JSON 文件与 Markdown 文档，检查输出目录中的文档是否包含完整资源列表且所有URL保持原始格式未被篡改。

4. 提交 Pull Request 时，请附带说明新批次的来源、链接总数以及校验通过状态。若包含对现有脚本或配置的修改，需同步更新对应单元测试。

5. 若发现已合并批次中存在失效链接或格式错误，请提交单独 Issue 描述具体条目及修正建议，维护者将在下一个补丁版本中处理。

## 常见问题

Q: 导入脚本提示编码错误，无法读取原始文件。

A: 请检查原始文件的字符编码，通常 UTF-8 无 BOM 格式为推荐标准。若文件来自 Windows 系统，可能包含 GBK 或 UTF-8 with BOM 编码，可尝试使用 chardet 自动检测编码：python -m chardet batch_{批次号}/raw/raw.txt，然后以检测到的编码重新运行导入脚本并添加 --encoding 参数。

Q: 导出的 Markdown 文档中某些 URL 被自动截断或换行。

A: 该问题通常源于原始文件中包含不可见换行符或回车符。请确认每行仅包含一个URL，且尾部无多余空格或制表符。可使用 dos2unix 工具转换文件换行符后再执行导入。若问题仍然存在，检查 validator 脚本输出的警告行。

Q: 如何校验某批次全部链接是否仍可访问？

A: 本项目提供可选网络校验模块，但默认不启用以避免网络请求影响性能。如需使用，请安装 requests 依赖后执行 python scripts/check_availability.py --batch 14 --timeout 5，该命令将输出每个URL的状态码及连接耗时，并生成可用性报告。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
