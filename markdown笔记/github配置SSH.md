# github配置SSH

## 步骤一 创建SSH key

在github上找到官方文档，开始阅读

> **Generating a new SSH key**
>
> 在终端上执行以下命令
>
> ```shell
> $ ssh-keygen -t ed25519 -C "your_email@example.com"
> ```
>
> 或者执行
>
> ```shell
> $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
> ```

然后出现**“Generating public/private algorithm key pair.”**

当系统提示**"Enter a file in which to save the key"**时，回车（press Enter）就是默认key文件保存位置。

当系统出现**“Enter passphrase (empty for no passphrase): [Type a passphrase]”**时，键入一个短语单词作为密码，例如：yida

再次键入密码确认。

Ubuntu示例：

> ```bash
> $ ssh-keygen -t rsa -b 4096 -C "you@example.com"   
> Generating public/private rsa key pair.
> Enter file in which to save the key (/home/yida/.ssh/id_rsa): 
> Enter passphrase (empty for no passphrase): 
> Enter same passphrase again: 
> Your identification has been saved in /home/yida/.ssh/id_rsa
> Your public key has been saved in/home/yida/.ssh/id_rsa.pub
> The key fingerprint is:
> *************************************
> ```

在根目录的ssh文件夹下就生成了**公钥和私钥**

## 步骤二 将SSH密钥添加到ssh-agent

在后台启动 ssh 代理。

> ```shell
> $ eval "$(ssh-agent -s)"
> > Agent pid 59566
> ```

将 SSH 私钥添加到 ssh-agent。 如果您创建了不同名称的密钥，或者您要添加不同名称的现有密钥，请将命令中的 *id_ed25519* 替换为您的私钥文件的名称。例如我的是id_rsa

> ```shell
> $ ssh-add ~/.ssh/id_ed25519
> ```

## 步骤三 公钥绑定github账号

使用cat命令输出公钥

> ```shell
> yida@ubuntuyida ~/.ssh$ cat id_rsa.pub
> ```

在github中的设置，将公钥粘贴在SSH and GPG keys中

