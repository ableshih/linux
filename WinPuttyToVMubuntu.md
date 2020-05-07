# Windows Putty 連線 Ubuntu 虛擬機器
[原始](http://seansharingblog.blogspot.com/2019/05/ubuntu-ssh-server-install.html "Putty WinToUbuntu" )
[![](http://img.youtube.com/vi/jNQXAC9IVRw/0.jpg)](http://www.youtube.com/watch?v=jNQXAC9IVRw)

```


Ubuntu SSH Service SSH 遠端連線服務安裝與使用

sudo apt update    # 更新套件庫資料清單
sudo apt upgrade   # 更新套件

sudo apt install openssh-server

sudo apt install synaptic

synaptic

開啟 Synaptic --> 按[放大鏡]搜尋 --> 出現搜尋對話框，輸入 openssh-server --> 按下[Search]按鈕。
搜尋到 openssh-server --> 滑鼠點左邊的選框 --> 會出現選單，選[Mark for Installation] --> 選框會被勾選。
點上方[Apply]按鈕開始安裝 --> 出現[Changes applied]對話框 --> 按下[Close]，完成安裝。
openssh-server 的選框變成實心的，表示安裝完成了。
再檢查 SSH遠端連線伺服器的狀態，以下任一指令都可以使用：
sudo service ssh status
sudo /etc/init.d/ssh status
sudo systemctl status ssh
```

----------------------------------
[原始](https://kanchengzxdfgcv.blogspot.com/2015/10/putty-windows-ubuntu-oracle-vm.html "Putty WinToUbuntu" )


# 利用 Putty Windows實體電腦 連線 Ubuntu虛擬機器 - Oracle VM VirtualBox
```

[要先安裝 ssh server]

vm stop

Ubuntu 找到IP
$ ifconfig

Windows 找到IP
> ipconfig


如上我們看到虛擬機器中用的是預設 NAT ，內部 IP 是 10.0.2.15

而 VirtualBox給我們 Windows實體機器用的虛擬乙太網路卡 IP 為 192.168.56.1

簡單的做法是用連結轉送的方式，將 VM 關機

VirtualBox 在 該VM上選 "設定" -> "網路" -> "進階" -> "連結阜轉送"

將協定、主客體IP、port都設定好

主機IP 192.168.56.1 port 22
客體IP 10.0.2.15 port 22

確定儲存後，用 putty 連上 IP (192.168.56.1)，Port (22) ，選擇 open 按 "是"，輸入虛擬機器帳密...即可連線


sudo service ssh status

```
