# H5 Blog Archive Aggregator

H5 Blog Archive Aggregator 是一个面向技术博客、开发日志与知识碎片的高效外链聚合与归档管理工具。项目定位于为个人开发者、技术内容创作者及小型团队提供一套轻量级的文章引用索引系统，用于统一管理分布在多个独立博客站点上的历史技术文章。通过集中式的外链登记与分类索引，用户能够快速定位特定主题、特定时间段内的技术笔记与问题解决方案，避免因博客站点迁移、链接失效或内容散落导致的知识资产流失。

本项目本质上是一个基于静态外链列表的知识导航系统，不存储任何文章正文内容，仅记录文章标题、来源域名、发布时间及原始访问链接。目标用户包括长期撰写技术博客的工程师、维护多个专题内容站点的站长，以及需要对外输出技术资源清单的团队负责人。系统设计上强调快速检索、清晰归类与原始来源可追溯性，适用于中小规模技术知识库的整理与公开分享。

## 功能概览

**多站点外链统一登记**：支持将来自不同二级域名的博客文章链接批量录入系统，自动识别来源站点并归类，无需手动整理域名清单。

**按文章ID与域名双重检索**：提供基于文章数字ID和来源域名的快速过滤能力，用户可输入任意已知参数定位目标记录，提升日常查阅效率。

**原始链接直出模式**：所有收录的外链均保留最原始的访问地址，包括协议类型、域名格式及大小写后缀，确保跳转路径与用户预期完全一致，杜绝因链接改写导致的访问异常。

**轻量级静态资源索引**：采用纯文本列表形式存储所有链接记录，无需数据库依赖，降低部署与维护成本，同时便于版本控制系统追踪变更历史。

**分类标签与备注扩展**：每条链接记录支持附加自定义标签（如Python、运维、前端）和简短备注说明，辅助用户在不点开原文的情况下快速了解文章核心内容。

**批量导入与导出支持**：提供基于纯文本列表的批量链接导入功能，以及按筛选条件导出子集的能力，方便用户与其他系统进行数据交换。

**开源可审计的代码基础**：整个项目源码完全公开，用户可自行审计链接处理逻辑，确保没有额外追踪脚本或隐私收集行为，适合对数据安全有要求的部署场景。

## 应用场景

个人技术博客归档整理：当开发者多年间在多个不同博客平台上发表过技术文章，且各平台账号分散难以统一回顾时，可使用本项目将所有历史文章的外链汇总到一个索引文件中，并按照年份或技术领域添加标签，从而形成个人完整的技术写作时间线。

团队内部知识库外链聚合：研发团队在解决特定技术难题时，往往会在临时wiki、工单系统或邮件中引用大量外部文章。利用本项目的链接登记功能，团队可将这些散落的外部引用统一收录，并备注每个链接对应的问题场景，便于后续同类问题出现时快速查阅参考资料。

技术资源清单对外发布：开源项目维护者或技术社区运营人员，在撰写项目文档或社区导航页面时，需要列出大量外部参考链接。本项目提供的纯外链列表输出模式，可直接嵌入到项目README或站点导航中，保证链接格式干净、无额外干扰元素。

## 快速开始

以下操作步骤适用于Linux/macOS及Windows WSL环境，确保系统已安装Git和Python 3.8以上版本。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/h5-blog-archive-aggregator.git

# 进入项目根目录
cd h5-blog-archive-aggregator

# 安装Python依赖（使用虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行索引构建脚本，生成外链汇总页面
python build_index.py --input data/links.txt --output dist/index.html

