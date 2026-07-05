# WebMap 技术资源索引

WebMap 是一个面向开发者、技术研究人员与内容策展人的轻量级技术文章聚合与导航系统。项目定位于对分散在多个技术博客子域名下的历史文章、笔记与案例进行统一发现、分类检索与快速引用。WebMap 不提供内容托管，而是作为结构化导航层，将大量存量技术链接以可维护、可检索、可共享的方式重新组织，适用于个人知识库建设、团队技术文档索引补充以及公开课资料的外部参考挂载。

目标用户包括需要频繁查阅技术细节的研发工程师、撰写技术报告的研究人员以及希望系统性整理外部参考资料的技术作者。WebMap 通过固定目录结构、分类映射规则与离线可用的导航页面，帮助用户从大量原始链接中快速定位到相关文章，减少重复搜索成本。

## 功能概览

**多源链接统一收录**：支持将多个独立博客子域名下的文章详情页链接按来源域名与文章编号进行归集，提供统一的条目管理界面。

**分类标签自动推断**：根据链接中的域名和路径模式，自动为每一条记录打上来源标签与内容类型标签，便于后续按主题筛选。

**全文检索与过滤**：内置简单的关键词检索能力，支持按域名、文章编号范围、推测发布时间等维度进行组合过滤，快速缩小目标范围。

**结构化目录树导出**：可将全部链接按域名分组导出为带注释的目录树结构，方便嵌入到项目文档或静态站点生成器中。

**可扩展数据导入接口**：支持通过 CSV 或 JSON 格式批量导入新增链接，并自动校验 URL 合法性，防止重复条目。

**多格式输出支持**：除 Markdown 列表外，可生成 HTML 静态导航页、JSON API 数据文件以及 TOML 配置文件，适配不同静态站点生成工具。

**离线缓存与增量更新**：提供本地缓存机制，对已收录链接进行增量检查，仅处理新增或变更的记录，提高大批量数据维护效率。

**权限分级管理**：内置管理员与普通用户两种角色，管理员可进行链接增删改查与分类编辑，普通用户仅可检索与查看。

## 应用场景

**个人知识库外部引用整理**：开发者可将经常查阅的第三方技术文章链接统一录入 WebMap，并按照 Java 后端、前端工程、数据库调优等主题分类，在撰写设计文档时快速引用。

**团队技术周报素材聚合**：技术负责人或周报编辑可将多个博客源中值得阅读的文章链接一次性导入 WebMap，生成带分类的推荐阅读列表，作为周报附件分发给团队成员。

**公开课或培训资料参考附录**：讲师在准备课程讲义时，可将涉及到的外部扩展阅读链接全部收录至 WebMap，按课时或知识点章节导出为结构化附录，方便学员课后查阅。

**遗留系统文档迁移辅助**：在技术债务清理或系统重构过程中，团队可将散落在各个旧博客中的设计笔记、故障复盘链接通过 WebMap 统一归档，避免因博客下线导致关键信息丢失。

## 快速开始

以下命令演示如何获取 WebMap 源码、安装依赖并启动开发服务。

```bash
git clone https://github.com/webmap-dev/webmap.git
cd webmap
npm install
npm run build
npm start
```

执行完上述步骤后，访问控制台输出的本地地址即可进入 WebMap 导航管理界面。首次启动会自动创建示例数据目录与配置文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理工具，与 Node.js 捆绑 |
| SQLite3 | 3.40 及以上 | 嵌入式数据库，用于存储链接索引与分类元数据 |
| Git | 2.30 及以上 | 用于克隆仓库和版本管理 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 跨平台支持，生产环境推荐 Linux |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何录入链接、如何进行检索、如何导出导航页 |
| 管理员指南 | /docs/admin-guide/ | 如何配置权限、如何执行增量更新、如何备份数据 |
| 开发者文档 | /docs/developer-guide/ | 数据模型设计、插件扩展接口、API 文档 |
| 部署运维 | /docs/deployment/ | 生产环境部署方案、性能调优参数、监控指标说明 |

