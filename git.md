```
git config --global user.name "kevin"
git config --global user.email "kevin@example.com"
```

### 设置git客户端提交时的认证问题，参考

https://www.nih-cfde.org/resource/setting-up-github-authentication/#user-content-step-3a-generate-a-pat

---

```
$ git config --global user.name "xiaowukong"
$ git config --global user.email "test@exmaple.com"

# 列出配置详细信息
$ git config --global -e
```

```
$ git version
$ git config --global core.editor "vi"
```

```
$ git config --global diff.tool p4merge
$ git config --global difftool.p4merge.path "/Applications/p4merge.app/Contents/MacOS/p4merge"
$ git config --global difftool.prompt false
```

```
$ git config --global merge.tool p4merge
$ git config --global mergetool.p4merge.path "/Applications/p4merge.app/Contents/MacOS/p4merge"
$ git config --global mergetool.prompt false
```

### New Repo
```
$ git init
$ git status
$ git add file.txt
$ git commit -m "first file in demo repo"
```

```
$ git add .
```

```
$ git log
$ git log --oneline
$ git log --graph
$ git log --decorate
$ git log --all
```

```
$ git show
$ git ls-files
$ git commit -am "Updating me"
```

```
$ git reset HEAD your_file
```
```
$ git checkout -- your_file
```

```
$ git config --global alias.hist "log --oneline --graph --decorate --all"
$ git config --global --list

$ git hist -- your_file

$ git mv your.file my.file
$ git commit -m "renaming example"

$ git rm your.file

$ git add -u
$ git add -A

$ git diff fc64fcc HEAD
$ git difftool fc64fcc HEAD
```

### Branching
#### Special Markers
* Like "pointers"
* HEAD
	* Points to Last Commit of Current Branch
	* Can be Moved
```
$ git branch
$ git checkout -b updates
```

```
// in our master branch
$ git merge updates

$ git branch -d updates
$ git branch -a

$ git tag mytag
$ git tag --list
$ git tag -d mytag

$ git stash
$ git reflog

$ git remote add origin https://github.com/xiaowukong/demo.git

$ git push -u origin master --tags
```


```
// 获取帮助
$ git help clone
$ git help init

$ git log
$ git log <your_file>
$ git branch new_branch

// 修改本地分支
$ git branch -m my_branch my_rename_branch
$ git branch -d my_branch

$ git branch -b new_branch basedon_branch

// 远程分支列表
$ git branch -r
```

### When to use the Stash
* before checking out a different branch
* before pulling remote changes
* before merging or rebasing a branch

when cloning, Git saves the cloned remotes as "origin"
Local & Remote repository:
	- independent from each other!

Local branches are private for you

#### git reflog 
head@{n}

#### git tag
```
$ git tag v-1.0.0
$ git tag --list
$ git show v-1.0.0
```

```
// -a 
// annotate
$ git tag -a v-1.9-rc2 -m "release version 1.9"
```


The command for updating a particular tag (say, tag "v-1.9-rc2") to a different commit-id (say, commit-id-x) is

```
$ git tag -a v-1.1.0 --force commit_id
$ git tag v-1.1.0 --delete
$ git push origin master --tags
$ git push origin :v-1.0.0
$ git push origin :tag1 :tag2 :tag3
```

### Pushing and Sharing Annoated Tags Only
```
$ git push origin master --follow-tags
```

Ideally, you should only push annotated tags to the remote, and keep lightweight tags for local development to avoid tag clashes

The configuration command for default pushing of annotated tags is:

```
$ git config --global push.followTags true
```

If "push.followTags" is set to true, then pushing of lightweight tags pushes annotated tags as well

The command for checking out a new branch "br-1" at a tag named "xtag" is
```
$ git checkout -b br-1 xtag
$ git stash
```

### 仅仅存跟踪的文件
WIP:
what in progress
```
$ git stash list
$ git stash save "message goes here..."
```

```
$ git stash -u
```

### 未跟踪的文件也保存
### the commands for creating a stash of untracked file
```
$ git stash apply
$ git stash apply stash@{3}
```

### 默认应用最上边的stash
```
$ git stash drop
$ git stash drop stash@{0}
```
### 默认删除最上边的stash
```
$ git stash pop
$ git stash pop stash@{2}
```

```
$ git stash clear
```

### 在stash的基础上创建分支

```
$ git stash branch demobranch
$ git show commit_id
```

### 如果github上创建了分支 而本地没有的话 可以使用git fetch:

```
$ git fetch
```

### 删除远程分支的方法
```
$ git push origin :test
```

### Pulling with rebase

```
$ git checkout -b shared origin/shared
$ git pull --rebase origin shared
```

```
$ git revert HEAD
$ git reset --hard _id
```

------

### create a new repository
```
echo "# ptzhao" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add github https://github.com/a4kz/sth.git
git push -u github main
```

