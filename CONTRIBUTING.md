# 协作说明

## 访问与写入权限

仓库现为公开，任何人都可以阅读和下载内容。直接上传和修改仓库文件需要协作者写权限；转发仓库链接只提供公开访问，不会自动授予写权限。

`YoakeLee` 已具有读写权限，可以直接提交文件和修改，也可以通过分支及 Pull Request 讨论较大改动。新增协作者需由仓库所有者发出邀请，受邀账号接受后获得相应写权限。

## 在 GitHub 网页编辑和上传

以下步骤适用于具有写权限的协作者。

1. 打开要修改的 `.md` 文件，点击编辑按钮。
2. 修改内容，使用 **Preview** 检查排版。
3. 点击 **Commit changes**，填写清楚的修改说明并提交。
4. 新建文件使用 **Add file → Create new file**，在文件名中写上 `.md` 后缀；上传已有文件使用 **Add file → Upload files**。

较大修改可以选择创建分支并提交 Pull Request，便于另一位同事先阅读后合并。

## 在本地协作

首次使用时克隆仓库：

```powershell
git clone https://github.com/BankSuo77Code/xn642-conversations.git
cd xn642-conversations
```

每次开始编辑前先拉取最新内容：

```powershell
git pull --ff-only
# 编辑或新增 Markdown 文件
git status
git add README.md
git commit -m "docs: 更新项目说明"
git push
```

`git add` 后填写本次实际修改的文件。遇到双方改了同一处的冲突时，先核对并合并双方内容，再提交；不要覆盖同事的修改。

## 内容约定

- 对话文件记录历史讨论。需要更正时，在相关段落旁补充日期和修订说明，让同事能识别后来的更正。
- 新研究结论、任务安排、资料和会议纪要可以新增到 `notes/`。
- 新笔记建议命名为 `YYYY-MM-DD-主题.md`，写明作者、日期、背景、结论和待办事项。
- 导出脚本的 `--overwrite` 会替换四份对话中的手工改动；重新导出前先提交，导出后检查 `git diff`。
- 当前脚本只更新已登记的四个聊天，新聊天需要明确补充到 `CHATS`。

## 导出与共享范围

导出来源、筛选规则、图片附件和本地文件缺失说明见 [docs/EXPORT_SCOPE.md](docs/EXPORT_SCOPE.md)。任何电脑都可以阅读和下载公开内容，具有写权限的协作者可以上传和编辑仓库；持有相应 Codex 原始记录的电脑才能重新导出这些聊天。
