
[1. 安裝](#安裝)  
[2. 型別](#型別)  
[3. 檔案](#來源)   
[4. 範例](#範例)   


Anaconda json

-----------------------------------------
# 安裝
```
裝 x86 OK (裝 x64 開不起來)
-----------------------------------------
```
# 使用
```
開啟
Anaconda Prompt (anaconda3)
輸入
jupyter notebook

右邊 New -> python3

或 往下找 *.ipynb
-----------------------------------------
```
# 密技
```
可以下 pwd 查看目前所在目錄
指定路徑 fn = 'C:\\Users\\C940\\Day_Confirmation_Age_County_Gender_19CoV.json'

本地路徑 fn = './Day_Confirmation_Age_County_Gender_19CoV.json'

-----------------------------------------

```



# 來源

1. 本地 陣列  
2. 本地 json file  
3. 網路 json file 要透過 import requests  



## 本地 陣列
```
import json

load_str = '[{"Country Name": "World", "Country Code": "WLD", "Year": "2000", "Numbers": "6117806174.56156"}, {"Country Name": "World", "Country Code": "WLD", "Year": "2000", "Numbers": "6117806174.56156"}]'
p_data = json.loads(load_str)

print(p_data)
```

## 本地 json file (read)
```
import json
jn = "./aaa.json"

with open(jn,'r') as load_f:
    load_dict = json.load(load_f)
          
print(load_dict)
```


## 本地 json file (write)
```
import json

js = [{"Country Name": "World", "Country Code": "WLD", "Year": "2000", "Numbers": "6117806174.56156"}, {"Country Name": "World", "Country Code": "WLD", "Year": "2010", "Numbers": "6894595189.85751"}, {"Country Name": "Angola", "Country Code": "AGO", "Year": "2000", "Numbers": "13926705.0"}]

jk = "./aaaw.json"

with open(jk, 'w') as save_f:
    json.dump(js, save_f)
```

## 網路 json file 要透過 import requests
```
import requests
import json

url = 'https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json'

with request.urlopen(url) as response:
    data = json.load(response, encoding='utf-8')
    
print(data[:5]) # 印出前 5 筆 
print('\n') # 空一行 
print(data[5]) # 印出第 5 筆 
print('\n') # 空一行 
print(data[5]["性別"])
```










# 型別
Json 模組裡的函式介紹  
[1. dumps](#dumps)  
[2. loads](#loads)  
[3. dump](#dump)  
[4. load](#load)  




#### dumps
將 dict 型別的資料轉成 str，直接把 dict 型 寫入 json檔案 會發生報錯
```
import json

nb = {'a':'100','b':'200','c':'300','d':'400'}  # 原始 dict

jDumps = json.dumps(nb)   # 用 dumps 轉成 str

print(nb, type(nb)) 

print(jDumps, type(jDumps)) 

```





#### loads
用於將str型別的資料轉成dict  
```
import json

nb = {'a':'100','b':'200','c':'300','d':'400'}  # 原始 dict

jDumps = json.dumps(nb)   # 用 dumps 轉成 str
jLoads = json.loads(jDumps) # 用 loads 轉成 dict

print(nb, type(nb)) 

print(jDumps, type(jDumps)) 

print(jLoads, type(jLoads)) 
```






#### dump
用於將dict型別的資料轉成str，並寫入成 json檔案  
```
import json  
nb = {'a':'100','b':'200','c':'300','d':'400'}  
ef = ('./aaaaw.json')  
# solution 1 
jObj = json.dumps(nb)   
with open(ef, "w") as f:  
    f.write(jObj)  
f.close()  
# solution 2   
json.dump(nb, open(ef, "w")) 

fs = ('./aaaaw.json')  
jObj = json.load(open(fs))   
print(jObj) 
print(type(jObj)) 

```






#### load
讀取 json 檔案  
```
import json

fs = ('./aaaw.json')  
jObj = json.load(open(fs))   
print(jObj) 
print(type(jObj)) 
```














# 載入 json 
```
例如 這一筆資料 是用 {}, 框起來，這一筆資料裡面有四組資料用 , 隔開
有幾種方式將資料帶入
1. 變數 接 code 裡的 json raw dada
2. 變數 接 載入 json 檔案
3. 變數 接 到網站抓 url  裡的 json raw dada
-----------------------------------------
```
# 解釋 一筆 json 內容
```
要資料 加一個變數 countryName = getData['Country Name'] 

"Country Name": "World", 
"Country Code": "WLD", 
"Year": "2000", 
"Numbers": "6117806174.56156"

populations.json
{
"Country Name": "World", 
"Country Code": "WLD", 
"Year": "2000", 
"Numbers": "6117806174.56156"
},


19CoV.json
{
"確定病名": "嚴重特殊傳染性肺炎", 
"個案研判日": "2020/01/22", 
"縣市": "高雄市", 
"性別": "女", 
"是否為境外移入": "是", 
"年齡層": "55-59", 
"確定病例數": "1"
}
 
-----------------------------------------
```

# 範例
## 變數 接 code 裡的 json raw dada # 本地 json 檔 # ch1_14.py
```
====================
import json

getDatas = [{"Country Name": "World", "Country Code": "WLD", "Year": "2000", "Numbers": "6117806174.56156"}, {"Country Name": "Albania", "Country Code": "ALB", "Year": "2000", "Numbers": "3072478.0"}, {"Country Name": "Albania", "Country Code": "ALB", "Year": "2010", "Numbers": "3205579.0"}, {"Country Name": "Algeria", "Country Code": "DZA", "Year": "2000", "Numbers": "30534041.0"}, {"Country Name": "Algeria", "Country Code": "DZA", "Year": "2010", "Numbers": "35468731.0"}, {"Country Name": "American Samoa", "Country Code": "ASM", "Year": "2000", "Numbers": "57995.0"}, {"Country Name": "American Samoa", "Country Code": "ASM", "Year": "2010", "Numbers": "69154.0"}, {"Country Name": "Andorra", "Country Code": "AND", "Year": "2000", "Numbers": "65258.0"}, {"Country Name": "Andorra", "Country Code": "AND", "Year": "2010", "Numbers": "85216.0"}, {"Country Name": "Angola", "Country Code": "AGO", "Year": "2000", "Numbers": "13926705.0"}, {"Country Name": "Angola", "Country Code": "AGO", "Year": "2010", "Numbers": "19082927.0"}, {"Country Name": "Antigua and Barbuda", "Country Code": "ATG", "Year": "2000", "Numbers": "78536.0"}, {"Country Name": "Zimbabwe", "Country Code": "ZWE", "Year": "2010", "Numbers": "12571128.0"}]

for getData in getDatas:
    if getData['Year'] == '2000':                   # 篩選2000年的數據
        countryName = getData['Country Name']       # 國家名稱
        countryCode = getData['Country Code']       # 國家代碼
        population = int(float(getData['Numbers'])) # 人口數據
        print('國家代碼 =', countryCode,
              '國家名稱 =', countryName,
              '人口數 =', population)
====================
```
## 變數 接 載入 json 檔案
```
====================
import json

fn = 'populations.json'
with open(fn) as fnObj:
    getDatas = json.load(fnObj)                     # 讀json檔案

for getData in getDatas:
    if getData['Year'] == '2000':                   # 篩選2000年的數據
        countryName = getData['Country Name']       # 國家名稱
        countryCode = getData['Country Code']       # 國家代碼
        population = int(float(getData['Numbers'])) # 人口數據
        print('國家代碼 =', countryCode,
              '國家名稱 =', countryName,
              '人口數 =', population)
====================
```
## 變數 接 到網站抓 url  裡的 json raw dada
```
====================
import requests

r = requests.get("https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json", verify=False)

list_of_dicts = r.json()

for i in list_of_dicts:
    print(i["縣市"], i["性別"], i["個案研判日"])
====================
```
### 找出 高雄 的確診
```
====================
import requests

r = requests.get("https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json", verify=False)

list_of_dicts = r.json()

for i in list_of_dicts:    
	if i["縣市"] == "高雄市": 
		print(i["縣市"], i["性別"], i["個案研判日"])
====================
```
### 找出 高雄 女 的確診
```
====================
import requests

r = requests.get("https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json", verify=False)

list_of_dicts = r.json()

for i in list_of_dicts:    
	if i["縣市"] == "高雄市": 
		if i["性別"] == "女": 
			print(i["縣市"], i["性別"], i["個案研判日"])
====================
```
### 找出 高雄 女 的確診
```
====================
import requests

r = requests.get("https://od.cdc.gov.tw/eic/Day_Confirmation_Age_County_Gender_19CoV.json", verify=False)

list_of_dicts = r.json()

for i in list_of_dicts:    
	if i["縣市"] == "高雄市" and i["性別"] == "女": 
			print(i["縣市"], i["性別"], i["個案研判日"])
====================
```

http://tw.gitbook.net/t/python3/article-68.html  
https://medium.com/ccclub/ccclub-python-for-beginners-tutorial-ae8becaf165e





















pip install selenium  
pip install beautifulsoup4  


# 看 資料類型
```
print("json陣列在Python的資料類型 ", type(jsonData1))
```
# 資料轉成 將串列資料轉成json資料
```
jsonData = json.dumps(listObj) 
```
# 資料排序
```
jsonObj2 = json.dumps(players, sort_keys=True)      # 有用排序將字典轉成json物件
```
# 加空白 0 無 4 四個空白
```
jsonObj = json.dumps(players, sort_keys=True, indent=4)
```
# json 轉 物件<class 'dict'>
```
jsonObj = '{"b":80, "a":25, "c":60}'    # json物件
dictObj = json.loads(jsonObj)           # 轉成Python物件

<class 'str'>
<class 'list'>
<class 'dict'>
```
# json 資料 提取法
```
obj = '{"Asia":[{"Japan":"Tokyo"},{"Taiwan":"Taipei"}]}'
json_obj = json.loads(obj)
print(json_obj)
print(json_obj["Asia"])
print(json_obj["Asia"][0])
print(json_obj["Asia"][1])
print(json_obj["Asia"][0]["Japan"])
print(json_obj["Asia"][1]["Taiwan"])
---
{'Asia': [{'Japan': 'Tokyo'}, {'Taiwan': 'Taipei'}]}
[{'Japan': 'Tokyo'}, {'Taiwan': 'Taipei'}]
{'Japan': 'Tokyo'}
{'Taiwan': 'Taipei'}
Tokyo
Taipei
```
# 資料的兩種方式
```
obj = '{"Asia":[{"Japan":"Tokyo"},{"Taiwan":"Taipei"}]}'
obj = '{"Asia":\
        [{"Japan":"Tokyo"},\
         {"Taiwan":"Taipei"}]\
       }'
```
# 資料 轉存成 json 檔
```
dictObj = {'b':80, 'a':25, 'c':60}      
fn = 'out1_8.json'
with open(fn, 'w') as fnObj:
    json.dump(dictObj, fnObj)
```
# 使用 with open() as 讀檔案
```
f = open('test.txt', 'r')
```
# 使用 with open() as 寫檔案
```
with open('test.txt', 'w') as f:
    f.write('Hello, python!')
```
# 中文問題 ch1_9_1.py
```
import json

objlist = [{"日本":"Japan", "首都":"Tykyo"},
           {"美州":"USA", "首都":"Washington"}]

fn = 'out1_9_2.json'
with open(fn, 'w', encoding='utf-8') as fnObj: # 中文
    json.dump(objlist, fnObj, indent=2, ensure_ascii=False) # 格式化存檔內容
```

# 讀取外部 json 檔 (不能中文)      
```
fn = 'out1_9.json'
with open(fn, 'r') as fnObj:
    data = json.load(fnObj)
```
# 讀取外部 json 檔 (能中文)
```
fn = 'out1_9_2.json'
with open(fn, 'r', encoding='utf-8') as fnObj:
    data = json.load(fnObj)
```
	
# 輸入 資料 並將其存成 json
```
fn = 'login.json'
login = input("請輸入帳號 : ")
with open(fn, 'w') as fnObj:
    json.dump(login, fnObj)
    print("%s! 歡迎使用本系統! " % login)
```
# 判斷是否有輸入過 沒有:輸入 有:讀取
```
import json

fn = 'login1_13.json'
try:
    with open(fn) as fnObj:
        login = json.load(fnObj)   
except Exception:
    login = input("請輸入帳號 : ") 
    with open(fn, 'w') as fnObj:
        json.dump(login, fnObj)
        print("系統已經記錄你的帳號 ")
else:
    print("%s 歡迎回來" % login)
```


# 將一大筆 json 檔讀取，判斷特定數值，印出
```
fn = 'populations.json'
with open(fn) as fnObj:
    getDatas = json.load(fnObj)                     # 讀json檔案

for getData in getDatas:
    if getData['Year'] == '2000':                   # 篩選2000年的數據
        countryName = getData['Country Name']       # 國家名稱
        countryCode = getData['Country Code']       # 國家代碼
        population = int(float(getData['Numbers'])) # 人口數據
        print('國家代碼 =', countryCode,
              '國家名稱 =', countryName,
              '人口數 =', population)
```

# python jupyter 模組安裝
```
再開啟一個 Anaconda Prompt (anaconda3)
(base) C:\Users\C940>pip install pygal_maps_world
裝完就可回到 jupyter 立刻就能用

from pygal.maps.world import COUNTRIES

for countryCode in sorted(COUNTRIES.keys()):
    print("國家代碼 :", countryCode, "  國家名稱 = ", COUNTRIES[countryCode])





```


# 輸出成 地圖檔案 標一個
```
import pygal.maps.world
worldMap = pygal.maps.world.World()         # 建立世界地圖物件
worldMap.title = 'Taiwan in the Map'         # 世界地圖標題
worldMap.add('Taiwan',['tw'])                # 標記中國
worldMap.render_to_file('out1_17.svg')      # 儲存地圖檔案
輸出成 地圖檔案 標多個
import pygal.maps.world
worldMap = pygal.maps.world.World()         # 建立世界地圖物件
worldMap.title = 'Taiwan/Japan/Thailand'     # 世界地圖標題
worldMap.add('Asia',['tw', 'jp', 'th'])     # 標記Asia
worldMap.render_to_file('out1_18.svg')      # 儲存地圖檔案
輸出成 地圖檔案 標多個分區
import pygal.maps.world
worldMap = pygal.maps.world.World()                         # 建立世界地圖物件
worldMap.title = ' Asia, Europe, Africa, and North America' # 世界地圖標題
worldMap.add('Asia',['cn', 'jp', 'th'])                     # 標記Asia
worldMap.add('Europe',['fr', 'de', 'it'])                   # 標記Europe
worldMap.add('Africa',['eg', 'ug', 'ng'])                   # 標記Africa
worldMap.add('North America',['ca', 'us', 'mx'])            # 標記北美洲
worldMap.render_to_file('out1_19.svg')                      # 儲存地圖檔案
```
# 讀取外部 xml
```
<深智數位>
     <總經理>John</總經理>
     <編輯部>Lai</編輯部>
     <業務部>
          <國外 主管='Linda'>
               <人數>10人</人數>
          </國外>
          <國內>Mary</國內>
     </業務部>
</深智數位>

import xmltodict
with open('myxml.xml', encoding='utf-8') as f:
    txt = xmltodict.parse(f.read())
print('總經理 : ',txt['深智數位']['總經理'])
print('總編輯 : ',txt['深智數位']['編輯部'],'\n')
print('國外業務主管 : ',txt['深智數位']['業務部']['國外']['@主管'])
print('國外業務人數 : ',txt['深智數位']['業務部']['國外']['人數'])
print('國內業務主管 : ',txt['深智數位']['業務部']['國內'])
```



