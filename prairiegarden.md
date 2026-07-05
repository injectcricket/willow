# WebLink Aggregate Server - WLS

WebLink Aggregate Server (WLS) 是一个面向技术内容聚合与外部链接治理的开源中间件项目。该项目定位于为中小型技术团队、个人站长以及内容平台运营者提供一套标准化的外链采集、分类、存储和展示方案。WLS 不依赖第三方商业 API，完全基于自建规则引擎与静态分析技术，能够将分散在多个技术博客、新闻源和社区平台中的优质外链资源统一归集并生成可检索、可审计的链接目录。

WLS 的目标用户包括技术文档维护者、开发者关系工程师、技术社区运营人员以及希望建立私有技术知识库的工程师。通过 WLS，用户可以在数分钟内完成对给定批次外链的元数据抓取、状态检测和结构化存储，最终输出用于静态站点生成或内部系统对接的标准化 JSON 与 Markdown 索引文件。

## 功能概览

- **批量链接解析引擎**：支持对大批量 URL 进行并发 HTTP 请求，自动跟随重定向并记录最终状态码与响应时间。
- **元数据智能提取**：从目标页面中抽取标题、描述、关键词、正文首段以及发表日期，支持常见 CMS 结构（如 WordPress、Typecho、Hexo）。
- **域名指纹识别**：对链接中的域名进行归属地、备案信息、SSL 证书签发者等基础信息的自动化采集与分类。
- **健康度监控**：周期性检查已收录链接的可访问性，对返回 4xx/5xx 状态的链接进行标记并生成告警日志。
- **多格式导出**：支持将链接索引导出为 Markdown 表格、JSON 数组、CSV 以及适用于 VuePress / Docusaurus 的侧边栏格式。
- **规则过滤系统**：基于正则表达式与域名黑白名单，允许用户设定收录规则，自动过滤广告、跟踪参数或无关页面。
- **审计追踪**：记录每次链接更新的时间戳、操作人（API Key 或 JWT 标识），支持完整历史回滚与变更差异对比。

## 应用场景

- **技术周报自动化**：团队维护内部技术周报时，可将本周收集到的数十篇博客链接统一提交给 WLS，系统自动提取摘要并按标签归类，最终生成用于邮件发送或内部 Wiki 发布的 Markdown 草稿。
- **外链质量审计**：安全团队定期对企业官网或产品文档中的所有外部引用链接进行批量检测，WLS 能够输出包含 HTTP 状态、响应大小、SSL 有效期的审计报告，协助识别失效或恶意链接。
- **知识库构建**：研究机构或技术社区在整理特定领域（如云原生、人工智能、数据库内核）的文章索引时，使用 WLS 对不同来源的链接进行去重和分类，最终构建出结构化程度较高的资源导航页面。
- **私有书签服务**：个人开发者通过 WLS 自建私有网络书签服务，替代依赖第三方在线书签工具，确保数据完全自主可控，同时获得全文检索和标签管理能力。
- **迁移辅助**：在将内容从一个 CMS 迁移至另一个 CMS 时，WLS 可批量解析旧站点导出的链接列表，提取内部链接与外部链接的映射关系，帮助迁移脚本正确处理 URL 重写逻辑。

## 快速开始

以下步骤适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL 2 或 Git Bash。

```bash
# 克隆仓库
git clone https://github.com/your-org/wls.git
cd wls

# 安装依赖（使用 pip 与虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 准备配置文件
cp config.example.yaml config.yaml
# 编辑 config.yaml 填入数据存储路径及并发参数

# 运行链接导入任务
python wls.py import --source list.txt --output index.json

# 启动 Web UI（可选）
python wls.py serve --port 8080
```

