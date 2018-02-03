### Git命令

- ##### 基本了解

  - git命令是一些命令工具的集合，可以用来跟踪，记录文件的变动。可以对文件进行保存、比对、分析、合并等。这个过程称之为版本控制。

- ##### 1、安装Git

  - **Linux **—— 打开控制台，然后通过包管理安装，在**Ubuntu**上命令是：

    ```
    sudo apt -get install git-all
    ```

  - **Windows** —— **git for windows**,包括图形工具以及命令行模拟器。

  - **OS X ** —— 最简单的方式使用**homebrew**安装,命令执行行

    ```
    brew install git
    ```

- ##### 2、配置Git

  - 安装好***git***,首先配置信息，主要是配置用户名和邮箱，打开终端，执行以下命令

    ```
    $ git config --global user.name "my name"
    $ git config --global user.email "my email"
    ```

- ##### 3、创建一个新仓库 —— git init

  - ***git***会把所有文件以及历史记录保存在你的项目中，创建一个新的仓库，首先要去项目路径，执行***git init***。然后创建一个隐藏的文件夹***.git***,所有的信息都存储在其中。

  - 在桌面创建一个文件夹 ***demo***,打开终端

    ```
    $ cd Desktop/demo/
    $ git init
    ```

- ##### 4、检查状态 —— git status

  - ***git status***是另一个非常重要的命令，它会告诉我们创建库的当前状态：是否为最新代码，

    ```
    $ git status
    on branch master
    Initial commit
    Untracked files:
    （use "git add...."to include in what will be committed）
    ```

- ##### 5、暂存 —— git add

  - ***git***有个概念叫暂存区，一开始为空，可以通过***git add***命令添加内容，并使用***git commit***提交

    ```
    $ git add 文件名
    $ git add .或git add ./提交所有的文件
    ```

- ##### 6、提交 —— git commit 

  - 一次提交代表着我们的仓库到了一个交付状态,创建提交，需要我们提交东西到暂存区(git add)

    ```
    $ git commit -m "注释"    //注释的内容为对这次提交内容的描述
    ```

#### 远端仓库

- ##### 1、链接远端仓库 —— git remote add

  - 首先需要在远端创建一个仓库，然后获取到地址

    ```
    $ git remote add origin https://github.com/
    ```

  - 一个项目可以同时用有好几个远端仓库为了能够区分，通常会起不同的名字。通常主远端仓库被称为origin。

- ##### 2、上传到服务器 —— git push

  - **git push**命令会有两个参数，远端仓库的名字，以及分支的名字

    ```
    $ git push origin master
    ```

- ##### 3、克隆仓库 —— git clone

  - 使用***git clone***进行下载到本地

    ```
    $ git clone 地址
    ```

  - 本地会创建一个新的仓库，并自动将***github***上的分支设定为远端分支

- ##### 4、从服务器上拉取代码 —— git pull

  - 如果你更新了代码到仓库上，其他人可以通过git pull命令拉取你的变动

    ```
    $ git pull origin master
    ```

  #### 分支

  - 当你在做一个新功能的时候，最好是在一个独立的区域上开发，通常称之为分支。分支之间相互独立，并且拥有自己的历史记录。这样做的好处：
    - 稳定版本的代码不会被破坏
    - 不同的功能可以由不同开发者同时开发
    - 开发者可以专注于自己的分支，不用担心被其他人破坏了环境
    - 在不确定之前，同一个特性可以拥有几个版本，便于比较

- ##### 1、创建新分支 —— git btanch

  - 每一个仓库的默认分支都叫***master***，创建新的分支

    ```
    $ git master zxy
    ```

  - 创建一个名为zxy的新分支，它跟当前分支同一起点

- ##### 2、切换分支 —— git checkout

  - 单独使用***git branch*** 可以查看分支状态

    ```
    $ git branch
    	zxy
    * master	
    ```

  - *号表示当前活跃分支为master，使用***git checkout***切换分支

    ```
    $ git checkout zxy
    ```

- ##### 3、合并分支 —— git merge

  - 在zxy分支的任务是增加一个**test.txt**。先创建，在添加到暂存区，提交

    ```
    $ git add test.txt
    $ git commit -m "分支添加的文件"
    ```

  - 分支任务完成了，回到master分支

    ```
    $ git checkout master
    ```

  - 在***master***分支上没有**test.txt**.可以使用***git merge***把***zxy***分支合并到***master***上。

    ```
    $ git merge zxy
    ```

  - 然后再把***zxy***分支删掉

    ```
    git branch -d zxy
    ```


#### 高级

- #### 1、对比两个不同提交之间的差别

  - 每次提交都有一个唯一的***id***，查看所有提交和他们的***id***，可以使用***git log***

    ```
    $ git log
    ```

  - ***id***很长，只需要复制前面一小部分即可，查看某一次提交更新了什么，使用***git show***

    ```
    $ git show id
    ```

  - 查看两次提交的不同，可以使用***git diff*** id..id

    ```
    $ git diff id1..id2
    ```

- ##### 2、回滚某个文件到之前的版本

  - ***git***允许将某个特定的文件回滚到特定的提交，使用***git checkout***

    ```
    $ git checkout id test.txt 将test.txt回滚到某个状态
    ```

- ##### 3、解决合并冲突

  - 冲突经常出现在合并分支或者是拉去别人的代码。有些时候***git***能自动处理冲突，但大部分需要手动处理

    ​