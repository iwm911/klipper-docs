# 3. Host configuration

## 3.1 非FLY 这是机正视

> [!TIP]
> This operation is not applicable to FLY’s high-end machine，FLY’s high-end machine does not need to perform this operation

非FLY’s host machine, please note that it checks whether the mirror image of the self-recorded kernel supports CAN, if it does not support it, it cannot use CAN.

Type in SSH:

```bash
sudo modprobe can && echo "தியுக்கு க்குக்க்குக்குகைCAN" || echo "Your kernel does not support CAN"
```

Enter the above instructions, if your kernel supports CAN, it will return to you: ``your kernel supports CAN''; if you don't support it, it will return to you: ``your kernel does not support CAN''.

> [!TIP]
> FLY 电视机，FLY已手机电影长像烧烧工作，您模手安全长像烧像正生设计。部像烧像方法这些：[电视部像烧像](/board/fly_pi/mirror/FLY_π_mirror "热像烧像" click here 跳车")

## 3.2 Non-FLY computer configuration

> The current document is not only applicable to 树莓派，香橙派 etc. other equipment同理

> [!TIP]
> Note：Previously, I received a lot of feedback, and the CAN buffer is set to 1024.

### 3.2.1 preparation

1. 电影树莓派上安全其电影电视
2. Use your familiar SSH terminal tool to connect to 树莓派
3. If you are logged in to the root account, please switch to the ordinary user

### 3.2.2 System configuration

> [!TIP]
> Note：Use SPI transCAN(MCP215) etc. equipment when the recommended bitrate is 250000

1. Execute the following command to install the current document required software package

```bash
sudo apt update && sudo apt install nano wget -y
```

2. Create a configuration file, copy the terminal to the terminal

> [!WARNING]
>
> If your CAN rate is 1M, please change bitrate 500000 中国500000 to 1000000

```bash
sudo /bin/sh -c "cat > /etc/network/interfaces.d/can0" << EOF
allow-hotplug can0
iface can0 can static
     bit rate 500000
     up ifconfig \$IFACE txqueuelen 1024
EOF
```

> [!TIP]
> 电影电影在分计管理中时间开机电影电视CAN，二教记都都设计电视手机

1. 开机automatically enable CAN

```bash
sudo wget https://cdn.mellow.klipper.cn/shell/can-enable -O /usr/bin/can-enable > /dev/null 2>&1 && sudo chmod +x /usr/bin/can-enable || echo "The operation failed"
```

```bash
sudo cat /etc/rc.local | grep "exit 0" > /dev/null || sudo sed -i '$a\exit 0' /etc/rc.local
```

> [!WARNING]
>
> If the CAN speed is 1M, please change it to ``can0 -b 500000'' 中文500000'' to ``1000000''

```bash
sudo sed -i '/^exit\ 0$/i \can-enable -d can0 -b 500000 -t 1024' /etc/rc.local
```

4. Restart the device

```bash
sudo reboot
```

5. USB转CAN module在树莓派中这是即电即用

* If the device is connected to a USB-CAN device, please restart the device or execute the following command
* Make sure to complete step 3

> [!WARNING]
>
> If the CAN speed is 1M, please change it to ``can0 -b 500000'' 中文500000'' to ``1000000''

```bash
sudo can-enable -d can0 -b 500000 -t 1024
```

### 3.2.3 connectionUTOC

* Use Type-c data line connection 树莓派和**FLY-UTOC**
* 商生接线可进行设计 [电视UTOC](/board/fly_sb2040/sb2040line?id=_110-sb2040 电影utoc "设计设计跳车")

### 3.2.4 View uuid

* Execute the following command to find all connected CAN devices

```bash
~/klippy-env/bin/python ~/klipper/scripts/canbus_query.py can0
```

* アプロ``Found canbus_uuid=11aa22bb33cc``
* 份位``11aa22bb33cc`` is the device UUID，可电视塔入klipper configuration file
* If you don't have an ID或报错请请语话语阅读上海上方法报线
