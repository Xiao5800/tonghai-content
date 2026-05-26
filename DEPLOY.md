# TongHai 听力内容部署说明

生成时间: 2026-05-26T18:42:02.497613+08:00
来源: ELLLO (English Listening Lesson Library Online)
数据收集: https://elllo.org

## GitHub Pages 部署

```bash
cd D:\tonghai_flutter\scripts\output
git init
git checkout -b gh-pages
# 如果 audio/ 目录较大，考虑使用 Git LFS
git add .
git commit -m "TongHai listening content pack"
git remote add origin https://github.com/<你的用户名>/tonghai-content.git
git push -u origin gh-pages
```

部署后更新 `lib/config/api_config.dart`:
```dart
static const String listeningCatalogUrl =
    'https://<你的用户名>.github.io/tonghai-content/catalog.json';
```

## 本地测试

```bash
cd D:\tonghai_flutter\scripts\output
python -m http.server 8080
```

然后在 App 中设置:
```dart
static const String listeningCatalogUrl =
    'http://10.0.2.2:8080/catalog.json';  // Android 模拟器
    // 或 'http://localhost:8080/catalog.json';  // iOS 模拟器
```

## 更新内容

重新运行脚本后，重新推送 gh-pages 分支即可。
