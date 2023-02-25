# 比亚迪汽车的维修手册和刷机资料
BYD (Build Your Dream) Car Repair Manuals and Factory Images

# 比亚迪汽车多种车型的维修手册和刷机文件
这几个Github仓库包含比亚迪汽车的维修手册和刷机资料，我需要研究一些比亚迪的汽车，发现网上有些网站提供零零散散的维修手册，发现维修手册可以在比亚迪售后网站 http://lms.bydauto.com.cn/ 下载，刷机资料可以在 http://yunpan.byd.com.cn/ 下载，但是都需要经销商或维修厂的账号才能下载。然后发现淘宝闲鱼上面有卖这些资料的，就都买了回来免费分享出来。

# 为什么免费分享？
发现网上有些零零散散的资料，找起来很麻烦。目前汽车的软硬件生态太过封闭，软件方面来说不像手机和路由器那样可以随意刷入第三方开源系统，硬件方面来说不像3D打印机那样有很多改装升级的零配件。想想如果汽车可以刷入开源系统，升级开源零件，也许会很酷可以实现之前没有的功能。  

目前国外有些人在研究改装加装辅助驾驶自动驾驶，比如这个视频 https://www.youtube.com/watch?v=Te4AhlRXnLw 把一款2005年的老车改装了特斯拉的iBooster并加装了开源辅助软件openpilot ( https://github.com/commaai/openpilot )，实现了自动行驶。还有一些人在研究燃油车改装成电动车，比如这个视频 https://www.youtube.com/watch?v=ZVtOss1U7_s 把一个老车大众甲壳虫改装成电动车。因此我分享这些资料以便促进国内外研究各种改装加装。

另外研究这些很有可能是有实际利益的哦，目前比亚迪在售最便宜的秦PLUS DM-i 2023款 9.98万元的低配版是不含全速自适应巡航等L2辅助驾驶功能的，想要全速自适应巡航的话只有加4.6万元升级到14.58万元的高配版。假如可以做出几千元升级辅助驾驶的改装配件，那样低配版加上改装配件的性价比就会很高。


# 大文件都分割压缩上传了
因为Github限制单个文件不能超过100M，单次上传push不能超过2GB，单个仓库不能超过100GB。所以我把大文件（主要是安卓车机的刷机包和几个维修手册）都分割上传了，我用了 https://github.com/sisl/GitHub-ForceLargeFiles 把大文件分割然后上传，分割后的是7zip压缩的分割包，可以手动用7zip解压，也可以用下面的代码自动把所有的文件都恢复
```
git clone https://github.com/sisl/GitHub-ForceLargeFiles

分割
python .\GitHub-ForceLargeFiles\src\main.py --root_dir "C:\xxx\BYDRepairManual\"

恢复
python .\GitHub-ForceLargeFiles\src\reverse.py --root_dir "C:\xxx\BYDRepairManual\"

```

# 国内下载速度可能会慢
因为文件比较多，每个仓库有几十GB，在中国大陆下载可能会不稳定。

首先可以尝试直接下载，如果网速好很快能下载下来

```
git clone https://github.com/BYDcar/BYDPackagesByChip1.git
```

其次如果下载速度慢或者容易断线。可以尝试Github代理，比如 https://ghproxy.com/ 之类  

再次如果下载整个仓库容易断线，可以仅下载需要的文件。参考这里的方法有些工具可以仅下载指定的文件夹 https://stackoverflow.com/questions/7106012/download-a-single-folder-or-directory-from-a-github-repo  

最后如果下载整个几十GB的仓库，git clone下载时有可能在十几GB断线，断线没法断点续传只能重新下，遇到这种情况可以考虑一个一个commit下载（或者几个几个commit下载）

```
# 本地创建一个空git仓库
git init

# 添加一个remote
git remote add origin https://github.com/BYDcar/BYDPackagesByChip1.git

# 拉取一个commit的hash（后面的hash是从GitHub的commits里复制过来的）
# Note: the full history up to this commit will be retrieved unless 
#       you limit it with '--depth=...' or '--shallow-since=...'
git fetch origin d0fcf97e634d670a34a36e71d2395064674c17a2

# 把git的文件解出来
git reset --hard FETCH_HEAD

# 再拉取下一个commit的hash（后面的hash是从GitHub的commits里复制过来的，按顺序复制下一个hash）
git fetch origin c638f4e1de4d61e2295665249d9854d63386e437

# 再把git的文件解出来
git reset --hard FETCH_HEAD

再这样继续重复
......

```

这一系列库包含的文件如下
# 维修手册，仪表盘固件，软件和刷机教程：
https://github.com/BYDcar/BYDRepairManual

# 安卓车机刷机资料
车机刷机包分为两种分类查找形式，一种是按车机控制器芯片版本，另一种是按车型分类。两种里面有些包是一样的只是分类形式不同。

## 按车机芯片版本

https://github.com/BYDcar/BYDPackagesByChip1
```
├─Di1
│      VP128_1.18.1912190.10.1911270.zip
│      VP128_1.18.1912190.6.1911270.zip
│      VP128_1.18.1912190.7.1911270.zip
│      VP128_1.36.2004030.4.2004039.zip
│      VP128_1.36.2005220.2.2005229.zip
│      VP128_1.36.2005220.3.2005229.zip
│      VP128_1.36.2005220.5.2005229.zip
│      VP128_1.36.2106220.9.2107060.zip
│      VP128_1.37.2010130.1.2009300.zip
│      VP128_1.37.2011060.6.2010220.zip
│      VP128_1.37.2011060.7.2010220.zip
│      VP128_1.38.2101090.13.2101090.zip
│      VP128_1.38.2103120.11.2103090.zip
│      VP128_1.38.2103120.14.2103090.zip
│      VP128_1.38.2108300.15.210706.zip
│      VP128_1.49.2106220.2.2107060.zip
│      VP128_1.49.2106220.3.2107060.zip
│      VP128_1.50.2106240.7.2107060.zip
│      一代机的车型升级教程.docx
│      版本详情第一位数为1用VP128，2用DL2L，4用DL2UL，5用DL2.1L.txt
│
└─Di2
    │  版本详情第一位数为1用VP128，2用DL2L，4用DL2UL，5用DL2.1L(20230106221045).txt
    │  版本详情第一位数为1用VP128，2用DL2L，4用DL2UL，5用DL2.1L.txt
    │
    ├─2.x芯片组
    │  ├─2.0UI
    │  │      Di2L_0929_0305_ota_27_signed_user_2006180.2006118.zip
    │  │      Di2L_0929_0305_ota_28_signed_user_2006180.2006118.zip
    │  │      Di2L_ota_21_signed_user_2103120.201207.zip
    │  │      Di2L_ota_22_signed_user_2103120.201207.zip
    │  │      Di2L_ota_22_signed_user_2111050.2112140.zip
    │  │      Di2L_ota_23_signed_user_2012230.2012070.zip
    │  │      Di2L_ota_31_signed_user_2012230.2012070.zip
    │  │
    │  └─3.0UI
    │          Di2L_3.0UI_20191225_20210715_ota_24_user_2108090.2107030.zip
    │          Di2L_3.0UI_20191225_20210715_ota_26_user_2108090.2107030.zip
    │          Di2L_3.0UI_20191225_ota_24_user_2209160.2209090.zip
    │          Di2L_3.0UI_20191225_ota_24_user_2210170.2209090.zip
    │          Di2L_3.0UI_20191225_ota_25_user_2111260.2110090.zip
    │          Di2L_3.0UI_20191225_ota_25_user_2209160.2209090.zip
    │
    ├─4.x芯片组
    │      Di2UL-1_4.1.1.2110220.1.4.2_3.1.2109240.2.4.6_7.1.2109240.1.zip
    │      Di2UL-1_4.1.3.2111240.1.4.2_3.1.2111240.2.4.6_7.1.2111240.2.zip
    │      Di2UL-3_4.1.7.2109240.1.4.4_5.3.2109240.2.4.8_9.3.2109240.2.zip
    │      Di2UL-4_4.1.3.2204070.1.4.2_3.4.2204040.2.4.6_7.4.2204040.2.zip
    │      Di2UL-5_4.1.3.2210140.1.4.2_3.5.2209280.2.4.6_7.5.2209280.2(20230106224053).zip
    │      Di2UL-5_4.1.3.2210140.1.4.2_3.5.2209280.2.4.6_7.5.2209280.2.zip
    │      Di2UL-7_4.1.1.2108100.1.4.2_3.7.2108040.2.4.6_7.7.2108040.2.zip
    │
    └─5.x芯片组
            Di2.1L_canfd_with2in1_SOP_ota_5_signed_user_2211180.2211180.zip
            Di2.1L_ota_1_31_signed_user_2112020.2112020.2112020.zip
            Di2.1L_ota_3_33_signed_user_2105260.2105100.2105180.zip
            Di2.1L_ota_4_34_signed_user_2108190.2108190.2108190.zip
            Di2.1L_ota_4_signed_user_2104130.2104130.zip
            Di2.1L_ota_6_36_signed_user_2110300.2110090.2110310.zip
            Di2.1L_ota_6_36_signed_user_2112060.2111220.2111220.zip
            Di2.1L_SOP210823_ota_4_34_signed_user_2210210.2108190.2108190.zip
```

