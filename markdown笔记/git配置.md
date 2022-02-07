# git配置

## 配置gitconfig

**git的配置文件主要依赖于gitconfig，使用"git config --global"配置全局git环境**

下面使用命令进行配置

> ```shell
> $ git config --global user.email "you@example.com"
> $ git config --global user.name "Your Name"
> $ git config --global core.quotepath false	#显示status编码
> $ git config --global gui.encoding UTF-8	#图形界面编码
> $ git config --global il8n.commitencoding UTF-8	#提交信息commit编码
> $ git config --global il8n.logoutputencoding UTF-8	#输出log编码
> $ export LESSCHARSET=UTF-8
> ```

下面我们查看gitconfig文件

> ```c++
> [user]
> 	email = XX@XX.com
> 	name = ***********
> [core]
> 	quotepath = false
> [gui]
> 	encoding = UTF-8
> [il8n]
> 	logoutputencoding = UTF-8
> 	commitencoding = UTF-8
> ```

