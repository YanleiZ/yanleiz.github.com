---
layout:     post
title:      Spring使用AOP需要的第三方jar包
date:       2017-01-03 09:28:10
summary:    Spring使用AOP需要的第三方jar包
categories: jekyll
thumbnail: jekyll
tags:
 - Java
 - 笔记
---

使用Spring的AOP，在官网下载的Spring4.15，写了一段AOP的代码老是报错，网上搜了下发现Spring从3.1开始不再集成第三方的jar包，
除了Spring提供的spring-aop-4.1.5.RELEASE.jar以外，还需要添加[aspectjrt.jar](http://www.java2s.com/Code/Jar/a/Downloadaspectjrtjar.htm)、
[aspectjweaver.jar](http://www.java2s.com/Code/Jar/a/Downloadaspectjweaverjar.htm) 、 [aopalliance.jar](http://www.java2s.com/Code/Jar/a/Downloadaopalliancejar.htm) 
三个jar文件和动态代理的[cglib.ja](http://www.java2s.com/Code/Jar/c/Downloadcglib22jar.htm)。
