        
 通过Git将本地代码push到远程github仓库简单示例

 作者：caolinxi

 时间：2018年7月24日

1.      在github端添加仓库
        Repositories-> New

2.      创建仓库
        输入repository name

3.      最初新建的仓库，没有任何branch：
        提示初始化仓库命令
        提示的代码：

        …or create a new repository on the command line
        echo "# git0724" >> README.md
        git init
        git add README.md
        git commit -m "first commit"
        git remote add origin https://github.com/mengxiangjialinxi/git0724.git
        git push -u origin master

        …or push an existing repository from the command line
        git remote add origin https://github.com/mengxiangjialinxi/git0724.git
        git push -u origin master

4.      新建本地仓库

        [root@docker01 mydocker]# pwd
        /root/mydocker
        [root@docker01 mydocker]# git init
        重新初始化现存的 Git 版本库于 /root/mydocker/.git/
        #####这时，当前文件夹/root/mydocker下就新建了一个本地仓.git/

5.      创建文件

        [root@docker01 mydocker]# echo "# git0724" >> README.md

6.      将文件添加并commit进本地仓

        [root@docker01 mydocker]# git add README.md
        [root@docker01 mydocker]# git commit -m "first commit"
        [master 0d7b8b1] first commit
         1 file changed, 1 insertion(+)

7.      将本地仓库关联到github远程仓库

        [root@docker01 mydocker]# git remote add git_test https://github.com/mengxiangjialinxi/git0724.git
        [root@docker01 mydocker]# git remote -v
        git_test        https://github.com/mengxiangjialinxi/git0724.git (fetch)
        git_test        https://github.com/mengxiangjialinxi/git0724.git (push)
        #####这里的git_test就是远程仓库在本地的别名，之后push时只需要用别名即可。

8.      将本地仓push到远程仓库

        ***命令说明：git push 远程仓别名 本地仓branch：远程仓branch

        [root@docker01 mydocker]# git push git_test master:master
        Username for 'https://github.com': mengxiangjialinxi
        Delta compression using up to 2 threads.
        [root@docker01 mydocker]# git add .
        [root@docker01 mydocker]# git commit -m "branch first commit"
        Compressing objects: 100% (1/1), done.
        Writing objects: 100% (1/1), 1.24 KiB | 0 bytes/s, done.
        Total 1 (delta 0), reused 0 (delta 0)
        To https://github.com/mengxiangjialinxi/git0724.git
         * [new branch]      master -> master
        #####可以看到，本地的master branch传到了远程仓的master branch

9.      添加branch分支

        ***通过修改文件后，将本地的文件add 并commit到本地仓，然后push到远程的另一个分支：branch_test-1

        [root@docker01 mydocker]# vim branch_test
                test for branch push
                auther  : caolinxi
                date    : 2018年7月24日 14:20:45

        [root@docker01 mydocker]# git add .
        [root@docker01 mydocker]# git commit -m "branch first commit"
        [master 8961651] branch first commit
         2 files changed, 2 insertions(+), 1 deletion(-)
        [root@docker01 mydocker]# git push git_test master:branch_test-1
        Username for 'https://github.com': mengxiangjialinxi
        Password for 'https://mengxiangjialinxi@github.com':
        Counting objects: 7, done.
        Delta compression using up to 2 threads.
        Compressing objects: 100% (3/3), done.
        Writing objects: 100% (4/4), 369 bytes | 0 bytes/s, done.
        Total 4 (delta 0), reused 0 (delta 0)
        To https://github.com/mengxiangjialinxi/git0724.git
           d7edf28..8961651  master -> branch_test-1

        #####可以看到，多了branch_test-1分支，此分支下多了文件branch_test，重新提交的文件，备注是"branch first commit"

