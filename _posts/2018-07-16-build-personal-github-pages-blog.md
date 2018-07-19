---
title: Build my personal blog based on GitHub Pages
categories:
 - Tutorial
tags:
---

This post records the procedure of building this personal blog. It contains mainly four parts: preparation, DNS setting, email redirection, blog configuration.

## Preparation

For a personal blog, we first need a server. I bought a domain name on [WanWang of Aliyun](https://wanwang.aliyun.com). If it is your first time to buy a domain name, you should create an information template and provide your personal information for an identity verification. My domain name is [wangsun.top](http://www.wangsun.top).

My blog is based on GitHub Pages, a GitHub account is necessary. Then we should choose a framework to easily build our blog. [Hexo](https://hexo.io/themes) and [Hugo](https://themes.gohugo.io) are two popular frameworks with many themes. [Jekyll](https://jekyllrb.com) is a simple, blog-aware, static site generator for personal, project, or organization sites. I chose a Hexo theme supported by Jekyll. Find the corresponding repository on GitHub, fork it and rename.

## DNS setting
Once we have a domain name, we cannot directly link our website to it. We need to create a mapping from the domain name to an IP address. 
* Use the IP address of your GitHub Pages obtained by

```sh
ping your_username.github.io
```

* Go to your DNS list, click on DNS setting of the domain you want to create the mapping. Add two new records with type `A` and record value `your GitHub Pages IP address`, one with host record `www` and the other with `@`. 
(域名列表-解析-添加记录)

* Go to your GitHub repository, find `GitHub Pages` under Setting, save `master branch` for source and `www.your_domain_name` for custom domain (this will create a CNAME file in repository).

Now we can access your personal blog by `www.your_domain_name` or directly `your_domain_name`. For example, [www.wangsun.top](http://www.wangsun.top) or directly [wangsun.top](http://wangsun.top) to access mine.

## Email redirection
If we want an email address like `me@wangsun.top`, we need to choose an mail server and then create a mapping from the domain name to it. Normally, we use email redirection for enterprise email. [Alibaba](https://qiye.aliyun.com), [NetEase](http://ym.163.com), [Tencent](https://exmail.qq.com) and some other companies provide enterprise email service. I chose [Alibaba](https://qiye.aliyun.com) because I automatically receive one account when I bought the domain name. And its DNS records (MX, CNAME, TXT) have already been added. If we want other companies' service. Sign up an account, add your favorate name as a staff account, search for email server information and add DNS records.

In fact, I tried to redirect my personal [tencent qq email](https://mail.qq.com). Sign up the account, go to setting, find `Domain name mailbox`, manage it, create domain name mailbox. However, my domain name `.top` is not supported by tencent emial server. So if your domain name is supported, follow the steps may work. 
(登录-设置-帐户-域名邮箱-管理域名邮箱-创建域名邮箱)

## Blog configuration
To modify and test the blog locally, we should prepare a local developing environment.

* Install Ruby if it doesn't exist in your PC because Jekyll is written in Ruby.

```sh
sudo apt-get install ruby
sudo apt-get install ruby-dev (optional)
```

* Install the Bundler gem. 

```sh
sudo gem install bundler
```

* Install Jekyll and other dependencies from the GitHub Pages gem.

```sh
sudo bundle install
```

* If there is a problem with nokogori, install it manully and then Jekyll & dependencies.

```sh
sudo apt-get install build-essential patch ruby-dev zlib1g-dev liblzma-dev
sudo gem install nokogiri
sudo bundle install
```

To open with local web browser for developpement:
```sh
bundle exec jekyll serve
```

Basic configuration is in `_config.yml`. Modify as needed.