# 启动本地预览服务（默认端口8000）
python -m http.server --directory dist
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 用于运行索引构建与链接校验脚本 |
| Git | 2.25 及以上 | 用于克隆仓库及版本管理 |
| pip | 20.0 及以上 | Python包管理工具，用于安装依赖库 |
| setuptools | 50.0 及以上 | 构建脚本依赖的基础工具包 |
| markdown | 3.3.0 及以上 | 用于将链接列表渲染为HTML页面 |
| jinja2 | 3.0.0 及以上 | 模板引擎，用于生成汇总页面的动态内容 |
| pytest | 7.0.0 及以上 | 可选，仅当需要运行单元测试时安装 |
| black | 22.0.0 及以上 | 可选，用于代码风格格式化检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/quick-start.md | 如何用最少步骤完成项目部署并生成第一个外链索引页面 |
| 链接格式规范 | docs/link-format-spec.md | 原始链接应遵循何种格式要求，哪些字符需要转义或保留 |
| 自定义分类规则 | docs/custom-taxonomy.md | 如何调整标签分类逻辑以及添加自定义元数据字段 |
| 高级过滤查询 | docs/advanced-filtering.md | 如何使用组合条件从大量链接中精确筛选目标记录 |
| 版本升级日志 | CHANGELOG.md | 每个版本的更新内容、API变动及迁移注意事项 |

## 资源列表

