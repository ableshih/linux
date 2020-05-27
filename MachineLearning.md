

-----------------------
scikit-learn algorithm cheat-sheet 科學學習 算法備忘單
START 開始
get more data 獲得更多數據
predicting a category 預測類別
do you have labeled data 你有標註數據嗎
predicting a quantity 預測數量
just looking 只是看看
predicting structure 預測結構
tough luck 倒霉

===
classification 分類
<100K samples 樣本
SGD Classifier SGD分類器
kernel approximation 核心近似
Linear SVC 線性SVC
Text Data 文字數據
Naive Bayes 樸素貝葉斯
KNeighbors Classifier 鄰居分類器
svc
Ensemble Classifiers 整體分類器

===
regression 回歸
<100K samples 樣本
SGD Regressor SGD回歸器
few features should be important 幾個功能應該很重要
Lasso 套索
ElasticNet 彈性網
RidgeRegression 嶺回歸
SVR(kernel='linear') SVR（內核='線性'）
SVR(kernel='rbf') SVR（內核='rbf'）
EnsembleRegressors 合奏回歸器

===
clustering 聚類
<10K samples 樣本
Meanshift 均值漂移
VBGMM
number of categories known 已知類別數
MiniBatch KMeans
KMeans 均值
Spectral Clustering 光譜聚類
GMM 

===
dimensionality reduction 降維
<10K samples 樣本
Randomized PCA 隨機PCA
kernel approximation 核心近似
Isomap 等值圖
Spectral Embedding 光譜嵌入
LLE

==


# 鳶尾花

機器學習 鳶尾花
強化學習 台科大 給一點小東西(球)就讓慢慢學會投籃

scikit-learn algorithm cheat-sheet

