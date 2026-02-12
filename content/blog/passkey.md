---
title: "Passkey"
date: 2024-04-27
draft: false
categories:
    - security
---
來到了2024年，你還在用一個密碼登入所有網站嗎?
來看看 Passkey 可以怎麼幫助你。

首先，我們來看看密碼的問題：
- 你有多少個密碼?
- 你的密碼有多長?

我們都聽密碼要長，要複雜，但是你真的能記得所有密碼嗎?許多人會用相同的密碼登入不同的網站，這樣一旦有一個網站被駭客入侵，你的所有帳號都會被盜走。

你可以去 [haveibeenpwned](https://haveibeenpwned.com/Passwords) 這個網站看看你的密碼有沒有被外洩過，如果有，你就應該趕快換掉。因為根據統計，有81%的資料外洩事故跟遺失密碼有關[Report](https://locker.io/blog/10-password-statistics-2022)

現在我們了解到密碼的問題，那麼 Passkey 可以怎麼幫助你呢?密碼學家發明了公鑰加密，一個簡單的解釋是，你可以產生一組公鑰和私鑰，你可以把公鑰給別人，別人可以用公鑰加密訊息，但是只有你的私鑰可以解密。這樣你就不用擔心密碼被盜了。比如說Bob公開了他的公鑰P，Alice用P加密了一個訊息M，只有Bob的私鑰S才能解密M。這樣子Alice就可以驗證這個訊息是Bob發出的。

為了方便使用，我們可以使用Google或是Apple的Passkey，這樣你就不用自己管理公鑰和私鑰了。

首先，我們來看看Google的Passkey怎麼設定：
在你的手機上登入 Google的帳號，點選進入 [Passkey](https://www.google.com/account/about/passkeys/)，然後點選"取得密碼金鑰"，之後就可以利用手機的指紋或是臉部辨識來登入你的帳號。

設定完Passkey之後，我們來看看如何使用Passkey登入網站，以下是露天拍賣的[設定步驟](https://www1.ruten.com.tw/help/member/9503/)。用手機網頁或是露天App進入登入後就可以設定。

既然Passkey這麼方便，為什麼不試試看呢? 目前唯一的理由就是支援Passkey的網站還不夠多，但是隨著時間的推移，我相信Passkey會變得越來越普及。
