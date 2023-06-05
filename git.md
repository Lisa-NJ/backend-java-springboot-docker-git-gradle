（资源一）简单介绍GIT版本控制 

https://www.youtube.com/watch?v=659kWnMgpoI

（资源二）2021最新版Git教程-git通俗易懂教学视频 P1-16 （乐字节）

https://www.bilibili.com/video/BV1Jr4y1P7z4?from=search&seid=5608034078573286055&spm_id_from=333.337.0.0 

其他：Git过滤文件和文夹

https://www.cnblogs.com/wjs2019/p/11720494.html

VSCode结合git的全面使用流程 --智伤帝

Mac下 VSCode 自己 集成了git



#### 基本概念

GIT -- 版本控制软体

GITHUB -- 储存 GIT 版本控制档案的云端服务

**Git文件的三种状态和工作模式**

工作区  --add--> 暂存区 --commit--> Git仓库区（.git隐藏目录）

已修改、              已暂存、                  已提交

客户端建有本地仓库，从远程仓库拉取版本时可得到完整的历史版本记录，不同于svn（客户端只存最新版本）；

每次提交的时候，先提交到本地仓库，再从本地仓库提交至远程仓库；

客户端之间可以相互连接，通信；

Windows 无内建 Git，需下载 Git for windows;

图形化界面有 Tortoise Git（Windows）、Source Tree（Mac） 等；



#### **下载安装及配置**：

官网下载地址：https://git-scm.com/downloads 

