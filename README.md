
## 取得檔案庫

根據 [github pages](https://pages.github.com/) 的說明，個人專案的靜態檔案是放置在 master 這個分支下，因此原始檔案便放置在 source 這個分支下。
clone repository 後必須切換分支才能正確編輯檔案。

```
git clone --recursive --branch source https://github.com/shian/shian.github.io.git
```

## 撰寫文章

* 使用 `hexo new draft <title>` 來建立草稿文件，檔案會建立在 source/_draft 下。
* 撰寫文章時可執行 `hexo server --draft` 並透過 http://0.0.0.0:4000 來確認文章呈現的結果。
* 撰寫完成後執行 `hexo publish <title>` 來發布草稿，此時檔案會移動到 source/_posts 下。

## 建立網站並發布到 github

* 執行 `hexo generate` 來將文章轉成靜態頁面。
* 執行 `hexo deploy` 將文章發布到 github page。

## 參考連結

* [Github Pages] (https://pages.github.com/)
* [Hexo] (http://hexo.io/)
* [Markdown basics] (https://help.github.com/articles/markdown-basics/)
* [Github Flavored Markdown] (https://help.github.com/articles/github-flavored-markdown/)

