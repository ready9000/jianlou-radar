# 捡漏雷达 APK 构建指南

## 方法一：使用 Docker 构建（推荐）

### 1. 安装 Docker
- macOS: https://docs.docker.com/desktop/install/mac-install/
- Windows: https://docs.docker.com/desktop/install/windows-install/

### 2. 构建 Docker 镜像
```bash
cd /Users/qinyonglu/WorkBuddy/20260314214958/cordova-app
docker build -t jianlou-builder .
```

### 3. 运行构建
```bash
docker run --rm -v $(pwd):/app jianlou-builder
```

### 4. 获取 APK
构建完成后，APK 文件位于：
```
platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

---

## 方法二：使用 Android Studio 构建

### 1. 安装 Android Studio
https://developer.android.com/studio

### 2. 打开项目
```bash
cd /Users/qinyonglu/WorkBuddy/20260314214958/cordova-app/platforms/android
```

### 3. 用 Android Studio 打开 android 文件夹

### 4. 点击 Build → Build Bundle(s) / APK(s) → Build APK(s)

---

## 方法三：使用 GitHub Actions 自动构建

项目已配置 `.github/workflows/build.yml`，推送代码到 GitHub 后会自动构建 APK。

---

## APK 安装

构建完成后，将 APK 传输到手机：

### Android 手机安装步骤：
1. 开启「允许安装未知来源应用」
   - 设置 → 安全 → 未知来源 → 允许
2. 传输 APK 到手机
3. 点击安装

---

## 项目结构

```
cordova-app/
├── www/
│   ├── index.html      # 主应用页面
│   ├── manifest.json   # PWA配置
│   └── sw.js          # Service Worker
├── config.xml         # Cordova配置
├── Dockerfile         # Docker构建配置
└── BUILD_GUIDE.md     # 本指南
```

## 应用功能

- ✅ 二手商品低价监控
- ✅ 规格参数精准匹配（同配置比价）
- ✅ 商家识别与过滤
- ✅ 价格趋势分析
- ✅ 一键跳转购买（咸鱼/转转）

## 注意事项

1. 首次构建需要下载依赖，时间较长
2. 调试版 APK 可以直接安装
3. 发布版需要配置签名证书
