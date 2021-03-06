
https://medium.com/bucketing/pyside2-pyqt-tutorial-3c2be590bc6a

#
#


C:\Users\V570\AppData\Roaming\Python\Python38\site-packages\PySide2


C:\Users\V570\AppData\Roaming\Python\Python38\Scripts

ui to py
pyside2-uic.exe

GUI
pyside2-designer.exe

https://zhuanlan.zhihu.com/p/75637361
https://doc.qt.io/qtforpython/PySide2/QtGui/index.html
使用pyside-uic 把.ui 文件轉為.py 文件

# 方法一 使用 pyside2-uic: 將 .ui檔案編譯成python原始碼，直接import 並使用

1. 安裝
```
pip install pyside2
```

2. 設計 UI
```
C:\Users\V570\AppData\Roaming\Python\Python38\Scripts\pyside2-designer.exe
```

3. 設計 UI ```存檔```

4. 轉檔
```
C:\Users\V570\Desktop>C:\Users\V570\AppData\Roaming\Python\Python38\Scripts\pyside2-uic mainwindow.ui > ui_mainwindow.py
```

5. 設計 py
```
import sys
from PySide2.QtWidgets import QApplication, QMainWindow
from PySide2.QtCore import QFile
from ui_mainwindow import Ui_MainWindow

class MainWindow(QMainWindow):
    def __init__(self):
        super(MainWindow, self).__init__()
        self.ui = Ui_MainWindow()
        self.ui.setupUi(self)

if __name__ == "__main__":
    app = QApplication(sys.argv)

    window = MainWindow()
    window.show()

    sys.exit(app.exec_())
```

6. 執行 py (顯示結果)
```
p2.py



```
```
NameError: name 'QIODevice' is not defined
from PySide2.QtCore import QIODevice
```
# 方法二 QUILoader 使用QUILoader：將建立好的 .ui 以動態的方式runtime的import到程式中

1. 安裝
```
pip install pyside2
```

2. 設計 UI
```
C:\Users\V570\AppData\Roaming\Python\Python38\Scripts\pyside2-designer.exe
```

3. 設計 UI ```存檔```

4. 設計 py
```
import sys
from PySide2.QtUiTools import QUiLoader
from PySide2.QtWidgets import QApplication
#from PySide2.QtCore import QFile
from PySide2.QtCore import QFile, QIODevice
if __name__ == "__main__":
    app = QApplication(sys.argv)

    ui_file_name = "mainwindow.ui"
    ui_file = QFile(ui_file_name)
    if not ui_file.open(QIODevice.ReadOnly):
        print("Cannot open {}: {}".format(ui_file_name, ui_file.errorString()))
        sys.exit(-1)
    loader = QUiLoader()
    window = loader.load(ui_file)
    ui_file.close()
    if not window:
        print(loader.errorString())
        sys.exit(-1)
    window.show()

    sys.exit(app.exec_())
```

5. 執行 py (顯示結果)
```
pl.py
```


# 方法三 Qt Library 直接畫
```
#!venv/bin/python3
import sys

from PySide2 import QtWidgets
from PySide2.QtWidgets import QLabel
from PySide2.QtWidgets import QMainWindow
from PySide2.QtWidgets import QPushButton


class MainWindow(QMainWindow):
    def __init__(self, parent=None):
        """Main window, holding all user interface including.

        Args:
          parent: parent class of main window
        Returns:
          None
        Raises:
          None
        """
        super(MainWindow, self).__init__(parent)
        self._width = 800
        self._height = 600
        self._title = QLabel('PySide2 is Great', self)
        self._exit_btn = QPushButton('Exit', self)

        self.setMinimumSize(self._width, self._height)

if '__main__' == __name__:
    app = QtWidgets.QApplication(sys.argv)
    w = MainWindow()
    w.show()

    ret = app.exec_()
    sys.exit(ret)
```

# 方法四 Layout

