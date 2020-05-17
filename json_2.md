

讀csv檔案
```
import csv
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件
    listReport = list(csvReader)        # 將資料轉成串列    
print(listReport)                       # 列印串列方法

```

```
import csv
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件csvReader
    for row in csvReader:               # 用迴圈列出csvReader物件內容
        print("Row %s = " % csvReader.line_num, row)
```

```
import csv
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件
    listReport = list(csvReader)        # 將資料轉成串列    
for row in listReport:                  # 使用迴圈列出串列內容
    print(row)

```

```

import csv
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件
    listReport = list(csvReader)        # 將資料轉成串列    

print(listReport[2][3], listReport[2][6])
```

```

import csv
fn = 'csvPeople.csv'
with open(fn) as csvFile:                   # 開啟csv檔案
    csvDictReader = csv.DictReader(csvFile) # 讀檔案建立DictReader物件   
    for row in csvDictReader:               # 使用迴圈列出字典內容
        print(row['first_name'], row['last_name'])




```

```



import csv
fn = 'out2_7.csv'
with open(fn, 'w', newline = '') as csvFile:    # 開啟csv檔案
    csvWriter = csv.writer(csvFile)             # 建立Writer物件   
    csvWriter.writerow(['Name', 'Age', 'City'])
    csvWriter.writerow(['Hung', '35', 'Taipei'])
    csvWriter.writerow(['James', '40', 'Chicago'])

```

```
import csv

fn = 'out2_7_1.csv'
with open(fn, 'w') as csvFile:                  # 開啟csv檔案
    csvWriter = csv.writer(csvFile)             # 建立Writer物件   
    csvWriter.writerow(['Name', 'Age', 'City'])
    csvWriter.writerow(['Hung', '35', 'Taipei'])
    csvWriter.writerow(['James', '40', 'Chicago'])

```



==========================

Jupyter Notebook
No2_Untitled1

```
import csv
​
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件
    listReport = list(csvReader)        # 將資料轉成串列    
print(listReport)                       # 列印串列方法
---
[['Name', 'Year', 'Product', 'Price', 'Quantity', 'Revenue', 'Location'], ['Diana', '2015', 'Black Tea', '10', '600', '6000', 'New York'], ['Diana', '2015', 'Green Tea', '7', '660', '4620', 'New York'], ['Diana', '2016', 'Black Tea', '10', '750', '7500', 'New York'], ['Diana', '2016', 'Green Tea', '7', '900', '6300', 'New York'], ['Julia', '2015', 'Black Tea', '10', '1200', '12000', 'New York'], ['Julia', '2016', 'Black Tea', '10', '1260', '12600', 'New York'], ['Steve', '2015', 'Black Tea', '10', '1170', '11700', 'Chicago'], ['Steve', '2015', 'Green Tea', '7', '1260', '8820', 'Chicago'], ['Steve', '2016', 'Black Tea', '10', '1350', '13500', 'Chicago'], ['Steve', '2016', 'Green Tea', '7', '1440', '10080', 'Chicago']]
```

```
import csv
​
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件csvReader
    for row in csvReader:               # 用迴圈列出csvReader物件內容
        print("Row %s = " % csvReader.line_num, row)
---
Row 1 =  ['Name', 'Year', 'Product', 'Price', 'Quantity', 'Revenue', 'Location']
Row 2 =  ['Diana', '2015', 'Black Tea', '10', '600', '6000', 'New York']
Row 3 =  ['Diana', '2015', 'Green Tea', '7', '660', '4620', 'New York']
Row 4 =  ['Diana', '2016', 'Black Tea', '10', '750', '7500', 'New York']
Row 5 =  ['Diana', '2016', 'Green Tea', '7', '900', '6300', 'New York']
Row 6 =  ['Julia', '2015', 'Black Tea', '10', '1200', '12000', 'New York']
Row 7 =  ['Julia', '2016', 'Black Tea', '10', '1260', '12600', 'New York']
Row 8 =  ['Steve', '2015', 'Black Tea', '10', '1170', '11700', 'Chicago']
Row 9 =  ['Steve', '2015', 'Green Tea', '7', '1260', '8820', 'Chicago']
Row 10 =  ['Steve', '2016', 'Black Tea', '10', '1350', '13500', 'Chicago']
Row 11 =  ['Steve', '2016', 'Green Tea', '7', '1440', '10080', 'Chicago']
```