https://github.com/BYDcar/BYDPackagesByChip2
```
└─Di3
    ├─13.x芯片组
    │  ├─3.0UI
    │  │      Di3.0_13.1.18.2110230.1.13.2.1.2110136.2.13.2.2.2110136.2.zip
    │  │      Di3.0_13.1.7.2108180.1_0.zip
    │  │      Di3.0_13.1.7.2109290.1_0.zip
    │  │      Di3.0_13.1.7.2109220.1_0.zip
    │  │      Di3.0_13.1.7.2111181.1_1.zip
    │  │      di3.0_13.1.7.2201130.1_0.zip
    │  │      Di3.0_13.1.7.2204050.1_1.zip
    │  │      Di3.0_13.1.7.2204051.1_0.zip
    │  │      Di3.0_13.1.7.2205262.1_0.zip
    │  │      Di3.0_13.1.7.2205265.1_0.zip
    │  │      Di3.0_13.1.7.2207251.1_5.zip
    │  │      Di3.0_13.1.7.2207252.1_0.zip
    │  │      Di3.0_13.1.7.2209031.1_0.zip
    │  │      Di3.0_13.1.7.2209032.1_0.zip
    │  │      Di3.0_13.1.7.2211100.1_0.zip
    │  │      Di3.0_13.1.7.2211200.1_0.zip
    │  │
    │  └─4.0UI
    │          Di3.0_13.1.22.2112070.1_1.zip
    │          di3.0_13.1.22.2112210.1_1.zip
    │          Di3.0_13.1.22.2201110.1_0.zip
    │          di3.0_13.1.22.2202080.1_0.zip
    │          di3.0_13.1.22.2202081.1_0.zip
    │          Di3.0_13.1.22.2202081.1_1.zip
    │          Di3.0_13.1.22.2204060.1_0.zip
    │          Di3.0_13.1.22.2205260.1_1.zip
    │          Di3.0_13.1.22.2205262.1_0.zip
    │          Di3.0_13.1.22.2207200.1_0.zip
    │          Di3.0_13.1.22.2209200.1_0.zip
    │          Di3.0_13.1.22.2209201.1_0.zip
    │          Di3.0_13.1.22.2209203.1_0.zip
    │          Di3.0_13.1.22.2209205.1_0.zip
    │          Di3.0_13.1.22.2211166.1_0.zip
    │          Di3.0_13.1.22.2212160.1_0.zip
    │
    └─15.x芯片组
        ├─3.0UI
        │      Di3.0_15.1.7.2112200.1_1.zip
        │      Di3.0_15.1.7.2201130.1_1.zip
        │      Di3.0_15.1.7.2204050.1_0.zip
        │      Di3.0_15.1.7.2205262.1_0.zip
        │      Di3.0_15.1.7.2209031.1_0.zip
        │      Di3.0_15.1.7.2209032.1_0.zip
        │      Di3.0_15.1.7.2211200.1_0.zip
        │
        ├─4.0UI
        └─EV车型
                Di3.0_15.1.28.2206140.1.15.2.6.2206156.2.zip
                Di3.0_15.1.28.2209270.1.15.2.6.2209226.2.zip
                Di3.0_15.1.9.2109140.1.15.2.6.2109070.2.zip
```


https://github.com/BYDcar/BYDPackagesByChip3
```
├─Di4
│  ├─16.x芯片组
│  │  │  Di4.0_16.1.18.2203180.1.16.2.2.2203190.2.16.3.2.2203190.2.zip
│  │  │  Di4.0_16.1.4.2112030.1.16.2.2.2112230.2.zip
│  │  │
│  │  └─带16.x芯片组的17.x刷机包
│  │          Di4.0_17.1.14.2206040.1_0.zip
│  │          Di4.0_17.1.14.2210283.1_0.zip
│  │          Di4.0_17.1.17.2202280.1_0.zip
│  │
│  ├─17.x芯片组
│  │      Di4.0_17.1.14.2206040.1_0.zip
│  │      Di4.0_17.1.14.2210130.1_0.zip
│  │      Di4.0_17.1.14.2210283.1_0.zip
│  │      Di4.0_17.1.17.2202280.1_0.zip
│  │
│  └─21.x芯片组
│          Di4.0_1for2_21.1.10.2208030.1_0.zip
│          Di4.0_1for2_21.1.14.2301030.1_1.zip
│          Di4.0_1for2_21.1.2.2204060.1_0.zip
│          Di4.0_1for2_21.1.2.2206010.1_2.zip
│          Di4.0_1for2_21.1.2.2208160.1_0.zip
│          Di4.0_1for2_21.1.2.2208230.1_2.zip
│          Di4.0_1for2_21.1.2.2208231.1_2.zip
│          Di4.0_1for2_21.1.2.2209230.1_0.zip
│          Di4.0_1for2_21.1.2.2210283.1_0.zip
│          Di4.0_1for2_21.1.2.2210284.1_1.zip
│          Di4.0_1for2_21.1.2.2212013.1_0.zip
│          Di4.0_1for2_21.1.2.2212080.1_0（唐DMP）.zip
│          Di4.0_1for2_21.1.2.2212080.1_0（汉DMP、汉DM-i、汉EV22款）.zip
│          Di4.0_1for2_21.1.2.2212080.1_3.zip
│          Di4.0_1for2_21.1.7.2206110.1_3.zip
│
└─Di5
    └─23.x芯片组
            Di5.0_23.1.2.2209151.1.23.2.2.2209151.2.zip
            Di5.0_23.1.2.2209156.1.23.2.2.2209152.2.zip
```


## 按车型
我得到的文件里另一部分是按车型分类的，原本准备上传但是经过对比文件的hash发现和上面按车机芯片分类的文件是一样的，所以这里仅把目录列出来就不上传了。按车机芯片文件的hash在`filehash-bychip.txt`里，按车型文件的hash在`filehash-bymodel.txt`文件里，可以根据hash从上面的仓库里选择文件下载。