其中 `list.txt` 为每行一个 URL 的纯文本文件，示例内容可从项目 `examples/` 目录获取。首次运行时会自动创建 SQLite 数据库文件与缓存目录。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 核心运行环境，推荐使用 3.11 |
| pip | 23.0 及以上 | 用于安装所有 Python 包依赖 |
| SQLite | 3.35 及以上 | 嵌入式数据库，用于存储链接元数据和审计日志 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端，用于并发请求 |
| lxml | 4.9.0 及以上 | HTML/XML 解析库，用于提取元数据 |
| PyYAML | 6.0 及以上 | 配置文件解析 |
| pytest | 7.0 及以上 | 仅开发测试时需要 |
| docker | 20.10 及以上 | 如需使用容器化部署方案时可选 |
| redis | 6.2 及以上 | 如需启用分布式任务队列时可选 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置并首次运行导入任务；如何验证输出结果 |
| 核心概念 | docs/core-concepts.md | 解释链接生命周期、规则引擎流程、缓存策略与数据模型 |
| 操作手册 | docs/operations.md | 如何配置定时任务、如何查看健康状态、如何手动干预失败队列 |
| API 参考 | docs/api-reference.md | 提供 RESTful API 的端点说明、请求示例和错误码含义 |
| 部署指南 | docs/deployment.md | 涵盖 Docker 部署、systemd 服务配置、反向代理与 HTTPS 设置 |
| 故障排查 | docs/troubleshooting.md | 常见错误日志含义、网络超时处理、数据库锁问题解法 |
| 性能调优 | docs/performance.md | 针对百万级链接的并发数调整、缓存命中率优化与分页策略 |

## 资源列表

