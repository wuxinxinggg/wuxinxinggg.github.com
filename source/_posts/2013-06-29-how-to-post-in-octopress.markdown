---
layout: post
title: "利用octopress和github page搭建个人博客"
date: 2013-03-26 10:38
comments: true
categories: 
---
###基础建设###
>安装RVM和Ruby
>

	安装RVM
	curl -L https://get.rvm.io | bash -s stable --ruby

	安装Ruby
	rvm install 1.9.3
	rvm use 1.9.3
	rvm rubygems latest

运行`ruby --version`确定输出是1.9.3

>配置octopress
>


	$ git clone git://github.com/imathis/octopress.git octopress
	$ cd octopress
	$ bundle install
	$ rake install

###部署到github page上###
***
	$ rake setup_github_pages

	$ rake generate

	$ rake deploy

	$ git add .

	$ git commit -m ‘your message’

	$ git push origin source

###自定义域名###
	echo ‘your-domain.com’ >> source/CNAME

###写博文###
>下面摘自geekontheway的博客
>		如果你是和别人合作博客，或者自己同时在好几个电脑上写博客，每次开始之前要做以下步骤

>		*新电脑的话要先克隆*，并`git checkout source` 切换到source版本

>		`git pull origin source`获得最新的文件

>		运行`bundle install`

>		运行`rake setup_github_pages`配置github page

>		运行`rake new_post["you_post_tittle"]`并编辑source/_post/下对应的markdown文件

>		运行`rake gen_deploy`部署到github page

>		最后别忘了同步到你的github上面去，运行`git push origin source`进行同步