```
├─海洋系列
│  ├─护卫舰07
│  │      Di4.0_1for2_21.1.2.2212013.1_0.zip
│  │
│  ├─海豚
│  │      Di3.0_13.1.22.2205262.1_0.zip
│  │      Di3.0_13.1.22.2207200.1_0.zip
│  │      Di3.0_13.1.22.2211166.1_0.zip
│  │
│  ├─海豹
│  │      Di4.0_1for2_21.1.14.2301030.1_1.zip
│  │      Di4.0_1for2_21.1.2.2209230.1_0.zip
│  │      Di4.0_1for2_21.1.2.2210284.1_1.zip
│  │      Di4.0_1for2_21.1.2.2212080.1_3.zip
│  │
│  ├─海鸥
│  └─驱逐舰05
│      ├─12.8英寸旋转屏pad（三代Dilink）
│      │      Di3.0_13.1.22.2207200.1_0.zip
│      │
│      └─15.6寸旋转屏pad（四代Dilink）
│              Di4.0_17.1.14.2206040.1_0.zip
│              Di4.0_17.1.17.2202280.1_0.zip
│
└─腾势
    └─D9
            Di5.0_23.1.2.2209151.1.23.2.2.2209151.2.zip
            Di5.0_23.1.2.2209156.1.23.2.2.2209152.2.zip
```

```
└─汉
    ├─混动车型
    │  └─汉DM
    │          Di2L_3.0UI_20191225_ota_24_user_2209160.2209090.zip
    │          Di3.0_15.1.7.2112200.1_1.zip
    │          Di3.0_15.1.7.2204050.1_0.zip
    │          Di3.0_15.1.7.2205262.1_0.zip
    │          Di3.0_15.1.7.2209031.1_0.zip
    │          Di3.0_15.1.7.2211200.1_0.zip
    │          教程.pptx
    │
    ├─纯电车型
    │  ├─汉EV
    │  │      Di2.1L_ota_1_31_signed_user_2112020.2112020.2112020.zip
    │  │      Di2L_3.0UI_20191225_ota_25_user_2111260.2110090.zip
    │  │      Di2L_3.0UI_20191225_ota_25_user_2209160.2209090.zip
    │  │      Di3.0_15.1.7.2112200.1_1.zip
    │  │      Di3.0_15.1.7.2204050.1_0.zip
    │  │      Di3.0_15.1.7.2205262.1_0.zip
    │  │      Di3.0_15.1.7.2209031.1_0.zip
    │  │      Di3.0_15.1.7.2211200.1_0.zip
    │  │      Di4.0_16.1.18.2203180.1.16.2.2.2203190.2.16.3.2.2203190.2.zip
    │  │      Di4.0_16.1.4.2112030.1.16.2.2.2112230.2.zip
    │  │      Di4.0_17.1.14.2210283.1_0.zip
    │  │      教程.pptx
    │  │
    │  └─汉EV 22款
    │          Di4.0_1for2_21.1.10.2208030.1_0.zip
    │          Di4.0_1for2_21.1.2.2208230.1_2.zip
    │          Di4.0_1for2_21.1.2.2208231.1_2.zip
    │          Di4.0_1for2_21.1.2.2210283.1_0.zip
    │          Di4.0_1for2_21.1.2.2212080.1_0.zip
    │
    └─超级混动车型
        ├─汉DM-i
        │      Di4.0_1for2_21.1.10.2208030.1_0.zip
        │      Di4.0_1for2_21.1.2.2208230.1_2.zip
        │      Di4.0_1for2_21.1.2.2208231.1_2.zip
        │      Di4.0_1for2_21.1.2.2210283.1_0.zip
        │      Di4.0_1for2_21.1.2.2212080.1_0.zip
        │
        └─汉DM-p
                Di4.0_1for2_21.1.2.2208231.1_2.zip
                Di4.0_1for2_21.1.2.2210283.1_0.zip
                Di4.0_1for2_21.1.2.2212080.1_0.zip
```

```
└─秦
    ├─混动车型
    ├─燃油车型
    │  ├─全新秦_燃油版
    │  │      Di2L_ota_23_signed_user_2012230.2012070.zip
    │  │
    │  ├─秦Pro
    │  │      Di2.1L_ota_6_36_signed_user_2112060.2111220.2111220.zip
    │  │      Di2L_0929_0305_ota_27_signed_user_2006180.2006118.zip
    │  │      VP128_1.36.2005220.5.2005229.zip
    │  │
    │  └─秦Pro_燃油
    ├─纯电车型
    │  ├─全新秦EV
    │  │  │  Di2.1L_ota_3_33_signed_user_2105260.2105100.2105180.zip
    │  │  │  Di2L_ota_22_signed_user_2111050.2112140.zip
    │  │  │
    │  │  └─多媒体系统（非dilink）
    │  │          HDE EMEA E2 E3多媒体系统更新程序更新作业指导书.doc
    │  │          MX9S-HDE8寸多媒体U盘升级包V5.0.zip
    │  │          MX9SC-HDE8寸多媒体U盘升级包V5.0.zip
    │  │          更新失败补救程序.rar
    │  │
    │  ├─秦PLUS EV
    │  │      Di3.0_13.1.7.2111181.1_1.zip
    │  │      Di3.0_13.1.7.2204050.1_1.zip
    │  │      Di3.0_13.1.7.2205262.1_0.zip
    │  │      Di3.0_13.1.7.2207252.1_0.zip
    │  │      Di3.0_13.1.7.2209031.1_0.zip
    │  │      Di3.0_13.1.7.2209032.1_0.zip
    │  │      Di3.0_13.1.7.2211200.1_0.zip
    │  │
    │  └─秦Pro_EV
    │          Di2.1L_ota_6_36_signed_user_2110300.2110090.2110310.zip
    │          Di2L_0929_0305_ota_28_signed_user_2006180.2006118.zip
    │          VP128_1.36.2005220.2.2005229.zip
    │          VP128_1.36.2106220.9.2107060.zip
    │
    └─超级混动车型
        ├─秦Plus DM-i（2021款）
        │  │  Di3.0_13.1.7.2111181.1_1.zip
        │  │  di3.0_13.1.7.2201130.1_0.zip
        │  │  Di3.0_13.1.7.2204050.1_1.zip
        │  │  Di3.0_13.1.7.2205262.1_0.zip
        │  │  Di3.0_13.1.7.2207252.1_0.zip
        │  │  Di3.0_13.1.7.2209031.1_0.zip
        │  │  Di3.0_13.1.7.2209032.1_0.zip
        │  │  Di3.0_13.1.7.2211200.1_0.zip
        │  │
        │  └─2021款 DM-i 55KM 尊贵型
        │          Di2.1L_canfd_with2in1_SOP_ota_5_signed_user_2211180.2211180.zip
        │
        └─秦Plus DM-i（2023款）
            ├─120KM旗舰型智能选装包(21.1.2.xxx)
            ├─55KM尊荣型120KM尊贵型(13.1.22 xx)
            ├─55KM尊贵型(26.1. .xxx)
            └─HA2HAA-20型120KM旗舰型(81.2.xxx)
```

