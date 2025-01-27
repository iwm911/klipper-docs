>[!TIP]
>SD卡烧录与USB烧录只需要使用其中一种烧录即可

>[!Warning]
>SD卡注意事项:
>容量必须不小于16GB 或 不大于128G TF 卡
>TF 卡的传输速度必须为 class10 级或 class10 级以上，建议使用闪迪等品牌的 TF 卡

## 烧录前的准备

**需要准备的东西：**

1. SD卡一张

2. 读卡器

3. 系统镜像

4. 工具软件请前往FLY官方群文件夹下载：Fly-Gemini系列；l 需要用到的软件有：balenaEtcher（fly群中文件名为系统镜像写入工具）、putty、WinSCP

5. [系统镜像](/introduction/downloadimg.md "点击即可跳转") 

**注：其他非FLY的上位机请勿使用FLY的专属镜像，否则会损坏上位机！！！**

**下载需要用到的工具和文件，国内用户请前往QQ群下载**

* [工具](https://drive.google.com/drive/folders/1llH-lq-WsbIdwkmLL51n3OHo5dNNpcPy)

## 2. 内存卡镜像烧录

1. 先安装好软件“balenaEtcher”，也可以用其他的(Win32DiskImager)等工具
2. SD卡插入读卡器，将读卡器插到电脑USB接口
3. 打开软件，点击“**Flash from file**”选择前面下载的系统镜像文件

<img src="../../images/boards/fly_pi/etcher.png" alt="etcher" style="zoom:80%;" />

4. 点击**“Select target**”选择SD卡，大小和SD卡容量差不多的就是，或进入资源管理器查看SD卡盘符

   <img src="../../images/boards/fly_pi/etcher2.png" alt="etcher2" style="zoom:80%;" />

   5. 点击“**Falsh**”,出现进度条及“**Falshing…**”时开始写入系统镜像到SD卡。等待大约十多分钟，等待写入完成。

      

   6. 至此已经完成FLY镜像的写入，但是请勿拔出内存卡，还需要修改boot盘中的FLY_config文件，具体修改方法请查看：[FLY_Config](/board/fly_pi/FLY_π_fly_config.md "点击即可跳转")

> [!Warning]
>
> 系统稍微完成后会有一个boot盘与一个win电脑无法识别的分区，请不要格式化！！
