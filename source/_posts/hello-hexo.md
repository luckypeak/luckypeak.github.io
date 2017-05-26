---
title: hello hexo
date: 2016-09-18 10:30:19
tags: 
  - hexo 
  - 入门
categories: 
  - hexo
---

hexo 搭建过程过程遇到的一些问题，记录一下


## hexo 本地运行浏览器打不开
hexo启动，控制台没有报错，但是浏览器打不开。
hexo 默认使用 4000端口，有可能是端口被占用了，window下使用 

{% codeblock %}
 netstat -ano | findstr "4000"
{% endcodeblock %}

```bash
netstat -ano | findstr "4000"
```
 查看端口当前的进程。

或者可以直接使用 -p 指定端口

```
hexo s -p 指定端口
```

## 不同机器使用Hexo

在git建两个分支：
init分支管理源文件 日常修改可以 git push origin init
master分支存放网站静态代码。修改_config.yml 修改deploy 分支为master。hexo deploy 到master。

当使用新机器时候，不要直接hexo init。安装下面顺序执行
	
```
git checkout init 
npm install hexo  
npm install

```

