## git fetch 和 pull的区别

+ 相同点
+ 不同点



## git squash 和 rebase的区别







## git里的一些操作优化

* 每天早上，记得切回master分支，从upstream里面拉取最新的master的代码，往正在开发的分支里rebase
* 每次提交pr/push之前，都要切回master分支，同上; git pull upsteam master
* 如果是你的分支里，有别人也在开发的内容，需要拉取别人的分支，记得在当前分支上新建一个test分支，在test分支里面，拉取别人的分支(比如你需要一些前端的代码)，测试，修改自己原本的分支，在test分支里面rebase原本的分支，这样可以保证git提交的内容不冲突，同时开发没问题，同时git log里的message也是没有问题的，干净的。



##  git的基本开发流程

* 首先，有了账号之后，加入你们的组织，获得代码的提交权限，关于git的权限，目前还有没有太多的了解，需要在做看一些关于权限的文章

* 有了基本的读写权限之后，就可以开发了，说说我目前了解到的开发流程，仅仅实用我们公司，不代表具有通用性。

  * 从组织的rep中，fork一份代码到你自己账号里，然后git pull 自己账号下的代码到本地，此时会有三个rep，分别为：

    * 1.本地的rep，即为local
    * 2.自己账号下的rep，即为origin
    * 3.远程的组织的rep，即为upstram

  * 在自己本地pull/clone下来的rep，默认为master分支，和你clone时选择的分支有关系，可以使用git branch命令查看

  * git branch branch_name ，新建一个分支名称，我们一般以issue号码为名称，然后切换到对应的分支里面，git checkout -b branch_name，在对应的分支里面开发

  * 开发完毕后，参考操作优化第二条

  * 同步了最新的代码后，现在需要提交到origin的master里面， git push origin branch_name:master

  * 此时，在自己账号下的rep里面，就可以看到对应的修改内容，点击file diff ，就能看到对应的修改的内容

  * 点击下面的pull request，此时可以把修改的内容合并到upstream的master里面，点击提交pr，输入对应的信息和reviewer的人，申请让他们review代码 ps:关于权限相关的内容，暂时还没有了解，此时应该会有权限相关的步骤的说明

  * 别人review玩你的代码，同时没有冲突的话，你就可以合并代码的主分支了，合并完，在本地的master里pull最新的代码

  * 一般是不需要操作origin的分支的，它只是作为我们的一个中转站，如果需要操作的话，就使用更新完毕的local的分支，覆盖掉origin的分支即可。

    