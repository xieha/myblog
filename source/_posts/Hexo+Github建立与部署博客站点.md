---
title: Hexo+Github建立与部署博客站点
date: 2018-03-20 23:16:44
tags: [hexo,github]
categories: 分享创造
---

## 什么是Hexo ？##

<blockquote>Hexo 是博客框架，将支持的类型的文件转换成静态Web页面（html+css+javascript）。
</blockquote>
## 什么是Github？##
百度百科，解释如下：
<blockquote>gitHub是一个面向开源及私有软件项目的托管平台，因为只支持git 作为唯一的版本库格式进行托管，故名gitHub。
</blockquote>

由于自己搭建Hexo踩了不少坑，为了减少其他小伙伴踩坑。也对Hexo和Github搭建博客的一个总结，分享一些经验。


## 配置与安装 ##
准备工具
<blockquote>

  1. 安装Git到本地电脑 </br> 
  2. 安装Node.js到本地电脑  
    </blockquote>
    git百度下载地址：[git-for-windows][1]，地址是我百度找的，如果你有更好的下载也可以去下载。百度下载的版本可能比较旧。
    nodejs下官网载地址：[node.js][2]，进去里面选择版本就好了。
    git和nodejs安装步骤就不详细说了，就一路NEXT下去就好了。
## 配置Git ##
首先到[Github][3]注册个帐号，看不懂英文可以百度。

![1.png][4]
注册完之后，新建项目，这里注意下，项目名称必须和子域名一样，例如，我的用户名是xieha，那么我的就是xieha.github.io。

## 配置Git ##
之后是配置github用户信息，在本地电脑桌面右键Git，名称是：Git bash here，打开之后是个命令窗口，输入如下命令：


    $ git config --global user.name "xieha"       ---这是用户名
    $ git config --global user.email xieha@example.com      ---这是邮箱地址

这里注意的是：复制请不要连 “$”和“---的文字”这个也复制。

## 安装Hexo ##



    $ npm install hexo-cli -g

安装hexo需要几分钟的时间。安装完大概是这样的。

![hexo.jpg][5]
安装完hexo后，我们来新建个博客，可以在D盘，或者F盘安装博客系统。输入如下命令：

    $ hexo init blog

命令后面的“blog”可以改成你喜欢的文件夹名称。</br>
继续安装，切换到该博客根目录下。命令是：

    $ cd blog

安装NPM

    $ npm install

访问hexo博客

    $ hexo c   
    $ hexo g    
    $ hexo s   

到这里，Hexo博客本地已经搭建完成了，输入本地地址访问看看：localhost:4000

![hexobendi][6]

## 部署到github ##

    $ hexo c   
    $ hexo g    
    $ hexo d    

部署成功的是这样的：
![github.png][7]
至此，hexo+Github教程差不多结束了，在这里要说下，git配置一定要配置准确，不然最后部署不到github。
![hexoindex.png][8]

稍等几分钟，或者刷新浏览器，就可以看到hexo成功部署到github上了。

**以下是遇到一些安装问题**
## 2018.3.17 ##
 提交 Hexo d 出现错误！

    bash: /dev/tty: No such device or address

  提示git用户名，node出错。 

![2018031701.png][9]
解决方法：
首先确保git配置用户正确。其次删除hexo博客.deploy_git文件。最重要的一步是一定要配置正确_config.yml。
之前我的配置文件是：

   deploy:
  type: git
  repo: https://github.com/xieha/xieha.github.io.git
  branch: master

把repo的链接改下，最终我的配置文件是：

  deploy:
  type: git
  repo: git@github.com:xieha/xieha.github.io.git
  branch: master

之后在重新hexo c hexo g    hexo d
      
![2018031702.png][10]

打开看看是不是成功部署到github上了。

[1]: http://rj.baidu.com/soft/detail/30195.html?ald
[2]: https://nodejs.org/zh-cn/
[3]: http://github.com
[4]: http://xieha.cn/usr/uploads/2017/12/1814145842.png
[5]: http://xieha.cn/usr/uploads/2017/12/4086500733.jpg
[6]: http://xieha.cn/usr/uploads/2017/12/1412803850.png
[7]: http://xieha.cn/usr/uploads/2017/12/625385888.png
[8]: http://xieha.cn/usr/uploads/2017/12/3970568572.png
[9]: https://xieha.cn/usr/uploads/2018/03/1891045187.png
[10]: https://xieha.cn/usr/uploads/2018/03/1539070674.png