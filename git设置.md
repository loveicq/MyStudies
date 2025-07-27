# 一、基础配置
*打开CMD窗口,输入下面两个命令,设置名称和邮箱*
```c++
//设置用户名
git config --global user.name "Your Name"
//设置邮箱
git config --global user.email "your_email@example.com"
//查询设置情况
git config -- global --list
//重新初始化 Git 仓库
git init
//关联新仓库 URL.注意:origin是仓库别名,最好改为gitee或github,方便区分
git remote add origin <你的新仓库URL>
//首次提交 & 推送
git add .
git commit -m "初始化新仓库"
git push -u origin main  # 如果默认分支是 master 则替换为 master
/*这三条命令是 Git 初始化仓库并推送到远程的基础流程，解析如下：
git add .
将当前目录下所有新增、修改的文件添加到 Git 暂存区（跟踪状态），准备提交。.表示当前目录及所有子目录。
git commit -m "初始化新仓库"
将暂存区的文件提交到本地仓库，-m后是提交说明（必填），这里描述为 “初始化新仓库”，用于记录本次提交的目的。
git push -u origin main
将本地main分支的提交推送到远程仓库origin，-u表示同时将本地main分支与远程origin/main分支关联（设置上游），后续可直接用git push推送。若远程默认分支是master，则替换为git push -u origin master。

如果需要同时推送到两个仓库（例如 GitHub + Gitee）：
bash
# 添加第二个远程仓库
git remote add gitee https://gitee.com/yourname/repo.git

# 同时推送到两个仓库
git push origin main
git push gitee main

# 或设置推送URL（一次push到两个仓库）
git remote set-url --add --push origin https://github.com/your/repo.git
git remote set-url --add --push origin https://gitee.com/your/repo.git

❤删除项目本地.git文件夹后(远程仓库已有文件),再重新初始化出现的问题解决:
根据你的描述和错误信息分析，问题在于远程仓库存在本地没有的初始提交（通常是创建仓库时自动生成的 README 或 .gitignore 文件）。以下是详细解释和解决方案：

错误原因
你首次推送时出现 ! [rejected] 错误，因为：

远程仓库非空：你在 Gitee/GitHub 网页端创建仓库时，勾选了"初始化仓库"选项（如添加 README 或 LICENSE 文件）。

本地与远程历史不同步：远程仓库已有初始提交（commit），

解决方案
方法 1：拉取远程变更并合并（推荐）
bash
# 1. 拉取远程内容（允许不相关历史合并）
git pull gitee main --allow-unrelated-histories

# 2. 解决可能出现的文件冲突（如有）
# 3. 重新推送
git push gitee main
原理：将远程初始提交与本地提交合并成一个新提交。

适用场景：需要保留远程初始文件（如 README）。

方法 2：强制覆盖远程（谨慎使用）
bash
git push -f gitee main
原理：用本地提交强制覆盖远程仓库（删除远程初始提交）。

风险：如果远程已有重要文件会被覆盖！

适用场景：远程初始化文件不需要保留。

完整操作流程（以 Gitee 为例）
bash
# 拉取远程内容（允许历史合并）
git pull gitee main --allow-unrelated-histories

# 此时会弹出合并提交的编辑器界面，保存退出即可
# 如果有冲突，手动解决后执行：
git add .
git commit -m "合并远程初始提交"

# 推送到远程
git push gitee main
预防措施
创建空远程仓库：

下次在 Gitee/GitHub 创建仓库时，取消勾选所有初始化选项（如 README、.gitignore、LICENSE）。

创建后直接按提示推送本地仓库：

bash
git remote add origin <url>
git push -u origin main
检查远程状态：

bash
# 查看远程分支详情
git ls-remote gitee
⚠️ 注意：对 GitHub 仓库重复相同操作（先 pull --allow-unrelated-histories 再 push）。

执行后你的本地提交和远程初始提交将合并，之后可正常双向同步。
*/
```
# 二、详细配置
## (一)忽略不必要的文件夹
# 三、使用技巧
1. github网站卡顿问题  
    - 打开bing.com网站,搜索Watt Toolkit软件,在微软应用商店下载安装
    - 打开Watt Toolkit,在左侧导航栏选择"网络加速",在github前打勾
    - 在右上方点击"一键加速"