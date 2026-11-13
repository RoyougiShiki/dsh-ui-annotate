# dsh-ui-annotate

在真实登录态的网页上做标注（点元素 / 改尺寸 / 移动 / 旋转），结果写进 dsh 输入框。

## 导航

- 术语表：[`GLOSSARY.md`](GLOSSARY.md)
- 裁决记录：[`docs/adr/`](docs/adr/)
- issue tracker 与协作约定：[`docs/agents/issue-tracker.md`](docs/agents/issue-tracker.md)
- 领域文档消费规则：[`docs/agents/domain.md`](docs/agents/domain.md)

## 组成

- `packages/extension/` —— ego/Edge/Chrome 通用 MV3 扩展：标注器在**目标页**，桥在**宿主页**。
- `packages/dsh-plugin/` —— dsh 客户端小插件：设置页安装引导 + 宿主页侧的草稿写入。
