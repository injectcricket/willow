# WapBlog Archive Aggregator

WapBlog Archive Aggregator 是一个面向移动端博客历史文章索引与聚合检索的开源工具集。该项目针对早期移动博客平台（WapBlog）遗留的海量历史文章链接，提供结构化的元数据抓取、链接可用性检测、内容分类标注以及批量导出能力。目标用户包括数字考古研究者、历史内容策展人、SEO 历史数据分析师以及需要批量访问移动端博客历史内容的开发者。通过本项目提供的脚本与配置模板，用户可以快速建立自己的历史文章索引库，并实现定时增量更新与健康检查。

## 功能概览

**批量链接规范化处理** 自动识别并标准化不同格式的移动博客文章链接，统一进行 URL 解码与参数重排，去除重复条目并生成标准化输出。

**文章元数据智能抓取** 对每个文章链接发起轻量级 HEAD 与 GET 请求，提取响应头中的最后修改时间、内容类型、内容长度，并尝试从 HTML 标题标签中提取文章主题。

**多线程并发探测引擎** 内置可配置的线程池，支持同时探测最多 50 个链接的可用状态，大幅缩短大规模链接集合的检测时间。

**健康状态分类与标记** 对每一条链接标记为有效、重定向、失效、超时或禁止访问等状态，并生成分类统计报告，便于后续数据清洗。

**结构化结果导出** 支持将探测结果导出为 JSON、CSV 以及 Markdown 表格三种格式，方便导入数据库或进行人工审阅。

**增量更新与变更追踪** 支持基于已有结果文件的增量扫描模式，仅检测上次扫描后新增或状态发生变化的链接，减少重复工作。

**自定义请求头与代理支持** 允许用户自定义 User-Agent、Referer 以及 HTTP 代理地址，以适应不同网络环境和目标站点的访问策略。

## 应用场景

**移动端博客历史内容编目** 数字档案馆管理员可使用本项目对大量移动博客历史文章链接进行自动化编目，记录每篇文章的最后响应时间与标题信息，生成可供查询的索引目录。

**SEO 历史数据分析** SEO 分析师可定期运行本工具，检测历史外链的存活率与重定向链变化，评估旧内容资产的持续价值，并为网站迁移或改版提供数据支撑。

**个人博客归档维护** 个人博主或内容创作者可使用本项目批量检查自己过去发布在移动平台上的文章链接是否仍然可访问，及时发现失效链接并进行修复或重定向。

**学术研究数据采集预处理** 社会学或传播学研究者可借助本项目对特定时间段内的移动博客文章链接进行批量可用性预检，筛选出有效样本后再进行后续的内容分析与文本挖掘。

## 快速开始

以下命令演示了从克隆仓库到执行首次完整扫描的完整流程。

```bash
git clone https://github.com/example/wapblog-archive-aggregator.git
cd wapblog-archive-aggregator
pip install -r requirements.txt
python wba.py --input sample_links.txt --output report.json --threads 20
```

其中 sample_links.txt 为每行一个 URL 的纯文本文件，report.json 为输出的结构化结果文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版本 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与会话管理，支持连接池复用 |
| beautifulsoup4 | 4.11.0 及以上 | 用于解析 HTML 文档并提取标题与 meta 信息 |
| lxml | 4.9.0 及以上 | 作为 BeautifulSoup 的解析器后端，提供高性能 HTML 解析 |
| tqdm | 4.64.0 及以上 | 提供进度条显示，便于用户观察批量任务执行进度 |
| pytest | 7.2.0 及以上 | 仅开发与测试时需要，用于运行单元测试与集成测试套件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何安装、配置、运行扫描任务以及解读输出结果 |
| 配置参考 | docs/configuration.md | 所有命令行参数、环境变量以及配置文件选项的详细说明 |
| 开发指南 | docs/development.md | 项目架构设计、模块划分、如何编写自定义插件或扩展新功能 |
| 常见任务 | docs/recipes.md | 包含增量扫描、代理配置、定时任务设置等实际场景的操作示例 |

## 资源列表

