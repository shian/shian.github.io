title: "setup hexo"
date: 2015-04-12 00:10:25
tags:
---


安裝 hexo 
=========

請參考 hexo 的[文件](http://hexo.io/zh-tw/docs/)

設定 Github Pages
=================

參考 Github pages 的[說明](https://pages.github.com/)



建立用來存放源碼的分支
===================

~~~
git checkout --orphan source
~~~

將發布的檔案放到 master 分支上
===========================

~~~
git clone -b master <<REPO>> public
~~~

新增文章與發布
============

撰寫新文章時可以直接新增到 _post 中，只要不要 commit 到 master 中就好，這樣也方便在本地端測試。首先先用 hexo new 產生文章樣板，在編輯文章的時候隨時可以用 git 將其 commit 到 source 分支中進行保存。撰寫完成後在執行 hexo g 產生發布文件於 public 目錄中，最後將 public 目錄 commit 到 master 分支中並 push 到 github 上。



