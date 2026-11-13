# 08 — 打包与安装闭环

- **状态**: ready-for-agent
- **Blocked by**: #07
- **交付效果**: 一条命令构建出可加载的扩展目录；按设置页指引装进 ego 后，全流程在真实登录页上跑通。

---

## 做什么

- `packages/extension/scripts/build.mjs`：把源码与 `subjx` 及其 CSS 打成一个可直接「加载已解压」的目录。
- `packages/extension/scripts/check.mjs`：断言产物里有 `manifest.json`、`subjx.js`、`subjx.css`，且 manifest 不含 `<all_urls>`。
- README 写清装法。

## 完成判据

- `node scripts/build.mjs && node scripts/check.mjs` 退出码 0。
- 装进 ego 后，在一个**需要登录**的真实页面上：点元素 → 改尺寸 → 拖动 → 写说明 → 送进 dsh 草稿，全程通。
- 刷新页面后草稿仍在，且没有被自动发送。