```
└─宋
    ├─混动车型
    │  ├─宋DM
    │  │      Di2UL-1_4.1.3.2111240.1.4.2_3.1.2111240.2.4.6_7.1.2111240.2.zip
    │  │      VP128_1.18.1912190.6.1911270.zip
    │  │
    │  ├─宋MAX DM
    │  │      VP128_1.37.2011060.6.2010220.zip
    │  │
    │  └─宋Pro_DM
    │          Di2L_ota_21_signed_user_2103120.201207.zip
    │          Di2UL-7_4.1.1.2108100.1.4.2_3.7.2108040.2.4.6_7.7.2108040.2.zip
    │          VP128_1.38.2103120.14.2103090.zip
    │
    ├─燃油车型
    │  ├─宋MAX
    │  │  └─12.8寸旋转屏pad（一代Dilink）
    │  │          VP128_1.37.2011060.7.2010220.zip
    │  │
    │  ├─宋MAX升级版
    │  │  │  Di2.1L_SOP210823_ota_4_34_signed_user_2210210.2108190.2108190.zip
    │  │  │
    │  │  ├─10.1寸旋转屏pad（Dilink 2.1）
    │  │  │      Di2.1L_ota_4_signed_user_2104130.2104130.zip
    │  │  │
    │  │  └─10.1寸旋转屏pad（Dilink 2.2）
    │  │          Di2UL-1_4.1.1.2110220.1.4.2_3.1.2109240.2.4.6_7.1.2109240.1.zip
    │  │
    │  ├─宋PLUS 燃油
    │  │      Di2UL-4_4.1.3.2204070.1.4.2_3.4.2204040.2.4.6_7.4.2204040.2.zip
    │  │
    │  ├─宋Pro_燃油版
    │  │      Di2UL-3_4.1.7.2109240.1.4.4_5.3.2109240.2.4.8_9.3.2109240.2.zip
    │  │
    │  ├─宋_燃油版_18款
    │  │      Di2.1L_ota_4_34_signed_user_2108190.2108190.2108190.zip
    │  │
    │  ├─宋燃油版
    │  │      Di2.1L_SOP210823_ota_4_34_signed_user_2210210.2108190.2108190.zip
    │  │
    │  └─第二代宋Pro
    │          Di2UL-3_4.1.7.2109240.1.4.4_5.3.2109240.2.4.8_9.3.2109240.2.zip
    │
    ├─纯电车型
    │  ├─宋EV_18款
    │  │      VP128_1.18.1912190.10.1911270.zip
    │  │
    │  ├─宋MAX EV
    │  │  └─12.8寸旋转屏pad（一代dilink）
    │  │          VP128_1.36.2005220.3.2005229.zip
    │  │
    │  ├─宋PLUS EV
    │  │      Di3.0_15.1.7.2201130.1_1.zip
    │  │      Di3.0_15.1.7.2204050.1_0.zip
    │  │      Di3.0_15.1.7.2205262.1_0.zip
    │  │      Di3.0_15.1.7.2209031.1_0.zip
    │  │      Di3.0_15.1.7.2209032.1_0.zip
    │  │      Di3.0_15.1.7.2211200.1_0.zip
    │  │
    │  └─宋Pro_EV
    │          Di2L_ota_22_signed_user_2103120.201207.zip
    │          VP128_1.38.2103120.11.2103090.zip
    │
    └─超级混动车型
        ├─宋MAX DM-i
        │      Di3.0_13.1.22.2207200.1_0.zip
        │
        ├─宋Plus DM-i
        │      Di3.0_13.1.18.2110230.1.13.2.1.2110136.2.13.2.2.2110136.2.zip
        │      Di3.0_13.1.22.2212160.1_0.zip
        │      Di3.0_13.1.7.2109290.1_0.zip
        │      Di3.0_13.1.7.2111181.1_1.zip
        │      Di3.0_13.1.7.2205262.1_0.zip
        │      Di3.0_13.1.7.2205265.1_0.zip
        │      Di3.0_13.1.7.2207251.1_5.zip
        │      Di3.0_13.1.7.2209031.1_0.zip
        │      Di3.0_13.1.7.2209032.1_0.zip
        │      Di3.0_13.1.7.2211200.1_0.zip
        │
        ├─宋PLUS DM-i 5G
        │      Di4.0_17.1.14.2210130.1_0.zip
        │
        ├─宋Plus DM-i AWD
        │      di3.0_13.1.22.2112210.1_1.zip
        │      Di3.0_13.1.22.2205262.1_0.zip
        │      Di3.0_13.1.22.2209205.1_0.zip
        │
        ├─宋Plus DM-i（5G）
        │      Di4.0_17.1.14.2210130.1_0.zip
        │
        └─宋Pro DM-i
                Di3.0_13.1.22.2209205.1_0.zip
```

```
├─元
│  ├─燃油车型
│  │  └─元Pro
│  │      └─10.1寸旋转屏pad（三代Dilink）
│  │              Di3.0_15.1.7.2204050.1_0.zip
│  │
│  └─纯电车型
│      ├─元EV
│      │  ├─10.1寸旋转屏pad（一代Dilink）
│      │  │      VP128_1.38.2101090.13.2101090.zip
│      │  │
│      │  └─10.1寸旋转屏pad（二代Dilink）
│      │          Di2L_ota_31_signed_user_2012230.2012070.zip
│      │
│      └─元PLUS EV
│              Di3.0_13.1.22.2202080.1_0.zip
│              Di3.0_13.1.22.2205262.1_0.zip
│              Di3.0_13.1.22.2209200.1_0.zip
│
└─唐
    ├─混动车型
    │  ├─全新一代唐DM
    │  │      VP128_1.37.2010130.1.2009300.zip
    │  │
    │  └─全新一代唐DM（2021款）
    │          Di2L_3.0UI_20191225_20210715_ota_24_user_2108090.2107030.zip
    │          Di2L_3.0UI_20191225_ota_24_user_2210170.2209090.zip
    │          Di3.0_15.1.7.2211200.1_0.zip
    │
    ├─燃油车型
    │  ├─全新一代唐_燃油版
    │  │      VP128_1.36.2005220.2.2005229.zip
    │  │
    │  └─全新一代唐燃油（2021款）
    │          Di2L_3.0UI_20191225_20210715_ota_26_user_2108090.2107030.zip
    │
    ├─纯电车型
    │  ├─22款唐EV
    │  │      Di4.0_1for2_21.1.2.2208160.1_0.zip
    │  │      Di4.0_1for2_21.1.2.2212080.1_0.zip
    │  │
    │  ├─全新一代唐EV 2021
    │  │      Di2UL-5_4.1.3.2210140.1.4.2_3.5.2209280.2.4.6_7.5.2209280.2.zip
    │  │      Di3.0_15.1.28.2206140.1.15.2.6.2206156.2.zip
    │  │      Di3.0_15.1.28.2209270.1.15.2.6.2209226.2.zip
    │  │      Di3.0_15.1.7.2211200.1_0.zip
    │  │      Di3.0_15.1.9.2109140.1.15.2.6.2109070.2.zip
    │  │
    │  └─全新一代唐_纯电版
    │          VP128_1.37.2010130.1.2009300.zip
    │          VP128_1.49.2106220.3.2107060.zip
    │
    └─超级混动车型
        ├─22款唐DM-p
        │      Di4.0_1for2_21.1.2.2208160.1_0.zip
        │      Di4.0_1for2_21.1.2.2212080.1_0.zip
        │
        └─唐DM-i
                Di3.0_13.1.7.2108180.1_0.zip
                Di3.0_13.1.7.2109220.1_0.zip
                Di3.0_13.1.7.2111181.1_1.zip
                Di3.0_13.1.7.2204051.1_0.zip
                Di3.0_13.1.7.2205262.1_0.zip
                Di3.0_13.1.7.2211100.1_0.zip
                Di3.0_13.1.7.2211200.1_0.zip
```

---
# BYD maintenance manual and flashing information
BYD (Build Your Dream) Car Repair Manuals and Factory Images

