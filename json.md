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



-----------------------------------------
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

