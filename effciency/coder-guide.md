# 程序员效率指南
几条建议

## 尽量不要用windows进行开发
除非你只用dotnet开发软件，不然osx/ubuntu会是更好的开发平台。太多太多优秀的工具在osx/ubuntu下可以一键安装，在windows下却不得不花费超过一个甚至几个数量级的时间去安装，更别提有的工具windows压根没有替代品。

如果不认可Rule 1，那么直接可以跳过下面的文字走人。

## 尽量使用mbp
我在「能花钱的，就不要花时间」文中已经强调，有条件买15"高配的就不要买15"低配，有条件买15"低配的就不要买13"（Retina/ssd版本是必备）。作为一个开发者，你实在应该在开发工具上对自己好些 —— 毕竟你跟她相处的时间比跟女盆友/老婆多多了！

如果实在觉得mbp太贵 [1]，可以考虑一个15"轻薄的本子装ubuntu。

mbp的好处不在于逼格 [2]，而在于优秀的硬件 + 优秀的Unix兼容的软件。retina屏，超长的电池续航（相比PC)，舒服的trackpad让工作的舒适度提高不是一星半点，而软件上强大的spotlight等系统功能让效率提升很多。这个我就不详述，自己看『mactalk·人生元编程』去。

## 使用大屏幕
工作中使用mbp是为了便携性 —— 在各种场合都可以进行开发任务，应对会议和各种各样的演示需求。可一旦坐在工位上好几个小时，全神贯注地写代码时，就最好有个大屏幕。

屏幕多大才好？在机器带的起来的情况下越大越好，能27"就不要24"，能24"就不要21"，能21"就不要直接使用笔记本的屏幕。大屏幕可以让一个屏幕同时显示好几个窗口而无需来回切换。我现在自己的工作配置是15" mbp + 27" apple display，用上了就回不去了，一天呆在公司12小时都不嫌多。

我自己一般把屏幕劈成两半，左边chrome，右边iterm，这样，在vim里写代码时，随时可以查文档。配合vim的热键，我可以用 <leader>xx 在chrome里打开某个开发语言的文档，鼠标都不用动一下。

## 使用dotfiles

一个程序员一天可能80%的时间都在跟shell打交道，有个好的shell(bash or zsh)，加上合理的shell配置绝对让效率提升一大截。我以前都是直接使用 mathiasbynens/dotfiles 的设置，后来自己改得多了，就干脆fork了一个版本 tyrchen/dotfiles 出来，把自己的改动放上去。

dotfiles这样的东西不必自己从头来，在github上找个star最高的clone或者fork之即可，这便是所谓的站在巨人的肩膀上。武学中要打通任督二脉，靠勤奋往往是不够的，还要有际遇，好比虚竹遇上了无涯子或者张无忌遇到了白猿。程序世界里的无涯子和白猿们都在github上，只是需要你的发掘。

我自己的dotfiles就在Mathias的基础上发展而来，基本上，我做了两个主要的改动：

- 把prompt换成帅呆了的liquidprompt
- vim使用vundle，并且使能了一堆我喜爱的插件（这个随后讲）

## 挑一款趁手的editor和ide
作为一个开发者，你需要精挑细选一款趁手的用来编辑代码的editor。我使用了几年的vim，又换用过大半年的emacs，为了强制自己习惯emacs，我甚至在bash中把vim alias成emacs。但最终，没能打开emacs下的任督二脉的我实在无法抗拒vim下的那些好用的插件，又回到了vim的阵营。所以在editor这里，我只能先讲讲更为熟悉的vim。

vim下最基本的vundle不提，至少这些插件你值得拥有：

- SirVer/ultisnips: 撰写和使用snippet神器，用过textmate/sublime的人应该都知道。一个程序员的效率很大程度上跟他的snippet库有关。如果你的python class，html的标签，erlang/elixir的otp代码还是一个字符一个字符手敲，那么你该好好看看这个插件了。配合着 honza/vim-snippets，大部分代码的snippet都有了；遇到结构类似的代码块（bolerplate），又没有已经定义好的snippet时，调用 :UltiSnipsEdit 立刻定义之，你基本上就走在无敌的路上了。
- scrooloose/nerdtree：让你的vim支持文件树。这个插件加上 tpope/vim-eunuch，文件系统的各种操作和显示全在vim里搞定了。
- sheerun/vim-polyglot：几乎所有程序语言的源文件syntax/tab等的支持。有此一个插件，就不再需要 vim-ruby，vim-go等一票单独的语言插件了。
- Valloric/YouCompleteMe：让vim支持自动补齐。这个几乎是IDE的标配，效率提升的另一大神器。有了它，IDE的需求就减弱很多。

其它的插件就不一一介绍了，感兴趣的可以在我的dotfiles里面一一翻阅。

