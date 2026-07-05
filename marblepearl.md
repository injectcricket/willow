# WebArchive Bridge

WebArchive Bridge 是一个面向技术研究者、数据挖掘工程师与内容回溯分析人员的轻量化外链聚合与元数据索引工具。该项目定位于将分散于多个移动端博客平台的历史技术文章、开发笔记与工程日志进行集中式导航，帮助用户在无法依赖搜索引擎或站内搜索功能退化的场景下，通过结构化链接库快速定位存量内容。

本项目的核心受众包括：需要长期维护技术文档索引的团队负责人、进行互联网内容演变分析的学术研究者、以及希望从个人博客历史沉淀中复用代码片段或架构思路的开发者。WebArchive Bridge 不提供全文检索，也不存储任何文章副本，而是通过精心维护的链接映射表，以最低成本实现最大范围的历史资源覆盖率。

---

## 功能概览

- **多源链接聚合**：支持从至少四个独立移动博客子域名下批量采集文章详情页链接，自动识别 URL 路径结构与文件扩展名类型。

- **批次化资源管理**：以 40 批、每批 250 条链接的粒度组织数据，便于版本控制、增量更新与回滚操作。

- **原始链接直出**：所有收录的 URL 严格保持用户提交时的原始格式，包括协议类型、域名大小写、路径后缀与文件扩展名，杜绝任何形式的自动补全或规范化改写。

- **静态目录树导航**：项目内部按资源类型、来源域名与采集时间建立三层目录结构，配合 ASCII 树形图提供可视化浏览入口。

- **零运行时依赖查询**：资源列表完全基于静态 Markdown 表格与列表呈现，无需数据库、缓存或后端服务即可完整浏览全部链接。

- **跨批次一致性校验**：提供链接去重检测、协议一致性检查与域名分布统计功能，确保每批资源在合并时保持数据完整性。

- **轻量化部署支持**：项目本身仅包含文本文件与基础脚本，可托管于任何静态 Web 服务或本地文件系统，无需额外环境配置。

---

## 应用场景

**场景一：个人技术博客的历史文章回溯**
开发者维护个人技术博客超过五年，早期文章因平台改版或分类调整导致站内导航失效。通过 WebArchive Bridge 的链接聚合表，可直接定位到历史文章的具体详情页 URL，绕过失效的分类标签与分页逻辑。

**场景二：团队内部知识库的补充索引**
技术团队在迁移内部 Wiki 系统时，部分历史决策记录与设计文档仅保存在第三方博客平台。使用本项目按批次导入链接映射，可在新系统中快速建立外部引用清单，降低知识碎片化风险。

**场景三：互联网内容存档项目的辅助工具**
从事网页存档或数字资源长期保存的研究人员，需要定期抓取特定域名下的文章元数据。本项目提供的结构化链接列表可作为爬虫入口配置的基础数据源，显著减少手动收集链接的时间成本。

---

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webarchive-bridge/webarchive-bridge.git

# 进入项目根目录
cd webarchive-bridge

# 安装基础依赖（仅用于脚本工具，非运行必需）
npm install

# 执行链接校验脚本，检查当前批次资源格式
node scripts/validate-links.js --batch=06

