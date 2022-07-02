---
title: Github page 搭配 Google domain 自訂網域
date: 2022-06-29 23:26:47
categories: 架站
tags: 
urlname: google-domain-tutorial
---

![cover](cover.png)

本來以為只要買完網域設定後，在github repo設定就ok了
但殊不知在買網域的過程中和買完網域後都有踩了一些沒想過的問題，所以就順手紀錄當作備忘錄
一開始看了一些教學文發現有些資訊已經跟現在有點不太一樣，所以打算自己重寫一篇，不過後來又看到一篇不錯的文章於是作罷改為整理資訊與步驟的形式
推[完整教學文](https://kulan.dev/b200603/)

<!--more-->

## 為何選擇Google Domain

如果上網搜尋買網域平台，最有名的大概是[GoDaddy](https://tw.godaddy.com/)，只不過價錢就比較貴一些
另外比較可靠的選擇還有[Namecheap](https://www.namecheap.com/)，價格便宜之外也有提供免費WhoIS Guard隱私保護

但! 最終改變心意的一點是朋友在當時剛好買了[Google domain](https://domains.google/)，而且他們有提供信箱轉址的服務!
可以直接在Google domain中設定像是`<custom_name>@chienwu.dev`的自訂信箱，以及別人寄到這信箱時要轉送的真正信箱。
這樣對外就可以使用一個看起來更簡潔專業的信箱了! (小時候設定的gmail名稱真的是包含太多個人資訊又很蠢xD)

## 設定步驟

1. 購買Google domain網域
2. Github page repo > setting > custom domain
3. Google Domains 設定 DNS
4. 回Github page檢查DNS審核狀態，開啟HTTPS

## issues

- Google Domains 目前仍不支援您所在的國家/地區
- Github page DNS check failed

## Notes

- 聯絡資訊的國家可以選擇台灣，不需造假填美國地址資料，也不必委屈被當成中國一省，那麼就照實填寫吧，將來網域若引起糾紛留下的資料必須能讓 Google 聯繫上，且 Google Domains 提供隱私保護，這些資料不會被查詢到
- [美國郵遞區號查詢](https://tw.nowmsg.com/us_zip.asp)

## 參考

第一篇看的教學文，資料有點舊了，填寫地址的欄位有點不太一樣，但還是列出給大家參考
[Google Domains 台灣可以使用了﹍購買 + 轉移網域(Godaddy) + DNS 設定心得](https://www.wfublog.com/2019/04/google-domains-tw-purchase-transfer-godaddy-dns.html)
