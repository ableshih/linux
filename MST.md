Daisy-chaining
MST(Multi-Stream Technology)

原文網址：https://kknews.cc/other/99xgepb.html

https://www.monitortests.com/pixelclock.php


EDID pixel clock
Pixel Clock = H total * V total * Frame Rate
H total = H active + H sync width + H front porch + H back porch
V total = V active + V sync width + V front porch + V back porch
Blinking = H sync width + H front porch + H back porch


http://jones-hsu.blogspot.com/2009/03/at91sam9263-vga-output-to-monitor.html





https://www.monitortests.com/blog/common-pixel-clock-limits/
Common pixel clock limits
DVI
Links	Limit	Data rate	Bandwidth
Single	165 MHz	3.96 Gbps	4.95 Gbps
Dual	330 MHz*	7.92 Gbps	9.9 Gbps
* Technically no limit defined by the DVI specification, but often limited to 330 MHz.

HDMI
Version	Limit	Data rate	Bandwidth
1.0-1.2a	165 MHz	3.96 Gbps	4.95 Gbps
1.3-1.4b	340 MHz*	8.16 Gbps	10.2 Gbps
2.0-2.0b	600 MHz	14.4 Gbps	18 Gbps
* AMD GPUs without HDMI 2.0 are limited to 297 MHz.

DisplayPort
DisplayPort limits depend on the number of lanes and the link rate:

Reduced Bit Rate (RBR) and High Bit Rate (HBR) are supported by all versions of DisplayPort.
High Bit Rate 2 (HBR2) is supported by DisplayPort 1.2 and newer.
High Bit Rate 3 (HBR3) is supported by DisplayPort 1.3 and newer.

4 lanes
Link rate	8 bpc limit	6 bpc limit	Data rate	Bandwidth
162 MHz (RBR)	216 MHz	288 MHz	5.184 Gbps	6.48 Gbps
270 MHz (HBR)	360 MHz	480 MHz	8.64 Gbps	10.8 Gbps
540 MHz (HBR2)	720 MHz*	960 MHz*	17.28 Gbps	21.6 Gbps
810 MHz (HBR3)	1080 MHz	1440 MHz	25.92 Gbps	32.4 Gbps
* NVIDIA Kepler GPUs are limited to 540 MHz.

2 lanes
Link rate	8 bpc limit	6 bpc limit	Data rate	Bandwidth
162 MHz (RBR)	108 MHz	144 MHz	2.592 Gbps	3.24 Gbps
270 MHz (HBR)	180 MHz	240 MHz	4.32 Gbps	5.4 Gbps
540 MHz (HBR2)	360 MHz	480 MHz	8.64 Gbps	10.8 Gbps
810 MHz (HBR3)	540 MHz	720 MHz	12.96 Gbps	16.2 Gbps

1 lane
Link rate	8 bpc limit	6 bpc limit	Data rate	Bandwidth
162 MHz (RBR)	54 MHz	72 MHz	1.296 Gbps	1.62 Gbps
270 MHz (HBR)	90 MHz	120 MHz	2.16 Gbps	2.7 Gbps
540 MHz (HBR2)	180 MHz	240 MHz	4.32 Gbps	5.4 Gbps
810 MHz (HBR3)	270 MHz	360 MHz	6.48 Gbps	8.1 Gbps



HDMI分辨率的PCLK: pixel clock(像素频率) 计算方法如下：
以1920x1080p/60hz为例，total pixel：2200，total line：1125，filed rate：60Hz，那么：PCLK = 2200*1125*60 = 148.5MHz；

1280x720p/60hz为例，total pixel：1650，total line：750，filed rate：60Hz，那么：PCLK = 1650*751*60 = 74.25MHz；

3840x2160p/60hz YCC444为例，total pixel：4400，total line：2250，filed rate：60Hz，那么：PCLK = 4400*2250*60 = 594MHz；


HDMI像素频率（字符频率/时钟频率），上面计算方式，算1080P时为什么不用1920*1080而要用2200*1125、算4K 时为什么不用3840*2160而要用4400*2250？
求高手赐教？



DisplayPort標準的連接器包含四對差分訊號線，或稱四條主要通道，利用主要通道傳輸影像資料，並可根據顯示資料量的多寡選擇使用一條、二條或四條通路(Lane)傳輸資料。此外，DisplayPort定義三種不同傳輸速率，每一條通路皆可選擇使用1.62Gbit/s、2.7Gbit/s或5.4Gbit/s傳輸。由於DisplayPort運用8b/10b編碼法，編碼後會多增加一些資料位元，因此實際上能支援的最高資料傳輸速率為：