### push an existing repository 

```
git remote add github https://github.com/a4kz/ptzhao.git
git branch -M main
git push -u github main
```

---

### 取消已经提交的文件,当commit后，再push到线上时，也会把线上仓库代码删除__
```
$ git rm --cached somefile.txt
```

### 查看当前分支状态和日志
```
$ git status
$ git log
```

### 查看分支某个文件的日志
```
$ git log myfile.txt
$ git log --oneline
```

### 查看某个提交区间的日志
```
$ git log commit_id_1..commit_id_2 --oneline
```

### 简化显示提交状态
```
$ git status -s
?? => untracked file
A => git add file
M => modified file
```

#### 查看最近的4次提交

```
$ git log -n 4
```

#### 还原到历史中的某个版本

```
$ git checkout commit_id
```


#### 还原某个文件到历史版本

```
$ git checkout commit_id somefile.txt
```


#### 从以前的历史版本中创建新分支

```
$ git branch new_branch_name commit_id
$ git checkout new_branch_name
```

```
$ git checkout -b new_branch commit_id
```

```
$ git revert HEAD // ???
```

```
$ git checkout commit_id
// Checking out a previous commit hash such as <commit-id> is a READ-ONLY operation
```

#### 将暂存区的文件改变为未跟踪的文件, 对已提交的文件不起作用

```
$ git reset myfile
```

#### 只作用于未跟踪的文件

```
$ git clean
$ git clean -n
$ git clean -f
$ git clean -df
$ git clean -xf
```

#### "pull before push"

```
// t: type
// b: length of key
// C: comment
$ ssh-keygen -t rsa -b 4096 -C 'Key generation'
$ ssh-keygen -t dsa
```

```
$ git remote set-url origin URL
```

#### 修改提交密码
```
$ ssh-keygen -p 
```


If your private key has a passphrase and you are not using ssh-agent, then you need to enter your passphrase each time you login using ssh.

```
$ git log --oneline --decorate --graph
// oneline 显示一行
// decorate 添加branch/tag名 ???
// graph 合并图
```

```
$ git diff
$ git difftool
// working directory file VS staging area file
```

```
$ git diff HEAD
$ git difftool HEAD
// working directory file VS committed area
```
```
$ git diff --staged HEAD
// ???
```

#### 已提交的历史某个版本和现在的版本比较
```
$ git diff commit_id HEAD
$ git diff HEAD^ HEAD
$ git diff HEAD~1 HEAD
```

#### 本地与远程文件比较
```
$ git diff master origin/master
$ git diff master origin/master file.name
```

#### 只查看my.file的不同
```
$ git diff -- my.file
```

#### 不同分支的比较
```
$ git diff feature_branch master
```

```
// 分支名称修改
$ git branch -m small-feature bug-hotfix
```

#### 删除本地分支
```
$ git branch -d bug-hotfix
```

#### 如果有未合并的内容，则使用以下强制删除
```
$ git branch -D bug-hotfix
```

#### 创建一个基于master的分支
```
$ git checkout -b new-feature master
```

#### 查看远程分支
```
$ git branch -r
```

```
$ git merge new-feature
$ git merge new-feature --no-ff
```

```
$ git commit --amend --no-edit
$ git commit 
```


#### 提交到线上仓库的代码千万不要amend！！！

```
$ git remote set-url origin git@git.com:kevin/website.git
```
```
$ git pull --rebase <remote-name> <remote-branch>
```

---

### Git Large File Storage
#### 安装
```
$ brew install git-lfs
```

#### 每个仓库都要运行这些语句
```
$ git lfs install
$ git lfs track "*.pdf" "*.psd"
$ git add .
$ git commit -m 'my pdf books'
$ git push origin master
```

---

# 三十分钟完成 Gitlab 搭建安装指南(支持 HTTPS 访问)
#### 2018年05月02日 16:43:51
#### 阅读数：4770
__背景__

由于我们早期使用 phabricator 进行代码管理，但是在使用的过程当中发现和社区的 `github` 使用方式有些不同，所以为了让大伙都习惯 `github` 社区相同的使用风格，所以我们换成了 `gitlab` 作为公司内部的代码管理系统；并且其强大的 `CI/CD` 的方式为后续的持续集成工作打下基础。

__注意__

`Gitlab` 分为 社区版 (`gitlab-ce`) 与 企业版 (`gitlab-ee`)，社区版免费，企业版收费，两个版本的区别参考官方文档：`gitlab-ce` VS `gitlab-ee`；

官方网站安装文档默认是针对 `gitlab-ee` 进行说明的，为了避免不必要的麻烦请直接安装 `gitlab-ce` 版本。

新版本方式 : 此文档针对大于 `Gitlab 10.5` 版本进行说明的，小于此版本的参考其它文档。

__开始安装__