```
import csv
​
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件
    listReport = list(csvReader)        # 將資料轉成串列    
for row in listReport:                  # 使用迴圈列出串列內容
    print(row)
---
['Name', 'Year', 'Product', 'Price', 'Quantity', 'Revenue', 'Location']
['Diana', '2015', 'Black Tea', '10', '600', '6000', 'New York']
['Diana', '2015', 'Green Tea', '7', '660', '4620', 'New York']
['Diana', '2016', 'Black Tea', '10', '750', '7500', 'New York']
['Diana', '2016', 'Green Tea', '7', '900', '6300', 'New York']
['Julia', '2015', 'Black Tea', '10', '1200', '12000', 'New York']
['Julia', '2016', 'Black Tea', '10', '1260', '12600', 'New York']
['Steve', '2015', 'Black Tea', '10', '1170', '11700', 'Chicago']
['Steve', '2015', 'Green Tea', '7', '1260', '8820', 'Chicago']
['Steve', '2016', 'Black Tea', '10', '1350', '13500', 'Chicago']
['Steve', '2016', 'Green Tea', '7', '1440', '10080', 'Chicago']
ader)        # 將資料轉成串列    

print(listReport[0][1], listReport[0][2])

```

```


import csv
​
fn = 'csvReport.csv'
with open(fn) as csvFile:               # 開啟csv檔案
    csvReader = csv.reader(csvFile)     # 讀檔案建立Reader物件
    listReport = list(csvReader)        # 將資料轉成串列    
​
print(listReport[0][1], listReport[0][2])
print(listReport[1][2], listReport[1][5])
print(listReport[2][3], listReport[2][6])
---
Year Product
Black Tea 6000
7 New York

```

```


import csv
​
fn = 'csvPeople.csv'
with open(fn) as csvFile:                   # 開啟csv檔案
    csvDictReader = csv.DictReader(csvFile) # 讀檔案建立DictReader物件   
    for row in csvDictReader:               # 列出DictReader各行內容
        print(row)
---
OrderedDict([('first_name', 'Eli'), ('last_name', 'Manning'), ('city', 'New York')])
OrderedDict([('first_name', 'Kevin '), ('last_name', 'James'), ('city', 'Cleveland')])
OrderedDict([('first_name', 'Mike'), ('last_name', 'Jordon'), ('city', 'Chicago')])
```

```
import csv
​
fn = 'csvPeople.csv'
with open(fn) as csvFile:                   # 開啟csv檔案
    csvDictReader = csv.DictReader(csvFile) # 讀檔案建立DictReader物件   
    for row in csvDictReader:               # 使用迴圈列出字典內容
        print(row['first_name'], row['last_name'])
---
Eli Manning
Kevin  James
Mike Jordon

```

```


import csv
​
fn = 'out2_7.csv'
with open(fn, 'w', newline = '') as csvFile:    # 開啟csv檔案
    csvWriter = csv.writer(csvFile)             # 建立Writer物件   
    csvWriter.writerow(['Name', 'Age', 'City'])
    csvWriter.writerow(['Hung', '35', 'Taipei'])
    csvWriter.writerow(['James', '40', 'Chicago'])
	
```

```	
import csv
​
fn = 'out2_7_1.csv'
with open(fn, 'w') as csvFile:                  # 開啟csv檔案
    csvWriter = csv.writer(csvFile)             # 建立Writer物件   
    csvWriter.writerow(['Name', 'Age', 'City'])
    csvWriter.writerow(['Hung', '35', 'Taipei'])
    csvWriter.writerow(['James', '40', 'Chicago'])

```

```


import csv
​
infn = 'csvReport.csv'                              # 來源檔案
outfn = 'out2_8.csv'                                # 目的檔案
with open(infn) as csvRFile:                        # 開啟csv檔案供讀取
    csvReader = csv.reader(csvRFile)                # 讀檔案建立Reader物件
    listReport = list(csvReader)                    # 將資料轉成串列 
​
with open(outfn, 'w', newline = '') as csvOFile:    # 開啟csv檔案供寫入
    csvWriter = csv.writer(csvOFile)                # 建立Writer物件   
    for row in listReport:                          # 將串列寫入
        csvWriter.writerow(row)


```

```


import csv
​
fn = 'out2_9.csv'
with open(fn, 'w', newline = '') as csvFile:            # 開啟csv檔案
    csvWriter = csv.writer(csvFile, delimiter='\t')     # 建立Writer物件   
    csvWriter.writerow(['Name', 'Age', 'City'])
    csvWriter.writerow(['Hung', '35', 'Taipei'])
    csvWriter.writerow(['James', '40', 'Chicago'])

```