# Maintenance manuals and flashing files for various models of BYD Auto
These Github repositories contain maintenance manuals and flashing materials for BYD cars. I need to research some BYD cars, and found that some websites on the Internet provide scattered maintenance manuals. I found that the maintenance manuals can be found on the BYD after-sales website http://lms. download from bydauto.com.cn/, flashing information can be downloaded from http://yunpan.byd.com.cn/, but you need the account of the dealer or repair shop to download. Then I found that Taobao Xianyu sold these materials, so I bought them all and shared them for free.

# Why share for free?
It is very troublesome to find some scattered information on the Internet. At present, the software and hardware ecology of automobiles is too closed. In terms of software, it is not like mobile phones and routers that can be flashed into third-party open source systems at will. In terms of hardware, there are not many modified and upgraded spare parts like 3D printers. Think about it, if the car can be flashed into the open source system, and the open source parts can be upgraded, it might be cool to realize functions that were not there before.

At present, some people abroad are researching on the modification and installation of assisted driving and automatic driving. For example, this video https://www.youtube.com/watch?v=Te4AhlRXnLw refits a 2005 old car with Tesla’s iBooster and installs it The open source auxiliary software openpilot (https://github.com/commaai/openpilot) is used to realize automatic driving. There are also some people who are studying the conversion of fuel vehicles into electric vehicles. For example, this video https://www.youtube.com/watch?v=ZVtOss1U7_s converts an old Volkswagen Beetle into an electric vehicle. Therefore, I share these materials in order to promote research on various modifications and installations at home and abroad.

In addition, studying these may be of practical benefit. At present, the cheapest Qin PLUS DM-i 2023 model sold by BYD is 99,800 yuan. The low-end version does not include L2 assisted driving functions such as full-speed adaptive cruise. For full-speed adaptive cruise, there is only an extra 46,000 yuan to upgrade to the high-end version of 145,800 yuan. If you can make a few thousand yuan to upgrade the modified accessories for driving assistance, then the low-end version plus modified accessories will be very cost-effective.


# Large files are divided and compressed for upload
Because Github limits a single file to no more than 100M, a single push cannot exceed 2GB, and a single warehouse cannot exceed 100GB. So I divided and uploaded the large files (mainly the flashing package of the Android car and several maintenance manuals). I used https://github.com/sisl/GitHub-ForceLargeFiles to divide the large files and upload them. After the division It is a split package compressed by 7zip, you can manually decompress it with 7zip, or use the following code to automatically restore all files
```
git clone https://github.com/sisl/GitHub-ForceLargeFiles

segmentation
python .\GitHub-ForceLargeFiles\src\main.py --root_dir "C:\xxx\BYDRepairManual\"

recover
python .\GitHub-ForceLargeFiles\src\reverse.py --root_dir "C:\xxx\BYDRepairManual\"

```

# Domestic download speed may be slow
Because there are many files, each warehouse has dozens of GB, downloading in mainland China may be unstable.

First of all, you can try to download directly. If the network speed is good, you can download it quickly.

```
git clone https://github.com/BYDcar/BYDPackagesByChip1.git
```

Secondly, if the download speed is slow or easy to disconnect. You can try Github proxy, such as https://ghproxy.com/

Again, if downloading the entire warehouse is easy to disconnect, you can only download the required files. Refer to the method here Some tools can only download the specified folder https://stackoverflow.com/questions/7106012/download-a-single-folder-or-directory-from-a-github-repo

Finally, if you download the entire warehouse of dozens of GB, the git clone download may be disconnected at more than a dozen GB, and the disconnection cannot be resumed and can only be downloaded again. In this case, you can consider commit downloading one by one (or several A few commit downloads)

```
# Create an empty git repository locally
git init

# add a remote
git remote add origin https://github.com/BYDcar/BYDPackagesByChip1.git

# Pull a commit hash (the latter hash is copied from GitHub commits)
# Note: the full history up to this commit will be retrieved unless
# you limit it with '--depth=...' or '--shallow-since=...'
git fetch origin d0fcf97e634d670a34a36e71d2395064674c17a2

# Extract the git file
git reset --hard FETCH_HEAD

# Then pull the hash of the next commit (the following hash is copied from the GitHub commits, copy the next hash in order)
git fetch origin c638f4e1de4d61e2295665249d9854d63386e437

# Extract the git file again
git reset --hard FETCH_HEAD

and so on and on
 …

```

The files included in this series of libraries are as follows
# Maintenance manual, dashboard firmware, software and flashing tutorial:
https://github.com/BYDcar/BYDRepairManual

# Android car machine flash data
There are two types of search methods for car flashing packages, one is based on the chip version of the car controller, and the other is classified by model. Some of the packages in the two are the same, but the classification forms are different.

## According to the chip version of the car

https://github.com/BYDcar/BYDPackagesByChip1
```
├─Di1
│ VP128_1.18.1912190.10.1911270.zip
│ VP128_1.18.1912190.6.1911270.zip
│ VP128_1.18.1912190.7.1911270.zip
│ VP128_1.36.2004030.4.2004039.zip
│ VP128_1.36.2005220.2.2005229.zip
│ VP128_1.36.2005220.3.2005229.zip
│ VP128_1.36.2005220.5.2005229.zip
│ VP128_1.36.2106220.9.2107060.zip
│ VP128_1.37.2010130.1.2009300.zip
│ VP128_1.37.2011060.6.2010220.zip
│ VP128_1.37.2011060.7.2010220.zip
│ VP128_1.38.2101090.13.2101090.zip
│ VP128_1.38.2103120.11.2103090.zip
│ VP128_1.38.2103120.14.2103090.zip
│ VP128_1.38.2108300.15.210706.zip
│ VP128_1.49.2106220.2.2107060.zip
│ VP128_1.49.2106220.3.2107060.zip
│ VP128_1.50.2106240.7.2107060.zip
│ Model Upgrade Tutorial for First Generation Machines.docx
│ The first digit of version details is 1 for VP128, 2 for DL2L, 4 for DL2UL, and 5 for DL2.1L.txt
│
└─Di2
     │ The first digit of version details is 1 for VP128, 2 for DL2L, 4 for DL2UL, 5 for DL2.1L(20230106221045).txt
     │ The first digit of version details is 1 for VP128, 2 for DL2L, 4 for DL2UL, and 5 for DL2.1L.txt
     │
     ├─2.x Chipset
     │ ├─2.0 UI
     │ │ Di2L_0929_0305_ota_27_signed_user_2006180.2006118.zip
     │ │ Di2L_0929_0305_ota_28_signed_user_2006180.2006118.zip
     │ │ Di2L_ota_21_signed_user_2103120.201207.zip
     │ │ Di2L_ota_22_signed_user_2103120.201207.zip
     │ │ Di2L_ota_22_signed_user_2111050.2112140.zip
     │ │ Di2L_ota_23_signed_user_2012230.2012070.zip
     │ │ Di2L_ota_31_signed_user_2012230.2012070.zip
     │ │
     │ └─3.0 UI
     │ Di2L_3.0UI_20191225_20210715_ota_24_user_2108090.2107030.zip
     │ Di2L_3.0UI_20191225_20210715_ota_26_user_2108090.2107030.zip
     │ Di2L_3.0UI_20191225_ota_24_user_2209160.2209090.zip
     │ Di2L_3.0UI_20191225_ota_24_user_2210170.2209090.zip
     │ Di2L_3.0UI_20191225_ota_25_user_2111260.2110090.zip
     │ Di2L_3.0UI_20191225_ota_25_user_2209160.2209090.zip
     │
     ├─4.x Chipset
     │ Di2UL-1_4.1.1.2110220.1.4.2_3.1.2109240.2.4.6_7.1.2109240.1.zip
     │ Di2UL-1_4.1.3.2111240.1.4.2_3.1.2111240.2.4.6_7.1.2111240.2.zip
     │ Di2UL-3_4.1.7.2109240.1.4.4_5.3.2109240.2.4.8_9.3.2109240.2.zip
     │ Di2UL-4_4.1.3.2204070.1.4.2_3.4.2204040.2.4.6_7.4.2204040.2.zip
     │ Di2UL-5_4.1.3.2210140.1.4.2_3.5.2209280.2.4.6_7.5.2209280.2(20230106224053).zip
     │ Di2UL-5_4.1.3.2210140.1.4.2_3.5.2209280.2.4.6_7.5.2209280.2.zip
     │ Di2UL-7_4.1.1.2108100.1.4.2_3.7.2108040.2.4.6_7.7.2108040.2.zip
     │
     └─5.x Chipset Di2.1L_canfd_with2in1_SOP_ota_5_signed_user_2211180.2211180.zip
             Di2.1L_ota_1_31_signed_user_2112020.2112020.2112020.zip
             Di2.1L_ota_3_33_signed_user_2105260.2105100.2105180.zip
             Di2.1L_ota_4_34_signed_user_2108190.2108190.2108190.zip
             Di2.1L_ota_4_signed_user_2104130.2104130.zip
             Di2.1L_ota_6_36_signed_user_2110300.2110090.2110310.zip
             Di2.1L_ota_6_36_signed_user_2112060.2111220.2111220.zip
             Di2.1L_SOP210823_ota_4_34_signed_user_2210210.2108190.2108190.zip
```

