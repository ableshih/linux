
一個是使用者 ID (User ID ，簡稱 UID)、一個是群組 ID (Group ID ，簡稱 GID)。

UID 0 (系統管理員)

rm：remove 刪除目錄或檔案

參數
rm -r ：recursive遞迴刪除
rm -d ：直接刪除目錄，目錄裡面不能有檔案或是資料夾。
rm -i ：刪除之前會詢問，如果要刪除建議使用這個參數，可以避免誤刪。
rm -f ：強制刪除檔案或目錄，不會有警告，請小心使用。


--------------------------------
開機選單

1. sudo vi /etc/default/grub (修改文件)
2. 找到所要修改的內容，改好存檔
3. sudo update-grub (執行更新配置)
4. init 6 (重啓電腦)

sudo gedit /etc/default/grub
--------------------------------
啓動菜單字體調大
$ sudo gedit /etc/default/grub
GRUB_GFXMODE=1024x768 (文件中找到GRUB_GFXMODE)
$ sudo update-grub (讓配置生效。重啓電腦，OK!)
--------------------------------
開機啟動等待時間
sudo vi /etc/default/grub (修改/etc/default/grub文件)
GRUB_TIMEOUT=5 (文件中找到 GRUB_TIMEOUT
$ sudo update-grub (讓配置生效。重啓電腦，OK!)
--------------------------------
修改默認啟動項和啟動等待時間
sudo vim /etc/default/grub
GRUB_DEFAULT=0 (文件中找到GRUB_DEFAULT 默認)
$ sudo update-grub (讓配置生效。重啓電腦，OK!)
--------------------------------
引導菜單背景圖片和默認啟動項
更改GRUB引導菜單背景圖片
1、首先準備一張想要的照片，文件名是啥無所謂，只要格式是*.jpg *.JPG *.jpeg *.JPEG *.png *.PNG *.tga * .TGA都行，都能自動找到，如果有多個，那麼顯示第一個找到的圖片。
例如名字為命名為：xihuan.jpg 複製到grub目錄/boot/grub/
root@linux:~# cp -v xihuan.jpg /boot/grub/
改變一下啟動界面的分辨率

root @ubuntu:~# vi /etc/default/grub

找到#GRUB_GFXMODE=640x480
更改為GRUB_GFXMODE=1920x1080 #這裡的分辨率改成自己電腦的分辨率
重新生成GRUB的啟動菜單配置文件(/boot/grub/grub.cfg)

root@ubuntu:~# update-grub

通過上面的配置，現在你就可以擁有自己想要的開機界面了。

--------------------------------
自定義開機動畫
sudo apt update
sudo apt install plymouth-themes
自己到org.gnome.themes去下載
將你下載的主題移動到/usr/share/plymouth/themes/下面。
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth 
default.plymouth /usr/share/plymouth/themes/"path/to-your-plymouth.plymouth" 100
行下面命令，應用更新
sudo update-initramfs -u

有人喜歡Mac的風格：
安裝：

$ sudo add-apt-repository ppa:noobslab/themes
$ sudo apt-get update
$ sudo apt-get install mbuntu-bscreen-v3

卸載：

sudo apt-get remove mbuntu-bscreen-v3










===========================================































netstat -e

2:10:45

建帳號

useradd test02

sudo su test02 (換user)
uid 

sh
more


more /etc/shadow
sudo more /etc/shadow (讀取文件的內容) 

不會建目錄


sudo passwd root
修改/home/${USER}/.bashrc 的內容

---------
新增與刪除使用者
在 Linux 底下跟使用者帳號管理相關的指令有：

useradd USERNAME        增加一名為USERNAME的帳號
userdel USERNAME        刪除USERNAME這個帳號
passwd [USERNAME]    更改USERNAME的密碼，若無參數，則改自己的密碼。
finger USERNAME[@HOSTNAME]    查詢使用者資料
chfn [USERNAME]        更動使用者USERNAME的資料，若無參數，則改自己的資料。
-----------
"useradd" 跟 "userdel" 這兩個指令都只有 root 可以使用

(/etc/passwd,/etc/shadow,/etc/group)

userdel -r test02

exit

uid 1001

看 gid

批次檔
用 vi 建十個帳號 (sh)

-r




看 process  卡著

sudo ps -ef，找到該process的pid
然後再下kill pid
sudo kill -9 pid 關






 關掉某特定的process
by sh
------
#!/bin/sh
 
ps $(ps aux | grep 'JavaStart' | awk '{print $2}')
sudo kill $(ps aux | grep 'JavaStart' | awk '{print $2}')
------
https://dotblogs.com.tw/newmonkey48/2012/06/28/73110



sudo killall -9 程式名稱
這樣子應該就可以刪除程序了

查詢 PID：
sudo ps aux | grep firefox

殺掉：
sudo kill -9 [PID 號碼]



昨天執行update-manager要自動更新套件
卻發現update-manager無法進行更新也關閉不掉
最後只好使出殺手鐧kill進行終止該程序
在執行kill之前必須先查出update-manager的處理程序(俗稱PID)
請輸入下列指令:

sudo ps aux | grep update-manager

接下來就會出現類似下面的訊息
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   3084  1560 ?        Ss   Oct05   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Oct05   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Oct05   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Oct05   0:01 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Oct05   0:00 [watchdog/0]
root      5112  0.1  5.5 112464 42976 ?        SNl  Oct10   5:19 /usr/bin/python2.6 /usr/bin/update-manager --no-focus-on-map
root     23441  0.0  0.1   4576   828 pts/0    S+   11:49   0:00 grep update-manager
其中PID為5112就是update-manager的處理程序
接下來執行下列指令來終止update-manager的處理程序

sudo kill 5112
原本關閉不掉的update-manager就會消失不見了








一個 param(佩倫) -> 底下有好幾個 pid

執行 sh
$ ./檔名
(要測試不加 .sh會怎麼?)

刪十個帳號的 sh


etc/passwd
etc/shawod

3:01:40
手動建 user 目錄 gid passwd shawod
改 uid怎0麼改

目地是 gid (把現有的user 改成同一個 gid)

午休
















04:17:40
uid 1001
gid 1001

建帳號 是看編號 不是看輸入的名稱

下午三個東西

遠端     防火牆

80 443

port 22, port 23


FileZilla client 
putty



ufw
要開 其他關

全開
沒禁都可有禁不行

全關
只開要的

一般防火牆只封 port 
貴的會看行為

04:48:02

開 vm
開瀏覽器
開 g driver
下載 
chmod
壓開


cd ~/Downloads

netstat -a ssh 0.0.0.0 誰都可以

ssh test01@localhost
netstat -a ssh 自己連自已 1000 server cline
低於 1000 是 server
high port 


nat 10.0.52. 單向
192.168.56.16
轉

putty.exe -load my_server -l your_user_name -pw your_password
putty.exe mylogin@somewhere.com -pw mypassword
putty.exe somewhere.com -l mylogin -pw mypassword
putty.exe -ssh root@somewhere.com -pw mypasswordforsomewherecom


找尋被占用的port
netstat -nab
-b參數會顯示出占用的process，但如果加上findstr :port去過濾，會因跳行的關係無法看到兇手是誰。
因此有另外一個方法是透過-o加tasklist指令:
netstat -nao | findstr :80
看到pid後，再使用tasklist找process名稱:
tasklist | findstr 5932



cat /etc/services | grep 834

tcp   0    0 0.0.0.0:834    0.0.0.0:*   LISTEN   653/ypbind







若要即時監控使用中的連線資訊，可以使用 watch ：
watch -d -n0 "netstat -atnp | grep ESTA"

列出完整的 URL 位址
netstat -tup -W

這個指令可以將所有連線的 IP 位址列出來，並依照每個 IP 位址的連線數排序
netstat -an | grep ESTABLISHED | awk '/^tcp/ {print $5}' | awk -F: '{print $1}' | sort | uniq -c | sort -nr

用 awk 分析連線
這個指令可以分析 Apache 的連線，列出每個 IP 位址的連線數
sudo netstat -anpt | grep http | grep ESTABLISHED | awk -F "[ :]*" '{print $4}' | uniq -c

這個指令可以將所有連線的 IP 位址列出來，並依照每個 IP 位址的連線數排序
netstat -an | grep ESTABLISHED | awk '/^tcp/ {print $5}' | awk -F: '{print $1}' | sort | uniq -c | sort -nr

這個指令可以驗證 MySQL 是否是透過 UNIX domain socket 連線
netstat -lx | grep -i sql

列出連線的協定及使用的應用程式
netstat -alp 

秀出目前已經啟動的網路服務
netstat -tulnp

觀察本機上頭所有的網路連線狀態
netstat -atunp


stat：狀態列，主要的狀態含有：

    ESTABLISED：已建立連線的狀態；
    SYN_SENT：發出主動連線 (SYN 標誌) 的連線封包；
    SYN_RECV：接收到一個要求連線的主動連線封包；
    FIN_WAIT1：該插槽服務(socket)已中斷，該連線正在斷線當中；
    FIN_WAIT2：該連線已掛斷，但正在等待對方主機回應斷線確認的封包；
    TIME_WAIT：該連線已掛斷，但 socket 還在網路上等待結束；
    LISTEN：通常用在服務的監聽 port ！可使用『 -l 』參數查閱


















































===========================================


xclock (獨佔執行)
xclock & (背景執行)

一行多指令
ls; ps; ls -la;

一行多指令 前面有錯，後面就不會作
ls && ps

一行多指令 前面對，後面就不作 前面錯，才會作後面
ls || ps

看路徑
echo $PATH

編譯1
1. sudo apt install gcc
2. new 123.c file
3. gcc 123.c
4. ls -la (多了一個 a.out)
5. ./a.out

123.c
#include <stdio.h>
int main()
{
	printf("hello ?\n");
}

別名 alias
alias (會顯示目前所設定的)

ailas kk='more 123.c' (增加)

kk (執行)

編譯2 (一般編譯會固定產生 a.out 用 -o 就可以改)
gcc 123.c -o kkk 
./kkk -rwxr-xr-x




終止
ctrl + c

ps -ef (找到 PID)
kill -1 PID的編號
kill -9 PID的編號

-1 終端掛斷
-2 ctrl+c
-9 強迫終止
-15 終止應用程式

<EOT>
End Of File
ctrl + d


clear
ctrl+l 同 clear
ctrl+u (清一行)
ctrl+e (移到行最後)

ctrl+p (執行過 上一個指令)
ctrl+n (執行過 下一個指令)

history | grep ls (grep 搜尋關鍵字)


輸入ls再按兩次tab鍵，會列出 字頭為ls*




chmod
chmod 644 a.out -rw-r--r--
(u = 當下 user)
chmod u+x a.out -rwxr--r--
chmod u-x a.out -rw-r--r--
(a = all user)
chmod a+x a.out -rwxr--r--
chmod a-x a.out -rw-r--r--




網路下載 c 原始碼
*.tar (找個目錄解開)
./configure
make
make install


Shell Script
./123.out
bash 123.sh
. 123.sh
source 123.sh


導向
cat >filename (不用 vi 編檔 filename)
more filename (顯示)
cat filename (顯示)
cat >no2 <no1 (把 no1 給 no2)



cal -d 2020-05

date +'%c' (現在時間)

date -d '1969/11/5' +'%A' (星期幾)

TZ=Taiwan date


who

whoami

sudo whoami

uname -msr (查看作業系統版本)

display

xrandr -s 800x600

xcalc (小算盤)


===========================================




Linux 使用 ffmpeg 將影片 90度、180度旋轉

發佈日期: 2019 年 02 月 18 日，作者: Tsung

Linux 想要將影片(Mp4、Mov...)做 90度、180度的旋轉，要怎麼做呢？


Linux 使用 ffmpeg 將影片 90度、180度旋轉
拍攝影片後，要將直的影片轉成橫的，就要 90度 或 270度的旋轉，可以使用 ffmpeg
來達成。

$ ffmpeg -i INPUT.mov -vf "transpose=1" OUTPUT.mov

transpose 參數
0 = 90 CounterCLockwise and Vertical Flip (default)
1 = 90 Clockwise 順時針轉90度
2 = 90 CounterClockwise 逆時鐘轉90度
3 = 90 Clockwise and Vertical Flip


---------------------------------------------

boxes：在 Linux CLI 自動繪製文字方塊
發佈日期: 2019 年 02 月 25 日，作者: Tsung

在 Linux 的 CLI (命令列) 想要輸入文字，自動產生程式碼上面的註解，甚至產生各種圖案的畫面，可以使用 boxes 來達成。


boxes：在 Linux CLI 自動繪製文字方塊

Debian、Ubuntu Linux 安裝 boxes

apt install boxes

boxes 主要資源

官網：boxes - Command line ASCII boxes unlimited!
http://boxes.thomasjensen.com/

GitHub：GitHub - ascii-boxes/boxes: Command line ASCII boxes unlimited!
https://github.com/ascii-boxes/boxes

boxes 的操作與使用

echo "hello world" | boxes # 預設會產出註解的框框(若輸入中文，長度判斷會有點錯誤)
echo "hello world" | boxes -d diamonds -a hcvc # -a format option can be used to position、「hcvc」 stands for "horizontally centered, vertically centered".
echo "hello world" | boxes -d dog -a c

還有更多可參考範例：boxes - Examples http://boxes.thomasjensen.com/examples.html

---------------------------------------------

Linux 使用 pstree 查看程序下面的所有子程序

發佈日期: 2019 年 03 月 05 日，作者: Tsung

Linux 可以使用 pstree 畫出所有程序下面的所有子程序，但是想要依照使用者另外分別查看所有程序，可以怎麼做呢？


Linux 使用 pstree 查看程序下面的所有子程序

pstree 幾個使用方式

pstree -u username # 查看 username 所有程序與子程序
pstree -aplu -u username # 可以查看 username 有沒有哪些子程序是沒有爸爸的


---------------------------------------------

Linux 如何於 Crontab 執行 Python Virtualenv 環境

發佈日期: 2019 年 03 月 29 日，作者: Tsung

Python 都會使用 virtualenv 來開發，Deploy 當然也希望可以建造一個乾淨的 virtualenv 的環境來搬移。

不過 Python 的 venv 執行的參數作法如下：

1. cd venv
2. . venv/bin/activate # 進入環境，問題出在這個階段，進不去
3. pip install -r requirements.txt # 安裝所需套件

Linux 如何於 Crontab 執行 Python Virtualenv 環境

於「. venv/bin/activate」進不去，所以研究看看 activate code 是寫什麼，結果只是簡單的 shell script，所以只要將 "." 改成 "source" 就可以執行囉~

不過於 crontab 寫法還是要稍微注意 PATH 的問題，crontab 寫法參考：

View Raw Code?

SHELL=/bin/bash

/10 * * * * source /project/venv/bin/activate && /project/bin/exec.py args

https://blog.longwin.com.tw/2019/03/linux-crontab-python-virtualenv-env-2019/#


相關網頁

python - Cron and virtualenv https://stackoverflow.com/questions/3287038/cron-and-virtualenv



---------------------------------------------

Linux 使用 parallel 來同時平行多工處理

發佈日期: 2019 年 04 月 08 日，作者: Tsung

Linux 於 Shell 不想寫程式，又想要程式可以平行處理，可以使用 parallel 來處理。


Linux 使用 parallel 來同時平行多工處理

Parallel 的程式簡介

parallel - build and execute command lines from standard input in parallel

parallel 安裝步驟

sudo apt install parallel

parallel 的功能非常多，建議先 man parallel 來查看，下面只有先列列範例參考看看：

	seq -w 0 100 | parallel -j 8 touch {}.txt
	seq -w 0 9999 | parallel -j 8 rm pict{}.jpg
	find . -name '.jpg' | parallel convert -geometry 120 {} {}_thumb.jpg
	find . -type d -name ".svn" -print | parallel rm -rf # 取代 xargs, find . -type d -name ".svn" -print | xargs rm -rf
	cat file.txt | parallel -j 8 --pipe -L 50000 import_script
		-j 8：並行 jobs 的數量，不想並行執行可以設為 1。若不加 -j，則預設為每個 CPU 執行一個 job
		--pipe：從 stdin 讀取, 再將 stdin 的資料分給各個jobs
		-L N: 一次最多讀取N行

使用 parallel 同時傳送命令到各台機器

	echo "command" | parallel --onall --slf servers.txt
		ex: echo "ls" | parallel --onall --slf servers.txt # servers.txt (w1.example.com, w2.example.com.. 一行一個 domain name)
	echo "grep QueryKeyword /var/log/apache2/access.log" | parallel –onall –slf servers.txt

使用 xargs 來平行處理(感謝 CHUNG TSAI)

	$ cat filename | xargs -P 8 touch # filename 內容是一行一行的東西，這個會 touch 出 filename 一行一行當檔名

相關網頁
GNU Parallel tutorial https://www.gnu.org/software/parallel/parallel_tutorial.html
GNU Parallel: 並行執行 Linux 命令 http://blog.csdn.net/xzz_hust/article/details/39183837
How To Use Your Entire CPU In Bash With Parallel https://bash-prompt.net/guides/parallell-bash/
Distributed Log Search Using GNU Parallel http://blog.codehate.com/post/134320079974/distributed-log-search-using-gnu-parallel
15分鐘神器 gnu parallel 入門觀 https://www.jianshu.com/p/c5a2369fa613
GNU Parallel videos - YouTube 教學影片 http://www.youtube.com/playlist?list=PL284C9FF2488BC6D1


---------------------------------------------

Linux 螢幕截圖、錄影、標記用工具

發佈日期: 2019 年 04 月 15 日，作者: Tsung

發現 Bug、重現流程等等，常常會需要截圖、錄影和簡單的劃線標記，在 Linux 有哪些軟體程式可以使用呢？


Linux 螢幕截圖、錄影、標記用工具

Ubuntu、Debian Linux 使用 Gnome 的 Xwindow，想要做螢幕截圖、圖片標示、錄影 等等，如下述整理：

截圖

	gnome-screenshot (Gnome 內建)
	shutter - feature-rich screenshot program
	flameshot - Powerful yet simple-to-use screenshot software https://github.com/lupoDharkael/flameshot

小畫家

	kolourpaint - simple image editor and drawing application http://kolourpaint.sourceforge.net/

錄影

	kazam - screencast and screenshot application created with design in mind

錄影 要錄比較長的影片

	下述兩套一起安裝
	recordmydesktop - Captures audio-video data of a Linux desktop session
	gtk-recordmydesktop - Graphical frontend for recordMyDesktop screencast tool

相關網頁
FFmpeg Screen Recorder─在Linux作業系統上進行螢幕錄影、錄音或網路直播 - 想要錄影並直播可參考此篇
https://magiclen.org/ffmpeg-screen-recorder/
Record Screen in Ubuntu Linux With Kazam
https://itsfoss.com/kazam-screen-recorder/
史上最全的使用 gnome-screenshot 截圖指南
https://kknews.cc/zh-tw/car/enrqm2r.html


---------------------------------------------

vim-php-manual：Vim 使用 Shift-k 秀出 PHP Manual 的 Plugin

發佈日期: 2019 年 04 月 18 日，作者: Tsung

使用 Vim 撰寫 PHP 的程式時，知道 Function 名稱，但是不曉得參數的順序，或者想要速查看 PHP 的文件，可以使用此外掛。


vim-php-manual：Vim 使用 Shift-k 秀出 PHP Manual 的 Plugin

在 Vim 裡面，安裝此外掛後，只要游標於 Function name 上面，按下大寫 K (Shift-k)，就可以直接秀出 PHP Manual (文件)。

	alvan/vim-php-manual: PHP Manual for Vim https://github.com/alvan/vim-php-manual

註：此套件會抓取是 PHP 檔案才啟用此外掛，平常 K 若指定到字典，不會有影響。


---------------------------------------------
Linux 使用 OpenSSL 對檔案做加解密

發佈日期: 2019 年 04 月 22 日，作者: Tsung

於 Linux 想要對檔案做加解密可以使用 OpenSSL 來達成。


Linux 使用 OpenSSL 對檔案做加解密

加密

	$ openssl aes-256-cbc -a -in filename -out filename.enc

解密

	$ openssl aes-256-cbc -d -a -in filename.enc -out filename

註：openssl help 可以查看 enc 還有哪些加解密演算法可以使用


---------------------------------------------

Flameshot：Linux 截圖(螢幕抓圖)與直接編輯的軟體

發佈日期: 2019 年 04 月 24 日，作者: Tsung

Ubuntu、Debian Linux 於 Xwindow 想要抓圖、截圖，然後直接在上面畫要注意哪些地方，可以使用 Flameshot。


Flameshot：Linux 截圖與直接編輯的軟體

以往都是使用截圖，然後在打開 gimp 或小畫家之類得來編輯，Flameshot 可以直接截圖順便編輯，非常方便~

	官網：lupoDharkael/flameshot: Powerful yet simple to use screenshot software https://github.com/lupoDharkael/flameshot
	安裝：apt install flameshot

Flameshot 操作影片

Flameshot 操作動畫
Flameshot 操作動畫

Flameshot 還有很多 CLI 的參數可以使用，可以參考此篇：
lupoDharkael/flameshot:Getting start https://flameshot.js.org/#/getting-start

---------------------------------------------
Linux grep 列出抓到內容的前後幾行內容

發佈日期: 2019 年 05 月 03 日，作者: Tsung

Linux 使用 grep 找資料很方便，再找程式碼的時候，除了找到的那一行外，特別需要在那行的前後幾行都列出來，要怎麼做呢？


Linux grep 列出抓到內容的前後幾行內容

grep 有 A、B、C 的參數可以使用，下述的 num 請自行帶入需要的數字

	-A 5：grep 到此行外，在多印出往下的5行
	-B 5：grep 到此行外，在多印出往上的5行
	-C 5：grep 到此行外，在多印出往上、往下的各5行
範例

	grep $Keyword filename -C 5 # 列出前後5行
	grep $Keyword filename -B 5 # 列出前5行

註：不想記太多的話，就一律用 -C 吧~



---------------------------------------------

Linux 使用 pgrep 找出 Processes 所有 pid

發佈日期: 2019 年 05 月 06 日，作者: Tsung

平常要找某 Process (Ex: Apache) 的 Pid，都是 ps aux | grep apache 然後在搭配 awk 來把 pid 撈出來。

上述方式撈出來的這些 pid 常常會有一個是 ps 的 pid，而且撈的方式還蠻辛苦的~ 使用 pgrep 可以比較輕鬆解決~


Linux 使用 pgrep 找出 Processes 所有 pid

Debian、Ubuntu Linux 安裝 pgrep 方式：

	apt install procps

pgrep 的操作使用上非常簡單，如下範例：

	pgrep apache2 # 列出 Apache2 的所有 pid
	pgrep -u root sshd # 找出 root user + sshd daemon
	renice +4 $(pgrep firefox)

註：pkill 也是類似用法

---------------------------------------------
讓 Linux 的 ls 速度加快一倍

發佈日期: 2019 年 05 月 20 日，作者: Tsung

Linux ls 是列出系統內的檔案用的，平常使用沒什麼感覺，但是若檔案、目錄特別多的情況，速度就會慢到爆炸，慢的主要原因是什麼呢？


讓 Linux 的 ls 速度加快一倍

由文章與實作發現，原來 ls 會慢的主因是在於要秀出顏色(LS_COLORS)，因為要秀出顏色，檔案有幾個，就要跑幾次的 lstat，若將這些關掉，就可以快上一倍的速度。

註1：下述原文的內容是會快 40倍，主要差異在使用 strace，我在 Linux 只有 lstat 會跑比較多次，其它的在 Linux 沒有看到，實測速度是快一倍

註2：ls 的顏色設定可參考下述幾篇：
	ls 顏色設定(in Bash shell) https://blog.longwin.com.tw/2006/07/color_ls_in_bash_2006/
	dircolors(1) - Linux manual page http://man7.org/linux/man-pages/man1/dircolors.1.html
	dir_colors(5) - Linux manual page http://man7.org/linux/man-pages/man5/dir_colors.5.html
	Configuring LS_COLORS http://www.bigsoft.co.uk/blog/2008/04/11/configuring-ls_colors

下述內容整理自此篇文章：When setting an environment variable gives you a 40x speedup https://news.sherlock.stanford.edu/posts/when-setting-an-environment-variable-gives-you-a-40-x-speedup

1. mkdir /tmp/dont
2. touch /tmp/dont/{1..10000} # 產生 10000 個檔案
3. time ls --color=always /tmp/dont | wc -l
	10000
	real 0m0.051s
	user 0m0.028s
	sys 0m0.016s
4. strace -c ls --color=always /tmp/dont | wc -l

10000
% time seconds usecs/call calls errors syscall
------ ----------- ----------- --------- --------- ----------------
100.00 0.000184 0 10000 lstat
0.00 0.000000 0 7 read
0.00 0.000000 0 34 write
0.00 0.000000 0 9 open
0.00 0.000000 0 11 close
0.00 0.000000 0 1 stat
0.00 0.000000 0 10 fstat
0.00 0.000000 0 19 mmap
0.00 0.000000 0 12 mprotect
0.00 0.000000 0 1 munmap
0.00 0.000000 0 6 brk
0.00 0.000000 0 2 rt_sigaction
0.00 0.000000 0 1 rt_sigprocmask
0.00 0.000000 0 3 3 ioctl
0.00 0.000000 0 8 8 access
0.00 0.000000 0 3 mremap
0.00 0.000000 0 1 execve
0.00 0.000000 0 9 getdents
0.00 0.000000 0 1 getrlimit
0.00 0.000000 0 2 2 statfs
0.00 0.000000 0 1 arch_prctl
0.00 0.000000 0 1 set_tid_address
0.00 0.000000 0 1 set_robust_list
------ ----------- ----------- --------- --------- ----------------
100.00 0.000184 10143 13 total

5. unset LS_COLORS # 測試將 LC_COLORS 拿掉
6. time ls --color=always dont | wc -l # 速度一樣差不多
	10000
	real 0m0.043s
	user 0m0.016s
	sys 0m0.020s
7. 文章作者發現是下面幾個參數造成的
	EXEC 00
	SETUID 00
	SETGID 00
	CAPABILITY 00
8. export LS_COLORS='ex=00:su=00:sg=00:ca=00:' # 所以將這幾個參數拿掉，lstat 就不會執行
9. time strace -c ls --color=always /tmp/dont | wc -l # 速度快一倍
	10000
	% time seconds usecs/call calls errors syscall
------ ----------- ----------- --------- --------- ----------------
0.00 0.000000 0 7 read
0.00 0.000000 0 12 write
0.00 0.000000 0 9 open
0.00 0.000000 0 11 close
0.00 0.000000 0 1 stat
0.00 0.000000 0 10 fstat
0.00 0.000000 0 19 mmap
0.00 0.000000 0 12 mprotect
0.00 0.000000 0 1 munmap
0.00 0.000000 0 6 brk
0.00 0.000000 0 2 rt_sigaction
0.00 0.000000 0 1 rt_sigprocmask
0.00 0.000000 0 2 2 ioctl
0.00 0.000000 0 8 8 access
0.00 0.000000 0 3 mremap
0.00 0.000000 0 1 execve
0.00 0.000000 0 9 getdents
0.00 0.000000 0 1 getrlimit
0.00 0.000000 0 2 2 statfs
0.00 0.000000 0 1 arch_prctl
0.00 0.000000 0 1 set_tid_address
0.00 0.000000 0 1 set_robust_list
------ ----------- ----------- --------- --------- ----------------
100.00 0.000000 120 12 total
real 0m0.031s
user 0m0.020s
sys 0m0.008s

於是我原本 LC_COLORS 的設定

	declare -x LS_COLORS="no=00:fi=00:di=01;36:ln=02;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:"

要將 LS_COLORS='ex=00:su=00:sg=00:ca=00:' 加入，裡面只有 ex 是不同的，所以將 ex 改 00，在加入其餘的值，如下：

	declare -x LS_COLORS="no=00:fi=00:di=01;36:ln=02;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:ex=00:su=00:sg=00:ca=00:"

速度就能提昇一倍囉~

不過執行檔的顏色就無法顯示出來，所以這個設定可以另外寫成 Shell function 來處理，特別對多檔案的時候用的 ls

function mls() {
    export LS_COLORS="no=00:fi=00:di=01;36:ln=02;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35:ex=00:su=00:sg=00:ca=00:"
    ls "$@"
}

速度測試比較

	time ls --color dont/ | wc -l
		10000
		real 0m0.067s
		user 0m0.040s
		sys 0m0.020s
	time mls --color dont/ | wc -l
		10000
		real 0m0.030s
		user 0m0.020s
		sys 0m0.004s
		Share this:

---------------------------------------------

Linux APT 遇到 NO_PUBKEY 的 GPG error 解法

發佈日期: 2019 年 05 月 23 日，作者: Tsung

Debian / Ubuntu Linux 若使用外部套件(Apt sources.list 有額外增加)，apt update 常常會遇到下述訊息：

	由於無法取得它們的公鑰，以下簽章無法進行驗證： NO_PUBKEY 9334A25F8507EFA5

或

	The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9334A25F8507EFA5

	W: GPG error: http://repo.percona.com/apt stretch InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9334A25F8507EFA5

要怎麼解決呢？


Linux APT 遇到 NO_PUBKEY 的 GPG error 解法

NO_PUBKEY 的解法已經寫過很多篇：

	GPG Error for apt-get https://blog.longwin.com.tw/2006/02/gpg_error_for_aptget/
	Debian /Ubuntu Linux GPG Key 匯入 https://blog.longwin.com.tw/2009/07/debian-ubuntu-linux-gpg-key-import-2009/

現在步驟都很簡化了，所以乾脆再來整理一個簡單快速的版本：

遇到 NO_PUBKEY 9334A25F8507EFA5 的解法

解法

	sudo apt-key adv --keyserver keys.gnupg.net --recv-keys <PUBKEY>
	或
	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <PUBKEY>
	註：解法有很多種，在這邊只紀錄最簡單一行的版本

方法1 (範例)

	sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 8507EFA5
	或
	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8507EFA5

方法2 (兩行版)

1. gpg --keyserver keys.gnupg.net --recv-key 9334A25F8507EFA5
2. gpg -a --export 9334A25F8507EFA5 | sudo apt-key add -

PUBKey 加入後，再來執行 apt update 就不會有此訊息囉~


---------------------------------------------

Linux 使用 pmap 查看 Process 的記憶體映照

發佈日期: 2019 年 05 月 27 日，作者: Tsung

Linux 的 Process 都有對應的 PID，而此 PID 到底使用多少記憶體？使用到哪些函式庫呢？


Linux 使用 pmap 查看 Process 的記憶體映照

於 Debian、Ubuntu Linux 安裝 pmap：

	apt install procps
		pmap - report memory map of a process

pmap 可以查看此 PID 使用哪些記憶體、相關函式庫 等等的資訊，詳細的印出來~

pmap 操作指令

	pmap pid # 可以看到此 pid 使用哪些 Memory、Library
	sudo pmap pid # 搭配 sudo 才能看到詳細
	sudo pmap -X pid
	sudo pmap -XX pid

pmap 範例

	sudo pmap `pgrep sshd`
	sudo pmap $(pgrep sshd)

000055a78b44c000    756K r-x-- sshd
000055a78b709000     12K r---- sshd
000055a78b70c000      4K rw--- sshd
000055a78b70d000     36K rw---   [ anon ]
000055a78c939000    132K rw---   [ anon ]
00007f1679cab000     40K r-x-- libnss_files-2.24.so
00007f1679cb5000   2048K ----- libnss_files-2.24.so
00007f1679eb5000      4K r---- libnss_files-2.24.so
00007f1679eb6000      4K rw--- libnss_files-2.24.so
Share this:

---------------------------------------------
Linux 判斷系統硬碟是 SSD 還是傳統硬碟

發佈日期: 2019 年 06 月 03 日，作者: Tsung

於 Linux 要查看現在機器使用的硬碟是不是 SSD，要怎麼查呢？

一般就是使用下述查到硬體型號後，再去查詢型號是不是 SSD。

	$ cat /proc/scsi/scsi # 直接用下述型號去找資料
		Model: SAMSUNG MZ7LF192

是否有更直接的方式可以查到呢？


Linux 判斷系統硬碟是 SSD 還是傳統硬碟

可以利用 SSD 不會 rotate 的特性來查詢，有下述幾種方法：

查 sys 的 rotational

	$ cat /sys/block/sda/queue/rotational
		0 就是 SSD
		1 就是 HDD

使用 lsblk
	$ lsblk -d -o name,rota
		NAME ROTA
		sda 0
			0 就是 SSD
			1 就是 HDD

使用 smartctl

	$ sudo smartctl -a /dev/sda # 找到下述則是 SSD
		Rotation Rate: Solid State Device

Share this:
---------------------------------------------
Shell script 依照空格分隔 每行一個字

發佈日期: 2019 年 06 月 04 日，作者: Tsung

Shell script 可以使用 tr / sed 來完成~ 如果還要某個特定欄位來做，可以在搭配 cut 或 awk~


Shell script 依照空格分隔 每行一個字

範例文件

	vim example.txt
		a b c d e f g h

依照空格分隔，每行一個字詞

	cat example.txt | tr ' ' '\n'
	cat example.txt | sed 's/ /\n/g'

若中間有 \t 之類分隔，可以搭配 cut

若要將第三欄位的值取出，裡面的值依照空格分隔，每行一個字詞

	cat example.txt | cut -f3 | tr ' ' '\n'

Share this:



---------------------------------------------
微秒(ms)、奈秒(ns) 等的時間單位

發佈日期: 2019 年 06 月 28 日，作者: Tsung

小於1秒的時間單位，有哪些呢？


微秒(ms)、奈秒(ns) 等的時間單位

下述摘錄自此篇：數量級 (時間)

普朗克時間：約 10-44 秒
攸秒（ys）：10-24 秒
介秒（zs）：10-21 秒
阿秒（as）：10-18 秒
飛秒（fs）：10-15 秒
皮秒（ps）：10-12 秒
奈秒（ns）：10-9 秒
微秒（µs）：10-6 秒
毫秒（ms）：10-3 秒


---------------------------------------------
Linux 使用 dot 將文字檔 轉換成 圖片

發佈日期: 2019 年 07 月 08 日，作者: Tsung

想要畫關聯性的圖片，線很多要在圖片排版很辛苦，使用 dot 只要把每個元件的關係設定好，就可以自動產生 svg、png .. 等等的圖形。


Linux 使用 dot 將文字檔 轉換成 圖片

於 Debian、Ubuntu Linux 要使用 dot，需要安裝下述：

	apt install graphviz

Graphviz 與 dot 的文件

	官網：Graphviz - Graph Visualization Software https://graphviz.gitlab.io/
	文件：Dot Guide https://graphviz.gitlab.io/_pages/pdf/dotguide.pdf

dot 文件範例

1. vim g.gv

digraph G {
    main -> parse -> execute;
    main -> init;
    main -> cleanup;
    execute -> make_string;
    execute -> printf
    init -> make_string;
    main -> printf;
    execute -> compare;
}

2. dot -Tps g.gv -o graph.ps # 轉成 ps 檔
3. dot -Tsvg g.gv -o graph.svg # 轉成 svg 檔
4. dot -Tpng g.gv -o graph.png # 轉成 png 檔
5. 註：上面範例簡化版

digraph G {
    main -> parse -> execute;
    main -> init;
    main -> cleanup;
    main -> printf;
}

其他範例

digraph G {
    graph [layout=dot rankdir=LR]
    vim [href="http://www.vim.org/"]
    dot [href="http://www.graphviz.org/"]
    vimdot [href="file:///usr/bin/vimdot"]
    {vim dot} -> vimdot
}
Share this:

---------------------------------------------

Debian Linux 10 Buster 穩定版釋出

發佈日期: 2019 年 07 月 11 日，作者: Tsung

Debian Linux 10 Buster 於 2019/7/6 stable 版本釋出，歷經 25個月的開發，將提供5年的 Long Term Support。 https://wiki.debian.org/LTS


Debian Linux 10 Buster 穩定版釋出

Debian Linux Buster 官方新聞可見：

	Debian -- News -- Debian 10 "buster" released https://www.debian.org/News/2019/20190706

升級注意事項的文件

	Debian 10 (buster), 64-bit PC 的發行說明 https://www.debian.org/releases/buster/amd64/release-notes/
	Debian GNU/Linux 安裝手冊 https://www.debian.org/releases/buster/amd64/

Debian 10 的主要變動

	預設使用 Wayland
	預設啟用 AppArmor
	APT (except cdrom, gpgv, and rsh) 可以選擇啟動 seccomp-bpf Sanbox
	預設使用 nftables 取代 iptables https://wiki.debian.org/nftables
	支援 UEFI Secure Boot

Xwindow 版本

	Cinnamon 3.8
	GNOME 3.30
	KDE Plasma 5.14
	LXDE 0.99.2
	LXQt 0.14
	MATE 1.20
	Xfce 4.12

常用套件版本

Apache 2.4.38
BIND DNS Server 9.11
Chromium 73.0
Emacs 26.1
Firefox 60.7 (in the firefox-esr package)
GIMP 2.10.8
GNU Compiler Collection 7.4 and 8.3
GnuPG 2.2
Golang 1.11
Inkscape 0.92.4
LibreOffice 6.1
Linux 4.19 series
MariaDB 10.3
OpenJDK 11
Perl 5.28
PHP 7.3
PostgreSQL 11
Python 3 3.7.2
Ruby 2.5.1
Rustc 1.34
Samba 4.9
systemd 241
Thunderbird 60.7.2
Vim 8.1

Share this:


---------------------------------------------

Bash 如何 Pipe 再透過 sudo 寫入檔案

發佈日期: 2019 年 07 月 15 日，作者: Tsung

於 Linux 的 bash shell 很常會 cat 某些資料，處理完後再寫入到某個檔案，但是常常會遇到權限不足，要怎麼做呢？


Bash 如何 Pipe 再透過 sudo 寫入檔案

主要可以使用 sudo 搭配 tee 來達成

	tee -a # append
	echo "example content" | sudo tee -a /tmp/filename

sudo + tee 操作範例

1. mkdir /tmp/rootdir
2. sudo chown root.root rootdir # 設定權限 造成無法寫入
3. cd /tmp/rootdir
4. touch filename
   touch: 無法觸碰（touch）'filename': 拒絕不符權限的操作
5. echo "example content" | sudo tee -a filename
6. cat filename # 寫入成功
   example content

Share this:

---------------------------------------------

Bash Shell 如何接收並切割字串

發佈日期: 2019 年 07 月 23 日，作者: Tsung

Linux 於 Bash Shell 如何將檔案內的內容切割到每個變數，或者如何撈外部 API 的內容，並 assign 到每個變數去？


Bash Shell 如何接收並切割字串

先對一個檔案，內容用空格分隔的三個參數

1. cat filename
	a b c
2. k1=$(cat filename | cut -d' ' -f 1)
3. k2=$(cat filename | cut -d' ' -f 2)
4. echo $k1
   a
5. echo $k2
   b

若抓遠端檔案 並 使用 tab 分隔

1. cat tab-filename.txt # a [tab] b 遠端檔案 a\tb
2. 範例程式

tmp=$(curl -s "http://example.com/tab-filename.txt")                                                                                                                         
if [[ -z $tmp ]]; then # 若是空的就結束                                                                                                                                      
    #echo "empty"                                                                                                                                                            
    exit                                                                                                                                                                     
fi                                                                                                                                                                           
k1=$(echo "$tmp" | cut -d $'\t' -f 1)                                                                                                                                        
k2=$(echo "$tmp" | cut -d $'\t' -f 2)                                                                                                                                        
k1decode=$(echo "$k1" | urldecode) # 若需要特殊處理                                                                                                                          
echo $k1 # a                                                                                                                                                                 
echo $k2 # b                                                                                                                                                                 
echo $k1decode # a     
                                                                                                                                                      
Share this:

---------------------------------------------


Linux Top 常用快速鍵 與 CLI 參數

發佈日期: 2019 年 07 月 29 日，作者: Tsung

Linux 要查看系統 Load、CPU、RAM、Process ... 等等，最常用也通用的工具就是 top。

top 進入後，有些快速鍵可以讓操作或資訊比較容易觀看(彩色 + highlight)，也可以寫入 ~/.toprc 裡面，預設就可以使用。


Linux Top 常用快速鍵 與 CLI 參數

top 的功能、參數等等，平常蠻少使用到的，不過有空可以 man top 看看，裡面的內容多到超乎想像~

top 常用快速鍵

	z：整個畫面變彩色
	x：垂直 Highlight (對「目前排序」的那列 垂直 highlight)
	> 或 <：排序 CPU、Mem... 左右移動排序參數 (搭配上面的 z、x 會比較容易看到 > 或 < 的效果)
	f：直接選擇要哪個欄位排序、或者取消看到某些欄位，F 按完選完後，按 s 來確認選定欄位，再 q 離開(選完後，再按 x 會 highlight 比較容易看到)
	w：把目前的設定寫到 ~/.toprc

top CLI 常用參數

	-b：要在 script 裡面使用 top 命令(不會畫出 UI)
	下述都要搭配 -b 使用
	-n：畫面更新幾次後就自動離開退出
	-d：Delay 時間。-d 3 就是 3秒更新一次(預設3秒)
	範例：/usr/bin/top -b -n 1 -d 1

Share this:

---------------------------------------------

Vim Profiling 抓出哪邊速度慢

發佈日期: 2020 年 01 月 16 日，作者: Tsung

Vim 的外掛很多，裝太多會造成啟動變慢，或者某些時候變慢，要怎麼知道是哪個外掛造成的？或者是哪個 Function 造成速度慢的呢？


Vim Profiling 抓出哪邊速度慢

沒想到 Vim Profiling 的工具光內建就一卡車可以使用，而且各種分析都有~

以下來列 Vim Profiling 的各種作法

	vim --startuptime vim.log # 離開 Vim 後，查看 vim.log 的檔案，可以看到各個檔案外掛所消耗的時間
	vim # 於 Vim 內，使用 : 的命令如下：
		:profile start profile.log
		:profile func
		:profile file
		" At this point do slow actions
		:profile pause
		:noautocmd qall!
		# 查看 profile.log 會看到 function 每個花的時間
	vim -V12log # 離開 Vim 後，查看 log 這個檔案內容，會有執行哪些東西
	vim --cmd 'profile start profile.log' \
		--cmd 'profile func ' \
		--cmd 'profile file ' \
		-c 'profdel func ' \
		-c 'profdel file ' \
		-c 'qa!' # 把所有歷程的 function 都印出來

---------------------------------------------
Git 如何修改 chmod 文件訪問權限

發佈日期: 2020 年 02 月 18 日，作者: Tsung

Git 已經 Commit 後，檔案權限就都一起 Commit 進去了，要怎麼修改檔案的訪問權限呢？


Git 如何修改 chmod 文件訪問權限

Git 版本不同，作法有些差異，主要都是靠 --chmod 來做設定

Git 2.9 版 以前

1. git update-index --chmod=+x path/to/file # +x、-x ... 都可以
2. chmod +x path/to/file # 註：上面步驟只有修改 index，檔案本身權限沒被修改
3. git ci -m 'chmod filename'

Git 2.9 以後

1. git add --chmod=+x path/to/file
2. chmod -x path/to/file
3. git ci -m 'chmod filename' path/to/file

相關網頁

How to add chmod permissions to file in GIT?

---------------------------------------------

Debian Linux 系統升級 PHP 需要注意的事項 - 2020

發佈日期: 2020 年 03 月 03 日，作者: Tsung

Debian Linux 由 jessie 一路升級到 buster，PHP 也由 7.1、7.2 升級到 7.3，有哪些要注意的事項呢？

	註：此篇還是採用 mod-php 的方式，不過 PHP 升級該注意的事項都是一樣的

Debian Linux 系統升級 PHP 需要注意的事項

PHP 升級除了一般套件升級外，額外要注意自己安裝了哪些 Extension，而這些額外套件主要要看 PECL 和 PEAR。

查看 系統 APT、PECL、PEAR 安裝哪些延伸套件

	dpkg -l | grep php
	pecl list # check version
	pear list # check version

當確認完套件後，再來會有下述資料夾做連結的事情要處理：

	/etc/php/7.2/apache2/
	/etc/php/7.2/cli/
	/etc/php/7.2/mods-available/
	註：mods-available 有設定檔(.ini)，會 ln 到 apache2、cli 裡面去

不想手動做的話，可以使用強制重新安裝來做：(PHP 7.2 → 7.3)

1. sudo apt remove libapache2-mod-php7.2 先移除 7.2，安裝 7.3 後，ln 設定就會到 7.3
2. sudo apt install libapache2-mod-php7.3
3. sudo apt install --reinstall php-memcache php-geoip php-redis # 重新安裝一次，會重新設定 ln 連結
	註：上述 php-memcache 等等只是舉例，請自行找出還有哪些需要重新安裝的

再來去檢查看看下述：

	/etc/php/7.3/apache2/
	/etc/php/7.3/cli/
	/etc/php/7.3/mods-available/
	註：至少裡面 .ini 檔案數量要一致

上述都升級完成後，再來才是升級 PECL、PEAR，要注意版本差異

	sudo pear upgrade
	sudo pecl upgrade

全部完成後，記得 tail -f error.log 觀察看看是否有語法或者相關錯誤要修復

Share this:


---------------------------------------------

Debian Linux 系統升級 PHP 需要注意的事項 - 2020

發佈日期: 2020 年 03 月 03 日，作者: Tsung

Debian Linux 由 jessie 一路升級到 buster，PHP 也由 7.1、7.2 升級到 7.3，有哪些要注意的事項呢？

	註：此篇還是採用 mod-php 的方式，不過 PHP 升級該注意的事項都是一樣的

Debian Linux 系統升級 PHP 需要注意的事項

PHP 升級除了一般套件升級外，額外要注意自己安裝了哪些 Extension，而這些額外套件主要要看 PECL 和 PEAR。

查看 系統 APT、PECL、PEAR 安裝哪些延伸套件
	dpkg -l | grep php
	pecl list # check version
	pear list # check version

當確認完套件後，再來會有下述資料夾做連結的事情要處理：

	/etc/php/7.2/apache2/
	/etc/php/7.2/cli/
	/etc/php/7.2/mods-available/
	註：mods-available 有設定檔(.ini)，會 ln 到 apache2、cli 裡面去

不想手動做的話，可以使用強制重新安裝來做：(PHP 7.2 → 7.3)

1. sudo apt remove libapache2-mod-php7.2 先移除 7.2，安裝 7.3 後，ln 設定就會到 7.3
2. sudo apt install libapache2-mod-php7.3
3. sudo apt install --reinstall php-memcache php-geoip php-redis # 重新安裝一次，會重新設定 ln 連結
	註：上述 php-memcache 等等只是舉例，請自行找出還有哪些需要重新安裝的

再來去檢查看看下述：

	/etc/php/7.3/apache2/
	/etc/php/7.3/cli/
	/etc/php/7.3/mods-available/
	註：至少裡面 .ini 檔案數量要一致

上述都升級完成後，再來才是升級 PECL、PEAR，要注意版本差異

	sudo pear upgrade
	sudo pecl upgrade

全部完成後，記得 tail -f error.log 觀察看看是否有語法或者相關錯誤要修復

Share this:

---------------------------------------------
Linux 如何離開、關閉 VIM

發佈日期: 2020 年 03 月 26 日，作者: Tsung

於 Linux 最常使用的編輯器就是 VI、VIM，但是之前有流傳著，非常多人在 Stack Overflow 裡面發問，而問題就是如何離開 VIM。

	如果是不小心進入，想離開 VIM 的：ESC 多按幾下，然後輸入 :q! ENTER 即可

下述摘錄自此篇：vi - How do I exit the Vim editor? - Stack Overflow https://stackoverflow.com/questions/11828270/how-do-i-exit-the-vim-editor

	:q to quit (short for :quit)
	:q! to quit without saving (short for :quit!)
	:wq to write and quit
	:wq! to write and quit even if file has only read permission (if file does not have write permission: force write)
	😡 to write and quit (similar to :wq, but only write if there are changes)
	:exit to write and exit (same as :x)
	:qa to quit all (short for :quitall)
	:cq to quit without saving and make Vim return non-zero error (i.e. exit with error)

Linux 如何離開、關閉 VIM

基本上，離開 Vim 比較常用的是下述：

	😡 + Enter (存檔 + 離開)
	:qa + Enter (關閉全部開啟的檔案)
	:q! + Enter (強制不存檔離開)
	Shift ZZ (存檔 + 離開)
	Shift ZQ (離開不要存檔)

而此篇文章整理一卡車的暴力離開 VIM 的方法：how-to-exit-vim/README.md at master · hakluke/how-to-exit-vim · GitHub https://github.com/hakluke/how-to-exit-vim/blob/master/README.md

	:!ps axuw | grep vim | grep -v grep | awk '{print $2}' | xargs kill -9
	python -c "from os import system; system('killall -9 vim')"
	timeout 600 vim
	... 上述摘錄自文章，都很暴力的作法~

Share this:

---------------------------------------------

JavaScript 驗證 JSON 是否正確

發佈日期: 2020 年 04 月 27 日，作者: Tsung

使用 JavaScript 要驗證 JSON 的格式是否正確，要怎麼做呢？


JavaScript 驗證 JSON 是否正確

JavaScript 要驗證 JSON 格式並沒什麼好方法，所以就先轉一次，沒轉成功就是格式有問題~

所以簡單寫就是下述：

View Raw Code? https://blog.longwin.com.tw/2020/04/javascript-validate-json-2020/#
json = typeof json === 'object' ? JSON.stringify(json) : json;

包成驗證用的 Function：

View Raw Code? https://blog.longwin.com.tw/2020/04/javascript-validate-json-2020/#
function validateJSON(json) {
    return typeof json === 'object' ? JSON.stringify(json) : json;
}

Share this:


---------------------------------------------

Linux Mint 如何升級

發佈日期: 2020 年 05 月 05 日，作者: Tsung

Linux Mint 系統是 Base 在 Ubuntu Linux 之上，純粹拿來當作業系統來用，長的跟 Windows 比較相像。
https://www.linuxmint.com/

隨手灌一台來用後，就懶得重灌了，Ubuntu 升級到 20.4 的時候，才在想這台都沒升級過，花點時間找怎麼升級~


Linux Mint 如何升級

先直接講 Linux Mint 的升級方式，跟 Ubuntu 類似，Ubuntu 是 do-release-upgrade，Mint 升級方式如下：

	sudo mint-release-upgrade

Mint 升級前的準備、檢查

	Mint Linux 升級檢查：mintupgrade check 或 mintupdate、mint-upgrade-info
	Mint Linux Repository file：/etc/apt/sources.list.d/official-package-repositories.list

相關網頁

How to Upgrade to Linux Mint 19 https://www.tecmint.com/upgrade-to-linux-mint-19/
How to upgrade to Linux Mint 19.3 – The Linux Mint Blog https://blog.linuxmint.com/?p=3838

Share this:


---------------------------------------------
scp 如何保持原始檔案日期、時間

發佈日期: 2020 年 05 月 08 日，作者: Tsung

scp 要怎麼保持檔案的原始時間呢？

man scp 可以看到下述參數：

	-p ：Preserves modification times, access times, and modes from the original file.
	範例：scp -p file.txt remote.example.com:

Share this:
---------------------------------------------
Linux initrd 的開機程式啟動管理

發佈日期: 2020 年 05 月 11 日，作者: Tsung

現在的時代都使用 Systemd 來管理開機、甚至所有程式的執行 等等，取代掉傳統 init 的 System V。
https://zh.wikipedia.org/zh-tw/Systemd
https://zh.wikipedia.org/wiki/UNIX_System_V

現在 Debian、Ubuntu Linux 雖然使用 systemd，但是還是有讓以前的操作習慣相容，維持著 rc0.d ~ rc6.d、rc.local 等等可以使用，有時候用舊方法來查詢還蠻方 便的，話說，今天要使用時，發現都快忘光了，來簡單寫點紀錄當回憶，雖然已經都用不太到了~


Linux initrd 的開機程式啟動管理

Debian Linux 使用 rc0.d ~ rc6.d 來管理，Debian runlevel 定義：

	0：關機 (Halt)
	1：單一使用者模式 (single user mode)
	2-5：多使用者模式 (multi user mode)
	6：系統重啟 (reboot)

/etc 相關檔案 與 update-rc.d 管理

	/etc/inittab
	/etc/rc0.d/
	/etc/rc1.d/
	/etc/rc6.d/
	my-scirpt 是要新增開機自動執行的 script
		update-rc.d my-script defaults
			全部預設：
			runlevel 2 3 4 5 啟動(start)
			runlevel 0 1 6 停止 (stop)。
	update-rc.d my-script start 20 2 3 4 . start 30 5 . stop 80 0 1 6 .
		指定：
		runlevel 2 3 4 執行啟動順序為 20
		runlevel 5 執行啟動順序為 30
		runlevel 0 1 6 執行停止順序為 80
	update-rc.d -f my-script remove # 由開機啟動移除

管理開機啟動的程式 CLI GUI

	rcconf
	sysv-rc-conf

相關網頁

	Linux系統的啟動程序 http://nmc.nchu.edu.tw/tanet/Linux_boot.htm

Share this:



---------------------------------------------
Linux Systemd 設定開機自動啟動的程式、服務

發佈日期: 2020 年 05 月 12 日，作者: Tsung

Linux 以前 initrd 管理開機啟動程式的時代，可以使用 update-rc.d、rcconf、sys-rc-conf 來管理 /etc/rc0.d/ ~ /etc/rc6.d/，現在換 Systemd 後，想要開機自動啟動的程式，要如何設定呢？
https://zh.wikipedia.org/zh-tw/Systemd

Linux Systemd 設定開機自動啟動的程式、服務

列出所有 Service

	systemctl list-units
	systemctl list-units --type=service
	systemctl list-units *.service
	systemctl --type=service
	其它狀態
		systemctl --type=service --state=active
		systemctl --type=service --state=running
		systemctl list-unit-files --type service --state enabled,generated

開機自動啟動、關閉自動啟動、查詢開機是否會自動啟動 .. 等

	sudo systemctl enable apache2.service # 設定 Apache 開機自動啟動
	sudo systemctl disable apache2.service # 設定 Apache 關閉開機自動啟動
	sudo systemctl is-enabled apache2.service # 查看 Apache 服務是否有設定開機自動啟動
	sudo systemctl is-active apache2.service # 檢查 Apache 服務是否正在運行
	sudo systemctl is-failed apache2.service # 檢查 Apache 服務是否啟動失敗

從檔案層面查看有哪些 Systemd service

	ls /lib/systemd/system/
	ls /etc/systemd/system/
	ls /etc/systemd/system/multi-user.target.wants/ # 由 /lib/systemd/system/ ln 到此處

Share this:


---------------------------------------------
---------------------------------------------

Python3 PIP3 套件安裝在哪裡？

發佈日期: 2018 年 09 月 17 日，作者: Tsung

Python3 使用 PIP (PIP3) 安裝套件，套件安裝的路徑在哪裡呢？ (環境：Debian、Ubuntu Linux)


Python3 PIP3 套件安裝在哪裡？

使用者直接使用 pip3 install 的話，預設會在自己目錄下的 ~/.local 裡面，執行檔會在 ~/.local/bin/ 裡面。

如何知道這些路徑，可以用此 Library：30.14. site — Site-specific configuration hook — Python 3.7.0 documentation
https://docs.python.org/3/library/site.html

	$ python3 -m site --user-base
		/home/user/.local
	$ python3 -m site --user-site
		/home/user/.local/lib/python3.5/site-packages

使用 python3 -m site 可以查看更多的資訊：

	$ python3 -m site

sys.path = [
'/home/user',
'/usr/lib/python35.zip',
'/usr/lib/python3.5', '/usr/lib/python3.5/plat-x86_64-linux-gnu',
'/usr/lib/python3.5/lib-dynload',
'/home/user/.local/lib/python3.5/site-packages',
'/usr/local/lib/python3.5/dist-packages',
'/usr/lib/python3/dist-packages',
]
USER_BASE: '/home/user/.local' (exists)
USER_SITE: '/home/user/.local/lib/python3.5/site-packages' (exists)
ENABLE_USER_SITE: True

	$ python -m site # Python 2 sys.path = [
'/home/user', '/usr/lib/python2.7', '/usr/lib/python2.7/plat-x86_64-linux-gnu',
'/usr/lib/python2.7/lib-tk', '/usr/lib/python2.7/lib-old',
'/usr/lib/python2.7/lib-dynload', '/usr/local/lib/python2.7/dist-packages', '/usr/lib       /python2.7/dist-packages',
'/usr/lib/pymodules/python2.7',
]
	USER_BASE: '/home/user/.local' (exists)
	USER_SITE: '/home/user/.local/lib/python2.7/site-packages' (doesn't exist)
	ENABLE_USER_SITE: True

Share this:


---------------------------------------------
APT 鎖定 與 解除套件指定版本 (Hold)

發佈日期: 2018 年 10 月 29 日，作者: Tsung

Debian、Ubuntu Linux 使用 APT 來管理系統套件，系統一直升級上來，總會遇到某些套件想要先鎖定在某些指定版本的問題，或者系統內有多個版本，要怎麼用系統的命令切換呢？

註：建議使用 apt-mark 和 update-alternatives 來設定

APT 鎖定 與 解除套件指定版本 (Hold)

APT 可以新增 /etc/apt/preferences 此檔案，內容參考可見此篇：Debian Linux 完整移除套件 / 重新安裝套件 / 鎖定套件版本(apt)
https://blog.longwin.com.tw/2008/10/debian-remove-purge-install-reinstall-hold-2008/

	vim /etc/apt/preferences # 內容如下, 把版本編號寫死.

		Package: gaim
		Pin: version 0.58

	或

		Package: php
		Pin: version 7.2
		Pin-Priority: 550

另外可以靠 apt-mark 來做鎖定的操作 (apt-mark 操作起來比較直覺)

apt-mark 的操作方式很簡單，看下面指令就可以理解

	sudo apt-mark hold php7 # 若想鎖定在 php 7.2，就寫 php7.2
	sudo apt-mark unhold php7
	sudo apt-mark showhold

在系統裡面有多個版本都裝在一起，ex: php5.6、php7.0 .. 等等，要切換可以靠 update-alternatives，如下述：

	sudo update-alternatives
	sudo update-alternatives --set php /usr/bin/php5.6 # 指定要使用 php5.6
	sudo update-alternatives --config php # 跳出選擇手動挑選

---------------------------------------------
Vim 使用 tee 和 sudo 解決臨時權限不足的問題

發佈日期: 2018 年 11 月 05 日，作者: Tsung

Vim 在編輯檔案時，偶爾會遇到在編輯某個檔案，但是這檔案的權限不足，要怎麼做呢？


Vim 使用 tee 和 sudo 解決臨時權限不足的問題

一般遇到權限不足但是又已經寫完的情況，最常見的作法，就是寫到 /tmp 或自己家目錄，再將此檔案 mv 蓋回來。

不過 tee + sudo 可以不用離開 Vim 一次解決寫入的問題，命令詳見下述：(於 Vim 裡面)

	:w !sudo tee %

環境準備 與 寫入測試

1. $ mkdir /tmp/test # 先來準備一個權限不足的環境
2. $ touch /tmp/test/test.txt
3. $ sudo chown -R root.root /tmp/test
4. 再來 使用 Vim 編輯 /tmp/test/test.txt
5. vim /tmp/test/test.txt # 隨便打幾個字，再來 :w 要存檔，就會遇到下述訊息：
   E45: 有設定 'readonly' 選項(唯讀) (可用 ! 強制執行)
6. 訊息說用 ! 可以強制寫入看看，使用 :w! 遇到下述訊息：
   "test.txt" E212: 無法以寫入模式開啟
7. 再來嘗試看看 ":w !sudo tee %"，會寫入完成，然後看到下述訊息，按 L 重新載入即可
   W12: 警告: 檔案 "test.txt" 自上次讀入後已變動, 而且編輯中的緩衝區也更動了
   See ":help W12" for more info.
   確定([O]), 載入檔案((L)):

「:w !sudo tee %」的功能分解

   :w：Vim 的標準檔案寫入
   !：執行外部命令
   sudo：權限提昇
   tee：把 stdin 存到文件的程式
   %：Vim 的暫存器，存目前編輯文件的路徑名稱，可以 :echo @% 查看，更多資訊可見下面：
	:echo @% " directory/name of file
	:echo expand('%:t') " name of file ('tail')
	:echo expand('%:p') " full path
	:echo expand('%:p:h') " directory containing file ('head')
   此命令就等同由外部 sudo 再使用 tee 將 stdin 寫入檔案，所以檔案變更，Vim 發覺有資料變更，需要重新載入檔案內容

Share this:



---------------------------------------------
grep 使用 Regex 找出相符字元的語法

發佈日期: 2018 年 11 月 08 日，作者: Tsung

Linux 經常使用 grep 來找需要的文字，grep 除了平常直接比對關鍵字外，還可以使用 Regular Expression (regex) 來找符合的字串~


grep 使用 Regex 找出相符字元的語法

grep 要使用 regex 來比對字串，主要是使用 -P 的參數

	grep -P '\d\d' filename # 找出符合兩個數字的
	grep -P '[\d\d|全滿天]' filename # 找出符合兩個數字或「全」、「滿」、「天」任一字元都印出來
	grep -P '(full|keyword)' filename # 找出 full 或 keyword 完全比對的關鍵字

Share this:


---------------------------------------------
Bash 如何取得路徑內的所有檔名

發佈日期: 2018 年 11 月 12 日，作者: Tsung

Linux Bash shell programming 想要取得目錄下的檔名，然後一個一個印出來，一個一個做需要的處理，要怎麼寫呢？


Bash 如何取得路徑內的所有檔名

要將目錄內的檔案，一個一個丟進變數 $filename 裡面，前面可以使用 for、ls 或 find 來送檔名，後面使用 while + read 來接收讀取。

範例可見

	印出此目錄下的檔名
for filename in *.csv; do echo $filename; done
ls | while read -r filename; do echo $filename; done
ls *.pdf | while read -r filename; do echo $filename; done

	印出此路徑下所有符合檔名規則的檔案
find ./ -name '*.csv' -print0 | while read -d '' -r filename; do echo "$filename"; done
find ./*.pdf -print0 | while read -d '' -r filename; do echo $filename; done

	此路靜下符合規則的檔案，在另外做進階的處理 (iconv 將 big5 轉成 utf-8)
find ./ -name '*.csv' -print0 | while read -d '' -r filename; do iconv -f big5 -t utf-8 "$filename"; done

	若想要 pipe 接著處理，轉檔完後，再印出此檔案前兩行
find ./ -name '*.csv' -print0 | while read -d '' -r filename; do iconv -f big5 -t utf-8 "$filename" | head -2; done

Share this:

---------------------------------------------
Linux 如何查看 影片檔案 的 詳細資訊

發佈日期: 2018 年 12 月 14 日，作者: Tsung

影片壓縮的技術在進步，畫質看起來差不多，容量卻差很多；使用 file 查看，只看得出來都是 mp4，要怎麼查看詳細的影片資訊呢？


Linux 如何查看 影片檔案 的 詳細資訊

於 Linux CLI 要查看影片詳細資訊，可以使用 MediaInfo https://zh.wikipedia.org/wiki/MediaInfo

	GitHub - MediaArea/MediaInfo: Convenient unified display of the most relevant technical and tag data for video and audio files.
	https://github.com/MediaArea/MediaInfo

MediaInfo 安裝

	sudo apt install mediainfo # 若想要圖形界面，可以再安裝 mediainfo-gui

MediaInfo 使用

	mediainfo example.mp4
	mediainfo --fullscan example.mp4

---------------------------------------------
在 Vim 玩「打磚塊」的遊戲

發佈日期: 2018 年 12 月 21 日，作者: Tsung

在 Vim 程式寫久了，想要玩個遊戲休息一下，當然也要在 Vim 裡面玩囉~

這遊戲可以把寫的程式當磚塊，然後，左右移動來消除程式碼.. XD


在 Vim 玩「打磚塊」的遊戲

打磚塊 (Breakout clone) 是很復古的遊戲，可見此影片： https://zh.wikipedia.org/wiki/%E6%89%93%E7%A3%9A%E5%A1%8A



在 Vim 想要玩此遊戲，下述有 Source code 與安裝步驟：

GitHub：johngrib/vim-game-code-break: Block-breaking game in vim 8.0 https://github.com/johngrib/vim-game-code-break

Vim Block-breaking Plugin 安裝

1. cd ~/.vim/bundle/ # 註：使用 Pathgen
2. git clone https://github.com/johngrib/vim-game-code-break
3. vim example.txt # 隨便打開任何文件
4. :VimGameCodeBreak # 於 Vim 開啟 遊戲模式
5. 遊戲快速鍵：
	h：←
	l：→
	space：new ball
	`：cheat key
	]：GOD mode
	[：human mode
	q：end game
	Q：quit & close game

若覺得速度太慢，可以於 .vimrc 做下述調整：

1. vim ~/.vimrc
   let g:vimgamecodebreakitem_limit = 4 " default value is 2
2. 存檔再次開啟試試看~

Share this:

---------------------------------------------

Linux 使用 touch 設定檔案修改時間

發佈日期: 2019 年 01 月 07 日，作者: Tsung

備份、測試... 很常會使用到時間，在 Linux CLI 想要將檔案的時間 設定成 未來的時間，或者指定的時間，要怎麼做呢？


Linux 使用 touch 設定檔案修改時間

Linux 常常使用 touch 來建立空檔案，或者將某個檔案「修改時間」設定為現在，要指定時間(過去、未來)、設定檔案 GMT 時間都可以~

	註：修改完，可以用 stat 查看詳細的檔案資訊

stat 操作範例
1. touch test.txt
2. stat test.txt
	File: test.txt
	Size: 0             Blocks: 0          IO Block: 4096   普通空白檔案
	Device: 24h/36d Inode: 104235      Links: 1
	Access: (0644/-rw-r--r--)  Uid: ( 1000/     test)   Gid: ( 1000/     test)
	Access: 2019-01-06 09:28:25.312318447 +0800
	Modify: 2019-01-06 09:28:25.312318447 +0800
	Change: 2019-01-06 09:28:25.312318447 +0800
	Birth: -

使用 touch 修改時間

touch --help 可以查看詳細參數

下述只有寫 touch 參數，stat 就自行查看囉~

	touch -m test.txt # 修改 modify time 為現在
	touch -a test.txt # 修改 access time 為現在

touch 指定時間可以使用 -t、-d 的參數，兩者支援的輸入格式不同

	-t STAMP：use [[CC]YY]MMDDhhmm[.ss] instead of current time
		CC：年份的前兩位
		YY：年份的後兩位
	-d STRING：parse STRING and use it instead of current time
	-t、-d 都會同時修改 Access 與 Modify time

操作範例

	touch -t 1901120958.27 test.txt # 2019-01-12 09:58:27
	touch -t 201901120958.27 test.txt # 2019-01-12 09:58:27
		19、2019 都是可以用的
	touch -d '10-December-2013' test.txt # 2013-12-10
	touch -d 2018-12-30 test.txt # 2018-12-10
	touch -d GMT3 test.txt # 時區修改，改為 GMT3 時區


---------------------------------------------

Linux 可仿 Putty 複製貼上 與 增加外掛的終端機 - Terminator

發佈日期: 2019 年 01 月 08 日，作者: Tsung

Linux 使用 Gnome 時，使用滑鼠選取文字後，通常就會「自動複製」，然後使用滑鼠中鍵「貼上」。

平常用的好好的，但是遇到很不幸的事情，滑鼠中鍵壞掉了...

想到 Windows 時代常常使用的 Putty，滑鼠選取文字後，會自動複製，然後使用滑鼠「右鍵」貼上，於是就找到 Terminator 可以達到這件事情~


Linux 可仿 Putty 複製貼上 與 增加外掛的終端機 - Terminator

Terminator = 終端機(Terminal)，發現8年前就有寫過一篇文章，那個時候應該還沒使用 tmux，使用 screen 切割視窗的快速鍵麻煩不少，Terminator 倒是可以快速切割視窗，詳見此篇：Linux 一個視窗可切割多個畫面的終端機 - Terminator
https://blog.longwin.com.tw/2010/12/linux-terminal-terminator-2010/

Terminator 除了可以設定成仿造 Putty 複製貼上的快速鍵外，還有很多人寫了外掛(Plugin)，可以看看下述文件：

	Welcome to Terminator’s documentation! — Terminator 2.0 alpha documentation https://terminator-gtk3.readthedocs.io/en/latest/
		Plugins — Terminator 2.0 alpha documentation https://terminator-gtk3.readthedocs.io/en/latest/plugins.html

Terminator 的安裝與設定

1. apt-get install terminator # 安裝
2. 要設定成 Putty paste style，可以參照此篇設定：A terminal which provides select-to-copy and right-click-to-paste http://askubuntu.com/questions/211292/a-terminal-which-provides-select-to-copy-and-right-click-to-paste
3. 若懶得看的，可以參考此設定檔：https://github.com/tsung/config/tree/master/gnome/terminator/config (Putty style 設定) https://github.com/tsung/config/blob/master/gnome/terminator/config
	A. cd /tmp
	B. git clone https://github.com/tsung/config/
	C. mv config/gnome/terminator/ ~/.config/ # 設定檔：/home/user/.config/terminator/config
	D. 此設定檔有設定：putty_paste_style = True，按右鍵會直接貼上，若要出現設定選單，需要按鍵盤的滑鼠右鍵的按鈕(Alt 右邊那顆)
	E. 若要停止 broadcast off：於視窗左上角，選擇 broadcast off
4. 註：詳細設定參數可使用：man terminator_config 查看

---------------------------------------------
Linux 查詢系統、套件 哪些檔案有被修改

發佈日期: 2019 年 01 月 15 日，作者: Tsung

Linux 想要查詢某個套件中，哪些檔案有被修改，要怎麼做呢？要查整個系統有哪些檔案有被修改，要怎麼做呢？


Linux 查詢系統、套件 哪些檔案有被修改

Debian / Ubuntu Linux 可以使用 debsums 來查看系統或套件有哪些檔案被修改過。

debsums 使用說明與參數

	debsums：checks the MD5 sums of installed debian packages.
	Usage: debsums [OPTIONS] [PACKAGE|DEB]

debsums 操作範例

	sudo debsums -ac apache2 # 查看 Apache2 的 Package 哪些檔案有被修改
	sudo debsums -ac # 找出系統上所有被修改過的檔案

---------------------------------------------

---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------
---------------------------------------------




---------------------------------------------



---------------------------------------------































