

Raspberry-Pi 4 的安裝過程  

https://william-weng.github.io/2019/12/08/raspberry-pi-helloworld/?fbclid=IwAR15NRWb9wHzCh1tzRDFoDf5I9rxdAqF631PwdMw8xHGcIUIjAdQ1BYEX9k  
```
更新
sudo apt update
sudo apt upgrade

輸入法
sudo apt install fcitx-table-boshiamy 

擷圖及錄影工具
sudo apt install scrot
sudo apt install simplescreenrecorder

exfat及ntfs支援工具
sudo apt install exfat-fuse
sudo apt install ntfs-3g

7zip壓縮
sudo apt install p7zip-full

備份及還原
# 利用dd指令將sd卡備份成檔案，其中bs的值為一次寫入的區塊大小
sudo dd if=/dev/disk2 of=back.img bs=4m
# 利用dd指令跟pv指令將sd卡備份成檔案，並且顯示進度，其中pv的值為sd卡的大小
sudo dd if=/dev/disk2 | pv -s 16G | sudo dd of=back.img bs=4m

縮小備份檔
sudo pishrink.sh image.img

還原備份 win
balenaEtcher 


SSH遠端登入
設定裡要打開ssh協定

ifconfig
ip a

ssh pi@192.168.0.8
exit


共享資料夾
安裝Samba協定，讓Windows也能讀得到樹莓派上的資料夾。

sudo apt install samba -y
mkdir Share
sudo geany /etc/samba/samba.conf
sudo systemctl restart smbd.service

設定smb.conf檔
[PiShare]
   comment = Share Fold
   path = /home/pi/Desktop/Share
   browseable = yes
   writeable = yes
   create mask = 0740
   directory mask = 0750
   guest ok = yes
   public = no
   
用 Windows登入共享資料夾
Windows登入就打「\192.168.0.8\PiShare」就可以了。

遠端桌面
在樹莓派端安裝xrdp跟tightvncserver
sudo apt install xrdp -y
sudo apt install tightvncserver -y

Windows登入遠端桌面
使用Windows本身的遠端桌面連線

FTP 伺服器
sudo apt install vsftpd
sudo geany /etc/vsftpd.conf
sudo service vsftpd restart

修改 /etc/vsftpd.conf 
local_enable=YES
write_enable=YES

設定固定IP
ip a
sudo geany /etc/dhcpcd.conf
sudo service vsftpd restart

修改  /etc/dhcpcd.conf
# 有線網卡 - eth0
interface eth0
static ip_address=192.168.0.87/24
static routers=192.168.0.1
static domain_name_server=192.168.0.1

# 無線網卡 - wlan0
interface wlan0
static ip_address=192.168.0.87/24
static routers=192.168.0.1
static domain_name_server=192.168.0.1






















$ sudo apt-get update 
更新軟體套件的清單 當/etc/apt/source.list (取得遠端更新伺服器的套件檔案清單)

$ sudo apt-get upgrade 
更新軟體套件本身(更新已安裝套件)

$ sudo apt-get dist-upgrade
更新系統已安裝套件，移除重複套件並clean，會比upgrade更花時間

$ sudo rpi-update
若想更新韌體部分，指令如下（若擔心的話，請事先備份整張記憶卡）：

$ sudo apt-get clean 
(清除更新時所下載回來的檔案)

$ sudo reboot 
$ sudo shutdown -r now
$ sudo sync;
重新啟動 重開機

sudo poweroff -f
關不掉時用 (強制)

uname -a
kernel version check

uname -m
CPU 架構

sudo su (, 退出用 exit)
切換到管理者帳號) 以 root 身分登入

$ sudo raspi-config   
系統設定 :(進入系統設定表單)
   

關機指令是 sudo halt 或 sudo poweroff
登出系統的指令是 logout 或 exit,


系統登入登出與關機 :
登出系統 logout 或 exit, 執行後會回到登入前狀態 (按 Ctrl-D 亦可).
關機指令 sudo halt 或 sudo poweroff, 強制 sudo poweroff -f , 







startx   (進入 X 視窗系統)

$ sudo /etc/rc.local 顯示自己的 IP 

$ sudo update-rc.d -f ssh defaults 20 允許 SSH 遠端登入

$ sudo mv old_name new_name 重新命名檔案





顯示網路設定
$ ifconfig  (全部)
$ ifconfig wlan0 (只顯示無線網路卡 wlan0)
查詢區網 IP :
$ hostname -I 
$ ifconfig 

顯示自己的 IP
$ sudo /etc/rc.local
允許 SSH 遠端登入
$ sudo update-rc.d -f ssh defaults 20

系統管理 :
$ su  (切換到管理者帳號)
$ ps -aux   (查看有多少程序在執行, 可查得其 PID 與程式名稱 COMMAND)
$ sudo kill 123  (刪除 PID=123 的執行中程序)
$ clear   (清空畫面)
$ passwd  (更改密碼)
$ su   (從現在登入帳號轉改換為系統管理者權限, 須輸入管理者帳號)
$ exit  (離開系統管理者權限回到原本登入帳號權限)











應用程式或套件安裝移除
$ sudo apt-get install PKGNAME (安裝 PKGNAME)
$ sudo apt-get install zip unzip (安裝 zip unzip)
$ sudo apt-get --purge remove PKGNAME  (移除 PKGNAME)
$ sudo apt-get remove --purge 'mysql-.*'   (移除 MySQL 伺服器)
$ pip install PKGNAME  (安裝 PKGNAME)
$ pip install "PKGNAME==1.0.4"  (安裝 PKGNAME-指定版本)
$ pip install "PKGNAME>=1.0.4"  (安裝 PKGNAME-指定最小版本)
$ pip install -U PKGNAME  (更新 PKGNAME)
$ pip uninstall PKGNAME (移除 PKGNAME)
$ sudo apt-get autoremove  (自動移除已不需要的套件)
$ pip list (顯示已安裝之套件)
註 :  Python 3 使用 pip3; Python 2 使用 pip2, 而 pip 則是安裝至目前環境 (Python2/3)
重新命名檔案
$ sudo mv old_name new_name
複製檔案
$ sudo cp interfaces /etc/network/interfaces
$ sudo cp wpa_supplicant.conf /etc/wpa_supplicant/wpa_supplicant.conf
移除檔案 
$ rm file_name
$ rm -f file_name (強制刪除)
$ rm -rf dir_name (強制刪除目錄及其下的全部檔案與子目錄)
查詢檔案 :
$ df  (列出全部硬碟使用情形, 單位 byte)
$ df -h (列出全部硬碟使用情形, 人性化以 MB/GB 為單位)
$ df -Bm (列出全部硬碟使用情形, 以 MB 為單位)
$ sudo find . -name 'test.py'   (查詢現在目錄下是否有 test.py)
$ sudo find . -name '*.py'       (查詢以 .py 結尾之檔案)
$ sudo find / -name 'test'.py'    (查詢根目錄下是否有 test.py)
$ sudo find / -name 'test*'         (查詢根目錄下以 test 開頭的檔案)
掃描無線基地台
$ sudo iwlist wlan0 scan    
重新啟動網路卡設定 (即 /etc/network/interfaces 之設定)
$ sudo /etc/init.d/networking restart
重置網路卡
$ sudo ifdown wlan0 (拉下來)
$ sudo ifup wlan0 (拉上去)
連線主機
$ ping yahoo.com  
壓縮解壓縮 :
$ tar -zcvf myfile.tar.gz mydir  (將 mydir 目錄下的檔案全部壓縮成 myfile.tar.gz)
$ tar -zxvf myfile.tar.gz  (將 myfile.tar.gz 解壓縮到 myfile 資料夾)
$ gzip -r mydir (將 mydir 目錄下的檔案全部壓縮)
$ gzip -d myfile.gz (將 myfile.gz 解壓縮)
$ zip zippedfile file1 file2 file3 (將 file1, file2, file3 壓縮成 zippedfile, , 須安裝 zip)
$ zip -r myfile.zip mydir  (將 myfile 含子資料夾壓縮成 myfile.zip, 須安裝 zip)
$ unzip myfile.zip  (解壓縮 zip 檔, 須安裝 unzip)

使用者管理 :
$ sudo useradd tony  (新增使用者帳號 tony)
$ sudo userdel tony   (刪除帳號為 tony 的使用者)
$ sudo usermod -d /var/www/html/tony tony  (更改帳號 tony 的預設目錄)
Apache+MySQL 伺服器
$ sudo apt-get install apache2  (安裝 Apache2 網頁伺服器)
$ sudo apt-get install php5 libapache2-mod-php5  (安裝 PHP5 語言解譯引擎)
$ sudo /etc/init.d/apache2 restart  (重啟 Apache 伺服器)
$ sudo service apache2 restart  (重啟 Apache 伺服器)
$ sudo apt-get install mysql-server mysql-client php5-mysql (安裝 MySQL 伺服器)
$ sudo apt-get install php5-mcrypt  (安裝  PHP5 安全性模組)
$ mysql -u root -p  (以 root 帳號進入 MySQL 命令列, 須輸入密碼)
$ systemctl status mysql.service  (顯示 MySQL 服務之狀態 Active/Failed)
$ sudo service mysql restart  (重啟 MySQL 伺服器)
$ use TABLE_NAME  (進入資料表, 可下達 SQL 指令)
$ exit   (跳出 MySQL 命令列) 
VNC 伺服器
$ sudo apt-get install tightvncserver   (安裝 VNC 伺服器)
$ sudo tightvncserver  (啟動與設定 VNC 伺服器)
$ vncserver :1 (執行 VNC 伺服器)
$ vncserver :1 -geometry 1366x768 -depth 16 -pixelformat rgb565 (指定解析度與彩色)
$ sudo vncserver -kill :1 (結束)
$ vncpasswd  (修改連線密碼)
$ service vncserver restart (重新啟動 VNC 伺服器)
GCC :
$ gcc -o helloworld helloworld.c  (將 helloworld.c 編譯成 helloworld)
Crontab :
$ crontab -e (編輯 crontab)
$ sudo cat /var/log/cron.log  (查看 crontab 執行記錄檔)
$ sudo nano /etc/rsyslog.conf  (編輯系統紀錄設定檔, 拿掉 cron.* 前之 # 即啟用 cron 紀錄)
$ sudo /etc/init.d/rsyslog restart  (重啟系統紀錄設定檔, cron 紀錄設定生效)









應用程式或套件安裝移除 (參考 PyPi)
$ python3 -m pip install --upgrade pip (更新 pip 本身版本)
$ python3 -m pip install --user --upgrade requests  (更新 requests)
$ sudo apt-get install PKGNAME (安裝 PKGNAME)
$ sudo apt-get install zip unzip (安裝 zip unzip)
$ sudo apt-get --purge remove PKGNAME  (移除 PKGNAME)
$ sudo apt-get remove --purge 'mysql-.*'   (移除 MySQL 伺服器)
$ pip install PKGNAME  (安裝 PKGNAME)
$ pip install "PKGNAME==1.0.4"  (安裝 PKGNAME-指定版本)
$ pip install "PKGNAME>=1.0.4"  (安裝 PKGNAME-指定最小版本)
$ pip install -U PKGNAME  (更新 PKGNAME)
$ pip uninstall PKGNAME (移除 PKGNAME)
$ sudo apt-get autoremove  (自動移除已不需要的套件)
$ pip list (顯示已安裝之套件)
註 :  Python 3 使用 pip3; Python 2 使用 pip2, 而 pip 則是安裝至目前環境 (Python2/3)
$ pip --version  (查詢 pip 版本)

查詢程式安裝位置 :
$ where python
$ which python 



複製檔案
$ sudo cp interfaces /etc/network/interfaces
$ sudo cp wpa_supplicant.conf /etc/wpa_supplicant/wpa_supplicant.conf
移除檔案 
$ rm file_name
$ rm -f file_name (強制刪除)
$ rm -rf dir_name (強制刪除目錄及其下的全部檔案與子目錄)
查詢檔案 :
$ df  (列出全部硬碟使用情形, 單位 byte)
$ df -h (列出全部硬碟使用情形, 人性化以 MB/GB 為單位)
$ df -Bm (列出全部硬碟使用情形, 以 MB 為單位)
$ sudo find . -name 'test.py'   (查詢現在目錄下是否有 test.py)
$ sudo find . -name '*.py'       (查詢以 .py 結尾之檔案)
$ sudo find / -name 'test'.py'    (查詢根目錄下是否有 test.py)
$ sudo find / -name 'test*'         (查詢根目錄下以 test 開頭的檔案)
掃描無線基地台
$ sudo iwlist wlan0 scan    
重新啟動網路卡設定 (即 /etc/network/interfaces 之設定)
$ sudo /etc/init.d/networking restart
重置網路卡
$ sudo ifdown wlan0 (拉下來)
$ sudo ifup wlan0 (拉上去)
連線主機
$ ping yahoo.com  

壓縮解壓縮 :
$ tar -zcvf myfile.tar.gz mydir  (將 mydir 目錄下的檔案全部壓縮成 myfile.tar.gz)
$ tar -zxvf myfile.tar.gz  (將 myfile.tar.gz 解壓縮到 myfile 資料夾)
$ gzip -r mydir (將 mydir 目錄下的檔案全部壓縮)
$ gzip -d myfile.gz (將 myfile.gz 解壓縮)
$ zip zippedfile file1 file2 file3 (將 file1, file2, file3 壓縮成 zippedfile, , 須安裝 zip)
$ zip -r myfile.zip mydir  (將 myfile 含子資料夾壓縮成 myfile.zip, 須安裝 zip)
$ unzip myfile.zip  (解壓縮 zip 檔, 須安裝 unzip)
系統管理 :
$ su  (切換到管理者帳號)
$ ps -aux   (查看有多少程序在執行, 可查得其 PID 與程式名稱 COMMAND)
$ sudo kill 123  (刪除 PID=123 的執行中程序)
$ clear   (清空畫面)
$ passwd  (更改密碼)
$ su   (從現在登入帳號轉改換為系統管理者權限, 須輸入管理者帳號)
$ exit  (離開系統管理者權限回到原本登入帳號權限)
$ free -h (檢查記憶體剩下多少)
$ df -h (檢查 SD 卡剩餘多少空間)
使用者管理 :
$ sudo useradd tony  (新增使用者帳號 tony)
$ sudo userdel tony   (刪除帳號為 tony 的使用者)
$ sudo usermod -d /var/www/html/tony tony  (更改帳號 tony 的預設目錄)
Apache+MySQL 伺服器
$ sudo apt-get install apache2  (安裝 Apache2 網頁伺服器)
$ sudo apt-get install php5 libapache2-mod-php5  (安裝 PHP5 語言解譯引擎)
$ sudo /etc/init.d/apache2 restart  (重啟 Apache 伺服器)
$ sudo service apache2 restart  (重啟 Apache 伺服器)
$ sudo apt-get install mysql-server mysql-client php5-mysql (安裝 MySQL 伺服器)
$ sudo apt-get install php5-mcrypt  (安裝  PHP5 安全性模組)
$ mysql -u root -p  (以 root 帳號進入 MySQL 命令列, 須輸入密碼)
$ systemctl status mysql.service  (顯示 MySQL 服務之狀態 Active/Failed)
$ sudo service mysql restart  (重啟 MySQL 伺服器)
$ use TABLE_NAME  (進入資料表, 可下達 SQL 指令)
$ exit   (跳出 MySQL 命令列) 
VNC 伺服器
$ sudo apt-get install tightvncserver   (安裝 VNC 伺服器)
$ sudo tightvncserver  (啟動與設定 VNC 伺服器)
$ vncserver :1 (執行 VNC 伺服器)
$ vncserver :1 -geometry 1366x768 -depth 16 -pixelformat rgb565 (指定解析度與彩色)
$ sudo vncserver -kill :1 (結束)
$ vncpasswd  (修改連線密碼)
$ service vncserver restart (重新啟動 VNC 伺服器)
GCC :
$ gcc -o helloworld helloworld.c  (將 helloworld.c 編譯成 helloworld)
Crontab :
$ crontab -e (編輯 crontab)
$ crontab -l (顯示 crontab)
$ crontab -r (刪除 crontab)
$ crontab -i (刪除 crontab 前提示)
$ sudo cat /var/log/cron.log  (查看 crontab 執行記錄檔)
$ sudo nano /etc/rsyslog.conf  (編輯系統紀錄設定檔, 拿掉 cron.* 前之 # 即啟用 cron 紀錄)
$ sudo /etc/init.d/rsyslog restart  (重啟系統紀錄設定檔, cron 紀錄設定生效)
查詢 Debian 版本 :
$ cat /etc/debian_version
從 MobaXterm 進入 X 視窗不是用 startx, 要下 :

$ lxsession&


(1)列出已安裝套件
#dpkg -l
(2)套件安裝了什麼
#dpkg -L 套件名稱
(3)查詢檔案由哪個套件安裝
#dpkg -S dpkg
(4)安裝套件
#dpkg  -i  套件名稱    或    #apt-get install 套件名稱
(5)移除套件
#dpkg -r 套件名稱 或 #apt-get remove 套件名稱
(6)搜尋套件
#apt-cache search 搜尋關鍵字
(7)獲得套件名稱的說明
apt-cache show 套件名稱

(9)下載套件原始碼
apt-get  source  套件名稱












樹莓派忘記密碼了？四步重設密碼，收藏之以供不時之需~


將樹莓派關機，移除sd卡，插入到你的電腦。

在PC上打開SD卡根目錄，啟動部分是可見的，並包含一個名為“cmdline.txt”的文件。

用編輯軟體編輯，於內容最後加入 init=/bin/sh

保存，將sd卡插入樹莓派

mount -o remount, rw /

passwd pi
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully

sync
exec /sbin/init

樹莓派會繼續啟動，然後關掉樹莓派並且斷電。

sudo halt

用電腦再次編輯“cmdline.txt” 刪除 init=/bin/sh 存檔

插入sd卡到你的樹莓派啦，再次啟動就可以使用新的密碼啦。






```