classification 
scikit-learn
won algorithm cheat-sheet
NOT eet
WORKING more
NO
NO
>50 i
YES NO NoT YES regression
ll cvs ws
predicting a
ves (a Category
YES €S
NOT labeled No
WORKING ele few features
YES \S important
predicting a . NO
quantity
YES VES categories
clustering cnown
samples NO
just
YES WORKING
No WORKING
YES
<10K . . :
4 Mo dimensionality
predicting *
Ccug reduction




classification分類 <100kY -> Linear SVC
classification分類 <100kN -> SGD classifier
regression回歸 <100k -> 
regression回歸 <100k -> 
clustering聚類 <10k -> labeled data沒標記 -> number of categories known 已知類別數
clustering聚類 <10k -> 
dimensionality reduction降維 <10kY -> spectral embedding
dimensionality reduction降維 <10kN -> kernel approximation



clustering


開始 -> 資料 50筆 -> category類別 -> labeled data標記數據 -> 超過100k筆
開始 -> 資料 50筆 -> category類別 -> labeled data沒有標記 -> number of categories knownYES ->
開始 -> 資料 50筆 -> category類別 -> labeled data沒有標記 -> number of categories knownNO ->10K

開始 -> 資料 50筆 -> category沒有 -> quantity數量 ->








# 2
Scikit-Learn 

基於
numpy 1.6.1
scipy 0.9

pip install numpy
pip install scipy  

pip install -U scikit-learn (-U update)
or 
conda install scikit-learn

# 3
機器圖ful
https://scikit-learn.org/stable/tutorial/machine_learning_map/index.html

要大於50筆

非監督式  clustering
監督式 regression 迴歸
監督式 classification
壓縮



# 4

iris
'''
from __future__ import print_function
from sklearn import datasets
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsClassifier

iris = datasets.load_iris()
iris_X = iris.data
iris_y = iris.target

##print(iris_X[:2, :]) # 看前兩筆資料屬性
##print(iris_y) # 看所有資料中的 分類 可得知資料是依 類別 排序過的 

X_train, X_test, y_train, y_test = train_test_split(
    iris_X, iris_y, test_size=0.3) # 切割資料 

##print(y_train) #看切割過的資料 看的是用來學習的70%資料 資料會被亂數重排過借以提高學習效率(亂的數據與不亂的數據 學亂的比學不亂的 好)

knn = KNeighborsClassifier() # 引用訓練函式
knn.fit(X_train, y_train) # 訓練
print(knn.predict(X_test)) # 預測值 訓練
print(y_test) # 原始的值 真實值
# 比出來不會百分百
'''
# 5 


除 iris 外 其他的資料庫
https://scikit-learn.org/stable/modules/classes.html#module-sklearn.datasets

破士頓房價 506筆 

'''
from __future__ import print_function
from sklearn import datasets
from sklearn.linear_model import LinearRegression


loaded_data = datasets.load_boston() 
data_X = loaded_data.data
data_y = loaded_data.target

model = LinearRegression() # 定義用 Regression
model.fit(data_X, data_y)

print(model.predict(data_X[:4, :])) # 用預測到的前四筆
print(data_y[:4]) # 真實的前四筆


# 畫出 訓練資料
import matplotlib.pyplot as plt

X, y = datasets.make_regression(n_samples=100, n_features=1, n_targets=1, noise=10) # 創造數據 100筆
plt.scatter(X, y)
plt.show()

'''

# 6 model 常用屬性與功能
'''
from __future__ import print_function
from sklearn import datasets
from sklearn.linear_model import LinearRegression

loaded_data = datasets.load_boston()
data_X = loaded_data.data
data_y = loaded_data.target

model = LinearRegression()
model.fit(data_X, data_y)

print(model.predict(data_X[:4, :]))

print(model.coef_)
print(model.intercept_)

print(model.get_params())
print(model.score(data_X, data_y)) # R^2 coefficient of determination



'''
# 7 normalization 標準化數據
 
取值 會影響 
'''

from __future__ import print_function
from sklearn import preprocessing
import numpy as np

a = np.array([[10, 2.7, 3.6],
                     [-100, 5, -2],
                     [120, 20, 40]], dtype=np.float64)

print(a) # 原始
print(preprocessing.scale(a)) # scale值
'''

'''
from __future__ import print_function
from sklearn import preprocessing
import numpy as np
from sklearn.model_selection import train_test_split # 切割
from sklearn.datasets.samples_generator import make_classification # 產生 classification
from sklearn.svm import SVC # 處理 模型
import matplotlib.pyplot as plt # 畫圖

X, y = make_classification(n_samples=300, n_features=2 , n_redundant=0, n_informative=2,
                           random_state=22, n_clusters_per_class=1, scale=100) # 產生300筆 2個屬性 2個相關 隨機22 

# 畫出 兩類 線性圖
plt.scatter(X[:, 0], X[:, 1], c=y)
plt.show()
'''

'''
from __future__ import print_function
from sklearn import preprocessing
import numpy as np
from sklearn.model_selection import train_test_split # 切割
from sklearn.datasets.samples_generator import make_classification # 產生 classification
from sklearn.svm import SVC # 處理 模型
import matplotlib.pyplot as plt # 畫圖
X = preprocessing.scale(X) # 壓縮   # normalization step
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=.3) # 切割
clf = SVC() #
clf.fit(X_train, y_train) # 學習
print(clf.score(X_test, y_test)) # 預測
# 印出準確百分比 0.9xx
'''

'''
# 不用 scale
from __future__ import print_function
from sklearn import preprocessing
import numpy as np
from sklearn.model_selection import train_test_split # 切割
from sklearn.datasets.samples_generator import make_classification # 產生 classification
from sklearn.svm import SVC # 處理 模型
import matplotlib.pyplot as plt # 畫圖
#X = preprocessing.scale(X) # 壓縮   # normalization step
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=.3) # 切割
clf = SVC() #
clf.fit(X_train, y_train) # 學習
print(clf.score(X_test, y_test)) # 預測
# 印出準確百分比 0.48xx
'''


# 評價 
原始資料切割 分 訓練資料 測試資料
交差驗證

# 8 cross validation 交叉驗證


'''
from __future__ import print_function
from sklearn.datasets import load_iris
from sklearn.cross_validation import train_test_split
from sklearn.neighbors import KNeighborsClassifier

iris = load_iris()
X = iris.data
y = iris.target

# test train split #
X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=4)
knn = KNeighborsClassifier(n_neighbors=5) # 訓練 附近的5點的平衡
knn.fit(X_train, y_train)
y_pred = knn.predict(X_test)
print(knn.score(X_test, y_test)) # 得到百分亡比 0.97xx

'''


'''
from __future__ import print_function
from sklearn.datasets import load_iris
from sklearn.cross_validation import train_test_split
from sklearn.neighbors import KNeighborsClassifier

iris = load_iris()
X = iris.data
y = iris.target


# 測 5 次 在平衡 
# this is cross_val_score #
from sklearn.cross_validation import cross_val_score
knn = KNeighborsClassifier(n_neighbors=5)
scores = cross_val_score(knn, X, y, cv=5, scoring='accuracy')
print(scores) # 印出5次 百分比 
print(scores.mean()) # 印出 5次平衡 百分比 0.97xx

'''

'''
# 調參

from sklearn.datasets import load_iris
from sklearn.cross_validation import train_test_split
from sklearn.neighbors import KNeighborsClassifier

iris = load_iris()
X = iris.data
y = iris.target


# this is how to use cross_val_score to choose model and configs #
from sklearn.cross_validation import cross_val_score
import matplotlib.pyplot as plt
k_range = range(1, 31)
k_scores = []
for k in k_range:
    knn = KNeighborsClassifier(n_neighbors=k)

# 兩種方法擇一 得到13~18
    scores = cross_val_score(knn, X, y, cv=10, scoring='accuracy') # for classification
    k_scores.append(scores.mean())

##    loss = -cross_val_score(knn, X, y, cv=10, scoring='mean_squared_error') # for regression
##    k_scores.append(loss.mean())

plt.plot(k_range, k_scores)
plt.xlabel('Value of K for KNN')
plt.ylabel('Cross-Validated Accuracy')
plt.show()

'''


# 9 cross validation 交叉驗證
# overfitting  過度擬合 離散 過度糾結 也會造成費時與不準確
# 改變 SVC(gamma=0.01) 可得知
'''
from __future__ import print_function
from sklearn.learning_curve import  learning_curve
from sklearn.datasets import load_digits
from sklearn.svm import SVC
import matplotlib.pyplot as plt
import numpy as np

digits = load_digits()
X = digits.data
y = digits.target

train_sizes, train_loss, test_loss= learning_curve(
        SVC(gamma=0.01), X, y, cv=10, scoring='mean_squared_error',
        train_sizes=[0.1, 0.25, 0.5, 0.75, 1])
train_loss_mean = -np.mean(train_loss, axis=1) # loss 的平衡
test_loss_mean = -np.mean(test_loss, axis=1) # testd 的平衡

plt.plot(train_sizes, train_loss_mean, 'o-', color="r",
             label="Training")
plt.plot(train_sizes, test_loss_mean, 'o-', color="g",
             label="Cross-validation")

plt.xlabel("Training examples")
plt.ylabel("Loss")
plt.legend(loc="best")
plt.show()
'''



# 10 cross validation 交叉驗證
# 改善 overfitting

'''

from __future__ import print_function
from sklearn.learning_curve import  validation_curve
from sklearn.datasets import load_digits
from sklearn.svm import SVC
import matplotlib.pyplot as plt
import numpy as np

digits = load_digits()
X = digits.data
y = digits.target
param_range = np.logspace(-6, -2.3, 5)
train_loss, test_loss = validation_curve(
        SVC(), X, y, param_name='gamma', param_range=param_range, cv=10,
        scoring='mean_squared_error')
train_loss_mean = -np.mean(train_loss, axis=1)
test_loss_mean = -np.mean(test_loss, axis=1)

plt.plot(param_range, train_loss_mean, 'o-', color="r",
             label="Training")
plt.plot(param_range, test_loss_mean, 'o-', color="g",
             label="Cross-validation")

plt.xlabel("gamma")
plt.ylabel("Loss")
plt.legend(loc="best")
plt.show()

# 會花不少時間運算 所以 gamma 值 最好是在 0.005~0.006之間

'''

# 11 保存 model

'''

from __future__ import print_function
from sklearn import svm
from sklearn import datasets

clf = svm.SVC()
iris = datasets.load_iris() # 分類器
X, y = iris.data, iris.target
clf.fit(X, y) # 訓練

# method 1: pickle
import pickle # 保存(存放)數據 
# save
with open('save/clf.pickle', 'wb') as f: # 存成 檔名為 clf.pickle  [write byte]wb
    pickle.dump(clf, f)
'''

'''
from sklearn import svm
from sklearn import datasets

iris = datasets.load_iris() # 分類器
X, y = iris.data, iris.target

# method 1: pickle
import pickle

# restore
with open('save/clf.pickle', 'rb') as f: # rb read byte
   clf2 = pickle.load(f)
   print(clf2.predict(X[0:1])) # 預測是否為 0 類的花
'''


'''
from sklearn import svm
from sklearn import datasets

clf = svm.SVC()
iris = datasets.load_iris() # 分類器
X, y = iris.data, iris.target
clf.fit(X, y) # 訓練

# method 2: joblib
from sklearn.externals import joblib
# Save
joblib.dump(clf, 'save/clf.pkl')
# restore
clf3 = joblib.load('save/clf.pkl')
print(clf3.predict(X[0:1]))
# joblib 會用多近程(process)多線程(thread)

'''





