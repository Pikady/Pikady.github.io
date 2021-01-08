---
title: environment
date: 2021-01-08
categories: [Blogging,Tutorial]
tages:[writting]
---



# 个人博客搭建

通过git+github+jekyll+markdown搭建写作环境，在一个文件编辑器（可能是Atom）中通过markdown语法写作，然后更新到个人博客网站中

## 探索（踩坑）步骤

### 一、搭建jekyll环境

#### 1.下载相关软件

* 下载[ruby(按照网页推荐下载)](https://rubyinstaller.org/downloads)
* 下载[MSYS2](http://repo.msys2.org/distrib/x86_64/msys2-x86_64-20161025.exe)

#### 2.安装Ruby和MSYS2
一路Next安装ruby及MSYS2。
安装完ruby后悔弹出一个窗口，输入3，然后回车
！[](https://blog.walterlv.com/static/posts/2018-03-04-12-14-41.png)
经过一段等待时间，出现以下，说明安装成功。

``` Install MSYS2 and MINGW development toolchain succeeded```

#### 3.安装Jekyll
点击桌面左下角搜索，输入`run`，输入`cmd`
输入`gem -v`
输入`gem install jekyll`安装jekyll
输入`jekyll -v`查看jekyll是否安装成功以及版本
输入`gem install jekyll bundler`安装jekyll依赖包
输入`bundler -v`查看依赖包是否安装成功以及版本

### 二、 git安装

#### 1.安装Git环境
[Git下载](https://git-scm.com/downloads)
安装
桌面右击出现两个git则安装成功

#### 2.Git基础知识
**Git工作区域：工作区——暂存区——GIt仓库**

比如说现在有一个文件叫“hello.php”
`git status`查看文件当前状态
`git add hello.php`把文件由工作区提交到暂存区
`git add --all`
`git status`查看文件当前状态
`git commit -m"添加描述"`把文件从暂存区提交到仓库

#### 3.Git初始化

(1)基本信息设置

* 选择一个文件夹，新建文件夹。如：test
* 设置用户名
`git config --global user.name 'Pikady'`

* 设置用户名邮箱
`git config --global user.email '2652917633@qq.com'`

* 查看设置是否成功
`git config --list`

(2)初始化git

在test中打开git命令栏，输入`git init`，创建了一个隐藏文件夹.git。如看不见，设置电脑显示隐藏文件

(3)git本地基础操作

* 向仓库中添加文件
`touch a1.md`添加一个a1.md的文件
`rm a1.md`删除a1.md的文件
2次提交到仓库

* 修改仓库文件
修改文件后，输入`git status`，显示有文件修改。文件修改后默认回到了工作区，再通过两次提交到仓库

* 删除仓库文件
`rm a1.md`删除文件
`git rm a1.md`从仓库中删除文件
`git comment -m"提交描述"`提交操作

* git管理远程操作
`git push`上传到github

### 三、Github Pages搭建网站

搭建步骤
1. 创建个人站点：新建仓库，仓库名为：Pikady.github.io
2. 在仓库下新建index.md文件
3. 点击”仓库“，点击”settings“，点击”change theme“，建立网站成功

### 四、使用jekyll搭建网站

1. 新建一个新的jekyll网站`jekyll new myblog`
2. 进入新目录`cd myblog`
3. 建立站点`jekyll server`或`bundle exec jekyll serve`

### 五、复制模板重新创建网站
jekyll模板分析


### 六、尝试添加上传文章

### 七、进阶：使用atom编辑器进行操作





## 第二次尝试
已有背景：已搭建好jekyll环境，git安装好

### 一.克隆主题
1. 找到jekyll主题，fork下来
2. 将该仓库名改为pikady.github.io
3. clone到本地
`$ git clone ...`

### 二.试运行
`$ jekyll serve`
如出现运行错误，根据提示运行`bundle update`

### 三.github pages 部署
在文件里有一个‘.github/workflows’的文件夹
我们通过在本地push任意的文件（commit）到origin/master，来触发github actions workflows。触发完成，会出现github网页上会新建了一个`gh-pages`的分支

在设置中将`gh-pages`作为github pages的默认分支

### 四.在本地修改相关内容
注：***不要本地与github线上同时修改***
同时修改的补救措施
1. 把增删的文件发送到线上（使用`git rm` 进行删除）
2. 然后通过`git pull origin master``git merge`等一系列操作进入到一个弹窗界面，需要你输入
* 按i键，进入插入（insert）描述操作，可以选择不输入
* 按Esc键，结束插入描述操作
* 按:wq，表示保存并结束本次操作
* enter键即可结束本次错误信息
3. `git push`