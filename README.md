# linux


http://tech.ols3.net/techdoc/old/shell/c1082.html  
http://mirror.sars.tw/Bash_Shell_by_ols3/book1.html  
http://wr.ols3.net/
https://blog.techbridge.cc/2019/11/15/linux-shell-script-tutorial  
https://www.facebook.com/groups/266288716757871/  
https://news.sina.com.tw/article/20200330/34703520.html  
南臺科技大學電子系李博明副教授  
https://www.youtube.com/channel/UCcDrreWV8cQ7KEhfZuIEYkA/featured  
https://www.youtube.com/channel/UCcDrreWV8cQ7KEhfZuIEYkA  

https://www.delftstack.com/zh-tw/howto/python-tkinter/  


https://jennaweng0621.pixnet.net/blog/post/404168963  


https://www.tutorialspoint.com/python/tk_button.htm  

https://www.tutorialspoint.com/get-method-for-dictionaries-in-python  

http://kaiching.org/pydoing/py/python-library-tkinter.html  

https://www.delftstack.com/zh-tw/howto/python-tkinter/how-to-close-a-tkinter-window-with-a-button/  


https://raw.githubusercontent.com/ableshih/linux/master/tk.ipynb  


## 顯示圖片
```
# 開圖 按鍵 關視窗 無框
import random, os
from tkinter import *
from PIL import ImageTk ,Image
#from tkinter import ttk


def callback():
    base.destroy() # 關閉 Tkinter 視窗

base = Tk()
base.title('Start Button')
base.state('zoomed') # 視窗最大化

# 隨機顯示圖片
path = r"C:\\Users\\C940\\Sa\\"
random_filename = random.choice([
    x for x in os.listdir(path)
    if os.path.isfile(os.path.join(path, x))
])
print(random_filename)

# 圖片按鈕
img=ImageTk.PhotoImage(Image.open (random_filename))
button1=Button(base, image=img, command=callback)
button1.pack()

base.wm_attributes('-fullscreen','true') # 無框

#app = Application(root)
base.mainloop()
```

## 開視窗
```
# ch8_11.py
from tkinter import *
import random

root = Tk()
root.title("ch8_11")

msgYes, msgNo, msgExit = 1,2,3
def MessageBox():                   # 建立對話方塊
    msgType = random.randint(1,3)   # 隨機數產生對話方塊方式
    if msgType == msgYes:           # 產生Yes字串
        labTxt = 'Yes'
    elif msgType == msgNo:          # 產生No字串
        labTxt = 'No'
    elif msgType == msgExit:        # 產生Exit字串
        labTxt = 'Exit'    
    tl = Toplevel()                 # 建立Toplevel視窗
    tl.geometry("300x180")          # 建立對話方塊大小
    tl.title("Message Box")
    Label(tl,text=labTxt).pack(fill=BOTH,expand=True)

btn = Button(root,text='Click Me',command = MessageBox)
btn.pack()

root.mainloop()
```

https://www.learncodewithmike.com/2020/01/python-inheritance.html  




