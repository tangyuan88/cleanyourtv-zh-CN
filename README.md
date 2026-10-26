# Clean Your TV — 简体中文汉化版（zh-CN）

[Clean Your TV](https://github.com/udhaykumarbala/cleanyourtv-app) 的简体中文本地化项目：一键清理 Android TV / Google TV 上预装的应用、广告与跟踪。

本项目包含两部分：

1. **中文版 APK**（`Clean-Your-TV-中文版-v0.3.4.apk`）——基于官方 v0.3.4 重打包，界面全中文，可直接安装。
2. **源码级本地化补丁**（`localization/`）——为原项目 9 个模块添加 `values-zh-rCN` 中文字符串资源，可合并到源码自行构建或向原仓库提交 PR。

## 汉化范围

- **866 条**中文字符串，覆盖原项目 main 分支全部 UI 文本（APK v0.3.4 内 668/668 条全量翻译）。
- 9 个模块：`app`、`feature/backup`、`feature/connect`、`feature/launcher`、`feature/manage`、`feature/modules`、`feature/setup`、`tv/curtain`、`ui/design`。
- 简体中文、口语化平稳风格；ICU MessageFormat（`{name}`、`{count, plural, ...}`）与 printf（`%1$d`）占位符逐字保留。
- 品牌名与命令保持英文原文：`Clean Your TV`、`Fire TV`、`Chromecast`、`Android TV`、`Google TV`、`adb` 命令等。
- 机型差异提示完整翻译：TCL 遥控器按键、小米盒子 USB 端口、Fire TV 广告等。

## 使用中文版 APK

1. **先卸载已安装的官方版**（签名密钥不同，无法覆盖安装），再安装本 APK。
2. 包名 `tv.cleanyour.app` 与原版一致，版本 v0.3.4（versionCode 7）。
3. 本 APK 使用调试密钥签名，仅用于个人使用；正式分发请从源码构建并自行签名。

## 从源码构建

将 `localization/cleanyourtv-app-main/` 下的 `values-zh-rCN` 目录合并到对应模块的 `src/main/res/` 下：

```bash
# 以 feature/setup 为例
cp -r localization/cleanyourtv-app-main/feature/setup/src/main/res/values-zh-rCN \
      feature/setup/src/main/res/
./gradlew assembleDebug
```

也可以直接向原项目 [cleanyourtv-app](https://github.com/udhaykumarbala/cleanyourtv-app) 提交 PR。

## 翻译约定

- 操作按钮统一：返回 / 取消 / 确定 / 撤销 / 完成 / 下一步。
- 英文复数 `one/other` 折叠为 `other`（中文无单复数区分），保留 `=0` 特殊分支。
- `tv/curtain`（电视端配套应用）使用 printf 风格占位符，已按其格式处理。

## 致谢与许可

- 原项目：[udhaykumarbala/cleanyourtv-app](https://github.com/udhaykumarbala/cleanyourtv-app)（MIT License）
- 本仓库翻译内容按 [MIT License](LICENSE) 许可发布，版权归属原项目贡献者。
