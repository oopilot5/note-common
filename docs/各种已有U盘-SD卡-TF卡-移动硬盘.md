# 各种已有 U盘-SD卡-TF卡-移动硬盘 速度
## 查看设备运行在什么协议下
win10 
设置-设备-蓝牙和其它设备
    其它设备 可以看到 设备支持的协议,以及设备已连接到什么协议下运行.

## 格式化类型 exFAT / NTFS 文件系统
U盘/TF卡 格式化成 exFAT 文件系统
    exFAT 单个文件大小突破了 FAT32 的 4GB 限制，最大可达 16EB
    不可使用NTFS文件系统，容易损坏闪存芯片
移动硬盘 应该选择 NTFS 文件系统

- ubuntu 20.04 支持 exFAT (kernel 5.4 开始默认支持 exfat) (并没有 默认不支持 exFAT)
```bash
cat /proc/filesystems | grep ex  #查看 linux 支持的文件系统类型, ubuntu 18.04 默认不支持 exFAT
apt-get install -y exfat-fuse #安装 exfat 文件系统
reboot
```

## 移动硬盘
wd-mypassport 2T-usb3.0-150MR120MW
Sumsang T7-PSSD-NVMe-1T-typec-usb3.2-1050MR1000MW （未买）

## U盘
> U盘 测试软件以4k结果为u盘标称
USB2.0 接口最大传输速率 480Mbps(60MB/s Max, 去掉协议占用一半, 实际速率基本在 20MB - 30MB)。
USB3.0        超高速   5Gbps(500MB/s Max)
读取高速卡，需要USB3.0的读卡器插在电脑的USB3.0接口上。

sandisk CZ880-128G-usb3.1-420MR380MW 
(闪迪至尊超极速™ USB3.1固态闪存盘,SanDisk Extreme Pro USB3.1 CZ880 128G， 将ATTO 的Total Length设置为4G以符合包装上Sandisk所标注测最大传输测试条件。) 片体发热或是遇到小文件的时候，速度立马断崖式下降，8秒后掉到90M，小文件甚至低到20M
toshiba EXII 64G-usb3.0-230MR196MW
toshiba MX 32G-usb3.0-170MR115MW (win10-GPT-UEFI启动盘)

sandisk CZ73-32G-usb3.0-150MR24MW (esxi,openwrt,ubuntu,win10pe启动盘；win10-MBR-BIOS启动盘; roger空闲) (闪电至尊高速酷铄)
sandisk CZ73-32G-usb3.0-150MR60MW-刻字版(蓉儿，杰哥，车车)
sandisk CZ73-32G-usb3.0-150MR62MW(黑-新)

## SD卡
sandisk ExtremePro 128G-SDXC-C10U3-95MR65MW(70D)（新的在170/90，和300/260）
sandisk ExtremePro 64G-SDXC-C10U3-95MR90MW(70D)（新的在170/90，和300/260）

sandisk Ultra(SDHC-UHS-I) 32G-SD-129MR40MW (UHS-I(超频)读卡器) (拥有)
sandisk Ultra(SDHC-UHS-I) 32G-SD-95MR39MW (UHS-I 读卡器)

## TF卡 (MicroSDXC/MicroSDHC)
Sandisk 已有A2性能等级的 160/90和170/90的，以及高耐用行车记录仪专用100读速

samsung EVOPlus 128G-TF(MicroSDXC)-C10U3-97MR88MW(无人机、行车记录仪-闲置）
toshiba 128G-TF(MicroSDXC)-C10U3-90MR23MW(爸手机)

samsung EVOPlus 64G-TF(MicroSDXC)-C10U1A1V10-135MR33MW (闲置)
sandisk Ultra(MicroSDXC-UHS-I) A1 64G-TF-123MR23MW ((UHS-I(超频)读卡器)（未买）
toshiba EXCERIA64G-TF(MicroSDXC)-C10U3-78MR24MW (闲置)

sandisk Ultra 16G-TF(MicroSDHC)-C10-48MR17MW (树莓派)

## 问题
CZ880 掉速问题：
使用TxBENCH可以查看到CZ880主控制器的基本性能，可及其支持了大多数固态硬盘的功能特性，这其中就包括了TRIM指令
设计上支持Trim指令，但是实际目前的固件并没有开放Trim功能，这便是CZ880依旧产生“掉速”的原因所在。希望Sandisk后续能够放出固件解决这一问题。
有条件清空U盘的用户可以使用Sandisk附送的RescuePRO软件(附带纸片上有序列号)进行擦除写0操作，这是最彻底解决“掉速”的方法。
对于一般情况下无法清空U盘，可以借助TxBENCH中的SSD Optimization来定期手动进行垃圾回收操作。优化后的写入速度基本可以满血复活，而且并不影响已存入数据的完整性，这一方法对于Sandisk品牌中采用SSD主控的U盘都有一定效果。

## 相机/手机 SD/TF 卡选择
拍照拍视频要用到的是写速，最高连拍速度不会被存储卡写速影响，主要看机身缓存，读速和写速均不会影响照片或视频的画质、观感、色彩、风格等等。
高写速的卡能使相机持续连拍的张数更多，指最大连拍数量（一直连拍最多能拍多少张），不是指最高连拍速度（每秒能拍多少张）。
高写速的卡在相机连拍后等待时间更短。

拍摄 1080P(FHD) 及 正常码率 4K 视频需要 U3 或 V30 级别的存储卡，
拍摄 高码率 4K 或者 8K 视频则需要 V60 或 V90 的存储卡

拍照至少要U1，拍视频至少U3最好V30，高端设备专业视频 V60或V90

如果你的相机只支持一代卡，最好不买二代卡，浪费性能和钱。