## 资源列表

- http://map.blog.jnjpgf.cn/Article/details/5283548.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5595.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6932541.sHtML
- http://map.blog.puhvjy.cn/Article/details/493026.sHtML
- http://map.blog.puhvjy.cn/Article/details/6058.sHtML
- http://map.blog.nzfnve.cn/Article/details/2012.sHtML
- http://map.blog.nzfnve.cn/Article/details/0179.sHtML
- http://map.blog.puhvjy.cn/Article/details/652608.sHtML
- http://map.blog.jnjpgf.cn/Article/details/09921.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2422.sHtML
- http://map.blog.nzfnve.cn/Article/details/7101352.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3832510.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5380796.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3470603.sHtML
- http://map.blog.puhvjy.cn/Article/details/80794.sHtML
- http://map.blog.nzfnve.cn/Article/details/02653.sHtML
- http://map.blog.puhvjy.cn/Article/details/867640.sHtML
- http://map.blog.nzfnve.cn/Article/details/0566.sHtML
- http://map.blog.nzfnve.cn/Article/details/069990.sHtML
- http://map.blog.jnjpgf.cn/Article/details/45986.sHtML
- http://map.blog.nzfnve.cn/Article/details/8975691.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2206638.sHtML
- http://map.blog.jnjpgf.cn/Article/details/09090.sHtML
- http://map.blog.puhvjy.cn/Article/details/29366.sHtML
- http://map.blog.puhvjy.cn/Article/details/4266.sHtML
- http://map.blog.nzfnve.cn/Article/details/3901.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5569.sHtML
- http://map.blog.nzfnve.cn/Article/details/7390.sHtML
- http://map.blog.puhvjy.cn/Article/details/2543128.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6793130.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6075.sHtML
- http://map.blog.nwbbyt.cn/Article/details/145095.sHtML
- http://map.blog.nwbbyt.cn/Article/details/87666.sHtML
- http://map.blog.puhvjy.cn/Article/details/4411790.sHtML
- http://map.blog.nwbbyt.cn/Article/details/660036.sHtML
- http://map.blog.jnjpgf.cn/Article/details/63399.sHtML
- http://map.blog.nzfnve.cn/Article/details/552333.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2712.sHtML
- http://map.blog.puhvjy.cn/Article/details/2406.sHtML
- http://map.blog.jnjpgf.cn/Article/details/95252.sHtML
- http://map.blog.nwbbyt.cn/Article/details/70121.sHtML
- http://map.blog.jnjpgf.cn/Article/details/527964.sHtML
- http://map.blog.puhvjy.cn/Article/details/9717021.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8244.sHtML
- http://map.blog.puhvjy.cn/Article/details/5883668.sHtML
- http://map.blog.jnjpgf.cn/Article/details/430216.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2092.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4957.sHtML
- http://map.blog.jnjpgf.cn/Article/details/663808.sHtML
- http://map.blog.puhvjy.cn/Article/details/9865.sHtML
- http://map.blog.puhvjy.cn/Article/details/22613.sHtML
- http://map.blog.nwbbyt.cn/Article/details/88961.sHtML
- http://map.blog.puhvjy.cn/Article/details/1477.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9009.sHtML
- http://map.blog.nwbbyt.cn/Article/details/934368.sHtML
- http://map.blog.nzfnve.cn/Article/details/828851.sHtML
- http://map.blog.jnjpgf.cn/Article/details/82655.sHtML
- http://map.blog.puhvjy.cn/Article/details/22284.sHtML
- http://map.blog.jnjpgf.cn/Article/details/41934.sHtML
- http://map.blog.nzfnve.cn/Article/details/3766.sHtML
- http://map.blog.nzfnve.cn/Article/details/5723389.sHtML
- http://map.blog.nwbbyt.cn/Article/details/019024.sHtML
- http://map.blog.nwbbyt.cn/Article/details/801301.sHtML
- http://map.blog.nzfnve.cn/Article/details/460895.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0145.sHtML
- http://map.blog.puhvjy.cn/Article/details/45891.sHtML
- http://map.blog.nzfnve.cn/Article/details/43685.sHtML
- http://map.blog.jnjpgf.cn/Article/details/99776.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3019.sHtML
- http://map.blog.jnjpgf.cn/Article/details/238565.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3709.sHtML
- http://map.blog.nzfnve.cn/Article/details/3556808.sHtML
- http://map.blog.nzfnve.cn/Article/details/9212.sHtML
- http://map.blog.puhvjy.cn/Article/details/9568.sHtML
- http://map.blog.puhvjy.cn/Article/details/3122.sHtML
- http://map.blog.jnjpgf.cn/Article/details/95449.sHtML
- http://map.blog.puhvjy.cn/Article/details/9990.sHtML
- http://map.blog.nzfnve.cn/Article/details/977608.sHtML
- http://map.blog.nzfnve.cn/Article/details/2745614.sHtML
- http://map.blog.nzfnve.cn/Article/details/49331.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6835696.sHtML
- http://map.blog.puhvjy.cn/Article/details/84133.sHtML
- http://map.blog.puhvjy.cn/Article/details/1860155.sHtML
- http://map.blog.nwbbyt.cn/Article/details/22542.sHtML
- http://map.blog.nzfnve.cn/Article/details/11588.sHtML
- http://map.blog.nwbbyt.cn/Article/details/651140.sHtML
- http://map.blog.jnjpgf.cn/Article/details/634430.sHtML
- http://map.blog.jnjpgf.cn/Article/details/104544.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6989.sHtML
- http://map.blog.nwbbyt.cn/Article/details/76699.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8677475.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5520.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7688.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4439084.sHtML
- http://map.blog.puhvjy.cn/Article/details/6505.sHtML
- http://map.blog.puhvjy.cn/Article/details/7844.sHtML
- http://map.blog.puhvjy.cn/Article/details/48705.sHtML
- http://map.blog.nzfnve.cn/Article/details/2435950.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7655.sHtML
- http://map.blog.nwbbyt.cn/Article/details/389455.sHtML
- http://map.blog.puhvjy.cn/Article/details/54245.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9353.sHtML
- http://map.blog.nwbbyt.cn/Article/details/10748.sHtML
- http://map.blog.nwbbyt.cn/Article/details/69884.sHtML
- http://map.blog.puhvjy.cn/Article/details/52296.sHtML
- http://map.blog.jnjpgf.cn/Article/details/937059.sHtML
- http://map.blog.nzfnve.cn/Article/details/63707.sHtML
- http://map.blog.nwbbyt.cn/Article/details/257058.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9833458.sHtML
- http://map.blog.nzfnve.cn/Article/details/25992.sHtML
- http://map.blog.nwbbyt.cn/Article/details/585756.sHtML
- http://map.blog.puhvjy.cn/Article/details/8176625.sHtML
- http://map.blog.nzfnve.cn/Article/details/120520.sHtML
- http://map.blog.nzfnve.cn/Article/details/07613.sHtML
- http://map.blog.puhvjy.cn/Article/details/48418.sHtML
- http://map.blog.nzfnve.cn/Article/details/15262.sHtML
- http://map.blog.nwbbyt.cn/Article/details/44181.sHtML
- http://map.blog.nzfnve.cn/Article/details/48632.sHtML
- http://map.blog.jnjpgf.cn/Article/details/12341.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3999.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0035.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2986.sHtML
- http://map.blog.nzfnve.cn/Article/details/84126.sHtML
- http://map.blog.nzfnve.cn/Article/details/31050.sHtML
- http://map.blog.nwbbyt.cn/Article/details/521524.sHtML
- http://map.blog.nwbbyt.cn/Article/details/042563.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1254.sHtML
- http://map.blog.nzfnve.cn/Article/details/5640184.sHtML
- http://map.blog.jnjpgf.cn/Article/details/7643991.sHtML
- http://map.blog.puhvjy.cn/Article/details/469832.sHtML
- http://map.blog.puhvjy.cn/Article/details/7788.sHtML
- http://map.blog.nzfnve.cn/Article/details/8415490.sHtML
- http://map.blog.nzfnve.cn/Article/details/732398.sHtML
- http://map.blog.nzfnve.cn/Article/details/5254.sHtML
- http://map.blog.nwbbyt.cn/Article/details/060719.sHtML
- http://map.blog.puhvjy.cn/Article/details/20297.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9526.sHtML
- http://map.blog.nwbbyt.cn/Article/details/746365.sHtML
- http://map.blog.nzfnve.cn/Article/details/6961.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4699631.sHtML
- http://map.blog.nwbbyt.cn/Article/details/36755.sHtML
- http://map.blog.jnjpgf.cn/Article/details/95577.sHtML
- http://map.blog.jnjpgf.cn/Article/details/71916.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2255820.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5311223.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5419461.sHtML
- http://map.blog.jnjpgf.cn/Article/details/486114.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6122262.sHtML
- http://map.blog.puhvjy.cn/Article/details/98614.sHtML
- http://map.blog.nwbbyt.cn/Article/details/990926.sHtML
- http://map.blog.jnjpgf.cn/Article/details/374656.sHtML
- http://map.blog.nzfnve.cn/Article/details/6828349.sHtML
- http://map.blog.nzfnve.cn/Article/details/5028.sHtML
- http://map.blog.nzfnve.cn/Article/details/2308865.sHtML
- http://map.blog.puhvjy.cn/Article/details/290322.sHtML
- http://map.blog.puhvjy.cn/Article/details/12837.sHtML
- http://map.blog.puhvjy.cn/Article/details/28279.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6019622.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9691.sHtML
- http://map.blog.nzfnve.cn/Article/details/9576.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9449.sHtML
- http://map.blog.nzfnve.cn/Article/details/3893.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8841081.sHtML
- http://map.blog.nzfnve.cn/Article/details/3537.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6151.sHtML
- http://map.blog.puhvjy.cn/Article/details/99970.sHtML
- http://map.blog.puhvjy.cn/Article/details/197178.sHtML
- http://map.blog.puhvjy.cn/Article/details/431087.sHtML
- http://map.blog.nzfnve.cn/Article/details/28724.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8980265.sHtML
- http://map.blog.nzfnve.cn/Article/details/9806097.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4839338.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8636109.sHtML
- http://map.blog.puhvjy.cn/Article/details/8279.sHtML
- http://map.blog.puhvjy.cn/Article/details/751922.sHtML
- http://map.blog.puhvjy.cn/Article/details/1705.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1448989.sHtML
- http://map.blog.puhvjy.cn/Article/details/4348.sHtML
- http://map.blog.nzfnve.cn/Article/details/3029.sHtML
- http://map.blog.puhvjy.cn/Article/details/45365.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5107312.sHtML
- http://map.blog.nzfnve.cn/Article/details/1838311.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6780.sHtML
- http://map.blog.puhvjy.cn/Article/details/413481.sHtML
- http://map.blog.nwbbyt.cn/Article/details/62495.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5603534.sHtML
- http://map.blog.nwbbyt.cn/Article/details/32192.sHtML
- http://map.blog.puhvjy.cn/Article/details/39549.sHtML
- http://map.blog.nwbbyt.cn/Article/details/84157.sHtML
- http://map.blog.nzfnve.cn/Article/details/73960.sHtML
- http://map.blog.nwbbyt.cn/Article/details/98832.sHtML
- http://map.blog.nzfnve.cn/Article/details/6225.sHtML
- http://map.blog.nzfnve.cn/Article/details/5117437.sHtML
- http://map.blog.jnjpgf.cn/Article/details/41994.sHtML
- http://map.blog.puhvjy.cn/Article/details/489006.sHtML
- http://map.blog.jnjpgf.cn/Article/details/93371.sHtML
- http://map.blog.nzfnve.cn/Article/details/550392.sHtML
- http://map.blog.nzfnve.cn/Article/details/89029.sHtML
- http://map.blog.puhvjy.cn/Article/details/285485.sHtML
- http://map.blog.nzfnve.cn/Article/details/076077.sHtML
- http://map.blog.jnjpgf.cn/Article/details/036391.sHtML
- http://map.blog.puhvjy.cn/Article/details/73292.sHtML
- http://map.blog.puhvjy.cn/Article/details/61468.sHtML
- http://map.blog.nzfnve.cn/Article/details/548132.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3280.sHtML
- http://map.blog.puhvjy.cn/Article/details/950935.sHtML
- http://map.blog.nwbbyt.cn/Article/details/721657.sHtML
- http://map.blog.nwbbyt.cn/Article/details/06310.sHtML
- http://map.blog.puhvjy.cn/Article/details/27453.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0265677.sHtML
- http://map.blog.jnjpgf.cn/Article/details/87693.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2565353.sHtML
- http://map.blog.nwbbyt.cn/Article/details/41893.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4637.sHtML
- http://map.blog.nwbbyt.cn/Article/details/71165.sHtML
- http://map.blog.puhvjy.cn/Article/details/6467649.sHtML
- http://map.blog.nzfnve.cn/Article/details/6009560.sHtML
- http://map.blog.jnjpgf.cn/Article/details/776016.sHtML
- http://map.blog.puhvjy.cn/Article/details/746450.sHtML
- http://map.blog.puhvjy.cn/Article/details/1125495.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0121.sHtML
- http://map.blog.nzfnve.cn/Article/details/4815.sHtML
- http://map.blog.nwbbyt.cn/Article/details/77200.sHtML
- http://map.blog.nwbbyt.cn/Article/details/272966.sHtML
- http://map.blog.puhvjy.cn/Article/details/154524.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3118.sHtML
- http://map.blog.nwbbyt.cn/Article/details/60587.sHtML
- http://map.blog.nzfnve.cn/Article/details/5610.sHtML
- http://map.blog.puhvjy.cn/Article/details/2815.sHtML
- http://map.blog.nwbbyt.cn/Article/details/113718.sHtML
- http://map.blog.nzfnve.cn/Article/details/78257.sHtML
- http://map.blog.jnjpgf.cn/Article/details/98700.sHtML
- http://map.blog.nzfnve.cn/Article/details/446717.sHtML
- http://map.blog.nzfnve.cn/Article/details/7787082.sHtML
- http://map.blog.jnjpgf.cn/Article/details/22049.sHtML
- http://map.blog.nwbbyt.cn/Article/details/085111.sHtML
- http://map.blog.puhvjy.cn/Article/details/19560.sHtML
- http://map.blog.nwbbyt.cn/Article/details/56050.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0919.sHtML
- http://map.blog.puhvjy.cn/Article/details/4444.sHtML
- http://map.blog.nwbbyt.cn/Article/details/070905.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7465281.sHtML
- http://map.blog.nzfnve.cn/Article/details/95231.sHtML
- http://map.blog.puhvjy.cn/Article/details/394369.sHtML
- http://map.blog.puhvjy.cn/Article/details/0069.sHtML
- http://map.blog.puhvjy.cn/Article/details/19573.sHtML
- http://map.blog.nzfnve.cn/Article/details/65077.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5929849.sHtML
- http://map.blog.jnjpgf.cn/Article/details/26046.sHtML
- http://map.blog.nzfnve.cn/Article/details/6655896.sHtML

