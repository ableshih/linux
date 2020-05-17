

```




Jupyter Notebook
No4_Untitled1
Last Checkpoint: 15 分鐘前
(autosaved)
Current Kernel Logo
Python 3 
File
Edit
View
Insert
Cell
Kernel
Widgets
Help

# ch4_1.py
import pandas as pd
years = range(2020, 2023)
beijing = pd.Series([20, 21, 19], index = years)
hongkong = pd.Series([25, 26, 27], index = years)
singapore = pd.Series([30, 29, 31], index = years)
citydf = pd.concat([beijing, hongkong, singapore])  # 預設axis=0
print(type(citydf))
print(citydf)
<class 'pandas.core.series.Series'>
2020    20
2021    21
2022    19
2020    25
2021    26
2022    27
2020    30
2021    29
2022    31
dtype: int64
# ch4_2.py
import pandas as pd
years = range(2020, 2023)
beijing = pd.Series([20, 21, 19], index = years)
hongkong = pd.Series([25, 26, 27], index = years)
singapore = pd.Series([30, 29, 31], index = years)
citydf = pd.concat([beijing, hongkong, singapore],axis=1)  # axis=1
print(type(citydf))
print(citydf)
<class 'pandas.core.frame.DataFrame'>
       0   1   2
2020  20  25  30
2021  21  26  29
2022  19  27  31
# ch4_3.py
import pandas as pd
years = range(2020, 2023)
beijing = pd.Series([20, 21, 19], index = years)
hongkong = pd.Series([25, 26, 27], index = years)
singapore = pd.Series([30, 29, 31], index = years)
citydf = pd.concat([beijing, hongkong, singapore],axis=1)  # axis=1
cities = ["Beijing", "HongKong", "Singapore"]
citydf.columns = cities
print(citydf)
      Beijing  HongKong  Singapore
2020       20        25         30
2021       21        26         29
2022       19        27         31
# ch4_4.py
import pandas as pd
years = range(2020, 2023)
beijing = pd.Series([20, 21, 19], index = years)
hongkong = pd.Series([25, 26, 27], index = years)
singapore = pd.Series([30, 29, 31], index = years)
beijing.name = "Beijing"
hongkong.name = "HongKong"
singapore.name = "Singapore"
citydf = pd.concat([beijing, hongkong, singapore],axis=1)  
print(citydf)
      Beijing  HongKong  Singapore
2020       20        25         30
2021       21        26         29
2022       19        27         31
# ch4_5.py
import pandas as pd
data = [{'apple':50,'Orange':30,'Grape':80},{'apple':50,'Grape':80}]
fruits = pd.DataFrame(data)
print(fruits)
   Grape  Orange  apple
0     80    30.0     50
1     80     NaN     50
# ch4_6.py
import pandas as pd
cities = {'country':['China', 'Japan', 'Singapore'],
          'town':['Beijing','Tokyo','Singapore'],
          'population':[2000, 1600, 600]}
citydf = pd.DataFrame(cities)
print(citydf)
     country       town  population
0      China    Beijing        2000
1      Japan      Tokyo        1600
2  Singapore  Singapore         600
# ch4_7.py
import pandas as pd
cities = {'country':['China', 'Japan', 'Singapore'],
          'town':['Beijing','Tokyo','Singapore'],
          'population':[2000, 1600, 600]}
rowindex = ['first', 'second', 'third']
citydf = pd.DataFrame(cities, index=rowindex)
print(citydf)
          country       town  population
first       China    Beijing        2000
second      Japan      Tokyo        1600
third   Singapore  Singapore         600
# ch4_8.py
import pandas as pd
cities = {'country':['China', 'Japan', 'Singapore'],
          'town':['Beijing','Tokyo','Singapore'],
          'population':[2000, 1600, 600]}
citydf = pd.DataFrame(cities, columns=["town","population"],
                      index=cities["country"])
print(citydf)
                town  population
China        Beijing        2000
Japan          Tokyo        1600
Singapore  Singapore         600
# ch4_9.py
import pandas as pd
cities = {'Country':['China','China','Thailand','Japan','Singapore'],
          'Town':['Beijing','Shanghai','Bangkok', 'Tokyo','Singapore'],
          'Population':[2000, 2300, 900, 1600, 600]}
df = pd.DataFrame(cities, columns=["Town","Population"],
                  index=cities["Country"])
print(df)
                Town  Population
China        Beijing        2000
China       Shanghai        2300
Thailand     Bangkok         900
Japan          Tokyo        1600
Singapore  Singapore         600
# ch4_10.py
import pandas as pd
import numpy as np
name = ['Frank', 'Peter', 'John']
score = ['first', 'second', 'final']
df = pd.DataFrame(np.random.randint(60,100,size=(3,3)),
                  columns=name,
                  index=score)
print(df)
        Frank  Peter  John
first      90     87    88
second     88     76    82
final      99     97    91
# ch4_11.py
import pandas as pd
​
course = ['Chinese', 'English', 'Math', 'Natural', 'Society']
chinese = [14, 12, 13, 10, 13]
eng = [13, 14, 11, 10, 15]
math = [15, 9, 12, 8, 15]
nature = [15, 10, 13, 10, 15]
social = [12, 11, 14, 9, 14]
​
df = pd.DataFrame([chinese, eng, math, nature, social],
                  columns = course,
                  index = range(1,6))
print(df)
   Chinese  English  Math  Natural  Society
1       14       12    13       10       13
2       13       14    11       10       15
3       15        9    12        8       15
4       15       10    13       10       15
5       12       11    14        9       14
# ch4_12.py
import pandas as pd
​
course = ['Chinese', 'English', 'Math', 'Natural', 'Society']
chinese = [14, 12, 13, 10, 13]
eng = [13, 14, 11, 10, 15]
math = [15, 9, 12, 8, 15]
nature = [15, 10, 13, 10, 15]
social = [12, 11, 14, 9, 14]
​
df = pd.DataFrame([chinese, eng, math, nature, social],
                  columns = course,
                  index = range(1,6))
df.to_csv("out4_12a.csv")
df.to_csv("out4_12b.csv", header=False, index=False)
# ch4_13.py
import pandas as pd
​
course = ['Chinese', 'English', 'Math', 'Natural', 'Society']
x = pd.read_csv("out4_12a.csv",index_col=0)
y = pd.read_csv("out4_12b.csv",names=course)
print(x)
print(y)
   Chinese  English  Math  Natural  Society
1       14       12    13       10       13
2       13       14    11       10       15
3       15        9    12        8       15
4       15       10    13       10       15
5       12       11    14        9       14
   Chinese  English  Math  Natural  Society
0       14       12    13       10       13
1       13       14    11       10       15
2       15        9    12        8       15
3       15       10    13       10       15
4       12       11    14        9       14
# ch4_14.py
import pandas as pd
import matplotlib.pyplot as plt
​
population = [860, 1100, 1450, 1800, 2020, 2200, 2260]
tw = pd.Series(population, index=range(1950, 2011, 10))
tw.plot(title='Population in Taiwan')
plt.xlabel("Year")
plt.ylabel("Population")
plt.show()
<Figure size 640x480 with 1 Axes>
# ch4_15.py
import pandas as pd
import matplotlib.pyplot as plt
​
cities = {'population':[1000, 850, 800, 1500, 600, 800],
          'town':['New York','Chicago','Bangkok','Tokyo',
                   'Singapore','HongKong']}
tw = pd.DataFrame(cities, columns=['population'],index=cities['town'])
          
tw.plot(title='Population in the World')
plt.xlabel('City')
plt.ylabel("Population")
plt.show()

# ch4_16.py
import pandas as pd
import matplotlib.pyplot as plt
​
cities = {'population':[1000, 850, 800, 1500, 600, 800],
          'town':['New York','Chicago','Bangkok','Tokyo',
                   'Singapore','HongKong']}
tw = pd.DataFrame(cities, columns=['population'],index=cities['town'])
          
tw.plot(title='Population in the World',kind='bar')
plt.xlabel('City')
plt.ylabel("Population")
plt.show()

# ch4_17.py
import pandas as pd
import matplotlib.pyplot as plt
​
cities = {'population':[1000, 850, 800, 1500, 600, 800],
          'area':[400, 500, 850, 300, 200, 320],
          'town':['New York','Chicago','Bangkok','Tokyo',
                   'Singapore','HongKong']}
tw = pd.DataFrame(cities, columns=['population','area'],index=cities['town'])
          
tw.plot(title='Population in the World')
plt.xlabel('City')
plt.show()

# ch4_18.py
import pandas as pd
import matplotlib.pyplot as plt
​
cities = {'population':[10000000,8500000,8000000,15000000,6000000,8000000],
          'area':[400, 500, 850, 300, 200, 320],
          'town':['New York','Chicago','Bangkok','Tokyo',
                   'Singapore','HongKong']}
tw = pd.DataFrame(cities, columns=['population','area'],index=cities['town'])
          
tw.plot(title='Population in the World')
plt.xlabel('City')
plt.show()

# ch4_19.py
import pandas as pd
import matplotlib.pyplot as plt
​
cities = {'population':[10000000,8500000,8000000,15000000,6000000,8000000],
          'area':[400, 500, 850, 300, 200, 320],
          'town':['New York','Chicago','Bangkok','Tokyo',
                   'Singapore','HongKong']}
tw = pd.DataFrame(cities, columns=['population','area'],index=cities['town'])
​
fig, ax = plt.subplots()
fig.suptitle("City Statistics")
ax.set_ylabel("Population")
ax.set_xlabel("City")
​
ax2 = ax.twinx()
ax2.set_ylabel("Area")
tw['population'].plot(ax=ax,rot=90)     # 繪製人口數線
tw['area'].plot(ax=ax2, style='g-')     # 繪製面積線
ax.legend(loc=1)                        # 圖例位置在右上
ax2.legend(loc=2)                       # 圖例位置在左上
plt.show()

# ch4_20.py
import pandas as pd
import matplotlib.pyplot as plt
​
cities = {'population':[10000000,8500000,8000000,15000000,6000000,8000000],
          'area':[400, 500, 850, 300, 200, 320],
          'town':['New York','Chicago','Bangkok','Tokyo',
                   'Singapore','HongKong']}
tw = pd.DataFrame(cities, columns=['population','area'],index=cities['town'])
​
fig, ax = plt.subplots()
fig.suptitle("City Statistics")
ax.set_ylabel("Population")
ax.set_xlabel("City")
ax.ticklabel_format(style='plain')      # 不用科學記號表示
ax2 = ax.twinx()
ax2.set_ylabel("Area")
tw['population'].plot(ax=ax,rot=90)     # 繪製人口數線
tw['area'].plot(ax=ax2, style='g-')     # 繪製面積線
ax.legend(loc=1)                        # 圖例位置在右上
ax2.legend(loc=2)                       # 圖例位置在左上
plt.show()

# ch4_21.py
import pandas as pd
import matplotlib.pyplot as plt
​
fruits = ['Apples', 'Bananas', 'Grapes', 'Pears', 'Oranges']
s = pd.Series([2300, 5000, 1200, 2500, 2900], index=fruits,
              name='Fruits Shop')
explode = [0.4, 0, 0, 0.2, 0]
s.plot.pie(explode = explode, autopct='%1.2f%%')
plt.show()

# ch4_21_1.py
from datetime import datetime
​
timeNow = datetime.now()
print(type(timeNow))
print("現在時間 : ", timeNow)
<class 'datetime.datetime'>
現在時間 :  2020-05-17 21:35:58.967117
# ch4_21_2.py
from datetime import datetime
​
timeNow = datetime.now()
print(type(timeNow))
print("現在時間 : ", timeNow)
print("年 : ", timeNow.year)
print("月 : ", timeNow.month)
print("日 : ", timeNow.day)
print("時 : ", timeNow.hour)
print("分 : ", timeNow.minute)
print("秒 : ", timeNow.second)
<class 'datetime.datetime'>
現在時間 :  2020-05-17 21:36:15.236977
年 :  2020
月 :  5
日 :  17
時 :  21
分 :  36
秒 :  15
# ch4_21_3.py
from datetime import datetime
​
timeStop = datetime(2019,7,28,19,50,50)
while datetime.now() < timeStop:
    print("Program is sleeping.", end="")
print("Wake up")
Wake up
# ch4_21_4.py
from datetime import datetime, timedelta
​
deltaTime = timedelta(days=3,hours=5,minutes=8,seconds=10)
print(deltaTime.days, deltaTime.seconds, deltaTime.microseconds)
3 18490 0
# ch4_21_5.py
from datetime import datetime, timedelta
​
deltaTime = timedelta(days=3,hours=5,minutes=8,seconds=10)
print(deltaTime.total_seconds())
277690.0
# ch4_21_6.py
import pandas as pd
from datetime import datetime, timedelta
​
ndays = 5
start = datetime(2019, 3, 11)   
dates = [start + timedelta(days=x) for x in range(0, ndays)]
data = [34, 44, 65, 53, 39]
ts = pd.Series(data, index=dates)
print(type(ts))
print(ts)
<class 'pandas.core.series.Series'>
2019-03-11    34
2019-03-12    44
2019-03-13    65
2019-03-14    53
2019-03-15    39
dtype: int64
# ch4_21_7.py
import pandas as pd
from datetime import datetime, timedelta
​
ndays = 5
start = datetime(2019, 3, 11)   
dates = [start + timedelta(days=x) for x in range(0, ndays)]
data1 = [34, 44, 65, 53, 39]
ts1 = pd.Series(data1, index=dates)
​
data2 = [34, 44, 65, 53, 39]
ts2 = pd.Series(data2, index=dates)
​
addts = ts1 + ts2
print("ts1+ts2")
print(addts)
​
meants = (ts1 + ts2)/2
print("(ts1+ts2)/2")
print(meants)
ts1+ts2
2019-03-11     68
2019-03-12     88
2019-03-13    130
2019-03-14    106
2019-03-15     78
dtype: int64
(ts1+ts2)/2
2019-03-11    34.0
2019-03-12    44.0
2019-03-13    65.0
2019-03-14    53.0
2019-03-15    39.0
dtype: float64
# ch4_21_8.py
import pandas as pd
from datetime import datetime, timedelta
​
ndays = 5
start = datetime(2019, 3, 11)   
dates1 = [start + timedelta(days=x) for x in range(0, ndays)]
data1 = [34, 44, 65, 53, 39]
ts1 = pd.Series(data1, index=dates1)
​
dates2 = [start - timedelta(days=x) for x in range(0, ndays)]
data2 = [34, 44, 65, 53, 39]
ts2 = pd.Series(data2, index=dates2)
​
addts = ts1 + ts2
print("ts1+ts2")
print(addts)
ts1+ts2
2019-03-07     NaN
2019-03-08     NaN
2019-03-09     NaN
2019-03-10     NaN
2019-03-11    68.0
2019-03-12     NaN
2019-03-13     NaN
2019-03-14     NaN
2019-03-15     NaN
dtype: float64
# ch4_21_9.py
import pandas as pd
​
dates = pd.date_range('3/11/2019', '3/15/2019')
data = [34, 44, 65, 53, 39]
ts = pd.Series(data, index=dates)
print(type(ts))
print(ts)
<class 'pandas.core.series.Series'>
2019-03-11    34
2019-03-12    44
2019-03-13    65
2019-03-14    53
2019-03-15    39
Freq: D, dtype: int64
# ch4_21_10.py
import pandas as pd
import matplotlib.pyplot as plt
​
dates = pd.date_range('3/11/2019', '3/15/2019')
data = [34, 44, 65, 53, 39]
ts = pd.Series(data, index=dates)
ts.plot(title='Data in Time Series')
plt.xlabel("Date")
plt.ylabel("Data")
plt.show()

# ch4_22.py
import requests
​
url = 'http://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data'
try:
    htmlfile = requests.get(url)                        # 將檔案下載至htmlfile
    print('下載成功')
except Exception as err:
    print('下載失敗')
​
fn = 'iris.csv'                                         # 未來儲存鳶尾花的檔案
with open(fn, 'wb') as fileobj:                         # 開啟iris.csv
    for diskstorage in htmlfile.iter_content(10240):
        size = fileobj.write(diskstorage)               # 寫入
下載成功
# ch4_23.py
import pandas as pd
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
print('資料集長度 : ', len(iris))
print(iris)
資料集長度 :  150
     sepal_len  sepal_wd  petal_len  petal_wd         species
0          5.1       3.5        1.4       0.2     Iris-setosa
1          4.9       3.0        1.4       0.2     Iris-setosa
2          4.7       3.2        1.3       0.2     Iris-setosa
3          4.6       3.1        1.5       0.2     Iris-setosa
4          5.0       3.6        1.4       0.2     Iris-setosa
5          5.4       3.9        1.7       0.4     Iris-setosa
6          4.6       3.4        1.4       0.3     Iris-setosa
7          5.0       3.4        1.5       0.2     Iris-setosa
8          4.4       2.9        1.4       0.2     Iris-setosa
9          4.9       3.1        1.5       0.1     Iris-setosa
10         5.4       3.7        1.5       0.2     Iris-setosa
11         4.8       3.4        1.6       0.2     Iris-setosa
12         4.8       3.0        1.4       0.1     Iris-setosa
13         4.3       3.0        1.1       0.1     Iris-setosa
14         5.8       4.0        1.2       0.2     Iris-setosa
15         5.7       4.4        1.5       0.4     Iris-setosa
16         5.4       3.9        1.3       0.4     Iris-setosa
17         5.1       3.5        1.4       0.3     Iris-setosa
18         5.7       3.8        1.7       0.3     Iris-setosa
19         5.1       3.8        1.5       0.3     Iris-setosa
20         5.4       3.4        1.7       0.2     Iris-setosa
21         5.1       3.7        1.5       0.4     Iris-setosa
22         4.6       3.6        1.0       0.2     Iris-setosa
23         5.1       3.3        1.7       0.5     Iris-setosa
24         4.8       3.4        1.9       0.2     Iris-setosa
25         5.0       3.0        1.6       0.2     Iris-setosa
26         5.0       3.4        1.6       0.4     Iris-setosa
27         5.2       3.5        1.5       0.2     Iris-setosa
28         5.2       3.4        1.4       0.2     Iris-setosa
29         4.7       3.2        1.6       0.2     Iris-setosa
..         ...       ...        ...       ...             ...
120        6.9       3.2        5.7       2.3  Iris-virginica
121        5.6       2.8        4.9       2.0  Iris-virginica
122        7.7       2.8        6.7       2.0  Iris-virginica
123        6.3       2.7        4.9       1.8  Iris-virginica
124        6.7       3.3        5.7       2.1  Iris-virginica
125        7.2       3.2        6.0       1.8  Iris-virginica
126        6.2       2.8        4.8       1.8  Iris-virginica
127        6.1       3.0        4.9       1.8  Iris-virginica
128        6.4       2.8        5.6       2.1  Iris-virginica
129        7.2       3.0        5.8       1.6  Iris-virginica
130        7.4       2.8        6.1       1.9  Iris-virginica
131        7.9       3.8        6.4       2.0  Iris-virginica
132        6.4       2.8        5.6       2.2  Iris-virginica
133        6.3       2.8        5.1       1.5  Iris-virginica
134        6.1       2.6        5.6       1.4  Iris-virginica
135        7.7       3.0        6.1       2.3  Iris-virginica
136        6.3       3.4        5.6       2.4  Iris-virginica
137        6.4       3.1        5.5       1.8  Iris-virginica
138        6.0       3.0        4.8       1.8  Iris-virginica
139        6.9       3.1        5.4       2.1  Iris-virginica
140        6.7       3.1        5.6       2.4  Iris-virginica
141        6.9       3.1        5.1       2.3  Iris-virginica
142        5.8       2.7        5.1       1.9  Iris-virginica
143        6.8       3.2        5.9       2.3  Iris-virginica
144        6.7       3.3        5.7       2.5  Iris-virginica
145        6.7       3.0        5.2       2.3  Iris-virginica
146        6.3       2.5        5.0       1.9  Iris-virginica
147        6.5       3.0        5.2       2.0  Iris-virginica
148        6.2       3.4        5.4       2.3  Iris-virginica
149        5.9       3.0        5.1       1.8  Iris-virginica

[150 rows x 5 columns]
# ch4_24.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
​
iris.plot(x='sepal_len',y='sepal_wd',kind='scatter')
plt.xlabel('Sepal Length')
plt.ylabel('Sepal Width')
plt.title('Iris Sepal length and width anslysis')
plt.show()

# ch4_25.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
​
plt.plot(iris['sepal_len'],iris['sepal_wd'],'*',color='g')
plt.xlabel('Sepal Length')
plt.ylabel('Sepal Width')
plt.title('Iris Sepal length and width anslysis')
plt.show()

# ch4_26.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
​
# 擷取不同品種的鳶尾花
iris_setosa = iris[iris['species'] == 'Iris-setosa']
iris_versicolor = iris[iris['species'] == 'Iris-versicolor']
iris_virginica = iris[iris['species'] == 'Iris-virginica']
# 繪製散點圖
plt.plot(iris_setosa['sepal_len'],iris_setosa['sepal_wd'],
         '*',color='g',label='setosa')
plt.plot(iris_versicolor['sepal_len'],iris_versicolor['sepal_wd'],
         'x',color='b',label='versicolor')
plt.plot(iris_virginica['sepal_len'],iris_virginica['sepal_wd'],
         '.',color='r',label='virginica')
# 標註軸和標題
plt.xlabel('Sepal Length')
plt.ylabel('Sepal Width')
plt.title('Iris Sepal length and width anslysis')
plt.legend()
plt.show()

# ch4_27.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
​
# 鳶尾花分組統計均值
iris_mean = iris.groupby('species', as_index=False).mean()
# 繪製直條圖
iris_mean.plot(kind='bar')
# 刻度處理
plt.xticks(iris_mean.index,iris_mean['species'], rotation=0)
​
plt.show()

# ch4_28.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
iris['species'] = iris['species'].apply(lambda x: x.replace("Iris-",""))
# 鳶尾花分組統計均值
iris_mean = iris.groupby('species', as_index=False).mean()
# 繪製直條圖
iris_mean.plot(kind='bar')
# 刻度處理
plt.xticks(iris_mean.index,iris_mean['species'], rotation=0)
​
plt.show()

# ch4_29.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
iris['species'] = iris['species'].apply(lambda x: x.replace("Iris-",""))
# 鳶尾花分組統計均值
iris_mean = iris.groupby('species', as_index=False).mean()
# 繪製堆疊直條圖
iris_mean.plot(kind='bar',stacked=True)
# 刻度處理
plt.xticks(iris_mean.index,iris_mean['species'], rotation=0)
​
plt.show()

# ch4_30.py
import pandas as pd
import matplotlib.pyplot as plt
​
colName = ['sepal_len','sepal_wd','petal_len','petal_wd','species']
iris = pd.read_csv('iris.csv', names = colName)
iris['species'] = iris['species'].apply(lambda x: x.replace("Iris-",""))
# 鳶尾花分組統計均值
iris_mean = iris.groupby('species', as_index=False).mean()
# 繪製堆疊橫條圖
iris_mean.plot(kind='barh',stacked=True)
# 刻度處理
plt.yticks(iris_mean.index,iris_mean['species'], rotation=0)
​
plt.show()

# ch4_31.py
import pandas as pd
​
url = 'http://www.stockq.org/market/currency.php'
currencys = pd.read_html(url)
​
print(type(currencys))              # 列出資料型態
print(currencys)                    # 列出匯率的串列內容
<class 'list'>
[                                                   0
0  google_ad_client = "ca-pub-9803646600609510"; ...,                                                    0
0  google_ad_client = "ca-pub-9803646600609510"; ...
1  首頁 市場動態 歷史股價 基金淨值 基金分類 經濟數據總覽 美元定存  技術指標 期貨報告 ...,     0                                                  1
0 NaN  google_ad_client = "ca-pub-9803646600609510"; ...,                                                    0     1
0  首頁 市場動態 歷史股價 基金淨值 基金分類 經濟數據總覽 美元定存  技術指標 期貨報告 ...  简体中文,                                                    0  \
0  市場動態 全球股市排行榜 相對低檔股市指數 相對高檔股市指數 亞洲股市指數 歐洲股市、非洲指...   

                                                   1  
0  全球貨幣匯率 刷新時間 2020/5/17 21:40:50  全球匯率 (Currency...  ,                                                    0
0  市場動態 全球股市排行榜 相對低檔股市指數 相對高檔股市指數 亞洲股市指數 歐洲股市、非洲指...,                                 0   1
0  全球貨幣匯率 刷新時間 2020/5/17 21:40:50 NaN,                            0                         1  \
0   全球匯率 (Currency Exchange)  全球匯率 (Currency Exchange)   
1                         貨幣                        匯率   
2                      歐元/美元                    1.0818   
3                      英鎊/美元                    1.2104   
4                    美元/瑞士法郎                    0.9714   
5                    美元/瑞典克朗                    9.8659   
6                     美元/俄盧布                   73.6160   
7                    美元/匈牙利幣                    327.49   
8                    美元/土耳其幣                    6.8992   
9                     美元/南非幣                   18.5599   
10                   美元/以色列幣                    3.5353   
11                    美元/摩洛哥                    9.8865   
12                     澳幣/美元                    0.6413   
13                     紐幣/美元                    0.5933   
14                     美元/日圓                    107.02   
15                    美元/人民幣                    7.1013   
16                     美元/港幣                    7.7508   
17                     美元/台幣                    29.954   
18                     美元/韓圜                   1232.69   
19                     美元/泰銖                    32.080   
20                     美元/新元                    1.4271   
21                    美元/菲披索                    50.650   
22                    美元/馬來幣                    4.3490   
23                    美元/印尼盾                   14830.0   
24                   美元/印度盧比                    75.817   
25                     美元/加幣                    1.4107   
26                    美元/巴西幣                    5.8554   
27                    美元/墨披索                   23.9282   
28                    美元/阿根廷                   67.5850   
29                     美元/智利                    827.13   

                           2                         3  \
0   全球匯率 (Currency Exchange)  全球匯率 (Currency Exchange)   
1                         漲跌                        比例   
2                     0.0016                     0.15%   
3                    -0.0120                    -0.98%   
4                    -0.0014                    -0.15%   
5                     0.0646                     0.66%   
6                     0.1285                     0.17%   
7                       0.18                     0.06%   
8                    -0.0168                    -0.24%   
9                     0.1460                     0.79%   
10                   -0.0040                    -0.11%   
11                    0.0333                     0.34%   
12                   -0.0047                    -0.73%   
13                   -0.0066                    -1.11%   
14                     -0.20                    -0.19%   
15                    0.0086                     0.12%   
16                   -0.0006                    -0.01%   
17                     0.090                     0.30%   
18                      6.16                     0.50%   
19                     0.000                     0.00%   
20                    0.0043                     0.30%   
21                     0.180                     0.36%   
22                    0.0135                     0.31%   
23                      20.0                     0.13%   
24                     0.350                     0.46%   
25                    0.0061                     0.43%   
26                    0.0456                     0.78%   
27                    0.0757                     0.32%   
28                    0.0915                     0.14%   
29                      6.17                     0.75%   

                           4  
0   全球匯率 (Currency Exchange)  
1                         台北  
2                      04:59  
3                      04:59  
4                      04:59  
5                      04:59  
6                      04:50  
7                      04:59  
8                      04:59  
9                      04:58  
10                     04:59  
11                     04:59  
12                     04:59  
13                     04:59  
14                     04:59  
15                     23:30  
16                     04:56  
17                     04:59  
18                     04:59  
19                     04:59  
20                     04:59  
21                     04:54  
22                     21:46  
23                     15:58  
24                     04:59  
25                     04:59  
26                     04:59  
27                     04:59  
28                     04:57  
29                     04:57  ,                                                    0
0  google_ad_client = "ca-pub-9803646600609510"; ...,                                                    0
0            行動網站  | 借錢救急 | Outlet  | 網站地圖  | 聯絡我們 ﻿
1  StockQ 全球股市指數 / 简体版 / English / Indeks pasar ©...]
# ch4_32.py
import pandas as pd
​
url = 'http://www.stockq.org/market/currency.php'
currencys = pd.read_html(url)         # 讀取全球匯率行情表
​
item = 0
for currency in currencys:
    print("元素 : ", item)            # 列出元素編號
    print(currency)                   # 列出元素內容
    print()
    item += 1
元素 :  0
                                                   0
0  google_ad_client = "ca-pub-9803646600609510"; ...

元素 :  1
                                                   0
0  google_ad_client = "ca-pub-9803646600609510"; ...
1  首頁 市場動態 歷史股價 基金淨值 基金分類 經濟數據總覽 美元定存  技術指標 期貨報告 ...

元素 :  2
    0                                                  1
0 NaN  google_ad_client = "ca-pub-9803646600609510"; ...

元素 :  3
                                                   0     1
0  首頁 市場動態 歷史股價 基金淨值 基金分類 經濟數據總覽 美元定存  技術指標 期貨報告 ...  简体中文

元素 :  4
                                                   0  \
0  市場動態 全球股市排行榜 相對低檔股市指數 相對高檔股市指數 亞洲股市指數 歐洲股市、非洲指...   

                                                   1  
0  全球貨幣匯率 刷新時間 2020/5/17 21:41:09  全球匯率 (Currency...  

元素 :  5
                                                   0
0  市場動態 全球股市排行榜 相對低檔股市指數 相對高檔股市指數 亞洲股市指數 歐洲股市、非洲指...

元素 :  6
                                0   1
0  全球貨幣匯率 刷新時間 2020/5/17 21:41:09 NaN

元素 :  7
                           0                         1  \
0   全球匯率 (Currency Exchange)  全球匯率 (Currency Exchange)   
1                         貨幣                        匯率   
2                      歐元/美元                    1.0818   
3                      英鎊/美元                    1.2104   
4                    美元/瑞士法郎                    0.9714   
5                    美元/瑞典克朗                    9.8659   
6                     美元/俄盧布                   73.6160   
7                    美元/匈牙利幣                    327.49   
8                    美元/土耳其幣                    6.8992   
9                     美元/南非幣                   18.5599   
10                   美元/以色列幣                    3.5353   
11                    美元/摩洛哥                    9.8865   
12                     澳幣/美元                    0.6413   
13                     紐幣/美元                    0.5933   
14                     美元/日圓                    107.02   
15                    美元/人民幣                    7.1013   
16                     美元/港幣                    7.7508   
17                     美元/台幣                    29.954   
18                     美元/韓圜                   1232.69   
19                     美元/泰銖                    32.080   
20                     美元/新元                    1.4271   
21                    美元/菲披索                    50.650   
22                    美元/馬來幣                    4.3490   
23                    美元/印尼盾                   14830.0   
24                   美元/印度盧比                    75.817   
25                     美元/加幣                    1.4107   
26                    美元/巴西幣                    5.8554   
27                    美元/墨披索                   23.9282   
28                    美元/阿根廷                   67.5850   
29                     美元/智利                    827.13   

                           2                         3  \
0   全球匯率 (Currency Exchange)  全球匯率 (Currency Exchange)   
1                         漲跌                        比例   
2                     0.0016                     0.15%   
3                    -0.0120                    -0.98%   
4                    -0.0014                    -0.15%   
5                     0.0646                     0.66%   
6                     0.1285                     0.17%   
7                       0.18                     0.06%   
8                    -0.0168                    -0.24%   
9                     0.1460                     0.79%   
10                   -0.0040                    -0.11%   
11                    0.0333                     0.34%   
12                   -0.0047                    -0.73%   
13                   -0.0066                    -1.11%   
14                     -0.20                    -0.19%   
15                    0.0086                     0.12%   
16                   -0.0006                    -0.01%   
17                     0.090                     0.30%   
18                      6.16                     0.50%   
19                     0.000                     0.00%   
20                    0.0043                     0.30%   
21                     0.180                     0.36%   
22                    0.0135                     0.31%   
23                      20.0                     0.13%   
24                     0.350                     0.46%   
25                    0.0061                     0.43%   
26                    0.0456                     0.78%   
27                    0.0757                     0.32%   
28                    0.0915                     0.14%   
29                      6.17                     0.75%   

                           4  
0   全球匯率 (Currency Exchange)  
1                         台北  
2                      04:59  
3                      04:59  
4                      04:59  
5                      04:59  
6                      04:50  
7                      04:59  
8                      04:59  
9                      04:58  
10                     04:59  
11                     04:59  
12                     04:59  
13                     04:59  
14                     04:59  
15                     23:30  
16                     04:56  
17                     04:59  
18                     04:59  
19                     04:59  
20                     04:59  
21                     04:54  
22                     21:46  
23                     15:58  
24                     04:59  
25                     04:59  
26                     04:59  
27                     04:59  
28                     04:57  
29                     04:57  

元素 :  8
                                                   0
0  google_ad_client = "ca-pub-9803646600609510"; ...

元素 :  9
                                                   0
0            行動網站  | 借錢救急 | Outlet  | 網站地圖  | 聯絡我們 ﻿
1  StockQ 全球股市指數 / 简体版 / English / Indeks pasar ©...

# ch4_33.py
import pandas as pd
​
url = 'http://www.stockq.org/market/currency.php'
currencys = pd.read_html(url)                               # 讀取全球匯率行情表
​
currency = currencys[7]                                     # 讀取第7元素
currency = currency.drop(currency.index[[0,1]])             # 拋棄前2 row
currency.columns = ['貨幣', '匯率', '漲跌', '比例', '台北'] # 建立column標題
currency.index = range(len(currency.index))                 # 建立row標題
print(currency)
         貨幣       匯率       漲跌      比例     台北
0     歐元/美元   1.0818   0.0016   0.15%  04:59
1     英鎊/美元   1.2104  -0.0120  -0.98%  04:59
2   美元/瑞士法郎   0.9714  -0.0014  -0.15%  04:59
3   美元/瑞典克朗   9.8659   0.0646   0.66%  04:59
4    美元/俄盧布  73.6160   0.1285   0.17%  04:50
5   美元/匈牙利幣   327.49     0.18   0.06%  04:59
6   美元/土耳其幣   6.8992  -0.0168  -0.24%  04:59
7    美元/南非幣  18.5599   0.1460   0.79%  04:58
8   美元/以色列幣   3.5353  -0.0040  -0.11%  04:59
9    美元/摩洛哥   9.8865   0.0333   0.34%  04:59
10    澳幣/美元   0.6413  -0.0047  -0.73%  04:59
11    紐幣/美元   0.5933  -0.0066  -1.11%  04:59
12    美元/日圓   107.02    -0.20  -0.19%  04:59
13   美元/人民幣   7.1013   0.0086   0.12%  23:30
14    美元/港幣   7.7508  -0.0006  -0.01%  04:56
15    美元/台幣   29.954    0.090   0.30%  04:59
16    美元/韓圜  1232.69     6.16   0.50%  04:59
17    美元/泰銖   32.080    0.000   0.00%  04:59
18    美元/新元   1.4271   0.0043   0.30%  04:59
19   美元/菲披索   50.650    0.180   0.36%  04:54
20   美元/馬來幣   4.3490   0.0135   0.31%  21:46
21   美元/印尼盾  14830.0     20.0   0.13%  15:58
22  美元/印度盧比   75.817    0.350   0.46%  04:59
23    美元/加幣   1.4107   0.0061   0.43%  04:59
24   美元/巴西幣   5.8554   0.0456   0.78%  04:59
25   美元/墨披索  23.9282   0.0757   0.32%  04:59
26   美元/阿根廷  67.5850   0.0915   0.14%  04:57
27    美元/智利   827.13     6.17   0.75%  04:57
​



```
