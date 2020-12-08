---
title: Homebrew更换软件源
date: 2018-09-17 16:46:42
tags:
    - homebrew
categories:
	- 中间件
---
<center>![](1*Xjef3Zcg4T1x-tJIYHWFbg.png)</center>
homebrew主要分两部分：git repo（位于GitHub）和二进制bottles（位于bintray），因为一些众所周知的原因，这两者在国内访问都不太顺畅；为了可以使用brew流畅的安装各种软件，你可以将其默认的软件源修改为访问国内的源镜像，以下以清华大学提供的源为例，演示如何更换本地的brew软件源为清华的brew源。

#### 替换现有上游
```bash
cd "$(brew --repo)"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
brew update
```
#### 使用homebrew-science或者homebrew-python
```bash
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-science"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-science.git
cd "$(brew --repo)/Library/Taps/homebrew/homebrew-python"
git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-python.git
brew update
```

**参考资料**
*  [清华大学开源软件镜像站](https://mirror.tuna.tsinghua.edu.cn/help/homebrew/)
*  [brew安装](https://brew.sh/index_zh-cn)



