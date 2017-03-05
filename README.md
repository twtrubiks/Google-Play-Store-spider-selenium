# Google-Play-Store-spider-selenium
抓取 [Google Play Store](https://play.google.com/store/apps/top) 資料 use [Selenium](http://selenium-python.readthedocs.io/index.html) on Python 📝  

並使用 SQLite 儲存 DB

* [Youtube Demo](https://youtu.be/bNTj-CtwX1w)
 
這個專案和 [Google-Play-Store-spider-bs4-excel](https://github.com/twtrubiks/Google-Play-Store-spider-bs4-excel) 類似，但這專案是使用  [Selenium](http://selenium-python.readthedocs.io/index.html) 結合  [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)。

之前我也介紹過 Selenium 的範例，可參考 [youtube-trends-spider](https://github.com/twtrubiks/youtube-trends-spider)，

因為 [Selenium](http://selenium-python.readthedocs.io/index.html) 有更新加上之前是使用python 2.7，寫法上也有點不同，所以這次使用 python 3.4.3 重新簡單介紹。

## 特色
* 透過 [Selenium](http://selenium-python.readthedocs.io/index.html) + [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) 抓取  [Google Play Store topselling_new_free ](https://play.google.com/store/apps/category/BOOKS_AND_REFERENCE/collection/topselling_new_free)資料。
* 使用 SQLITE 儲存資料。



## 安裝套件 
確定電腦有安裝 [Python](https://www.python.org/) 之後

clone 我的簡單範例

``` 
git clone https://github.com/twtrubiks/Google-Play-Store-spider-selenium.git
```

接著請在  cmd (命令提示字元) 輸入以下指令
``` 
pip install -r requirements.txt
```

## 使用 Selenium
建議看一下 [Selenium](http://selenium-python.readthedocs.io/index.html) 官方說明。

首先，必須安裝 [Selenium drivers](http://selenium-python.readthedocs.io/installation.html#drivers) ，請注意 <b>作業系統</b> 、 <b>位元數</b> 、 <b>瀏覽器</b>。

範例是使用 Firefox，需要額外將 [geckodriver.exe](https://github.com/twtrubiks/Google-Play-Store-spider-selenium/blob/master/geckodriver.exe) 這個 drivers 放入路徑底下，否則執行會出現錯誤。

```
profile = webdriver.FirefoxProfile()
profile.accept_untrusted_certs = True
driver = webdriver.Firefox(firefox_profile=profile)
driver.get(targetURL)
```

如果修改成 Chrome，需要額外將 [chromedriver.exe](https://github.com/twtrubiks/Google-Play-Store-spider-selenium/blob/master/chromedriver.exe) 這個 drivers 放入路徑底下，否則執行會出現錯誤。

```
options = webdriver.ChromeOptions()
options.add_argument('--ignore-certificate-errors')
driver = webdriver.Chrome(chrome_options=options)
driver.get(targetURL)
```

IE的部分我一直沒有測試成功，所以這裡我們暫時跳過。
  
以上方法是參考  [how-to-deal-with-certificates-using-selenium](http://stackoverflow.com/questions/24507078/how-to-deal-with-certificates-using-selenium)

## 使用方法 以及 執行畫面

``` 
python app.py
```
執行畫面

![alt tag](http://i.imgur.com/frCEqu7.jpg)

在執行時，背景會跳出一個瀏覽器，<b>請不要去亂點他(或關閉他)，抓完資料瀏覽器會自動關閉</b>

![alt tag](http://i.imgur.com/tLXt0zM.jpg)

![alt tag](http://i.imgur.com/x9Tuyf8.jpg)

![alt tag](http://i.imgur.com/bhJJVXl.jpg)


執行完畢後，會將資料存在 app.db 裡，可以使用 [SQLiteBrowser](http://sqlitebrowser.org/) 觀看

![alt tag](http://i.imgur.com/PYOkVNN.jpg)



## 執行環境
* Python 3.4.3
* Windows 10

## Reference 
* [Selenium](http://selenium-python.readthedocs.io/index.html)
* [Flask-Migrate](https://flask-migrate.readthedocs.io/en/latest/) 
* [beautifulsoup4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
* [requests](http://docs.python-requests.org/en/master/)


## License
MIT license
