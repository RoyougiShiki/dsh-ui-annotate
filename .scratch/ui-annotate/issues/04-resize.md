# 04 — 改尺寸：subjx 手柄 + 实时预览 + 旧新值

- **状态**: ready-for-agent
- **Blocked by**: #03
- **交付效果**: 点元素后拖 8 个手柄 → 元素实时变大变小 → 松手后恢复原样 → 条目里记着 旧 W×H → 新 W×H。

---

## 做什么

- 引入 `subjx@2.0.1`；注入它的 `dist/style/subjx.css`（**必须**，否则手柄 0×0 点不到）。
- `subjx(el).drag({ resizable: true, rotatable: false })`，监听 `resize` 改 `style.width/height`。
- `resizeEnd`：读 `getDimensions()` 与进入前 rect 比较，生成 old→new，然后还原 `style`。
- 尺寸同时记「目标容器宽度的百分比」与「最接近的邻居元素宽度」。

## 完成判据

- 真机：抓右下角手柄拖，元素实时变大，`getDimensions()` 的 width/height 变化被记录。
- 松手后 `style.width` / `style.height` 为空（已还原）。
- 条目 markdown 出现 `200×120 → 272×174` 这类文字。
