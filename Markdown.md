
# 流程圖語法叫flow

```flow
st=start:Start 
i=inputoutput:輸入年份n 
cond1=condition:n能否被4整除？ 
cond2=condition:n能否被100整除？ 
cond3=condition:n能否被400整除？ 
o1=inputoutput:輸出非閏年 
o2=inputoutput:輸出非閏年 
o3=inputoutput:輸出閏年 
o4=inputoutput:輸出閏年 
e=end 

st-i-cond1 
cond1(no)-o1-e 
cond1(yes)-cond2 
cond2(no)-o3-e 
cond2(yes)-cond3 
cond3(yes)-o2-e 
cond3(no)-o4-e 




```






```flow 

s=start:開始 
e=end:結束 
o=operation:操作項

s-o-e 

```





# 列表
1. 第一   
2. 第二   
3. 第三   

* 第一   
* 第二   
* 第三   

1. 第一   
    2. 第二   
    3. 第三   
* 第一   
    * 第二   
        * 第三  
```
範例
1. 第一   
2. 第二   
3. 第三   

* 第一   
* 第二   
* 第三   

1. 第一   
    2. 第二   
    3. 第三   
* 第一   
    * 第二   
        * 第三  

說明
使用1. 2. 3.表示有序列表，
使用*或-或+表示無序列表
行頭 前面 按 tab 鍵 或 四個空白 為下一階
```



