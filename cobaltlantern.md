# BlogNav 技术资源导航站

BlogNav 是一个面向开发者与技术研究者的结构化外链资源聚合系统。本项目不对原始内容做二次加工，仅提供分类索引与稳定的访问入口，帮助用户快速定位分布于多个博客子域名下的技术文章、教程与代码示例。目标用户包括正在学习特定编程语言或框架的初学者、需要查阅特定实现方案的中级开发者，以及希望从海量博客文章中筛选有效信息的资深工程师。BlogNav 通过统一的目录结构与标准化的文档体系，将分散在多个独立博客站点中的技术内容整合为可检索、可追溯的资源集合，显著降低信息筛选成本。

## 功能概览

- 多源聚合索引：支持从多个独立博客子域名自动采集文章元数据，生成统一的资源访问入口列表。

- 结构化目录输出：按技术领域、发表日期或文章类型生成分类目录，便于用户按需浏览。

- 原始链接直出：所有资源链接保持用户提交时的原始格式，不做任何协议补全或域名改写，确保访问路径的精确性。

- 静态资源缓存：对高频访问的文章链接提供本地缓存校验，减少外部站点不可用导致的访问失败。

- 批次管理机制：支持按导入批次（如第 38/40 批）筛选和展示资源，便于增量更新与历史回溯。

- 依赖环境检测：启动时自动检查运行环境、网络连通性与必需依赖，输出详细的检测报告。

- 访问统计看板：提供简单的点击计数与来源分析，帮助管理员了解热点资源分布。

## 应用场景

1. 技术团队内部知识库补充：团队可将 BlogNav 部署为内部导航页，成员通过统一入口访问分散在多个个人博客中的技术笔记与解决方案，避免重复搜索。

2. 个人开发者学习路线规划：开发者可根据 BlogNav 输出的分类目录，按主题顺序阅读来自不同博客的系列文章，系统化地构建知识体系。

3. 开源项目文档外链管理：开源项目维护者可将 BlogNav 作为项目 Wiki 的补充模块，集中列出所有参考过的外部技术博客链接，方便贡献者追溯设计依据。

4. 技术社区资源分享平台：技术社区运营方可基于 BlogNav 构建公开的资源导航站，将成员提交的优质博客链接按批次整理并对外开放查询。

5. 离线文档归档辅助：结合静态缓存功能，BlogNav 可用于批量获取指定批次文章的本地快照，供内部网络或无网络环境下的查阅使用。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境。请确保已安装 Git 与 Node.js（版本参见安装要求）。

```bash
# 克隆仓库
git clone https://github.com/your-org/blognav.git
cd blognav

# 安装依赖
npm install

# 启动开发服务器（默认端口 3000）
npm run dev
```

生产环境构建与启动：

```bash
npm run build
npm start
```

访问控制台输出中显示的本地地址（如 http://localhost:3000）即可进入导航站首页。首次启动时将自动加载资源索引文件，若索引文件缺失，系统会使用内置的初始数据集。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | >= 18.0.0 | 运行时环境，用于执行核心服务与构建脚本 |
| npm | >= 9.0.0 | 包管理器，用于安装第三方依赖库 |
| Git | >= 2.30.0 | 版本控制工具，用于克隆仓库与拉取更新 |
| SQLite3 | 内置（无需额外安装） | 轻量级数据库，用于存储资源索引与访问日志 |
| 网络连接 | 外网可访问 | 用于首次加载时校验外部资源链接的可达性（可选） |
| 操作系统 | Linux / macOS / Windows 10+ | 支持主流操作系统，Windows 下推荐使用 WSL2 |
| 内存 | >= 512 MB | 运行时内存占用，不含浏览器或其他应用程序 |
| 硬盘空间 | >= 200 MB | 包含源码、依赖包及初始索引数据 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | /docs/getting-started.md | 如何快速部署、配置环境变量、验证服务是否正常运行 |
| 使用 | /docs/usage-guide.md | 如何浏览分类目录、搜索资源、查看访问统计与批次信息 |
| 管理 | /docs/admin-manual.md | 如何新增资源批次、更新索引、清理缓存、备份数据库 |
| 开发 | /docs/developer-guide.md | 如何扩展数据源插件、修改目录结构、自定义主题样式 |
| 故障 | /docs/troubleshooting.md | 常见启动错误、链接访问失败、数据库锁问题的排查方法 |
| 参考 | /docs/api-reference.md | 对外提供的 RESTful API 接口说明与调用示例 |

