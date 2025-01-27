

#  3. FLY_Config 的使用

* FLY-Config用来简化系统配置等，适用于Klipper全家桶，免去进入ssh写命令的麻烦
* 只能在FLY定制Armbian系统运行
* 对初学者友好
* 直接配置Klipper及周边

## 3.1 打开 FLY_Config

1. 如果您已经制作好SD卡，请使用读卡器连接到电脑。此时电脑应该会弹出资源管理器并且有一个“**可移动磁盘BOOT**” .如果未出现，请重新拔下 sd 卡，再插入电脑

   eMMc进入BOOT盘方法，请参考：[通过usb为emmc烧录系统镜像](/board/fly_pi/FLY_π_description1?id=_2-通过usb为emmc烧录系统镜像)

   ![open_boot](../../images/boards/fly_pi/open_boot.png)

   

2. 打开BOOT盘下的FLY-Config.conf

   ![open_flyconfig](../../images/boards/fly_pi/open_flyconfig.png)

## 3.2 可用配置

* 配置主板型号（仅限Gemini系列，其他系列默认即可）
* 配置WIFI
* 配置Klipperscreen
* 配置屏幕

## 3.3 连接WiFi

   找到WIFI配置，将WIFI处的flase改成true，并将WiFi名称和密码填写上，保存，插回上位机。等待几分钟后，进入路由器后台管理界面查看IP地址。
   ![connect_wifi](../../images/boards/fly_pi/connect_wifi.png)

> [!Warning]
>
> 系统启动后会将此wifi保存到系统，并且将**WiFi=true**修改为**WiFi=flase**

## 3.4 Klipperscreen的配置

![config1](../../images/boards/fly_pi/config1.png)

另外还需要指定使用的屏幕类型才能够正常使用！！！按下图中的提示修改为对应的配置即可。

![tft](../../images/boards/fly_pi/tft1.png)

* 请注意屏幕版本

<!-- tabs:start -->

### **FLY-MiniPad 电容屏版本**

* HDMI屏幕只需要修改Display此选项即可

![tft](../../images/boards/fly_mini_pad/MiniPad.png)

### **FLY-MiniPad 电阻屏**

![tft1](../../images/boards/fly_mini_pad/R.png)

<!-- tabs:end -->

* TFT屏幕旋转只能选择**90**或者**270**

![tft](../../images/boards/fly_pi/tft3.png)

## 3.5 mainsail切换

在浏览器输入ip+:81即可切换mainsail

例如将``192.168.1.123``修改为``192.168.1.123:81``
