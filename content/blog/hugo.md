+++
date = '2026-02-11T22:46:18+08:00'
draft = false
title = '轉移自己的 Blog 到 Hugo 上'
+++

# 摘要
看到 YWC 的[文章](https://ywctech.net/tech/start-hugo-site/)介紹如何用 Hugo 做自己的 blog，想說把目前用 python mkdoc 做的 blog 轉移過來。本來預期會花一整天做轉換，但是現在不愧是 AI 時代，我使用 VS Code 搭配 Claude，一個小時內就完成了。

# 轉移過程
## 匯入 markdown 文章
首先我要求 Claude 幫我把目前的 markdown 文章匯入到 Hugo 專案中。沒有遇到什麼問題，但是花了 5 分鐘才把所有的 markdown 文章都匯入完成，途中看到 Claude 花了不少時間在分析原本的專案的目錄結構，還好最後成功了，一開始 Claude 每次下指令都要問每次下指令都要問我，後來就直接授權給他了，這樣就不會每次都要問了。

## 首頁文章列表沒有顯示
轉移完成後執行 `hugo server`，發現首頁的文章列表沒有顯示出來，叫 Claude 看看是什麼問題，結果發現是因為沒有建立 _index.md 的關係，建立好之後就正常了，幫我省下很多查看文件的時間 ^^

## table of contents 沒有顯示
接著我發現文章裡的 table of contents 沒有顯示出來，我把 YWC 的文章截圖給 Claude 看，Claude 很快找到修正方法：在 hugo.toml 中設定 showTableOfContents = true。

# 部署
## 發布到 Cloudflare Pages
接下來我要把 Hugo 的專案部署到 Cloudflare 上。我們來參考 YWC 的文章，但是 Cloudflare 的設定方式已經跟 YWC 的介紹不同，所以我就直接要求 Claude 幫我部署。不過事情並沒有這麼順利，在途中遇到需要一個新的 API Key 的要求。

跟 Claude 討論，它建議這是新的部署流程，建議我用比較原始的方式來做就好。既然它沒辦法直接處理，我只好去看 Hugo 官方建議的 Cloudflare [部署方式](https://gohugo.io/host-and-deploy/host-on-github-pages/)，按照那個方式去做之後是 OK 的。

但是這時候又遇到問題，就是 Hugo 的模組 congo 並沒有正確安裝。經過 Claude 的指正之後，發現是要 `hugo mod get` 也順利解決了這個問題。

## 正確設定我的 Domain
發佈到 Cloudflare Pages 之後，會得到一個像是 homepage.jyunfan.workers.dev 的 domain。但是我想要用自己的 domain，於是我把 Porkbun 的 Nameserver 轉換到 Cloudflare 上， 很可惜，這一步還是手動問了 ChatGPT 才完成的，還沒有辦法用 Claude 讓我自動地都完成。