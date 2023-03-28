# 版本控制系统的分类
1.本地版本控制系统：单机运行，使维护文件版本的操作工具化
2.集中化的版本控制系统：联网运行，支持多人协作开发
3.分布式版本控制系统：联网运行，支持多人协作开发，性能优秀，用户体验好

# Git快速和高效
1.直接记录快照，而非差异比较
2.近乎所有操作都是本地执行

# Git三个区域
工作区
暂存区
Git仓库

# Git三种状态
已修改 modified
表示修改了文件，但还没将修改结果放到暂存区
已暂存 staged
表示对已修改文件的当前版本做了标记，使之包含在下次提交的列表中
已提交 committed
表示文件已经安全的保存在本地的Git仓库中
注意：
工作区的文件被修改了，但是还没有放到暂存区，就是已修改状态
如果文件已修改并放入了暂存区，就属于已暂存状态
如果git仓库保   存着特定版本的文件，就属于已提交状态

# 配置用户信息
git config --global user.name "yinsong1205"
git config --global user.email "yinsong1205@163.com"
全局配置文件信息
C:\Users\YS\.gitconfig
除了用记事本查看全局配置外，还可以运行终端命令，快速查看Git的全局配置信息
查看所有的全局配置项
git config --list --global
查看指定的全局配置项
git config user.name
git config user.email
获取帮助信息
git help <verb>命令
要想打开git congfig命令的帮助手册
git help config
通过git config -h命令获取更简明的“help”输出
git config -h

# 获取Git仓库的两种方式
1.将尚未进行版本控制的本地目录转换为Git仓库
2.从其他服务器克隆一个已存在的Git仓库

# 在现有目录中初始化仓库
如果自己有一个尚未进行版本控制的项目目录，想要用Git来控制它，需要执行两个步骤
1.在项目目录中，通过鼠标右键打开“Git Bash”
2.执行git init命令讲当前的目录转化为Git仓库
git init命令会创建一个名为.git的隐藏目录，这个.git目录就是当前项目的Git仓库，里面包含了初始的必要文件，这些文件是Git仓库的必要组成部分

# 工作区中文件的4种状态
未被Git管理
未跟踪 Untracked
已被Git管理
未修改 Unmodified
已修改 Modified
已暂存 Staged
Git操作的终极结果，让工作区的文件都处于“未修改”的状态

# 检查文件状态
可以使用git status命令查看文件处于什么状态
精简方式,-s是--short简写形式
git status -s
git status --short

# 跟踪新文件
使用git add开始跟踪一个文件，要跟踪index.html.使用下面的命令
git add index.html
新添加到暂存区的文件前面有绿色的A标记

# 提交更新
现在暂存区中有一个index.html文件被提交到Git仓库中进行保存，可以执行git commit命令进行提交，其中，-m选项后面是本次提交消息，用来对提交内容做进一步的描述
git commit -m "新建了index.html文件"

# 撤销对文件的修改
撤销对文件的修改，指的是：把对工作区对应文件的修改，还原成Git仓库所保存的版本
操作的结果：所有的修改会丢失，且无法恢复，危险性较高，请谨慎操作
git checkout --index.html

# 向暂存中一次性添加多个文件
添加多个文件，一次性讲所有的新增和修改
git add .

# 取消暂存的文件
如果需要从暂存区中移除对应的文件，使用下面命令
git reset HEAD 要移除的文件名称
从暂存区中移除所有的文件
git reset HEAD .

# 跳过使用暂存区域
git commit -a -m "描述消息"
-a表示跳过暂存区域

# 移除文件
从Git仓库中移除文件有两种
1.从Git仓库和工作区中同时移除对应的文件
git rm -f index.html
2.只从Git仓库中移除指定的文件，但保留工作区中对应的文件
git rm --cached -f index.html

# 忽略文件
创建一个.gitignore的配置文件，列出要忽略的文件的匹配格式
文件.gitignore文件格式如下
1.以#开头的是注释
2.以/结尾的是目录
3.以/开头防止递归
4.以!开头表示取反
5.可以使用glob模式进行文件和文件夹的匹配(glob指简化了的正则表达式)

# glob模式
glob指简化了的正则表达式
1.星号*匹配零个或多个任意字符
2.[abc]匹配任何一个列在方括号中的字符(此案例匹配一个a或一个b或一个c)
3.问号?只匹配一个任意字符
4.在方括号使用短划线分隔两个字符，表示所有在这两个字符范围内的都可以匹配(例如，[0-9]表示匹配所有0到9的数字)
5.两个星号**表示匹配任意中间目录(比如a/**/Z 可以匹配a/z,a/b/z或a/b/c/z等)

# .gitignore文件的例子
1.忽略所有的 .a文件
*.a
2.跟踪所有的lib.a. 即使你在前面忽略了 .a文件
!lib.a
3.z之忽略当前目录下的TODO文件，而不忽略subdie/TODU
/TODU
4.忽略任何目录下名为build的文件夹
build/
5.忽略doc/notes.txt 但不忽略doc/server/arch.txt
doc/*.txt
6.忽略doc/目录及其所有子目录下的.pdf文件
doc/**/*.pdf

