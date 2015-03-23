---
layout: post
title: 在GitHub上免费搭建你的Blog
---

###前言###
  前段时间突然想给自己搭建一个Blog，用来记录自己生活学习上的所做所想，避免浑浑噩噩
  每一天（其实大学都快混完了），希望现在开始还不晚。然后就开始买域名，整网站，弄了两天才搞定。

  我为什么要自己搭建？

  1. 我想拥有一个属于自己的网站，它的域名是我的网络ID。
  2. 我要写的是博客。我想让我写的东西被更多人看到，并可留言讨论。
  3. 我想使用自己喜欢的风格展示网站。

另外，用我下面讲到的方式搭建可以省一笔钱，因为不需要购买主机空间。

##**一、Jekyll是什么？**##

  Jekyll是一个静态网站生成工具，由Ruby语言写成，它也是一个[开源项目](https://github.com/jekyll/jekyll)。

  它的核心是一个文本转换引擎，其概念就是: 你用你喜欢的标记语言，比如Markdown、Textile，
  在你喜欢的编辑器里将文章写成，然后Jekyll可以将它转换成HTML网页，并为它应用预设或者自定义的样式。
  一个Jekyll网站不需要用到数据库，它自己也不是一个内容管理系统（CMS），不像WordPress之类。
  你所做的只是本地编辑文章，然后用一个命令生成一个网站，它就是一些文件和文件夹，
  最后用工具把这些文档上传到服务器就可以了。

  如果服务器支持Jekyll（比如GitHub Pages），你都不必事先生成网站，
  直接用工具（比如Git）上传编辑好的文档就行，服务器端会自动生成网站，并且以后传入新的文档它也会自动更新。
  总之，使用Jekyll你只需关心写作本身。

  Jekyll默认生成的主题（模版/网站样式）可能有些简陋，如果不喜欢，你可以到[这里](http://jekyllthemes.org/)找自己喜欢的主题。
  如果有编程基础的话，你还可以自行定制一个主题，官方指南在[这里](http://jekyllcn.com/)。

##**二、GitHub Pages是什么？**##

  GitHub Pages是GitHub免费提供的一个静态网页托管服务，当然你要有GitHub账号。
  而且GitHub Pages支持托管使用Jekyll创建的网站。

  >所以利用Jekyll 和 Github Pages 就可以免费建站了

  事实上，你可以不用Jekyll，而是编写原始的HTML文本，组织好目录结构并发布到你的GitHub Pages。
  但这种方式肯定超级累。所以有了Jekyll这个工具，使用它
  做起事来更方便，更简单，而且方便定制网站布局样式等。不过你得先会如下工具：

  1. Markdown/Textile: 你直接写文章用到的标记语言，会一种就行。
  2. Jekyll: 几个基本命令，了解就行。
  3. Liquid，HTML，CSS，javascript: 如果要定制自己的主题就需要会这些语言，不必精通。
  4. Git/GitHub: 如果是托管在GitHub上，必须先知道这些，也是基本的几个命令，算简单。

正如[Rei](http://chloerei.com/2013/09/30/back-to-jekyll/)所说，使用门槛很高，但除了第3点，也就是你打算用现成的主题的话，
其他的只要用过一遍就会了，以后主要就是用Markdown写文章了。


### GitHub Pages的两种类型：###

  - **Project Pages网站**

      用作项目主页，展示关于一个项目的详细信息。个人/组织用户都可以创建。
      要创建一个Project Pages网站，需要到项目所在的仓库创建一个名为“gh-pages”的分支。
      gh-pages分支的内容将被自动托管，因此只要把创建好的网站文件放入该分支就可以了。
      它的访问URL默认是这样：

      ```
      http://username.github.io/project-name
      ```

      username是你的GitHub用户名, project-name是项目的名字


  - **User/Organization Pages网站**

      用作个人/组织主页，我当然用的是这种类型。其实也可用Project Pages去展示，只不过这样做不符合约定习惯。
      与Project Pages不同，要创建一个User/Organization Pages网站，你必须新建一个仓库，
      并且仓库的名称必须像这样：

      ```
      username.github.io
      ```

      即必须以用户名打头，所以每个个人/组织只能创建一个自己的主页。

      创建后，该仓库的master分支的内容将自动被托管。同样，放入网站文件即可。它的访问URL就是：

      ```
      http://username.github.io
      ```

##**三、如何在GitHub Pages上部署一个基于Jekyll的博客站点？**##

  我使用的是Ubuntu 12.04LTS，所以我以Linux上的步骤为例作介绍。其实在Windows、Mac OS X上的步骤是差不多的。

  运行Jekyll需要ruby环境，你必须先安装好ruby，最好是1.9版本以上，这样不用再单独安装gem。
  Git也是必须安装的。

  假设这些你已经安装好了。

###1、安装Jekyll并创建一个网站###

  打开终端：

  1）安装Jekyll

  ```
  $ gem install jekyll
  ```

  2）用Jekyll命令创建一个网站

  ```
  $ jekyll new myblog
  ```

  3）运行网站

  ```
  $ cd myblog
  $ jekyll serve --watch #这个命令监视网站文件，可以进行热部署。
  ```

  打开浏览器访问 localhost:4000 就可以看见一个原始Jekyll网站了。当然样子比较简陋。

  现在你用一个文本编辑器打开 myblog 目录，在 _post 目录下创建一篇文章, 编辑如下内容, 然后保存为 2014-12-01-first-blog.html

  ```html
  <h1>Hello Jekyll</h1>
  ```

  再在浏览器里刷新页面，就可以查看刚才新发布的文章了。

通过上面的方式得到的网站，只能使用Jekyll默认的主题，而且相当简陋。
你要想更漂亮要么自己开发制作，要么使用别人制作好的，我当然推荐后者了。

要使用某个Jeykll主题的话，步骤如下：

打开终端:

a. 新建一个目录，比如myblog2

  ```
  $ mkdir myblog2
  ```
b. 下载主题（包），解压（如果需要）并复制到myblog2目录。

c. 一个Jekyll主题实质上就是一个已经编译好的Jekyll网站，只不过稍微复杂，
  用到了许多样式设计组件。
  因此，在本地运行时需要安装额外的gem(Jekyll也是一个gem，因此也会安装好)，
  所以还要执行如下命令：

  ```
  $ cd myblog2
  $ bundle install
  ```

e. 编译并以热部署的形式运行网站：

  ```
  $ jekyll serve --watch
  ```
f. 在myblog2/_posts目录下创建和编辑文章，保存, 在浏览器上访问网站并审视效果(该步骤可重复)。

###2、用Git将网站推送到GitHub###

登陆GitHub，新建一个仓库，命名形式：username.github.io

然后在终端：

1）将仓库克隆到本地。

  ```
  $ git clone https://github.com/username/username.github.io
  ```

2）切换到username.github.io目录。

  ```
  $ cd username.github.io
  ```
现在你可以在该目录下按照前面的方式，用Jekyll命令创建网站了，这里我直接把myblog目录里的文件拷贝进来。

3）将username.github.io目录里的所有内容添加到本地仓库的暂存区。

  ```
  $ git add .

  "."代表当前目录（所有的内容），这个命令相当于做一个预提交。
  ```
4）提交暂存区的内容到本地仓库的当前分支（master分支），永久保存。

  ```
  $ git commit -m "First submit for myblog"

  -m: 即--message的简写。
  后面的字符串内容是对这次提交动作的描述，可指明做了哪些修改。
  ```

5）将当前分支的内容推送到远程仓库的master分支。

  ```
  $ git push

  这里省略了两个参数：
    完整命令: git push origin master
    origin: 一个远程仓库如果被克隆到本地，那么GitHub默认它的别名为origin，它的本地仓库可
          通过这个别名连接自己。
          比如这里的origin就是下面这个远程仓库的别名:
          https://github.com/username/username.github.io

    master: 远程仓库origin的master分支。
  ```

上传成功后，大约过10-15分钟，访问

  ```
  http://username.github.io
  ```
就可以见到你的网站了。

另外，创建一个Project GitHub pages的步骤跟上面差不多，只需在项目所在仓库新建一个gh-pages分支，
然后把网站文档push到origin gh-pages即可。访问

  ```
  http://username.github.io/project-name
  ```
即可见。

###3、为网站配置独立域名###
如果你自己有个域名，你也可以将GitHub Pages网站解析到你的域名下。事实上大家都这样干。

**GitHub支持配置两种类型的域名：**

  - 配置一个一级域名的方式

    比如，将hooozer.com --> username.github.io
    这种方式要求你在你的域名上配置一个A记录，将你的一级域名指向下面这两个IP：

    ```
      192.30.252.153
      192.30.252.154
    ```
    我试过这样设置，但访问起来有些慢。
    详见[这里](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/)。

    有些域名注册商支持将一级域名解析到另一个域名，即类似为一级域名配置一个CNAME记录。
    但我在godaddy上注册的好像没有这种功能。

  - 配置一个二级（子）域名的方式，这也是GitHub推荐的

    比如，将www.hooozer.com --> username.github.io

    或者将blog.hooozer.com --> username.github.io

    这种方式你必须配置一个CNAME记录：
      将www/blog.hooozer.com 指向 username.github.io
    详见[这里](https://help.github.com/articles/tips-for-configuring-a-cname-record-with-your-dns-provider/)。这种方式访问速度确实快些。

**添加CNAME记录**

配置好上述的任意一种后，你必须在你的网站文档根目录里新建一个CNAME文件，
内容是前面你为 username.github.io 配置的域名，比如：

```
hooozer.com
```
或者

```
www.hooozer.com
```
或者

```
blog.hooozer.com
```

*记得 push 到 GitHub*

**注意**：如果前面两种类型的域名都配置了，比如我，
那么如果我的CNAME文件里填写的是hooozer.com，
那么当我访问www/blog.hooozer.com将会指向hooozer.com
的解析（访问有些慢），浏览器的地址栏里总是hooozer.com

如果我的CNAME文件里填写的是www/blog.hooozer.com，
那么访问hooozer.com，将会指向www/blog.hooozer.com 的解析（访问较快），浏览器的地址栏总是www/blog.hooozer.com

另外，以后你如果为自己的某个项目创建了Project Pages站点，比如demo-app, 那么现在通过
[www/blog.]hooozer.com/demo-app就可以访问demo-app的主页了。

##**四、更多资料**##

  - Markdown 写作：https://help.github.com/articles/markdown-basics/
  - Jekyll 指南：http://jekyllcn.com/
  - Jekyll 主题：http://jekyllthemes.org/
  - 一个很流行的Jekyll主题：http://octopress.org/
