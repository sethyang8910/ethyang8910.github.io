## MyBolg

### 分支信息

源文件在```source```分支  

master分支仅用于github pages部署。


### source下目录介绍

博客发布在_post/文件夹.

assets/目录下存放 图片，CSS,js等资源

### tag

1. 新增tag

  ```_data/tags.yml```  

2. 如果新tag要显示在导航条

  ```_includes/navigation.html```中新增。

  修改导航条也在这里。

### 新增、修改图片css等资源

```assets/```

### 草稿箱

本地仓库中新建_drafts目录 或者随便。

### 获取源码

在项目界面点击Clone，下载zip包，或者 使用命令

```git clone git@github.com:sethyang8910/sethyang8910.github.io.git ```

### 编译

  首次运行

  ```bundle install```

  然后

  ```bundle exec jekyll serve```

  本地调试地址 ``` 127.0.0.1:4000 ```

```jekyll serve```执行后会自动把整站的静态文件生成到```../publish-sethy```目录

### 推送+部署


```../publish-sethy``` 将该目录作为一个新的git仓库

``` git init ```

``` git remote add origin git@github.com:sethyang8910/sethyang8910.github.io.git ```


以下命令可以写成脚本，发布的时候执行脚本即可。

``` git add . ```  追踪所有修改。

``` git commit -m "auto push" ```  相当于带备注的ctrl+s

``` git push origin master ``` 推送到远程仓库的master分支

部署是github自动执行。

### 为啥搞这么麻烦

1. github 的安全限制会导致编译失败。

  所以只能自己编译.

2. github部署的奇怪变更

  以前是可以编译到一个当前目录，比如site下面，然后指定pages服务使用哪个目录发布。
  然而现在的情况是，如果你使用username.github.io作为仓库名的时候，你发布的网站网址就是username.github.io，这很好，但是这种情况下pages只能默认使用master分支发布，这就导致该分支下面只能放编译好的文件。

  不用username.github.io作为仓库名时，可以任意指定分支和目录进行发布，但是网址的url就会变成```username.github.io/仓库名```，这就导致不管是绑定自己的域名也好，做https也好，甚至各种模版中{site.url}的修改啥的都会很麻烦.


---
## Jasper2

[![Build Status](https://travis-ci.org/jekyller/jasper2.svg?branch=master)](https://travis-ci.org/jekyller/jasper2)
[![Ruby](https://img.shields.io/badge/ruby-2.5.1-blue.svg?style=flat)](http://travis-ci.org/jekyller/jasper2)
[![Jekyll](https://img.shields.io/badge/jekyll-3.7.4-blue.svg?style=flat)](http://travis-ci.org/jekyller/jasper2)

This is a full-featured port of Ghost's default theme [Casper](https://github.com/tryghost/casper)
*v2.1.9* for [Jekyll](https://jekyllrb.com/) / [GitHub Pages](https://pages.github.com/).

## Live Demo

[Ghost's Casper](https://demo.ghost.io) // [Jasper2](https://jekyller.github.io/jasper2)

![home page](https://raw.githubusercontent.com/jekyller/jasper2/master/assets/screenshot-desktop.jpg)


## Features

* Out of the box support for multiple authors (via `_data/authors.yml`)
* Full author information including: picture, bio, website, twitter, facebook, etc.
* Tag description(s) and personalised covers (via `_data/tags.yml`)
* Related posts view at the bottom of each post
* All Ghost default pages: Author page(s), Tag page(s), About page(s), 404, etc.
* Pagination (infinite scrolling or standard pagination, i.e. posts across multiple pages)
* Atom Feeds by [Jekyll-feed](https://github.com/jekyll/jekyll-feed)
* Toggleable subscribe button (requires an external service)
* Code Syntax Highlight with [highlight.js](https://highlightjs.org/)
* Support for Google Analytics tracking
* Support for Disqus comments (not Ghost standard)


## Getting Started

### Deployment

**Important:**  For security reasons, Github does not allow plugins (under `_plugins/`) when
deploying with Github Pages. This means:

**1)** that we need to generate your site locally (more details below) and push the resulting
HTML (the contents of `_site/` or `../jasper2-pages/`) to a Github repository, that GitHub Pages
then host;

**2)** built the site with [travis-ci](https://travis-ci.org/) (with goodies from
[jekyll-travis](https://github.com/mfenner/jekyll-travis)) automatically pushing the
generated HTML files to a *gh-pages* branch.
This later approach is the one I am currently using to generate the live demo.

**3)** deploy the static website with Jekyll-compatible hosters, such as https://www.netlify.com/, that allow for deployment from the Github repo and publish the website using CDNs. Netlify has a free starter offer.

For option **1)** simply clone this repository (*master branch*), and then run
`bundle exec jekyll serve` inside the directory. Upload the resulting `_site/` (or `../jasper2-pages/`)
contents to your repository (*master branch* if uploading as your personal page
(e.g. username.github.io) or *gh-pages branch* if uploading as a project page
(as for the [demo](https://github.com/jekyller/jasper2/tree/gh-pages)).

For option **2)** you will need to set up travis-ci for your personal fork. Briefly all you
need then is to change your details in *[\_config.yml](_config.yml)* so that you can push
to your github repo. You will also need to generate a secure key to add to your
*[.travis.yml](.travis.yml)* (you can find more info on how to do it in that file).
Also make sure you read the documentation from
[jekyll-travis](https://github.com/mfenner/jekyll-travis). This approach has clear
advantages in that you simply push your file changes to GitHub and all the HTML files
are generated for you and pushed to *gh-pages*. Also you get to know if everything is
still fine with your site builds. Don't hesitate to contact me if you still have any
issues (see below about issue tracking).

### Author Pages

In order to properly generate author pages you need to rename the field *author* in the
front matter of every post to match that of your each author's *username* as defined
in the *[\_data/authors.yml](_data/authors.yml)* file.
With the latest update, multiple author blogs are now supported out of the box.

### Compiling Styles

Following on the way Casper styles are compiled as [described here](https://github.com/tryghost/casper#development):

Jasper2 styles are compiled using Gulp/PostCSS to polyfill future CSS spec. You'll need Node and Gulp installed globally. After that, from the theme's root directory:

```bash
$ npm install
$ gulp
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

## Issues and Contributing

This install builds well with Ruby v2.5.1 and Jekyll v3.7.4. If you run into any problems
please log them on the [issue tracker](https://github.com/jekyller/jasper2/issues).

Feel free pull-request your patches and fixes.

## Thanks


Many thanks to the Ghost team for all the design work. Also many thanks to all contributors,
that help keeping the project alive and updated :smile:


## Copyright & License

Same licence as the one provided by Ghost's team. See Casper's theme [license](GHOST.txt).

Copyright (C) 2015-2018 - Released under the MIT License.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