https://github.com/BYDcar/BYDPackagesByChip2
```
└─Di3
     ├─13.x Chipset
     │ ├─3.0UI
     │ │ Di3.0_13.1.18.2110230.1.13.2.1.2110136.2.13.2.2.2110136.2.zip
     │ │ Di3.0_13.1.7.2108180.1_0.zip
     │ │ Di3.0_13.1.7.2109290.1_0.zip
     │ │ Di3.0_13.1.7.2109220.1_0.zip
     │ │ Di3.0_13.1.7.2111181.1_1.zip
     │ │ di3.0_13.1.7.2201130.1_0.zip
     │ │ Di3.0_13.1.7.2204050.1_1.zip
     │ │ Di3.0_13.1.7.2204051.1_0.zip
     │ │ Di3.0_13.1.7.2205262.1_0.zip
     │ │ Di3.0_13.1.7.2205265.1_0.zip
     │ │ Di3.0_13.1.7.2207251.1_5.zip
     │ │ Di3.0_13.1.7.2207252.1_0.zip
     │ │ Di3.0_13.1.7.2209031.1_0.zip
     │ │ Di3.0_13.1.7.2209032.1_0.zip
     │ │ Di3.0_13.1.7.2211100.1_0.zip
     │ │ Di3.0_13.1.7.2211200.1_0.zip
     │ │
     │ └─4.0UI
     │ Di3.0_13.1.22.2112070.1_1.zip
     │ di3.0_13.1.22.2112210.1_1.zip
     │ Di3.0_13.1.22.2201110.1_0.zip
     │ di3.0_13.1.22.2202080.1_0.zip
     │ di3.0_13.1.22.2202081.1_0.zip
     │ Di3.0_13.1.22.2202081.1_1.zip
     │ Di3.0_13.1.22.2204060.1_0.zip
     │ Di3.0_13.1.22.2205260.1_1.zip
     │ Di3.0_13.1.22.2205262.1_0.zip
     │ Di3.0_13.1.22.2207200.1_0.zip
     │ Di3.0_13.1.22.2209200.1_0.zip
     │ Di3.0_13.1.22.2209201.1_0.zip
     │ Di3.0_13.1.22.2209203.1_0.zip
     │ Di3.0_13.1.22.2209205.1_0.zip
     │ Di3.0_13.1.22.2211166.1_0.zip
     │ Di3.0_13.1.22.2212160.1_0.zip
     │
     └─15.x Chipset
         ├─3.0UI
         │ Di3.0_15.1.7.2112200.1_1.zip
         │ Di3.0_15.1.7.2201130.1_1.zip
         │ Di3.0_15.1.7.2204050.1_0.zip
         │ Di3.0_15.1.7.2205262.1_0.zip
         │ Di3.0_15.1.7.2209031.1_0.zip
         │ Di3.0_15.1.7.2209032.1_0.zip
         │ Di3.0_15.1.7.2211200.1_0.zip
         │
         ├─4.0UI
         └─EV model
                 Di3.0_15.1.28.2206140.1.15.2.6.2206156.2.zip
                 Di3.0_15.1.28.2209270.1.15.2.6.2209226.2.zip
                 Di3.0_15.1.9.2109140.1.15.2.6.2109070.2.zip
```


https://github.com/BYDcar/BYDPackagesByChip3
```
├─Di4
│ ├─16.x Chipset
│ │ │ Di4.0_16.1.18.2203180.1.16.2.2.2203190.2.16.3.2.2203190.2.zip
│ │ │ Di4.0_16.1.4.2112030.1.16.2.2.2112230.2.zip
│ │ │
│ │ └─17.x flashing package with 16.x chipset
│ │ Di4.0_17.1.14.2206040.1_0.zip
│ │ Di4.0_17.1.14.2210283.1_0.zip
│ │ Di4.0_17.1.17.2202280.1_0.zip
│ │
│ ├─17.x Chipset
│ │ Di4.0_17.1.14.2206040.1_0.zip
│ │ Di4.0_17.1.14.2210130.1_0.zip
│ │ Di4.0_17.1.14.2210283.1_0.zip
│ │ Di4.0_17.1.17.2202280.1_0.zip
│ │
│ └─21.x Chipset
│ Di4.0_1for2_21.1.10.2208030.1_0.zip
│ Di4.0_1for2_21.1.14.2301030.1_1.zip
│ Di4.0_1for2_21.1.2.2204060.1_0.zip
│ Di4.0_1for2_21.1.2.2206010.1_2.zip
│ Di4.0_1for2_21.1.2.2208160.1_0.zip
│ Di4.0_1for2_21.1.2.2208230.1_2.zip
│ Di4.0_1for2_21.1.2.2208231.1_2.zip
│ Di4.0_1for2_21.1.2.2209230.1_0.zip
│ Di4.0_1for2_21.1.2.2210283.1_0.zip
│ Di4.0_1for2_21.1.2.2210284.1_1.zip
│ Di4.0_1for2_21.1.2.2212013.1_0.zip
│ Di4.0_1for2_21.1.2.2212080.1_0 (Tang DMP).zip
│ Di4.0_1for2_21.1.2.2212080.1_0 (Han DMP, Han DM-i, Han EV22).zip
│ Di4.0_1for2_21.1.2.2212080.1_3.zip
│ Di4.0_1for2_21.1.7.2206110.1_3.zip
│
└─Di5
     └─23.x Chipset
             Di5.0_23.1.2.2209151.1.23.2.2.2209151.2.zip
             Di5.0_23.1.2.2209156.1.23.2.2.2209152.2.zip
```


## By car model
The other part of the file I got is classified by model. I was going to upload it, but after comparing the hash of the file, I found that it is the same as the file classified by car chip above, so I just list the directory here and don’t upload it. The hash of the car chip file is in `filehash-bychip.txt`, and the hash of the model file is in the `filehash-bymodel.txt` file. You can choose the file to download from the above warehouse according to the hash.

