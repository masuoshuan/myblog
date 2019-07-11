title: git比svn的优势
date: 2016-05-22 11:13:00
tags: others
categories: 开发工具
---
** git比svn的优势：** <Excerpt in index | 首页摘要>
    主要介绍svn和git在使用的时候一些区别
<!-- more -->
<The rest of contents | 余下全文>

## 合并操作时对提交过程的保留
- git:合并操作保留原有的提交过程
- svn:多个提交合并为一个提交
- 不用因为合并操作而导致追踪的困难

## 修正提交
- git：可以修正提交。  
使用功能分支工作流，在自己的分支可以方便修正提交而不会影响大家。
- svn：一旦提交就到服务器上，实际使用中就是不能修改  
（svn可以在服务器上修改，因为过程复杂需要权限实际上从不会这样做）


## 本地分支
- git可以方便的创建本地分支,创建时间极短,分支可以是本地的,不会存在svn中目录权限的问题

## 强大的合并能力
- git：重命名（无论文件还有目录）提交 可以合并上 文件重命名前的这些文件的提交

- svn：重命名（无论文件还有目录）提交后，你本地/或是分支上 有文件重命名前的这些文件的修改或提交，在做合并操作时,你会碰上传说中难搞的***树冲突***！

- 这就导致在调整目录名称和类名调整的时候比较繁琐,需要告诉大家,我修改完以后你再修改


## tag的支持

- svn在模型上是没有分支和tag的。tag是通过目录权限限制（对开发只读）来保证不变。
- git模型上一等公民支持tag，保证只读。

## 速度优势

- git的提交是个本地提交,相对svn来说如闪电一般
- git提供了暂存区,可以方便制定提交内容,而不是全部内容

## 日志查看
- git：本地包含了完整的日志，闪电的速度（并且无需网络)
- svn：需要从服务拉取。
- 一旦用了git后，等待svn日志过程简直让我发狂