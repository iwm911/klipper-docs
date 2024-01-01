# 6. pin distribution

## 6.1 SB2040-PRO pins

![SB2040 v2 Pinout](../../images/boards/fly_sb2040_pro/pinout.jpg ":no-zooom")



### 6.2 Communication

* CANBUS

| function | 电影号 |
| :----: | :----- |
| RX | ***gpio4*** |
| TX | ***gpio5*** |

### 6.3 步进电视电视电视

* Electric motors

| drive | function | 电影号 |
| :----: | :----: | :----- |
| E| EN | ***gpio7*** |
| E| STEP | ***gpio9*** |
| E| DIR | ***gpio10*** |
| E| CS | ***gpio8*** |

* Electric motors
| SPI | 电影号 |
| :----: | :----- |
| SCLK | ***gpio0*** |
| MOSI | ***gpio3*** |
| MISO | ***gpio2*** |

### 6.4 Limitations

| 限位 | 电影号 |
| :----: | :----- |
| 1 | ***gpio28*** |
| 2 | ***gpio29*** |
| 3 | ***gpio25*** |

### 6.5 heating control

| function | 电影号 |
| :----: | :----- |
| 新出电视 | ***gpio6*** |

### 6.6 Temperature sensor

| function | 电影号 |
| :----: | :----- |
| 新出水水 | ***gpio27*** |
| 板自NTC | ***gpio26*** |

### 6.7 fan

| function | 电影号 |
| :----: | :----- |
| fan0 | ***gpio13*** |
| fan1 | ***gpio14*** |
| fan2 | ***gpio15*** |

### 6.8 RGB

| function | 电影号 |
| :----: | :----- |
| RGB1 | ***gpio12*** |

## 6.9 Acceleration

| function | 电影号 |
| :----: | :----- |
| MISO | ***gpio2*** |
| MOSI | ***gpio3*** |
| CLK | ***gpio0*** |
| ADXL345-CS | ***gpio1*** |
| ADXL345-INT1 | ***gpio21*** |
| ADXL345-INT2 | ***gpio20*** |

----

## 6.10 MAX31865

| function | 电影号 |
| :----: | :----- |
| MISO | ***gpio23*** |
| MOSI | ***gpio19*** |
| CLK | ***gpio18*** |
| MAX31865-CS | ***gpio22*** |