- http://h5.blog.jnjpgf.cn/Article/details/5283548.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5595.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6932541.sHtML
- http://h5.blog.puhvjy.cn/Article/details/493026.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6058.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2012.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0179.sHtML
- http://h5.blog.puhvjy.cn/Article/details/652608.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/09921.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2422.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7101352.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3832510.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5380796.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3470603.sHtML
- http://h5.blog.puhvjy.cn/Article/details/80794.sHtML
- http://h5.blog.nzfnve.cn/Article/details/02653.sHtML
- http://h5.blog.puhvjy.cn/Article/details/867640.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0566.sHtML
- http://h5.blog.nzfnve.cn/Article/details/069990.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/45986.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8975691.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2206638.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/09090.sHtML
- http://h5.blog.puhvjy.cn/Article/details/29366.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4266.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3901.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5569.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7390.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2543128.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6793130.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6075.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/145095.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/87666.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4411790.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/660036.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/63399.sHtML
- http://h5.blog.nzfnve.cn/Article/details/552333.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2712.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2406.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/95252.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/70121.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/527964.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9717021.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8244.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5883668.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/430216.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2092.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4957.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/663808.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9865.sHtML
- http://h5.blog.puhvjy.cn/Article/details/22613.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/88961.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1477.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9009.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/934368.sHtML
- http://h5.blog.nzfnve.cn/Article/details/828851.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/82655.sHtML
- http://h5.blog.puhvjy.cn/Article/details/22284.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/41934.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3766.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5723389.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/019024.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/801301.sHtML
- http://h5.blog.nzfnve.cn/Article/details/460895.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0145.sHtML
- http://h5.blog.puhvjy.cn/Article/details/45891.sHtML
- http://h5.blog.nzfnve.cn/Article/details/43685.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/99776.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3019.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/238565.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3709.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3556808.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9212.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9568.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3122.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/95449.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9990.sHtML
- http://h5.blog.nzfnve.cn/Article/details/977608.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2745614.sHtML
- http://h5.blog.nzfnve.cn/Article/details/49331.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6835696.sHtML
- http://h5.blog.puhvjy.cn/Article/details/84133.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1860155.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/22542.sHtML
- http://h5.blog.nzfnve.cn/Article/details/11588.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/651140.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/634430.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/104544.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6989.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/76699.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8677475.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5520.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7688.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4439084.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6505.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7844.sHtML
- http://h5.blog.puhvjy.cn/Article/details/48705.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2435950.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7655.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/389455.sHtML
- http://h5.blog.puhvjy.cn/Article/details/54245.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9353.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/10748.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/69884.sHtML
- http://h5.blog.puhvjy.cn/Article/details/52296.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/937059.sHtML
- http://h5.blog.nzfnve.cn/Article/details/63707.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/257058.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9833458.sHtML
- http://h5.blog.nzfnve.cn/Article/details/25992.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/585756.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8176625.sHtML
- http://h5.blog.nzfnve.cn/Article/details/120520.sHtML
- http://h5.blog.nzfnve.cn/Article/details/07613.sHtML
- http://h5.blog.puhvjy.cn/Article/details/48418.sHtML
- http://h5.blog.nzfnve.cn/Article/details/15262.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/44181.sHtML
- http://h5.blog.nzfnve.cn/Article/details/48632.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/12341.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3999.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0035.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2986.sHtML
- http://h5.blog.nzfnve.cn/Article/details/84126.sHtML
- http://h5.blog.nzfnve.cn/Article/details/31050.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/521524.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/042563.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1254.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5640184.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7643991.sHtML
- http://h5.blog.puhvjy.cn/Article/details/469832.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7788.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8415490.sHtML
- http://h5.blog.nzfnve.cn/Article/details/732398.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5254.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/060719.sHtML
- http://h5.blog.puhvjy.cn/Article/details/20297.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9526.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/746365.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6961.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4699631.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/36755.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/95577.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/71916.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2255820.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5311223.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5419461.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/486114.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6122262.sHtML
- http://h5.blog.puhvjy.cn/Article/details/98614.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/990926.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/374656.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6828349.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5028.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2308865.sHtML
- http://h5.blog.puhvjy.cn/Article/details/290322.sHtML
- http://h5.blog.puhvjy.cn/Article/details/12837.sHtML
- http://h5.blog.puhvjy.cn/Article/details/28279.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6019622.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9691.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9576.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9449.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3893.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8841081.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3537.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6151.sHtML
- http://h5.blog.puhvjy.cn/Article/details/99970.sHtML
- http://h5.blog.puhvjy.cn/Article/details/197178.sHtML
- http://h5.blog.puhvjy.cn/Article/details/431087.sHtML
- http://h5.blog.nzfnve.cn/Article/details/28724.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8980265.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9806097.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4839338.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8636109.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8279.sHtML
- http://h5.blog.puhvjy.cn/Article/details/751922.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1705.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1448989.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4348.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3029.sHtML
- http://h5.blog.puhvjy.cn/Article/details/45365.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5107312.sHtML
- http://h5.blog.nzfnve.cn/Article/details/1838311.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/6780.sHtML
- http://h5.blog.puhvjy.cn/Article/details/413481.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/62495.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5603534.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/32192.sHtML
- http://h5.blog.puhvjy.cn/Article/details/39549.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/84157.sHtML
- http://h5.blog.nzfnve.cn/Article/details/73960.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/98832.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6225.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5117437.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/41994.sHtML
- http://h5.blog.puhvjy.cn/Article/details/489006.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/93371.sHtML
- http://h5.blog.nzfnve.cn/Article/details/550392.sHtML
- http://h5.blog.nzfnve.cn/Article/details/89029.sHtML
- http://h5.blog.puhvjy.cn/Article/details/285485.sHtML
- http://h5.blog.nzfnve.cn/Article/details/076077.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/036391.sHtML
- http://h5.blog.puhvjy.cn/Article/details/73292.sHtML
- http://h5.blog.puhvjy.cn/Article/details/61468.sHtML
- http://h5.blog.nzfnve.cn/Article/details/548132.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3280.sHtML
- http://h5.blog.puhvjy.cn/Article/details/950935.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/721657.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/06310.sHtML
- http://h5.blog.puhvjy.cn/Article/details/27453.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0265677.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/87693.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2565353.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/41893.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4637.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/71165.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6467649.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6009560.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/776016.sHtML
- http://h5.blog.puhvjy.cn/Article/details/746450.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1125495.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0121.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4815.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/77200.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/272966.sHtML
- http://h5.blog.puhvjy.cn/Article/details/154524.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3118.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/60587.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5610.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2815.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/113718.sHtML
- http://h5.blog.nzfnve.cn/Article/details/78257.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/98700.sHtML
- http://h5.blog.nzfnve.cn/Article/details/446717.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7787082.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/22049.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/085111.sHtML
- http://h5.blog.puhvjy.cn/Article/details/19560.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/56050.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0919.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4444.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/070905.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7465281.sHtML
- http://h5.blog.nzfnve.cn/Article/details/95231.sHtML
- http://h5.blog.puhvjy.cn/Article/details/394369.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0069.sHtML
- http://h5.blog.puhvjy.cn/Article/details/19573.sHtML
- http://h5.blog.nzfnve.cn/Article/details/65077.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5929849.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/26046.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6655896.sHtML

## 项目结构

