---
title: 使用latex来生成毕业论文的一点点经验
author: 崩溃了几百次的嘉奕
date: '2019-01-15'
slug: latex-graduation-thesis
categories:
  - code
tags:
  - latex
  - fun
---
### **引言**  
其实呢，是拖延症导致本人时不时想玩耍偷懒好吃懒做好逸恶劳骄奢淫逸，可是纯玩吧又太内疚太空虚，于是想到用latex排版咯，感谢前辈们铺平的康庄大道！  
排版过程中遇到过各种各样的问题，很令人抓狂，但解决过程又让人欲罢不能！所以决定记下来解决方法，希望以后再翻看时有所收获，如果有益于后人那便更好。  

\#latex用久了又快要忘了markdown了……木鱼脑子真是名副其实呀！  

**一些个人习惯**  
debug的时候，如果需要步骤 >= 3，那本木鱼脑子是肯定记不住回去的路的，所以会复制一个duplicate文件夹用来折腾。理想状态是有台备用电脑啦，可是本木鱼现在的水平还没资格。  
此方法得到了家父科班认证。一脸得意。  

**系统信息**  
0. 源代码：[上海交通大学 XeLaTeX 学位论文及课程论文模板](https://github.com/sjtug/SJTUThesis)  
1. macos 10.14.2 (18C54)  
2. MacTeX-2018  
3 Atom editor  
4. 编译用latexmk或xelatex    
5. 参考文件生成使用BibDesk  
<sup>如果有时间我想尝试sublime 嘻嘻

**终于到正文了**  
常见问题可以搜索[issues栏目](https://github.com/sjtug/SJTUThesis/issues?utf8=✓&q=参考文献)  
  
* 自定义标题  
问题场景：原模版“主要符号对照表”，本医学狗需要改成“缩略语中英文对照”。  
解决方法：找到thesis.cls 修改相关内容
  
* 文献引用  
  _在github的教程中是这样描述的：_  
用户将论文中需要引用的参考文献条目，录入纯文本数据库文件 (bib 文
件)。 --> 调用xelatex对论文模板做第一次编译，扫描文中引用的参考文献，生成参
考文献入口文件 (aux) 文件。--> 调用 bibtex，以参考文献格式和入口文件为输入，生成格式化以后的参考
文献条目文件 (bib) -->再次调用 xelatex 编译模板，将格式化以后的参考文献条目插入正文。   
我自己遇到的问题场景是：1.无法编译我自定义的bib文件, 2.bibtex无法编译后续的aux文件  
解决方法：创建.bib文件，使用BibDesk再生成bib文件；调用latexmk对模版thesis.tex进行编译；调用*biber*对thesis.bcf文件进行编译；再次调用latexmk对模版tesis.tex进行编译，就可以啦。引用command包括\cite和\parencite（这是一句废话）  
感谢：[github@double-free](https://github.com/double-free)，[这是](https://github.com/sjtug/SJTUThesis/issues/204)相关帖子，[这是](https://www.jianshu.com/p/50464c7c5ffe)具体解决方法链接。  
------------以下1.16更新  
3. citekey问题
问题场景：（前提是我现在没搞明白bibtex怎么编译）我用googlescholar来生成.bib，再用bibdesk这个软件生成.bib file时，citekey会提示unexpected
解决方法：生成原始bibtex的时候对cite key进行修改，修改成英文就好。  
4. export in batches @ googlescholar  
问题场景：每条文献手动编辑要疯  
解决方法：search-->"star"" the paper --> go to "My Library" in the left-side bar --> select all on the top bar --> export as BibTeX;尝试了百度学术同理，而且百度学术导出的bibtex还带abstract。