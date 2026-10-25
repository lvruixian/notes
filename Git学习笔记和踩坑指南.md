

---


🎯 任务目标

学习 Git 命令行基本操作，在 GitHub 新建仓库，完成 clone、add、commit、push 的完整流程至少一次，并截图显示提交记录。

---

🛠️ 完整操作流程（基于 Windows）

1. 安装与环境准备

· 下载：前往 Git 官网下载安装包（如果慢可以使用国内镜像）。
· 安装关键点：在 Adjusting your PATH environment 界面，务必选择默认的中间项 Git from the command line and also from 3rd-party software，确保系统能全局识别 git 命令。
· 默认编辑器：推荐选择 VS Code（不要选带有 Insiders 的测试版），或者最稳妥的选 Notepad（记事本）。
· 默认分支名：推荐选择 Override the default branch name 并保持为 main，以与 GitHub 当前默认的主分支名称保持一致。
· 打开终端：在开始菜单搜索并打开 Git Bash，或者在文件夹空白处右键选择 Open Git Bash here。

2. 配置 Git 身份（首次使用）

打开 Git Bash 终端，输入以下命令关联你的 GitHub 账号：

```bash
git config --global user.name "你的GitHub用户名"
git config --global user.email "你的GitHub注册邮箱"
```

3. 在 GitHub 上新建仓库

4. 登录 GitHub，点击右上角 + 号 -> New repository。
5. 填写仓库名（如 git-test），点击 Create repository。
6. 复制仓库的 HTTPS 链接（格式为 https://github.com/用户名/仓库名.git）。

7. 核心操作流程（Clone -> Add -> Commit -> Push）

在 Git Bash 中依次执行以下命令：

```bash
# 1. Clone (克隆远程仓库到本地)
git clone https://github.com/lvruixian/git-test.git

# 2. 进入本地仓库文件夹
cd git-test

# 3. 创建一个测试文件
echo "Hello Git" > test.txt

# 4. Add (将文件添加到暂存区)
git add .

# 5. Commit (将暂存区内容提交到本地仓库)
git commit -m "完成第一次提交作业"

# 6. Push (将本地提交推送到 GitHub 远程仓库)
git push origin main
```

5. 截图交作业

在浏览器中刷新 GitHub 仓库页面，点击 Commits 或文件上方的提交记录，截图包含提交信息的页面。

---

💣 踩坑点记录与解决方案

在操作过程中遇到了不少报错和卡点，以下是避坑指南：

坑 1：终端无法识别 git 命令

· 现象：在 PowerShell 或 CMD 中输入 git，提示 无法将“git”项识别为 cmdlet...。
· 原因：电脑未安装 Git，或者安装时未勾选配置环境变量的选项。
· 解决：重新下载安装 Git，并确保 PATH 环境变量选项选的是默认推荐项；或者重启终端让环境变量生效。

坑 2：命令语法输错（短横线数量）

· 现象：输入 git -version 报错。
· 解决：Git 的长参数需要两个短横线。正确的命令是 git --version。

坑 3：Clone 链接重复粘贴

· 现象：复制粘贴时，不小心把链接复制了两遍，导致 clone 失败。
· 解决：执行命令前检查代码：git clone https://... 后面只能跟一个完整的 URL 地址。

坑 4：WSL 环境下的代理/网络问题

· 现象：在 WSL (Ubuntu) 下使用 Git 提示 NAT 模式不支持 localhost 代理，clone 可能失败。
· 解决：对于新手，强烈建议直接在 Windows 原生的 Git Bash 中操作，避免跨系统网络代理的繁琐配置。如果非要用 WSL，需要手动配置宿主机的 IP 和代理端口。

坑 5：Git Bash 的粘贴快捷键

· 现象：习惯性使用 Ctrl + V 无法粘贴。
· 解决：在 Git Bash 窗口内，点击鼠标右键，选择 Paste 即可粘贴。

坑 6：安装 Git 时“下一步(Next)”按钮变灰

· 现象：在选择默认编辑器时，选了“Visual Studio Code Insiders”，但电脑上没装这个版本，导致 Next 按钮灰色无法点击。
· 解决：退回上一步或更改选项，选择普通的 VS Code 或 Notepad 即可。

坑 7：首次 push 弹出登录授权窗口

· 现象：第一次输入 git push 后，弹出一个黑框要求 Sign in。
· 解决：这是 GitHub 的正常身份验证。点击 Sign in with your browser，在弹出的网页中登录 GitHub 账号并点击 Authorize（授权），授权成功后回到终端等待 push 完成即可。

坑 8：关于换行符的警告

· 现象：执行 git add 时提示 warning: LF will be replaced by CRLF...
· 解决：Windows 和 Linux 的换行符不同，这是 Git 的自动转换机制，属于正常警告，直接忽略即可，不影响提交。