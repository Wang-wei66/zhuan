# 备考应用 · GitHub Pages 静态托管

本目录（`beikao/`）是两个备考 App 的**永久在线版本**，由 GitHub Pages 直接托管静态文件，
不依赖任何临时运行环境或后端进程，链接固定有效。

## 入口

| App | 相对路径 | 说明 |
| --- | --- | --- |
| 选择页 | `beikao/` | 两个 App 的统一入口 |
| 安考通 | `beikao/za/` | 2027 广东省中级注册安全工程师（其他安全），4 科 / 35 章 / 404 知识点 / 1231 题 |
| 素学 | `beikao/sx/` | 公共营养师（四级 / 三级）纯净素专题，6 科 / 32 章 / 267 知识点 / 827 题 |

完整 URL 形如 `https://<用户名>.github.io/<仓库名>/beikao/za/`。

## 与「在线同步版」的区别

| | 本静态版 | 在线同步版 |
| --- | --- | --- |
| 托管 | GitHub Pages 纯静态 | 临时 Node 服务 |
| 链接稳定性 | 固定、长期有效 | 依赖运行环境，重建后需恢复 |
| 跨设备同步 | 不支持（无后端） | 支持，按同步码自动合并 |
| 学习数据 | 当前浏览器 localStorage | 本机 + 云端双写 |
| 离线使用 | 打开后可用 | 打开后可用 |

静态版会自动降级为「本机模式」，不会报错，同步面板也不再显示云端状态。
换设备前请在 App 内**导出 JSON 备份**，到新设备导入即可迁移全部记录。

## 文件说明

```
beikao/
├── index.html              选择页（内联 CSS / SVG，无外部依赖）
├── .nojekyll               跳过 Jekyll 构建
├── za/
│   ├── index.html          安考通单文件自包含版
│   ├── manifest.json       PWA 配置（standalone）
│   ├── apple-touch-icon.png
│   ├── icon-192.png
│   └── icon-512.png
└── sx/
    └── （同 za/）
```

两个 `index.html` 均为**单文件自包含**：CSS、JS、知识库、题库、favicon 全部内联，
无任何外部脚本或样式依赖。仅 iOS 图标与 manifest 为同目录相对文件。

## iPhone 添加到主屏幕

用 Safari 打开对应 App 页面 → 底部分享按钮 → 添加到主屏幕 → 确认名称 → 添加。
之后桌面出现独立图标，点击全屏运行（`apple-mobile-web-app-capable` + 安全区适配已配置）。

## 内容说明

- 题库均为按考点编写的仿真题，**暂未收录官方历年真题**，导入通道要求
  `real:true / paper / year / source:"官方真题"` 才会标记为真题套卷。
- 考务政策、报考条件、膳食指南版本与推荐摄入量会更新，以当年官方公告与最新版指南为准。
- 两个 App 使用不同的 localStorage 键（`za_app_v1` / `suxue_app_v1`），数据互不干扰。

## 更新方式

重新生成两个单文件版后，覆盖 `za/index.html` 与 `sx/index.html`，提交推送即可，
GitHub Pages 会自动重新构建。
