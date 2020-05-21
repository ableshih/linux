# Anaconda jupyter notebook

[1. 啟動](#啟動)  
[2. 安裝](#安裝)  
[3. 安裝套件](#安裝套件)  



[2. Numpy](#Numpy)  
[3. Pandas](#Pandas)  
[4. Matplotlib](#Matplotlib)  
[5. requests](#requests)  
[6. Spyder](#Spyder)  
[7. webdriver](#webdriver)  


課程  
http://moocs.nccu.edu.tw/course/123/intro  




## 啟動
```
開啟
Anaconda Prompt (anaconda3)

輸入
jupyter notebook

使用
會開出一個本地網頁
網頁 右邊 New -> python3
或在網頁目錄結構 往下找 *.ipynb 開啟舊檔
```






## 安裝

裝 x86 OK (裝 x64 開不起來)  

下載網頁 要移到最底下  
https://www.anaconda.com/products/individual  

Anaconda3-2020.02-Windows-x86_64  
https://repo.anaconda.com/archive/Anaconda3-2020.02-Windows-x86_64.exe  

所有版本  
https://repo.anaconda.com/archive/  




## 安裝套件
```
要用 以系統管理員身份執行

pip install selenium
pip install beautifulsoup4
pip install chromedriver
pip install requests
pip install pysqlite3
pip install matplotlib
pip install twstock
pip install requests-html
pip install Scrapy
pip install Scipy

python -m pip install -U pip setuptools
python -m pip install matplotlib

conda install -c conda-forge tqdm

swifter：加速你的數據處理
conda install -c conda-forge swifter
```








### Numpy
什麼是 Numpy 能快速操作多重維度的陣列 
數值運算套件，主要功能為陣列與向量運算   
```
pip install Scipy

scipy 和 pillow版本問題

先卸載舊版本：

pip uninstall scipy
pip uninstall pillow
重新安裝

pip install pillow==5.2.0
pip install scipy==1.1.0
```
https://numpy.org/  

Python Numpy Tutorial (with Jupyter and Colab)  
https://cs231n.github.io/python-numpy-tutorial/  

Hello NumPy  
https://ithelp.ithome.com.tw/articles/10222455  

Python 與 OpenCV 基本讀取、顯示與儲存圖片教學  
https://blog.gtwang.org/programming/opencv-basic-image-read-and-write-tutorial/  

從零開始學資料科學：Numpy 基礎入門  
https://blog.techbridge.cc/2017/07/28/data-science-101-numpy-tutorial/  

NumPy 簡介  
http://yltang.net/tutorial/dsml/7/  





### Matplotlib
Matplotlib(之後簡稱Matplot)  
畫圖功能最齊全，基本上沒什麼圖表畫不出來的  
圖表不好看(舊版的matplot很醜，但新版的matplot其實也算好看，尤其在style功能出來之後可以自行切換圖表的風格)  
畫圖指令複雜  

```
%matplotlib inline
圖都直接顯示在網頁的頁面

python -m pip install -U pip setuptools
python -m pip install matplotlib
```
多個範例  
https://gist.github.com/yehjames  

https://matplotlib.org/  

NumPy Matplotlib  
https://www.runoob.com/numpy/numpy-matplotlib.html  

用 Python 自學資料科學與機器學習入門實戰：Matplotlib 基礎入門  
https://blog.techbridge.cc/2018/05/11/python-data-science-and-machine-learning-matplotlib-tutorial/  

周沫凡  
https://morvanzhou.github.io/tutorials/data-manipulation/plt/  




### Pandas
```
Pandas 是 python 的一個數據分析 lib，2009 年底開源出來，
提供高效能、簡易使用的資料格式(Data Frame)讓使用者可以快速操作及分析資料，

主要特色描述如下：
1. 在異質數據的讀取、轉換和處理上，都讓分析人員更容易處理，
   例如：從列欄試算表中找到想要的值。
2. Pandas 提供兩種主要的資料結構，Series 與 DataFrame。
   Series 顧名思義就是用來處理時間序列相關的資料(如感測器資料等)，
   主要為建立索引的一維陣列。DataFrame 則是用來處理結構化(Table like)的資料，
   有列索引與欄標籤的二維資料集，例如關聯式資料庫、CSV 等等。
3. 透過載入至 Pandas 的資料結構物件後，可以透過結構化物件所提供的方法，
   來快速地進行資料的前處理，如資料補值，空值去除或取代等。
4. 更多的輸入來源及輸出整合性，
   例如：可以從資料庫讀取資料進入 Dataframe，也可將處理完的資料存回資料庫。

conda install -c conda-forge tqdm

swifter：加速你的數據處理
conda install -c conda-forge swifter

```
資料科學家的 pandas 實戰手冊：掌握 40 個實用數據技巧  
https://leemeng.tw/practical-pandas-tutorial-for-aspiring-data-scientists.html  

Pandas 基礎教學  
https://oranwind.org/python-pandas-ji-chu-jiao-xue/  

從 pandas 開始 Python 與資料科學之旅  
https://medium.com/datainpoint/%E5%BE%9E-pandas-%E9%96%8B%E5%A7%8B-python-%E8%88%87%E8%B3%87%E6%96%99%E7%A7%91%E5%AD%B8%E4%B9%8B%E6%97%85-8dee36796d4a  

Python Pandas 基本操作教學_成績表  
https://medium.com/@weilihmen/python-pandas-%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C%E6%95%99%E5%AD%B8-%E6%88%90%E7%B8%BE%E8%A1%A8-f6d0ec4f89  







### webdriver
操控瀏覽器 例 上一頁 下一頁 點一下
```
webdriver 的問題
1. 下載
	chrome: chromedriver
	https://chromedriver.chromium.org/downloads
	https://chromedriver.storage.googleapis.com/index.html?path=81.0.4044.138/
	https://chromedriver.storage.googleapis.com/81.0.4044.138/chromedriver_win32.zip
2. 解壓
3. copy to C:\Users\C940\chromedriver.exe
   為了省麻煩 copy chromedriver.exe 改名成 geckodriver.exe
4. 程式裡
	原 driverPath = 'D:\geckodriver\geckodriver.exe'
	   browser = webdriver.Firefox(executable_path=driverPath)
	改 driverPath = 'geckodriver.exe'
	   browser = webdriver.Chrome(executable_path=driverPath)
技
'C:\\Users\\C940\\h7_1.html'
```
python網路爬蟲教學-Selenium基本操作 參考  
https://freelancerlife.info/zh/blog/python%E7%B6%B2%E8%B7%AF%E7%88%AC%E8%9F%B2%E6%95%99%E5%AD%B8-selenium%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/  



### Spyder
```
Spyder
網頁爬蟲：你也可以輕鬆爬取台灣第一位武漢肺炎確診資訊
網路爬蟲只是用Python去模擬使用者操作瀏覽器的行為。其中抓資料的關鍵就是 “Get 請求”。 而我們這次就要帶大家實作一個廣義的網路爬蟲了！
```
地區年齡性別統計表-嚴重特殊傳染性肺炎-依個案研判日統計  
https://data.gov.tw/dataset/120711  
https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json  

輕鬆爬取台灣第一位武漢肺炎確診資訊  
https://medium.com/%E8%AA%A4%E9%97%96%E6%95%B8%E6%93%9A%E5%8F%A2%E6%9E%97%E7%9A%84%E5%95%86%E7%AE%A1%E4%BA%BAzino/%E7%AC%AC%E4%B8%80%E6%94%AF%E7%B6%B2%E9%A0%81%E7%88%AC%E8%9F%B2-%E4%BD%A0%E4%B9%9F%E5%8F%AF%E4%BB%A5%E8%BC%95%E9%AC%86%E7%88%AC%E5%8F%96%E5%8F%B0%E7%81%A3%E7%AC%AC%E4%B8%80%E4%BD%8D%E6%AD%A6%E6%BC%A2%E8%82%BA%E7%82%8E%E7%A2%BA%E8%A8%BA%E8%B3%87%E8%A8%8A-%E5%90%AB%E5%BD%B1%E7%89%87%E8%88%87%E7%A8%8B%E5%BC%8F%E7%A2%BC-b24ccf308025  
操作影片  
https://www.youtube.com/watch?v=7tZ_B3e6KkU&feature=emb_title  
Telegram聊天機器人超詳細懶人包  
https://medium.com/%E8%AA%A4%E9%97%96%E6%95%B8%E6%93%9A%E5%8F%A2%E6%9E%97%E7%9A%84%E5%95%86%E7%AE%A1%E4%BA%BAzino/telegram%E8%81%8A%E5%A4%A9%E6%A9%9F%E5%99%A8%E4%BA%BA%E8%B6%85%E8%A9%B3%E7%B4%B0%E6%87%B6%E4%BA%BA%E5%8C%85-%E5%95%86%E7%AE%A1%E4%BA%BA%E9%83%BD%E7%9C%8B%E5%BE%97%E6%87%82-%E9%99%84python%E7%A8%8B%E5%BC%8F%E7%A2%BC-1ec81a91ce48  

Python 3 與數據分析概要 蔡炎龍  
https://github.com/yenlung/Python-3-Data-Analysis-Basics  
http://moocs.nccu.edu.tw/media/17830  
成為 python 數據分析達人的第一堂課  
https://www.youtube.com/watch?time_continue=4&v=QvX7RqmypBk&feature=emb_title  

Colab中使用筆記本 不用安裝、免費 GPU!  
https://colab.research.google.com/notebooks/intro.ipynb#recent=true  



### requests
模擬 產生 HTTP 請求，下載網頁資料  
```
# 引入 requests 模組
import requests

# 使用 GET 方式下載普通網頁
r = requests.get('https://www.google.com.tw/')

# 伺服器回應的狀態碼
print(r.status_code)

# 檢查狀態碼是否 OK
if r.status_code == requests.codes.ok:
  print("OK")
  
# 輸出網頁 HTML 原始碼
print(r.text)  
  
# 查詢參數
my_params = {'key1': 'value1', 'key2': 'value2'}

# 將查詢參數加入 GET 請求中
r = requests.get('http://httpbin.org/get', params = my_params)

# 觀察 URL
print(r.url)

# 自訂表頭
my_headers = {'user-agent': 'my-app/0.0.1'}

# 將自訂表頭加入 GET 請求中
r = requests.get('http://httpbin.org/get', headers = my_headers)

# 需要帳號登入的網頁
r = requests.get('https://api.github.com/user', auth=('user', 'pass'))

# 資料
my_data = {'key1': 'value1', 'key2': 'value2'}

# 將資料加入 POST 請求中
r = requests.post('http://httpbin.org/post', data = my_data)

# 具有重複鍵值的資料
my_data = (('key1', 'value1'), ('key1', 'value2'))

# 將資料加入 POST 請求中
r = requests.post('http://httpbin.org/post', data = my_data)

# 要上傳的檔案
my_files = {'my_filename': open('my_file.docx', 'rb')}

# 將檔案加入 POST 請求中
r = requests.post('http://httpbin.org/post', files = my_files)

# 含有 cookie 的內容
r = requests.get("http://my.server.com/has/cookies")

# 取出 cookie
print(r.cookies['my_cookie_name'])

# 設定 cookie
my_cookies = dict(my_cookie_name='G. T. Wang')

# 將 cookie 加入 GET 請求
r = requests.get("http://httpbin.org/cookies", cookies = my_cookies)

# 等待 3 秒無回應則放棄
requests.get('http://github.com/', timeout = 3)

# 關閉憑證檢查
r = requests.get('https://my.server.com/', verify = False)

```
Python 使用 requests 模組產生 HTTP 請求，下載網頁資料  
https://blog.gtwang.org/programming/python-requests-module-tutorial/  