```


import csv
​
fn = 'out2_10.csv'
with open(fn, 'w', newline = '') as csvFile:                    # 開啟csv檔案
    fields = ['Name', 'Age', 'City']
    dictWriter = csv.DictWriter(csvFile, fieldnames=fields)     # 建立Writer物件
​
    dictWriter.writeheader()                                    # 寫入標題
    dictWriter.writerow({'Name':'Hung', 'Age':'35', 'City':'Taipei'})
    dictWriter.writerow({'Name':'James', 'Age':'40', 'City':'Chicago'})

```

```


import csv
​
dictList = [{'Name':'Hung', 'Age':'35', 'City':'Taipei'},       # 定義串列,元素是字典
          {'Name':'James', 'Age':'40', 'City':'Chicago'}]
          
fn = 'out2_11.csv'
with open(fn, 'w', newline = '') as csvFile:                    # 開啟csv檔案
    fields = ['Name', 'Age', 'City']
    dictWriter = csv.DictWriter(csvFile, fieldnames=fields)     # 建立Writer物件
​
    dictWriter.writeheader()                                    # 寫入標題
    for row in dictList:                                        # 寫入內容
        dictWriter.writerow(row)

```

```


import csv
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)         # 讀取文件下一行
print(headerRow)
---
['Date', 'HighTemperature', 'MeanTemperature', 'LowTemperature']

```

```


import csv
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)         # 讀取文件下一行
for i, header in enumerate(headerRow):
    print(i, header)
---
0 Date
1 HighTemperature
2 MeanTemperature
3 LowTemperature
```

```

import csv
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)         # 讀取文件下一行
    highTemps, lowTemps = [], []        # 設定空串列
    for row in csvReader:
        highTemps.append(row[1])        # 儲存最高溫
        lowTemps.append(row[3])         # 儲存最低溫
​
print("最高溫 : ", highTemps)
print("最低溫 : ", lowTemps)
---
最高溫 :  ['26', '25', '22', '27', '25', '25', '26', '22', '18', '20', '21', '22', '18', '15', '15', '16', '23', '23', '22', '18', '15', '17', '16', '17', '18', '19', '24', '26', '25', '27', '18']
最低溫 :  ['20', '18', '19', '20', '19', '20', '20', '18', '16', '16', '18', '18', '14', '12', '13', '13', '16', '18', '18', '12', '12', '12', '13', '14', '13', '13', '13', '16', '17', '14', '14']

```

```


import csv
import matplotlib.pyplot as plt
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)          # 讀取文件下一行
    highTemps = []                       # 設定空串列
    for row in csvReader:
        highTemps.append(int(row[1]))    # 儲存最高溫
        
plt.plot(highTemps)
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()
---
<Figure size 640x480 with 1 Axes>

```

```


import csv
import matplotlib.pyplot as plt
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)             # 讀取文件下一行
    highTemps = []                          # 設定空串列
    for row in csvReader:
        highTemps.append(int(row[1]))       # 儲存最高溫
plt.figure(dpi=80, figsize=(12, 8))         # 設定繪圖區大小                  
plt.plot(highTemps)
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()
```

```
from datetime import datetime
​
dateObj = datetime.strptime('2017/1/1', '%Y/%m/%d')
print(dateObj)
---
2017-01-01 00:00:00

```

```


import csv
import matplotlib.pyplot as plt
from datetime import datetime
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)             # 讀取文件下一行
    dates, highTemps = [], []               # 設定空串列
    for row in csvReader:
        highTemps.append(int(row[1]))       # 儲存最高溫
        currentDate = datetime.strptime(row[0], "%Y/%m/%d")
        dates.append(currentDate)
       
plt.figure(dpi=80, figsize=(12, 8))         # 設定繪圖區大小                  
plt.plot(dates, highTemps)                  # 圖標增加日期刻度
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()

```

```


import csv
import matplotlib.pyplot as plt
from datetime import datetime
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)             # 讀取文件下一行
    dates, highTemps = [], []               # 設定空串列
    for row in csvReader:
        highTemps.append(int(row[1]))       # 儲存最高溫
        currentDate = datetime.strptime(row[0], "%Y/%m/%d")
        dates.append(currentDate)
       
fig = plt.figure(dpi=80, figsize=(12, 8))   # 設定繪圖區大小                  
plt.plot(dates, highTemps)                  # 圖標增加日期刻度
fig.autofmt_xdate()                         # 日期旋轉
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()

```

