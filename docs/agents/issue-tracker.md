# Issue tracker

- **Kind**: GitHub Issues（远端**尚未创建**，等用户点头）
- **Repository (planned)**: `https://github.com/RoyougiShiki/dsh-ui-annotate`（private）
- **CLI**: `gh` at `E:\SoftWare\GitHubCLI\bin\gh.exe`（2.96.0，已登录）。`where gh` 失败只是因为 `run_code` 的 `process.env` 为空，不代表没装。
- **PRs as a request surface**: off

## 当前状态

票先写成 **local markdown**，落在 `.scratch/ui-annotate/issues/`，一票一文件、按依赖顺序编号。
远端仓库建好之后，把它们逐条发成 GitHub issue（blockers 先发），并把 `Blocked by` 写成 `Blocked by: #12` 这种文本引用——私有免费仓库没有原生 blocking link。

## 旧仓库

`https://github.com/RoyougiShiki/ui-annotate`（private，main@27bc686，1745 行）**不再使用，待删除**。
它用的是 `ego-browser` 往 TaskSpace 注入 `recorder.js` 那套架构（Windows 上有三处断点）；本仓库是扩展 + dsh 客户端插件，两者不共享代码，旧代码也没有参考价值——旧架构为什么不成立已由 `docs/adr/0001` 记录。
删除是不可逆操作（GitHub 只提供 90 天内恢复），等用户明确确认后执行 `gh repo delete`，届时删掉本节。

## Conventions

- 一票一个文件，文件名 `NN-slug.md`。
- `Blocked by` 写在标题下第一块元数据里；填「（无，可立即开始）」表示无阻塞。
- 关闭时把验证命令的输出贴进票里，不要只写「完成」。
- 标签：`needs-triage` / `needs-info` / `ready-for-agent` / `ready-for-human` / `wontfix`——按需创建（`triage` skill 未安装，标签词表未协商）。