# 跳轉
[你好](#jump)    
[你好1](#jump1)    
[你好2](#jump2)    


<span id = "jump">hehe</span>


<span id = "jump1">hehe1</span>


<span id = "jump2">hehe2</span>


```
範例
[你好](#jump)    
[你好1](#jump1)    
[你好2](#jump2)    

<span id = "jump">hehe</span>
<span id = "jump1">hehe1</span>
<span id = "jump2">hehe2</span>

說明
使用html代碼實現頁內跳轉
在要跳轉到的位置定義個錨<span id = "jump">hehe</span>
然後使用[你好](#jump)將你好設置為一單擊即跳轉到hehe所在位置的效果

```

# 刪除線
~~AAAAAA~~
```
範例
~~AAAAAA~~

說明
使用~~表示刪除線
```
# 區塊引用
>aaaaaaaa
>>aaaaaaaa
    
>aaaaaaaa    
>>aaaaaaaa
```
範例
>aaaaaaaa
>>aaaaaaaa
    
>aaaaaaaa    
>>aaaaaaaa

說明
在段落的第一行最前面加">"
```




# 註腳
这是一个注脚测试[^footer1]。
[^footer1]: 这是一个测试，用来阐释注脚。


AAAA[^footer1]BBBB    
[^footer1]:CCCC
```
2.3.1 說明
使用[^footer] 表示註腳。

2.3.2 示例
这是一个注脚测试[^footer1]。
[^footer1]: 这是一个测试，用来阐释注脚。
```



# 加粗、列表、代碼區塊
>**AA**    
>*AA    
>*AA




# 待辦事宜Todo 列表
[]aaa    
[x]aaa    
[]aaa    
```
使用帶有[ ] 或[x] （未完成或已完成）項的列表語法撰寫一個待辦事宜列表例如：
```

# 時序圖
```sequence
air->book: c
d book: e
book-->air: h
```

$E = 2^2$

# ttt




```
+ [簡介](#簡介)
    + [改網卡練習](#改網卡練習)
    - [弄壞](#弄壞)
    - [BootMenu](#BootMenu)
        - [mount硬碟](#mount硬碟)
        - [建分身](#建分身)
        - [改密碼](#改密碼)
            * [tar](#tar)
            - [grub](#grub)
            - [更改GRUB背景圖片](#更改GRUB背景圖片)
+ [如何更改grub的紫色背景色](#如何更改grub的紫色背景色)
+ [更改開機樣式](#更改開機樣式)
```

```
* [顯示文字](#標籤名)
    * [4個空白](#或tab鍵)
```






```

  1. [查 IP addr](#IP)
  2. 關閉虛擬機
  3. [設定 VirtualBox](#設定)
  4. 開啟虛擬機
  5. [安裝 ssh server](#ssh)
  6. [Win10 安裝 Putty](#Putty)
  7. 連到 虛擬機
  
  
  
  
* [常用](#常用)
* [三種模式](#三種模式)

+ [呵呵](#三種模式)
    + [嘉嘉](#三種模式)
    * [淢嘻嘻](#常用)
    - [吼吼](#三種模式)
        - [淢三種模式](#三種模式)
        + [桀桀](#三種模式)
        * [桀桀](#三種模式)
            * [不改設定檔](#三種模式)
            - [淢不改設定檔](#三種模式)
            + [桀桀](#三種模式)
+ [常用](#常用)







$$E=mc^2$$



```

# rrr
```



列表
1.7.1 說明
使用1. 2. 3.表示有序列表，使用*或-或+表示無序列表。

1.7.2 示例
例1：有序列表

1. 第一点
2. 第二点
4. 第三点
第一點
第二點
第三點
例2：無序列表

+ 呵呵
    * 嘉嘉
    - 嘻嘻
    - 吼吼
        - 嘎嘎
        + 桀桀
* 哈哈
呵呵
嘉嘉
嘻嘻
吼吼
嘎嘎
桀桀
哈哈


```


























# 換行
abc
ykk

abc    
ykk
```
範例
abc
ykk

abc    
ykk

說明
在最後加四個空白
```

# 粗體和斜體
  **粗体1**    
  __粗体2__
 
  *斜体1*    
  _斜体2_
 
 ***粗斜體1***      
 ___粗斜體2___  
```
範例
  **粗体1**    
  __粗体2__
 
  *斜体1*    
  _斜体2_
 
 ***粗斜體1*** 
 ___粗斜體2___  
 
說明
三個***或者___表示粗斜體
二個**或者__表示粗體
一個*或者_表示斜體
```



# 分割線
---

***

* * *
```
範例
---
***
* * *

說明
使用---或者***或者* * *表示水平分割線效果一樣

注意
* -大於等於三個就可組成一條平行線
使用---時，要在 前後 空一行，防止---被當成標題標
```



# 索引式超連結
[G1][1]    
[G2][2]    
[G3][3]

[1]:https://www.google.com "谷哥" 
[2]:https://www.google.com.tw/imghp "圖片" 
[3]:https://translate.google.com.tw/ "翻譯" 
```
範例
[G1][1]
[G2][2]
[G3][3]

[1]:https://www.google.com "谷哥" 
[2]:https://www.google.com.tw/imghp "圖片" 
[3]:https://translate.google.com.tw/ "翻譯" 
```


# 代碼
```javascript
if (age > 18) {
    status = 'adult';
} else {
    status = 'minor';
}
```

```
說明
加程式語言

範例
```javascript
if (age > 18) {
    status = 'adult';
} else {
    status = 'minor';
}```
```


# 標題
## 標題
### 標題
#### 標題
##### 標題
###### 標題
```
說明
使用 # 表示標題，
一級標題使用一個 #，
二級標題使用兩個 ##，
以此類推，共有 六級 標題。

範例
# 標題
## 標題
### 標題
#### 標題
##### 標題
###### 標題
```

这是高阶标题（效果和一级标题一样 ）
========
这是次阶标题（效果和二级标题一样）
--------------
```
說明
使用=====表示高階標題，
使用---------表示次階標題。

範例
这是高阶标题（效果和一级标题一样 ）
========
这是次阶标题（效果和二级标题一样）
--------------
```

# 超連結
[顯示文字](https://github.com/ableshih "ableshih" )

```
說明
[顯示文字](網址 "氣球文字" )

範例
[顯示](https://github.com/ableshih "ableshih" )
```
# 圖片
![圖](https://d.rimg.com.tw/ahd/230x26_1587957147.jpg "1234567")
```
說明
![如果圖片無法顯示時顯示的文字](圖片網址 "顯示標題")

範例
![圖](https://d.rimg.com.tw/ahd/230x26_1587957147.jpg "1234567")
```