(4通路)x(5.4Gbit/s每通路)x(8/10 Coding Overhead)=17.28Gbit/s。
eDP 1.4提供更多主要通道傳輸速率選擇的彈性。在1.4版以前，eDP主要通道傳輸速率跟DisplayPort完全相同，分為1.62Gbit/s、2.7Gbit/s及5.4Gbit/s，而eDP 1.4又增加新的速率選擇：2.16Gbit/s、2.43Gbit/s、3.24Gbit/s及4.32Gbit/s。
舉例來說，若要傳輸一個1,920x1,200、24位元彩色的面板資料，設計人員可以用二條主要通道以2.7Gbit/s傳輸，或用一條主要通道用5.4Gbit/s傳輸。但實際上，1,920x1,200、24位元彩色面板的資料量僅須用3.7Gbit/s傳輸即可，而不論用二通道2.7Gbit/s或一通道5.4Gbit/s，均提供4.32Gbit/s充分的頻寬。但若同樣1,920x1,200的面板把顏色提高至30位元時，所需的頻寬會增加到4.625Gbit/s，這時上述的頻寬都不夠用。在eDP 1.4之前，這種狀況就得加倍傳輸速率，或者提高通道數，由二通道加至四通道，但在eDP 1.4，此時僅須將傳輸速率由2.7G提高至3.24G，即有5.184Gbit/s足夠的頻寬傳輸資料，而在輸出端與接收端主要通道介面實體層的功耗都能降低，面板端也可以降低等化器線路的功耗。



原文網址：https://kknews.cc/other/99xgepb.html

原文網址：https://kknews.cc/other/99xgepb.html
原文網址：https://kknews.cc/other/99xgepb.html

	
NVIDIA GeForce GTX 1650
Architecture Turing
Video outputs and ports
1x DVI, 1x HDMI, 1x DisplayPort


NVIDIA GeForce MX250
Architecture Pascal
Video outputs and ports
No outputs


NVIDIA 在官網上並沒有詳細說明 MX250、MX230
與 Intel HD620 內顯比較 MX250 效能提升了3.5倍


MX350顯卡等於GTX1050級別？筆記本MX350對比MX250獨顯性能簡評



筆記本中的NVIDIA GeForce MX250顯卡，相比上一代MX150性能提升可以說是微乎其微，只能達到相當於GTX750Ti的性能水平
MX350配備了2GB GDDR5顯存，顯存位寬為64bit，擁有640個流處理器單元
3DMark圖形測試






https://www.videocardbenchmark.net/compare/Quadro+P2000vsQuadro+P1000/3712vs3727
GeForce RTX 2080 Ti
(86%)
21,567
1,399.99

GeForce MX130
(7%)
1,920


display 相關原理
[轉載請註明出處] http://kezeodsnx.pixnet.net/blog

作者: kezeodsnx

講到display，要先從pixel clock(PCLK)談起。PCLK的單位是HZ，從意義上來看，就是每秒要畫幾個點(pixel)。10MHz就表示其能力為每秒可畫10M個點，就這麼簡單。

那PCLK跟display的關係又是什麼呢?基本上，我認為是display的大小，決定了PCLK的值。舉個例好了，假設spec是resolution:1024x768，frame rate(註1)是60Hz

==>每秒鐘，桌面需要畫的點數為1024x768x60=47185920=47.18MHz

因此lcdc至少需要有47.18MHz的能力，才有辦法滿足這個spec。

或許你使用過gtf這個工具來編寫xorg,conf，會覺得有些奇怪，在設定相同的sepc時，所需的PCLK不是47.18MHz。那是因為lcdc將pixel打到panel時，因為硬體的關係，需要有一些blanking的buffer。因此如果是要畫上一張1024x768的桌面，打出來的點其實不止1024x768。舉個例子，如果你想將桌面投影到某台電視，必須先決定要以多少frame rate/resolution來投影。通常絕大多數的電視會follow vesa的spec來訂定blanking的值，因此可用gtf等utility來產生:

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

對lcdc來說，所要打的範圍其實是加上blanking的部份，也就是1344x795x60=64108800=64.11MHz。因此，lcdc必須用此PCLK，才能將vsync鎖在60hHz，電視也才能夠投影。

相關資訊請見:http://kezeodsnx.pixnet.net/blog/post/24115814

至於什麼是blanking的parameter，請參閱這篇文章，說的相當清楚!

http://realchecko.blogspot.com/2007/12/lcd-controller-timing-parameters.html

另附上dsub的pin assignment，給相關工作者參考~

Dsub pin assignment

註1:frame rate: 整個桌面每秒更新的次數，一般的PC/NB都設在60/75HZ，有人說什麼要45Hz人眼才不會覺得閃爍。總之，載狼A啦。









