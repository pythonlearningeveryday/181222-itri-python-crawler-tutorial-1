# 181222-day2-quiz

## 1. 為什麼 Python 程式語言要分成 Python2, Python3 不同的版本，使用上有什麼問題？
1.新舊版本的分別.
2.互不相容.

## 2. 完成以下填空：

- 使用者在看瀏覽網站的操作行為，使基於【＿HTTP__】  協定：
- 使用者在瀏覽器上輸入網址…
- [使用者/Client side] 發送 【＿request＿】 給 [網站伺服器/ Server side]
- [網站伺服器/ Server side] 回傳 【＿response＿】給 [使用者/Client side]
瀏覽器將內容處理之後顯示給使用者…

## 3. 請問動態網頁爬蟲跟靜態網頁爬蟲主要的差別是什麼？
1.靜態網頁:是指沒有包含動畫(Flash動畫或Gif動畫)的純文字及圖片網頁。
2.動態網頁:係指包含網頁程式(如ASP、PHP、ASP.Net…等)及資料庫的純文字及圖片網頁。


## 4. 動態網頁爬蟲跟靜態網頁爬蟲的爬蟲策略有什麼差別？
1.靜態網頁:直接解析html。
2.動態網頁:採用第三方的工具,模擬瀏覽器的行為,去載入資料。

## 5. 找一個網站，說明哪些內容是可以透過靜態方式取得？哪些是需要透過動態方式取得？
1.可靜態取得:https://tw.sports.appledaily.com/realtime/20181225/1489222/
2.須動態取得:https://tw.appledaily.com/


## 6. 實作題：利用 Yahoo! 電影，取出本週熱門新片的「中英文名稱」、「上映日期」、「期待度」、「滿意度」，還有「封面照片網址」，並印出。用一個你覺得適合的型態存到一個變數內。

```
import requests
from bs4 import BeautifulSoup

res = requests.get('https://movies.yahoo.com.tw/movie_thisweek.html')
soup = BeautifulSoup(res.text.strip())

for item in soup.select('.release_info'):
    print (item.select('.btn_s_introduction')[0].text.strip()) #上映日期
    print (item.select('.gabtn')[0].text.strip()) #中文片名
    print (item.select('.release_movie_time')[0].text.strip()) #期待度
    print (item.select('.leveltext')[0].text.strip()) #網友想看
    
for cover in soup.select('img'): #電影封面網址
    print(cover)
```

## 7. 實作題：利用 104 人力銀行，計算出台中市用「資料」關鍵字可以找到的公司數量有幾個？

```
import requests
from bs4 import BeautifulSoup

res = requests.get('https://www.104.com.tw/jobs/search/?ro=0&kwop=7&keyword=%E8%B3%87%E6%96%99&area=6001008000&order=1&asc=0&page=2&mode=s&jobsource=joblist_b_relevance')
soup = BeautifulSoup(res.text.strip())

for item in soup.select('#js-job-header'):
    print (item.select('.js-txt')[0]) #total companies
```