pu.py
```
import sys

from PySide2 import QtWidgets

# from layout.main_window import MainWindow
from MW import MainWindow

if '__main__' == __name__:
    app = QtWidgets.QApplication(sys.argv)
    w = MainWindow()
    w.show()

    ret = app.exec_()
    sys.exit(ret)
```

MW.py
```
from PySide2.QtWidgets import QWidget
from PySide2.QtWidgets import QMainWindow
from PySide2.QtWidgets import QPushButton, QLineEdit
from PySide2.QtWidgets import QVBoxLayout, QHBoxLayout, QGridLayout, QFormLayout


class MainWindow(QMainWindow):
    def __init__(self, parent=None):
        """Main window, holding all user interface including.
        Args:
          parent: parent class of main window
        Returns:
          None
        Raises:
          None
        """
        super(MainWindow, self).__init__(parent)
        self._widget = QWidget()
        self._width = 400
        self._height = 300
        self.setFixedSize(self._width, self._height)

        g_layout = QGridLayout()
        v_layout = self.build_v_layout()
        h_layout = self.build_h_layout()
        f_layout = self.build_f_layout()

        g_layout.addItem(v_layout, 1, 0, 1, 1)
        g_layout.addItem(h_layout, 0, 0, 1, 2)
        g_layout.addItem(f_layout, 1, 1, 1, 1)

        self._widget.setLayout(g_layout)

        self.setCentralWidget(self._widget)

    @staticmethod
    def build_v_layout():
        hello_btn = QPushButton('Hello')
        work_btn = QPushButton('Working')
        play_btn = QPushButton('Playing')
        sleep_btn = QPushButton('Sleeping')

        v_layout = QVBoxLayout()
        v_layout.addWidget(hello_btn)
        v_layout.addWidget(work_btn)
        v_layout.addWidget(play_btn)
        v_layout.addWidget(sleep_btn)

        return v_layout

    @staticmethod
    def build_h_layout():
        hello_btn = QPushButton('Hello')
        work_btn = QPushButton('Working')
        play_btn = QPushButton('Playing')
        sleep_btn = QPushButton('Sleeping')

        h_layout = QHBoxLayout()
        h_layout.addWidget(hello_btn)
        h_layout.addWidget(work_btn)
        h_layout.addWidget(play_btn)
        h_layout.addWidget(sleep_btn)

        return h_layout

    @staticmethod
    def build_f_layout():
        hello_btn = QPushButton('Hello')
        work_btn = QPushButton('Working')
        play_btn = QPushButton('Playing')
        sleep_btn = QPushButton('Sleeping')
        hello_line = QLineEdit()
        work_line = QLineEdit()
        play_line = QLineEdit()
        sleep_line = QLineEdit()

        f_layout = QFormLayout()
        f_layout.addRow(hello_btn, hello_line)
        f_layout.addRow(work_btn, work_line)
        f_layout.addRow(play_btn, play_line)
        f_layout.addRow(sleep_btn, sleep_line)

        return f_layout
```


# 方法五 signal_slot

main.py
```
import sys

from PySide2 import QtWidgets

from main_window import MainWindow
# from signal_slot.main_window import MainWindow

if '__main__' == __name__:
    app = QtWidgets.QApplication(sys.argv)
    w = MainWindow()
    w.show()

    ret = app.exec_()
    sys.exit(ret)
```

