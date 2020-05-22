






# encoding

```
# 讀取 CSV File
import pandas as pd # 引用套件並縮寫為 pd  

df_utf8 = pd.read_csv('./iii.csv',encoding='utf-8')  
df_big5 = pd.read_csv('./output4.csv',encoding='big5')

print(df_utf8)  
print(df_big5)  

# codecs.encode(obj, encoding='utf-8', errors='strict')

```

# 用 open 讀取檔案判斷，當檔案為 UTF-8 就印出
```
name = input('請輸入檔名：')

with open(name, 'r', encoding='UTF-8') as file:
    content = file.read()
    print(content)
---
請輸入檔名：./iii.csv
sepal_length,sepal_width,petal_length,petal_width,species
5.1,3.5,1.4,0.2,setosa
4.9,3,1.4,0.2,setosa
4.7,3.2,1.3,0.2,setosa
4.6,3.1,1.5,0.2,setosa

```

# Big5 轉 UTF-8
```
with open("output4.csv", "r", encoding = "Big5") as inFile, open("utf8_output.csv", "w", encoding = "UTF-8") as outFile:
    outFile.write(inFile.read())
```
# Big5 轉 UTF-8
```
# 開啟 Big5 輸入檔案
inFile = open("output4.csv", "r", encoding = "Big5")

# 開啟 UTF-8 輸出檔案
outFile = open("utf8_output.csv", "w", encoding = "UTF-8")

# 以 Big5 編碼讀取檔案
content = inFile.read()

# 以 UTF-8 編碼寫入檔案
outFile.write(content)

# 關閉檔案
inFile.close()
outFile.close()

```

# csv 檔的內容讀取出來
```
import csv

# 開啟 CSV 檔案
with open('./iii.csv', newline='') as csvfile:

  # 讀取 CSV 檔案內容
  rows = csv.reader(csvfile)

  # 以迴圈輸出每一列
  for row in rows:
    print(row)

```

# 這個檔案內容的各個欄位是以冒號（:）來分隔的
```

import csv
with open('./pw.txt', newline='') as csvfile:

    # 以冒號分隔欄位，讀取檔案內容
    rows = csv.reader(csvfile, delimiter=':')

    for row in rows:
        print(row)
```


# 讀取成 Dictionary
## 我們也可以將 csv 檔案的內容讀取進來之後，轉為 Python 的 dictionary 格式
```
import csv
with open('output4.csv', newline='') as csvfile:

    # 讀取 CSV 檔內容，將每一列轉成一個 dictionary
    rows = csv.DictReader(csvfile)

    # 以迴圈輸出指定欄位
    for row in rows:
        print(row['姓名'], row['體重'])

```

# 寫入 CSV 檔案
## 如果我們在程式中產生了表格的資料，想要儲存為 csv 檔案
```
import csv

# 開啟輸出的 CSV 檔案
with open('output4.csv', 'w', newline='') as csvfile:
    # 建立 CSV 檔寫入器
    writer = csv.writer(csvfile)

    # 寫入一列資料
    writer.writerow(['姓名', '身高', '體重'])

    # 寫入另外幾列資料
    writer.writerow(['令狐沖', 175, 60])
    writer.writerow(['岳靈珊', 165, 57])
```



# 指定分隔字元
## 輸出 csv 檔案時也可以自行指定欄位的分隔字元

```
import csv
with open('output3.csv', 'w', newline='') as csvfile:

    # 以空白分隔欄位，建立 CSV 檔寫入器
    writer = csv.writer(csvfile, delimiter=' ')

    writer.writerow(['姓名', '身高', '體重'])
    writer.writerow(['令狐', 175, 60])
    writer.writerow(['岳珊', 165, 57])


```


# 一次寫入二維表格
## 如果我們的資料是已經整理好的二維表格，也可以一次就把整張表格寫進 csv 檔案中
```
import csv

# 二維表格
table = [
    ['姓名', '身高', '體重'],
    ['令狐沖', 175, 60],
    ['岳珊', 165, 57]
]

with open('output2.csv', 'w', newline='') as csvfile:
    writer = csv.writer(csvfile)

    # 寫入二維表格
    writer.writerows(table)

```



# 寫入 Dictionary 
## 如果我們在 Python 中的資料格式是 dictionary，也可以使用 csv.DictWriter 直接將 dictionary 寫入 csv 檔案中

```

import csv
with open('output1.csv', 'w', newline='') as csvfile:
    # 定義欄位
    fieldnames = ['姓名', '身高', '體重']

    # 將 dictionary 寫入 CSV 檔
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)

    # 寫入第一列的欄位名稱
    writer.writeheader()

    # 寫入資料
    writer.writerow({'姓名': '令狐沖', '身高': 175, '體重': 60})
    writer.writerow({'姓名': '岳靈珊', '身高': 165, '體重': 57})
```