## 资源列表

- http://h5.blog.nwbbyt.cn/Article/details/3959755.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8814.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6841.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/89508.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4075.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2494.sHtML
- http://h5.blog.nzfnve.cn/Article/details/09375.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1183.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1375468.sHtML
- http://h5.blog.puhvjy.cn/Article/details/46854.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7756.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5021995.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0979.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8666.sHtML
- http://h5.blog.puhvjy.cn/Article/details/5762261.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6489435.sHtML
- http://h5.blog.puhvjy.cn/Article/details/772872.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/41519.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/1421.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/71629.sHtML
- http://h5.blog.puhvjy.cn/Article/details/529195.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/182312.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/714687.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/262821.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5685541.sHtML
- http://h5.blog.puhvjy.cn/Article/details/405006.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/90537.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7836.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8520755.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/287848.sHtML
- http://h5.blog.puhvjy.cn/Article/details/68575.sHtML
- http://h5.blog.nzfnve.cn/Article/details/346908.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0376966.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4543.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5427476.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5987.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4470795.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7647625.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/076033.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4908.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/0723053.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/76491.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5422.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9934.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6815584.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3794472.sHtML
- http://h5.blog.puhvjy.cn/Article/details/251907.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0621.sHtML
- http://h5.blog.puhvjy.cn/Article/details/801026.sHtML
- http://h5.blog.nzfnve.cn/Article/details/21412.sHtML
- http://h5.blog.nzfnve.cn/Article/details/18785.sHtML
- http://h5.blog.puhvjy.cn/Article/details/2363.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4971121.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6295.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9255500.sHtML
- http://h5.blog.nzfnve.cn/Article/details/853965.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3725712.sHtML
- http://h5.blog.nzfnve.cn/Article/details/942992.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/502275.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2209285.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7199.sHtML
- http://h5.blog.nzfnve.cn/Article/details/98142.sHtML
- http://h5.blog.puhvjy.cn/Article/details/219658.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6626535.sHtML
- http://h5.blog.nzfnve.cn/Article/details/01170.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8373.sHtML
- http://h5.blog.puhvjy.cn/Article/details/68287.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9629463.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2698.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5616.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2070304.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6305210.sHtML
- http://h5.blog.puhvjy.cn/Article/details/018024.sHtML
- http://h5.blog.puhvjy.cn/Article/details/40785.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6579.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5885.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9275.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/854694.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3245545.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3976954.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2104033.sHtML
- http://h5.blog.puhvjy.cn/Article/details/1348888.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3498.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3965100.sHtML
- http://h5.blog.puhvjy.cn/Article/details/41351.sHtML
- http://h5.blog.puhvjy.cn/Article/details/93097.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/8277076.sHtML
- http://h5.blog.puhvjy.cn/Article/details/651354.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/83578.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1646.sHtML
- http://h5.blog.nzfnve.cn/Article/details/483986.sHtML
- http://h5.blog.puhvjy.cn/Article/details/326835.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3800512.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3805245.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7086858.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5464652.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3033.sHtML
- http://h5.blog.puhvjy.cn/Article/details/225163.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5353.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8441412.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5093.sHtML
- http://h5.blog.puhvjy.cn/Article/details/706867.sHtML
- http://h5.blog.nzfnve.cn/Article/details/139217.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/690696.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9418653.sHtML
- http://h5.blog.nzfnve.cn/Article/details/82275.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/455039.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9656377.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/790901.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/228963.sHtML
- http://h5.blog.nzfnve.cn/Article/details/898656.sHtML
- http://h5.blog.puhvjy.cn/Article/details/890337.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/4724.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4295318.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3226936.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/83604.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/517554.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/97382.sHtML
- http://h5.blog.nzfnve.cn/Article/details/67636.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6374.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9272.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/96456.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4850.sHtML
- http://h5.blog.puhvjy.cn/Article/details/707151.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7943.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/824453.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/84840.sHtML
- http://h5.blog.nzfnve.cn/Article/details/06825.sHtML
- http://h5.blog.puhvjy.cn/Article/details/443710.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/408832.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/5811783.sHtML
- http://h5.blog.puhvjy.cn/Article/details/607492.sHtML
- http://h5.blog.nzfnve.cn/Article/details/340926.sHtML
- http://h5.blog.nzfnve.cn/Article/details/850421.sHtML
- http://h5.blog.nzfnve.cn/Article/details/960089.sHtML
- http://h5.blog.puhvjy.cn/Article/details/21222.sHtML
- http://h5.blog.nzfnve.cn/Article/details/59345.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8549537.sHtML
- http://h5.blog.puhvjy.cn/Article/details/494541.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6123.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0938099.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/8920.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7069.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/67358.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/711376.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/50195.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4268.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3340273.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2360381.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3333.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6826681.sHtML
- http://h5.blog.puhvjy.cn/Article/details/4425828.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7559665.sHtML
- http://h5.blog.puhvjy.cn/Article/details/97294.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/233225.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3837870.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/162060.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5758.sHtML
- http://h5.blog.puhvjy.cn/Article/details/9681261.sHtML
- http://h5.blog.puhvjy.cn/Article/details/280206.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/448197.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/973938.sHtML
- http://h5.blog.puhvjy.cn/Article/details/7602881.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/513573.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9926.sHtML
- http://h5.blog.puhvjy.cn/Article/details/05628.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/081907.sHtML
- http://h5.blog.puhvjy.cn/Article/details/0684723.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/395291.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7928891.sHtML
- http://h5.blog.nzfnve.cn/Article/details/0530.sHtML
- http://h5.blog.nzfnve.cn/Article/details/56375.sHtML
- http://h5.blog.nzfnve.cn/Article/details/45325.sHtML
- http://h5.blog.puhvjy.cn/Article/details/29210.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/416704.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9842387.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7307.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/9650.sHtML
- http://h5.blog.nzfnve.cn/Article/details/4189.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/171129.sHtML
- http://h5.blog.nzfnve.cn/Article/details/9476.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/822263.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2233.sHtML
- http://h5.blog.nzfnve.cn/Article/details/47454.sHtML
- http://h5.blog.nzfnve.cn/Article/details/10992.sHtML
- http://h5.blog.puhvjy.cn/Article/details/02332.sHtML
- http://h5.blog.puhvjy.cn/Article/details/6108.sHtML
- http://h5.blog.nzfnve.cn/Article/details/403748.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/95807.sHtML
- http://h5.blog.puhvjy.cn/Article/details/41150.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/01445.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/558790.sHtML
- http://h5.blog.nzfnve.cn/Article/details/8296189.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/791825.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/287508.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8611.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/76854.sHtML
- http://h5.blog.puhvjy.cn/Article/details/880204.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/380818.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/65998.sHtML
- http://h5.blog.puhvjy.cn/Article/details/73815.sHtML
- http://h5.blog.puhvjy.cn/Article/details/57047.sHtML
- http://h5.blog.nzfnve.cn/Article/details/7108.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/670052.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/7152166.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2939.sHtML
- http://h5.blog.puhvjy.cn/Article/details/178025.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2604662.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/012888.sHtML
- http://h5.blog.nzfnve.cn/Article/details/77147.sHtML
- http://h5.blog.puhvjy.cn/Article/details/8061676.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5701708.sHtML
- http://h5.blog.puhvjy.cn/Article/details/638233.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/12113.sHtML
- http://h5.blog.nzfnve.cn/Article/details/224293.sHtML
- http://h5.blog.nzfnve.cn/Article/details/2936.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3423746.sHtML
- http://h5.blog.nzfnve.cn/Article/details/3693.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/3695.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4825.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/2114.sHtML
- http://h5.blog.puhvjy.cn/Article/details/53840.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/3031.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5319658.sHtML
- http://h5.blog.puhvjy.cn/Article/details/957560.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/687909.sHtML
- http://h5.blog.nzfnve.cn/Article/details/6581726.sHtML
- http://h5.blog.puhvjy.cn/Article/details/05783.sHtML
- http://h5.blog.nzfnve.cn/Article/details/51195.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/673858.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/09158.sHtML
- http://h5.blog.puhvjy.cn/Article/details/3192.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5066.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/5303.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/67129.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5534.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1539153.sHtML
- http://h5.blog.nzfnve.cn/Article/details/5498163.sHtML
- http://h5.blog.puhvjy.cn/Article/details/142427.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/885204.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/1159699.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/0206744.sHtML
- http://h5.blog.nzfnve.cn/Article/details/1610364.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/7058.sHtML
- http://h5.blog.nwbbyt.cn/Article/details/73957.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/02220.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/9002556.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/6601923.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/4859.sHtML
- http://h5.blog.jnjpgf.cn/Article/details/2342146.sHtML