## 项目结构

```
webmap/
├── src/                                 # 核心源代码目录
│   ├── core/                            # 核心业务逻辑模块
│   │   ├── indexer.js                   # 链接索引与解析引擎
│   │   ├── classifier.js                # 分类标签推断器
│   │   └── cache.js                     # 离线缓存与增量更新管理器
│   ├── api/                             # RESTful API 接口层
│   │   ├── routes/                      # 路由定义
│   │   ├── controllers/                 # 控制器实现
│   │   └── validators/                  # 请求参数校验器
│   ├── ui/                              # 前端界面组件
│   │   ├── pages/                       # 页面级组件
│   │   ├── components/                  # 可复用 UI 组件
│   │   └── static/                      # 静态资源文件
│   ├── exporters/                       # 多格式输出模块
│   │   ├── markdown.js                  # Markdown 列表生成器
│   │   ├── html.js                      # HTML 导航页生成器
│   │   └── json.js                      # JSON API 数据输出
│   └── utils/                           # 通用工具函数库
│       ├── url-validator.js             # URL 合法性校验
│       ├── logger.js                    # 日志记录器
│       └── config-loader.js             # 配置文件加载器
├── config/                              # 配置文件目录
│   ├── default.toml                     # 默认配置
│   └── production.toml                  # 生产环境配置
├── data/                                # 本地数据存储目录
│   ├── index.db                         # SQLite 索引数据库
│   └── cache/                           # 链接内容缓存
├── docs/                                # 完整项目文档
│   ├── user-guide/                      # 用户手册
│   ├── admin-guide/                     # 管理员指南
│   └── developer-guide/                 # 开发者文档
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 单元测试
│   └── integration/                     # 集成测试
├── scripts/                             # 运维辅助脚本
│   ├── backup.sh                        # 数据备份脚本
│   └── migrate.sh                       # 数据库迁移脚本
├── package.json                         # npm 包依赖声明
├── README.md                            # 项目说明文档
└── LICENSE                              # MIT 许可证文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库到个人账号，并克隆到本地开发环境。建议在 dev 分支上进行所有开发工作，保持主分支与上游同步。

2. 创建功能分支时请使用 `feature/` 或 `fix/` 前缀，并在分支名称中简要描述改动内容，例如 `feature/add-csv-importer`。提交信息请遵循 Conventional Commits 规范，以便自动生成变更日志。

3. 在提交 Pull Request 之前，请确保所有单元测试与集成测试通过，并在本地执行 `npm run lint` 检查代码风格。新增功能需附带相应的测试用例。

4. 提交 PR 时请清晰描述改动目的、实现思路以及可能影响的范围，并关联相关 Issue（如有）。至少一名项目维护者审核通过后方可合并。

5. 对于重大功能更新或破坏性变更，请提前在 Issue 中发起讨论，与维护者达成一致后再进行开发，避免无效工作。

## 常见问题

**Q：WebMap 是否会自动抓取每个链接的完整页面内容？**

A：不会。WebMap 默认仅收录链接的元数据，包括来源域名、文章编号、收录时间与人工标注的分类标签。系统不进行全页抓取或内容存储，仅提供结构化导航功能。如有需要，用户可通过配置开启轻量级标题或摘要抓取，但该功能默认关闭以保证性能与合规性。

**Q：导入大量链接后，检索速度是否会明显下降？**

A：WebMap 使用 SQLite 作为后端存储，并在域名和分类字段上建立了索引。在 5000 条以内的记录规模下，关键词检索响应时间通常低于 100 毫秒。对于超过此规模的部署，建议使用 PostgreSQL 替代 SQLite，并配置全文检索扩展。

**Q：如何从旧版本迁移数据到新版本？**

A：每个版本升级前，请先运行 `scripts/backup.sh` 备份当前数据库文件。升级完成后，执行 `npm run migrate` 运行数据库迁移脚本。迁移过程会自动检测当前数据库版本并逐级执行升级 SQL，不会删除现有数据。如遇到迁移失败，请回滚到备份版本并提交 Issue。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
