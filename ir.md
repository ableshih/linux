

```

# https://www.itread01.com/content/1546119574.html
#匯入資料集iris  
from sklearn.datasets import load_iris  
#載入資料集  
iris = load_iris()  
#輸出資料集  
print (iris.data)

#    Iris Setosa（山鳶尾）
#    Iris Versicolour（雜色鳶尾）
#    Iris Virginica（維吉尼亞鳶尾）
    
#輸出真實標籤  
print (iris.target)
print (len(iris.target))
#150個樣本 每個樣本4個特徵  
print (iris.data.shape)

'''
可以看到，類標共分為三類，前面50個類標位0，中間50個類標位1，
後面為2。下面講解另一種匯入鳶尾花資料集的方法，這裡是從某一網頁匯入資料，
但是如果網頁打不開很可能就匯入不了，但也普及下方法。程式碼如下：
'''


import pandas
#匯入資料集iris  
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names) #讀取csv資料
print(dataset.describe())
'''
輸出如圖所示，鳶尾花(iris)是資料探勘常用到的一個數據集，
包含150種鳶尾花的資訊，每50種取自三個鳶尾花種之一（setosa,versicolour或virginica)。
每個花的特徵用下面的5種屬性描述萼片長度(Sepal.Length)、萼片寬度(Sepal.Width)、花瓣長度(Petal.Length)、
花瓣寬度(Petal.Width)、類(Species)。

'''


import pandas
#匯入資料集iris  
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names) #讀取csv資料
print(dataset.describe())
#直方圖 histograms
dataset.hist()



import pandas
#匯入資料集iris  
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names) #讀取csv資料
print(dataset.describe())
dataset.plot(x='sepal-length', y='sepal-width', kind='scatter')



import pandas
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names) #讀取csv資料
print(dataset.describe())
dataset.plot(kind='kde')



import pandas 
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names) #讀取csv資料
print(dataset.describe())
dataset.plot(kind='kde')
dataset.plot(kind='box', subplots=True, layout=(2,2), 
             sharex=False, sharey=False)


import pandas
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names)

from pandas.tools.plotting import radviz
radviz(dataset, 'class')

from pandas.tools.plotting import andrews_curves
andrews_curves(dataset, 'class')

from pandas.tools.plotting import parallel_coordinates
parallel_coordinates(dataset, 'class')




import pandas
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data"
names = ['sepal-length', 'sepal-width', 'petal-length', 'petal-width', 'class']
dataset = pandas.read_csv(url, names=names)

from pandas.tools.plotting import scatter_matrix
scatter_matrix(dataset, alpha=0.2, figsize=(6, 6), diagonal='kde')




from sklearn.datasets import load_iris
hua = load_iris()
#獲取花瓣的長和寬
x = [n[0] for n in hua.data]
y = [n[1] for n in hua.data]




import numpy as np #轉換成陣列
x = np.array(x).reshape(len(x),1)
y = np.array(y).reshape(len(y),1)




from sklearn.linear_model import LinearRegression
clf = LinearRegression()
clf.fit(x,y)
pre = clf.predict(x)




#第三步 畫圖
import matplotlib.pyplot as plt
plt.scatter(x,y,s=100)
plt.plot(x,pre,"r-",linewidth=4)
for idx, m in enumerate(x):
    plt.plot([m,m],[y[idx],pre[idx]], 'g-')
plt.show()



from sklearn.datasets import load_iris
hua = load_iris()
#獲取花瓣的長和寬
x = [n[0] for n in hua.data]
y = [n[1] for n in hua.data]
import numpy as np #轉換成陣列
x = np.array(x).reshape(len(x),1)
y = np.array(y).reshape(len(y),1)

from sklearn.linear_model import LinearRegression
clf = LinearRegression()
clf.fit(x,y)
pre = clf.predict(x)

#第三步 畫圖
import matplotlib.pyplot as plt
plt.scatter(x,y,s=100)
plt.plot(x,pre,"r-",linewidth=4)
for idx, m in enumerate(x):
    plt.plot([m,m],[y[idx],pre[idx]], 'g-')
plt.show()



print(u"係數", clf.coef_)
print (u"截距", clf.intercept_)
print (np.mean(y-pre)**2)
# 係數 [[-0.05726823]]
# 截距 [ 3.38863738]
# 1.91991214088e-31



print (clf.predict([[5.0]]))
# [[ 3.10229621]]



sklearn.tree.DecisionTreeClassifier(criterion='gini', splitter='best'
    ,max_depth=None, min_samples_split=2, min_samples_leaf=1
    ,max_features=None, random_state=None, min_density=None
    ,compute_importances=None, max_leaf_nodes=None)



# 鳶尾花資料集使用決策樹的程式碼如下：
from sklearn.datasets import load_iris 
from sklearn.tree import DecisionTreeClassifier   
iris = load_iris()    
clf = DecisionTreeClassifier()  
clf.fit(iris.data, iris.target)  
print (clf)
predicted = clf.predict(iris.data)  
  
#獲取花卉兩列資料集  
X = iris.data  
L1 = [x[0] for x in X]  
print (L1)  
L2 = [x[1] for x in X]  
print (L2)  
  
import numpy as np  
import matplotlib.pyplot as plt  
plt.scatter(L1, L2, c=predicted, marker='x')  #cmap=plt.cm.Paired  
plt.title("DTC")  
plt.show()




from sklearn.datasets import load_iris   
from sklearn.tree import DecisionTreeClassifier  
 
iris = load_iris()   
#訓練集  
train_data = np.concatenate((iris.data[0:40, :], iris.data[50:90, :], iris.data[100:140, :]), axis = 0)  
train_target = np.concatenate((iris.target[0:40], iris.target[50:90], iris.target[100:140]), axis = 0)  
#測試集  
test_data = np.concatenate((iris.data[40:50, :], iris.data[90:100, :], iris.data[140:150, :]), axis = 0)  
test_target = np.concatenate((iris.target[40:50], iris.target[90:100], iris.target[140:150]), axis = 0)  

#訓練  
clf = DecisionTreeClassifier()   
clf.fit(train_data, train_target)  
predict_target = clf.predict(test_data)  
print (predict_target)
  
#預測結果與真實結果比對  
print (sum(predict_target == test_target))
  
#輸出準確率 召回率 F值  
from sklearn import metrics  
print(metrics.classification_report(test_target,predict_target))  
print(metrics.confusion_matrix(test_target,predict_target)) 
X = test_data  
L1 = [n[0] for n in X]  
print (L1) 
L2 = [n[1] for n in X]  
print (L2)  
import numpy as np  
import matplotlib.pyplot as plt  
plt.scatter(L1, L2, c=predict_target, marker='x')  #cmap=plt.cm.Paired  
plt.title("DecisionTreeClassifier")  
plt.show()



# Kmeans聚類分析鳶尾花
# KMeans聚類鳶尾花的程式碼如下，它則不需要類標（屬於某一類鳶尾花），而是根據資料之間的相似性，按照“物以類聚，人以群分”進行聚類。程式碼如下：

# -*- coding: utf-8 -*-
from sklearn.datasets import load_iris 
from sklearn.cluster import KMeans   
iris = load_iris()    
clf = KMeans()  
clf.fit(iris.data, iris.target)  
print (clf)   
predicted = clf.predict(iris.data)  
  
#獲取花卉兩列資料集  
X = iris.data  
L1 = [x[0] for x in X]  
print (L1)  
L2 = [x[1] for x in X]  
print (L2)  
  
import numpy as np  
import matplotlib.pyplot as plt  
plt.scatter(L1, L2, c=predicted, marker='s',s=200,cmap=plt.cm.Paired)  
plt.title("DTC")  
plt.show() 




```
