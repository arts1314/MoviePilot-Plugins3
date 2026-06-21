# P115StrgmSub - 115网盘订阅追更魔改版

金愉皓定制的 MoviePilot 第三方插件,基于 [mrtian2016/MoviePilot-Plugins](https://github.com/mrtian2016/MoviePilot-Plugins) fork。

## 🔥 魔改内容(相对于上游 v1.5.3)

- **DoVi(杜比视界)硬拒绝改造**:内置全局兜底排除正则 `DoVi|Dolby[\s.]?Vision|DOVI|杜比视界`,所有订阅转存前会先过这一关,命中即不放行(任何模式下)。
- **SubscribeFilter 扩展**:新增 `include / exclude / filter` 3 个字段,支持基于文件名的硬拒绝型过滤。
- **SyncHandler 注入**:新增 `global_exclude` 参数,所有订阅共用全局兜底规则。
- **UI 配置面板**:新增"全局兜底排除(正则,命中即拒绝)"输入框,可在配置页直接修改兜底正则。
- **plugin_id 保持 `P115StrgmSub`**:跟上游一致,可直接覆盖升级,`user.db` 现有 47 字段配置无缝迁移。

## 📦 安装

在 MoviePilot 的 `PLUGIN_MARKET` 环境变量中添加本仓地址:

```
https://github.com/jinyuhao-886/MoviePilot-Plugins/
```

然后在 MoviePilot 后台 → 插件市场 → 搜索"115网盘订阅追更魔改版" → 安装。

## 🔄 升级

在 MoviePilot 后台点"检查更新",会显示新版本号(本仓 git commit SHA 决定)。直接点升级即可。

⚠️ **不要同时安装本魔改版和 mrtian2016 上游版**(plugin_id 相同,会冲突)。

## 🐛 已知问题

如果遇到 `pip check` 失败 + "已清理对应插件目录" 警告,说明 venv 缺少 `future` 包。请先执行:
```bash
docker exec moviepilot-v2 pip install future
```
然后重启 MP 容器。本仓的 `entrypoint_wrapper.sh` 已增强,会自动兜底装 future(见 skill)。

## 📝 完整工作流

本插件配合 [P115StrmHelper](https://github.com/DDSRem-Dev/MoviePilot-Plugins) 可实现完整的自动化追剧流程:

```
MoviePilot订阅 -> 本插件搜索转存 -> STRM助手生成STRM -> 媒体库刮削 -> 播放器观看
```

## 🛠️ 定制开发

所有魔改都在以下 4 个文件中(对比 upstream 看 git diff 即可):

- `plugins.v2/p115strgmsub/utils/file_matcher.py` - SubscribeFilter + _is_rejected()
- `plugins.v2/p115strgmsub/handlers/sync.py` - SyncHandler 加 global_exclude + effective_exclude
- `plugins.v2/p115strgmsub/__init__.py` - 类属性 _global_exclude + init_plugin 读 + get_config 暴露
- `plugins.v2/p115strgmsub/ui/config.py` - 全局兜底排除输入框

## 致谢

- 上游作者 [mrtian2016](https://github.com/mrtian2016/MoviePilot-Plugins)
- 115网盘STRM助手 [DDSRem-Dev](https://github.com/DDSRem-Dev/MoviePilot-Plugins)
- MoviePilot [jxxghp](https://github.com/jxxghp/MoviePilot)