版本
1.0
2006年5月發布。頻寬10.8Gbps。DisplayPort 1.0的最大傳輸速度是8.64Gbit/s，長度是2米。已經廢棄。

1.1a
2008年1月發布。DisplayPort 1.1允許使用其他傳輸媒介（例如光纖），令傳輸距離增加[2]，但沒有標準化其他傳輸媒介。同時加入HDCP到DisplayPort Content Protection (DPCP). 目前極少使用。

1.2
於2009年12月22日發布。它最大的改變是傳輸速度增加兩倍到21.6Gbit/s（High Bit Rate 2（HBR2）mode），支援4K（4096X2160）60Hz，因此支授更高的解析度、影格速率及色深。蘋果公司設計的Mini DisplayPort亦相容此標準[3] [4][5][6]。支援3D、支援多流（multi-streaming）。目前此版本是主流。

1.2a
2012年5月12日，影片電子標準協會宣布，DisplayPort 1.2a增加可由視訊輸出端動態控制螢幕更新率的技術「適應性同步」（Adaptive-Sync），讓螢幕完全配合視訊輸出端的指示來更新畫面[7][8]。

1.3
2014年9月15日，影片電子標準協會發布DisplayPort 1.3，頻寬速度最高32.4 Gbps（HBR3），編碼後有效頻寬為25.92 Gbps，可支援4K（3840X2160）120hz、5K（5120X2880）60hz、8K（7680X4320）30hz。

1.4
2016年2月份最終版的DP 1.4連接埠規範，新標準基於2014年9月的DP 1.3規範，頻寬不變但加入了顯示壓縮串流(Display Stream Compression)技術、前向錯誤更正(Forward Error Correction)、高動態範圍資料封包（HDR meta transport），聲道也提升到32聲道1536 KHz取樣頻率，將為筆記型電腦、智慧型手機及AIO一體機帶來8K級別（7680x4320）的60Hz輸出，4K的話則可以上到120Hz。

2.0
三倍數據帶寬效能
之前版本的DisplayPort v1.4a提供了32.4 Gbps的最大鏈路帶寬，四個通道中的每一個都以8.1 Gbps / lane的鏈路速率運行。使用8b / 10b信道編碼，相當於25.92 Gbps的最大有效載荷。DP 2.0將最大鏈路速率提高到20 Gbps / lane，並具有更高效的128b / 132b信道編碼，最大有效載荷為77.37 Gbps - 與DP 1.4a相比，增加了三倍。這意味著DP 2.0是第一個以60 Hz重新整理率支援8K解析度（7680 x 4320）的標準，全彩色4：4：4解析度，包括每像素30位（bpp），支援HDR-10。

最大化USB-C連接器的增益
DP 2.0實現的效能提升是通過本機DP連接器和通過DP Alt模式的USB-C連接器實現的。USB-C允許單個連接器用於USB數據，影片數據和電源。如果需要同時支援SuperSpeed USB數據和影片，DP 2.0支援的顯著提高的數據速率使用戶能夠在超高解析度影片的同時獲得電源和SuperSpeed USB數據。








我有上網去查詢 晶片顯示 現在來說 幾乎都是 HDMI 2.0 或者 DP1.3

目前查的到的是說
HDMI 1.4 (最大頻寬10.2Gbit/s)
HDMI 2.0 (18Gbit/s)
DP 1.3 (HBR3, 32.4Gbps)

每個基本上HDMI 1.4都說可以支援到 4K(4096*2160) 以上
所以只要 頻寬10.2Gbit/s 就可以了吧

那請問一下 要怎麼算才知道 他不到10.2Gbit/s






--
※ 發信站: 批踢踢實業坊(ptt.cc), 來自: 118.150.139.93
※ 文章網址: https://www.ptt.cc/bbs/VideoCard/M.1468599313.A.2EE.html
推 coldcolour: 你要考慮到螢幕更新率跟色深阿 07/16 01:01
→ coldcolour: 舉例來說 3840x2160 60Hz 10bit 那麼用掉的頻寬就是 07/16 01:03
→ coldcolour: 3840x2160x10x3x60=14.93 Gbit/s 必須HDMI 2.0才夠 07/16 01:04
→ coldcolour: HDMI 1.4 最多就是4096x2160 8bit 24Hz或是3840x2160 07/16 01:09
→ coldcolour: 30 Hz  如果勉強要讓HDMI 1.4傳3840x2160 60Hz 則必須 07/16 01:10
→ coldcolour: 壓縮色度分量  把YCbCr 4:4:4壓成YCbCr 4:2:0 07/16 01:11
→ coldcolour: 也就是NV在沒有HDMI 2.0的那些舊卡上面玩過的把戲