- http://www.blog.nzfnve.cn/Article/details/0343.sHtML
- http://www.blog.nwbbyt.cn/Article/details/33530.sHtML
- http://www.blog.nwbbyt.cn/Article/details/992011.sHtML
- http://www.blog.nwbbyt.cn/Article/details/93177.sHtML
- http://www.blog.nzfnve.cn/Article/details/6377.sHtML
- http://www.blog.puhvjy.cn/Article/details/00521.sHtML
- http://www.blog.nzfnve.cn/Article/details/79857.sHtML
- http://www.blog.jnjpgf.cn/Article/details/139215.sHtML
- http://www.blog.jnjpgf.cn/Article/details/13794.sHtML
- http://www.blog.nwbbyt.cn/Article/details/69863.sHtML
- http://www.blog.nwbbyt.cn/Article/details/665409.sHtML
- http://www.blog.jnjpgf.cn/Article/details/11924.sHtML
- http://www.blog.nwbbyt.cn/Article/details/520396.sHtML
- http://www.blog.nzfnve.cn/Article/details/7136415.sHtML
- http://www.blog.nzfnve.cn/Article/details/153846.sHtML
- http://www.blog.nwbbyt.cn/Article/details/62601.sHtML
- http://www.blog.puhvjy.cn/Article/details/44530.sHtML
- http://www.blog.jnjpgf.cn/Article/details/391561.sHtML
- http://www.blog.puhvjy.cn/Article/details/246944.sHtML
- http://www.blog.jnjpgf.cn/Article/details/76918.sHtML
- http://www.blog.puhvjy.cn/Article/details/190902.sHtML
- http://www.blog.nzfnve.cn/Article/details/48503.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6421300.sHtML
- http://www.blog.nwbbyt.cn/Article/details/642086.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1232.sHtML
- http://www.blog.puhvjy.cn/Article/details/2612561.sHtML
- http://www.blog.nzfnve.cn/Article/details/77374.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7315504.sHtML
- http://www.blog.nzfnve.cn/Article/details/6031.sHtML
- http://www.blog.nzfnve.cn/Article/details/8815776.sHtML
- http://www.blog.nzfnve.cn/Article/details/69244.sHtML
- http://www.blog.nwbbyt.cn/Article/details/13327.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6109528.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9107190.sHtML
- http://www.blog.nwbbyt.cn/Article/details/8121.sHtML
- http://www.blog.puhvjy.cn/Article/details/5725312.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9590412.sHtML
- http://www.blog.nzfnve.cn/Article/details/633378.sHtML
- http://www.blog.jnjpgf.cn/Article/details/36845.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0958.sHtML
- http://www.blog.puhvjy.cn/Article/details/8796882.sHtML
- http://www.blog.jnjpgf.cn/Article/details/23914.sHtML
- http://www.blog.jnjpgf.cn/Article/details/268735.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6957.sHtML
- http://www.blog.jnjpgf.cn/Article/details/259400.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2504.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9507.sHtML
- http://www.blog.nzfnve.cn/Article/details/42581.sHtML
- http://www.blog.nzfnve.cn/Article/details/6280.sHtML
- http://www.blog.jnjpgf.cn/Article/details/37940.sHtML
- http://www.blog.puhvjy.cn/Article/details/88178.sHtML
- http://www.blog.puhvjy.cn/Article/details/64784.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9070867.sHtML
- http://www.blog.puhvjy.cn/Article/details/626940.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6751438.sHtML
- http://www.blog.puhvjy.cn/Article/details/9571565.sHtML
- http://www.blog.nzfnve.cn/Article/details/989801.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0620266.sHtML
- http://www.blog.puhvjy.cn/Article/details/9231588.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8165260.sHtML
- http://www.blog.jnjpgf.cn/Article/details/567068.sHtML
- http://www.blog.nzfnve.cn/Article/details/08299.sHtML
- http://www.blog.puhvjy.cn/Article/details/0581118.sHtML
- http://www.blog.nzfnve.cn/Article/details/809002.sHtML
- http://www.blog.nzfnve.cn/Article/details/0356.sHtML
- http://www.blog.nzfnve.cn/Article/details/4691.sHtML
- http://www.blog.nwbbyt.cn/Article/details/007866.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2085.sHtML
- http://www.blog.puhvjy.cn/Article/details/7208750.sHtML
- http://www.blog.puhvjy.cn/Article/details/40423.sHtML
- http://www.blog.nwbbyt.cn/Article/details/645426.sHtML
- http://www.blog.nzfnve.cn/Article/details/8105.sHtML
- http://www.blog.puhvjy.cn/Article/details/110330.sHtML
- http://www.blog.nwbbyt.cn/Article/details/6665.sHtML
- http://www.blog.jnjpgf.cn/Article/details/739772.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5311058.sHtML
- http://www.blog.nzfnve.cn/Article/details/184394.sHtML
- http://www.blog.nzfnve.cn/Article/details/8364.sHtML
- http://www.blog.nwbbyt.cn/Article/details/461379.sHtML
- http://www.blog.jnjpgf.cn/Article/details/234577.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3423787.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2728.sHtML
- http://www.blog.nwbbyt.cn/Article/details/273215.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6868.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4718612.sHtML
- http://www.blog.nzfnve.cn/Article/details/14110.sHtML
- http://www.blog.jnjpgf.cn/Article/details/17551.sHtML
- http://www.blog.nzfnve.cn/Article/details/868906.sHtML
- http://www.blog.puhvjy.cn/Article/details/119027.sHtML
- http://www.blog.nzfnve.cn/Article/details/58978.sHtML
- http://www.blog.nzfnve.cn/Article/details/6445391.sHtML
- http://www.blog.jnjpgf.cn/Article/details/858518.sHtML
- http://www.blog.puhvjy.cn/Article/details/8304232.sHtML
- http://www.blog.nzfnve.cn/Article/details/1947913.sHtML
- http://www.blog.jnjpgf.cn/Article/details/493465.sHtML
- http://www.blog.jnjpgf.cn/Article/details/641615.sHtML
- http://www.blog.nzfnve.cn/Article/details/94338.sHtML
- http://www.blog.nzfnve.cn/Article/details/84237.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5622842.sHtML
- http://www.blog.puhvjy.cn/Article/details/7495793.sHtML
- http://www.blog.puhvjy.cn/Article/details/5548083.sHtML
- http://www.blog.nwbbyt.cn/Article/details/17578.sHtML
- http://www.blog.puhvjy.cn/Article/details/999956.sHtML
- http://www.blog.puhvjy.cn/Article/details/5703009.sHtML
- http://www.blog.jnjpgf.cn/Article/details/59973.sHtML
- http://www.blog.nzfnve.cn/Article/details/10634.sHtML
- http://www.blog.nwbbyt.cn/Article/details/900249.sHtML
- http://www.blog.puhvjy.cn/Article/details/37447.sHtML
- http://www.blog.jnjpgf.cn/Article/details/976663.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4025340.sHtML
- http://www.blog.puhvjy.cn/Article/details/38965.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9299.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7765.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3451.sHtML
- http://www.blog.jnjpgf.cn/Article/details/601259.sHtML
- http://www.blog.puhvjy.cn/Article/details/41546.sHtML
- http://www.blog.nzfnve.cn/Article/details/9388.sHtML
- http://www.blog.nzfnve.cn/Article/details/819617.sHtML
- http://www.blog.nzfnve.cn/Article/details/4859.sHtML
- http://www.blog.nwbbyt.cn/Article/details/675028.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6341683.sHtML
- http://www.blog.nwbbyt.cn/Article/details/404398.sHtML
- http://www.blog.nzfnve.cn/Article/details/7806.sHtML
- http://www.blog.nzfnve.cn/Article/details/6700735.sHtML
- http://www.blog.nzfnve.cn/Article/details/4081504.sHtML
- http://www.blog.jnjpgf.cn/Article/details/382004.sHtML
- http://www.blog.puhvjy.cn/Article/details/3053218.sHtML
- http://www.blog.puhvjy.cn/Article/details/16928.sHtML
- http://www.blog.puhvjy.cn/Article/details/1830.sHtML
- http://www.blog.nzfnve.cn/Article/details/2667.sHtML
- http://www.blog.nzfnve.cn/Article/details/26748.sHtML
- http://www.blog.nzfnve.cn/Article/details/3801.sHtML
- http://www.blog.jnjpgf.cn/Article/details/64429.sHtML
- http://www.blog.nwbbyt.cn/Article/details/57467.sHtML
- http://www.blog.puhvjy.cn/Article/details/0802414.sHtML
- http://www.blog.nwbbyt.cn/Article/details/264793.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1320.sHtML
- http://www.blog.nwbbyt.cn/Article/details/1184520.sHtML
- http://www.blog.nwbbyt.cn/Article/details/21021.sHtML
- http://www.blog.jnjpgf.cn/Article/details/0636867.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2597448.sHtML
- http://www.blog.nwbbyt.cn/Article/details/179216.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2596.sHtML
- http://www.blog.puhvjy.cn/Article/details/3454.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3799850.sHtML
- http://www.blog.nzfnve.cn/Article/details/35369.sHtML
- http://www.blog.nwbbyt.cn/Article/details/708616.sHtML
- http://www.blog.puhvjy.cn/Article/details/611360.sHtML
- http://www.blog.jnjpgf.cn/Article/details/876041.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0989.sHtML
- http://www.blog.nzfnve.cn/Article/details/3765220.sHtML
- http://www.blog.nwbbyt.cn/Article/details/3213900.sHtML
- http://www.blog.puhvjy.cn/Article/details/99228.sHtML
- http://www.blog.puhvjy.cn/Article/details/84101.sHtML
- http://www.blog.puhvjy.cn/Article/details/5555.sHtML
- http://www.blog.nzfnve.cn/Article/details/6611.sHtML
- http://www.blog.nzfnve.cn/Article/details/8523.sHtML
- http://www.blog.nzfnve.cn/Article/details/910277.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4051.sHtML
- http://www.blog.nzfnve.cn/Article/details/408895.sHtML
- http://www.blog.nzfnve.cn/Article/details/126489.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8770.sHtML
- http://www.blog.nzfnve.cn/Article/details/2710.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2811.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9279295.sHtML
- http://www.blog.jnjpgf.cn/Article/details/09839.sHtML
- http://www.blog.puhvjy.cn/Article/details/94614.sHtML
- http://www.blog.puhvjy.cn/Article/details/2508670.sHtML
- http://www.blog.nzfnve.cn/Article/details/896902.sHtML
- http://www.blog.jnjpgf.cn/Article/details/9428.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9820.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6196.sHtML
- http://www.blog.nzfnve.cn/Article/details/529076.sHtML
- http://www.blog.jnjpgf.cn/Article/details/533907.sHtML
- http://www.blog.jnjpgf.cn/Article/details/980850.sHtML
- http://www.blog.jnjpgf.cn/Article/details/06536.sHtML
- http://www.blog.puhvjy.cn/Article/details/17339.sHtML
- http://www.blog.puhvjy.cn/Article/details/6816808.sHtML
- http://www.blog.jnjpgf.cn/Article/details/63156.sHtML
- http://www.blog.nwbbyt.cn/Article/details/51418.sHtML
- http://www.blog.puhvjy.cn/Article/details/9444.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6968.sHtML
- http://www.blog.nwbbyt.cn/Article/details/2754270.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0282.sHtML
- http://www.blog.nzfnve.cn/Article/details/49431.sHtML
- http://www.blog.puhvjy.cn/Article/details/5530.sHtML
- http://www.blog.nzfnve.cn/Article/details/09639.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6653.sHtML
- http://www.blog.puhvjy.cn/Article/details/7447.sHtML
- http://www.blog.jnjpgf.cn/Article/details/183292.sHtML
- http://www.blog.puhvjy.cn/Article/details/200398.sHtML
- http://www.blog.jnjpgf.cn/Article/details/21769.sHtML
- http://www.blog.jnjpgf.cn/Article/details/5274.sHtML
- http://www.blog.nzfnve.cn/Article/details/65110.sHtML
- http://www.blog.jnjpgf.cn/Article/details/41482.sHtML
- http://www.blog.puhvjy.cn/Article/details/749071.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5427729.sHtML
- http://www.blog.nwbbyt.cn/Article/details/272620.sHtML
- http://www.blog.jnjpgf.cn/Article/details/91877.sHtML
- http://www.blog.puhvjy.cn/Article/details/0803441.sHtML
- http://www.blog.nwbbyt.cn/Article/details/9448.sHtML
- http://www.blog.nzfnve.cn/Article/details/0906681.sHtML
- http://www.blog.puhvjy.cn/Article/details/36997.sHtML
- http://www.blog.jnjpgf.cn/Article/details/590709.sHtML
- http://www.blog.nzfnve.cn/Article/details/29900.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8318.sHtML
- http://www.blog.puhvjy.cn/Article/details/8847.sHtML
- http://www.blog.jnjpgf.cn/Article/details/3821084.sHtML
- http://www.blog.nzfnve.cn/Article/details/3093396.sHtML
- http://www.blog.puhvjy.cn/Article/details/7991.sHtML
- http://www.blog.nzfnve.cn/Article/details/3270.sHtML
- http://www.blog.puhvjy.cn/Article/details/47129.sHtML
- http://www.blog.nzfnve.cn/Article/details/497804.sHtML
- http://www.blog.nzfnve.cn/Article/details/203085.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7321.sHtML
- http://www.blog.jnjpgf.cn/Article/details/1650.sHtML
- http://www.blog.puhvjy.cn/Article/details/710767.sHtML
- http://www.blog.jnjpgf.cn/Article/details/044990.sHtML
- http://www.blog.nzfnve.cn/Article/details/0684051.sHtML
- http://www.blog.nzfnve.cn/Article/details/70890.sHtML
- http://www.blog.jnjpgf.cn/Article/details/483810.sHtML
- http://www.blog.nzfnve.cn/Article/details/615223.sHtML
- http://www.blog.jnjpgf.cn/Article/details/6565.sHtML
- http://www.blog.puhvjy.cn/Article/details/818369.sHtML
- http://www.blog.jnjpgf.cn/Article/details/2371.sHtML
- http://www.blog.nzfnve.cn/Article/details/077626.sHtML
- http://www.blog.jnjpgf.cn/Article/details/635581.sHtML
- http://www.blog.nwbbyt.cn/Article/details/019199.sHtML
- http://www.blog.nzfnve.cn/Article/details/657452.sHtML
- http://www.blog.nwbbyt.cn/Article/details/0674.sHtML
- http://www.blog.nzfnve.cn/Article/details/376349.sHtML
- http://www.blog.nzfnve.cn/Article/details/22416.sHtML
- http://www.blog.nwbbyt.cn/Article/details/7255623.sHtML
- http://www.blog.puhvjy.cn/Article/details/1211.sHtML
- http://www.blog.puhvjy.cn/Article/details/1786458.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4174.sHtML
- http://www.blog.nzfnve.cn/Article/details/7113545.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5950.sHtML
- http://www.blog.nwbbyt.cn/Article/details/27465.sHtML
- http://www.blog.nzfnve.cn/Article/details/826238.sHtML
- http://www.blog.nwbbyt.cn/Article/details/5355.sHtML
- http://www.blog.puhvjy.cn/Article/details/56000.sHtML
- http://www.blog.jnjpgf.cn/Article/details/4909261.sHtML
- http://www.blog.puhvjy.cn/Article/details/76364.sHtML
- http://www.blog.puhvjy.cn/Article/details/1323.sHtML
- http://www.blog.nwbbyt.cn/Article/details/4068.sHtML
- http://www.blog.nwbbyt.cn/Article/details/445460.sHtML
- http://www.blog.nzfnve.cn/Article/details/275103.sHtML
- http://www.blog.jnjpgf.cn/Article/details/8797287.sHtML
- http://www.blog.jnjpgf.cn/Article/details/7300.sHtML

