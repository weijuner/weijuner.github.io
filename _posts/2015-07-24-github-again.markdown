---
layout:     post
title:      "还是github"
subtitle:   "github"
date:       2015-07-24
author:     "weijuner"
header-img: "img/20150722.jpg"
categories: [github]
tags:
    - github
---
# 还是github


    git remote add origin <server>
    git checkout -b feature_x
    git branch -d feature_x

要更新你的本地仓库至最新改动，执行：

    git pull

要合并其他分支到你的当前分支（例如 master），执行：

    git merge <branch>

在合并改动之前，也可以使用如下命令查看：

    git diff <source_branch> <target_branch>

假如你做错事（自然，这是不可能的），你可以使用如下命令替换掉本地改动：

    git checkout -- <filename>
此命令会使用 HEAD 中的最新内容替换掉你的工作目录中的文件。已添加到缓存区的改动，以及新文件，都不受影响。
假如你想要丢弃你所有的本地改动与提交，可以到服务器上获取最新的版本并将你本地主分支指向到它：

    git fetch origin
    git reset --hard origin/master

reset命令有3种方式：

    git reset --mixed：
此为默认方式，不带任何参数的git reset，
即时这种方式，它回退到某个版本，只保留源码，回退commit和index信息

    git reset --soft：
回退到某个版本，只回退了commit的信息，不会恢复到index file一级。如果还要提交，直接commit即可

    git reset --hard：
彻底回退到某个版本，本地的源码也会变为上一个版本的内容


以下是一些reset的示例：

(1) 回退所有内容到上一个版本  

    git reset HEAD^  
(2) 回退a.py这个文件的版本到上一个版本
  
    git reset HEAD^ a.py
  
(3) 向前回退到第3个版本
  
    git reset –soft HEAD~3
  
(4) 将本地的状态回退到和远程的一样
  
    git reset –hard origin/master
  
(5) 回退到某个版本
  
    git reset 057d
  
(7) 回退到上一次提交的状态，按照某一次的commit完全反向的进行一次commit
  
    `git revert HEA`D   


在本地开发了一个版本，然后加入某些代码， git commit 之后再 git push 与远程版本库同步，这时出现一个问题，在这次 git commit 之前的版本内容如何找回？
首先git log显示提交的历史

    commit ee50348120302b19318ab6a564d4092dd87a85ef
    Author: ShichaoXu <gudujianjsk@gmail.com>
    Date:   Mon Jun 3 15:18:16 2013 +0800
    
    support for printf
    
    commit e7a5e492c742a7b68c07f124edd4b713122c0666
    Author: ShichaoXu <gudujianjsk@gmail.com>
    Date:   Tue May 7 15:44:11 2013 +0800
    
    del file lib/2440slib.s init/2440init.s
    
    commit 5a05f002ef1dfbbf118b2ffd7b829159b727ce16
    Author: ShichaoXu <gudujianjsk@gmail.com>
    Date:   Tue May 7 15:26:30 2013 +0800
    
    change file name lib/2440slib.s init/2440init.s to lib/2440slib.S init/2440init.S
    
    commit a948e62c9eabd54bfc4de3c4dfd14b4fc2bb48dd
    Author: ShichaoXu <gudujianjsk@gmail.com>
    Date:   Tue May 7 15:06:17 2013 +0800
    
    add code for this project
    
    commit 59a902efdef8fb3dd47264df8a666de7026d1595
    Author: ShichaoXu <gudujianjsk@gmail.com>
    Date:   Mon May 6 23:15:01 2013 -0700
    
    Initial commit
    
    Initial commit
  
然后用
 
`~/gun-ucos$$git reset --hard e7a5e492c742a7b68c07f124edd4b713122c0666`  

显示如下
    
    HEAD is now at e7a5e49 del file lib/2440slib.s init/2440init.s  


此时正常回到git commit    "support for printf" 之前的状态！


**国际惯例**


![img](/img/20150724.jpg)