# 查看提交历史
q键退出查看
1.按时间先后顺序列出所有的提交历史，最近的提交安排在最上面
git log
2.只展示最新的两条历史，数字可以按需进行填写
git log -2
3.在一行显示最近两条提交历史的信息
git log -2 --pretty=oneline
4.在一行上展示最近两条提交历史的信息，并自定义输出的格式
%h提交的简写哈希值  %an作者名字  %ar作者修订日期，按多久以前的方式显示  %s提交说明
git log -2 --pretty=format:"%h | %an | %ar |%s"

# 回退到指定的版本
1.在一行展示所有的提交历史
git log --pretty=oneline
2.使用 git reset --hard 命令，根据指定的提交ID回退到指定版本
git reset --hard CommitID
3.在旧版本中使用 git reflog --pretty=online 命令，真看命令操作的历史
git reflog --pretty=online
4.再次根据最新的提交ID，跳转到最新的版本
git reset --hard CommitID

# 开源相关概念
1.什么是开源，闭源
开源即开放源代码，代码是公开git branch -M main的，任何人都可以查看，修改和使用开源代码
闭源软件的代码是封闭的，只有作者能看到闭源软件的代码，只有作者能对源代码进行修改

通俗解释
开源不仅提供程序还提供程序的源代码
闭源只提供程序，不提供源代码

# 开源许可协议
开源并不意味着完全没有限制，为了限制使用者的使用范围和保护作者的权利，每个开源项目都应该遵守开源许可协议

# 五种开源许可协议
1.BSD
2.Apache Licence 2.0
3.GPL 具有传染性的一种开源协议，不允许修改后和衍生的代码作为闭源的商业软件发布和销售
使用GPL最著名的软件项目是，Linux
4.LGPL
5.MIT 是目前限制最少的协议，wqqqqqqqq唯一的条件，在修改后的代码或发行包中，必须包含原作者的许可信息，
使用MIT的软件项目jquery，Node.js

# 拥抱开源
开源的核心思想是：我为人人，人人为我，喜欢开源的原因：
1.开源给使用这更多控制权
2.开源让学习变得容易
3.开源才有真正的安全

# 开源项目托管平台
1.Github
2.Gitlab
3.Gitee

# 注册github账号的流程
1.访问 Github 的官网首页 https://github.com/
2.点击“sign up”按钮跳转到注册页面
3.填写可用的用户名、邮箱、密码
4.通过点击箭头的形式，将验证图片摆正
5.点击“Create account”按钮注册新用户
6.登录到第三步填写的邮箱中，点击激活链接，完成注册

# 激活github账号
登录邮箱激活

# 远程仓库的两种访问方式
Github上的远程仓库，有两种访问形式，分别是HTTPS和SSH，他们的区别是：
1.HTTPS：零配置，但是每次访问仓库时，需要重复输入Github的账号和密码才能访问成功
2.SSH：需要进行额外的配置，但是配置成功后，每次访问仓库时，不需重复输入Git的账号和密码

在实际开发中，推荐使用SSH的方式访问远程仓库

# 本地没有git仓库
1.使用终端命令创建README.md文档 并写入初始内容为# project 02
echo "# project 02" >> README.md
2.初始化本地git仓库，并将文件的修改提交到本地的Git仓库中
git init
git add README.md
git commit -m "first commit"
git branch -M main
3.将本地仓库和远程仓库进行关联，并把远程仓库命名为origin
git remote add origin 线上项目地址
例如：
git remote add origin https://github.com/yinsong1205/MyStudy.git
git push -u origin main
4.将本地仓库中的内容推送到远程的origin仓库中
git push -u origin main

# 本地有git仓库
1.将本地仓库和远程仓库进行关联，并把远程仓库命名为origin
git remote add origin 线上项目地址
例如：
git remote add origin https://github.com/yinsong1205/MyStudy.git
git branch -M main
2.将本地仓库中的内容推送到远程的origin仓库中
git push -u origin main

# 修改文件后提交
只有第一次用git push -u origin main
后面都用git push

# SSH KEY
作用：实现本地仓库和github之间的免登录的加密传输
好处：免登录身份认证，数据加密传输
由两部分组成：
1.id_rsa(私钥文件，存放于客户端的电脑中即可)
2.id_rsa.pub(公钥文件，需要配置到github中)

# 生成SSH key
1.打开Git Bash
2.粘贴如下命令，并将your_email@example.com替换为注册Github账号是填写的邮箱：
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
3.连续敲击三次回车，即可在C:\Users\用户名文件夹\.ssh目录中生成id_rsa和id_rsa.pub两个文件

