# 一、Git 常用命令实战

| 命令                              | 作用           |
| :-------------------------------- | :------------- |
| `git config user.name 用户名`     | 设置用户签名   |
| `git config user.email 邮箱`      | 设置用户签名   |
| `git init`                        | 初始化本地库   |
| `git status`                      | 查看本地库状态 |
| `git add 文件名`                  | 添加至暂存区   |
| `git commit -m "日志信息" 文件名` | 提交至本地库   |
| `git reflog`                      | 查看历史记录   |
| `git reset --hard 版本号`         | 版本穿梭       |

### 1.1 设置用户签名

1）基本语法

```bash
git config --global user.name 用户名
git config --global user.email 邮箱
```

2）案例实操
全局范围的签名设置
![image-20210917001235229](https://i.loli.net/2021/09/17/62JueaM9ByrmHdX.png)

说明：

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的

<mark>Git 首次安装必须设置一下用户签名，否则无法提交代码</mark>

:bangbang: 注意：这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系

### 3.2、初始化本地库

1）基本语法

```bash
git init
```

2）案例实操

![image-20210917203400924](https://i.loli.net/2021/09/17/QBPNgHCUzGOiJuy.png)

### 3.3、查看本地库状态

1）基本语法

```bash
git status
```

2）案例实操

![git status](https://i.loli.net/2021/09/17/b645MnGSFxRyhaQ.gif)

新增文件前

![image-20210917204804510](https://i.loli.net/2021/09/17/4xCVHGPLgjXbB1F.png)

新增文件后

![image-20210917204858689](https://i.loli.net/2021/09/17/IqK6GEc92hYx7HF.png)

###  3.4、添加暂存区

1）基本语法

```bash
git add 文件名
```

2）案例实操

红色表示仍在工作区，修改尚未被追踪；绿色表示已添加至暂存区，修改被追踪

![image-20210917205319556](https://i.loli.net/2021/09/17/DnfmIo3KZlt5zJ4.png)

使用命令，删除暂存区该文件（只是删除暂存区，不影响工作区）

```bash
git rm --cached hello.txt
```

![image-20210917205546165](https://i.loli.net/2021/09/17/uJS8Gp3CazAKU7l.png)

### 3.5、提交至本地库

1）基本语法

```bash
# -m 表示添加一个版本日志信息，不写此参数也会打开日志信息的文件框。一般带参数
git commit -m "日志信息" 文件名
```

2）案例实操

正常操作

![image-20210917210542226](https://i.loli.net/2021/09/17/KNfMvCTkE3YQxdj.png)

无`-m`参数时

![image-20210917210109185](https://i.loli.net/2021/09/17/bvTfga13wtuSUhq.png)

如果强制退出

![image-20210917210156460](https://i.loli.net/2021/09/17/XIx7L3lTW9FcBtP.png)

### 3.6、修改文件

案例实操

![image-20210917211143162](https://i.loli.net/2021/09/17/o2p7dO4F9A5VDjJ.png)

git 里是按照行维护文件的，所以修改内容其实就是之前的行删除，修改过后的行添加进来

因此在`commit`之后提示信息`1 insertion(+), 1 deletion(-)`

### 3.7、历史版本

#### 查看历史版本

1）基本语法

```bash
# 查看精简版本信息
git reflog
# 查看详细版本信息
git log
```

2）案例实操

![image-20210917211945690](https://i.loli.net/2021/09/17/p2mvTbZuEqVkYB9.png)

#### 版本穿梭

1）基本语法

```bash
git reset --hard 版本号
```

2）案例实操

![image-20210917212348218](https://i.loli.net/2021/09/17/nBw6OEL9liyMe7d.png)

文件验证当前版本号

![image-20210917212941200](https://i.loli.net/2021/09/17/vMYXFVyWo6PNOzf.png)

Git 切换版本，底层其实是移动的 HEAD 指针，具体原理如下图所示

![image-20210917213424162](https://i.loli.net/2021/09/17/5GQRnhD8XijVZuy.png)

![image-20210917213247141](https://i.loli.net/2021/09/17/CVdReJPu5YMTmHQ.png)

![image-20210917213333350](https://i.loli.net/2021/09/17/oU5ORWqvghNCcTi.png)

![image-20210917213616760](https://i.loli.net/2021/09/17/6jGfxUmrERZSV9h.png)

### 4.1、什么是分支

在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支。使用分支意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支的时候，不会影响主线分支的运行。对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本（分支底层其实也是指针的引用）

![image-20210917213935209](https://i.loli.net/2021/09/17/AVwpC1ZLzmOlEUg.png)

### 4.2、分支的好处

同时并行推进多个功能开发，**提高开发效率**

各个分支在开发过程中，如果某一个分支开发失败，**不会对其他分支有任何影响**。失败的分支删除重新开始即可

### 4.3、分支的操作

| 命令                  | 作用                       |
| :-------------------- | :------------------------- |
| `git branch 分支名`   | 创建分支                   |
| `git branch -v`       | 查看分支                   |
| `git checkout` 分支名 | 切换分支                   |
| `git merge` 分支名    | 把指定的分支合并到当前分支 |

#### 创建分支、查看分支

1）基本语法

```bash
git branch 分支名
git branch -v
```

2）案例实操

![image-20210917214653546](https://i.loli.net/2021/09/17/PVOR9ZjmIqkr4cv.png)

#### 切换分支

1）基本语法

```bash
git checkout 分支名
```

2）案例实操

![image-20210917215246415](https://i.loli.net/2021/09/17/AR9NuTBG2UweEnb.png)

#### 合并分支

1）基本语法

```bash
git merge 分支名
```

2）案例实操

**正常合并**

![image-20210917215908842](https://i.loli.net/2021/09/17/UcwRJu78Kmvod4k.png)

**冲突合并**

冲突产生的原因：合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改。Git无法替我们决定使用哪一个。必须人为决定新代码内容

![image-20210917220923478](https://i.loli.net/2021/09/17/gcnCSJKtNqrokIQ.png)

解决冲突

![image-20210917221121233](https://i.loli.net/2021/09/17/mU3Y9JodyTpV7nB.png)

![image-20210917221239011](https://i.loli.net/2021/09/17/S6OrkKeFsCymWcB.png)

![image-20210917222018377](https://i.loli.net/2021/09/17/iMQfWOwkSH8ujh2.png)

#### 创建分支和切换分支图解

![image-20210917221451896](https://i.loli.net/2021/09/17/6WNlEc9FbaJmhkv.png)

![image-20210917221515718](https://i.loli.net/2021/09/17/OKwIG2BvZC7mVjl.png)

master、hot-fix 其实都是指向具体版本记录的指针。当前所在的分支，其实是由 HEAD 决定的。所以创建分支的本质就是多创建一个指针

- HEAD 如果指向 master，那么我们现在就在 master 分支上
- HEAD 如果指向 hotfix，那么我们现在就在 hotfix 分支上

所以切换分支的本质就是移动HEAD指针

## 5、Git 团队协作机制

### 5.1、团队内协作

![image-20210917222216595](https://i.loli.net/2021/09/17/HWlevFmCKdRju6V.png)

### 5.2、跨团队协作

![image-20210917222441407](https://i.loli.net/2021/09/17/gvmsB4Rn7xYfc9A.png)

## 6、GitHub 操作

- GitHub 官网：[https://github.com/](https://github.com/)

PS：全球最大同性交友网站，技术宅男的天堂，新世界的大门，你还在等什么？

| 账号                 | 姓名       | 验证邮箱                     |
| :------------------- | :--------- | :--------------------------- |
| `atguiguyuebuqun`    | `岳不群`   | `atguiguyuebuqun@aliyun.com` |
| `atguigulinghuchong` | `令狐冲`   | `atguigulinghuchong@163.com` |
| `atguigudongfang1`   | `东方不败` | `atguigudongfang1@163.com`   |

### 6.1、创建远程仓库

![image-20210917223235275](https://i.loli.net/2021/09/17/iP9EZnU81O3wGYB.png)

![](https://i.loli.net/2021/09/17/gLQzrsRiN2Cj6Fe.png)

### 6.2、远程仓库操作

| 命令                               | 作用                                                     |
| :--------------------------------- | :------------------------------------------------------- |
| `git remote add 别名 远程地址`     | 起别名                                                   |
| `git remote -v`                    | 查看当前所有远程别名                                     |
| `git clone 远程地址`               | 将远程仓库的内容克隆到本地                               |
| `git pull 远程地址别名 远程分支名` | 将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并 |
| `git push 别名 分支`               | 推送本地分支上的内容到远程仓库                           |

#### 创建远程仓库别名

1）基本语法

```bash
git remote -v
git remote add 别名 远程地址
```

2）案例实操

![image-20210917225451875](https://i.loli.net/2021/09/17/PfZBknlC8RjHvxV.png)

#### 推送本地分支到远程仓库

1）基本语法

```bash
git push 别名 分支
```

2）案例实操

由于 GitHub 外网的特殊原因，会有网络延迟，等待时间可能较长，属于正常现象。可能要多尝试几次，需要点耐心。当然你有工具除外

```bash
git push git-demo master
```

如果本地还没有过 SSH 免密登录操作（下面内容会详细介绍），则在执行命令后会弹出一个`Connect to GitHub`的提示框

![image-20210918224448045](https://i.loli.net/2021/09/18/27XoOIwArYdnhyE.png)

点击`Sign in with your browser`后会自动打开系统默认浏览器

如果你的 GitHub 尚未进行过任何 Git 相关授权，则会给出确认授权提示信息，点击`Authorize GitCredentialManager`进行授权即可

![image-20210918231341801](https://i.loli.net/2021/09/19/sOguJ7GYApZUiLS.png)

接着会提示授权成功（如果在此之前已经对`Git Credential Manager`进行过授权，则直接提示此信息）

![image-20210918224627107](https://i.loli.net/2021/09/18/clQsuFdDfemyxzR.png)

成功推送本地分支至远程库

![image-20210918224403240](https://i.loli.net/2021/09/18/ApuMYyt5S73LF6E.png)

**凭据管理器**

在上述操作过程中，点击`Authorize GitCredentialManager`进行授权后，在 GitHub 设置页面的`Application`选项—`Authorized OAuth Apps`中可以查看到 `Git Credential Manager`的授权信息

![image-20210918231735259](https://i.loli.net/2021/09/18/QgZLxhAM5fzis6n.png)

在上述过程前，本地凭据管理器中还没有任何身份凭证信息（没有 Git 和 GitHub 相关的凭据信息）

![image-20210918230512316](https://i.loli.net/2021/09/18/hBtO3EZJRnmWYeC.png)

执行过上述命令等操作后，本地凭据管理器中会出现 Git 相关凭据信息

![image-20210918233953904](https://i.loli.net/2021/09/19/nfe4SVwFj39JTuB.png)

#### 拉取远程仓库到本地

1）基本语法

```bash
git pull 别名 分支
```

2）案例实操

![image-20210918234422490](https://i.loli.net/2021/09/19/lqVRcoryfCZnMeg.png)

#### 克隆远程仓库到本地

1）基本语法

```bash
git clone 远程库地址
```

2）案例实操

首先获取需要克隆的远程库地址

![image-20210918235159899](https://i.loli.net/2021/09/18/V1s3vjWHUAiyIC2.png)

由于`workspace`下面已经存在一个同名的仓库地址，所以直接在`workspace`中键入命令会有错误提示信息

![image-20210918235519853](https://i.loli.net/2021/09/18/MIc5GEnqgrZsWBe.png)

这是因为，`clone`命令默认帮我们创建的一个远程仓库名称同名的文件夹，所以这里我删除了`git-demo`目录

![image-20210918235857263](https://i.loli.net/2021/09/19/LZYvpoBcJR56VlA.png)

小结：`clone` 会做如下操作

- 1、拉取代码
- 2、初始化本地仓库
- 3、创建别名（默认`origin`）

### 6.3、团队内协作

如果项目之外成员想要将自己编写的代码推送至远程库，则会提示`unable to access...403`

![image-20210919002334885](https://i.loli.net/2021/09/19/URnavcD49XsEkwY.png)

要想获取推送的权限，则需要该项目管理员对该成员进行邀请，将其添加至该项目中

1）邀请合作者，输入用户名，复制地址并发送给合作者

![image-20210919001646877](https://i.loli.net/2021/09/19/yHmSVrhQN5eFZow.png)

![image-20210919001732944](https://i.loli.net/2021/09/19/r6yLWmFxQVogejR.png)

![image-20210919001847491](https://i.loli.net/2021/09/19/p4qvjwdhcrSXM2R.png)

2）合作者访问该链接，点击接受邀请，可以在其账号上看到该远程仓库

- [https://github.com/atguiguvueyue/git-demo/invitations](https://github.com/atguiguvueyue/git-demo/invitations)

![image-20210919002022667](https://i.loli.net/2021/09/19/fxEsGzic2mgAJRt.png)

![image-20210919002239871](https://i.loli.net/2021/09/19/R9O3bTxLo7HfBw6.png)

接下来，就可以通过`git`命令对远程库进行克隆、拉取、提交、推送等操作了

### 6.4、跨团队协作

1）合作者视角

点击`Fork`，将其他项目“叉”到自己账号上

![image-20210919003412417](https://i.loli.net/2021/09/19/TzkfoeEVc5wi67d.png)

自己账号上就有了该项目，可以清楚地看到该项目`forked from xxx`，即可对代码进行修改

![image-20210919003500235](https://i.loli.net/2021/09/19/YzAaK6L4o8rx3Jw.png)

修改代码后，点击`Pull requests`—`New pull request`，发起拉取请求

![image-20210919004019396](https://i.loli.net/2021/09/19/UDezhHG5E7v93r1.png)

查看修改内容，点击`Create pull request`，创建拉取请求

![image-20210919004334829](https://i.loli.net/2021/09/19/rG3BDcENxJMot4R.png)

填写请求信息及评论内容，点击`Create pull request`

![image-20210919004505828](https://i.loli.net/2021/09/19/J8hZK1oVE2Hi9Gm.png)

创建完成

![image-20210919004830149](https://i.loli.net/2021/09/19/9kpVQfbAGz2gRL5.png)

2）项目管理员视角

可以在该项目中查看到`Pull requests`有一条新的记录，可以点击下方提交信息进行查看

![image-20210919005217558](https://i.loli.net/2021/09/19/nItWOHxSi9kleV5.png)

想要看到合作者修改的具体内容，可以点击提交记录进行查看

![image-20210919005303909](https://i.loli.net/2021/09/19/dOGxz6gusfM4onA.png)

![image-20210919005442954](https://i.loli.net/2021/09/19/54QENAfDJj3ikSl.png)

同时，可以对拉取请求进行审查和评论

![image-20210919005558618](https://i.loli.net/2021/09/19/385yrHgBX1uvPYR.png)

最后，审查通过就可以对拉取请求进行合并了，点击`Merge pull request`进行合并

![image-20210919005831430](https://i.loli.net/2021/09/19/K4EfVpQ1BvhwSFL.png)

点击`Confirm merge`，确认合并

![image-20210919005854745](https://i.loli.net/2021/09/19/ZYHrCAUJQvED93K.png)

合并成功之后，项目成员就可以看到修改的相关内容了

### 6.5、SSH 免密登录

1）基本语法

```bash
# -t指定加密算法，-C添加注释
ssh-keygen -t rsa -C 描述
```

2）案例实操

**本地生成 SSH 密钥**

键入命令，连敲三次回车即可

![image-20210919011352497](https://i.loli.net/2021/09/19/puY46lMsi2GkbKj.png)

进入`~/.ssh`目录，复制公钥信息

![image-20210919011953686](https://i.loli.net/2021/09/19/fZvNMLo1p7CGWIJ.png)

**GitHub 上添加公钥**

未添加任何公钥之前，`Code`—`SSH`会有警告提示信息，表示目前 SSH 方式是没有权限的

![image-20210919014241528](https://i.loli.net/2021/09/19/Zl6xeMd7qnV5UPW.png)

在 GitHub 的`settings`—`SSH and GPG keys`中，点击`New SSH key`添加一个公钥

![image-20210919012856831](https://i.loli.net/2021/09/19/pbSW2LukQAz5Cqj.png)

将`id_rsa.pub`即公钥信息粘贴至`Key`中，`Title`随意，点击`Add SSH key`进行添加

![image-20210919013103108](https://i.loli.net/2021/09/19/J1FOEVfW5bI6Tyl.png)

出现下列信息，说明添加成功

![image-20210919013731928](https://i.loli.net/2021/09/19/g1bZS56xRVdQIsm.png)

**验证 SSH免密登录 是否可用**

进入`git-demo`项目，点开`Code`—`SSH`，发现已经没有警告提示信息了，表示可用

![image-20210919014010529](https://i.loli.net/2021/09/19/DEvC6qPBAMS32ra.png)

复制 SSH 协议地址，使用`clone`命令克隆到本地，键入`yes`即可

![image-20210919015207022](https://i.loli.net/2021/09/19/Be8LsuUKFtbGf2j.png)

接下来就是修改内容、添加暂存区、提交本地库、推送远程库的操作了

这时候我们发现已经不再弹出登录授权的提示信息，就可以推送过去了

![image-20210919015907992](https://i.loli.net/2021/09/19/shjpkZWQNRwH9Gg.png)

查看远程库历史版本信息，确认推送成功

![image-20210919020511037](https://i.loli.net/2021/09/19/nla3Lbq2v5DWNcE.png)

至此，SSH 免密登录配置成功！