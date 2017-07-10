---
title: 最详细“截图”搭建Hexo博客并部署到Github上
date: 2017-07-06 18:02:36
comments: true
tags: 
- Hexo 
- Github
- Blog
categories: 心得
---
这两天忙的一件事是搭建博客，在这个过程中很多时候，都是按着教程来做就可以了，但是我当时为了搭建Hexo博客并部署到Github，走了不少弯路。现在终于搭建出来了，为了帮助大家，我决定写一篇“最详细“截图”搭建Hexo博客并部署到Github上”。当然大家可以访问我的[Github](https://github.com/wjf9492/wjf9492.github.io).

## 安装Hexo
1. 利用 npm 命令即可安装。在任意位置点击鼠标右键，选择Git Base。
![](http://i.imgur.com/oVRpP5Y.png)
2. 输入命令：
npm install -g hexo
注意：-g是指全局安装hexo。

## 创建Hexo文件夹
安装完成后，在你喜爱的文件夹下（如C:\Hexo），执行以下指令(在C:\Hexo内点击鼠标右键，选择Git Bash)，Hexo 即会自动在目标文件夹建立网站所需要的所有文件。
hexo init

## 安装依赖包
npm install

## 本地查看
现在我们已经搭建起本地的hexo博客了，执行以下命令(在C:\Hexo)，然后到浏览器输入localhost:4000看看。
hexo generate/ hexo g
hexo server/hexo g

![](http://i.imgur.com/vbIiljI.png)

## 注册Github账号
假设你以及注册Github账户（这里不演示了，不懂得百度一下）

## 利用Github创建Repository

创建的时候注意Repository的名字。比如我的Github账号是wjf9492，那么我应该创建的Repository的名字是：wjf9492.github.io。

## 修改配置文件
### 第一步
到你刚刚创建的Repository下，找到以下内容：
![](http://i.imgur.com/Xpx3I6J.png)

### 第二步
先点击HTTPS，然后复制里面的地址。然后编辑_config.yml文件（在C:\Hexo下）。
![](http://i.imgur.com/GmvSUph.png)

### 第三步
修改文件里面的deploy。其中的repository就改成你刚刚复制的地址。保存这个文件。（小提醒：1、例如(type: git)中间是有用半圆角的设置的空格；2、注意新的GitHub版本写法如下：）
![](http://i.imgur.com/KnS77D4.png)

## 设置SSH keys（※※※※※）
1. 在Git Bash输入以下指令（任意位置点击鼠标右键），检查是否已经存在了SSH keys。
ls -al ~/.ssh
2. 如果不存在就没有关系，如果存在的话，直接删除.ssh文件夹里面所有文件：![](http://i.imgur.com/v5o85JC.png)
3. 输入以下指令（邮箱就是你注册Github时候的邮箱）后，回车：
ssh-keygen -t rsa -C "1514163006@qq.com"![](http://i.imgur.com/4kDcMXj.png)
4. 然后它会提示要你输入passphrase（如上图，我没有输入直接回车，如果你输入的话，要记得，到时候会用到）。之后，如果出现类似下图：![](http://i.imgur.com/9KYWP62.png)
5. 然后键入以下指令：
ssh-agent -s![](http://i.imgur.com/TfAFl2L.png)
6. 继续输入指令：
ssh-add ~/.ssh/id_rsa
7. 输入之后，在我这里是出错了，不知道你的有没有出错。![](http://i.imgur.com/VF95xHP.png)
8. 如果你的也是这样子出错了的话，就输入以下指令：
eval 'ssh-agent -s'
ssh-add!（PS	：两个小点是这个 shift+~ 按钮生成的）
[](http://i.imgur.com/E60e4ih.png)
9. 到了这一步，就可以添加SSH key到你的Github账户了。键入以下指令，拷贝Key（先拷贝了，等一下可以直接粘贴）：
clip < ~/.ssh/id_rsa.pub
10. 然后到Github里面，点击右上角的设置图标：
11. 在Settings sidebar那里，点击SSH keys：
12. 点击Add SSH key：
13. 然后这个Key就是刚刚拷贝的，你直接粘贴就好（也可以文本打开以下文件）：![](http://i.imgur.com/xaJpyBr.png)
14. 点击Add Key：
15. 输入你的Github密码即可完成SSH Key的添加。嗯，最后还是测试一下吧，键入以下命令：
ssh -T git@github.com![](http://i.imgur.com/xVTz6kH.png)
16. 你可能会看到有警告，没事，输入“yes”就好。
## 完成部署

- 在你创建的hexo 根目录下，键入指令：
hexo g
hexo d
- OK，我们的博客就已经完全搭建起来了，在浏览器输入（当然，是你的用户名）：
http://wjf9492.github.io/![](http://i.imgur.com/f9WyJoM.png)
- 注意：每次修改本地文件后，需要键入hexo g才能保存。每次使用命令时，都要在C:\Hexo目录下。每次想要上传文件到Github时，就应该先键入hexo g保存之后，再键入hexo d。大概成功之后是酱紫的：![](http://i.imgur.com/QGQ7NAd.png)
- 对了，记住上图的Username是你的Github账号名称，而不是邮箱；Password就是你的Github的密码。
## Tips
hexo现在支持更加简单的命令格式了，比如：
hexo g == hexo generate
hexo d == hexo deploy
hexo s == hexo server
hexo n == hexo new



本文章借鉴[百度经验](http://jingyan.baidu.com/article/d8072ac47aca0fec95cefd2d.html)