```
├─Ocean series
│ ├─Frigate 07
│ │ Di4.0_1for2_21.1.2.2212013.1_0.zip
│ │
│ ├─Dolphins
│ │ Di3.0_13.1.22.2205262.1_0.zip
│ │ Di3.0_13.1.22.2207200.1_0.zip
│ │ Di3.0_13.1.22.2211166.1_0.zip
│ │
│ ├─seal
│ │ Di4.0_1for2_21.1.14.2301030.1_1.zip
│ │ Di4.0_1for2_21.1.2.2209230.1_0.zip
│ │ Di4.0_1for2_21.1.2.2210284.1_1.zip
│ │ Di4.0_1for2_21.1.2.2212080.1_3.zip
│ │
│ ├─Seagull
│ └─Destroyer 05
│ ├─12.8-inch rotating screen pad (three generations of Dilink)
│ │ Di3.0_13.1.22.2207200.1_0.zip
│ │
│ └─15.6-inch rotating screen pad (fourth generation Dilink)
│ Di4.0_17.1.14.2206040.1_0.zip
│ Di4.0_17.1.17.2202280.1_0.zip
│
└─Teng potential
     └─D9
             Di5.0_23.1.2.2209151.1.23.2.2.2209151.2.zip
             Di5.0_23.1.2.2209156.1.23.2.2.2209152.2.zip
```

```
└─Chinese
     ├─Hybrid models
     │ └─Han DM
     │ Di2L_3.0UI_20191225_ota_24_user_2209160.2209090.zip
     │ Di3.0_15.1.7.2112200.1_1.zip
     │ Di3.0_15.1.7.2204050.1_0.zip
     │ Di3.0_15.1.7.2205262.1_0.zip
     │ Di3.0_15.1.7.2209031.1_0.zip
     │ Di3.0_15.1.7.2211200.1_0.zip
     │ Tutorial.pptx
     │
     ├─Pure electric vehicle
     │ ├─Han EV
     │ │ Di2.1L_ota_1_31_signed_user_2112020.2112020.2112020.zip
     │ │ Di2L_3.0UI_20191225_ota_25_user_2111260.2110090.zip
     │ │ Di2L_3.0UI_20191225_ota_25_user_2209160.2209090.zip
     │ │ Di3.0_15.1.7.2112200.1_1.zip
     │ │ Di3.0_15.1.7.2204050.1_0.zip
     │ │ Di3.0_15.1.7.2205262.1_0.zip
     │ │ Di3.0_15.1.7.2209031.1_0.zip
     │ │ Di3.0_15.1.7.2211200.1_0.zip
     │ │ Di4.0_16.1.18.2203180.1.16.2.2.2203190.2.16.3.2.2203190.2.zip
     │ │ Di4.0_16.1.4.2112030.1.16.2.2.2112230.2.zip
     │ │ Di4.0_17.1.14.2210283.1_0.zip
     │ │ Tutorial.pptx
     │ │
     │ └─Han EV 22 models
     │ Di4.0_1for2_21.1.10.2208030.1_0.zip
     │ Di4.0_1for2_21.1.2.2208230.1_2.zip
     │ Di4.0_1for2_21.1.2.2208231.1_2.zip
     │ Di4.0_1for2_21.1.2.2210283.1_0.zip
     │ Di4.0_1for2_21.1.2.2212080.1_0.zip
     │
     └─Super Hybrid
         ├─Chinese DM-i
         │ Di4.0_1for2_21.1.10.2208030.1_0.zip
         │ Di4.0_1for2_21.1.2.2208230.1_2.zip
         │ Di4.0_1for2_21.1.2.2208231.1_2.zip
         │ Di4.0_1for2_21.1.2.2210283.1_0.zip
         │ Di4.0_1for2_21.1.2.2212080.1_0.zip
         │
         └─Han DM-p
                 Di4.0_1for2_21.1.2.2208231.1_2.zip
                 Di4.0_1for2_21.1.2.2210283.1_0.zip
                 Di4.0_1for2_21.1.2.2212080.1_0.zip
```

```
└─Qin
     ├─Hybrid models
     ├─fuel vehicle
     │ ├─New Qin_fuel version
     │ │ Di2L_ota_23_signed_user_2012230.2012070.zip
     │ │
     │ ├─Qin Pro
     │ │ Di2.1L_ota_6_36_signed_user_2112060.2111220.2111220.zip
     │ │ Di2L_0929_0305_ota_27_signed_user_2006180.2006118.zip
     │ │ VP128_1.36.2005220.5.2005229.zip
     │ │
     │ └─Qin Pro_Fuel
     ├─Pure electric vehicle
     │ ├─New Qin EV
     │ │ │ Di2.1L_ota_3_33_signed_user_2105260.2105100.2105180.zip
     │ │ │ Di2L_ota_22_signed_user_2111050.2112140.zip
     │ │ │
     │ │ └─Multimedia system (not dilink)
     │ │ HDE EMEA E2 E3 multimedia system update program update operation guide.doc
     │ │ MX9S-HDE 8-inch multimedia U disk upgrade package V5.0.zip
     │ │ MX9SC-HDE 8-inch multimedia U disk upgrade package V5.0.zip
     │ │ Update failure remedy program.rar
     │ │
     │ ├─QIN PLUS EV
     │ │ Di3.0_13.1.7.2111181.1_1.zip
     │ │ Di3.0_13.1.7.2204050.1_1.zip
     │ │ Di3.0_13.1.7.2205262.1_0.zip
     │ │ Di3.0_13.1.7.2207252.1_0.zip
     │ │ Di3.0_13.1.7.2209031.1_0.zip
     │ │ Di3.0_13.1.7.2209032.1_0.zip
     │ │ Di3.0_13.1.7.2211200.1_0.zip
     │ │
     │ └─Qin Pro_EV
     │ Di2.1L_ota_6_36_signed_user_2110300.2110090.2110310.zip
     │ Di2L_0929_0305_ota_28_signed_user_2006180.2006118.zip
     │ VP128_1.36.2005220.2.2005229.zip
     │ VP128_1.36.2106220.9.2107060.zip
     │
     └─Super Hybrid
         ├─Qin Plus DM-i (2021 model)
         │ │ Di3.0_13.1.7.2111181.1_1.zip
         │ │ di3.0_13.1.7.2201130.1_0.zip
         │ │ Di3.0_13.1.7.2204050.1_1.zip
         │ │ Di3.0_13.1.7.2205262.1_0.zip
         │ │ Di3.0_13.1.7.2207252.1_0.zip
         │ │ Di3.0_13.1.7.2209031.1_0.zip
         │ │ Di3.0_13.1.7.2209032.1_0.zip
         │ │ Di3.0_13.1.7.2211200.1_0.zip
         │ │
         │ └─2021 DM-i 55KM Premium
         │ Di2.1L_canfd_with2in1_SOP_ota_5_signed_user_2211180.2211180.zip
         │
         └─Qin Plus DM-i (2023 model)
             ├─120KM Flagship Smart Optional Package (21.1.2.xxx)
             ├─55KM honor type 120KM honor type (13.1.22 xx)
             ├─55KM premium type (26.1. .xxx)
             └─HA2HAA-20 120KM Flagship (81.2.xxx)
```