- http://wap.blog.nzfnve.cn/Article/details/3606.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9614.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/5962756.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/809531.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6438737.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1104.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/2774.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/774211.sHtML
- http://wap.blog.nzfnve.cn/Article/details/284724.sHtML
- http://wap.blog.puhvjy.cn/Article/details/13906.sHtML
- http://wap.blog.nzfnve.cn/Article/details/370062.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/924611.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9003269.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/1195849.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/3616267.sHtML
- http://wap.blog.puhvjy.cn/Article/details/8988487.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7286988.sHtML
- http://wap.blog.nzfnve.cn/Article/details/34069.sHtML
- http://wap.blog.nzfnve.cn/Article/details/5834.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3767.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6839.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/63944.sHtML
- http://wap.blog.nzfnve.cn/Article/details/34129.sHtML
- http://wap.blog.puhvjy.cn/Article/details/3941937.sHtML
- http://wap.blog.nzfnve.cn/Article/details/634380.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/25996.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/336300.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/9990.sHtML
- http://wap.blog.puhvjy.cn/Article/details/315086.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9884.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/0533720.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6236.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/240675.sHtML
- http://wap.blog.puhvjy.cn/Article/details/06463.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/2950.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6187.sHtML
- http://wap.blog.puhvjy.cn/Article/details/7737833.sHtML
- http://wap.blog.puhvjy.cn/Article/details/24254.sHtML
- http://wap.blog.nzfnve.cn/Article/details/68714.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/615839.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/4739.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/141579.sHtML
- http://wap.blog.nzfnve.cn/Article/details/21240.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7063356.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/255642.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/729336.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/3258.sHtML
- http://wap.blog.puhvjy.cn/Article/details/563292.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3420013.sHtML
- http://wap.blog.nzfnve.cn/Article/details/69124.sHtML
- http://wap.blog.puhvjy.cn/Article/details/8104135.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/525853.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5074891.sHtML
- http://wap.blog.nzfnve.cn/Article/details/577328.sHtML
- http://wap.blog.nzfnve.cn/Article/details/44712.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/257654.sHtML
- http://wap.blog.nzfnve.cn/Article/details/42967.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0952.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/121119.sHtML
- http://wap.blog.nzfnve.cn/Article/details/76007.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/4343.sHtML
- http://wap.blog.nzfnve.cn/Article/details/79365.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7617705.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/99157.sHtML
- http://wap.blog.puhvjy.cn/Article/details/467067.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/1623.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6555.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4500522.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6597.sHtML
- http://wap.blog.nzfnve.cn/Article/details/847990.sHtML
- http://wap.blog.nzfnve.cn/Article/details/2425.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9641.sHtML
- http://wap.blog.nzfnve.cn/Article/details/029112.sHtML
- http://wap.blog.nzfnve.cn/Article/details/88452.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/00883.sHtML
- http://wap.blog.nzfnve.cn/Article/details/22831.sHtML
- http://wap.blog.nzfnve.cn/Article/details/858978.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5233524.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/2718.sHtML
- http://wap.blog.nzfnve.cn/Article/details/852429.sHtML
- http://wap.blog.puhvjy.cn/Article/details/057864.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/959920.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/6298966.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/70500.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/737125.sHtML
- http://wap.blog.puhvjy.cn/Article/details/600293.sHtML
- http://wap.blog.nzfnve.cn/Article/details/1416.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3470346.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0046120.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/4211750.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7671037.sHtML
- http://wap.blog.puhvjy.cn/Article/details/190791.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/300210.sHtML
- http://wap.blog.puhvjy.cn/Article/details/0529.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9889782.sHtML
- http://wap.blog.puhvjy.cn/Article/details/098412.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/1412004.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/1510.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/04651.sHtML
- http://wap.blog.nzfnve.cn/Article/details/212560.sHtML
- http://wap.blog.nzfnve.cn/Article/details/7060.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/880093.sHtML
- http://wap.blog.puhvjy.cn/Article/details/4860.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/316810.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/460695.sHtML
- http://wap.blog.puhvjy.cn/Article/details/535272.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3293028.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4150457.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5589113.sHtML
- http://wap.blog.puhvjy.cn/Article/details/044936.sHtML
- http://wap.blog.nzfnve.cn/Article/details/036901.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/5279.sHtML
- http://wap.blog.puhvjy.cn/Article/details/56257.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/191809.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/449662.sHtML
- http://wap.blog.puhvjy.cn/Article/details/3672089.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/06726.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/885184.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6727.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/75025.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/1787.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4113.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/1426960.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/6712.sHtML
- http://wap.blog.puhvjy.cn/Article/details/4969.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9264956.sHtML
- http://wap.blog.puhvjy.cn/Article/details/2049.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/2781.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/5812585.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/76620.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/0264.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/95539.sHtML
- http://wap.blog.nzfnve.cn/Article/details/4293392.sHtML
- http://wap.blog.puhvjy.cn/Article/details/519139.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5500348.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/7113086.sHtML
- http://wap.blog.nzfnve.cn/Article/details/808140.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/474094.sHtML
- http://wap.blog.puhvjy.cn/Article/details/03952.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/38202.sHtML
- http://wap.blog.puhvjy.cn/Article/details/59044.sHtML
- http://wap.blog.puhvjy.cn/Article/details/854377.sHtML
- http://wap.blog.nzfnve.cn/Article/details/8283498.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/2927749.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/130576.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/0541.sHtML
- http://wap.blog.nzfnve.cn/Article/details/8276181.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7295.sHtML
- http://wap.blog.puhvjy.cn/Article/details/049990.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3560.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7981263.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0911918.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/2751.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/33045.sHtML
- http://wap.blog.puhvjy.cn/Article/details/79908.sHtML
- http://wap.blog.nzfnve.cn/Article/details/73240.sHtML
- http://wap.blog.puhvjy.cn/Article/details/2559260.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/4853863.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1973.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0125301.sHtML
- http://wap.blog.nzfnve.cn/Article/details/085527.sHtML
- http://wap.blog.nzfnve.cn/Article/details/038143.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0029169.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/8796865.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3777472.sHtML
- http://wap.blog.puhvjy.cn/Article/details/6170640.sHtML
- http://wap.blog.puhvjy.cn/Article/details/0658.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1033.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1603132.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9801.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/0615190.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5775038.sHtML
- http://wap.blog.puhvjy.cn/Article/details/86556.sHtML
- http://wap.blog.nzfnve.cn/Article/details/95265.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/7877572.sHtML
- http://wap.blog.puhvjy.cn/Article/details/5883.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/9479231.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/79106.sHtML
- http://wap.blog.nzfnve.cn/Article/details/69982.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/24033.sHtML
- http://wap.blog.puhvjy.cn/Article/details/287357.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/4146874.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/58496.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/03945.sHtML
- http://wap.blog.nzfnve.cn/Article/details/5785134.sHtML
- http://wap.blog.puhvjy.cn/Article/details/628795.sHtML
- http://wap.blog.puhvjy.cn/Article/details/29721.sHtML
- http://wap.blog.puhvjy.cn/Article/details/0299412.sHtML
- http://wap.blog.puhvjy.cn/Article/details/9659302.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/698603.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1385292.sHtML
- http://wap.blog.puhvjy.cn/Article/details/1185288.sHtML
- http://wap.blog.puhvjy.cn/Article/details/104952.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5923628.sHtML
- http://wap.blog.puhvjy.cn/Article/details/2087014.sHtML
- http://wap.blog.nzfnve.cn/Article/details/982082.sHtML
- http://wap.blog.puhvjy.cn/Article/details/7645357.sHtML
- http://wap.blog.puhvjy.cn/Article/details/48658.sHtML
- http://wap.blog.puhvjy.cn/Article/details/557672.sHtML
- http://wap.blog.nzfnve.cn/Article/details/9384.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3238096.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/90229.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/5551838.sHtML
- http://wap.blog.puhvjy.cn/Article/details/7960.sHtML
- http://wap.blog.puhvjy.cn/Article/details/4246006.sHtML
- http://wap.blog.nzfnve.cn/Article/details/077482.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/58636.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/9051.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/99004.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/90014.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6839.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/34936.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/051107.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/7931.sHtML
- http://wap.blog.nzfnve.cn/Article/details/131258.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/4161167.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/21073.sHtML
- http://wap.blog.puhvjy.cn/Article/details/460508.sHtML
- http://wap.blog.nzfnve.cn/Article/details/09689.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/15071.sHtML
- http://wap.blog.puhvjy.cn/Article/details/7396027.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/9308.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/8948.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/3864057.sHtML
- http://wap.blog.nzfnve.cn/Article/details/77462.sHtML
- http://wap.blog.nzfnve.cn/Article/details/87923.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/6428.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/13614.sHtML
- http://wap.blog.nzfnve.cn/Article/details/0571.sHtML
- http://wap.blog.puhvjy.cn/Article/details/368109.sHtML
- http://wap.blog.nzfnve.cn/Article/details/113995.sHtML
- http://wap.blog.nzfnve.cn/Article/details/68338.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/7257461.sHtML
- http://wap.blog.nzfnve.cn/Article/details/312950.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/1280.sHtML
- http://wap.blog.nzfnve.cn/Article/details/5367.sHtML
- http://wap.blog.puhvjy.cn/Article/details/34298.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/866493.sHtML
- http://wap.blog.puhvjy.cn/Article/details/04096.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/89395.sHtML
- http://wap.blog.nzfnve.cn/Article/details/3528.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/747180.sHtML
- http://wap.blog.nwbbyt.cn/Article/details/272904.sHtML
- http://wap.blog.nzfnve.cn/Article/details/6493.sHtML
- http://wap.blog.nzfnve.cn/Article/details/405409.sHtML
- http://wap.blog.jnjpgf.cn/Article/details/91026.sHtML
- http://wap.blog.puhvjy.cn/Article/details/21243.sHtML
- http://wap.blog.puhvjy.cn/Article/details/551949.sHtML
- http://wap.blog.puhvjy.cn/Article/details/4097.sHtML
- http://wap.blog.puhvjy.cn/Article/details/2915491.sHtML

