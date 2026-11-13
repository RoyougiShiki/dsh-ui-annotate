# 05 — 移动 + 旋转

- **状态**: ready-for-agent
- **Blocked by**: #04
- **交付效果**: 拖动元素本体改变位置、拖旋转手柄改变角度，两者都记成 旧→新。

---

## 做什么

- `subjx(el).drag({ resizable: true, rotatable: true })`。
- `dragEnd`：读位移与落点。落点用「元素中心落在哪个兄弟元素的前半/后半」判断，输出「放到 <邻居选择器> 之前/之后」。
- `rotateEnd`：读 `getDimensions().rotation`，输出 `0° → 30°`。
- 两者都还原 `transform`。

## 完成判据

- 真机：拖本体，位移被记录；`getDimensions()` 的 x/y 变化符合拖动量。
- 真机：旋转后 `rotation` 落进条目。
- 松手后 `style.transform` 已还原。
