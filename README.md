# XN642 项目对话归档

用于团队共享、补充和修订“XN642-比赛”项目的讨论记录。对话按聊天分别保存为 UTF-8 Markdown，可直接在 GitHub 阅读和编辑。

仓库地址：<https://github.com/BankSuo77Code/xn642-conversations>

## 对话目录

本次快照时间：**2026-10-21 00:23:52（上海时间）**，共 4 个聊天、64 条用户及助手可见消息。

| 对话 | 消息数 | 内容 |
|---|---:|---|
| [01-比赛信息与选题讨论](01-比赛信息与选题讨论.md) | 36 | 比赛方向、资料整理及选题讨论 |
| [02-目标姿态与应用背景](02-目标姿态与应用背景.md) | 9 | 目标姿态研究的应用背景 |
| [03-三维场景仿真研究方向](03-三维场景仿真研究方向.md) | 12 | 基于海岛三维场景仿真软件的研究讨论 |
| [04-GitHub仓库与协作请求](04-GitHub仓库与协作请求.md) | 7 | 私有仓库、对话共享与协作需求 |

每份记录包含消息时间、发言角色和原文。第 4 份记录是仓库搭建过程中的快照，后续操作结果以 GitHub 仓库实际状态为准。

图片以附件占位保留，原聊天中的本地文件链接不随 Markdown 自动上传。具体范围见 [导出说明](docs/EXPORT_SCOPE.md)。

## 团队协作

仓库使用 **Public（公开）** 可见性，任何人都可以阅读和下载内容。具有写权限的协作者可以直接上传和修改仓库文件。

[@YoakeLee](https://github.com/YoakeLee) 已具有读写权限，可直接上传和修改内容。新增协作者由仓库所有者通过 GitHub 的 Collaborators 设置邀请。

具有写权限的协作者登录 GitHub 后，可点击 Markdown 文件的编辑按钮修改；新增文件使用 **Add file → Create new file**，上传文件使用 **Add file → Upload files**，最后点击 **Commit changes** 保存。

协作约定、分支操作及本地更新方法见 [CONTRIBUTING.md](CONTRIBUTING.md)。补充研究笔记可放入 [notes/](notes/README.md)。

## 更新对话

这是一次手工导出的快照；后续聊天不会自动同步。原电脑可以运行 [export-conversations.py](export-conversations.py) 重新导出这 4 个聊天，再检查并提交修改。脚本只读取本地 Codex 记录，不需要 GitHub 密码，也不会自行上传。

```powershell
python .\export-conversations.py --output .\snapshots\2026-10-22
```

默认拒绝覆盖已有导出。需要刷新原文件时可使用 `--overwrite`，但会替换这四份记录中的手工编辑；请先提交需要保留的修改。新增聊天需要在脚本的 `CHATS` 中明确登记其 ID。
