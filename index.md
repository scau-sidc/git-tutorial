<div class="hidden">如果你看到这行字, 说明打开的方式不太对. 我们墙裂建议你观看<a href="http://scau-sidc.github.io/git-tutorial/">用 Bootstrap 渲染的页面</a></div>
<div class="alert alert-info">
<strong>如果你看到这个蓝色的小框框</strong> 那就对了. 大家好我是小框框, 肩负着插入和旁白的职责 (｀･ω･)ノ
</div>

# 超科学的git和Github讲座

> @author ![](https://avatars0.githubusercontent.com/u/2285039?v=2&s=20) cuter44  
> @version 3.0.0-build20141028  
> @license ![](https://i.creativecommons.org/l/by/3.0/cn/80x15.png) CC 3.0 BY CN  
> @acknowledge [Github](https://github.com/), [StackEdit](https://stackedit.io/‎), [SCAU-SIDC](https://github.com/scau-sidc)  
> @source hosted on [Github](https://github.com/scau-sidc/git-tutorial/)    

## 0.

通常来说这个时候应该说下 _git是什么_, 不过为了以行动表达对国产垃圾教材的鄙视, 我决定啥都不写有兴趣的话自己翻[维基](http://zh.wikipedia.org/wiki/Git)去. 现在, 只需要将 git 理解成 **一个可以在多人环境下随时保存和合并源代码的工具** 即可.  

还有 Github, Github 就是依托 git 所建立的代码托管平台/社区, 如果非要做个对比的话它有点像 Google Code 和 SourceForge. 你可以在那里四处乱逛, 寻找自己想要的代码, 吐槽别人; 或者直接脑洞大开自己写个软件出来, 搞不好还会受到路过大神的加持...

然后呢, 我们的目标是, 写一个"萌萌哒的""一个一两个钟能学会, 并且一两个钟之后还想回头看的教程". 在这个教程中我们会以一种实践的态度完成对git的学习, 各位一定要全力地去do哦 ^▽^

<div class="alert alert-info">比如这个教程就是托管在Github上面的, 如果有幸能接收到<a href="https://github.com/scau-sidc/git-tutorial/issues">小纸条</a>的话我会很开心的~</div>

<div class="alert alert-info">啊对了这里顺便推荐一个烂片, <i>遇见未来 Next</i> (IMDb:<a href="http://www.imdb.com/title/tt0435705/">tt0435705</a> | <a href="http://movie.douban.com/subject/1793909/">豆瓣↗</a>). 凯奇大叔演的. 据说只有程序猿能看懂, 当中演示了分支推衍和回滚等(蓝星人看了会Σ(°д°|||) 程序猿看了会(.ㅍ_ㅍ)的)烂梗, 而这些基本可以类比于 git 的原理模型. <del>有兴趣</del>实在闲得慌的可以去观赏下.</div>

## 1. 首先, 我们需要一个工具

那当然就是在自机部署一个 git 了.  

### on Linux

一个命令搞掂:  

	apt-get install git

, 或者等价的包管理器指令(yum, pacman 等)

### on Windows
这里是适合普通人的操作步骤:  

作为一个有强烈<del>责任心</del>精神洁癖的软件攻城狮, 我会墙裂推荐从官方软件源获得软件:

http://git-scm.org/

然后按蓝星人的风俗一路 Next 下去, 除了这些点: 

![](./asset/setup-4.png)  
建议这么点, 理由是我有精神洁癖   

![](./asset/setup-6.png)  
建议这么点, 理由是这样对蓝星人友好  

![](./asset/setup-7.png)  
建议这么点, 理由是: 现在除了Microsoft Notepad以外已经没有哪个编辑器不能 handle \r\n 这个问题了, 这样可以避免引入污染.

### ...and Github
这里先说明一点, git是一种对等的分布式仓库系统, aka. 它不是非要一个服务器端才能互相交流. 它支持多种通信协议 包括 `git://`, `ssh://`, `https://`, 甚至`file:///`. 换句话说, 只要能够读写对应的文件, 任何一台机器/存储设备都可以作为远程仓库, 甚至不必在上面安装 git .

辣么为啥要有 Github 呢? ...这问题谁也说不清楚. 其中一点或许是他实践了开源精神, 将代码作为交流话题, 并使他看得见摸得着, 看到代码推动世界的前进甚至亲手影响世界... <del>起码比刷微博来得有意义.</del>
不对我要说的不是这个!! ≧□≦"

Github 除了有作为 git 的远程仓库, 提供代码可视化, 版本可视化之外, 还集成了问题追踪(Issue), 代码速记(Gist), Pull Request 等有效提升程序猿战斗力的工具. 反正...用过都说好...

废话了这么多总该去注册个 Github 帐号吧? 快去!! → https://github.com/join
然后找到组织→ https://github.com/scau-sidc , 加不进去对吧? 嗯这坑爹的至今都没有站内信功能, 所以你只能私下找老邝或者副主任等老油条把你拉进去了. 

<div class="alert alert-warning"><strong>注意</strong> 必须提前做好这一步, 因为下一步实验会用到里面的仓库, 不加进来的话就只能干瞪眼了 (.ㅍ_ㅍ)</div>

英文界面不会撸? 可以去看看 [Github官方的新手教程](https://help.github.com/categories/bootcamp/) (←还是英文的), 或者在本教程的稍后部分也会教授一点.

## 2. 心に刻んだ夢を放て!

![](./asset/72f5bfea-s.jpg)

<div class="alert alert-info">标题出自炮姐OP, 题图出自机巧少女, 图片仅供参考.</div>

当然不可能立即就碉堡到这种程度↑咯 (´・ω・｀)  

对于 Windows 来说, 安装的 git 会附带一个 gui , 可以从开始菜单, 文件管理器的上下文菜单 或者 `git gui` 来启动它. 简单起见我们将从这里入手, 对应的命令行指令使用 `行内引用` 标示, 详细的参数请自行 `git help`.

<div class="alert alert-success">git 是基于命令行的, 这意味着你可以自己安装甚至开发各种高大上酷炫狂拽屌的 GUI, 比如 <a href="http://git-scm.com/downloads/guis">官方列出的那些</a>. 但本喵在实际使用了几个之后觉得还是原生的那个最诺基亚. </div>

<div class="alert alert-info">首先, 请结合自己的使用习惯准备一个目录专门放各种 project , 通常我们将它称之为 工作空间(Workspace), 后文我们用 ${ws} 指代这个目录</div>

假如你不是在一个本地仓库中启动 Git GUI 的话他会弹出下面这个框框:  
![](./asset/gui-1.png)  
意思很明确, 你要新建(`init`)呢? 还是克隆(`clone`)呢? 还是打开呢?

这里咱们选克隆, 然后填入以下参数:  

	Source Location: https://github.com/scau-sidc/git-tutorial.git  
	Target Location: ${ws}\git-tutorial

<div class="alert alert-info">假如你是在一个空目录里启动 Git GUI 并准备进行 clone, 它会默认你想要 clone 到这个目录, 于是不显示第二个输入框</div>

完事之后会变成以下的样子(略微会有些不同, 这种细节不用在意 (･ω･｀)っ彡/ ):  
![](./asset/gui-3.png)  

红黄绿的很好看对吧? 时间关系我就不画箭头什么的了...  
<span class="bg-danger">左上角红色的部分</span> 表示 工作目录(Working Copy), 也就是你以传统方式写代码时(aka. 不使用 git ), 打开项目文件夹会看到的文件集合. 仅当你新建/修改/删除文件时, 他们会被列出在这里.  
<span class="bg-success">左下角绿色的部分</span> 表示 Index(可以理解成缓存区, 目前没有公认的中文翻译), 是你在缓存改动准备用于提交的地方, 关于<b>提交</b>的概念将在后文详述.  
<abbr title="Working Copy">WC</abbr> 和 Index 中的文件图标是可以点击的(注意我说的是图标= =b). WC 中的文件被点后会进入 Index, 意思是你缓存( `stage` )这个改动; Index 中的文件被点后会进入 WC, 意思是你放弃缓存这个文件的改动( `reset --mixed` );  
  
<span class="bg-warning">右上角黄色的部分</span> 表示 差异(diff) 仅在你在点击 WC 或者 Index 中的文件名时(注意我说的是文件名= =b), 这个区域会列出这个文件改动了哪些行.  
右下角是用来写 <b>提交说明</b> 这个也在后文讲.  

## 3. 摩擦! 摩擦!!

嗯...总之先从 菜单栏 的 `版本库(repository)` > `图示所有分支的历史(Visualize all barnches history)`, 然后会弹出一个新的窗口. 这货叫做 gitk , 大概长得像下面的样子: 

![](./asset/gitk-1.png)  

顶部那个就是整个仓库的历史记录(术语叫做`版本树`)了, (默认会)按时间顺序倒序排列. 现在看到的是一条直线, 但随着项目的多人合作这个它会逐渐产生分叉和合并. 这条线上的每一个小圆点表示一个 `提交(commit)`, 各种小圆点/小标签都有不同的含义:

* <span style="color:yellow;">黄色的小圆点 ● </span> 表示 `HEAD`, 也就是当前所处的提交点, 或者说(打游戏时)目前读出的存档点.
* <span style="color:blue;">蓝色的小圆点 ●</span> 是已经存入数据库的提交, 这些点是不能修改的(叶结点除外, 这个之后讲)
* <span style="color:red;">红色的小圆点 ●</span> 是当前 工作目录(WC) 发生的变更, 仅在修改/删除过内容时出现.
* <span style="color:#00ff00;">绿色的小圆点 ●</span> 表示缓存区的变更, 仅在缓存区有内容时出现, 且出现在红点和黄点之间.
* 至于点与点之间的线就不用我解释了吧 →_→

而你写的代码或者别的什么东西就是经过 <span style="color:red;">红点</span>→<span style="color:green;">绿点</span>→<span style="color:yellow;">黄点</span>/<span style="color:blue;">蓝点</span> 这个过程逐步进化成整个版本树的.  
每个提交都有一个唯一的 <strong>SHA1 ID</strong>, 这个值是通过提交内容等一堆因子算出来的, 理论上全球唯一.

* 还有 <span style="background-color:#00ff00; border:1px solid;">绿色的小标签</span> 表示 `分支(branch)` , 其中有些带有 <span style="background-color:#ffd8aa; border:1px solid;">嫩肉色前缀</span> 的表示 `远程分支(remote branch)`. 两者的区别是前者是由你建立和管理的, 可以随便操作, 后者是别人建立和管理的, 对远程分支的操作需要经过分支主人的同意.  
* 成熟的项目还会有 <span style="background-color:yellow; border:1px solid;">黄色的小标签</span>, 它叫做 `tag` 或者 `里程碑(milestone)`, 通常会写着类似 <span style="background-color:yellow; border:1px solid black;">1.0.0</span> 的版本号, 嗯这是给大牛发行用的, 小朋友没事不要玩这种危险的东西. (‾w‾ )  

那么这个版本树的存在意义是什么呢? 首先请将它想象成一个 有向无环图 (数据结构学得不好的同学请想象成 有向链表 ‾ω‾b ). 那么每一个 ● 提交 都是这个图的节点. 而每一个 <span style="border:1px solid black;">分支/tag</span> 可以想象成指向这个节点的指针/引用. 通过将指针随便乱指(大误), 你可以读出任意一个节点的完整代码然后加以修改. 这就跟打游戏时的S/L大法一样bug. (｡・ω´・)っ  
不过呢, 如果只是用版本树来开挂那也太low逼了(因为现在随便一个现代编辑器都有按时备份的功能). gitk或者说版本树本身还提供额外的信息, 比如说...看到提交记录里的邮件地址和时间了吗? 合作编程时被人捣乱? No problem! 除了能用 git 回滚之外你还能通过提交记录找到凶手然后冲过去揪住那人的衫领打他个半死...

<div class="alert alert-warning">虽然现实很残酷, 不过, 看不懂版本树的人...会被同伴像垃(le)圾(se)一样抛弃的哦~</div>

<div class="alert alert-info">那么版本树存在哪儿呢? 打开 `${ws}\git-tutorial\.git` , 这是一个隐藏文件夹, 下面还有n个子文件夹, 四处打开看看? 切记不要乱删东西啊.. </div>

## 4. 挖掘! 挖掘!!
呃...我们还是来做实验吧! ヾ(*ΦωΦ)ﾉ︵◇  

首先我必需假定你们已经完成上述步骤了, 没完成的按前文 HINT 真的就只能干瞪眼.  
实验内容依然是毫无新意的订外卖...

### 提交

1. git gui 打开前文拷贝回来的仓库.
2. `分支(branch)` > `新建(create...)` > (名字里面随便输点什么, 我建议用你们的Github id, 这样可以避免重复, 其余默认即可). > 新建
3. `版本库(repository)` > `Explorer Working Copy` > (打开了文件浏览器, 显示的是这个项目的根目录) > 打开 experiment 文件夹
4. 随便挑个你喜欢的餐馆菜单, 打开, 点个餐然后保存.
5. 回到 git GUI > `重新扫描(Rescan)` > (看到 WC 里有个很醒目的列表项?) > 将它缓存到 Index > 点 `提交(commit)` > (弹框!! 要先写提交记录才能提交!!)
6. 焦点到右下方的`提交描述(Commit Message)` > 写点什么, 比如 `${name}点了${dish}` , name=自己的名字, dish=餐的名字. > 再次点 `提交(commit)` > (弹框!! 你是谁!?)
7. `编辑(edit)` > `选项(option)` > (弹一个大框出来) > `用户名(User Name)` `Email Address` 理论上可以随便填, 但现在请填写你在Github的id和email.  > `保存` 
   <div class="alert alert-info">细心的小伙伴会发现... Σ(ﾟДﾟ；≡；ﾟдﾟ)咦怎么有两列!? 区别是左边的(仓库配置)仅作用于当前仓库, 右边的(全局配置)作用于所有仓库, 仓库配置高于全局配置.</div>
8. 再点 `提交(commit)` > (终于交上去了...)
9. 打开 gitk 看看版本树变成怎样了?

有没有一种<del>荡气回肠</del>傲娇的感觉? 事实上诸如 代码要留名 提交有理由 都是良好的软件工程实践, git 以一种还算友好的方式督导你完成这些工作, 习惯了就好.

<div class="alert alert-warning">虽然现实很残酷, 不过, 不好好写提交记录的人...会被同伴像垃(le)圾(se)一样抛弃的哦~</div>

好吧来分步解释:

1. Step 1 不解释
2. Step 2 创建分支
  * 先来解释下分支的意义: 你可以将分支理解成代码界的平行世界, 每个独立的分支等于一个独立的环境, 里面含有分支前的代码的镜像. 你可以在分支这个封闭空间里随意演绎, 而(在与其它分支合并前)不受到其他分支的干扰, 也不会干扰到别的分支. 
  * 所以为什么要新建分支呢? 正所谓一山不能容二虎, 当两个独立意识同时影响一个世界时, 那个世界...应该会爆掉吧?  
3. Step 3
4. ...和 Step 4 模拟了实际工作时对代码的修改
5. Step 5 (试图)将变更沿着 WC → Index → commit 移动, 就如我们在前文提及的那样.
   当然在写代码的过程中可以进行多次的 WC → Index, 在提交之前, 多个 Index 会以幂等的方式合并, 不过这在大多数情况下没什么意义...
   注意仔细甄别要提交的内容, 有些会对强迫症患者造成伤害的东西(参见下面的红色框框)是不能交上去的. 这里介绍两种一劳永逸的方法: .gitignore
   <div class="alert alert-danger">git 不会自动地/定时地提交更改, 你自己也不要试图实现这种功能. 因为版本库都有"提交了就删不掉"的特性, 所以例如写到一半根本过不了编译的源代码啊, 程序运行日志啊, 编译时产生的中间文件啊, 连接数据库的帐号和密码啊, 果照啊(喂!), 小电影啊(喂喂!!)之类的东西要是一不小心提交上去的话...会死人的...</div> 