## 项目结构

项目采用模块化设计，核心逻辑与辅助工具分离，便于维护与扩展。以下为主要的目录与文件组织结构。

```
wapblog-archive-aggregator/
├── wba.py                          # 主入口脚本，解析命令行参数并协调各模块执行
├── config.yaml                     # 全局配置文件，包含线程数、超时时间、重试策略等
├── requirements.txt                # Python 依赖清单，固定版本号以保证环境一致性
├── src/                            # 核心源码目录
│   ├── core/                       # 核心处理模块
│   │   ├── fetcher.py              # 负责发起 HTTP 请求并返回响应对象与元数据
│   │   ├── parser.py               # 解析 HTML 内容提取标题、描述等文本信息
│   │   └── validator.py            # 验证 URL 格式、去重、过滤非法协议
│   ├── engine/                     # 调度与并发引擎
│   │   ├── pool.py                 # 实现线程池管理与任务队列分发
│   │   ├── scheduler.py            # 定义增量扫描、全量扫描等执行策略
│   │   └── tracker.py              # 记录任务执行状态与进度
│   ├── export/                     # 结果导出模块
│   │   ├── json_exporter.py        # 导出为 JSON 格式，保留完整元数据
│   │   ├── csv_exporter.py         # 导出为 CSV 表格，便于电子表格软件打开
│   │   └── markdown_exporter.py    # 生成 Markdown 格式报告，适合直接插入文档
│   └── utils/                      # 通用工具函数集
│       ├── logger.py               # 日志配置与分级输出
│       ├── network.py              # 代理检测、网络连通性测试
│       └── file_ops.py             # 文件读写、路径规范化、目录创建
├── tests/                          # 测试套件
│   ├── unit/                       # 单元测试，覆盖各模块核心函数
│   ├── integration/                # 集成测试，模拟真实运行场景
│   └── fixtures/                   # 测试用的固定样本数据与预期结果
├── docs/                           # 项目文档
│   ├── user_guide.md               # 用户手册，从安装到高级用法的完整说明
│   ├── configuration.md            # 配置项详解与示例
│   ├── development.md              # 开发者指南，包含代码规范与提交流程
│   └── recipes.md                  # 常见任务的操作配方
└── samples/                        # 示例输入输出文件
    ├── sample_links.txt            # 示例输入链接列表
    ├── sample_report.json          # 示例输出 JSON 报告
    └── sample_report.csv           # 示例输出 CSV 表格
```