由于官方的方式下载软件包太慢，并且我们是专门购买的一台机器安装 `gitlab` 使用，再加上本人觉得直接下载软件包 *.deb 手动安装方便一些，所以我直接在清华大学开源软件源下载的包进行安装的。

注意：我这里的操作系统版本是 `Ubuntu 16.04` ，最后的那位博客使用的是 `Centos` 方式安装的，最好对照自己的操作系统方式进行博客参考。

__下载安装__

以下通过手动方式安装的，如果希望通过添加软件源的方式添加方便后续的自动更新，可以参考: 清华大学开源文档如何添加 gitlab-ce 软件源。

__下载包文件__

```
wget https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/ubuntu/pool/xenial/main/g/gitlab-ce/gitlab-ce_10.7.2-ce.0_amd64.deb
```

* 开始安装
`dpkg -i gitlab-ce_10.7.2-ce.0_amd64.deb`

* 基础配置
打开 `/etc/gitlab/gitlab.rb` 文件进行基础设置，所有的核心设置均在这个文件中。

__设置外部地址__
```
## GitLab URL
##! URL on which GitLab will be reachable.
##! For more details on configuring external_url see:
##! https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-the-external-url-for-gitlab
external_url 'https://gitlab.xxx.com'
```
注意：如果没有设置以下 https 方式，则需要把地址前面换成 http。

设置 HTTPS 方式
如果想要以上的 https 方式正常生效使用，则需要把 letsencrypt 自动生成证书的配置打开，这样在执行重新让配置生效命令 (gitlab-ctl reconfigure) 的时候会自动给域名生成免费的证书并自动在 gitlab 自带的 nginx 中加上相关的跳转配置，都是全自动的，非常方便。

注意：进行生成证书的时候请预先把域名解析设置完毕，否则会执行配置生效命令失败。
```
################################################################################
# Let's Encrypt integration
################################################################################
 letsencrypt['enable'] = true
 letsencrypt['contact_emails'] = ['caryyu@qq.com'] # This should be an array of email addresses to add as contacts
```

__邮件配置__

很多博客及大多数的情况都推荐使用 postfix 模块进行邮件通知处理；但是我们公司已有邮箱服务器，所以 postfix 并非必须的；所以我这里采用 SMTP 的方式配置邮件服务器来实现通知效果；具体配置参考如下： 


打开 ``/etc/gitlab/gitlab.rb` 配置 SMTP 服务的具体内容如下，我这里采用的邮箱安全端口，点击打开更多配置参考。

### Email Settings
```
 gitlab_rails['gitlab_email_enabled'] = true
 gitlab_rails['gitlab_email_from'] = 'system.notice@qq.com'
 gitlab_rails['gitlab_email_display_name'] = 'gitlab.notice'
 gitlab_rails['gitlab_email_reply_to'] = 'system.notice@qq.com'
 gitlab_rails['gitlab_email_subject_suffix'] = 'gitlab'
```

```
### GitLab email server settings
###! Docs: https://docs.gitlab.com/omnibus/settings/smtp.html
###! **Use smtp instead of sendmail/postfix.**

 gitlab_rails['smtp_enable'] = true
 gitlab_rails['smtp_address'] = "smtp.qq.com"
 gitlab_rails['smtp_port'] = 465
 gitlab_rails['smtp_user_name'] = "system.notice@qq.com"
 gitlab_rails['smtp_password'] = "xxxxx"
 gitlab_rails['smtp_domain'] = "qq.com"
 gitlab_rails['smtp_authentication'] = "login"
 gitlab_rails['smtp_enable_starttls_auto'] = true
 gitlab_rails['smtp_tls'] = true
```



利用以下命令进行测试邮箱配置是否正确，测试使用方式更多参考：如何测试
```
gitlab-ctl console
irb(main):002:0>Notify.test_email('xx@qq.com', '邮件标题', '邮件正题').deliver_now
```

__配置生效__

当 `/etc/gitlab/gitlab.rb` 配置发生改变的时候想要生效必须执行以下命令:

`gitlab-ctl reconfigure`

以上的操作执行完毕并且成功之后，这个时候就可以直接在浏览器中打开了。

__注意__：如果依然无法访问的话，请检查主机防火墙或云服务安全组中的 80 或 443 端口是否正常开放，切记！切记！切记！

__最后__
此篇主要只涉及安装与基础配置的部分，如果需要查看更多包括：忘记 `root` 密码重置、备份与恢复等；可以点击这篇博客（如何安装与使用 Gitlab）进行查看，此篇主要参考了这位作者的博客内容，并根据自己的操作进行整理，感谢这位作者的付出！

__安装时报错__
```
initdb.bin: invalid locale settings; check LANG and LC_* environment variables
```

The issue solved when i used the following commands
```
LC_ALL="en_US.UTF-8"
LC_CTYPE="en_US.UTF-8"
```
