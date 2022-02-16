# zsh+ohmyzsh

## one

首先普通用户使用命令下载zsh，并设置为默认终端

debian系列

> ```shell
> $ sudo apt intall zsh
> $ chsh -s /bin/zsh
> $ echo $SHELL	#输出使用的默认终端
> ```

**注意不要使用root用户**

## two

接下来就是去github下载ohmyzsh.地址为[ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)

文档里指导了下载命令

| Method | command                                                      |
| ------ | ------------------------------------------------------------ |
| curl   | sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" |
| wegt   | sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" |
| fetch  | sh -c "$(fetch -o - https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" |

## three

接下来就是编辑配置文件了。

推荐使用**vim**来进行编辑(普通用户)

```shell
$ vim ~/.zshrc
```

注意的就是Plugins以及Theme

```shell
plugins=(
  git
  bundler
)
# 有需要自己添加
```

```shell
ZSH_THEME="agnoster"	#一款非常好看的主题
```

选择困难症患者可以使用随即主题

```shell
ZSH_THEME="random"	#随机选择一款主题展现
```

## four

接下来开始配置root用户的**ohmyzsh**

在普通用户下执行以下命令

debian系列

```shell
$ sudo ln -s $HOME/.oh-my-zsh           /root/.oh-my-zsh
$ sudo ln -s $HOME/.zshrc               /root/.zshrc
```

这是使用软链接的方法

同理，我们切换到root用户，将默认终端设置成zsh。

```shell
$ sudo su
$ chsh -s /bin/zsh
```

如果每次**sudo su**过去遇到以下问题

"**For safety, we will not load completions from these directories until...**"

解决办法就是在当前用户(root，就是报错的那个用户)的根目录的.zshrc文件里的加载oh-my-zsh.sh之前添加 ZSH_DISABLE_COMPFIX="true"。

```shell
------------------------------------------
ZSH_DISABLE_COMPFIX="true"
source $ZSH/oh-my-zsh.sh
------------------------------------------
```