1080I/60Hz 1125 1080 2200 1920 74.25MHz
1080I/50Hz 1125 1080 2640 1920 74.25MHz
720P/60Hz 750 720 1650 1280 74.25MHz
720P/50Hz 750 720 1980 1280 74.25MHz
Analog BandWidth=1650*750*60=74.25MHz 含义为每个时钟要传输74.25M个模拟视频数据。同理1080P60的P CLOCK为148.5MHz



隨著各類高頻寬影音內容包括 4K 、 8K 、 HDR 、 VR 等需要更多的影音傳輸頻寬， VESA 也宣布可提供更高頻寬的 HBR3 ( High Bit Rate 3 )影像與顯示產品的早期認證計畫，基於 HBR3 規範，將可提供 DisplayPort 以及透過 USB Type-C Alt Mode 進行單路 8K 顯示輸出，或是多個 4K 輸出，同時可用於高效能遊戲、 AR 、 VR 與電視應用。

基於 DisplayPort 1.4 與 USB Type-C 的 HBR3 將使用四路通到，在 DisplayPort 下以每通到 8.1Gbps 提供 32.4Gbps 總頻寬，相較於現行 HBR2 頻寬提升 50% ，同時利用 DisplayPort 的多路串接可提供多顯示器串接；此外， HBR3 能夠利用兩路通道就提供 4K 60Hz 影像傳輸，這點可說是解放 DisplayPort over USB Type-C  Alt-Mode 的實用性，這意味著透過 USB Type-C 輸出 4K 影像時僅需使用二路通道輸出影像，可保留兩路通道作為數據傳輸使用。

至於 DisplayPort 1.4 規範是首度支援 HBR3 的介面規範，除了整合用於 USB Type-C 連接器的新技術外，同時也是首個導入對 VESA DSC 顯示串流壓縮的標準，可在 USB Type-C 介面提供包括 HDR 與 8K 顯示輸出，利用 DP1.4 輸出的解析度可達到 8Kp60Hz HDR 與 4Kp120Hz HDR 。

目前包括 AMD 、 NVIDIA 、 RealTek 、晨星半導體等硬體產品已經率先通過前期認證，同時因應日本 2020 夏季奧運要採用 8K 播放， VESA 相關成員也正積極地導入能夠以單纜線提供 8K 傳輸的 HBR3 規範。



The total bandwidth of High Bit Rate 2 connections is 21.6 Gbit/s, the Video Data Rate being 17.28 Gbit/s.




In this mode, you'll be able to connect monitors with these resolutions on one DisplayPort 1.2 output:

One 4096 x 2160 (4K) at 60 frames per second (hertz)
One 3840 x 2160 (4K) at 60 frames per second (hertz)
Up to two 2560 x 1600 up to 60 frames per second (hertz), or one monitor up to 120 hz
Up to four 1920 x 1200 up to 60 frames per second (hertz), or one monitor up to 240 hz
Up to four 1920 x 1080 up to 60 frames per second (hertz), or one monitor up to 240 hz
& all lower resolutions and the ones in between. There is a maximum number of monitors that can be connected to any card, so be sure to check in your owner's manual.
& a variety of mix and match resolutions like one 2560 x 1600 and two 1920 x 1080, etc, as long as the total resolution is below the total bandwidth available




Data Rates
RBR (1.62Gb/s), 
HBR (2.7Gb/s)
HBR2 (5.4Gb/s), 
HBR3 (8.1Gb/s)

2010年1月發表的DP 1.2，由數個新功能組成：

．多重串流傳輸(MST)：利用單一顯示器連接能提供支援給高達四個1,080p螢幕，在進行多檔作業時可協助簡化流程。

．高位元率2(HBR2)：每管線高達5.4Gbps的HBR2，為MST提供更多的功能，同時促成利用單一視訊連接的4K顯示器之開發。


https://www.2cm.com.tw/2cm/zh-tw/tech/3F27C4576BB44D6CB3091EF1C3A70E76



USB 3.0頻寬理論值是5Gbit/s，但是面對Full HD，60Hz畫面更新率(FR)影像傳輸已捉襟見肘，

我就好奇想要來計算一下頻寬,卻怎麼都算不出來,是那裡漏掉了嘛? 有高手知道答案嘛?

Full HD = 1920 x 1080 

頻寬 = 解析度 x 更新率 = 1920 x 1080 x 60 = 124416000 pixel/s

假設 VGA 來說 1個pixel 是 32 bits , 所以 124416000 x 32 =  3981312000 bit/s 

也就是 3.9Gbit/s , 這不到5Gbit/s


1920x1080為實際顯示區，還需要包含Bank區

所以全部為2200x1125。

2200x1125x60x32=4.75G





