
---


🧠 一、 核心知识点总结

1. Git vs GitHub
   · Git：是一个本地的版本控制软件（运行在你电脑上的黑框框），负责记录代码的每一次修改。
   · GitHub：是一个基于 Web 的远程代码托管平台（网页），用来存放你的代码备份。
2. Git 的四个核心区域
   · 工作区 (Workspace)：你电脑上能看到的文件夹，平时写代码的地方。
   · 暂存区 (Stage)：git add 后，代码被暂时存放的地方，准备提交。
   · 本地仓库 (Local Repository)：git commit 后，代码被正式记录在本地的版本库中。
   · 远程仓库 (Remote)：git push 后，代码被上传到 GitHub 云端。
3. 关于 add . 和 add *.cpp
   · git add .（加一个英文句号）：把当前文件夹下所有新修改或新添加的文件全部加入暂存区。Git 不认后缀名，只认文件内容的变化。
   · git add *.cpp：只把后缀为 .cpp 的文件加入暂存区。

---

💣 二、 踩坑记录（避坑指南）

1. 环境混淆坑：WSL vs Windows 原生
   · 现象：在开始菜单搜 Git Bash 搜不到，点进去是网页；或者在 WSL (Ubuntu) 里敲命令报错。
   · 解决：理清自己是在哪个终端操作。Windows 环境下，需要明确安装并打开 Git Bash，不要和虚拟机（WSL）搞混。
2. 安装配置坑：选了不存在的编辑器
   · 现象：Git 安装界面提示 Next 按钮是灰色的，点不了。
   · 原因：在下拉菜单选中了 Visual Studio Code Insiders（测试版），但电脑上没装这个。
   · 解决：下拉菜单选择 Use Visual Studio Code as Git's default editor 或最稳妥的 Notepad（记事本）。
3. 网络连接坑（最大坑）：443 超时
   · 现象：浏览器能打开 GitHub，但终端执行 git push 时报 Failed to connect to github.com port 443 after 21000 ms（连接超时）。
   · 原因：终端（Git Bash）默认直连，不会自动走你电脑上的代理软件（VPN/加速器）。国内直连 GitHub 极不稳定。
   · 解决：找到代理软件的本地端口（如 7890, 7892），手动让 Git 挂上代理。
4. 分支命名坑：master vs main
   · 现象：推送时提示分支不存在。
   · 原因：GitHub 现在默认主分支叫 main，而老版本 Git 默认叫 master。
   · 解决：安装时把默认分支设为 main；如果报错，尝试 git push origin master。

---

💻 三、 常用代码片段 (Cheat Sheet)

1. 初次安装后的身份配置（全局，只需一次）

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的注册邮箱"
```

2. 日常开发四步曲（核心工作流）

```bash
# 1. 从 GitHub 克隆（下载）仓库到本地
git clone https://github.com/用户名/仓库名.git

# 2. 进入该仓库文件夹
cd 仓库名

# 3. 将修改或新建的文件添加到暂存区
git add . 

# 4. 提交到本地仓库，并写下备注说明
git commit -m "你的提交说明（如：完成第一次作业）"

# 5. 推送到远程 GitHub 仓库
git push origin main
```

3. 网络代理配置（针对终端连不上 GitHub）

```bash
# 配置代理（端口号需根据你的代理软件实际情况修改，如 7890/7892）
git config --global http.proxy http://127.0.0.1:7892
git config --global https.proxy http://127.0.0.1:7892

# 测试成功后重新推送
git push origin main
```

4. 查询与撤销（如果忘了自己改了什么）

```bash
# 查看当前文件状态（红色代表未添加，绿色代表已添加待提交）
git status

# 取消 Git 的代理配置（如果关了代理软件导致连不上，可以执行此命令）
git config --global --unset http.proxy
git config --global --unset https.proxy
```