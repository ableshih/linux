
## 基礎知識
```
最好安裝 vim 增強功能
sudo apt install vim
```

# 常用操作
```
:wq
:q!
:w!
:set

yyp
dd
h 左
j 下
k 上
l 右
```

# 三種模式
1. 一般指令模式 (command mode)預設
2. 編輯模式 (insert mode)
3. 指令列命令模式 (command-line mode)



## 一般指令模式 (command mode)預設
```
按鍵盤 del 上下左右
在一般指令模式中可以進行刪除、複製、貼上等等的動作，但是卻無法編輯文件內容的！ 
```

## 編輯模式 (insert mode)
``` JavaScript
var i = 1, y =2;

要等到你按下『i, I, o, O, a, A, r, R』等任何一個字母之後才會進入編輯模式。
注意了！通常在 Linux 中，按下這些按鍵時，在畫面的左下方會出現『 INSERT 或 REPLACE 』的字樣，
此時才可以進行編輯。而如果要回到一般指令模式時， 則必須要按下『Esc』這個按鍵即可退出編輯模式。

不可用鍵盤 上下左右鍵 (大部份鍵盤功能鍵都不可用)
```

## 指令列命令模式 (command-line mode)
```
在一般模式當中，輸入『 : / ? 』三個中的任何一個按鈕，就可以將游標移動到最底下那一列。在這個模式當中， 
可以提供你『搜尋資料』的動作，而讀取、存檔、大量取代字元、離開 vi 、顯示行號等等的動作則是在此模式中達成的！
```




# 解決 左下角狀態列中無法出現 –INSERT- 的字樣
```
test01@linux:~$ vi ~/.vimrc

set showmode (輸入這行 -> esc -> :wq 離開)

test01@linux:~$ vi
```
## 不改設定檔 (每次都要輸入)
```
進 vi 程式

:set showmode (指令列命令模式)
```

## 改設定檔 (本地)
```
test01@linux:~$ sudo vi ~/.vimrc (開啟後內容是空的)
```

## 改設定檔 (全堿)
```
test01@linux:~$ sudo vi /etc/vim/vimrc 
```

## 改設定檔 (出現錯誤)
```
改了沒效 或 出現錯誤 要裝 : vim
sudo apt install vim
```

## 改設定檔 (內容值)
```
"雙引號 (") 是註解
set hlsearch            " 高亮度反白 搜索時，高亮顯示匹配結果。
set backspace=2         " 可隨時用倒退鍵刪除
set autoindent          " 自動縮排
set ruler               " 可顯示最後一列的狀態
set showmode            " 左下角那一列的狀態 要顯示 –INSERT- 的字樣
set nu                  " 開啟在每一列的最前面顯示行號啦！
set nonu                " 關閉在每一列的最前面顯示行號啦！
set number              " 開啟在每一列的最前面顯示行號啦！
set nonumber            " 關閉在每一列的最前面顯示行號啦！
set bg=dark             " 顯示不同的底色色調
syntax enable           " 打開語法高亮 進行語法檢驗，顏色顯示。
syntax on               " 打開語法高亮 進行語法檢驗，顏色顯示。
syntax off              " 關閉語法高亮 進行語法檢驗，顏色顯示。
set mouse=a             " 開啟支持使用滑鼠控制功能
set mouse=              " 關閉vim的滑鼠控制功能
set encoding=utf-8      " 使用 utf-8 編碼
set cursorcolumn        " 顯示游標所在的行(顯示光bar)
set compatible          " 開啟vim的vi相容模式
set nocompatible        " 關閉vim的vi相容模式
set ruler               " 開啟/關閉vim的游標座標顯示 (無效)
set nobackup            " 不備份
set backupext=.bak      " 備份
set writebackup         " 寫備份但關閉vim後自動刪除
set backupdir=path      " 設置備份路徑
set expandtab           "vim的TAB和空格處理 使用以下指令可以開啟vim的TAB擴展功能
set tabstop=4           "vim的TAB和空格處理 使用以下指令可以開啟vim的TAB擴展功能
set softtabstop=4       "vim的TAB和空格處理 使用以下指令可以開啟vim的TAB擴展功能

:colo ron   " 改顏色配置
:colo torte " 改顏色配置

```


## 參考網址
https://kknews.cc/news/agl8n3x.html
https://magiclen.org/vimrc/
http://linux.vbird.org/linux_basic/0310vi.php#vim_set
https://magiclen.org/vimrc/
https://kknews.cc/zh-tw/news/agl8n3x.html

