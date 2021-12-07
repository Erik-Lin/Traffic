# a readme from link-studio

## 傻瓜教程：
注意：现在git是用户名+密码是token不是你的登录密码，可以看教材配置或ssl配置
先建一个文件夹，在里面执行git clone https://github.com/Erik-Lin/Traffic.git

然后进入目录cd .\link-studio\
此时你默认在main分支内，然后创建自己本地分支git checkout -b xxx
可以执行git branch ，看看自己现在的位置
然后在本地可以创建文件夹，放入你想添加的代码
git status可以查看状态
执行 git add .添加所有改动到本地git分支
执行 git commit -m "xxxxxxxxx" 添加commit
执行 git push origin xxx 这里的xxx是你的本地分支名字，直接push到远程，可以取github查看你是否成功
管理好自己的分支，不要改动别人分支，私戳给我你的分支名，我的分支是zhangmh可以直接下载zip看代码

每个人维护自己的分支，分支自己起个名就行，push就push到自己的分支上 git push origin xxx:xxxx, xxx代表自己本地分支，xxxx代表远程你的分支，当然如果你嫌分支管理麻烦就直接 git push origin xxx 就好，如果想拉取别人的分支需要在本地先创建分支git checkout -b 你起的一个本地分支名，然后git pull origin 别人远程的分支名，这样就把别人的分支拉取下来了；还有git的操作git branch 查看自己当前的分支；git checkout 分支名 切换到相应分支；git status 查看当前git状态； git stash 如果分子内容没有commit，保存当前分支的修改，这样之后可以轻松切换分支， git stash apply 当你回到之前修改的分支了用来恢复内容
