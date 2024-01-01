# 2. SB2040-Pro wiring

> [!TIP]
> A heat sink can be attached to the 2240 driver

## 2.1 Wiring diagram

### 2.1 SB2040-Pro

![pinout](../../images/boards/fly_sb2040_pro/pinout.jpg)

## 2.2 Terminal resistor configuration

> [!TIP]
> Before using CAN, please configure the CANBUS terminal resistor correctly.

* CANBUS bus protocol must and can only have two 120 ohm resistors in a bus
* No matter how many USB devices you connect, only configure two 120 ohm resistors on one bus. No need to add a resistor to each device
* After connecting the CAN H and CAN L signal lines, use a multimeter to measure CAN H and CAN L. The resistance between them should be about 60 ohms.

![120Ω](../../images/boards/fly_sb2040_pro/120Ω.png)

## 2.3 Power wiring


> [!TIP]
> SB2040 Pro does not support the anti-reverse connection function of the power supply. Please check whether the positive and negative poles of the power supply are connected correctly before powering on! ! ! Otherwise, the SB2040 Pro tool board will be damaged! ! ! !

* Cable color of SB2040 Pro

| Color | Function |
| :--: | :------------------- |
| Red | ***DC 12/24v input*** |
| Black | ***DC Negative Pole (GND)*** |
| Yellow | ***CAN H*** |
| White | ***CAN L*** |

<img src="../../images/boards/fly_sb2040_pro/power.png" alt="power" style="zoom:80%;" />

## 2.4 Heating rod wiring

The heating rod supports a maximum current of 10A, please pay attention to the power of the heating rod when using it!

![heater](../../images/boards/fly_sb2040_pro/heater.png)

## 2.5 Connection method between ordinary thermal and PT1000

The figure below shows the wiring method of ordinary thermal and **PT1000**.

<img src="../../images/boards/fly_sb2040_pro/thermistor.png" alt="thermistor" style="zoom:80%;" />

## 2.5.1 PT100 wiring

> [!Tip]
>
> Please make sure whether the tool board you purchased comes with **31865 chip**
>
> **PT100** wiring method, the two-wire PT100 is connected to the two middle pins

<img src="../../images/boards/fly_sb2040_pro/sb2040v2_pt100.png" alt="sb2040v2_pt100" style="zoom:90%;" />

## 2.6 Fan wiring

SB2040 supports up to two controllable fans. The fan voltage can be selected from 24V or 5V. It supports 2, 3, and 4-wire fans. The wiring method is as follows.

> [!TIP]
> The third wire of a three-wire fan is usually a speed measuring wire. It can be left alone and connected directly to the two power wires. The wiring method is the same as that of a two-wire fan.

<img src="../../images/boards/fly_sb2040_pro/2_3-fan.png" alt="2_3-fan" style="zoom:65%;" />

<img src="../../images/boards/fly_sb2040_pro/4-fan.png" alt="4-fan" style="zoom:65%;" />

## 2.7 RGB wiring

The positive and negative poles of the RGB lamp beads must not be connected reversely, otherwise the CAN tool board will be damaged.

<img src="../../images/boards/fly_sb2040_pro/RGB.png" alt="RGB" style="zoom:65%;" />

## 2.8 Extruder wiring

After the extruder wiring is completed, please pay attention to configure the drive current and calibrate the extruder motor steering.

![extruder](../../images/boards/fly_sb2040_pro/extruder.png)

## 2.9 Limit switch

There are two types of limit switches: normally open (NO) and normally closed (NC). Generally on 3D printers, it is recommended to use normally closed (NC), so that when there is a problem with the limit switch circuit, the system will report an error in time, which can avoid unnecessary crashes and damage to the printer.

If it is a VORON model, you can consider changing the installation position of the limit, installing an X limit switch on the print head trolley, and installing a Y limit switch on the A motor base. In addition, on SB2040, it is recommended to add ``^`` before the limit switch to pull up the signal. For example:

```bash
[stepper_x]
endstop_pin: ^sb2040:PA0 # Add ^ in front to pull up the signal
```

![endstop](../../images/boards/fly_sb2040_pro/endstop.png)

## 2.10 Leveling sensor wiring

### 2.10.1 Proximity switch

VORON’s official recommendation is to use Omron TL-Q5MC (the previous official recommendation was PL08N, the two have the same principle, but the detection distance is different) sensor for hot bed leveling.

![pl08](../../images/boards/fly_sb2040_pro/pl08.png)

### 2.10.2 Klicky

Klicky is a third-party leveling sensor that can be made at home at a very low cost. It has stable performance and is very cost-effective. It is recommended to use. The wiring method is shown in the figure below.

![klicky](../../images/boards/fly_sb2040_pro/klicky.png)

### 2.10.3 Voron Tap

Voron Tap is the latest leveling sensor solution released by the Voron team. It has the characteristics of high accuracy, strong stability and good adaptability. When wiring, please be careful not to reverse the positive and negative poles, otherwise the Tap sensor or even the SHT tool board will be damaged.

> [!TIP]
> Voron Tap is not recommended to be connected to **24V**. Using **24V** in some versions has a certain probability of causing the Tap sensor to burn out. This is not a problem with Fly products, but a design defect of Voron Tap. Please be informed! ! !

![tap](../../images/boards/fly_sb2040_pro/tap.png)

### 2.10.4 Bltouch

BL-touch has a total of five wires. The first group of three wires is responsible for the power supply of the sensor and the retraction and retraction of the probe. The second group is the ground wire and signal wire, which outputs the limit signal. Please check the wiring sequence carefully when wiring BL-touch. Wrong wiring may permanently damage the sensor and main board! ! ! The wiring method is shown in the figure below.

![bltouch](../../images/boards/fly_sb2040_pro/bltouch.png)

> [!TIP]
> **This capacitor needs to be removed to use Bltouch! ! **

![touch](../../images/boards/fly_sb2040_pro/touch.png)

## 2.11 SB2040 connected to UTOC

FLY UTOC is a USB-to-CAN bus module. Through it, the USB port of FLY π is designed for CAN bus, and it can connect to 3D printing motherboards, SB2040 and other CAN bus products through the CAN bus. The FLY UTOC board has a variety of terminal interfaces, which has good flexibility and can be adapted to different usage scenarios. **In addition, the firmware of UTOC has been flashed when it leaves the factory, so it can be used immediately, and there is no need to flash the firmware again. **

![utoc](../../images/boards/fly_sb2040_pro/utoc.png)

![utoc2](../../images/boards/fly_sb2040_pro/utoc2.png)

**USB-IN:** USB to CAN input interface, connected to the host computer

**12-24v & GND:** Power interface

**CANBUS:** CAN interface, connected to expansion motherboards and tool boards (connected to devices with onboard CAN transceiver chips)

**CANBUS\*:** CAN interface, connected to expansion motherboards and tool boards, etc. (only USB interface [PA11, PA12] connected to STM32 devices, please pay attention to purchase the corresponding version of UTOC)
