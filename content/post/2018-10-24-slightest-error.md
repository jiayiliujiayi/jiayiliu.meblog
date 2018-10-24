---
title: 差之毫厘谬之千里
author: Jiayi
date: '2018-10-24'
slug: slightest-error
categories:
  - code
tags:
  - reflection
---

前天想在主题栏多加两个个选项（eg. blog，about，weibo），就更改了config文件，也没太在意细节，直接按照github的简介来着；而后又加了一篇博文。commit和push都没问题。最终，无论如何也无法deploy。推测了几个可能：检查了variable里的hugo version，重新开始一个deployment，删除了可疑的最新博文，但还是部署失败。

问题一直持续到今天（昨天很鸵鸟，借着饱暖思淫欲的借口）。试着deploy了local branch，成功，再试master branch，失败。结论是master branch有问题。

再在一个个commit查找，到底是哪里有问题。最终找到一个最最可疑的内容：

总结

