# BlogMap 技术文章聚合导航

BlogMap 是一个面向技术研究者和开发者的分布式博客文章聚合与导航系统。该项目通过统一的数据采集管道，将分散在多个技术博客平台上的高质量文章进行结构化收录，并提供多维度检索与分类浏览能力。

项目定位为技术知识的中转枢纽，而非内容存储仓库。所有资源条目均保留原始出处链接，确保版权归属清晰，同时为技术社区提供一个可公开访问、可扩展的文章导航索引。目标用户包括技术研究人员、开源项目维护者、技术内容创作者以及希望系统化追踪特定领域技术动态的工程师。

---

## 功能概览

**多源文章聚合收录**：系统定期从多个技术博客子域名拉取文章元数据，包括标题、发布时间、分类标签及原始 URL。

**按分类与标签筛选**：每篇文章在收录时均附带至少一个主题分类标签，支持按标签快速定位相关资源。

**时间轴浏览模式**：提供按发布时间倒序排列的浏览视图，便于用户追踪最新技术动态。

**文章详情快速跳转**：每条资源条目均直接链接至原始文章页面，确保用户始终获取第一手内容。

**基础检索与过滤**：支持对已收录文章标题进行关键词匹配检索，并可按域名来源进行过滤。

**收录状态监控面板**：提供可视化的收录进度与各来源站点的健康状态检查，便于运维人员掌握数据采集质量。

**定期更新机制**：系统每日自动执行增量收录任务，确保导航库内容保持活跃。

---

## 应用场景

技术研究选题参考：研究人员可通过 BlogMap 快速浏览近期多个技术博客的高频话题，辅助判断当前技术趋势，为论文或技术报告选题提供依据。

开源项目文档外链管理：开源项目维护者可将 BlogMap 作为项目 README 或文档站点的外部参考资源池，将相关技术文章链接按主题分类后嵌入项目 Wiki，丰富项目生态资料。

技术团队内部知识共享：团队可使用 BlogMap 的筛选与时间轴功能，每周汇总团队成员关注的博客文章，形成内部技术周报的素材来源。

个人技术阅读流整合：开发者可将 BlogMap 作为统一入口，替代逐一访问各博客站点的低效习惯，在单一界面内完成每日技术资讯的扫描与深度阅读筛选。

---

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户请使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/tech-navigation/blogmap.git

# 进入项目目录
cd blogmap

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地 SQLite 数据库
python scripts/init_db.py

