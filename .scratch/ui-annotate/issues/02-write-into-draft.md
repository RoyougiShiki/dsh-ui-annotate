# 02 — 把条目写进 dsh 草稿

- **状态**: ready-for-agent
- **Blocked by**: #01
- **交付效果**: 标注一条 → 点「发送到 dsh」→ dsh 输入框出现这段 markdown，**没有自动发送**。

---

## 做什么

- 宿主页内容脚本：manifest `matches: ["http://127.0.0.1:3081/*"]`，常驻。
- 传输：背景脚本 → 宿主页内容脚本（`chrome.tabs.sendMessage` / `chrome.runtime.sendMessage`）。不用 HTTP、端口、token。
- 写入：`document.execCommand("insertText", false, markdown)`。
- 没有宿主页时给出可读提示（「先打开 dsh」），不静默失败。

## 完成判据

- 真实 dsh 页面里草稿出现文字，且**刷新后仍在**。
- 消息**没有被自动发送**。
- 没有 3081 标签页时扩展显示明确提示。

## 先例

注入与 postMessage 已验证（见 `docs/adr/0002`）；`execCommand("insertText")` 在 ISOLATED world 里已验证可用。
