# 01 — 在目标页注入标注器并拿到元素信息

- **状态**: ready-for-agent
- **Blocked by**: （无，可立即开始）
- **交付效果**: 点扩展图标 → 当前页浮出标注条 → 点任意元素 → 拿到该元素的选择器与可见文本。

---

## 做什么

- MV3 manifest：`activeTab` + `scripting`；`host_permissions` 只含 `http://127.0.0.1:3081/*`。
- 工具栏图标点击 → `chrome.scripting.executeScript` 往当前标签页注入目标页内容脚本与 CSS。
- 标注条：一条浮条（自己的 shadow DOM 或高 z-index overlay），含「标注 / 退出」。
- 点元素：`document.elementFromPoint` 命中后高亮；生成选择器（`#id` → `data-testid` → 回溯 CSS 路径）与可见文本。

## 完成判据

- 在本地 stub 页上点元素，能打印出选择器与可见文本。
- 不点图标时，除 `127.0.0.1:3081` 外任何页面都不运行脚本（`chrome://extensions` 里权限只有 activeTab）。