## 贡献指南

我们欢迎开发者以多种方式参与本项目。请遵循以下步骤提交代码、文档或问题报告。

1. 在 GitHub 上 fork 本仓库，并克隆到本地开发环境。建议在 dev 分支上进行修改，保持主分支与上游同步。
2. 安装开发依赖，包括 pytest、black、flake8 等代码质量工具。运行 `pip install -r requirements-dev.txt` 完成安装。
3. 编写或修改代码后，确保所有现有单元测试通过，并为新功能或修复补充相应的测试用例。使用 `pytest tests/` 执行全部测试。
4. 提交代码前运行代码格式化工具 black 和静态检查工具 flake8，保持代码风格一致且无潜在语法错误。
5. 发起 Pull Request 到主仓库的 dev 分支，并在描述中清晰说明修改内容、关联 issue 以及测试覆盖情况。项目维护者将在审阅后合并。

## 常见问题

**Q: 扫描过程中大量链接返回超时或连接错误，应如何优化？**

A: 可以尝试以下几种方式。首先降低并发线程数，避免对目标服务器造成过大压力。其次增加每次请求的超时时间，通过 --timeout 参数调整，默认值为 10 秒。最后可以配置代理参数 --proxy，使用稳定的代理池转发请求。如果目标站点有反爬机制，建议自定义 User-Agent 并启用会话持久化。

**Q: 增量扫描模式如何工作，第一次运行需要全量扫描吗？**

A: 增量扫描依赖上次运行生成的 JSON 结果文件。首次运行时必须使用全量扫描模式，生成基准结果文件。后续运行时可指定 --incremental 参数并传入上次的结果文件路径，程序将仅对新增链接或上次状态为失败的链接重新探测，有效减少不必要的网络请求。

**Q: 导出的 JSON 和 CSV 结果中包含哪些字段，如何解读状态码？**

A: 每条记录包含 url、status、status_code、content_type、content_length、last_modified、title、timestamp 等字段。status 字段为枚举值，包括 active（正常访问）、redirect（重定向）、timeout（超时）、error（连接错误）、forbidden（禁止访问）、not_found（404）。status_code 为原始 HTTP 响应码。建议结合 status 与 status_code 综合判断链接可用性。

## 许可证

MIT License

Copyright (c) 2026 WapBlog Archive Aggregator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
