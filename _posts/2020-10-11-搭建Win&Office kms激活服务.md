---
layout:     post
title:      "搭建Win&Office kms激活服务"
subtitle:   ""
date:       2020-10-11
author:     "QiQ"
header-img: "img/BingWallpaper-2020-10-11.jpg"
tags:
    - Win&Office激活

---

## 获取vlmcsd
- [vlmcsd](https://github.com/Wind4/vlmcsd)
- git clone https://github.com/Wind4/vlmcsd

## 运行vlmcsd服务
- 解压后cd到binaries/Linux/intel/static目录
- 赋予执行权限 chmod u+x vlmcsd-x64-musl-static
- 启动服务 ./vlmcsd-x64-musl-static
- 启动服务并写日志 ./vlmcsd-x64-musl-static -l /var/log/vlmcsd.log

***⚠️不支持激活win7旗舰版***

## 激活教程
```
slmgr.vbs -upk
slmgr.vbs -ipk W269N-WFGWX-YVC9B-4J6C9-T83GX      #不同系统版本这里的激活码不一样
slmgr.vbs -skms xxxx      #这里填Kms域名，如果你自己的已搭建好，可以输入你的域名或者IP
slmgr.vbs -ato
slmgr.vbs -dlv
```
### 各版本系统kms密钥
```
Windows Server 半年频道版本

Windows Server 版本 1809

操作系统版本

KMS 客户端安装密钥

Windows Server Datacenter

6NMRW-2C8FM-D24W7-TQWMY-CWH2D

Windows Server Standard

N2KJX-J94YW-TQVFB-DG9YT-724CC

Windows Server 版本 1803

操作系统版本

KMS 客户端安装密钥

Windows Server Datacenter

2HXDN-KRXHB-GPYC7-YCKFJ-7FVDG

Windows Server Standard

PTXN8-JFHJM-4WC78-MPCBR-9W4KR

Windows Server 版本 1709

操作系统版本

KMS 客户端安装密钥

Windows Server Datacenter

6Y6KB-N82V8-D8CQV-23MJW-BWTG6

Windows Server Standard

DPCNP-XQFKJ-BJF7R-FRC8D-GF6G4

Windows Server LTSC/LTSB 版本

Windows Server 2019

操作系统版本

KMS 客户端安装密钥

Windows Server 2019 Datacenter

WMDGN-G9PQG-XVVXX-R3X43-63DFG

Windows Server 2019标准版

N69G4-B89J2-4G8F4-WWYCC-J464C

Windows Server 2019 Essentials

WVDHN-86M7X-466 P 6-VHXV7-YY726

Windows Server 2016

操作系统版本

KMS 客户端安装密钥

Windows Server 2016 Datacenter

CB7KF-BWN84-R7R2Y-793K2-8XDDG

Windows Server 2016 Standard

WC2BQ-8NRM3-FDDYY-2BFGV-KHKQY

Windows Server 2016 Essentials

JCKRF-N37P4-C2D82-9YXRT-4M63B

Windows 10 中，所有受支持的半年频道版本

操作系统版本

KMS 客户端安装密钥

Windows 10 专业版

W269N-WFGWX-YVC9B-4J6C9-T83GX

Windows 10 专业版 N

MH37W-N47XK-V7XM9-C7227-GCQG9

Windows 10 专业工作站

NRG8B-VKK3Q-CXVCJ-9G2XF-6Q84J

Windows 10 专业工作站 N

9FNHH-K3HBT-3W4TD-6383H-6XYWF

Windows 10 专业教育版

6TP4R-GNPTD-KYYHQ-7B7DP-J447Y

Windows 10 专业教育版 N

YVWGF-BXNMC-HTQYQ-CPQ99-66QFC

Windows 10 教育版

NW6C2-QMPVW-D7KKK-3GKT6-VCFB2

Windows 10 教育版 N

2WH4N-8QGBV-H22JP-CT43Q-MDWWJ

Windows 10 企业版

NPPR9-FWDCX-D2C8J-H872K-2YT43

Windows 10 企业版 N

DPH2V-TTNVB-4X9Q3-TJR4H-KHJW4

Windows 10 企业版 G

YYVX9-NTFWV-6MDM3-9PT4T-4M68B

Windows 10 企业版 G N

44RPN-FTY23-9VTTB-MP9BX-T84FV

Windows 10 LTSC/LTSB 版本

Windows 10 LTSC 2019

操作系统版本

KMS 客户端安装密钥

Windows 10 企业版 LTSC 2019

M7XTQ-FN8P6-TTKYV-9D4CC-J462D

Windows 10 企业版 N LTSC 2019

92NFX-8DJQP-P6BBQ-THF9C-7CG2H

Windows 10 LTSB 2016

操作系统版本

KMS 客户端安装密钥

Windows 10 企业版 LTSB 2016

DCFःK-NFMTC-ः88 NJ-PFHPY-QJ4BJ

Windows 10 企业版 N LTSB 2016

QFFDN-GRT3P-VKWWX-X7T3R-8B639

Windows 10 LTSB 2015

操作系统版本

KMS 客户端安装密钥

Windows 10 企业版 2015 长期服务

WNMTR-4C88C-JK8YV-HQ7T2-76DF9

Windows 10 企业版 2015 长期服务 N

2F77B-TNFGY-69QQF-B8YKP-D69TJ

较早版本的 Windows Server

Windows Server 2012 R2

操作系统版本

KMS 客户端安装密钥

Windows Server 2012 R2 Server Standard

D2N9P-3P6X9-2R39C-7RTCD-MDVJX

WindowsServer 2012 R2 Datacenter

W3GGN-FT8W3-Y4M27-J84CP-Q3VJ9

WindowsServer 2012 R2 Essentials

KNC87-3J2TX-XB4WP-VCPJV-M4FWM

Windows Server 2012

操作系统版本

KMS 客户端安装密钥

Windows Server 2012

BN3D2-R7TKB-3YPBD-8DRP2-27GG4

Windows Server 2012 N.

8N2M2-HWPGY-7PGT9-HGDD8-GVGGY

Windows Server 2012 单语言版

2WN2H-YGCQR-KFX6K-CD6TF-84YXQ

Windows Server 2012 特定国家/地区版

4K36P-JN4VD-GDC6V-KDT89-DYFKP

Windows Server 2012 Server Standard

XC9B7-NBPP2-83J2H-RHMBY-92BT4

Windows Server 2012 MultiPoint Standard

HM7DN-YVMH3-46JC3-XYTG7-CYQJJ

Windows Server 2012 MultiPoint Premium

XNH6W-2V9GX-RGJ4K-Y8X6F-QGJ2G

Windows Server 2012 Datacenter

48HP8-DN98B-MYWDG-T2DCC-8W83P

Windows Server 2008 R2

操作系统版本

KMS 客户端安装密钥

Windows Server 2008 R2 Web 版

6TPJF-RBVHG-WBW2R-86QPH-6RTM4

Windows Server 2008 R2 HPC 版

TT8MH-CG224-D3D7Q-498W2-9QCTX

WindowsServer 2008 R2标准版

YC6KT-GKW9T-YTKYR-T4X34，R7VHC

WindowsServer 2008 R2 企业版

489J6-VHDMP-X63PK-3K798-CPX3Y

WindowsServer 2008 R2数据中心

74YFP-3QFB3-KQT8W-PMXWJ-7M648

面向基于 Itanium 系统的 Windows Server 2008 R2

GT63C-RJFQ3-4GMB6-BRFB9-CB83V

Windows Server 2008

操作系统版本

KMS 客户端安装密钥

Windows Web Server 2008

WYR28-R7TFJ-3X2YQ-YCY4H-M249D

Windows Server 2008 Standard

TM24T-X9RMF-VWXK6-X8JC9-BFGM2

不带 Hyper-V 的 Windows Server 2008 Standard

W7VD6-7JFBR-RX26B-YKQ3Y-6FFFJ

Windows Server 2008 企业版

YQGMW-MPWTJ-34KDK-48M3W-X4Q6V

不带 Hyper-V 的 Windows Server 2008 企业版

39BXF-X8Q23-P2WWT-38T2F-G3FPG

Windows Server 2008 HPC

RCTX3-KWVHP-BR6TB-RB6DM-6X7HP

Windows Server 2008 Datacenter

7M67G-PC374-GR742-YH8V4-TCBY3

不带 Hyper-V 的 Windows Server 2008 Datacenter

22XQ2-VRXRG-P8D42-K34TD-G3QQC

面向基于 Itanium 系统的 Windows Server 2008

4DWFP-JF3DJ-B7DTH-78FJB-PDRHK

早期版本的 Windows

Windows 8.1

操作系统版本

KMS 客户端安装密钥

Windows 8.1 专业版

GCRJD-8NW9H-F2CDX-CCM8D-9D6T9

Windows 8.1 专业版 N

HMCNV-VVBFX-7HMBH-CTY9B-B4FXY

Windows 8.1 企业版

MHF9N-XY6XB-WVXMC-BTDCT-MKKG7

Windows 8.1 企业版 N

TT4HM-HN7YT-62K67-RGRQJ-JFFXW

Windows 8

操作系统版本

KMS 客户端安装密钥

Windows 8 专业版

NG4HW-VH26C-733KW-K6F98-J8CK4

Windows 8 专业版 N

XCVCF-2NXM9-723PB-MHCB7-2RYQQ

Windows 8 企业版

32JNW-9KQ84-P47T8-D8GGY-CWCK7

Windows 8 企业版 N

JMNMF-RHW7P-DMY6X-RF3DR-X2BQT

Windows 7的

操作系统版本

KMS 客户端安装密钥

Windows 7 专业版

FJ82H-XT6CR-J8D7P-XQJJ2-GPDD4

Windows 7 专业版 N

MRPKT-YTG23-K7D7T-X2JMM-QY7MG

Windows 7 专业版 E

W82YF-2Q76Y-63HXB-FGJG9-GF7QX

Windows7 企业版

33PXH-7Y6KF-2VJC9-XBBR8-HVTHH

Windows 7 企业版 N

YDRBP-3D83W-TY26F-D46B2-XCKRJ

Windows 7 企业版 E

C29WB-22CC8-VJ326-GHFJW-H9DH4
```

## 参考
> [沧水 KMS Cloud](https://kms.cangshui.net/)

> [神代綺凜](https://moe.best/tutorial/linux-kms-server.html)

> [Win10&Office KMS服务器搭建激活教程](https://www.jianshu.com/p/28b07d6cc75b)
