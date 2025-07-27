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


```
# 二、详细配置
## (一)忽略不必要的文件夹
# 三、使用技巧
1. github网站卡顿问题  
    - 打开bing.com网站,搜索Watt Toolkit软件,在微软应用商店下载安装
    - 打开Watt Toolkit,在左侧导航栏选择"网络加速",在github前打勾
    - 在右上方点击"一键加速"