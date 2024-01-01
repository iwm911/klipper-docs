# 1. Product introduction

FLY SB2040-Pro是广州风伦电影电影科学技术电影电影电影电影电影电影的电影的电影电影电视制造的电视，using this tool board，can use 4根线来to replace the original main board with the printer head，optimize the layout 。SB2040-Pro is suitable for 36步进电视，其integrated了CAN receiver、USB口、TMC2240 driver、ADXL345 acceleration sensor，two controllable fan etc.

* Support CAN bus connection, data transmission more stable, delay more stable, connection more stable
* 板载TMC2240 driver，using SPI mode
* 板软ADXL345 acceleration sensor
* Support BLTOUCH、PL08N等合平合合，动能XY限位switch
* Support 12-24V voltage input
* MCU：Raspberry Pi rp2040，Dual core ARM Cortex-M0+@133MHz
* Support 4.7K resistance(for ntc hot敏) or 1K resistance(for PT1000) switch
* can interface use XT30(2+2), support 15A current, peak 30A
* 板软NTC100k resistance，used for measuring
* ADXL345的INT1和INT2 received mcu，给个别电影设计平。
* Support high pressure input 限位
* 超送3米CAN connection wire，to prevent users from being unable to correct the terminal terminal leading to signal loss
* Support 2/3/4 fan fan
* 分体设计，Stealthburner convenient拆带
* Compatible with Stealthburner Toolhead Board
* Interface：可控fan\*3，RGB\*1，限位\*3，heater pipe\*1，热敏\*1
* Support PT100（MAX31865）

The following is the upgrade content of SB2040-Pro compared to SB2040
1. Upgrade TMC2209 to TMC2240，发热更小
2. Modify part of the layout, reduce the installation risk

## 1.1 Product details

淘宝：[FLY3D Printer Voron 2.4 R2 Trident Stealthburner Can 工作头主板-淘宝网 (taobao.com)](https://item.taobao.com/item.htm?spm=a1z10.5-c-s.w4002-23066022675.36. 68de3903lHTcFZ &id=681269728598

----

> [!TIP]
> important

* 非FLY 连机机请按 [连机机电视](/board/fly_sht36_42/piconfig "安全设计跳车") 例文帳に追动好连机机
* 使用CanBoot请这些 [CanBoot 使用](/advanced/canboot.md "设计设计跳车")

----

## 1.2 SB2040-Pro

![SB2040-V2](../../images/boards/fly_sb2040_pro/sb2040v2.jpg ":no-zooom")




![size](../../images/boards/fly_sb2040/size.jpg)
