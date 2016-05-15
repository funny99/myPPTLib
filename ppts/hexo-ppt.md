title: hexo
speaker: gongjuan
url: https://github.com/funny99/myPPTLib
transition: glue
files: 
theme: colors

[slide]

# hexo
----
Hexo是一个快速、简洁且高效的博客框架（静态博客生成器）。Hexo使用Markdown解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

[slide data-transition="cards" data-outcallback="outCB" data-incallback="inCB"]

# 为什么选择hexo
----
* 不用配置服务器 {:&.moveIn}  
* 不用数据库
* 访问速度相当快
* 没有安全性可言
* 使用户可更注重博客内容
* 支持markdown

[slide]

## 使用教程1-环境配置
----
1. 安装node
2. 安装Git

[slide]

## 使用教程2-GitHub
----
1. 注册账号
2. 新建仓库（name必须和用户名一致，如果你的用户名为‘zhangsan’，那么仓库名字为：‘zhangsan.github.io’）
3. 添加SSH公钥（避免后续提交代码时每次都要输入用户名密码）

[slide]

## 使用教程3-安装、初始化hexo
----
1. 安装hexo
```html
npm install -g hexo
```
2. 初始化hexo
```html
hexo init <folder>
```
&lt;folder&gt;为放blog代码的目录。也可以直接cd到这个目录，执行
```html
hexo init
```

[slide]

![hexo_mulu](/img/hexo_mulu.png)

[slide]

## 使用教程4-生成静态页面并本地启动
----
1. 生成静态页面
```html
hexo generate
```
或
```html
hexo g
```
2. 本地启动
```html
hexo server
```
或
```html
hexo s
```
在浏览器输入 http://localhost:4000 就可以看到你的博客啦

[slide]

## 使用教程5-部署
----
1. 与github建立关联  
在项目根目录下找到配置文件_config.yml，找到最后deploy，修改成
```html
deploy: 
	type: git
	repository: <您的github仓库地址>
	branch: master
```
<font color=red>修改配置文件时注意YAML语法，参数冒号:后一定要留空格！！</font>
2. 安装插件
```html
npm install hexo-deployer-git --save
```
3. 部署
```html
hexo deploy
```
在浏览器输入 http://<您的github仓库名称> 就可以看到你的博客啦
4. 每次部署可以按如下三个步骤来执行
```html
hexo clean
hexo generate
hexo deploy
```

[slide]

# 写博客 
----
新建一篇文章 {:&.flexbox.vleft}
```html
hexo new post "myFirstBlog"
```
以上会在/source/_posts/下生成文件 myFirstBlog.md。现在开始写文章了，首先熟悉下markdown语法
&ensp;   
[markdown的语法介绍](http://wowubuntu.com/markdown/ "markdown语法介绍") {:&.flexbox.vleft}

[slide]

# markdown简介
----
markdown是一种用来写作的轻量级「标记语言」 
* 专注你的文字内容而不是排版样式
* 轻松的导出HTML、PDF和本身的.md文件
* 纯文本内容、兼容所有的文本编辑器和字处理软件
* 可读，直观。适合所有人的写作语言  
**编辑器推荐**  
* mac： Mou
* windows： MarkdownPad MarkPad
* web端： [简书](http://www.jianshu.com/ "简书主站")

[slide]

# markdown语法
---- 
&ensp;  
<iframe data-src="http://funny99.github.io/2016/04/30/markdown-grammar/" src="about:blank;"></iframe>

[slide]

# 切换主题
----
1. 下载主题（这里以modernist为例）
```html
git clone https://github.com/heroicyang/hexo-theme-modernist.git themes/modernist
```
2. 在配置文件中修改默认主题
打开_config.yml,修改
```html
theme: modernist
```
3. 主题介绍  
https://github.com/hexojs/hexo/wiki/Themes   
https://www.zhihu.com/question/24422335  

[slide]

# 使用评论系统
----
以 多说 为例
在多说设置你的short_name（在 http://duoshuo.com/create-site/ 自己申请）  
copy一份通用代码，粘贴到你的/themes/modernist/layout/_partial/comment.ejs里面

[slide style="background-image:url('/img/bg1.png')"]

## 谢谢
