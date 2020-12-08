---
title: Mac多版本python
date: 2018-08-15 14:58:01
tags: 
    - python
    - pynev
---
经常遇到这样的情况：
系统自带的Python是2.x，自己需要Python 3.x，测试尝鲜；
系统是2.6.x，开发环境是2.7.x
由于Mac机器系统保护的原因，默认的Python中无法对PIP一些包升级，需要组建新的Python环境。
此时需要在系统中安装多个Python，但又不能影响系统自带的Python，即需要实现Python的多版本共存。pyenv就是这样一个Python版本管理器。
#### 安装Homebrew
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
```bash
brew -v # 验证是否安装成功
```
#### 安装pyenv
```bash
brew install pyenv
```
```bash
pyenv -v # 验证是否安装成功
```
#### pyenv 常用命令
*  pyenv install --list # 查看可以安装的python版本
*   pyenv install x.x.x # 安装x.x.x版本
* pyenv rehash   # 安装之后记得一定要rehash
* pyenv version # 查看当前激活的版本
* pyenv versions # 查看已安装的版本
* pyenv global x.x.x # 将全局切换为x.x.x版本
* pyenv local x.x.x # 将当前用户切换为x.x.x版本

#### tips  某些机器pyenv命令不生效的解决方法
Add to your shell (~/.bashrc or ~/.zshrc) 

```bash
export PATH="/Users/username/.pyenv:$PATH"
eval "$(pyenv init -)"
```