```


import csv
import matplotlib.pyplot as plt
from datetime import datetime
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)             # 讀取文件下一行
    dates, highTemps = [], []               # 設定空串列
    for row in csvReader:
        highTemps.append(int(row[1]))       # 儲存最高溫
        currentDate = datetime.strptime(row[0], "%Y/%m/%d")
        dates.append(currentDate)
       
fig = plt.figure(dpi=80, figsize=(12, 8))   # 設定繪圖區大小                  
plt.plot(dates, highTemps)                  # 圖標增加日期刻度
fig.autofmt_xdate(rotation=60)              # 日期旋轉
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()


```

```


import csv
import matplotlib.pyplot as plt
from datetime import datetime
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)             # 讀取文件下一行
    dates, highTemps, lowTemps = [], [], [] # 設定空串列
    for row in csvReader:
        try:                    
            currentDate = datetime.strptime(row[0], "%Y/%m/%d")
            highTemp = int(row[1])          # 設定最高溫
            lowTemp = int(row[3])           # 設定最低溫
        except Exception:
            print('有缺值')
        else:
            highTemps.append(highTemp)      # 儲存最高溫
            lowTemps.append(lowTemp)        # 儲存最低溫
            dates.append(currentDate)       # 儲存日期
       
fig = plt.figure(dpi=80, figsize=(12, 8))   # 設定繪圖區大小
plt.plot(dates, highTemps)                  # 繪製最高溫
plt.plot(dates, lowTemps)                   # 繪製最低溫
fig.autofmt_xdate()                         # 日期旋轉
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()
```


```
import csv
import matplotlib.pyplot as plt
from datetime import datetime
​
fn = 'TaipeiWeatherJan.csv'
with open(fn) as csvFile:
    csvReader = csv.reader(csvFile)
    headerRow = next(csvReader)             # 讀取文件下一行
    dates, highTemps, lowTemps = [], [], [] # 設定空串列
    for row in csvReader:
        try:                    
            currentDate = datetime.strptime(row[0], "%Y/%m/%d")
            highTemp = int(row[1])          # 設定最高溫
            lowTemp = int(row[3])           # 設定最低溫
        except Exception:
            print('有缺值')
        else:
            highTemps.append(highTemp)      # 儲存最高溫
            lowTemps.append(lowTemp)        # 儲存最低溫
            dates.append(currentDate)       # 儲存日期
       
fig = plt.figure(dpi=80, figsize=(12, 8))   # 設定繪圖區大小
plt.plot(dates, highTemps)                  # 繪製最高溫
plt.plot(dates, lowTemps)                   # 繪製最低溫
plt.fill_between(dates, highTemps, lowTemps, color='y', alpha=0.2) # 填滿區間
fig.autofmt_xdate()                         # 日期旋轉
plt.title("Weather Report, Jan. 2017", fontsize=24)
plt.xlabel("", fontsize=14)
plt.ylabel("Temperature (C)", fontsize=14)
plt.tick_params(axis='both', labelsize=12, color='red')
plt.show()
```


```
import pickle
game_info = {
    "position_X":"100",
    "position_Y":"200",
    "money":300,
    "pocket":["黃金", "鑰匙", "小刀"]
}
​
fn = "ch2_23.dat"
fn_obj = open(fn, 'wb')         # 二進位開啟
pickle.dump(game_info, fn_obj)
fn_obj.close()
```


```
import pickle
​
fn = "ch2_23.dat"
fn_obj = open(fn, 'rb')         # 二進位開啟
game_info = pickle.load(fn_obj)
fn_obj.close()
print(game_info)
---
{'position_X': '100', 'position_Y': '200', 'money': 300, 'pocket': ['黃金', '鑰匙', '小刀']}
```

```
import xlwt
​
fn = 'out2_25.xls'
datahead = ['Phone', 'TV', 'Notebook']
price = ['35000', '18000', '28000']
wb = xlwt.Workbook()
sh = wb.add_sheet('sheet1', cell_overwrite_ok=True)
for i in range(len(datahead)):
    sh.write(0, i, datahead[i])     # 寫入datahead list
for j in range(len(price)):
    sh.write(1, j, price[j])        # 寫入price list
​
wb.save(fn)
```

```
import xlrd
​
fn = 'out2_25.xls'
wb = xlrd.open_workbook(fn)
sh = wb.sheets()[0]
rows = sh.nrows
for row in range(rows):
    print(sh.row_values(row))
---	
['Phone', 'TV', 'Notebook']
['35000', '18000', '28000']
​```





