# 7. FLY-SB2040-Pro configuration reference

> [!TIP]
> The contents of all `*` packages appearing in the document need to be modified according to your actual situation

> [!TIP]
> SB2040-P is configured to replace TMC2240, and the rest of the configuration is fully compatible
> 
```cfg
################################################ ###################
# Motherboard configuration
################################################ ###################
[mcu sb2040] # Tool motherboard serial number
canbus_uuid: e51d5c71a901
### The query can firmware ID is: ~/klippy-env/bin/python ~/klipper/scripts/canbus_query.py can0

################################################ ###################
# adxl345 accelerometer configuration (enable if needed)
################################################ ###################
## ADXL345 accelerometer
[adxl345]
cs_pin: sb2040:gpio1
spi_software_sclk_pin: sb2040:gpio0
spi_software_mosi_pin: sb2040:gpio3
spi_software_miso_pin: sb2040:gpio2
#------------------------------------------------ -------------------
[resonance_tester]
accel_chip: adxl345 # Acceleration chip model
probe_points: 150,150,10 # The coordinates are configured as the middle of the hot bed

################################################ ###################
# Temperature monitoring
################################################ ###################
[temperature_sensor FLY-SB2040-PRO] # Tool board main control temperature
sensor_type: temperature_mcu #Associate mcu
sensor_mcu: sb2040
min_temp: 0
max_temp: 490
#------------------------------------------------ -------------------
[temperature_sensor Warehouse] # Tool board thermal temperature
sensor_type: ATC Semitec 104GT-2
sensor_pin: sb2040:gpio26
min_temp: -50
max_temp: 490

################################################ ###################
# E Extruder settings #
################################################ ###################
#Note: After connecting the wires, you need to test the running direction.
[extruder]
step_pin: sb2040:gpio9
dir_pin: sb2040:gpio10 # Extrusion motor direction pin setting
enable_pin: !sb2040:gpio7
## When performing extruder calibration, update the following values
## For example, if you ask for 100 mm feed, but it is actually 102:
## rotation_distance = <old rotation_distance> * <actual extrusion length> / <requested extrusion length>
## Calibration step value: 22.44=old value 22*actual value 102/target value 100
rotation_distance: 22.44 # step value
gear_ratio: 50:17 # Reduction ratio (Galileo gear ratio 7.5:1 and comment out this line; BMG is 50:17, output shaft in front, input shaft in rear)
microsteps: 16 # Motor subdivision setting, the higher the subdivision, the higher the quality, but the greater the main control load
full_steps_per_rotation: 200 # Single-turn pulse number (200 is 1.8 degrees, 400 is 0.9 degrees)
nozzle_diameter: 0.400 # Nozzle diameter
filament_diameter: 1.75 # filament diameter
heater_pin: sb2040:gpio6 # Heating rod pin, connected to HETA0
#------------------------------------------------ -------------------
##Normal thermal configuration
sensor_type: ATC Semitec 104GT-2 # Sensor model (Generic 3950, ATC Semitec 104GT-2, PT1000)
sensor_pin: sb2040:gpio27 # Sensor pin
#------------------------------------------------ -------------------
##pt1000 configuration
#sensor_type: PT1000 # Sensor model (Generic 3950, ATC Semitec 104GT-2, PT1000)
#pullup_resistor: 1000 # The thermal pull-up resistor is 1000. If the temperature is negative -180, the jumper needs to be replaced.
#sensor_pin: sb2040:gpio27 # Sensor pin
#------------------------------------------------ -------------------
#sensor_type: MAX31865 # Sensor model, PT100 version
#sensor_pin: sb2040:gpio22 # Sensor pin, PT100 version
# spi_software_sclk_pin: sb2040:gpio18
# spi_software_mosi_pin: sb2040:gpio19
# spi_software_miso_pin: sb2040:gpio23
#rtd_reference_r: 430 # Need to delete the previous # when using 31865
#------------------------------------------------ -------------------
min_temp: -200 # Minimum temperature
max_temp: 500 # Maximum temperature
max_power: 1.0 # Maximum power
min_extrude_temp: 170 # Minimum extrusion temperature (at least this temperature needs to be reached before the extruder can extrude)
pressure_advance: 0.05 # Advance pressure - try to keep the pressure below 1.0 (pressure advance is to adjust this)
#Pressure adjustment method in advance: https://www.klipper3d.org/zh/Pressure_Advance.html
pressure_advance_smooth_time: 0.040 # Smooth advancement time - the default value is 0.040
#max_extrude_only_distance: 200.0 # You can comment this when extruding traffic errors, but it is recommended to re-slice it.
#Nozzle temperature PID calibration command: "PID_CALIBRATE HEATER=extruder TARGET=245
control = pid #PID nozzle temperature automatic calibration item (will be commented after pid calibration is completed)
pid_kp = 26.213
pid_ki = 1.304
pid_kd = 131.721
step_pulse_duration: 0.000004
#------------------------------------------------ -------------------
[tmc2240 extruder]
cs_pin: sb2040:gpio11 # SPI chip select pin definition
spi_software_sclk_pin: sb2040:gpio0
spi_software_mosi_pin: sb2040:gpio3
spi_software_miso_pin: sb2040:gpio2
run_current: 0.65 # Motor running current value
interpolate: False # Whether to enable 256 micro-step interpolation (not recommended)
rref: 12300 # Drive sampling resistor
stealthchop_threshold: 99999 # Silence threshold (if silence is not required, please change the value to 0)
driver_TPFD: 0

################################################ ###################
# Fan configuration
################################################ ###################
[fan] # Model cooling fan
pin: sb2040:gpio13 # Signal interface
kick_start_time: 0.5 # Start time (don’t move)
off_below: 0.10 # Don’t move
#------------------------------------------------ -------------------
[heater_fan hotend_fan] # Duct cooling fan
pin: sb2040:gpio14 # Signal interface
max_power: 1.0 # Maximum speed
kick_start_time: 0.5 # Start time (don’t move)
heater: extruder # Associated equipment: extruder
heater_temp: 50 # What temperature does the extruder reach to start the fan?
fan_speed: 1.0 # Fan speed

################################################ ###################
# X limit configuration
################################################ ###################
[stepper_x]
endstop_pin: !sb2040:gpio29
## The SB2040 board has three limit pins available: gpio25, gpio28, and gpio29. gpio25 supports high-voltage input. Modify configuration according to actual wiring

################################################ ###################
# SB header led configuration
################################################ ###################
[neopixel sb_leds]
pin: sb2040:gpio12
chain_count: 3 # Number of lamp beads
color_order: GRBW # Lamp bead type
initial_RED: 0.4
initial_GREEN: 0.8
initial_BLUE: 1
initial_WHITE: 0.0

################################################ ###################
# PL08N induction probe
################################################ ###################
# The PL08N induction probe is not lower than the nozzle height and is only used for leveling. If your PL08N is NO (normally open), please add the change pin to!
#[probe]
#pin: ^sb2040:gpio25 # Signal interface
#x_offset: 0 # The offset of the sensor relative to the nozzle, you need to determine the offset yourself
#y_offset: 25.0
#z_offset: 0
#speed: 10.0 # Leveling speed
#samples: 3 # Number of samples
#samples_result: median
#sample_retract_dist: 4.0 # Leveling the retract distance
#samples_tolerance: 0.010 # Sampling tolerance (note that too small a value may cause an increase in the number of samples)
#samples_tolerance_retries: 3 # Number of out-of-tolerance retries

#------------------------------------------------ -------------------
#[bltouch]
#sensor_pin: ^sb2040:gpio29 # Signal interface
#control_pin: sb2040:gpio28 # Servo control
#x_offset: -26.1
#y_offset: -15.3
#z_offset: 2.1