```
└─Song
     ├─Hybrid models
     │ ├─Song DM
     │ │ Di2UL-1_4.1.3.2111240.1.4.2_3.1.2111240.2.4.6_7.1.2111240.2.zip
     │ │ VP128_1.18.1912190.6.1911270.zip
     │ │
     │ ├─Song MAX DM
     │ │ VP128_1.37.2011060.6.2010220.zip
     │ │
     │ └─Song Pro_DM
     │ Di2L_ota_21_signed_user_2103120.201207.zip
     │ Di2UL-7_4.1.1.2108100.1.4.2_3.7.2108040.2.4.6_7.7.2108040.2.zip
     │ VP128_1.38.2103120.14.2103090.zip
     │
     ├─fuel vehicle
     │ ├─Song MAX
     │ │ └─12.8-inch rotating screen pad (first generation Dilink)
     │ │ VP128_1.37.2011060.7.2010220.zip
     │ │
     │ ├─Song MAX upgrade version
     │ │ │ Di2.1L_SOP210823_ota_4_34_signed_user_2210210.2108190.2108190.zip
     │ │ │
     │ │ ├─10.1 inch rotating screen pad (Dilink 2.1)
     │ │ │ Di2.1L_ota_4_signed_user_2104130.2104130.zip
     │ │ │
     │ │ └─10.1 inch rotating screen pad (Dilink 2.2)
     │ │ Di2UL-1_4.1.1.2110220.1.4.2_3.1.2109240.2.4.6_7.1.2109240.1.zip
     │ │
     │ ├─Song PLUS Fuel
     │ │ Di2UL-4_4.1.3.2204070.1.4.2_3.4.2204040.2.4.6_7.4.2204040.2.zip
     │ │
     │ ├─Song Pro_fuel version
     │ │ Di2UL-3_4.1.7.2109240.1.4.4_5.3.2109240.2.4.8_9.3.2109240.2.zip
     │ │
     │ ├─Song_fuel version_18 styles
     │ │ Di2.1L_ota_4_34_signed_user_2108190.2108190.2108190.zip
     │ │
     │ ├─Song Fuel Version
     │ │ Di2.1L_SOP210823_ota_4_34_signed_user_2210210.2108190.2108190.zip
     │ │
     │ └─Second Generation Song Pro
     │ Di2UL-3_4.1.7.2109240.1.4.4_5.3.2109240.2.4.8_9.3.2109240.2.zip
     │
     ├─Pure electric vehicle
     │ ├─Song EV_18
     │ │ VP128_1.18.1912190.10.1911270.zip
     │ │
     │ ├─Song MAX EV
     │ │ └─12.8-inch rotating screen pad (first generation dilink)
     │ │ VP128_1.36.2005220.3.2005229.zip
     │ │
     │ ├─Song PLUS EV
     │ │ Di3.0_15.1.7.2201130.1_1.zip
     │ │ Di3.0_15.1.7.2204050.1_0.zip
     │ │ Di3.0_15.1.7.2205262.1_0.zip
     │ │ Di3.0_15.1.7.2209031.1_0.zip
     │ │ Di3.0_15.1.7.2209032.1_0.zip
     │ │ Di3.0_15.1.7.2211200.1_0.zip
     │ │
     │ └─Song Pro_EV
     │ Di2L_ota_22_signed_user_2103120.201207.zip
     │ VP128_1.38.2103120.11.2103090.zip
     │
     └─Super Hybrid
         ├─Song MAX DM-i
         │ Di3.0_13.1.22.2207200.1_0.zip
         │
         ├─Song Plus DM-i
         │ Di3.0_13.1.18.2110230.1.13.2.1.2110136.2.13.2.2.2110136.2.zip
         │ Di3.0_13.1.22.2212160.1_0.zip
         │ Di3.0_13.1.7.2109290.1_0.zip
         │ Di3.0_13.1.7.2111181.1_1.zip
         │ Di3.0_13.1.7.2205262.1_0.zip
         │ Di3.0_13.1.7.2205265.1_0.zip
         │ Di3.0_13.1.7.2207251.1_5.zip
         │ Di3.0_13.1.7.2209031.1_0.zip
         │ Di3.0_13.1.7.2209032.1_0.zip
         │ Di3.0_13.1.7.2211200.1_0.zip
         │
         ├─Song PLUS DM-i 5G
         │ Di4.0_17.1.14.2210130.1_0.zip
         │
         ├─Song Plus DM-i AWD
         │ di3.0_13.1.22.2112210.1_1.zip
         │ Di3.0_13.1.22.2205262.1_0.zip
         │ Di3.0_13.1.22.2209205.1_0.zip
         │
         ├─Song Plus DM-i (5G)
         │ Di4.0_17.1.14.2210130.1_0.zip
         │
         └─Song Pro DM-i
                 Di3.0_13.1.22.2209205.1_0.zip
```

```
├─yuan
│ ├─fuel vehicle
│ │ └─Yuan Pro
│ │ └─10.1-inch rotating screen pad (third generation Dilink)
│ │ Di3.0_15.1.7.2204050.1_0.zip
│ │
│ └─Pure electric vehicle
│ ├─Yuan EV
│ │ ├─10.1-inch rotating screen pad (first generation Dilink)
│ │ │ VP128_1.38.2101090.13.2101090.zip
│ │ │
│ │ └─10.1-inch rotating screen pad (second generation Dilink)
│ │ Di2L_ota_31_signed_user_2012230.2012070.zip
│ │
│ └─Yuan PLUS EV
│ Di3.0_13.1.22.2202080.1_0.zip
│ Di3.0_13.1.22.2205262.1_0.zip
│ Di3.0_13.1.22.2209200.1_0.zip
│
└─Don
     ├─Hybrid models
     │ ├─A new generation of Tang DM
     │ │ VP128_1.37.2010130.1.2009300.zip
     │ │
     │ └─New generation Tang DM (2021 model)
     │ Di2L_3.0UI_20191225_20210715_ota_24_user_2108090.2107030.zip
     │ Di2L_3.0UI_20191225_ota_24_user_2210170.2209090.zip
     │ Di3.0_15.1.7.2211200.1_0.zip
     │
     ├─fuel vehicle
     │ ├─The new generation of Tang_fuel version
     │ │ VP128_1.36.2005220.2.2005229.zip
     │ │
     │ └─New generation Tang fuel oil (2021 model)
     │ Di2L_3.0UI_20191225_20210715_ota_26_user_2108090.2107030.zip
     │
     ├─Pure electric vehicle
     │ ├─22 Tang EVs
     │ │ Di4.0_1for2_21.1.2.2208160.1_0.zip
     │ │ Di4.0_1for2_21.1.2.2212080.1_0.zip
     │ │
     │ ├─New generation Tang EV 2021
     │ │ Di2UL-5_4.1.3.2210140.1.4.2_3.5.2209280.2.4.6_7.5.2209280.2.zip
     │ │ Di3.0_15.1.28.2206140.1.15.2.6.2206156.2.zip
     │ │ Di3.0_15.1.28.2209270.1.15.2.6.2209226.2.zip
     │ │ Di3.0_15.1.7.2211200.1_0.zip
     │ │ Di3.0_15.1.9.2109140.1.15.2.6.2109070.2.zip
     │ │
     │ └─The new generation Tang_pure electric version
     │ VP128_1.37.2010130.1.2009300.zip
     │ VP128_1.49.2106220.3.2107060.zip
     │
     └─Super Hybrid
         ├─22 Tang DM-p
         │ Di4.0_1for2_21.1.2.2208160.1_0.zip
         │ Di4.0_1for2_21.1.2.2212080.1_0.zip
         │
         └─Don DM-i
                 Di3.0_13.1.7.2108180.1_0.zip
                 Di3.0_13.1.7.2109220.1_0.zip
                 Di3.0_13.1.7.2111181.1_1.zip
                 Di3.0_13.1.7.2204051.1_0.zip
                 Di3.0_13.1.7.2205262.1_0.zip
                 Di3.0_13.1.7.2211100.1_0.zip
                 Di3.0_13.1.7.2211200.1_0.zip
```