# 启动开发服务器（默认监听 127.0.0.1:5000）
python app.py
```

访问 http://127.0.0.1:5000 即可使用本地实例。生产环境部署请参考 `docs/deployment.md`。

---

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，推荐 3.10 |
| SQLite | 3.28.0 及以上 | 内置数据库，用于存储文章索引与元数据 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于采集文章详情页 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析库，用于提取文章标题与标签 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，作为 BeautifulSoup 后端 |
| cron / systemd-timer | 任意版本 | 用于配置周期性增量采集任务（生产环境） |
| git | 2.25.0 及以上 | 版本控制，用于克隆与更新项目 |

---

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | `docs/user-guide.md` | 如何使用 BlogMap 的检索、筛选与时间轴功能？如何提交新站点收录申请？ |
| 运维手册 | `docs/operations.md` | 如何部署生产实例？如何配置每日增量采集任务？如何检查收录状态？ |
| 开发指南 | `docs/development.md` | 如何扩展新的采集源？如何修改分类标签映射规则？如何运行测试套件？ |
| API 参考 | `docs/api.md` | 系统提供了哪些 HTTP 接口用于查询文章列表、标签统计与收录状态？ |

---

## 资源列表

- http://map.blog.nwbbyt.cn/Article/details/251631.sHtML
- http://map.blog.nwbbyt.cn/Article/details/37056.sHtML
- http://map.blog.puhvjy.cn/Article/details/8667891.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8711.sHtML
- http://map.blog.nzfnve.cn/Article/details/1411.sHtML
- http://map.blog.puhvjy.cn/Article/details/3831906.sHtML
- http://map.blog.puhvjy.cn/Article/details/323281.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9480.sHtML
- http://map.blog.nzfnve.cn/Article/details/9735599.sHtML
- http://map.blog.nzfnve.cn/Article/details/888295.sHtML
- http://map.blog.jnjpgf.cn/Article/details/811082.sHtML
- http://map.blog.jnjpgf.cn/Article/details/873016.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4893.sHtML
- http://map.blog.nzfnve.cn/Article/details/7457.sHtML
- http://map.blog.nzfnve.cn/Article/details/456423.sHtML
- http://map.blog.nzfnve.cn/Article/details/37357.sHtML
- http://map.blog.nzfnve.cn/Article/details/3093.sHtML
- http://map.blog.nzfnve.cn/Article/details/99998.sHtML
- http://map.blog.nwbbyt.cn/Article/details/78331.sHtML
- http://map.blog.puhvjy.cn/Article/details/7888893.sHtML
- http://map.blog.nzfnve.cn/Article/details/5308987.sHtML
- http://map.blog.puhvjy.cn/Article/details/2739410.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9818.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8132377.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1131.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7695.sHtML
- http://map.blog.puhvjy.cn/Article/details/931577.sHtML
- http://map.blog.puhvjy.cn/Article/details/994078.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5804983.sHtML
- http://map.blog.nzfnve.cn/Article/details/99189.sHtML
- http://map.blog.puhvjy.cn/Article/details/78412.sHtML
- http://map.blog.jnjpgf.cn/Article/details/19318.sHtML
- http://map.blog.jnjpgf.cn/Article/details/04937.sHtML
- http://map.blog.nzfnve.cn/Article/details/5430164.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4629.sHtML
- http://map.blog.nwbbyt.cn/Article/details/675680.sHtML
- http://map.blog.jnjpgf.cn/Article/details/727622.sHtML
- http://map.blog.nzfnve.cn/Article/details/4627377.sHtML
- http://map.blog.puhvjy.cn/Article/details/4848.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9915165.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9409965.sHtML
- http://map.blog.jnjpgf.cn/Article/details/060569.sHtML
- http://map.blog.puhvjy.cn/Article/details/8255903.sHtML
- http://map.blog.puhvjy.cn/Article/details/6744167.sHtML
- http://map.blog.puhvjy.cn/Article/details/15288.sHtML
- http://map.blog.puhvjy.cn/Article/details/07188.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3949784.sHtML
- http://map.blog.nwbbyt.cn/Article/details/9105.sHtML
- http://map.blog.puhvjy.cn/Article/details/3032.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3550.sHtML
- http://map.blog.nzfnve.cn/Article/details/06027.sHtML
- http://map.blog.nzfnve.cn/Article/details/8584.sHtML
- http://map.blog.nzfnve.cn/Article/details/4787.sHtML
- http://map.blog.nzfnve.cn/Article/details/1712517.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0798209.sHtML
- http://map.blog.puhvjy.cn/Article/details/9362.sHtML
- http://map.blog.nwbbyt.cn/Article/details/48171.sHtML
- http://map.blog.nzfnve.cn/Article/details/816117.sHtML
- http://map.blog.nzfnve.cn/Article/details/786053.sHtML
- http://map.blog.puhvjy.cn/Article/details/701461.sHtML
- http://map.blog.nzfnve.cn/Article/details/4504.sHtML
- http://map.blog.nwbbyt.cn/Article/details/56036.sHtML
- http://map.blog.jnjpgf.cn/Article/details/33651.sHtML
- http://map.blog.puhvjy.cn/Article/details/4450588.sHtML
- http://map.blog.nwbbyt.cn/Article/details/24106.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6620155.sHtML
- http://map.blog.puhvjy.cn/Article/details/133415.sHtML
- http://map.blog.nwbbyt.cn/Article/details/17322.sHtML
- http://map.blog.nzfnve.cn/Article/details/9856.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3062896.sHtML
- http://map.blog.puhvjy.cn/Article/details/384763.sHtML
- http://map.blog.puhvjy.cn/Article/details/156965.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1682.sHtML
- http://map.blog.nzfnve.cn/Article/details/56853.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4467715.sHtML
- http://map.blog.jnjpgf.cn/Article/details/10442.sHtML
- http://map.blog.nwbbyt.cn/Article/details/35501.sHtML
- http://map.blog.jnjpgf.cn/Article/details/32387.sHtML
- http://map.blog.jnjpgf.cn/Article/details/8546.sHtML
- http://map.blog.puhvjy.cn/Article/details/68731.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4557882.sHtML
- http://map.blog.nwbbyt.cn/Article/details/0307221.sHtML
- http://map.blog.jnjpgf.cn/Article/details/595431.sHtML
- http://map.blog.puhvjy.cn/Article/details/1801.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5118.sHtML
- http://map.blog.nzfnve.cn/Article/details/92557.sHtML
- http://map.blog.jnjpgf.cn/Article/details/951086.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2293.sHtML
- http://map.blog.nzfnve.cn/Article/details/08204.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2312.sHtML
- http://map.blog.puhvjy.cn/Article/details/369220.sHtML
- http://map.blog.nzfnve.cn/Article/details/1356.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1482.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1580826.sHtML
- http://map.blog.nzfnve.cn/Article/details/63660.sHtML
- http://map.blog.jnjpgf.cn/Article/details/95196.sHtML
- http://map.blog.nzfnve.cn/Article/details/20552.sHtML
- http://map.blog.jnjpgf.cn/Article/details/098880.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9485.sHtML
- http://map.blog.puhvjy.cn/Article/details/950881.sHtML
- http://map.blog.nwbbyt.cn/Article/details/09672.sHtML
- http://map.blog.puhvjy.cn/Article/details/3958306.sHtML
- http://map.blog.nzfnve.cn/Article/details/4559711.sHtML
- http://map.blog.nwbbyt.cn/Article/details/069526.sHtML
- http://map.blog.nzfnve.cn/Article/details/87113.sHtML
- http://map.blog.nwbbyt.cn/Article/details/852130.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3403422.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8701906.sHtML
- http://map.blog.jnjpgf.cn/Article/details/07327.sHtML
- http://map.blog.jnjpgf.cn/Article/details/5663.sHtML
- http://map.blog.nzfnve.cn/Article/details/9017328.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4262377.sHtML
- http://map.blog.nwbbyt.cn/Article/details/501290.sHtML
- http://map.blog.nwbbyt.cn/Article/details/079393.sHtML
- http://map.blog.puhvjy.cn/Article/details/6318112.sHtML
- http://map.blog.jnjpgf.cn/Article/details/76680.sHtML
- http://map.blog.puhvjy.cn/Article/details/26533.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2822102.sHtML
- http://map.blog.puhvjy.cn/Article/details/9418474.sHtML
- http://map.blog.nwbbyt.cn/Article/details/239909.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6539.sHtML
- http://map.blog.puhvjy.cn/Article/details/098408.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4649.sHtML
- http://map.blog.jnjpgf.cn/Article/details/15753.sHtML
- http://map.blog.puhvjy.cn/Article/details/759948.sHtML
- http://map.blog.nwbbyt.cn/Article/details/922734.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6213927.sHtML
- http://map.blog.nzfnve.cn/Article/details/8529.sHtML
- http://map.blog.nzfnve.cn/Article/details/7106734.sHtML
- http://map.blog.nzfnve.cn/Article/details/8453.sHtML
- http://map.blog.nwbbyt.cn/Article/details/174505.sHtML
- http://map.blog.nzfnve.cn/Article/details/3309986.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3881.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8027579.sHtML
- http://map.blog.puhvjy.cn/Article/details/2780.sHtML
- http://map.blog.nzfnve.cn/Article/details/98217.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4145786.sHtML
- http://map.blog.nzfnve.cn/Article/details/3542.sHtML
- http://map.blog.puhvjy.cn/Article/details/7191097.sHtML
- http://map.blog.puhvjy.cn/Article/details/6878926.sHtML
- http://map.blog.puhvjy.cn/Article/details/330321.sHtML
- http://map.blog.jnjpgf.cn/Article/details/12782.sHtML
- http://map.blog.nwbbyt.cn/Article/details/125396.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3514862.sHtML
- http://map.blog.nzfnve.cn/Article/details/7565553.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3422.sHtML
- http://map.blog.nzfnve.cn/Article/details/0544.sHtML
- http://map.blog.puhvjy.cn/Article/details/3679006.sHtML
- http://map.blog.nwbbyt.cn/Article/details/77256.sHtML
- http://map.blog.puhvjy.cn/Article/details/2862661.sHtML
- http://map.blog.puhvjy.cn/Article/details/234996.sHtML
- http://map.blog.nzfnve.cn/Article/details/64113.sHtML
- http://map.blog.nzfnve.cn/Article/details/58069.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2748019.sHtML
- http://map.blog.nwbbyt.cn/Article/details/35782.sHtML
- http://map.blog.nwbbyt.cn/Article/details/61940.sHtML
- http://map.blog.jnjpgf.cn/Article/details/4952505.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3066.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5411599.sHtML
- http://map.blog.nwbbyt.cn/Article/details/236685.sHtML
- http://map.blog.nzfnve.cn/Article/details/10622.sHtML
- http://map.blog.nzfnve.cn/Article/details/1277749.sHtML
- http://map.blog.nzfnve.cn/Article/details/60285.sHtML
- http://map.blog.jnjpgf.cn/Article/details/392223.sHtML
- http://map.blog.nzfnve.cn/Article/details/9249.sHtML
- http://map.blog.nwbbyt.cn/Article/details/975293.sHtML
- http://map.blog.nzfnve.cn/Article/details/3997.sHtML
- http://map.blog.jnjpgf.cn/Article/details/9546212.sHtML
- http://map.blog.puhvjy.cn/Article/details/5068244.sHtML
- http://map.blog.nwbbyt.cn/Article/details/261435.sHtML
- http://map.blog.nwbbyt.cn/Article/details/847190.sHtML
- http://map.blog.nwbbyt.cn/Article/details/685701.sHtML
- http://map.blog.nzfnve.cn/Article/details/6177711.sHtML
- http://map.blog.nwbbyt.cn/Article/details/778205.sHtML
- http://map.blog.nwbbyt.cn/Article/details/7788.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2955238.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5220454.sHtML
- http://map.blog.nwbbyt.cn/Article/details/1486605.sHtML
- http://map.blog.puhvjy.cn/Article/details/24240.sHtML
- http://map.blog.nwbbyt.cn/Article/details/4663493.sHtML
- http://map.blog.nwbbyt.cn/Article/details/844415.sHtML
- http://map.blog.nwbbyt.cn/Article/details/241052.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2200348.sHtML
- http://map.blog.nzfnve.cn/Article/details/42647.sHtML
- http://map.blog.nwbbyt.cn/Article/details/36393.sHtML
- http://map.blog.nzfnve.cn/Article/details/1804385.sHtML
- http://map.blog.jnjpgf.cn/Article/details/236263.sHtML
- http://map.blog.jnjpgf.cn/Article/details/2316.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6740499.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0134476.sHtML
- http://map.blog.puhvjy.cn/Article/details/3505612.sHtML
- http://map.blog.puhvjy.cn/Article/details/689981.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1712.sHtML
- http://map.blog.nwbbyt.cn/Article/details/96100.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5916580.sHtML
- http://map.blog.nwbbyt.cn/Article/details/48052.sHtML
- http://map.blog.nwbbyt.cn/Article/details/8566.sHtML
- http://map.blog.nzfnve.cn/Article/details/5066.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3450183.sHtML
- http://map.blog.puhvjy.cn/Article/details/9896056.sHtML
- http://map.blog.puhvjy.cn/Article/details/5812190.sHtML
- http://map.blog.nzfnve.cn/Article/details/287873.sHtML
- http://map.blog.jnjpgf.cn/Article/details/62389.sHtML
- http://map.blog.nzfnve.cn/Article/details/16591.sHtML
- http://map.blog.nwbbyt.cn/Article/details/75925.sHtML
- http://map.blog.puhvjy.cn/Article/details/73441.sHtML
- http://map.blog.nwbbyt.cn/Article/details/999178.sHtML
- http://map.blog.jnjpgf.cn/Article/details/275509.sHtML
- http://map.blog.puhvjy.cn/Article/details/564324.sHtML
- http://map.blog.jnjpgf.cn/Article/details/284487.sHtML
- http://map.blog.puhvjy.cn/Article/details/7876805.sHtML
- http://map.blog.puhvjy.cn/Article/details/441748.sHtML
- http://map.blog.puhvjy.cn/Article/details/3414.sHtML
- http://map.blog.nzfnve.cn/Article/details/573831.sHtML
- http://map.blog.nzfnve.cn/Article/details/8599.sHtML
- http://map.blog.jnjpgf.cn/Article/details/3942.sHtML
- http://map.blog.puhvjy.cn/Article/details/97813.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3917.sHtML
- http://map.blog.jnjpgf.cn/Article/details/6725.sHtML
- http://map.blog.nwbbyt.cn/Article/details/404079.sHtML
- http://map.blog.nzfnve.cn/Article/details/9852.sHtML
- http://map.blog.puhvjy.cn/Article/details/933887.sHtML
- http://map.blog.nwbbyt.cn/Article/details/38952.sHtML
- http://map.blog.puhvjy.cn/Article/details/23064.sHtML
- http://map.blog.nwbbyt.cn/Article/details/53403.sHtML
- http://map.blog.jnjpgf.cn/Article/details/0194492.sHtML
- http://map.blog.nzfnve.cn/Article/details/57212.sHtML
- http://map.blog.nzfnve.cn/Article/details/02897.sHtML
- http://map.blog.nwbbyt.cn/Article/details/23487.sHtML
- http://map.blog.puhvjy.cn/Article/details/489579.sHtML
- http://map.blog.nwbbyt.cn/Article/details/5274541.sHtML
- http://map.blog.jnjpgf.cn/Article/details/10994.sHtML
- http://map.blog.nzfnve.cn/Article/details/0030942.sHtML
- http://map.blog.nzfnve.cn/Article/details/72434.sHtML
- http://map.blog.nwbbyt.cn/Article/details/3977605.sHtML
- http://map.blog.puhvjy.cn/Article/details/2382002.sHtML
- http://map.blog.nwbbyt.cn/Article/details/40980.sHtML
- http://map.blog.nzfnve.cn/Article/details/103011.sHtML
- http://map.blog.nwbbyt.cn/Article/details/105351.sHtML
- http://map.blog.nwbbyt.cn/Article/details/2465.sHtML
- http://map.blog.puhvjy.cn/Article/details/76403.sHtML
- http://map.blog.nzfnve.cn/Article/details/540518.sHtML
- http://map.blog.nwbbyt.cn/Article/details/6402680.sHtML
- http://map.blog.jnjpgf.cn/Article/details/1134591.sHtML
- http://map.blog.puhvjy.cn/Article/details/40299.sHtML
- http://map.blog.nzfnve.cn/Article/details/20021.sHtML
- http://map.blog.nzfnve.cn/Article/details/70407.sHtML
- http://map.blog.nwbbyt.cn/Article/details/81024.sHtML
- http://map.blog.nzfnve.cn/Article/details/8385563.sHtML
- http://map.blog.nzfnve.cn/Article/details/033910.sHtML

## 项目结构

```
blogmap/
├── app.py                      # Flask 应用主入口，注册路由与启动服务
├── requirements.txt            # Python 依赖列表（requests, flask, bs4, lxml）
├── config/
│   ├── __init__.py             # 配置模块初始化
│   ├── settings.py             # 环境变量读取与默认配置（数据库路径、采集间隔等）
│   └── sources.yaml            # 收录源站点列表与分类映射规则（YAML 格式）
├── core/
│   ├── __init__.py             # 核心模块初始化
│   ├── crawler.py              # 文章采集引擎，处理 HTTP 请求与 HTML 解析
│   ├── indexer.py              # 索引更新逻辑，负责去重与标签规范化
│   └── scheduler.py            # 定时任务调度器（基于 APScheduler）
├── models/
│   ├── __init__.py             # 数据模型初始化
│   ├── database.py             # SQLite 连接管理与基础 CRUD 操作
│   └── article.py              # 文章实体类，定义字段与序列化方法
├── static/
│   ├── css/                    # 前端样式文件（基于 Bootstrap 定制）
│   └── js/                     # 前端交互脚本（检索、分页、状态刷新）
├── templates/
│   ├── base.html               # 基础模板，包含导航栏与页脚
│   ├── index.html              # 首页，展示时间轴与分类筛选器
│   └── detail.html             # 文章详情页（展示元数据并跳转至原始链接）
├── scripts/
│   ├── init_db.py              # 初始化数据库表结构
│   ├── import_links.py         # 批量导入资源列表（用于初始数据填充）
│   └── health_check.py         # 检查各收录源站点可达性与响应时间
├── tests/
│   ├── test_crawler.py         # 采集引擎单元测试
│   ├── test_indexer.py         # 索引逻辑测试
│   └── fixtures/               # 测试用 HTML 样本数据
├── docs/
│   ├── user-guide.md           # 用户手册
│   ├── operations.md           # 运维手册
│   ├── development.md          # 开发指南
│   └── api.md                  # API 参考文档
└── README.md                   # 项目说明文档（当前文件）
```

---

## 贡献指南

1. 复刻项目仓库至个人账号，在本地创建新分支进行开发。分支命名建议采用 `feature/功能简述` 或 `fix/问题描述` 格式。

2. 编写或修改代码后，请确保所有现有单元测试通过，并为新增功能补充对应的测试用例。测试文件位于 `tests/` 目录下。

3. 若涉及收录源配置变更（如新增站点或调整分类标签），请同步修改 `config/sources.yaml` 文件，并在 Pull Request 描述中说明变更原因及验证结果。

4. 提交 Pull Request 前，请执行代码格式化工具（black）与静态检查（flake8），确保代码风格与项目现有风格保持一致。

5. Pull Request 合并前需至少一位项目维护者进行 Code Review，Review 通过后由维护者执行合并操作。

---

## 常见问题

**Q：系统每天什么时间执行增量采集任务？能否手动触发？**

A：默认增量采集任务每日凌晨 2:00 执行，生产环境通过系统 cron 或 systemd-timer 触发。如需手动触发，可在项目根目录执行 `python scripts/manual_crawl.py` 脚本，该脚本会调用核心采集引擎并输出本次新收录的文章数量。

**Q：如何添加一个新的博客站点作为收录源？**

A：在 `config/sources.yaml` 文件中新增一个条目，包含站点域名、基础 URL 路径、文章列表页的 CSS 选择器规则以及分类标签映射。添加后运行 `python scripts/validate_sources.py` 验证配置有效性，验证通过后重新启动服务即可。详细语法请参考 `docs/development.md` 中的扩展采集源章节。

**Q：收录的文章是否会存储完整内容？是否涉及版权问题？**

A：系统仅存储文章标题、发布时间、分类标签及原始 URL 等元数据，不存储文章正文。所有资源条目均直接链接至原始出处，用户点击后跳转至源站阅读完整内容。该设计符合合理引用原则，若版权方要求移除特定条目，请联系项目维护者处理。

---

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