## 项目结构

```
blognav/
├── src/                                # 核心源代码目录
│   ├── core/                           # 核心引擎模块
│   │   ├── indexer.js                  # 资源索引构建器，负责解析链接元数据
│   │   ├── cache.js                    # 缓存管理，控制本地存储与过期策略
│   │   └── validator.js                # 链接格式校验与协议规范化检查
│   ├── routes/                         # 路由控制器
│   │   ├── api.js                      # RESTful API 路由定义
│   │   └── web.js                      # 前端页面路由与渲染逻辑
│   ├── services/                       # 业务服务层
│   │   ├── batchService.js             # 批次管理服务，处理导入、查询与切换
│   │   └── statsService.js             # 访问统计服务，记录点击与来源
│   ├── models/                         # 数据模型定义
│   │   ├── resourceModel.js            # 资源链接的数据结构与验证规则
│   │   └── batchModel.js               # 批次元数据模型
│   ├── utils/                          # 通用工具函数
│   │   ├── logger.js                   # 日志输出工具，支持分级与文件写入
│   │   └── network.js                  # 网络请求辅助函数，含超时与重试
│   └── app.js                          # 应用入口，初始化服务与中间件
├── config/                             # 配置文件目录
│   ├── default.json                    # 默认配置项（端口、缓存时间、日志级别）
│   └── production.json                 # 生产环境覆盖配置
├── data/                               # 数据存储目录
│   ├── index.db                        # SQLite 数据库文件，存储资源索引与统计
│   └── batches/                        # 批次导入原始数据存档
│       └── batch_38.json               # 第 38 批资源原始数据备份
├── docs/                               # 文档目录，与文档导航章节对应
│   ├── getting-started.md              # 入门指南
│   ├── usage-guide.md                  # 使用手册
│   ├── admin-manual.md                 # 管理员手册
│   └── developer-guide.md              # 开发者指南
├── public/                             # 静态资源目录
│   ├── css/                            # 样式表文件
│   │   └── main.css                    # 全局主题样式
│   └── js/                             # 前端 JavaScript 脚本
│       └── dashboard.js                # 控制台交互逻辑
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 单元测试用例
│   └── integration/                    # 集成测试脚本
├── .env.example                        # 环境变量示例文件
├── package.json                        # npm 项目描述文件，含依赖与脚本
├── README.md                           # 项目说明文档（本文件）
└── LICENSE                             # MIT 许可证文本
```

