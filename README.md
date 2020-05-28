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

## python 多子視窗
```
https://www.itread01.com/content/1547112810.html
關於python GUI程式設計(Tkinter) 建立子視窗及在視窗上用圖片繪圖
import tkinter as tk
from PIL import Image, ImageTk 
global attackTime
attackTime=1


    
def show1():
    top1=tk.Toplevel()
    image = Image.open('1.jpg') 
    img = ImageTk.PhotoImage(image)
    canvas1 = tk.Canvas(top1, width = image.width*2 ,height = image.height*2, bg = 'white')
    canvas1.create_image(0,0,image = img,anchor="nw")
    canvas1.create_image(image.width,0,image = img,anchor="nw")
    canvas1.pack()   
    top1.mainloop()


def show2():
    top1=tk.Toplevel()
    image = Image.open('3.jpg') 
    img = ImageTk.PhotoImage(image)
    #canvas = tk.Canvas(top1, width = image.width ,height = image.height, bg = 'white')
    canvas=tk.Button(top1, image=img, command=show1)
    canvas.pack()
    #canvas.create_image(0,0,image = img,anchor="nw")
    #canvas.pack()   
    top1.mainloop()

def callback():
    top1.destroy() # 關閉 Tkinter 視窗
'''
# 圖片按鈕
img=ImageTk.PhotoImage(Image.open (random_filename))
button1=Button(base, image=img, command=callback)
button1.pack()
'''
    
    # base.destroy() # 關閉 Tkinter 視窗


def showMessage():
    top=tk.Toplevel()
    l=tk.Label(top,text='Attacks cost '+str(attackTime)+' s',width=20)
    l.pack()
    top.mainloop()
    
root=tk.Tk()
b1=tk.Button(root,text='start1',command=show1)
b1.pack()
b2=tk.Button(root,text='start2',command=show2)
b2.pack()
root.mainloop()
```

