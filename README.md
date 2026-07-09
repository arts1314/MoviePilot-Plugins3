# MoviePilot Plugins

> **MoviePilot 第三方插件仓库** — 包含自研 & 魔改插件

**维护：** [jinyuhao-886](https://github.com/jinyuhao-886)

---

## 📦 插件列表

### 1. 🤖 Doc911Subscribe — 金山文档订阅同步

从 KDocs（金山文档）xlsx 表格自动解析在播剧集并添加 MP 订阅。

**适用场景：** 内部共享追剧表 → 自动同步到 MoviePilot 订阅

| 功能 | 说明 |
|------|------|
| 定时执行 | 每天 21:01 自动拉取最新文档 |
| 三段解析 | 国产剧 / 国外剧 / 综艺 分区过滤 |
| 在播识别 | 自动过滤已完结剧集，只追更新中的 |
| AI 辅助识别 | TMDB 匹配失败时调用 AI 智能助手自动纠正 |
| 季数提取 | 自动提取"第X季"并正确传参 |

> 📄 [完整文档 →](plugins.v2/doc911subscribe/README.md)

---

### 2. 🔧 P115StrgmSub — 115网盘订阅追更魔改版

基于 [mrtian2016/MoviePilot-Plugins](https://github.com/mrtian2016/MoviePilot-Plugins) 的 `P115StrgmSub` 深度魔改增强。

**核心魔改特性：**

| 特性 | 说明 |
|------|------|
| 调度锁解除 | 无最低间隔限制 |
| 网盘洗版 | 评分对比 → 自动转存高分 → 联动删除低分 |
| PT 洗版 | 下载前评分拦截，只有评分提升才放行 |
| 屏蔽态调度 | 屏蔽态仅 115 网盘 / 开放态恢复全部站点 |
| 规则组管理 | 自动注入 4 套自定义规则组 |
| 双渠道通知 | PT / 网盘洗版分开推送通知 |

> 📄 [完整文档 →](README_P115StrgmSub.md)

---

### 3. 🔩 LibraryScraper Enhanced — 媒体库刮削增强

基于官方 `LibraryScraper` 插件的功能增强版。

**增强特性：**
- 多线程并行刮削（官方版串行 `for` 循环 → ThreadPoolExecutor）
- 性能提升，大数据量媒体库显著加速

---

## 🚀 安装

### 第 1 步：添加自定义插件源

在 MP（MoviePilot）的 **插件源设置** 中添加：

```
https://github.com/jinyuhao-886/MoviePilot-Plugins
```

### 第 2 步：安装插件

重启 MP → 进入插件市场 → 搜索插件名 → 安装

---

## 📁 仓库结构

```
MoviePilot-Plugins/
├── plugins.v2/
│   ├── doc911subscribe/          # 金山文档订阅同步
│   │   └── __init__.py
│   ├── libraryscraper_enhanced/  # 媒体库刮削增强
│   │   └── __init__.py
│   └── p115strgmsub/            # 115网盘订阅追更魔改
│       └── __init__.py
├── package.v2.json               # 插件市场索引
├── package.json
├── README.md                     ← 你在这里
└── README_P115StrgmSub.md        # P115StrgmSub 完整文档
```

---

## 🔗 相关链接

- **[MoviePilot](https://github.com/jxxghp/MoviePilot)** - 本体项目
- **[原版 P115StrgmSub](https://github.com/mrtian2016/MoviePilot-Plugins)** - 上游插件
- **CloudDrive2** - 115 网盘挂载方案
