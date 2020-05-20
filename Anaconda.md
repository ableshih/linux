[1. 安裝](#安裝)  
[2. Numpy](#Numpy)  
[3. Pandas](#Pandas)  
[4. Matplotlib](#Matplotlib)  
[5. Anaconda](#Anaconda)  
[6. Spyder](#Spyder)  
[7. webdriver](#webdriver)  


## 安裝
```

開啟
Anaconda Prompt (anaconda3)
輸入
jupyter notebook

安裝套件 要用 以系統管理員身份執行

pip install selenium
pip install beautifulsoup4
pip install chromedriver
pip install requests

pip install pysqlite3
pip install matplotlib
pip install twstock

pip install requests-html

pip install Scrapy

conda install matplotlib


pip install Scipy

python -m pip install -U pip setuptools
python -m pip install matplotlib

conda install -c conda-forge tqdm

swifter：加速你的數據處理
conda install -c conda-forge swifter


Anaconda3-2020.02-Windows-x86_64

下載 Anaconda 裝 x64 開不起來 裝 x86 OK
```
https://repo.anaconda.com/archive/Anaconda3-2020.02-Windows-x86_64.exe  
https://www.anaconda.com/products/individual  
https://repo.anaconda.com/archive/  





## Numpy

https://numpy.org/  

https://cs231n.github.io/python-numpy-tutorial/  
超讚無敵  

https://ithelp.ithome.com.tw/articles/10222455  
也不錯  

https://blog.gtwang.org/programming/opencv-basic-image-read-and-write-tutorial/  
Python 與 OpenCV 基本讀取、顯示與儲存圖片教學  
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
https://blog.techbridge.cc/2017/07/28/data-science-101-numpy-tutorial/  
什麼是 Numpy 能快速操作多重維度的陣列  
Numpy 基礎操作  


http://yltang.net/tutorial/dsml/7/  
數值運算套件，主要功能為陣列與向量運算  




## Matplotlib

https://matplotlib.org/  
```
Matplotlib(之後簡稱Matplot)
畫圖功能最齊全，基本上沒什麼圖表畫不出來的
圖表不好看(舊版的matplot很醜，但新版的matplot其實也算好看，尤其在style功能出來之後可以自行切換圖表的風格)
畫圖指令複雜
```
https://gist.github.com/yehjames  
```
python -m pip install -U pip setuptools
python -m pip install matplotlib
```
https://www.runoob.com/numpy/numpy-matplotlib.html  
https://blog.techbridge.cc/2018/05/11/python-data-science-and-machine-learning-matplotlib-tutorial/  
https://morvanzhou.github.io/tutorials/data-manipulation/plt/  




## Pandas

https://leemeng.tw/practical-pandas-tutorial-for-aspiring-data-scientists.html  
```
conda install -c conda-forge tqdm

swifter：加速你的數據處理
conda install -c conda-forge swifter


Pandas 介紹
Pandas 是 python 的一個數據分析 lib，2009 年底開源出來，提供高效能、簡易使用的資料格式(Data Frame)讓使用者可以快速操作及分析資料，主要特色描述如下：

1. 在異質數據的讀取、轉換和處理上，都讓分析人員更容易處理，例如：從列欄試算表中找到想要的值。
2. Pandas 提供兩種主要的資料結構，Series 與 DataFrame。Series 顧名思義就是用來處理時間序列相關的資料(如感測器資料等)，主要為建立索引的一維陣列。DataFrame 則是用來處理結構化(Table like)的資料，有列索引與欄標籤的二維資料集，例如關聯式資料庫、CSV 等等。
3. 透過載入至 Pandas 的資料結構物件後，可以透過結構化物件所提供的方法，來快速地進行資料的前處理，如資料補值，空值去除或取代等。
4. 更多的輸入來源及輸出整合性，例如：可以從資料庫讀取資料進入 Dataframe，也可將處理完的資料存回資料庫。
```

https://oranwind.org/python-pandas-ji-chu-jiao-xue/  
https://medium.com/datainpoint/%E5%BE%9E-pandas-%E9%96%8B%E5%A7%8B-python-%E8%88%87%E8%B3%87%E6%96%99%E7%A7%91%E5%AD%B8%E4%B9%8B%E6%97%85-8dee36796d4a  
https://medium.com/@weilihmen/python-pandas-%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C%E6%95%99%E5%AD%B8-%E6%88%90%E7%B8%BE%E8%A1%A8-f6d0ec4f89  
https://medium.com/@weilihmen/python-pandas-%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C%E6%95%99%E5%AD%B8-%E6%88%90%E7%B8%BE%E8%A1%A8-f6d0ec4f89  




## Anaconda
```
jupyter notebook

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

conda install matplotlib
```

## webdriver
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
參考  
https://freelancerlife.info/zh/blog/python%E7%B6%B2%E8%B7%AF%E7%88%AC%E8%9F%B2%E6%95%99%E5%AD%B8-selenium%E5%9F%BA%E6%9C%AC%E6%93%8D%E4%BD%9C/  



## Spyder
```

Spyder
網頁爬蟲：你也可以輕鬆爬取台灣第一位武漢肺炎確診資訊
網路爬蟲只是用Python去模擬使用者操作瀏覽器的行為。其中抓資料的關鍵就是 “Get 請求”。 而我們這次就要帶大家實作一個廣義的網路爬蟲了！
```
https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json  
https://medium.com/%E8%AA%A4%E9%97%96%E6%95%B8%E6%93%9A%E5%8F%A2%E6%9E%97%E7%9A%84%E5%95%86%E7%AE%A1%E4%BA%BAzino/%E7%AC%AC%E4%B8%80%E6%94%AF%E7%B6%B2%E9%A0%81%E7%88%AC%E8%9F%B2-%E4%BD%A0%E4%B9%9F%E5%8F%AF%E4%BB%A5%E8%BC%95%E9%AC%86%E7%88%AC%E5%8F%96%E5%8F%B0%E7%81%A3%E7%AC%AC%E4%B8%80%E4%BD%8D%E6%AD%A6%E6%BC%A2%E8%82%BA%E7%82%8E%E7%A2%BA%E8%A8%BA%E8%B3%87%E8%A8%8A-%E5%90%AB%E5%BD%B1%E7%89%87%E8%88%87%E7%A8%8B%E5%BC%8F%E7%A2%BC-b24ccf308025  
https://www.youtube.com/watch?v=7tZ_B3e6KkU&feature=emb_title  
https://medium.com/%E8%AA%A4%E9%97%96%E6%95%B8%E6%93%9A%E5%8F%A2%E6%9E%97%E7%9A%84%E5%95%86%E7%AE%A1%E4%BA%BAzino/telegram%E8%81%8A%E5%A4%A9%E6%A9%9F%E5%99%A8%E4%BA%BA%E8%B6%85%E8%A9%B3%E7%B4%B0%E6%87%B6%E4%BA%BA%E5%8C%85-%E5%95%86%E7%AE%A1%E4%BA%BA%E9%83%BD%E7%9C%8B%E5%BE%97%E6%87%82-%E9%99%84python%E7%A8%8B%E5%BC%8F%E7%A2%BC-1ec81a91ce48  


Anaconda3-2020.02-Windows-x86_64  

下載 Anaconda  
https://repo.anaconda.com/archive/Anaconda3-2020.02-Windows-x86_64.exe  
https://www.anaconda.com/products/individual  
https://repo.anaconda.com/archive/  
```
裝 x64 開不起來
裝 x86 OK

開啟
Anaconda Prompt (anaconda3)
輸入
jupyter notebook


%matplotlib inline
圖都直接顯示在網頁的頁面
```
蔡炎龍  
https://github.com/yenlung/Python-3-Data-Analysis-Basics  

http://moocs.nccu.edu.tw/media/17830  
https://www.youtube.com/watch?time_continue=4&v=QvX7RqmypBk&feature=emb_title  

不用安裝、免費 GPU!  
https://colab.research.google.com/notebooks/intro.ipynb#recent=true  

```