```
h5-blog-archive-aggregator/
├── data/                               # 原始数据目录
│   ├── links.txt                       # 主链接列表文件，每行一条原始URL
│   ├── categories.yaml                 # 分类映射配置，定义域名与标签的对应关系
│   └── metadata/                       # 文章元数据扩展目录
│       ├── 5283548.yaml                # 按文章ID存储的备注与标签信息
│       └── 5595.yaml
├── src/                                # 核心源代码
│   ├── build_index.py                  # 索引构建主脚本
│   ├── link_parser.py                  # 链接解析与校验模块
│   ├── template_engine.py              # Jinja2模板渲染封装
│   └── filters/                        # 自定义Jinja过滤器
│       ├── domain_extract.py           # 从URL中提取域名
│       └── sort_by_id.py               # 按文章ID数字排序
├── templates/                          # HTML模板文件
│   ├── base.html                       # 基础布局模板
│   ├── index.html                      # 汇总页模板
│   └── detail.html                     # 单篇文章详情页模板（预留）
├── dist/                               # 构建输出目录（自动生成）
│   ├── index.html                      # 生成的汇总页面
│   └── assets/                         # 静态资源
│       ├── style.css
│       └── script.js
├── tests/                              # 单元测试目录
│   ├── test_link_parser.py
│   └── test_filters.py
├── docs/                               # 文档目录
│   ├── quick-start.md
│   ├── link-format-spec.md
│   └── custom-taxonomy.md
├── requirements.txt                    # Python依赖清单
├── setup.py                            # 项目安装配置
└── README.md                           # 本文件
```

## 贡献指南

贡献者需遵守以下流程以确保链接索引的准确性与代码质量：

1. 复刻项目仓库至个人账号，并在本地创建功能分支。分支命名建议采用 feature/功能简述 或 fix/问题简述 格式，便于后续追溯。

2. 在 data/links.txt 文件中追加新链接时，必须确保每条链接单独占据一行，且严格遵循原始URL格式要求，不得添加额外描述性文字或Markdown语法符号。如需为链接添加分类标签或备注，请在 metadata/ 目录下创建对应的YAML文件，文件名与文章ID保持一致。

3. 提交代码前，需在本地运行 pytest 命令确保所有单元测试通过，同时执行 black src/ 进行代码风格格式化。若新增了功能模块，应在 tests/ 目录下补充对应的测试用例。

4. 发起合并请求时，请在描述中明确说明本次变更的内容范围，包括新增链接的数量、涉及的域名分类，以及是否对构建脚本或模板逻辑产生了影响。若变更涉及链接格式解析规则的调整，需同步更新 docs/link-format-spec.md 文档。

5. 项目维护者将在收到合并请求后的五个工作日内进行审查，如有修改意见将通过评论反馈。贡献者需在收到反馈后及时更新分支，直至变更被合并或关闭。

## 常见问题

问：为什么收录的链接访问时返回404错误？

答：本项目仅作为外链索引工具，不负责验证链接的实时可用性。部分历史文章可能因源站点迁移、内容删除或域名过期而无法访问。建议用户在收录链接前自行确认目标地址的有效性。若确认链接已永久失效，可在 metadata 目录下对应的YAML文件中标记 status: dead 以便后续筛选。

问：能否修改链接的输出格式，例如添加超链接标签或缩短显示？

答：根据项目的设计原则，所有链接必须以原始形态原样输出，不添加任何HTML标签、Markdown链接语法或URL缩短处理。这是为了保证跳转路径的确定性，避免因格式转换导致的访问异常。若需展示可点击的链接，请使用项目生成的HTML页面，其中已包含自动超链接化处理，但底层数据文件始终保持纯文本原始格式。

问：如何对链接进行分类或添加自定义标签？

答：分类标签功能通过 data/categories.yaml 和 metadata/ 目录下的YAML文件共同实现。首先在 categories.yaml 中定义域名级别的默认分类规则，然后在具体文章ID对应的YAML文件中通过 tags 字段覆盖或补充个性化标签。构建脚本会自动合并这两层配置，并在生成的汇总页面中展示。详细语法请参考 docs/custom-taxonomy.md 文档。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
