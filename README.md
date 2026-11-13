# dsh-ui-annotate

在真实登录态的网页上标注：点元素、调尺寸、移动、旋转，然后写一句「要改成什么」。结果写进 DeepSeek Harness 的输入框，不直接发送。

- 浏览器扩展负责看页面、做手势、产出结构化 markdown。
- dsh 客户端小插件负责把 markdown 写进草稿，并在设置页里教你装扩展。

细节见 [`AGENTS.md`](AGENTS.md)、[`GLOSSARY.md`](GLOSSARY.md)、[`docs/adr/`](docs/adr/)。
