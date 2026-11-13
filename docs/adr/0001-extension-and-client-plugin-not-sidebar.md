# ADR-0001：用浏览器扩展 + dsh 客户端小插件，不用侧栏，也不自己 spawn 浏览器

- **Status**: accepted
- **Date**: 2026-11-13

## 背景

需求是「在**真实登录态**的网页上做标注，结果进 dsh 输入框」。本机是 Windows，dsh 跑在 ego lite 里（`http://127.0.0.1:3081`）。

已装过的三个方案都不成立：

- `dsh-annotated-browser` 用宿主无头 Chromium 渲染页面，README 明写「不会复用你自己浏览器的 cookie」⇒ 拿不到登录态。
- `dsh-sidepanel-web` 用侧栏同源 iframe 代理，cookie jar 是进程内 Map，同样继承不了登录态。
- `dsh-annotator` 自己 spawn 一个 Edge 窗口，登录态在它自己的 profile 里，用户得重新登录，而且页面不在 dsh 界面里。

用户另有一条硬约束：**侧栏不要放**（dsh 侧栏当时是空的），且**绝不能自己敲端口地址**（dsh-redline 因此被否）。

## 决定

做成**浏览器扩展 + dsh 客户端小插件**两件：

1. 扩展在**目标页**里跑标注器（`activeTab` 按需注入，用户点工具栏图标触发）。它是唯一能碰到用户真实登录态的手段。
2. 扩展把条目送进**宿主页**（`http://127.0.0.1:3081`，靠 manifest `matches` 常驻的 content script + `window.postMessage`）。
3. dsh 客户端小插件在宿主页里把条目写进草稿。第一期的填充走 `document.execCommand('insertText')`，不用 `InputActions`。

## 后果

- 不需要端口、token、配对码。
- 扩展无法静默安装（Chromium 限制），首次必须人工三步：开发者模式 → 加载已解压 → 选文件夹。dsh 插件设置页只负责把这条路指出来。
- 依赖扩展存在。扩展没装时，插件设置页是唯一能解释原因的地方。
