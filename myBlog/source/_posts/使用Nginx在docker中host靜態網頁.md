---
title: 使用Nginx在docker中host靜態網頁
date: 2022-06-15 23:09:31
categories:
tags:
- nginx
- docker
urlname: host-html-in-docker-with-nginx
---

![nginx-hosting](nginx-hosting.png)

前陣子在公司新專案中引入了icon font，主要是為了讓單色icon圖檔的引用更加方便
由於平時只會把相關的style檔放在專案裡使用，偶爾想查找icon的class name時，就只能自己打開當初那包下載下來的zip去看demo.html有點不太方便

<!--more-->

如果有其他人也更新了icon font，那每次就只能再跟他要最新的icfont.zip來看
但前提是要先去問有沒有人更新過，實在是有點麻煩

印象中在先前的專案，是直接在內部某台server裡開一個port來host，所以這次想自己試看看

## Solution

通常為了避免汙染server環境，不同的服務我們都會習慣建立不同的docker去跑

Google直接搜尋"host html in docker with nginx"
第一篇文章就寫的滿簡單好懂了，但還是在這邊簡單用中文做個紀錄分享

### Step 1 - 建立資料夾 & 放入html檔

一般來說可以只放入一個index.html即可
但由於icfont下的demo.html需要依賴其他檔案，所以我選擇整包解壓縮後放入

![structure](structure.png)

### Step 2 - 建立Dockerfile

現在host server幾乎都是使用nginx了，但如果要使用Apache下方也有提供對應指令

第一行會指定要用的nginx image版本為alpine
第二行會將當前目錄的所有檔案放進`/usr/share/nginx/html`

(確保你建立的Dockerfile跟html位於同個目錄下，否則以下範例指令需要自行修改)

**Use Nginx Web server**

```Dockerfile
FROM nginx:alpine
COPY . /usr/share/nginx/html
```

**Use Apache Web server**

```Dockerfile
FROM apache
COPY . /var/www/html
```

### Step 3 - build docker image

```bash
docker build -t html-server-image:v1 .
```

可以使用`docker images`檢查剛剛指定的html-server-image是否成功被建立
也可以自行換成別的image name

![image-good](image-good.png)

### Step 4 - Run the Docker Container

這邊docker的外部port對應不使用80改用5555，避免檔到其他服務

```bash
docker run -d -p 5555:80 html-server-image:v1
```

### Step 5 - Test the Port

可以下curl檢查是否返回正確的html，或是直接去localhost:5555看
如果當初你放入的是index.html，那你應該會看到對應的內容出現
不過因為icfont下載完後的網頁檔是demo.html，因此在port 5555會看到的是nginx預設的html內容
要記得到localhost:5555/demo.html才會顯示icon font的網頁

```bash
curl localhost:5555
```

![curl-host](curl-host.png)

![nginx-success](nginx-good.png)

## Refference

[Steps for Deploying a Static HTML Site with Docker and Nginx](https://www.dailysmarty.com/posts/steps-for-deploying-a-static-html-site-with-docker-and-nginx)
