# 07 — dsh 插件：设置页安装引导 + 中英文案

- **状态**: ready-for-agent
- **Blocked by**: #06
- **交付效果**: dsh 设置页出现「UI 标注」一节，写着装扩展的三步，能一键复制扩展目录路径；界面跟随 dsh 语言。

---

## 做什么

- 客户端模块：`window.__ModuleLoader__.load({ id, factory })`，`exports.apply` / `exports.inject`。
- 注册 `ctx.slots.inject('settings.section', () => ctx.slots.register({ name: 'settings.section', id: 'dsh-ui-annotate', order: 120, label }, Section))`。
- 内容：三步说明（开发者模式 → 加载已解压 → 选文件夹）+ 扩展目录绝对路径 + 一键复制 + 「打开 ego 扩展页」。
- **不做斜杠命令**（用户明确不需要）。
- 文案中英双语，跟随 dsh 语言设置。

## 完成判据

- dsh 设置页里能看到这一节。
- 复制按钮真的把路径写进剪贴板。
- 切语言后文案跟着变。
