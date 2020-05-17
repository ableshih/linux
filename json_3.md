```

Jupyter Notebook
google.com
# ch3_1.py
import webbrowser
webbrowser.open('http://www.google.com')
True
# ch3_2.py
import webbrowser
​
address = input("請輸入地址 : ")
webbrowser.open('http://www.google.com.tw/maps/place/' + address)
請輸入地址 : 基隆市仁愛區港西街5號
True
台北車站
# ch3_3.py
import math
​
r = 6371                        # 地球半徑
x1, y1 = 22.2838, 114.1731      # 香港紅磡車站經緯度
x2, y2 = 25.0452, 121.5168      # 台北車站經緯度
​
d = 6371*math.acos(math.sin(math.radians(x1))*math.sin(math.radians(x2))+
                   math.cos(math.radians(x1))*math.cos(math.radians(x2))*
                   math.cos(math.radians(y1-y2)))
​
print("distance = ", d)
distance =  808.3115099471376
http://google.com
# ch3_4.py
import requests
​
url = 'http://google.com'
htmlfile = requests.get(url)
print(type(htmlfile))
<class 'requests.models.Response'>
# ch3_5.py
import requests
​
url = 'http://google.com'
htmlfile = requests.get(url)
if htmlfile.status_code == requests.codes.ok:
    print("取得網頁內容成功")
else:
    print("取得網頁內容失敗")
取得網頁內容成功
http://google.com
# ch3_6.py
import requests
​
url = 'http://google.com'
htmlfile = requests.get(url)
if htmlfile.status_code == requests.codes.ok:
    print("取得網頁內容成功")
    print("網頁內容大小 = ", len(htmlfile.text))
else:
    print("取得網頁內容失敗")
取得網頁內容成功
網頁內容大小 =  12449
https://www.dinbendon.net/
# ch3_7.py
import requests
​
url = 'https://www.dinbendon.net/'
htmlfile = requests.get(url)
if htmlfile.status_code == requests.codes.ok:
    print("取得網頁內容成功")
else:
    print("取得網頁內容失敗")
print(htmlfile.text)            # 列印網頁內容
取得網頁內容成功
<html><head><meta http-equiv="Refresh" content="0; url=do/"></head></html>

https://www.dinbendon.net/
# ch3_8.py
import requests
import re
​
url = 'https://www.dinbendon.net/'
htmlfile = requests.get(url)
if htmlfile.status_code == requests.codes.ok:
    pattern = input("請輸入欲搜尋的字串 : ")    # pattern存放欲搜尋的字串
# 使用方法1
    if pattern in htmlfile.text:                # 方法1
        print("搜尋 %s 成功" % pattern)
    else:
        print("搜尋 %s 失敗" % pattern)
    # 使用方法2, 如果找到放在串列name內
    name = re.findall(pattern, htmlfile.text)   # 方法2
    if name != None:
        print("%s 出現 %d 次" % (pattern, len(name)))
    else:
        print("%s 出現 0 次" % pattern)
else:
    print("網頁下載失敗")
請輸入欲搜尋的字串 : url
搜尋 url 成功
url 出現 1 次
https://www.dinbendon.net/
# ch3_9.py
import requests
​
url = 'https://www.dinbendon.net/'  # 不存在的內容
htmlfile = requests.get(url)
try:
    htmlfile.raise_for_status()                 # 異常處理
    print("下載成功")
except Exception as err:                        # err是系統自訂的錯誤訊息
    print("網頁下載失敗: %s" % err)
print("程式結束")
下載成功
程式結束
https://www.dinbendon.net/
# ch3_10.py
import requests
​
url = 'https://www.dinbendon.net/existed'  # 錯誤的網址
htmlfile = requests.get(url)
try:
    htmlfile.raise_for_status()                 # 異常處理
    print("下載成功")
except Exception as err:                        # err是系統自訂的錯誤訊息
    print("網頁下載失敗: %s" % err)
print("程式結束")
網頁下載失敗: 404 Client Error: Not Found for url: https://www.dinbendon.net/existed
程式結束
https://www.dinbendon.net/
# ch3_11.py
import requests
​
url = 'https://www.dinbendon.net/'  # 錯誤的網址
try:
    htmlfile = requests.get(url)
    print("下載成功")
except Exception as err:                        # err是系統自訂的錯誤訊息
    print("網頁下載失敗: %s" % err)
print("程式結束")
下載成功
程式結束
https://www.dinbendon.net/
# ch3_12.py
import requests
​
url = 'https://www.dinbendon.net/1'
htmlfile = requests.get(url)
htmlfile.raise_for_status()
---------------------------------------------------------------------------
HTTPError                                 Traceback (most recent call last)
<ipython-input-31-03046c59e4dc> in <module>
      4 url = 'https://www.dinbendon.net/1'
      5 htmlfile = requests.get(url)
----> 6 htmlfile.raise_for_status()

C:\ProgramData\Anaconda3\lib\site-packages\requests\models.py in raise_for_status(self)
    938 
    939         if http_error_msg:
--> 940             raise HTTPError(http_error_msg, response=self)
    941 
    942     def close(self):

HTTPError: 404 Client Error: Not Found for url: https://www.dinbendon.net/1

https://www.dinbendon.net/
# ch3_12_1.py
import requests
​
url = 'https://www.dinbendon.net/q'
htmlfile = requests.get(url)
htmlfile.raise_for_status()
---------------------------------------------------------------------------
HTTPError                                 Traceback (most recent call last)
<ipython-input-34-d5e539264d6e> in <module>
      4 url = 'https://www.dinbendon.net/q'
      5 htmlfile = requests.get(url)
----> 6 htmlfile.raise_for_status()

C:\ProgramData\Anaconda3\lib\site-packages\requests\models.py in raise_for_status(self)
    938 
    939         if http_error_msg:
--> 940             raise HTTPError(http_error_msg, response=self)
    941 
    942     def close(self):

HTTPError: 404 Client Error: Not Found for url: https://www.dinbendon.net/q

# ch3_13.py
import requests
​
headers = { 'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64)\
            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101\
            Safari/537.36', }
url = 'http://aaa.24ht.com.tw/'
htmlfile = requests.get(url, headers=headers)
htmlfile.raise_for_status()
print("偽裝瀏覽器擷取網路資料成功")
偽裝瀏覽器擷取網路資料成功
# ch3_13_1.py
import requests
​
headers = { 'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64)\
            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101\
            Safari/537.36', }
url = 'https://www.kingstone.com.tw/new/basic/2013120504769?zone=book&lid=search&actid=WISE'
htmlfile = requests.get(url, headers=headers)
htmlfile.raise_for_status()
print("偽裝瀏覽器擷取網路資料成功")
偽裝瀏覽器擷取網路資料成功
# ch3_13_2.py
import requests
​
headers = { 'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64)'
                          'AppleWebKit/537.36 (KHTML, like Gecko)'
                          'Chrome/75.0.3770.142 Safari/537.36', }
url = 'https://www.kingstone.com.tw/new/basic/2013120504769?zone=book&lid=search&actid=WISE'
htmlfile = requests.get(url, headers=headers)
htmlfile.raise_for_status()
print("偽裝瀏覽器擷取網路資料成功")
偽裝瀏覽器擷取網路資料成功
# ch3_14.py
import requests
​
url = 'http://www.deepmind.com.tw'                     # 網址
try:
    htmlfile = requests.get(url)
    print("下載成功")
except Exception as err:                                # err是系統自訂的錯誤訊息
    print("網頁下載失敗: %s" % err)
# 儲存網頁內容
fn = 'out3_14.txt'
with open(fn, 'wb') as file_Obj:                        # 以二進位儲存
    for diskStorage in htmlfile.iter_content(40960):    # Response物件處理
        size = file_Obj.write(diskStorage)              # Response物件寫入
        print(size)                                     # 列出每次寫入大小
    print("以 %s 儲存網頁HTML檔案成功" % fn)
下載成功
757
以 out3_14.txt 儲存網頁HTML檔案成功
https://www.dinbendon.net/
# ch3_15.py
import urllib.request
​
url = 'https://www.dinbendon.net/'
htmlfile = urllib.request.urlopen(url)
print(type(htmlfile))
print(htmlfile)
<class 'http.client.HTTPResponse'>
<http.client.HTTPResponse object at 0x00F8E890>
https://www.dinbendon.net/
# ch3_16.py
import urllib.request
​
url = 'https://www.dinbendon.net/'
htmlfile = urllib.request.urlopen(url)
print(htmlfile.read())
b'<html><head><meta http-equiv="Refresh" content="0; url=do/"></head></html>\n'
https://techbank.wdasec.gov.tw/owInform/TestReferData.aspx
# ch3_17.py
import urllib.request
​
url = 'https://share.qclt.com/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/Savrin/'
htmlfile = urllib.request.urlopen(url)
print(htmlfile.read().decode('utf-8'))
<html><head><title>share.qclt.com - /东南凌绅维修手册/Savrin/</title></head><body><H1>share.qclt.com - /东南凌绅维修手册/Savrin/</H1><hr>

<pre><A HREF="/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/">[To Parent Directory]</A><br><br>2010/12/21    15:56        &lt;dir&gt; <A HREF="/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/Savrin/%E5%B7%A5%E4%BD%9C%E6%89%8B%E5%86%8A/">工作手冊</A><br>2010/12/21    15:56        &lt;dir&gt; <A HREF="/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/Savrin/%E9%9B%B6%E4%BB%B6%E5%86%8A/">零件冊</A><br></pre><hr></body></html>
https://www.dinbendon.net/
# ch3_18.py
import urllib.request
​
url = 'https://www.dinbendon.net/'
htmlfile = urllib.request.urlopen(url)
print('版本 : ', htmlfile.version)
print('網址 : ', htmlfile.geturl())
print('下載 : ', htmlfile.status)
print('表頭 : ')
for header in htmlfile.getheaders():
    print(header)
版本 :  11
網址 :  https://www.dinbendon.net/
下載 :  200
表頭 : 
('Server', 'nginx/1.16.1')
('Date', 'Sun, 17 May 2020 13:00:54 GMT')
('Content-Type', 'text/html')
('Content-Length', '75')
('Connection', 'close')
('ETag', 'W/"75-1412665918000"')
('Last-Modified', 'Tue, 07 Oct 2014 07:11:58 GMT')
('Strict-Transport-Security', 'max-age=31536000')
('P3P', 'CP="ALL ADM DEV PSAi COM OUR OTRo STP IND ONL"')
('X-Cache-Status', 'MISS')
('Accept-Ranges', 'bytes')
https://www.dinbendon.net/
# ch3_19.py
import urllib.request
​
headers = { 'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64)\
            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101\
            Safari/537.36', }
url = 'https://share.qclt.com/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/Savrin/'
req = urllib.request.Request(url, headers=headers)
htmlfile = urllib.request.urlopen(req)
print(htmlfile.read().decode('utf-8'))
<html><head><title>share.qclt.com - /东南凌绅维修手册/Savrin/</title></head><body><H1>share.qclt.com - /东南凌绅维修手册/Savrin/</H1><hr>

<pre><A HREF="/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/">[To Parent Directory]</A><br><br>2010/12/21    15:56        &lt;dir&gt; <A HREF="/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/Savrin/%E5%B7%A5%E4%BD%9C%E6%89%8B%E5%86%8A/">工作手冊</A><br>2010/12/21    15:56        &lt;dir&gt; <A HREF="/%E4%B8%9C%E5%8D%97%E5%87%8C%E7%BB%85%E7%BB%B4%E4%BF%AE%E6%89%8B%E5%86%8C/Savrin/%E9%9B%B6%E4%BB%B6%E5%86%8A/">零件冊</A><br></pre><hr></body></html>
saved
# ch3_20.py
import urllib.request
​
url_pict = 'https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png'
fn = 'saved.png'
pict = urllib.request.urlretrieve(url_pict,fn)
# ch3_21.py
from urllib import parse
​
s = '台灣積體電路製造'
url_code = parse.quote(s)
print('URL編碼  : ', url_code)
code = parse.unquote(url_code)
print('中文編碼 : ', code)
URL編碼  :  %E5%8F%B0%E7%81%A3%E7%A9%8D%E9%AB%94%E9%9B%BB%E8%B7%AF%E8%A3%BD%E9%80%A0
中文編碼 :  台灣積體電路製造
# ch3_22.py
from urllib import parse
​
url = 'https://docs.python.org/3/search.html?q=parse&check_keywords=yes&area=default'
urp = parse.urlparse(url)
print(type(urp))
print(urp)
print('scheme   = ', urp.scheme)
print('netloc   = ', urp.netloc)
print('path     = ', urp.path)
print('params   = ', urp.params)
print('query    = ', urp.query)
print('fragment = ', urp.fragment)
<class 'urllib.parse.ParseResult'>
ParseResult(scheme='https', netloc='docs.python.org', path='/3/search.html', params='', query='q=parse&check_keywords=yes&area=default', fragment='')
scheme   =  https
netloc   =  docs.python.org
path     =  /3/search.html
params   =  
query    =  q=parse&check_keywords=yes&area=default
fragment =  
# ch3_23.py
from urllib import parse
​
url = 'https://docs.python.org/3/search.html?q=parse&check_keywords=yes&area=default'
urp = parse.urlsplit(url)
print(type(urp))
print(urp)
print('scheme   = ', urp.scheme)
print('netloc   = ', urp.netloc)
print('path     = ', urp.path)
print('query    = ', urp.query)
print('fragment = ', urp.fragment)
<class 'urllib.parse.SplitResult'>
SplitResult(scheme='https', netloc='docs.python.org', path='/3/search.html', query='q=parse&check_keywords=yes&area=default', fragment='')
scheme   =  https
netloc   =  docs.python.org
path     =  /3/search.html
query    =  q=parse&check_keywords=yes&area=default
fragment =  
# ch3_24.py
from urllib import parse
​
scheme = 'https'
netloc  = 'docs.python.org'
path = '/3/search.html'
params = ''
query = 'q=parse&check_keywords=yes&area=default'
frament = ''
url_unparse = parse.urlunparse((scheme,netloc,path,params,query,frament))
print(url_unparse)
url_unsplit = parse.urlunsplit([scheme,netloc,path,query,frament])
print(url_unsplit)
https://docs.python.org/3/search.html?q=parse&check_keywords=yes&area=default
https://docs.python.org/3/search.html?q=parse&check_keywords=yes&area=default
# ch3_25.py
from urllib import parse
​
url_python = 'https://docs.python.org/3/search.html?'
query = {
         'q':'parse',
         'check_keywords':'yes',
         'area':'default'}
url = url_python + parse.urlencode(query)
print(url)
https://docs.python.org/3/search.html?q=parse&check_keywords=yes&area=default
# ch3_26.py
from urllib import parse
​
query_str = 'q=parse&check_keywords=yes&area=default'
print('parse.parse_qs  = ', parse.parse_qs(query_str))
print('parse.parse_qsl = ', parse.parse_qsl(query_str))
parse.parse_qs  =  {'q': ['parse'], 'check_keywords': ['yes'], 'area': ['default']}
parse.parse_qsl =  [('q', 'parse'), ('check_keywords', 'yes'), ('area', 'default')]
# ch3_27.py
from urllib import request, error
​
headers = { 'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64)\
            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101\
            Safari/537.36', }
# 錯誤網址
url_error = 'http://aaa.24t.com.tw/'            # 錯誤網址
try:
    htmlfile = request.urlopen(url_error)
except error.URLError as e:
    print('錯誤原因 : ', e.reason)
else:
    print("擷取網路資料成功")
# 正確網址
url = 'http://aaa.24ht.com.tw/'                 # 網址正確
try:
    req = request.Request(url, headers=headers)
    htmlfile = request.urlopen(req)
except error.URLError as e:
    print('錯誤原因 : ', e.reason)
else:
    print("擷取網路資料成功")
錯誤原因 :  [Errno 11001] getaddrinfo failed
擷取網路資料成功
# ch3_28.py
from urllib import request, error
​
headers = { 'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64)\
            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101\
            Safari/537.36', }
# 錯誤1
url_error = 'http://aaa.24t.com.tw/'            # 錯誤網址
try:
    htmlfile = request.urlopen(url_error)
except error.HTTPError as e:
    print('錯誤代碼 : ', e.code)
    print('錯誤原因 : ', e.reason)
    print('回應表頭 : ', e.headers)
except error.URLError as e:
    print('錯誤原因 : ', e.reason)
else:
    print("擷取網路資料成功")
print('-'*70)
# 錯誤2
url = 'http://aaa.24ht.com.tw/'                 # 網址正確
try:
    htmlfile = request.urlopen(url)
except error.HTTPError as e:
    print('錯誤代碼 : ', e.code)
    print('錯誤原因 : ', e.reason)
    print('回應表頭 : ', e.headers)    
except error.URLError as e:
    print('錯誤原因 : ', e.reason)    
else:
    print("擷取網路資料成功")
print('-'*70)
# 正確
url = 'http://aaa.24ht.com.tw/'                 # 網址正確
try:
    req = request.Request(url, headers=headers)
    htmlfile = request.urlopen(req)
except error.HTTPError as e:
    print('錯誤代碼 : ', e.code)
    print('錯誤原因 : ', e.reason)
    print('回應表頭 : ', e.headers)    
except error.URLError as e:
    print('錯誤原因 : ', e.reason)
else:
    print("擷取網路資料成功")
錯誤原因 :  [Errno 11001] getaddrinfo failed
----------------------------------------------------------------------
錯誤代碼 :  406
錯誤原因 :  Not Acceptable
回應表頭 :  Date: Sun, 17 May 2020 13:09:01 GMT
Server: Apache
Accept-Ranges: bytes
Connection: close
Transfer-Encoding: chunked
Content-Type: text/html


----------------------------------------------------------------------
擷取網路資料成功
https://www.dinbendon.net/
# ch3_29.py
import requests
​
url = 'https://www.dinbendon.net/'
r = requests.get(url)
print(r.url)
https://www.dinbendon.net/
https://www.dinbendon.net/
# ch3_30.py
import requests
​
url = 'https://www.dinbendon.net/'
form_data = {'gender':'M','page':'1'}
r = requests.get(url, params=form_data)
print(r.url)
https://www.dinbendon.net/?gender=M&page=1
# ch3_31.py
import requests
​
url = 'https://www.httpbin.org/post'
form_data = {'gender':'M','page':'1'}
r = requests.post(url, data=form_data)
print(r.url)
print('-'*70)
print(r.text)
https://www.httpbin.org/post
----------------------------------------------------------------------
{
  "args": {}, 
  "data": "", 
  "files": {}, 
  "form": {
    "gender": "M", 
    "page": "1"
  }, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Content-Length": "15", 
    "Content-Type": "application/x-www-form-urlencoded", 
    "Host": "www.httpbin.org", 
    "User-Agent": "python-requests/2.22.0", 
    "X-Amzn-Trace-Id": "Root=1-5ec13813-6b1d547315da438c6409cce1"
  }, 
  "json": null, 
  "origin": "182.233.165.144", 
  "url": "https://www.httpbin.org/post"
}

# ch3_32.py
import requests, json
​
url = 'https://www.httpbin.org/post'
form_data = {'gender':'M','page':'1'}
r = requests.post(url, data=json.dumps(form_data))
print(r.url)
print('-'*70)
print(r.text)
https://www.httpbin.org/post
----------------------------------------------------------------------
{
  "args": {}, 
  "data": "{\"gender\": \"M\", \"page\": \"1\"}", 
  "files": {}, 
  "form": {}, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Content-Length": "28", 
    "Host": "www.httpbin.org", 
    "User-Agent": "python-requests/2.22.0", 
    "X-Amzn-Trace-Id": "Root=1-5ec13835-4bbd1028e8afe49097e10d98"
  }, 
  "json": {
    "gender": "M", 
    "page": "1"
  }, 
  "origin": "182.233.165.144", 
  "url": "https://www.httpbin.org/post"
}

# ch3_33.py
import requests, json
​
url = 'https://www.httpbin.org/post'
form_data = {'gender':'M','page':'1'}
r = requests.post(url, json=form_data)
print(r.url)
print('-'*70)
print(r.text)
https://www.httpbin.org/post
----------------------------------------------------------------------
{
  "args": {}, 
  "data": "{\"gender\": \"M\", \"page\": \"1\"}", 
  "files": {}, 
  "form": {}, 
  "headers": {
    "Accept": "*/*", 
    "Accept-Encoding": "gzip, deflate", 
    "Content-Length": "28", 
    "Content-Type": "application/json", 
    "Host": "www.httpbin.org", 
    "User-Agent": "python-requests/2.22.0", 
    "X-Amzn-Trace-Id": "Root=1-5ec13852-0e7c96bca3e5e3fc78e7d4a3"
  }, 
  "json": {
    "gender": "M", 
    "page": "1"
  }, 
  "origin": "182.233.165.144", 
  "url": "https://www.httpbin.org/post"
}

# ch3_34.py
import requests, json
​
headers = { 'User-Agent':'Mozilla/5.0 (Windows NT 6.1; WOW64)\
            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101\
            Safari/537.36', }
url = 'https://www.httpbin.org/post'
form_data = {'gender':'M','page':'1'}
r = requests.post(url, json=form_data, headers=headers)
print(r.url)
print('-'*70)
print('r.request.headers :\n', r.request.headers)
print('-'*70)
print('r.headers :\n', r.headers)
https://www.httpbin.org/post
----------------------------------------------------------------------
r.request.headers :
 {'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64)            AppleWebKit/537.36 (KHTML, like Gecko) Chrome/45.0.2454.101            Safari/537.36', 'Accept-Encoding': 'gzip, deflate', 'Accept': '*/*', 'Connection': 'keep-alive', 'Content-Length': '28', 'Content-Type': 'application/json'}
----------------------------------------------------------------------
r.headers :
 {'Date': 'Sun, 17 May 2020 13:13:10 GMT', 'Content-Type': 'application/json', 'Content-Length': '633', 'Connection': 'keep-alive', 'Server': 'gunicorn/19.9.0', 'Access-Control-Allow-Origin': '*', 'Access-Control-Allow-Credentials': 'true'}
# ch3_35.py
import requests
​
url = 'https://www.httpbin.org/get'
r = requests.get(url)
print(r.status_code)
print(r.reason)
200
OK
https://www.dinbendon.net/
# ch3_36.py
import requests
​
url = 'https://www.dinbendon.net/'
r = requests.get(url)
print(r.encoding)
print('-'*70)
print(r.text)
ISO-8859-1
----------------------------------------------------------------------
<html><head><meta http-equiv="Refresh" content="0; url=do/"></head></html>

# ch3_37.py
import requests
​
url = 'https://www.httpbin.org/response-headers?freeform='
r = requests.get(url)
if r.status_code == 200:
    print(r.headers.get('content-type'))
    print('-'*70)
    print(r.json())
application/json
----------------------------------------------------------------------
{'Content-Length': '87', 'Content-Type': 'application/json', 'freeform': ''}
# ch3_38.py
import requests
​
url = 'https://www.httpbin.org/image/jpeg'
r = requests.get(url)
img = r.content
​
fn = 'out3_38.jpg'
with open(fn, 'wb') as fout:
    fout.write(img)
# ch3_39.py
import requests
​
url = 'http://httpbin.org/cookies'
cookies = dict(key1='value1')
r = requests.get(url, cookies=cookies)
print(r.text)
{
  "cookies": {
    "key1": "value1"
  }
}

# ch3_40.py
import requests
​
proxies = {
  "http": "http://111.231.81.109:3128",         # ip:port
  "https": "https://111.231.81.109:1080",       # ip:port
}
​
r = requests.get("https://docs.python.org", proxies=proxies)
---------------------------------------------------------------------------
TimeoutError                              Traceback (most recent call last)
C:\ProgramData\Anaconda3\lib\site-packages\urllib3\connection.py in _new_conn(self)
    158             conn = connection.create_connection(
--> 159                 (self._dns_host, self.port), self.timeout, **extra_kw)
    160 

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\util\connection.py in create_connection(address, timeout, source_address, socket_options)
     79     if err is not None:
---> 80         raise err
     81 

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\util\connection.py in create_connection(address, timeout, source_address, socket_options)
     69                 sock.bind(source_address)
---> 70             sock.connect(sa)
     71             return sock

TimeoutError: [WinError 10060] 連線嘗試失敗，因為連線對象有一段時間並未正確回應，或是連線建立失敗，因為連線的主機無法回應。

During handling of the above exception, another exception occurred:

NewConnectionError                        Traceback (most recent call last)
C:\ProgramData\Anaconda3\lib\site-packages\urllib3\connectionpool.py in urlopen(self, method, url, body, headers, retries, redirect, assert_same_host, timeout, pool_timeout, release_conn, chunked, body_pos, **response_kw)
    593             if is_new_proxy_conn:
--> 594                 self._prepare_proxy(conn)
    595 

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\connectionpool.py in _prepare_proxy(self, conn)
    804         conn.set_tunnel(self._proxy_host, self.port, self.proxy_headers)
--> 805         conn.connect()
    806 

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\connection.py in connect(self)
    300         # Add certificate verification
--> 301         conn = self._new_conn()
    302         hostname = self.host

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\connection.py in _new_conn(self)
    167             raise NewConnectionError(
--> 168                 self, "Failed to establish a new connection: %s" % e)
    169 

NewConnectionError: <urllib3.connection.VerifiedHTTPSConnection object at 0x016F8330>: Failed to establish a new connection: [WinError 10060] 連線嘗試失敗，因為連線對象有一段時間並未正確回應，或是連線建立失敗，因為連線的主機無法回應。

During handling of the above exception, another exception occurred:

MaxRetryError                             Traceback (most recent call last)
C:\ProgramData\Anaconda3\lib\site-packages\requests\adapters.py in send(self, request, stream, timeout, verify, cert, proxies)
    448                     retries=self.max_retries,
--> 449                     timeout=timeout
    450                 )

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\connectionpool.py in urlopen(self, method, url, body, headers, retries, redirect, assert_same_host, timeout, pool_timeout, release_conn, chunked, body_pos, **response_kw)
    637             retries = retries.increment(method, url, error=e, _pool=self,
--> 638                                         _stacktrace=sys.exc_info()[2])
    639             retries.sleep()

C:\ProgramData\Anaconda3\lib\site-packages\urllib3\util\retry.py in increment(self, method, url, response, error, _pool, _stacktrace)
    398         if new_retry.is_exhausted():
--> 399             raise MaxRetryError(_pool, url, error or ResponseError(cause))
    400 

MaxRetryError: HTTPSConnectionPool(host='docs.python.org', port=443): Max retries exceeded with url: / (Caused by ProxyError('Cannot connect to proxy.', NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x016F8330>: Failed to establish a new connection: [WinError 10060] 連線嘗試失敗，因為連線對象有一段時間並未正確回應，或是連線建立失敗，因為連線的主機無法回應。')))

During handling of the above exception, another exception occurred:

ProxyError                                Traceback (most recent call last)
<ipython-input-93-e74fb2539767> in <module>
      7 }
      8 
----> 9 r = requests.get("https://docs.python.org", proxies=proxies)

C:\ProgramData\Anaconda3\lib\site-packages\requests\api.py in get(url, params, **kwargs)
     73 
     74     kwargs.setdefault('allow_redirects', True)
---> 75     return request('get', url, params=params, **kwargs)
     76 
     77 

C:\ProgramData\Anaconda3\lib\site-packages\requests\api.py in request(method, url, **kwargs)
     58     # cases, and look like a memory leak in others.
     59     with sessions.Session() as session:
---> 60         return session.request(method=method, url=url, **kwargs)
     61 
     62 

C:\ProgramData\Anaconda3\lib\site-packages\requests\sessions.py in request(self, method, url, params, data, headers, cookies, files, auth, timeout, allow_redirects, proxies, hooks, stream, verify, cert, json)
    531         }
    532         send_kwargs.update(settings)
--> 533         resp = self.send(prep, **send_kwargs)
    534 
    535         return resp

C:\ProgramData\Anaconda3\lib\site-packages\requests\sessions.py in send(self, request, **kwargs)
    644 
    645         # Send the request
--> 646         r = adapter.send(request, **kwargs)
    647 
    648         # Total elapsed time of the request (approximately)

C:\ProgramData\Anaconda3\lib\site-packages\requests\adapters.py in send(self, request, stream, timeout, verify, cert, proxies)
    508 
    509             if isinstance(e.reason, _ProxyError):
--> 510                 raise ProxyError(e, request=request)
    511 
    512             if isinstance(e.reason, _SSLError):

ProxyError: HTTPSConnectionPool(host='docs.python.org', port=443): Max retries exceeded with url: / (Caused by ProxyError('Cannot connect to proxy.', NewConnectionError('<urllib3.connection.VerifiedHTTPSConnection object at 0x016F8330>: Failed to establish a new connection: [WinError 10060] 連線嘗試失敗，因為連線對象有一段時間並未正確回應，或是連線建立失敗，因為連線的主機無法回應。')))

# ch3_41.py
import requests
​
proxies = {
  "http": "http://203.83.182.86:8080",         # ip:port
}
​
r = requests.get("https://docs.python.org", proxies=proxies)
if r.status_code == 200:
    print('代理IP使用成功')
代理IP使用成功
​

```
