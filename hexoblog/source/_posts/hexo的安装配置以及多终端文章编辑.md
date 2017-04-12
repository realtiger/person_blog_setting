---
layout: post
title: hexo的安装配置以及多终端文章编辑
comments: true
date: 2017-04-12 11:13:41
updated:
tags: hexo 博客
categories: markdown写作
---
通过Linux利用GitHub平台搭建Hexo博客平台，并且实现多终端能够编辑文章，上传（笨办法）
<!-- more -->
# 使用Linux搭建Hexo博客平台
一直以来都想自己搭建一个自己的博客平台，至于为什么，只能说就是这么任性。经过一段时间的考察（其实是正好看到），个人感觉Hexo还不错，同时作为颜控，Hexo的皮肤还是能够满足需求的。
但是网上搜索之后发现，Hexo大部分都是使用windows进行搭建，却没有Linux搭建的教程，以下就是我在Linux操作系统下进行搭建的过程，只能说，就是这么爱折腾。

# GitHub新建仓库
## 注册GitHub帐号
这里就是普通的帐号注册，可以自己摸索，不是很难

## 新建仓库
点击右上角的“+”号，选择新建仓库选项

## 输入仓库信息
输入你的仓库名字，这个名字就是以后访问博客的地址。据说，后缀必须是github.io或者github.com，没有验证真伪，如果是别的代码平台需参考平台规则。

# git使用密钥添加
## 生成密钥
在Linux机器上注册密钥

```
ssh-keygen -t rsa -C "GitHub注册邮箱"
```

直接一路回车就可以了，会在当前目录的.ssh目录下生成id_rsa和id_rsa.pub两个文件，注意，id_rsa不要泄漏给其他人。
使用命令打开id_rsa.pub，复制里面的内容。

```
cat .ssh/id_rsa.pub
```

## 输入密钥
点击右上角的头像旁的三角，选择设置选项卡。
在新页面中选择“SSH and GPG keys”选项卡。
点击添加“SSH key”按钮。
将刚才复制的内容都添加进去。

## 验证密钥是否生效
回到Linux机器，输入以下命令：

```
ssh -T git@github.com
```

中间会有一个询问，输入yes，如果能够看到以下提示就说明连接没有问题。

```
You've successfully authenticated, but GitHub does not provide shell access.
```

# 安装设置git
## 安装git
我使用的版本是centos7.2，默认没有安装，如果你使用的是其他版本除了安装命令不同之外，其他的差别不大，具体参考相应的命令。

```
yum install git -y
```

## git conf 设置
安装完成之后设置你的用户名以及邮箱

```
git config --global user.name "realtiger"
git config --global user.email "ganchangde@163.com"
```

# 安装nodejs
因为Hexo需要使用nodejs，所以我们要先安装nodejs
## 下载nodejs的安装包

```
wget http://nodejs.org/dist/v7.8.0/node-v7.8.0-linux-x64.tar.xz
```

解压至你想要放置的地方

```
tar Jxf node-v7.8.0-linux-x64.tar.xz -C /usr/local
```

## 链接node和npm命令

```
ln -s ~/node-v7.8.0-linux-x64/bin/node /usr/local/bin/node
ln -s ~/node-v7.8.0-linux-x64/bin/npm /usr/local/bin/npm
```

# 安装hexo
## 下载安装hexo
由于国外源并不稳定，因此使用淘宝源

```
npm install -g hexo-cli --registry=https://registry.npm.taobao.org
ln -s /usr/local/node-v7.8.0-linux-x64/bin/hexo /usr/local/bin/hexo
```

安装完成，输入hexo命令，如果显示如下提示，则说明安装成功

```
Usage: hexo <command>

Commands:
  help     Get help on a command.
  init     Create a new Hexo folder.
  version  Display version information.

Global Options:
  --config  Specify config file instead of using _config.yml
  --cwd     Specify the CWD
  --debug   Display all verbose messages in the terminal
  --draft   Display draft posts
  --safe    Disable all plugins and scripts
  --silent  Hide output on console

For more help, you can use 'hexo help [command]' for the detailed information
or you can check the docs: http://hexo.io/docs/
```