## 项目结构

```
wls/
├── config/                          # 配置目录
│   ├── default.yaml                 # 默认配置（并发数、超时、缓存路径）
│   └── rules/                       # 规则定义目录
│       ├── domain_whitelist.txt     # 域名白名单，每行一个正则
│       └── exclude_patterns.txt     # 排除规则，用于过滤广告或跟踪链接
├── src/                             # 核心源代码
│   ├── core/                        # 引擎核心模块
│   │   ├── crawler.py               # 异步抓取器，管理连接池与重试策略
│   │   ├── parser.py                # 元数据解析器，适配不同 CMS 模板
│   │   ├── fingerprint.py           # 域名指纹采集（SSL、备案、Whois）
│   │   └── storage.py               # 数据库读写抽象层，支持 SQLite / PostgreSQL
│   ├── api/                         # RESTful API 服务
│   │   ├── app.py                   # FastAPI 应用入口
│   │   ├── routes.py                # 路由定义（导入、查询、导出、健康检查）
│   │   └── schemas.py               # Pydantic 请求与响应模型
│   ├── cli/                         # 命令行工具入口
│   │   ├── main.py                  # click 命令组定义
│   │   ├── import_cmd.py            # 链接导入逻辑
│   │   ├── export_cmd.py            # 多格式导出逻辑
│   │   └── serve_cmd.py             # 启动 Web 服务
│   └── utils/                       # 通用工具函数
│       ├── http.py                  # 自定义 HTTP 头构造、代理支持
│       ├── logger.py                # 结构化日志输出（JSON 格式）
│       └── validators.py            # URL 校验、编码转换
├── tests/                           # 单元测试与集成测试
│   ├── unit/                        # 针对 parser、storage 的独立测试
│   ├── integration/                 # 端到端导入导出流程测试
│   └── fixtures/                    # 模拟 HTML 样本与预期输出
├── docs/                            # 文档源文件，用于生成静态站点
│   ├── getting-started.md
│   ├── core-concepts.md
│   ├── operations.md
│   ├── api-reference.md
│   ├── deployment.md
│   ├── troubleshooting.md
│   └── performance.md
├── examples/                        # 使用示例
│   ├── list.txt                     # 示例链接列表文件
│   └── output/                      # 示例导出结果（JSON / Markdown）
├── scripts/                         # 辅助脚本
│   ├── init_db.py                   # 初始化数据库表结构
│   ├── migrate_v1_to_v2.py          # 数据迁移脚本
│   └── cron_health_check.py         # 定时健康检查任务入口
├── docker/                          # 容器化构建文件
│   ├── Dockerfile                   # 基于 Python 3.11-slim 镜像
│   └── docker-compose.yml           # 包含 Redis 与 PostgreSQL 可选服务
├── requirements.txt                 # 生产环境依赖列表
├── requirements-dev.txt             # 开发测试额外依赖（pytest, black, mypy）
├── setup.py                         # 打包发布配置，支持 pip install
├── pyproject.toml                   # 项目元数据与 black/isort 配置
├── Makefile                         # 常用命令快捷方式（install, test, run）
└── README.md                        # 本文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并克隆到本地开发环境。建议使用 Python 3.11 虚拟环境，并执行 `make install-dev` 安装所有开发依赖。
2. 选择标签为 `good-first-issue` 或 `help-wanted` 的 issue 作为起点，或在 Discussions 中提出新功能建议并获得维护者反馈后再开始开发，避免重复或方向偏离。
3. 编写代码时严格遵守项目约定的代码风格（Black 格式化 + isort 导入排序 + mypy 类型检查），并确保所有新增功能都附带对应的单元测试，测试覆盖率不低于 85%。
4. 提交前运行 `make test` 和 `make lint` 确保本地全部通过，并在 PR 描述中清晰说明改动目的、实现方式以及测试覆盖情况。
5. PR 需要至少一位维护者 approve 后才会合并。对于破坏性变更或数据库模型调整，需在 PR 中附带迁移脚本和回滚方案。

## 常见问题

**Q: WLS 能否处理需要登录或带有 Cloudflare 防护的站点？**

A: 目前 WLS 不内置模拟登录或 JavaScript 渲染引擎。对于需要 Cookie 的站点，可以在配置文件中设置全局请求头（如 Authorization 或 Cookie），但对于带有反爬验证的站点（如 Cloudflare 五秒盾），建议使用外部代理或等待后续版本对 Selenium/Playwright 的可选集成支持。

**Q: 导入 250 个链接大约需要多长时间？**

A: 在默认配置（并发数 20，单次超时 10 秒）下，250 个链接通常在 30 到 90 秒内完成，具体取决于目标服务器的响应速度和网络延迟。如果遇到大量超时，建议调整 `config.yaml` 中的 `timeout` 和 `max_redirects` 参数，并检查网络环境。

**Q: 如何迁移数据库或更换后端存储？**

A: WLS 默认使用 SQLite，适合小型部署。如需迁移至 PostgreSQL，可在配置文件中修改 `database.url` 为 PostgreSQL 连接串，并执行 `scripts/migrate_v1_to_v2.py` 进行数据迁移。迁移前请务必备份原始 SQLite 文件。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