大部分编程的工作，轻量级的editor就足够胜任，但有些开发语言和框架，bolerplate代码实在太多，整个开发目录太繁杂，这时候不得不使用IDE，比如说java下的很多项目。当你不得不使用IDE的时候，intelliJ系列的IDE是比eclipse系列好很多的选择。

当然，这条rule的核心是尽量使用editor，能不用IDE就不用IDE。

## 把常用的任务命令化/快捷键化
国外的开发高手也都是使用快捷键的高手，我以前不习惯使用快捷键，但看了很多高手的screencast后，发现他们都是当一个任务重复几次后，顺手就定义快捷键或者命令。这里我讲讲vim怎么做，emacs的用户自行脑补。

在进行elixir做TDD开发的时候，我经常需要运行 mix test 来确保我新写的代码或者重构的代码能够跑过已有的test case。这事做多了也就烦了，因为在vim里总需要输入 !mix test，这个时候，我就会为此定义个快捷键。如果快捷键只跟当前项目有关，那么就在当前项目根目录下生成一个 .vimrc，定义快捷键，否则在系统的 .vimrc 中定义：

```
noremap <leader>et :!mix test<CR>
```

这样，以后需要运行这个命令的时候，直接敲 <leader> key + ed 就好。对于elixir，我有这些定义：

```
noremap <leader>ed :!mix deps.get<CR>
noremap <leader>et :!mix test<CR>
noremap <leader>ec :!mix compile<CR>
```

因为每个语言都有类似的 dependency，test，compile等任务，如果要定义在全局的 .vimrc 文件里，可以为每种语言附不同的前缀（elixir为 e）区隔。如果你喜欢按项目定义，那可以把 <leader>t 统一定义为UT的命令，这样可以省去敲一个字符的时间。

## 培养自己好的重构习惯
这里讲的重构和代码里的重构大体意思一样，就是不断优化自己的工作环境。Rule 6其实就是一种重构。

经常问问自己这些问题：

- 常用的命令是不是做了alias？比如：总敲 ls -l，是不是应该alias出一个 ll 来？
- 常用的服务器信息是否写在了 .ssh/config 里？服务器登录是否使用了pub/private key（毋须输入密码）？
- 对于某些操作，可不可以定义一些快捷键（比如说google search）？
- 项目里重复的工作是不是写成了makefile（或是其他任务脚本，如rake，jake）？
- 常写的代码结构是否定义了snippet？

讲讲snippet。我特别喜欢vim的ultisnips，它能让我按语言很方便地定义snippet。比如在elixir里总要写的 GenServer 代码，大体结构是 Public API + GenServer API，我可以定义一个snippet，在敲入 defgen 的时候，可以展开成为下面的代码（并且我可以在代码中跳至需要我修改的地方）：

```
defmodule name do
  @moduledoc """

  """
  use GenServer

  ### Public API

  def start_link do
    {:ok, server} = :gen_server.start_link __MODULE__, [], []
  end

  ### GenServer API
  def init(state) do
    {:ok, state}
  end

  def handle_call(, _from, state) do

  end

  def handle_cast(, state) do

  end
end
```

这将省去我多少bolerplate的时间 —— 更关键的时，我的思绪不会被撰写这些无趣，但又不得不写的bolerplate打断。

## 使用git管理个人文件
大部分开发者对于自己的代码项目都有很好的习惯：使用git（或者其他scm）管理。但代码之外的文档，管理起来就有些随意，即没有历史记录，单纯存储在本地也容易丢失。建议大家对 $HOME 下的文件，只要是自己生成的文档（太大的二进制除外），一律用git管理（在目录下 git init）。你们看到的这个公众号的所有文章就是用github存储（private repo）。然而github上存储private repo毕竟要花钱 —— 不想花钱，又想很多私人的文档想管理怎么办？可以在dropbox（或者其他类似的网盘）上生成一个git的bare project，然后把本地的文档push上去。

## 多看高手的screencast
很多时候我们没有机会近距离看高手是怎么工作的，但观看他们的screencast不失是一种提高自己的好办法。在这个方面，其他语言的爱好者估计都要妒忌ruby的拥趸 —— ruby社区的各种screencast多得令人发指！通过订阅这些screencast，你不仅能快速学到语言相关的知识和实用的技巧，更重要的是，你知道高手都在用什么工具，如何写代码。11年的时候我看过一个php的screencast，一个法国人介绍如何用symfony撰写项目。那是我第一次领略什么是指尖如飞，也给我播下了snippet的种子（他用的是textmate）。从那以后，我会时不时地看一些各种各样的screencast（以rails的居多），学习点新东西的同时，还能学习高手的习惯。

## 参考资料
- [程序员效率指南](http://mp.weixin.qq.com/s?__biz=MzA3NDM0ODQwMw==&mid=206041450&idx=1&sn=3982c8cc45d7c47f0fbc19fe8371490f#rd)