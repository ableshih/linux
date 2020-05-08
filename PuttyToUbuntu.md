

# 主機 Win10 用 Putty 連線到 Ubuntu 虛擬機器 VirtualBox

  1. 查 IP addr(##IP)
  2. 關閉虛擬機
  3. 設定 VirtualBox
  4. 開啟虛擬機
  5. 安裝 ssh server
  6. Win10 安裝 Putty
  7. 連到 虛擬機

[要先安裝 ssh server]

## IP
```
Ubuntu (找到IP)
$ ifconfig

Windows 找到IP
> ipconfig
```
## 關機
```
vm stop (關機)
```

## 設定
```
如上我們看到虛擬機器中用的是預設 NAT ，內部 IP 是 10.0.2.15

而 VirtualBox給我們 Windows實體機器用的虛擬乙太網路卡 IP 為 192.168.56.1

簡單的做法是用連結轉送的方式，將 VM 關機

VirtualBox 在 該VM上選 "設定" -> "網路" -> "進階" -> "連結阜轉送"

將協定、主客體IP、port都設定好

主機IP 192.168.56.1 port 22
客體IP 10.0.2.15 port 22
```
## ssh
```
sudo apt update    # 更新套件庫資料清單
sudo apt upgrade   # 更新套件
sudo apt install openssh-server (裝 ssh server)
```
## Putty
```
確定儲存後，用 putty 連上 IP (192.168.56.1)，Port (22) ，選擇 open 按 "是"，
輸入虛擬機器帳密...即可連線
```


## other
```
再檢查 SSH遠端連線伺服器的狀態，以下任一指令都可以使用：
sudo service ssh status
sudo /etc/init.d/ssh status
sudo systemctl status ssh

sudo service ssh status

```


[參考1](https://kanchengzxdfgcv.blogspot.com/2015/10/putty-windows-ubuntu-oracle-vm.html "Putty WinToUbuntu" )
[參考2](http://seansharingblog.blogspot.com/2019/05/ubuntu-ssh-server-install.html "Putty WinToUbuntu" )
