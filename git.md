
### 创建版本库

  git仓库的创建

  在一个文件夹打开 git bash
  输入
  git init

  添加文件

  git add <文件名>

  git add . // 添加所有文件

  提交文件

  git commit -m "<输入注释>" // 最好输有意义的


### 时光机穿梭

  git status 查看仓库的状态
  ``` 
      $ git status
      On branch master
      Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git checkout -- <file>..." to discard changes in working directory)

          modified:   git.md

      no changes added to commit (use "git add" and/or "git commit -a")

  ```

  上述代码说明需要进行提交

  git diff 查看仓库中的代码和文件中代码区别

  ```
    @@ -1,16 +1,38 @@
    -git仓库的创建

    -在一个文件夹打开 git bash
    -输入
    -git init
    +### 创建版本库

    -添加文件
    +  git仓库的创建

    -git add <文件名>
    +  在一个文件夹打开 git bash
    +  输入
    +  git init

    -git add . // 添加所有文件
    +  添加文件

    -提交文件
    +  git add <文件名>

    -git commit -m "<输入注释>" // 最好输有意义的
    +  git add . // 添加所有文件
    +
  ```

  然后

  git add .

  git commit -m "进入时光机部分"

  git status

  #### 回退版本

  git reset --hard HEAD^ // (添加冲突)回退到上一版本

  git reset --hard <commit id> // 回退到指定的版本

  穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。

  要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

  ### 工作区和版本库

  #### 工作区

  文件里显示的代码文件所在的位置

  #### 版本库

  .git 文件夹

  里面有 stage 暂存区 和 HEAD指针

  stage 暂存区

  git add . 提交的文件是放在暂存区

  git commit 将暂存区的文件提交到当前分支

  ### 修改

  每次修改，如果不用git add到暂存区，那就不会加入到commit中。

  #### 撤销修改

  取消工作区的修改

  git checkout --<文件名> 丢弃当前工作区文件的修改 (不要在打开vscode的时候用这个)

  取消已经git add 到缓存区的修改

  git reset --hard HEAD <文件名> 将暂存区的文件回退到工作区

  git checkout --<文件名> 丢弃工作区的修改

  场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

  场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。

  场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。

  本地部分已完成

  ### 远端仓库

  git 指的就是本地仓库.

  github 是一个git的服务器,帮助我们在网络上,保存我们的文件.

  1. 将远程仓库和本地仓库连接,并将文件推到远端的步骤:

  在 github 上创建一个远程的仓库

  git remote add origin <github仓库的网址> // 将git 本地仓库与 github 的远程仓库连接. 

  因为第一次还没有commit

  需要使用 

  git push -u origin master // 将本地文件推到远程仓库

  2. 将远程仓库的文件,同步到本地的步骤:

  在要同步的文件夹中,右键打开 git bash .

  输入

  git clone <网址> // 将远端的文件同步到本地

  ### 分支

  回到之前版本库的问题 

  其中的HEAD指针,指向当前正在工作区的分支, 当调整分支时,工作区的文件也会改变

  ####　创建 dev 分支

  git branch dev

  ####　切换到 dev 分支

  git checkout dev

  #### 创建并切换分支

  git checkout -b dev

  #### git branch (查看当前分支)

  分支也可以进行

  git add

  和 

  git commit

  可以编写与主分支不一样的部分

  #### 合并分支

  git merge dev

  把 dev 分支的内容合并到当前分支

  删除分支

  git branch -d dev

  #### git 的新命令 (在本人的电脑上无法使用)

  创建并切换到新的 dev 分支

  git switch -c dev

  切换到已有的 master 分支

  git switch master

  #### 解决冲突

  下面是冲突的文字

  这是git中的 master 分支的语句
  这是git中的 dev 分支的语句

  当我们合并时,提示冲突后,通过

  git status

  查看冲突是在那个文件

  将冲突一个一个解决完后,再

  git add .

  git commit 

  然后提交

  git log --graph 

  可以看到合并时的示意图

  ### 分支管理策略

  通过 --no-ff 方式的 git merge

  git merge --no-ff -m "通过 --no-ff 合并分支" dev

  这样合并分支时.会创建一个commit 提示曾经合并过

  <span style="color:rgb(144, 24, 89)">这里是修复的bug</span>