# 配置SSH key
1.使用记事本打开id_rsa.pub文件，复制里面的内容
2.在浏览器登陆Github,点击头像->Settings->SSH and GPG keys->New SSH key
3.将id_rsa.pub文件的内容，粘贴到key对应的文本框中
4.在Title文本框中填写，以标识key的来源

# 检测Github的SSH key是否配置成功
打开Git Bash,输入下面的命令并回车执行
ssh -T git@github.com

# 基于SSH将本地仓库上传到Github
同http同步方式，远程地址换成了git@形式的线上项目地址

# 将远程仓库克隆到本地
打开Git Bash ,输入如下命令并回车
git clone 远程仓库的地址

# 分支在实际开发中的作用
在进行多人协作开发的时候，为了防止互相干扰，提高协同开发的体验，建议每个开发者都给予分支进行项目功能的开发

# master主分支
在初始化本地Git仓库的时候，Git默认创建的一个master的分支，通常把这个master分支叫做主分支

在实际工作中，master主分支的作用是：保存和记录整个项目已完成的功能代码
因此，不允许直接在master分支上面修改代码，风险高

# 功能分支
由于不允许直接在master分支上面修改代码，所以有了功能分支的概念
功能分支指的是专门用来开发新功能的分支，是临时从master主分支上分叉出来的，当新功能开发且测试完毕后，最终需要合并到master主分支上面

功能分支生命短，主分支一直存在

# 查看分支列表
使用下面命令，查看当前仓库所有分支列表
git branch

*星号代表所处分支

# 创建新分支
使用如下命令，可以基于当前分支，创建一个新的分支，此事，新分支中的代码和当前分支完全一样
git branch 分支名称

# 切换分支
使用如下命令，可以切换到对应的分支上进行开发
git checkout 分支名称

# 分支的快速创建和切换
-b表示一个新分支
checkout 表示切换到刚才新建的分支上
git checkout -b 分支名称

# 合并分支
功能分支的代码开发测试完毕以后，可以使用如下的命令，将完成后的代码合并到master主分支上，在此之前，必须git add .的状态上进行下面操作
1.切换到master分支上
git checkout master
2.在master分支上运行git merge命令，讲login分支的代码合并到master分支
git merge login

合并分支的注意点
假设要把C分支的代码合并到A分支，则必须先切换到A分支上，再运行merge命令，来合并C分支

# 删除分支
当把功能分支的代码合并到master主分支上以后，就可以使用如下的命令，删除对应的功能分支
git branch -d 分支名称

# 遇到冲突时的分支合并
如果在两个不同的分支中，对同一个文件进行了不同的修改，Git就没办法干净的合并他们，此事，我们需要打开这些包含冲突的文件然后手动解决冲突
假设，再把reg分支合并到master分支期间，代码发生了冲突
git checkout master
git merge reg

打开包含冲突的文件，手动解决冲突后，再执行如下的命令
git add .
git commit -m "解决了合并冲突的问题"

# 讲本地分支推送到远程仓库
新版github更新了，推送前，要增加下面指令
git branch -M main

-u表示把本地分支和远程分支进行关联，只在第一次推送的时候需要带 -U 参数
git push -u 远程仓库的别名 本地分支名称:远程分支名称

实际案例：
git push -u origin payment:pay

如果希望远程分支的名称和本地分支名称保持一致，可以对命令进行简化
git push -u origin payment

注意：第一次推送分支需要带-u参数，此后可以直接使用git push推送代码到远程分支

# 查看远程仓库中所有的分支列表
通过如下的命令，可以查看远程仓库中，所有的分支列表的信息
git remote show 远程仓库名称（默认origin）

# 跟踪分支
跟踪分支指的是：从远程仓库中，把远程分支下载到本地仓库中，需要运行的命令如下：
从远程仓库中，把对应的远程分支下载到本地仓库，保持本地分支和远程分支名称相同
git checkout 远程分支的名称
示例：
git checkout pay

从远程仓库中，把对应的远程分支下载到本地仓库，并把下载的本地分支进行重命名
git checkout -b 本地分支名称 远程仓库名称/远程分支名称
示例：
git checkout -b payment origin/pay

# 拉取远程分支的最新的代码
可以使用如下的命令，把远程分支最新的代码下载到本地对应的分支中：
从远程仓库，拉取当前分支最新的代码，保持当前分支的代码和远程分支代码一致
git pull

# 删除远程分支列表
可以使用如下的命令，删除远程仓库中指定的分支
删除远程仓库中，指定名称的远程分支
git push 远程仓库名称 --delete 远程分支名称
示例：
git push origin --delete pay

强制删除分支
git branch -D reg




# 总结
1.能够掌握Git中基本命令的使用
git init 
git add .
git commit -m "提交消息"
git status 和 git status -s
2.能够使用Github创建和维护远程仓库
能够配置Github的SSH访问
能够将本地仓库上传到Github
3.能够掌握Git分支的基本使用
git checkout -b 新分支名称
git push -u orgin 新分支名称
git checkout 分支名称
git branch