## 贡献指南

1. 问题报告与功能建议：请在 GitHub Issues 中提交详细的问题描述或功能请求，包含复现步骤、预期行为与实际行为。对于功能建议，请说明使用场景与收益。

2. 代码贡献流程：Fork 本仓库，在您的分支上进行开发，确保代码通过所有单元测试与集成测试。提交前运行 npm run lint 进行代码风格检查。完成后提交 Pull Request，描述变更内容与影响范围。

3. 文档与资源列表更新：若您发现资源链接失效或需要新增批次，请按照 data/batches/ 目录下的示例格式准备 JSON 文件，并在 Pull Request 中注明变更原因与验证结果。

4. 本地测试环境搭建：参考安装要求配置好依赖后，运行 npm run test 执行全部测试用例。新增功能请同步补充对应的测试代码，确保测试覆盖率不低于 80%。

5. 社区行为准则：本项目的所有参与者需遵守贡献者公约，保持友善、专业的沟通氛围。维护者保留对不符合准则的贡献进行退回的权利。

## 常见问题

Q：启动时提示 "SQLite3 数据库无法写入"，如何解决？

A：请检查 data/ 目录是否存在且具有写入权限。在 Linux/macOS 下执行 chmod 755 data/ 赋予目录读写权限。若目录不存在，请手动创建该目录。若权限无误但仍报错，请检查磁盘空间是否充足。

Q：访问资源链接时返回 404 或超时，是否影响导航站自身运行？

A：BlogNav 仅做链接聚合与展示，不代理或缓存原始内容。单个外部链接的不可用不会影响导航站本身的正常运行。您可以在管理员后台标记失效链接，系统将在统计看板中单独列出不可达资源。

Q：如何导入后续批次（如第 39 批）的资源？

A：将新批次的链接列表按 JSON 格式整理后，放入 data/batches/ 目录下，命名格式为 batch_39.json。随后访问管理接口 /api/batch/import 触发导入任务，系统会自动合并索引并更新目录结构。详细操作请参阅 admin-manual.md 中的批次管理章节。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-07-06 03:28:41
