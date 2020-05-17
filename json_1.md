


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


