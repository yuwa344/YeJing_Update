# YeJing_Update

野径 App 的更新分发仓库。

- `version.json`：最新版本清单（versionCode / 分片列表 / SHA256）
- `yejing-*.apk.000/.001`：APK 分片（GitHub 单文件 100MB 上限）
- 客户端在「我的 → 检查更新」或启动时静默检查，经 ghproxy 镜像下载分片、合并、SHA256 校验后唤起系统安装器
- 覆盖安装自动保留用户数据（SharedPreferences）与已下载的 Gemma 模型（documents/models/）

## 发布新版本
1. 修改 `yejing_flutter/pubspec.yaml` 的 `version:`（versionCode +1）
2. `flutter build apk --release`
3. 分片 APK（`split -b 90m`）、更新 `version.json` 的 versionCode/notes/sha256
4. 提交并推送到本仓库