main_window.py
```
from PySide2 import QtCore
from PySide2.QtCore import Signal
from PySide2.QtWidgets import QWidget
from PySide2.QtWidgets import QMainWindow
from PySide2.QtWidgets import QPushButton, QLineEdit
from PySide2.QtWidgets import QVBoxLayout, QHBoxLayout, QGridLayout, QFormLayout


class MainWindow(QMainWindow):
    hello_signal = Signal(str)

    def __init__(self, parent=None):
        """Main window, holding all user interface including.
        Args:
          parent: parent class of main window
        Returns:
          None
        Raises:
          None
        """
        super(MainWindow, self).__init__(parent)
        self._widget = QWidget()
        self._width = 400
        self._height = 300
        self.setFixedSize(self._width, self._height)

        g_layout = QGridLayout()
        h_layout = self.build_h_layout()

        g_layout.addItem(h_layout, 0, 0, 1, 1)

        self._widget.setLayout(g_layout)

        self.setCentralWidget(self._widget)
        self.hello_signal.connect(self.say_hello)
        self.hello_signal.emit('Pyside2!')

    def build_h_layout(self):
        hello_btn = QPushButton('Hello')
        work_btn = QPushButton('Working')
        play_btn = QPushButton('Playing')
        sleep_btn = QPushButton('Sleeping')

        h_layout = QHBoxLayout()
        h_layout.addWidget(hello_btn)
        h_layout.addWidget(work_btn)
        h_layout.addWidget(play_btn)
        h_layout.addWidget(sleep_btn)

        sleep_btn.clicked.connect(self.exit)

        return h_layout

    @QtCore.Slot()
    def exit(self):
        self.close()

    @QtCore.Slot(str)
    def say_hello(self, msg):
        print('Hello ' + msg)
```





最簡單的視窗
```
##!venv/bin/python 3

import sys

from PySide2 import QtWidgets

if '__main__' == __name__:
    app = QtWidgets.QApplication(sys.argv)
    w = QtWidgets.QMainWindow()
    w.show()

    ret = app.exec_()
    sys.exit(ret)
```



```
# -*- coding: utf-8 -*-
"""PySide2.ipynb

Automatically generated by Colaboratory.

Original file is located at
    https://colab.research.google.com/drive/13IIcQYA-5Xx_DpQMkgA6Kd7sxkYn0zvJ
"""

#!pip install --index-url=http://download.qt.io/snapshots/ci/pyside/5.11/latest/ pyside2 --trusted-host download.qt.io
# pip install pyside2
# https://github.com/se7enXF/pyside2

# -*- coding: utf-8 -*-#
# File:     helloworld.py
# Author:   se7enXF
# Github:   se7enXF
# Date:     2019/2/19
# Note:     此程序源自Qt官網文檔！使用PySide2顯示窗口，點擊按鈕隨機顯示不同語言的“hello world”

import sys
import random
from PySide2 import QtGui, QtWidgets, QtCore


# 定義主窗口
class MainWindow(QtWidgets.QWidget):
    def __init__(self):
        super().__init__()
        # 設置主窗口大小
        self.resize(400, 300)
        # 設置主窗口標題
        self.setWindowTitle("hello world")

        # 定義不同語言
        self.hello = ["Hallo Welt", "你好世界！", "Hola Mundo", "Привет мир", "Hello world"]

        # 定義按鈕
        self.button = QtWidgets.QPushButton("Click me!")

        # 定義標籤
        self.text = QtWidgets.QLabel("Hello World")
        # 文字居中對齊
        self.text.setAlignment(QtCore.Qt.AlignCenter)

        # 定義佈局，垂直分佈
        self.layout = QtWidgets.QVBoxLayout()

        # 在佈局上添加文字
        self.layout.addWidget(self.text)
        # 在佈局上添加按鈕
        self.layout.addWidget(self.button)
        # 在主窗口上佈置佈局
        self.setLayout(self.layout)

        # 添加槽鏈接
        self.button.clicked.connect(self.magic)

    # 定義槽函數
    def magic(self):
        self.text.setText(random.choice(self.hello))


# 以下是主程序入口，格式基本固定，無須修改
if __name__ == '__main__':
    app = QtWidgets.QApplication(sys.argv)
    window = MainWindow()
    window.show()
    sys.exit(app.exec_())


```


