
<div class="alert alert-info">
test...test 啊很好可以使用 Bootstrap   
注意这些小框框的提示哦, 里面会夹杂很多有用的或者没用的吐槽.
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
![](./asset/main-1.png)  
意思很明确, 你要新建(`init`)呢? 还是克隆(`clone`)呢? 还是打开呢?

这里咱们选克隆, 然后填入以下参数:  

	Source Location: https://github.com/scau-sidc/git-tutorial.git  
	Target Location: ${ws}\git-tutorial

<div class="alert alert-info">假如你是在一个空目录里启动 Git GUI 并准备进行 clone, 它会默认你想要 clone 到这个目录, 于是不显示第二个输入框</div>

完事之后会变成以下的样子(略微会有些不同, 这种细节不用在意 (･ω･｀)っ彡/ ):  
![](./asset/main-3.png)  

红黄绿的很好看对吧? 时间关系我就不画箭头什么的了...  
<span class="bg-danger">左上角红色的部分</span> 表示 工作副本(Working Copy), 也就是你以传统方式写代码时(aka. 不使用 git ), 打开项目文件夹会看到的文件集合. 仅当你新建/修改/删除文件时, 他们会被列出在这里.  
<span class="bg-success">左下角绿色的部分</span> 表示 Index(可以理解成缓存区, 目前没有公认的中文翻译), 是你在缓存改动准备用于提交的地方, 关于<b>提交</b>的概念将在后文详述.  
<abbr title="Working Copy">WC</abbr> 和 Index 中的文件图标是可以点击的(注意我说的是图标= =b). WC 中的文件被点后会进入 Index, 意思是你缓存( `stage` )这个改动; Index 中的文件被点后会进入 WC, 意思是你放弃缓存这个文件的改动( `reset --mixed` ); 
<span class="bg-warning">左上角黄色的部分</span> 表示 差异(diff) 仅在你在点击 WC 或者 Index 中的文件名时(注意我说的是文件名= =b), 这个区域会列出这个文件改动了哪些行.
右下角是用来写 <b>提交说明</b> 这个也在后文讲.