# 初始化博客
## 建立特定目录
因为有需求需要在不同的电脑上进行文档的编辑，所以最终会将所有的Hexo目录进行上传备份保存。因为博客也是要给其他人看的，博客框架以及主题又是开源的，所以谈不上什么信息泄露之类的，我比较懒，就直接传到github
但是目前还是先建立一个特定目录。

```
mkdir realtiger
cd realtiger/
```

## 初始化博客目录
hexoblog是自定义的文件夹名，可以随便起名字，hexo所有的目录文件都会初始化到hexoblog目录里

	hexo init hexoblog
	cd hexoblog/
	# 根据博客安装依赖包
	npm install --registry=https://registry.npm.taobao.org

此时博客目录下是这样的
	
	$ ls -a
	.  ..  _config.yml  .gitignore  node_modules  package.json  scaffolds  source  themes

# 配置博客
修改_config.yml文件，根据自身不同要求进行不同的修改。以下是默认文件，我添加了一些注释，我在后面配置了一些配置示例，也可跳过默认配置直接查看示例。
注意：因为文件是yaml格式，所以冒号后面有一个空格，不能省略，否则解析会出现错误。

	# Hexo Configuration
	## Docs: https://hexo.io/docs/configuration.html
	## Source: https://github.com/hexojs/hexo/
	
	# 站点信息
	# Site
	# 博客标题
	title: # The title of your website
	# 博客副标题
	subtitle: # The subtitle of your website
	# 博客描述
	description: # The description of your website
	# 作者
	author: # Your name
	# 语言，支持的语言在"./themes/landscape/languages/"下
	language: # The language of your website
	# 时区
	timezone: 
	
	# 网址信息
	# URL
	## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
	# 绑定域名，就是新建github时填写的那个网址
	url: http://yoursite.com/child
	# 网站的根目录
	root: /
	# 网站的永久链接
	permalink: :year/:month/:day/:title/
	# 网站的默认永久链接
	permalink_defaults:
	
	# 目录信息
	# Directory
	# 源文件目录
	source_dir: source
	# 网站网页目录
	public_dir: public
	# 标签目录
	tag_dir: tags
	# 归档目录
	archive_dir: archives
	# 分类目录
	category_dir: categories
	# 代码目录
	code_dir: downloads/code
	# 国际化
	i18n_dir: :lang
	skip_render:
	
	# 写作信息
	# Writing
	# 新文章标题
	new_post_name: :title.md # File name of new posts
	# 默认布局
	default_layout: post
	# 标题转换大小写
	titlecase: false # Transform title into titlecase
	# 是否在新标签页打开
	external_link: true # Open external links in new tab
	filename_case: 0
	render_drafts: false
	post_asset_folder: false
	relative_link: false
	future: true
	# 语法高亮设置
	highlight:
	  # 是否启用
	  enable: true
	  # 显示行号
	  line_number: true
	  auto_detect: false
	  tab_replace:
	
	# Category & Tag
	default_category: uncategorized
	category_map:
	tag_map:
	
	# Date / Time format
	## Hexo uses Moment.js to parse and display date
	## You can customize the date format as defined in
	## http://momentjs.com/docs/#/displaying/format/
	date_format: YYYY-MM-DD
	time_format: HH:mm:ss
	
	# 分页信息
	# Pagination
	## Set per_page to 0 to disable pagination
	# 每页的文章数
	per_page: 10
	# 分页目录
	pagination_dir: page
	
	# 扩展信息
	# Extensions
	## Plugins: https://hexo.io/plugins/
	## Themes: https://hexo.io/themes/
	# 使用主题
	theme: landscape
	
	# 部署信息
	# Deployment
	## Docs: https://hexo.io/docs/deployment.html
	deploy:
	  type:

以下是以我的博客配置做的示例。

1. 站点信息

		# Site
		title: realtiger's blog
		subtitle: 小真虎的个人博客
		description: 小真虎的分享平台
		author: realtiger
		language: zh-CN
		timezone: Asia/Shanghai
