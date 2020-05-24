PyQt5 基本教學 (1) 安裝 PyQt5，印出 Hello World!  
https://clay-atlas.com/blog/2019/08/26/python-chinese-pyqt5-tutorial-install/  

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
檔案 -> 存檔 -> 檔案名稱 UI.ui
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
        self.ui.Label.setText('Hello World!')

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



