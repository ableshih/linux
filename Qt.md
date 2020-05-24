PyQt5 基本教學 (1) 安裝 PyQt5，印出 Hello World!  
https://clay-atlas.com/blog/2019/08/26/python-chinese-pyqt5-tutorial-install/  
#### Anaconda3+pyqt5+Eric6 沒成功 資源少 別試

## 安裝與環境配置
```
Anaconda
python-3.8.3.exe
pip install PyQt5
pip install pyqtwebengine
pip install pyqt5-tools
```

## 啟動 Qt IDE
```
開啟 Anaconda Prompt (Anaconda3) 
輸入 designer # 就會開啟 Qt IDE
```

## Qt IDE New MainWindow
```
新表單 -> Main Window -> 建立
左邊 Display Widgets -> Label (點選 拖拉到 MainWindow)
檔案 -> 存檔 -> 檔案名稱 UI.ui # *.ui 是 xml 格式的檔案
關閉也可不用關
```

## 轉檔
```
開啟 Anaconda Prompt (Anaconda3) 
pyuic5 d:\UI.ui -o d:\UI.py
```

## code
```
from PyQt5 import QtWidgets
from UI import Ui_MainWindow
import sys

class MainWindow(QtWidgets.QMainWindow):
    def __init__(self):
        super(MainWindow, self).__init__()
        self.ui = Ui_MainWindow()
        self.ui.setupUi(self)
        self.ui.Label.setText('Hello World!') # 不管Qt裡打什麼 改這行內容就會變

if __name__ == '__main__':
    app = QtWidgets.QApplication([])
    window = MainWindow()
    window.show()
    sys.exit(app.exec_())
```

## Jupyter notebooks
```
貼上 code

from UI import Ui_MainWindow
UI 就是轉出來的 UI.py (名稱要配對)
```

## UI code
```
# -*- coding: utf-8 -*-

# Form implementation generated from reading ui file 'd:\UI.ui'
#
# Created by: PyQt5 UI code generator 5.13.0
#
# WARNING! All changes made in this file will be lost!


from PyQt5 import QtCore, QtGui, QtWidgets


class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")
        MainWindow.resize(800, 600)
        self.centralwidget = QtWidgets.QWidget(MainWindow)
        self.centralwidget.setObjectName("centralwidget")
        self.Label = QtWidgets.QLabel(self.centralwidget)
        self.Label.setGeometry(QtCore.QRect(140, 320, 191, 111))
        font = QtGui.QFont()
        font.setFamily("Arial Black")
        font.setPointSize(16)
        font.setBold(True)
        font.setWeight(75)
        self.Label.setFont(font)
        self.Label.setObjectName("Label")
        MainWindow.setCentralWidget(self.centralwidget)
        self.menubar = QtWidgets.QMenuBar(MainWindow)
        self.menubar.setGeometry(QtCore.QRect(0, 0, 800, 25))
        self.menubar.setObjectName("menubar")
        MainWindow.setMenuBar(self.menubar)
        self.statusbar = QtWidgets.QStatusBar(MainWindow)
        self.statusbar.setObjectName("statusbar")
        MainWindow.setStatusBar(self.statusbar)

        self.retranslateUi(MainWindow)
        QtCore.QMetaObject.connectSlotsByName(MainWindow)

    def retranslateUi(self, MainWindow):
        _translate = QtCore.QCoreApplication.translate
        MainWindow.setWindowTitle(_translate("MainWindow", "MainWindow"))
        self.Label.setText(_translate("MainWindow", "Hello Word"))

```

利用pyuic5將ui文件轉換為py  
pyuic5 -o destination.py source.ui  
-o是操作參數，表示要生成一個文件  

```

-----------------------
class Ui_MainWindow(object):
    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")


    ui = Ui_MainWindow()
    ui.setupUi(MainWindow)  ### 加在下 ###
    MainWindow.show()
    sys.exit(app.exec_())
-----------------------

-----------------------
在類中添加init方法，其實也是可以的，寫了初始化方法之後，
在初始化方法中執行setupUI（），
實例化之後就不需要再執行setupUI（）方法了

class Ui_MainWindow(object):
    def __init__(self):            ### 加在上
        self.setupUi(MainWindow)   ### 加在上

    def setupUi(self, MainWindow):
        MainWindow.setObjectName("MainWindow")

    ui = Ui_MainWindow()
    MainWindow.show()
    sys.exit(app.exec_())
-----------------------

```