2. 个人网址设定

		url: http://realtiger.github.io
		root: /
		permalink: :year/:month/:day/:title/
		permalink_defaults:

3. 部署配置
	
以下信息是部署至GitHub的配置，如果需要部署至其他地方请再参考其他资料。

		# Deployment
		## Docs: https://hexo.io/docs/deployment.html
		deploy:
		  type: git
		  repo: https://github.com/realtiger/realtiger.github.io.git
		  branch: master

repo是你的GitHub仓库，可以进入你的仓库，点击右上角的“Clone or download”按钮，获得对应的URL

branch是项目的分支，默认使用主分支master

# 发表文章

输入以下命令新建一篇文章：

	hexo new "first"
	INFO  Created: ~/realtiger/hexoblog/source/_posts/first.md

可以看到系统已经创建了一个markdown文档，下面我们对文档进行编辑

	---
	title: first
	date: 2017-04-10 17:28:19
	tags:
	---
	欢迎大家来到我的新博客[1](https://realtiger.github.io):https://realtiger.github.io

保存。

# 发布、部署博客
## 生成网站静态文件

	hexo generate
	
	INFO  Start processing
	INFO  Files loaded in 368 ms
	INFO  Generated: index.html
	INFO  Generated: archives/index.html
	INFO  Generated: fancybox/blank.gif
	INFO  Generated: fancybox/jquery.fancybox.css
	INFO  Generated: fancybox/jquery.fancybox.pack.js
	INFO  Generated: fancybox/jquery.fancybox.js
	INFO  Generated: fancybox/fancybox_loading.gif
	INFO  Generated: fancybox/fancybox_sprite.png
	INFO  Generated: fancybox/fancybox_loading@2x.gif
	INFO  Generated: fancybox/fancybox_overlay.png
	INFO  Generated: fancybox/fancybox_sprite@2x.png
	INFO  Generated: archives/2017/04/index.html
	INFO  Generated: archives/2017/index.html
	INFO  Generated: js/script.js
	INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.css
	INFO  Generated: css/fonts/FontAwesome.otf
	INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.js
	INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.css
	INFO  Generated: fancybox/helpers/jquery.fancybox-media.js
	INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.js
	INFO  Generated: css/style.css
	INFO  Generated: fancybox/helpers/fancybox_buttons.png
	INFO  Generated: css/fonts/fontawesome-webfont.eot
	INFO  Generated: css/fonts/fontawesome-webfont.woff
	INFO  Generated: css/fonts/fontawesome-webfont.svg
	INFO  Generated: css/images/banner.jpg
	INFO  Generated: css/fonts/fontawesome-webfont.ttf
	INFO  Generated: 2017/04/10/hello-world/index.html
	INFO  Generated: 2017/04/10/first/index.html
	INFO  29 files generated in 1.04 s

## 本地发布

	hexo server

	INFO  Start processing
	INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.

然后在浏览器中打开http://localhost:4000/就可以看到我们搭建好的博客和发布的文章了。
注意：因为是linux机器，一定要打开防火墙的对应端口，否则无法进行访问。

防火墙的打开方法如下：
	
	# 防火墙临时打开端口
	firewall-cmd --add-port=4000/tcp

	# 防火墙永久打开端口，需要重新载入，载入前端口规则不生效
	firewall-cmd --add-port=4000/tcp --permanent
	firewall-cmd --reload

## 部署博客
现在还只是我们自己可以看到博客，其他人没有办法访问，只要输入以下命令就可以将博客部署到GitHub上了，这样其他人就可以访问，访问时只要输入自定义的网址即可，比如我的URL是:https://realtiger.github.io
	
	# 安装deployer git
	npm install hexo-deployer-git --save --registry=https://registry.npm.taobao.org
	hexo deploy

# 博客备份
返回目录上层，然后将博客目录作为一个整体目录备份到GitHub上的另一个仓库中

	cd ..
	git init
	git add hexoblog
	git commit -m "没有更改主题的初始形态"
	# person_blog_setting是我用于存储blog的新仓库
	git remote add origin git@github.com:realtiger/person_blog_setting.git
	# 将hexoblog整体进行推送
	git push -u origin master

至此，博客已经全部进行了备份

# 主题更改
作为一个看脸的吃瓜群众，我个人认为，默认主题还是不符合自己的要求，本来自己想写一个，无奈懒癌已经晚期，于是东找西找，觉得[Yelee](https://github.com/MOxFIVE/hexo-theme-yelee)的主题还是挺不错的，直接拿来用吧。

为了能够备份自己的配置，首先需要将主题fork到自己的仓库

然后进入自己的博客目录中，将fork的主题clone到主题目录中

	git clone git@github.com:realtiger/hexo-theme-yelee.git themes/yelee

然后根据自己的需求配置“./themes/yelee/_config.yml”，配置方法参考，[Yelee 主题使用说明 [简中]](http://moxfive.coding.me/yelee/)

其中特意提示一下404页面，我认为，我这个人虽然有很多不足，心还是善良的。我在自己的404页面上加入了腾讯的公益信息，至于能起多大作用，我不知道，但是如果能够起到哪怕一丝丝作用，即使一个站长看到了产生一些共鸣，用在了自己的404页面上也是一件好事。

在Hexo主目录下使用一下命令创建404页面。

	hexo new page 404

然后修改```source/404/index.md```页面

	---
	title: 404 Not Found：该页无法显示
	date: 2017-04-12 09:23:55
	toc: false
	comments: false
	permalink: /404
	---
	<script type="text/javascript" src="//qzonestyle.gtimg.cn/qzone/hybrid/app/404/search_children.js" charset="utf-8" homePageUrl="https://realtiger.github.io" homePageName="回到我的主页"></script>

其中js部分是腾讯的公益广告代码，因为404页面只能绑定顶级域名，所以我这里使用先跳转到自己的页面然后再跳转到腾讯公益广告页面的这种办法。

如果你想使用以上的404代码，请留意homePageUrl和homePageName属性，根据你自己的情况进行更改。

配置完成后，更改"./_config.yml"

	theme: yelee

之后再从本地发布

	hexo server

如果没有问题，提交yelee主题到仓库。
注意：如果提交的是主分支，你之后就无法提交对yelee主题的贡献了，如果还想要提交不同的贡献，建议提交到分支，具体如何提交到分支，请参考git命令，这里不再赘述。

	cd themes/yelee/
	git add .
	git commit -m "first"
	git push origin master 

这样就将修改文件上传到了GitHub上了。

最后不要忘了将Hexo进行更新，部署，上传，否则公网的博客主题不会有变化的。
	
	cd ../..
	hexo generate
	hexo deploy
	cd ..
	git add .
	git commit -m "更改主题"
	git push

# 不同终端编辑文章
## Hexo整体目录创建
首先在GitHub上添加密钥，安装nodejs就不再叙述了，主要看不同的地方。
首先要克隆Hexo整体目录

	git clone git@github.com:realtiger/person_blog_setting.git realtiger
	# 进入hexoblog目录
	cd realtiger/hexoblog
	# 根据博客安装依赖包
	npm install --registry=https://registry.npm.taobao.org
	# 安装deployer git
	npm install hexo-deployer-git --save --registry=https://registry.npm.taobao.org
	# 克隆主题
	git clone git@github.com:realtiger/hexo-theme-yelee.git themes/yelee
	# 如果有搜索插件需求，还要将插件进行安装
	npm install hexo-generator-search --save --registry=https://registry.npm.taobao.org

## 克隆目录的使用
之后这个文件夹就完全一样了，写文章，发布，修改就都一样了。如果做了更改，记得保存配置哦。
如果在别的机器上做了更改，本机要```git pull```更新一下本地目录再进行操作。

相关文章推荐：
	
- [20分钟教你使用hexo搭建github博客](http://www.jianshu.com/p/e99ed60390a8)