Install [homebrew](https://brew.sh/) if you don't already have it, then:

`$ brew install git`

**Windows系统 Command命令**：

​	dir /a 显示所有文件，包括隐藏文件 

​	rd \/s/q 全部删除

​	type fileName 打开文件

​    echo.>file.txt. 建立有空白行的档案

​	 type nul>file1.txt 建立空档

​	del 删除档案 

​	move  file1.txt abc\file1.txt 移动文件

​	copy file1.txt file1-c.txt 复制

​	ren file1-c.txt file2.txt  改名

Unix like 无磁碟机概念 /dev/sda

​                                        /dev/sdb

Mac系统

​	rm - rf/ 全部删除

#### 本地仓库操作

Git规定：所有 commit 必须要有使用者名称和信箱；

```
git init  //在目前的资料夹内部建立本地档案库

git init folder //建立资料夹并建立本地档案库
git config user.name "Lisa Huang" 
git config  user.email ***@gmail.com. //设定当前档案库使用者Email
git config --global user.name "Lisa Huang" //设定全域使用者名称
git config --global user.email ***@gmail.com //设定全域使用者Email

git config --global color.ui auto //设置配色方案
git config --global merge.conflictstyle diff3
git config --global code.editor "code --wait"
git config --global init.defaultBranch main

git config --list //显示所有有效的设定

git config --list --local  //显示在local上面有效的设定
git config --list --global 

git config --list --edit  //可以打开写好的配置文件进行修改
git config --list --system 

git branch
git branch -v 
git branch --merged
git branch --no-merged

// change a branch's name to a new name locally and on the remote
git branch --move old-branch-name new-branch-name
git push --set-upstream origin new-branch-name
git push origin --delete old-branch-name
```


PAT - GitHub / Settings / Developer... / Generate ->
	ghp_...

```
$ git clone https://<tokenhere>@github.com/<user>/<repo>.git
$ git push

// update the message of the lase commit
$ git commit --amend -m [message]

// connect current branch with a remote branch
$ git branch --set-upstream [branch] [remote-branch] 
```

 

git status //查看目前暂存区的状态

git add filename  //暂存某文件

git add .  //暂存当前目录下的所有文件

git add *.js filename  //暂存所有 js文件以及 fileaname 文件 

git reset filename //反悔从 暂存区 拿回，针对还没有 commit 过的文件 



git commit -m 'comment' //将暂存区的档案 commit 到本地档案库

git add -u //只加入被追踪&修改过 的档案到暂存区，不包含新增的档案  

git commit -am "update" //commit 被追踪&修改过 的档案到本地档案库，不包含新增的档案

git commit --amend -m "fix comment" //修改最后一次 commit 的注释

git rm file.txt //从本地库移除指定文件

git log //显示所有 commit 记录，如果太长按 Q - 退出

git log --pretty=oneline //简要版本的提交记录 查看

 

.gitignore //排除被追踪的档案清单（每个档案或资料夹一行，可使用万用字元），git status 后不再显示这里面指定的文件



**重要概念**

HEAD：工作目录比对的基准；

master：预设的分支名称，类似变数指向 commit；

commit 发生什么事？HEAD 和 目前分支（master）都会移到最新的 commit 上；

**原理：**

git cat-file -p HashID //查看hash id的内容，hash id最少4码以上

100644 blob 一般文件

040000 tree 资料夹

利用档案内容计算一个hash ID，如果内容不变，ID 不变；



git show //列出最后一个 commit， 包含异动内容

git show commitID//显示：指定 ID 的 commit与上一版的变更

git show commitID abc.txt //查看某文件是否发生变化，如果没有显示空白

git show commitID: abc.txt //查看指定版号下指定档案的完整内容

git diff    //比对 工作目录与暂存区 文件的差异  
git diff master..feature //比较两个不同版本之间的区别
git diff master..feature -- path/to/file //比较两个不同版本某个文件的区别

git add -p s y n e //将档案 分块 加入 暂存区，commit 过的才有效

【git checkout】

git checkout index.html //复原 HEAD 的index.html（修改过的档案还原），如果暂存区有index.html，优先从暂存区取回

git checkout commitID index.html //复原 指定commitID 的index.html，(但比對還是HEAD，預設加到暫存區，有修改還是要再次add)

git checkout commitID //工作目錄和HEAD更新到這個commit，(**不重設暫存區，但不会还原commit后改過的檔案，也就是后来修改过的档案以目前工作区的为准**)，git log只會顯示 HEAD之前的紀錄，git log --all才可看到全部 -- 使用场景：想要查看以前某 版本下文件的内容，使用该命令，用完后再checkout回到当前版本；

HEAD 会指向最新 checkout 的版本，但是 Master 不变，所以 HEAD 和 Master 脱钩；git log 只会显示 HEAD 之前的记录；尽量用 分支 名称 做 checkout；

git log --all //可以显示全部记录

git checkout master //HEAD 可以 重新指回到 master

做commit的时候，是我所在的分支名称会跟着往前跑；

【git revert】

git revert commitID //复原commit做的事情，自动重做一个新的commit，跳出编辑器 :q 可以退出编辑状态

git revert commitID -n //复原commit做的事情，还原到工作目录，不会自动重做新的commit

git revert c4 c3 c2 //依次连续做rollback

【git reset】

git reset filename //将错add的文件从暂存区拿回

git reset --hard //重设目前 HEAD 的工作目录，清除暂存区；

git reset commitID --hard   //重设 HEAD & 工作目录 & 目前分支 到 commitID 指定的版本，清除暂存区

git reset --mixed //保持工作目录不变，清除暂存区

git reset commitID --mixed   //重设 HEAD & 目前分支 到 commitID 指定的版本，保持工作目录不变，清除暂存区；用途：合并或打散 commit

git reflog //显示 HEAD 移动的历史记录

git reset --soft //基本上没什么用  

git reset commitID --soft //重设 HEAD & 目前分支 到 commitID 指定的版本，保持 工作目录&暂存区 不变；

**revert - checkout - reset 对比图**



git reset --hard HEAD^  //HEAD 指向 退回一次

git reset --hard HEAD~3  //HEAD 指向 回退 3 个版本



**分支**

```
git branch  //列出所有分支

git branch -M main // 将当前分支名称改为 main 

git branch dev //在目前 HEAD 位置建立一个新分支

git branch dev -d  //删除分支 dev，不能删除当前操作的分支

git branch dev commitID //在指定 commitID 位置建立一个新分支

git checkout dev  //如果在master修改了某文档，还没有commit之前，切到分支 branchName，带异动切换
```

注意：切不过去的情况，解决办法：

1 reset 舍弃

2 commit 提交

3 stash 收藏

git stash - it is used to temporarily remove the changes you have made on the working tree 

这样可以继续 切换 到别的分支，重新切回来的时候，可以：

git stash list //显示收藏的内容

git stash pop //取出刚才改了一半收藏过的文件





git checkout [commitID] -b new_branch  //在([commitID] or 目前)位置创建并切到新分支

git log --all --graph //显示有线图的commit记录



git merge dev  // 在目前的分支上 合并 dev，预设：使用快进

git merge --no-ff dev  // 不使用快进合并分支 

//。。。

快进：只有 dev 有新的 commit，合并的时候，只需移动 master 到 d2 即可；

不快进：一定产生 commit，看线图比较容易分辨是从主线还是分支； 

**冲突出现**：当合并分支和主干，分支和主干同样的文件相同位置内容不同时，即出现冲突；

**冲突解决**方法：手工修改，重新 add commit（不需要加注解），完成。

多人协同冲突解决：谁发现谁解决，先 git pull，解决冲突，再 提交 并推至远程； 建议 先 pull 再 push。  



如果想要维持版本线条一条的话：

git rebase master //把目前分支重写到 master，如果有冲突先修好 git add 加入，再透过 git rebase --continue 完成

//。。。

其他技巧：

完整 commit 命令需要输入 m，如果没有的话：i 可输入 注释，wq 可以保存并退出；   

git branch -m/-M oldName newName  //修改/强制修改 分支名

git restore **--staged** filename //撤销不小心提交到暂存区的文件

git reset HEAD filename  //撤销上次的操作，可能是 commit

rebase之后，想要再找回 dev 分支，需要用到 ref 



git cherry-pick commitID //摘取别的分支上的某个 commitID 套用到目前分支上

**远端档案库**

git init --bare //在目前资料夹建立远端档案库，没有 .git 文件夹

git init --bare folder//开新资料夹并建立远端档案库

【本地档案库连接远端档案库】

第一种：已有本地库，跟远端做连接

git remote // give the name of the remote repo

git remote -v // give the name and url of the remote repo

git remote add origin url //新增遠端檔案庫位置(適合已經有本地端檔案庫)，遠端檔案庫代號origin

git remote show origin //显示远端档案库资讯

git ls-remote url //查看远端档案库所有的分支内容

git fetch //把远端commit记录抓下来到本地端，不会重设工作目录，也不会改变HEAD和分支位置，origin/master遠端分支

//怎麼更新到工作目錄?把远端当作分支来看

git merge origin/master //如果本地端沒有任何commit則master會自動建立；如果本地端有master分支則依照合併方式處理

//抓取远端档案库内容 git pull 

pull = fetch + merge；拉下紀錄並同時自動merge；(這時候就會改變工作目錄,HEAD,分支位置)

git pull origin master //抓取遠端檔案庫的master分支內容

git branch -u origin/master master //設定遠端master跟本地端master為預設推送或拉取的位置

git remote remove origin //刪除遠端檔案庫設定

第二种：如果沒有本地端檔案庫

git clone url //建立相同名稱資料夾並且下載檔案庫全部內容，(全新的本地端檔案庫，同時也設定好遠端預設推送或拉取的位置)

git clone url folder //下载到folder资料夹

git checkout -b devL origin/dev //拉取远程指定分支到本地 并 创建 devL 及切到新分支

git push //把本地端的commit推送到遠端

git push -u origin master //和 git branch -u origin/master master 意思相同，然後同時也會把commit推到遠端去。-u是 --set-upstream 的缩写

输入用户名 + password:PAT 即可push成功

【push時會先要求pull】

因為push上去的commit一定要包含遠端最後一個commit，所以得先pull合併現在遠端最後一commit接下來才能push



通过merge来解决push不上去的问题：



不好的方法：

git push -f //強制遠端設為跟本地端一樣的分支位置，(團隊合作中通常禁用,避免不知情的人又合併進去)，新建一個commit然後push才是正解

git push --force-with-lease //稍微安全一點的做法，你至少要先fetch確定知道有些記錄沒更新到，才能硬推

【清除不必要的档案】

git clean -f //清理未版控的檔案(reset不會把沒有版控的檔案刪除)
git clean -xf //清除工作目录中未跟踪的文件和目录, -x：清除工作目录中未跟踪的文件, -f：强制执行清除操作

git gc //清理不必要git的Objects物件

#### **标签管理**

git tag //查看所有标签

git tag tag_name //加标签，默认 为 最后一次记录

git tag tag_name 版本唯一标识 //为 唯一标识符 指定 的版本 加标签

git tag -a tag_name -m "" //加 标签 及 描述信息

git push origin tag_name //将 tag_name 标签 推到远程

git push origin --tags  //推送所有 没有推送过的 标签

git push origin :refs/tags/tag_name //删除远程 tag_name 标签，本地不变

git tag -d tag_name  //删除本地 指定标签

补充：Linux 命令 窗口下 Ctrl Insert 、Shift Insert 为 拷贝 粘贴 快捷键



git ls-files  //查看本地仓库的文件列表 

git checkout 文件名 //从本地仓库拉某文件到工作目录

**本地仓库文件删除** 当成一次修改来处理，假如工作目录删除了 file1.txt

git add file1.txt

git commit -am 'del file1.txt'

或者：

git rm file1.txt //从当前工作目录和本地库同时删掉指定文件



#### 远程仓库及操作

GitHub 和 码云 是最大的开源远程仓库，公司一般会自己搭自己的远程仓库，购买物理服务器开始搭建或者购买云服务的方式。

OCTOTREE：显示层级目录的插件，用在 GitHub 网站，可以在google商店下载

**非登陆状态下下载资源**

在网页上 通过 Download ZIP 下载到本地，然后解压；

或者：shell 里面 通过命令 git clone

git clone 资源在github上的地址链接   //下载资源

**SSH下载资源**

获取 SSH key（文件：*pub），添加进 github Setting/SSH and GPG keys/New key **删除格**，检查是否授权与绑定

ssh-keygen -t rsc -C "$email" //生成 key 到本地

ssh -T git@github.com // You have successfully ... 表示 SSH 绑定 github 成功

注：公钥和私钥类似于锁和钥匙的关系

补充：添加完 ssh key 到 github 账户后，检查时 permission denied 的解决方法：

After add ssh key, add you ssh key to ssh agent too (from official [docs](https://help.github.com/articles/generating-ssh-keys/))

```bash
ssh-agent -s
ssh-add ~/.ssh/id_rsa
```



**提交到远程**

git branch -v；git branch -vv，可以查看上流分支的名字

git remote add origin gitSSH链接 //绑定到远程仓库，只需要做一次

git push -u origin master //推到远程 master 分支

​	加了参数-u后，以后即可直接用git push 代替 git push origin master

git checkout 文件名 //检出

提交的是整体的版本记录

#### **远程分支操作**

git branch --a //查看所有本地及远程分支

git push origin :dev  //删除 dev 分支

git fetch //获取远程分支最新状态

git push origin HEAD:AW-266/Users-can-EDIT-any-task-details-in-Listview-and-Broadview //推到266



#### Pull Request 

https://www.zhihu.com/question/21682976

当你想更正别人仓库里的错误时，要走一个流程：

1. 先 fork 别人的仓库，相当于拷贝一份，相信我，不会有人直接让你改修原仓库的
2. clone 到本地分支，做一些 bug fix
3. 发起 pull request 给原仓库，让他看到你修改的 bug
4. 原仓库 review 这个 bug，如果是正确的话，就会 merge 到他自己的项目中

至此，整个 pull request 的过程就结束了。



//... LISA 理解 SSH 秘钥  2021-12-31

#### Git Hooks

https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks

Like many other Version Control Systems, Git has a way to fire off custom scripts when certain important actions occur. There are two groups of these hooks: **client-side** and **server-side**. Client-side hooks are triggered by operations such as committing and merging, while server-side hooks run on network operations such as receiving pushed commits. You can use these hooks for all sorts of reasons.

The hooks are all stored in the `hooks` subdirectory of the Git directory. In most projects, that’s `.git/hooks`. 

最常用的两个如下，都在 git commit 执行前调用，都可以用 git commit -no-verify 绕过：

1. `commit-msg`：可用于将消息规范化为某种项目标准格式，还可用于检查消息文件后拒绝提交；
2. `pre-commit`：会在提交前被调用，并且可以按需指定是否要拒绝本次提交；不接受任何参数，并且在获取提交日志消息并进行提交之前被调用；脚本 git commit 以非零状态退出会导致命令在创建提交之前中止；

【使用 `git hooks` 来去校验我们的提交信息】

要完成这么个目标，需要使用两个工具：

1. [commitlint](https://link.zhihu.com/?target=https%3A//github.com/conventional-changelog/commitlint)：用于检查提交信息

   安装依赖@commitlint/cli + 创建 commitment.config.js 文件

2. [husky](https://link.zhihu.com/?target=https%3A//github.com/typicode/husky)：是`git hooks`工具

```bash
npm install husky@7.0.1 --save-dev  //安装依赖 husky
npx husky install //启动`hooks`生成`.husky`文件夹
npm set-script prepare "husky install" //在 package.json 中生成 prepare 指令
npm run prepare //执行 prepare 指令
> husky - Git hookd installed //执行成功，提示
npx husky add .husky/commit-msg 'npx --no-install commitlint --edit "$1"' //添加 commitlint 的 hook 到 husky中, 并指令在 commit-msg 的 hooks 下执行 '...' 指令
```

至此， 不符合规范的 [commit](https://so.csdn.net/so/search?q=commit&spm=1001.2101.3001.7020) 将不再可提交；
