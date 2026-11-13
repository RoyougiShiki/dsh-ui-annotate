# Issue tracker

- **Kind**: GitHub Issues（远端**尚未创建**，等用户点头）
- **Repository (planned)**: `https://github.com/RoyougiShiki/dsh-ui-annotate`（private）
- **CLI**: `gh` at `E:\SoftWare\GitHubCLI\bin\gh.exe`（2.96.0，已登录）。`where gh` 失败只是因为 `run_code` 的 `process.env` 为空，不代表没装。
- **PRs as a request surface**: off

## 当前状态

票先写成 **local markdown**，落在 `.scratch/ui-annotate/issues/`，一票一文件、按依赖顺序编号。
远端仓库建好之后，把它们逐条发成 GitHub issue（blockers 先发），并把 `Blocked by` 写成 `Blocked by: #12` 这种文本引用——私有免费仓库没有原生 blocking link。

## Conventions

- 一票一个文件，文件名 `NN-slug.md`。
- `Blocked by` 写在标题下第一块元数据里；填「（无，可立即开始）」表示无阻塞。
- 关闭时把验证命令的输出贴进票里，不要只写「完成」。
- 标签：`needs-triage` / `needs-info` / `ready-for-agent` / `ready-for-human` / `wontfix`——按需创建（`triage` skill 未安装，标签词表未协商）。
