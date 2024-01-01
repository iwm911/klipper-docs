# 9. Use of acceleration

## 9.1 configuration

configuration as follows:

```cfg
##ADXL345 accelerometer
[adxl345]
cs_pin: sb2040:gpio1
spi_software_sclk_pin: sb2040:gpio0
spi_software_mosi_pin: sb2040:gpio3
spi_software_miso_pin: sb2040:gpio2


[resonance_tester]
accel_chip: adxl345
probe_points:
      100, 100, 20 # This coordinate is the position you need to measure, generally for hot bed middle
```

> [!TIP]
> The design package is the best for school computers

> [!TIP]
> This TV is powered by ``Non-FLY motor'', if you are ``Fly-π'' or ``Gemini'' series, you don't need to execute it!!!

Download the three designs in sequence to install the design download package.

```bash
sudo apt update
```

```bash
sudo apt install python3-numpy python3-matplotlib libatlas-base-dev
```

```bash
~/klippy-env/bin/pip install matplotlib numpy
```

Please note that according to the CPU performance, it may take a lot of time, up to 10-20 minutes.

## 9.2 testing

Modify the configuration and save it after restarting, enter the command on the console:

```bash
ACCELEROMETER_QUERY
```

If it appears, please check the connection and configuration, the normal output is as follows.

<img src="../../images/adv/accele/acc4.png" alt="ACCE" title=":no-zooom" style="zoom:90%;" />

X, Y, Z are all required before the test.

The command of test X axis is as follows:

```bash
TEST_RESONANCES AXIS=X
```

The command of the test axis is as follows:

```bash
TEST_RESONANCES AXIS=Y
```

> [!TIP]
> If during the test process, the printer is in a state of emergency.

```cfg
[resonance_tester]
accel_chip: adxl345
accel_per_hz: 50 # Default value is 75
probe_points: ...
```

## 9.3 Usage

> [!TIP]
> klipper supports automatic calibration, safe and reset before calibration start

* `SHAPER_CALIBRATE` executes this command and executes the printer to automatically calibrateX,Y
* After the calibration is completed, perform `SAVE_CONFIG` and save the data
* You can also use `SHAPER_CALIBRATE AXIS=X` to automatically calibrate one axis,
* After each axis calibration is finished, you must first save the data in the next calibration

![ACCE](../../images/adv/accele/acc5.png ":no-zooom")

* The calibration process may take a while, please wait