```

PyQt、PySide、PySide2這三者到底有什麼區別？

luoyayun361 2019-08-12 21:13:52  19096  收藏 12
文章標籤： PyQt PySide PySide2 區別
版權
前言
眾所周知，Python語言在這兩年確實很火，作為一種“膠水”語言，似乎它是萬能的，什麼都能做，這依賴於它能夠支持無數的外部庫，這使得Python就變得無比強大。那麼身為Qt的開發者，也自然不會放過Python語言的集成了，畢竟它這麼牛叉，說不定哪天可以用到項目中來呢是吧，那就必須得提前了解一下了。

那麼，面對網上那麼多支持的模塊：PyQt、PySide、PySide2，到底該用哪一個呢？這幾個之間到底有什麼區別？

兩個不同的玩意兒
首先要明確的最重要的一點就是，PyQt和PySide是兩個完全不同的玩意兒，千萬別以為這兩個都是Qt支持Python或者Python支持Qt，他倆是不一樣的，雖然實現的功能都差不多。

PyQt
PyQt要比PySide推出時間早得多，它的開發商是Riverbank Computing，由於推出時間早，PyQt就比較成熟了，並且資料也很完善，最開始是有PyQt4對應的是Qt4版本，後來推出了PyQt5 ，對應Qt5版本，目前最新發布的版本是PyQt v5.13.0。值得注意的是PyQt的採用的是GPLv3許可證和需要購買版權的商業許可證發布的，該許可證允許開發專有應用程序，可以由開發者選擇。GPLv3許可證大概意思就是說，使用PyQt後你的程序就必須要開源，如果閉源商用就會違反協議，後果自負，在國內可能很多公司部注重這個，隨便在用，但是如果公司比較有影響力的話，違反協議說不定哪天收到律師函。

PySide
對比PyQt，PySide就要晚的多問世了，由於先前PySide項目不是很完善，又缺乏文檔，所以其存在感不高。上面我們說到PyQt的開發商是Riverbank Computing，而PySide就不同了，它是Qt的親兒子。

當時Nokia（Nokia那時候收購了Trolltech，所以Nokia是當時Qt的爹）和Riverbank Computing談，希望PyQt能添加對LGPL協議的支持，這對於很多商業用戶會更加友好，畢竟PyQt裡使用的也是我們LGPL協議版本的Qt，但是Riverbank Computing不同意。

Nokia一氣之下決定單幹，於2009年8月發布了支持了LGPL協議的PySide，PyQt的對標產品。

LGPL協議是一個商業友好的協議使用LGPL 協議開發閉源程序，如果你使用動態鏈接的形式，那麼，你可以以任何形式（商業的、非商業的、開源的、非開源的等等）發布你的應用程序。

2011年，Nokia將Qt的商業許可賣給Digia。

2012年，Nokia將Qt完全賣給Digia，後者在2012年年底推出了Qt5。

2015 年10 月14 日PySide 1.2.4 發布，支持Qt 4.8.7 框架。兼容Python2.6 2.7 (採用MSVC2008 構建)，兼容Python3.3 3.4 (採用MSVC2010 構建)。

反觀PyQt，在Qt5推出的半年內（2013年6月）就發布了支持Qt5的pyQt5。

PySide2
PySide對Qt5提供支持的計劃也從2014年開始籌備，也就是2015年上馬的Qt for Python項目，該項目開發的模塊命名為PySide2，以表示與老一代PySide的不同。所以其實PySide2只是PySide的升級版，PySide對標PyQt4，而PySide2對標PyQt5。

總結
總的來說PyQt和PySide2這兩者最大的區別就是協議的不同，來自於不同的開發商，但其實這兩個如果要修改並兼容的話，改動並不是很大，具體的可以參照Qt官方文檔介紹
雖然PyQt發布的早，並且穩定，資料也比較多，而PySide起步比較晚，直到2018年6月正式發布了PySide2的第一個版本，從0到1是最難的一步，後面就容易了，尤其發布的Qt 5.12 LTS釋放了非常積極的信號，PySide2已經日趨完善，又是親生的，還有LGPL開源協議的加持，今後PySide2有足夠的理由成為Python開發者使用Qt的第一選擇。

參考資料：

https://wiki.qt.io/Differences_Between_PySide_and_PyQt_SimplifiedChinese
https://pypi.org/project/PyQt5/
http://forum.digitser.cn/forum.php?mod=viewthread&tid=2021&highlight=PySide1.2.x+和+ PySide2.x
https://www.zhihu.com/question/21237276
https://www.zhihu.com/question/306793447
```