# 生成静态导航页面（可选）
npm run build
```

---

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 14.x 或更高 | 仅用于运行辅助校验与构建脚本，浏览资源列表无需安装 |
| npm | 6.x 或更高 | 包管理工具，用于安装脚本依赖 |
| Git | 2.20 或更高 | 用于克隆仓库与版本管理 |
| Markdown 渲染器 | 任意 | 任何支持标准 Markdown 的阅读器或编辑器均可查看文档 |
| 文本编辑器 | 任意 | 推荐 UTF-8 编码支持，用于查看或编辑资源列表 |
| 操作系统 | Windows / Linux / macOS | 无平台限制，所有脚本均为跨平台实现 |
| 网络连接 | 建议存在 | 访问资源列表中的 URL 需外网连接 |
| 浏览器 | 现代版本 | 用于查看生成的静态导航页面（如启用） |

---

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户入门 | `/docs/quick-start.md` | 如何快速查看资源列表、如何理解链接格式规范 |
| 数据维护 | `/docs/maintenance-guide.md` | 如何新增批次、如何更新现有链接、如何执行去重 |
| 开发者参考 | `/docs/api-spec.md` | 辅助脚本的输入输出格式、校验规则说明 |
| 项目治理 | `/docs/governance.md` | 批次编号规则、URL 保留策略、贡献者行为准则 |

---

## 资源列表

- http://m.blog.nwbbyt.cn/Article/details/3959755.sHtML
- http://m.blog.nwbbyt.cn/Article/details/8814.sHtML
- http://m.blog.puhvjy.cn/Article/details/6841.sHtML
- http://m.blog.nwbbyt.cn/Article/details/89508.sHtML
- http://m.blog.puhvjy.cn/Article/details/4075.sHtML
- http://m.blog.nwbbyt.cn/Article/details/2494.sHtML
- http://m.blog.nzfnve.cn/Article/details/09375.sHtML
- http://m.blog.jnjpgf.cn/Article/details/1183.sHtML
- http://m.blog.puhvjy.cn/Article/details/1375468.sHtML
- http://m.blog.puhvjy.cn/Article/details/46854.sHtML
- http://m.blog.nwbbyt.cn/Article/details/7756.sHtML
- http://m.blog.nzfnve.cn/Article/details/5021995.sHtML
- http://m.blog.nzfnve.cn/Article/details/0979.sHtML
- http://m.blog.nzfnve.cn/Article/details/8666.sHtML
- http://m.blog.puhvjy.cn/Article/details/5762261.sHtML
- http://m.blog.nzfnve.cn/Article/details/6489435.sHtML
- http://m.blog.puhvjy.cn/Article/details/772872.sHtML
- http://m.blog.nwbbyt.cn/Article/details/41519.sHtML
- http://m.blog.jnjpgf.cn/Article/details/1421.sHtML
- http://m.blog.nwbbyt.cn/Article/details/71629.sHtML
- http://m.blog.puhvjy.cn/Article/details/529195.sHtML
- http://m.blog.nwbbyt.cn/Article/details/182312.sHtML
- http://m.blog.nwbbyt.cn/Article/details/714687.sHtML
- http://m.blog.nwbbyt.cn/Article/details/262821.sHtML
- http://m.blog.nwbbyt.cn/Article/details/5685541.sHtML
- http://m.blog.puhvjy.cn/Article/details/405006.sHtML
- http://m.blog.nwbbyt.cn/Article/details/90537.sHtML
- http://m.blog.nwbbyt.cn/Article/details/7836.sHtML
- http://m.blog.nwbbyt.cn/Article/details/8520755.sHtML
- http://m.blog.nwbbyt.cn/Article/details/287848.sHtML
- http://m.blog.puhvjy.cn/Article/details/68575.sHtML
- http://m.blog.nzfnve.cn/Article/details/346908.sHtML
- http://m.blog.nzfnve.cn/Article/details/0376966.sHtML
- http://m.blog.nzfnve.cn/Article/details/4543.sHtML
- http://m.blog.nzfnve.cn/Article/details/5427476.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5987.sHtML
- http://m.blog.puhvjy.cn/Article/details/4470795.sHtML
- http://m.blog.jnjpgf.cn/Article/details/7647625.sHtML
- http://m.blog.nwbbyt.cn/Article/details/076033.sHtML
- http://m.blog.jnjpgf.cn/Article/details/4908.sHtML
- http://m.blog.nwbbyt.cn/Article/details/0723053.sHtML
- http://m.blog.jnjpgf.cn/Article/details/76491.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5422.sHtML
- http://m.blog.nwbbyt.cn/Article/details/9934.sHtML
- http://m.blog.jnjpgf.cn/Article/details/6815584.sHtML
- http://m.blog.jnjpgf.cn/Article/details/3794472.sHtML
- http://m.blog.puhvjy.cn/Article/details/251907.sHtML
- http://m.blog.puhvjy.cn/Article/details/0621.sHtML
- http://m.blog.puhvjy.cn/Article/details/801026.sHtML
- http://m.blog.nzfnve.cn/Article/details/21412.sHtML
- http://m.blog.nzfnve.cn/Article/details/18785.sHtML
- http://m.blog.puhvjy.cn/Article/details/2363.sHtML
- http://m.blog.jnjpgf.cn/Article/details/4971121.sHtML
- http://m.blog.jnjpgf.cn/Article/details/6295.sHtML
- http://m.blog.nzfnve.cn/Article/details/9255500.sHtML
- http://m.blog.nzfnve.cn/Article/details/853965.sHtML
- http://m.blog.puhvjy.cn/Article/details/3725712.sHtML
- http://m.blog.nzfnve.cn/Article/details/942992.sHtML
- http://m.blog.jnjpgf.cn/Article/details/502275.sHtML
- http://m.blog.nzfnve.cn/Article/details/2209285.sHtML
- http://m.blog.puhvjy.cn/Article/details/7199.sHtML
- http://m.blog.nzfnve.cn/Article/details/98142.sHtML
- http://m.blog.puhvjy.cn/Article/details/219658.sHtML
- http://m.blog.jnjpgf.cn/Article/details/6626535.sHtML
- http://m.blog.nzfnve.cn/Article/details/01170.sHtML
- http://m.blog.nzfnve.cn/Article/details/8373.sHtML
- http://m.blog.puhvjy.cn/Article/details/68287.sHtML
- http://m.blog.nwbbyt.cn/Article/details/9629463.sHtML
- http://m.blog.nzfnve.cn/Article/details/2698.sHtML
- http://m.blog.nzfnve.cn/Article/details/5616.sHtML
- http://m.blog.nzfnve.cn/Article/details/2070304.sHtML
- http://m.blog.puhvjy.cn/Article/details/6305210.sHtML
- http://m.blog.puhvjy.cn/Article/details/018024.sHtML
- http://m.blog.puhvjy.cn/Article/details/40785.sHtML
- http://m.blog.nzfnve.cn/Article/details/6579.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5885.sHtML
- http://m.blog.puhvjy.cn/Article/details/9275.sHtML
- http://m.blog.jnjpgf.cn/Article/details/854694.sHtML
- http://m.blog.jnjpgf.cn/Article/details/3245545.sHtML
- http://m.blog.nzfnve.cn/Article/details/3976954.sHtML
- http://m.blog.jnjpgf.cn/Article/details/2104033.sHtML
- http://m.blog.puhvjy.cn/Article/details/1348888.sHtML
- http://m.blog.puhvjy.cn/Article/details/3498.sHtML
- http://m.blog.jnjpgf.cn/Article/details/3965100.sHtML
- http://m.blog.puhvjy.cn/Article/details/41351.sHtML
- http://m.blog.puhvjy.cn/Article/details/93097.sHtML
- http://m.blog.jnjpgf.cn/Article/details/8277076.sHtML
- http://m.blog.puhvjy.cn/Article/details/651354.sHtML
- http://m.blog.jnjpgf.cn/Article/details/83578.sHtML
- http://m.blog.nwbbyt.cn/Article/details/1646.sHtML
- http://m.blog.nzfnve.cn/Article/details/483986.sHtML
- http://m.blog.puhvjy.cn/Article/details/326835.sHtML
- http://m.blog.puhvjy.cn/Article/details/3800512.sHtML
- http://m.blog.nwbbyt.cn/Article/details/3805245.sHtML
- http://m.blog.nzfnve.cn/Article/details/7086858.sHtML
- http://m.blog.nzfnve.cn/Article/details/5464652.sHtML
- http://m.blog.nzfnve.cn/Article/details/3033.sHtML
- http://m.blog.puhvjy.cn/Article/details/225163.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5353.sHtML
- http://m.blog.puhvjy.cn/Article/details/8441412.sHtML
- http://m.blog.nzfnve.cn/Article/details/5093.sHtML
- http://m.blog.puhvjy.cn/Article/details/706867.sHtML
- http://m.blog.nzfnve.cn/Article/details/139217.sHtML
- http://m.blog.jnjpgf.cn/Article/details/690696.sHtML
- http://m.blog.puhvjy.cn/Article/details/9418653.sHtML
- http://m.blog.nzfnve.cn/Article/details/82275.sHtML
- http://m.blog.nwbbyt.cn/Article/details/455039.sHtML
- http://m.blog.nzfnve.cn/Article/details/9656377.sHtML
- http://m.blog.jnjpgf.cn/Article/details/790901.sHtML
- http://m.blog.jnjpgf.cn/Article/details/228963.sHtML
- http://m.blog.nzfnve.cn/Article/details/898656.sHtML
- http://m.blog.puhvjy.cn/Article/details/890337.sHtML
- http://m.blog.nwbbyt.cn/Article/details/4724.sHtML
- http://m.blog.puhvjy.cn/Article/details/4295318.sHtML
- http://m.blog.nzfnve.cn/Article/details/3226936.sHtML
- http://m.blog.nwbbyt.cn/Article/details/83604.sHtML
- http://m.blog.jnjpgf.cn/Article/details/517554.sHtML
- http://m.blog.nwbbyt.cn/Article/details/97382.sHtML
- http://m.blog.nzfnve.cn/Article/details/67636.sHtML
- http://m.blog.jnjpgf.cn/Article/details/6374.sHtML
- http://m.blog.nwbbyt.cn/Article/details/9272.sHtML
- http://m.blog.nwbbyt.cn/Article/details/96456.sHtML
- http://m.blog.jnjpgf.cn/Article/details/4850.sHtML
- http://m.blog.puhvjy.cn/Article/details/707151.sHtML
- http://m.blog.jnjpgf.cn/Article/details/7943.sHtML
- http://m.blog.jnjpgf.cn/Article/details/824453.sHtML
- http://m.blog.jnjpgf.cn/Article/details/84840.sHtML
- http://m.blog.nzfnve.cn/Article/details/06825.sHtML
- http://m.blog.puhvjy.cn/Article/details/443710.sHtML
- http://m.blog.jnjpgf.cn/Article/details/408832.sHtML
- http://m.blog.nwbbyt.cn/Article/details/5811783.sHtML
- http://m.blog.puhvjy.cn/Article/details/607492.sHtML
- http://m.blog.nzfnve.cn/Article/details/340926.sHtML
- http://m.blog.nzfnve.cn/Article/details/850421.sHtML
- http://m.blog.nzfnve.cn/Article/details/960089.sHtML
- http://m.blog.puhvjy.cn/Article/details/21222.sHtML
- http://m.blog.nzfnve.cn/Article/details/59345.sHtML
- http://m.blog.nwbbyt.cn/Article/details/8549537.sHtML
- http://m.blog.puhvjy.cn/Article/details/494541.sHtML
- http://m.blog.puhvjy.cn/Article/details/6123.sHtML
- http://m.blog.jnjpgf.cn/Article/details/0938099.sHtML
- http://m.blog.nwbbyt.cn/Article/details/8920.sHtML
- http://m.blog.nwbbyt.cn/Article/details/7069.sHtML
- http://m.blog.jnjpgf.cn/Article/details/67358.sHtML
- http://m.blog.nwbbyt.cn/Article/details/711376.sHtML
- http://m.blog.nwbbyt.cn/Article/details/50195.sHtML
- http://m.blog.jnjpgf.cn/Article/details/4268.sHtML
- http://m.blog.puhvjy.cn/Article/details/3340273.sHtML
- http://m.blog.nzfnve.cn/Article/details/2360381.sHtML
- http://m.blog.jnjpgf.cn/Article/details/3333.sHtML
- http://m.blog.jnjpgf.cn/Article/details/6826681.sHtML
- http://m.blog.puhvjy.cn/Article/details/4425828.sHtML
- http://m.blog.nzfnve.cn/Article/details/7559665.sHtML
- http://m.blog.puhvjy.cn/Article/details/97294.sHtML
- http://m.blog.jnjpgf.cn/Article/details/233225.sHtML
- http://m.blog.jnjpgf.cn/Article/details/3837870.sHtML
- http://m.blog.nwbbyt.cn/Article/details/162060.sHtML
- http://m.blog.nzfnve.cn/Article/details/5758.sHtML
- http://m.blog.puhvjy.cn/Article/details/9681261.sHtML
- http://m.blog.puhvjy.cn/Article/details/280206.sHtML
- http://m.blog.nwbbyt.cn/Article/details/448197.sHtML
- http://m.blog.jnjpgf.cn/Article/details/973938.sHtML
- http://m.blog.puhvjy.cn/Article/details/7602881.sHtML
- http://m.blog.jnjpgf.cn/Article/details/513573.sHtML
- http://m.blog.jnjpgf.cn/Article/details/9926.sHtML
- http://m.blog.puhvjy.cn/Article/details/05628.sHtML
- http://m.blog.jnjpgf.cn/Article/details/081907.sHtML
- http://m.blog.puhvjy.cn/Article/details/0684723.sHtML
- http://m.blog.jnjpgf.cn/Article/details/395291.sHtML
- http://m.blog.nzfnve.cn/Article/details/7928891.sHtML
- http://m.blog.nzfnve.cn/Article/details/0530.sHtML
- http://m.blog.nzfnve.cn/Article/details/56375.sHtML
- http://m.blog.nzfnve.cn/Article/details/45325.sHtML
- http://m.blog.puhvjy.cn/Article/details/29210.sHtML
- http://m.blog.jnjpgf.cn/Article/details/416704.sHtML
- http://m.blog.nwbbyt.cn/Article/details/9842387.sHtML
- http://m.blog.jnjpgf.cn/Article/details/7307.sHtML
- http://m.blog.nwbbyt.cn/Article/details/9650.sHtML
- http://m.blog.nzfnve.cn/Article/details/4189.sHtML
- http://m.blog.nwbbyt.cn/Article/details/171129.sHtML
- http://m.blog.nzfnve.cn/Article/details/9476.sHtML
- http://m.blog.nwbbyt.cn/Article/details/822263.sHtML
- http://m.blog.nzfnve.cn/Article/details/2233.sHtML
- http://m.blog.nzfnve.cn/Article/details/47454.sHtML
- http://m.blog.nzfnve.cn/Article/details/10992.sHtML
- http://m.blog.puhvjy.cn/Article/details/02332.sHtML
- http://m.blog.puhvjy.cn/Article/details/6108.sHtML
- http://m.blog.nzfnve.cn/Article/details/403748.sHtML
- http://m.blog.nwbbyt.cn/Article/details/95807.sHtML
- http://m.blog.puhvjy.cn/Article/details/41150.sHtML
- http://m.blog.nwbbyt.cn/Article/details/01445.sHtML
- http://m.blog.jnjpgf.cn/Article/details/558790.sHtML
- http://m.blog.nzfnve.cn/Article/details/8296189.sHtML
- http://m.blog.nwbbyt.cn/Article/details/791825.sHtML
- http://m.blog.jnjpgf.cn/Article/details/287508.sHtML
- http://m.blog.puhvjy.cn/Article/details/8611.sHtML
- http://m.blog.jnjpgf.cn/Article/details/76854.sHtML
- http://m.blog.puhvjy.cn/Article/details/880204.sHtML
- http://m.blog.jnjpgf.cn/Article/details/380818.sHtML
- http://m.blog.jnjpgf.cn/Article/details/65998.sHtML
- http://m.blog.puhvjy.cn/Article/details/73815.sHtML
- http://m.blog.puhvjy.cn/Article/details/57047.sHtML
- http://m.blog.nzfnve.cn/Article/details/7108.sHtML
- http://m.blog.nwbbyt.cn/Article/details/670052.sHtML
- http://m.blog.jnjpgf.cn/Article/details/7152166.sHtML
- http://m.blog.jnjpgf.cn/Article/details/2939.sHtML
- http://m.blog.puhvjy.cn/Article/details/178025.sHtML
- http://m.blog.jnjpgf.cn/Article/details/2604662.sHtML
- http://m.blog.jnjpgf.cn/Article/details/012888.sHtML
- http://m.blog.nzfnve.cn/Article/details/77147.sHtML
- http://m.blog.puhvjy.cn/Article/details/8061676.sHtML
- http://m.blog.nzfnve.cn/Article/details/5701708.sHtML
- http://m.blog.puhvjy.cn/Article/details/638233.sHtML
- http://m.blog.jnjpgf.cn/Article/details/12113.sHtML
- http://m.blog.nzfnve.cn/Article/details/224293.sHtML
- http://m.blog.nzfnve.cn/Article/details/2936.sHtML
- http://m.blog.nzfnve.cn/Article/details/3423746.sHtML
- http://m.blog.nzfnve.cn/Article/details/3693.sHtML
- http://m.blog.jnjpgf.cn/Article/details/3695.sHtML
- http://m.blog.jnjpgf.cn/Article/details/4825.sHtML
- http://m.blog.nwbbyt.cn/Article/details/2114.sHtML
- http://m.blog.puhvjy.cn/Article/details/53840.sHtML
- http://m.blog.nwbbyt.cn/Article/details/3031.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5319658.sHtML
- http://m.blog.puhvjy.cn/Article/details/957560.sHtML
- http://m.blog.jnjpgf.cn/Article/details/687909.sHtML
- http://m.blog.nzfnve.cn/Article/details/6581726.sHtML
- http://m.blog.puhvjy.cn/Article/details/05783.sHtML
- http://m.blog.nzfnve.cn/Article/details/51195.sHtML
- http://m.blog.jnjpgf.cn/Article/details/673858.sHtML
- http://m.blog.nwbbyt.cn/Article/details/09158.sHtML
- http://m.blog.puhvjy.cn/Article/details/3192.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5066.sHtML
- http://m.blog.jnjpgf.cn/Article/details/5303.sHtML
- http://m.blog.nwbbyt.cn/Article/details/67129.sHtML
- http://m.blog.nzfnve.cn/Article/details/5534.sHtML
- http://m.blog.nwbbyt.cn/Article/details/1539153.sHtML
- http://m.blog.nzfnve.cn/Article/details/5498163.sHtML
- http://m.blog.puhvjy.cn/Article/details/142427.sHtML
- http://m.blog.jnjpgf.cn/Article/details/885204.sHtML
- http://m.blog.nwbbyt.cn/Article/details/1159699.sHtML
- http://m.blog.jnjpgf.cn/Article/details/0206744.sHtML
- http://m.blog.nzfnve.cn/Article/details/1610364.sHtML
- http://m.blog.nwbbyt.cn/Article/details/7058.sHtML
- http://m.blog.nwbbyt.cn/Article/details/73957.sHtML
- http://m.blog.jnjpgf.cn/Article/details/02220.sHtML
- http://m.blog.jnjpgf.cn/Article/details/9002556.sHtML
- http://m.blog.jnjpgf.cn/Article/details/6601923.sHtML
- http://m.blog.jnjpgf.cn/Article/details/4859.sHtML
- http://m.blog.jnjpgf.cn/Article/details/2342146.sHtML

## 项目结构

```
webarchive-bridge/
├── README.md                           # 项目说明文档（当前文件）
├── LICENSE                             # MIT 许可证文件
├── package.json                        # npm 脚本与依赖声明
├── .gitignore                          # Git 忽略规则
│
├── batches/                            # 批次资源根目录
│   ├── batch_001/                      # 第 1 批链接（已完成）
│   ├── batch_002/                      # 第 2 批链接（已完成）
│   ├── batch_003/                      # 第 3 批链接（已完成）
│   ├── batch_004/                      # 第 4 批链接（已完成）
│   ├── batch_005/                      # 第 5 批链接（已完成）
│   └── batch_006/                      # 第 6 批链接（当前批次）
│       ├── sources.txt                 # 原始链接列表（纯文本）
│       ├── manifest.json               # 批次元数据（域名统计、采集时间）
│       └── validation.log              # 链接格式校验日志
│
├── scripts/                            # 辅助脚本目录
│   ├── validate-links.js               # 链接格式与协议校验
│   ├── deduplicate.js                  # 跨批次链接去重工具
│   ├── generate-index.js               # 生成总导航页面的构建脚本
│   └── utils/                          # 脚本共用工具函数
│       ├── parser.js                   # URL 解析与格式化辅助
│       └── logger.js                   # 日志输出与错误记录
│
├── docs/                               # 文档目录
│   ├── quick-start.md                  # 快速入门指南
│   ├── maintenance-guide.md            # 批次维护与更新流程
│   ├── api-spec.md                     # 脚本接口规范
│   └── governance.md                   # 项目治理与贡献规则
│
└── assets/                             # 静态资源（仅用于可选的页面生成）
    ├── templates/                      # HTML 模板文件
    └── styles/                         # CSS 样式表
