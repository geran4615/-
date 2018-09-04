# 安装Git
Git Bash打开git命令行，然后设置(初次使用时设置)

    git config --global user.name "Your name"
    git config --global user.email "email@zlg.cn"

## 初始化Git仓库
通过`git  init`命令，可以把目录变成Git可以管理的仓库。如，

    git init
## 把文件添加到版本库

    git add readme.txt
    git commit -m "本次提交的说明，可输入任意内容"

commit可以一次性提交很多文件，所以可以多次add**_不同的文件**。如:

    git add file.txt
    git add file2.txt file3.txt
    git commit -m "add 3 files"

## 时光机穿梭

    git status          //查看工作区的状态
    git diff            //查看修改内容
    //版本回退
    git log             //显示提交日志，从最近到最远
                        //如果嫌输出信息太多，可以加上--pretty=oneline参数

在Git中，HEAD表示当前版本，HEAD^表示上一个版本，HEAD^^表示上上个版本，上100个版本写成HEAD~100。

    git reset --hard HEAD^      //回退到上一个版本
    git reset --hard [commit_id]  //指定回到过去的某个版本，版本号没必要写全，能让Git区分就好
    cat readme.txt     //查看readme.txt文本内容
    git reflog         //查看历史命令，以便确定回到哪个版本

# 工作区和暂存区
Git和其他版本控制系统如SVN的一个不同之处就是有暂存区的概念。
## 工作区（Working Directory）
指电脑里能看到的目录。
## 版本库 （Repository）
工作区有一个隐藏目录.git。它不算工作区，而是Git的版本库。

`git add`命令实际上就是把要提交的所有修改放到暂存区（stage）。然后，执行`git commit`就可以一次性把暂存区的所有修改提交到分支，一旦提交完成，而又没有对工作区做任何修改，那么工作区就是“干净”的。
# 管理修改
`git commit`命令可以将多次`git add`添加的修改一次性提交。
# 撤销修改
    git checkout --readme.txt    //丢弃工作区的修改
上面命令的作用是把readme.txt文件在工作区的修改全部撤销，这里有两种情况：

1. readme.txt自修改后还没有被放到暂存区。现在撤销修改就回到和版本库一模一样的状态。（回到最近一次`git commit`时的状态。）

2. readme.txt已经添加到暂存区，又做了修改。现在，撤销修改就回到添加到暂存区后的状态。（回到最后一次`git add`时的状态。）

***

    git reset HEAD readme.txt    //把暂存区的修改撤销掉（unstage）

## 场景1
***
扰乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout --file`。
## 场景2
***
不仅乱改了工作区某个文件的内容，还添加到了暂存区时，想撤销修改，分两步：第一步用命令`git reset HEAD file回到场景1，然后按场景1操作。
## 场景3
***
已经提交了不合适的修改到版本库时，想要撤销本次提交，可参考时光机穿梭一节。（前提是没有推送到远程库）

# 删除文件
    rm test.txt    //删除工作区中的test.txt文件，版本库中仍存在
    git rm test.txt   //删除版本库和工作区内的test.txt文件
                      //此时用`git checkout --file`无法恢复

如果删错了，可以很轻松地把误删的文件恢复到最新版本。

    git checkout --test.txt
`git checkout`其实是用版本库里的版本替换工作区的版本。无论是修改还是误删，都可以“一键还原”。
# 忽略特殊文件
Step 1:在需要创建.gitignore文件的文件夹，右键选择`git bash`进入命令行，进入项目所在目录；

Step 2:输入`touch .gitignore`,在文件夹就生成了一个“.gitignore”文件；

Step 3:在“.gitignore”文件里输入要忽略的文件夹及文件，再用`git add`提交.gitignore即可。

## .gitignore文件的编写
+ 如果名称的最前面是路径分隔符（/），表示忽略的文件在此目录下；
+ 如果名称的最后面是（/），表示忽略整个目录，但同名文件不忽略；
+ 如果名称前面加（!），代表不忽略。

# 如何删除错误添加到暂存区或版本库里的文件？
1.  仅删除暂存区里的文件

        git rm --cache 文件名
    
2.  删除暂存区和工作区的文件
        
        git rm -f 文件名

3.  删除错误提交的commit

    此时工作区、暂存区、版本库三者内容一致。
        
        //仅撤销已提交的版本库，不会修改暂存区和工作区
        git reset --soft 版本库ID

        //仅撤销已提交的版本库和暂存区，不会修改工作区
        git reset --mixed 版本库ID

        //彻底将工作区、暂存区和版本库恢复到指定的版本
        git reset --hard 版本库ID
