---
title: nginx
date: 2016-10-18 00:24:25
tags:
	- nginx
	- 入门	
categories:
	- nginx	
---

nginx 常用知识点

# rewrite

  语法：
    regex replacement flag 第一个代表匹配的路径，第二个代表转发的路径 只对相对路径进行匹配,不包含hostname  ,querystring
    flag: last,break,redirect,permanent
    last : 相当于Apache的[L]标记，表示完成rewrite
	break : 停止执行当前虚拟主机的后续rewrite指令集
	redirect : 返回302临时重定向，地址栏会显示跳转后的地址
	permanent : 返回301永久重定向，地址栏会显示跳转后的地址 
	last vs break
	   last其实就相当于一个新的url，对nginx进行了一次请求，需要走一遍大多数的处理过程，最重要的是会做一次find config，提供了一个可以转到其他location的配置中处理的机会，而break则是在一个请求处理过程中将原来的url(包括uri和args)改写之后，在继续进行后面的处理，这个重写之后的请求始终都是在同一个location中处理。
  指令位置：
    localtion，server，if


# proxy:
    在nginx中配置proxy_pass时，如果是按照^~匹配路径时,要注意proxy_pass后的url最后的/,当加上了/，相当于是绝对根路径，则nginx不会把location中匹配的路径部分代理走;如果没有/，则会把匹配的路径部分也给代理走