```

---

## 贡献指南

**步骤一：复刻项目仓库**
在 GitHub 上点击 Fork 按钮，将本仓库复制到个人账户下，随后克隆到本地开发环境。

**步骤二：创建特性分支**
基于 main 分支创建新的分支，分支命名格式为 `feature/batch-XXX` 或 `fix/description`，确保分支名称清晰反映变更内容。

**步骤三：更新资源列表**
在对应批次的 `sources.txt` 文件中追加或修改链接。必须严格遵守原始 URL 格式规范，不得添加协议前缀、不得改动域名大小写、不得更改文件扩展名。

**步骤四：执行本地校验**
运行 `npm run validate -- --batch=06` 检查链接格式是否符合项目要求，确保所有条目均可解析且协议类型统一。

**步骤五：提交变更并发起拉取请求**
提交信息使用约定式提交格式，例如 `feat: add batch 007 links` 或 `fix: correct malformed URL in batch 006`。推送分支后，在 GitHub 上发起拉取请求，等待项目维护者审核。

---

## 常见问题

**问：为什么所有链接都必须保持原始格式，不能统一转为 HTTPS 或去掉 www？**

答：本项目的核心原则是“绝对保真”。目标博客平台可能仅支持 HTTP 协议，或对 HTTPS 请求返回重定向循环；某些域名的 www 子域与非 www 子域可能对应完全不同的站点配置。任何格式化改动都可能导致链接无法正常访问。因此，项目强制要求所有收录的 URL 与用户提交时完全一致。

**问：如何确认某个链接是否已经存在于之前的批次中？**

答：项目根目录下提供了去重脚本 `scripts/deduplicate.js`。运行 `npm run dedupe` 即可扫描所有批次目录，输出重复链接列表及其所在批次编号。建议在新增批次前执行此检查，避免资源冗余。

**问：如果某个原始链接已经失效（返回 404），是否可以从列表中移除？**

答：本项目不主动删除任何链接，即使目标资源暂时不可访问，链接本身仍具有历史索引价值。项目维护者会定期对链接进行可用性标记，但不会从列表中移除。用户可在本地使用 `scripts/validate-links.js` 配合 `--check-status` 参数自行检测链接状态，但该检测结果不影响项目主干内容。

---

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
