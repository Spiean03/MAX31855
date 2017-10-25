Python driver for [MAX31855 Cold-Junction Compensated Thermocouple-to-Digital Converter](http://www.maximintegrated.com/datasheet/index.mvp/id/7273)

Requires:
- The [GPIO Library](https://code.google.com/p/raspberry-gpio-python/) (Already on most Raspberry Pi OS builds)
- A [Raspberry Pi](http://www.raspberrypi.org/)

## Basic use

```python

#!/usr/bin/python
from max31855 import MAX31855, MAX31855Error

cs_pin = 24
clock_pin = 23
data_pin = 22
units = "f"
thermocouple = MAX31855(cs_pin, clock_pin, data_pin, units)
print(thermocouple.get())
thermocouple.cleanup()

```

*Note: these are the GPIO pin numbers, not the header pin numbers.*  
*This can be overriden by passing `GPIO.BOARD` as the fifth [init parameter](https://github.com/Tuckie/max31855/blob/master/max31855.py#L11).*

See max31855.py for a multi-chip example.

## Code Example to read out several Max31855 chips

See picture master_slave.png as an example. In this case Master is the Pi, and Slaves are the MAX31855's. SS (Slave Select) is the same as CS (Chip Select).

```python

from max31855 import MAX31855, MAX31855Error

cs_pin_1=24
clock_pin=23
data_pin=22
cs_pin_2=21
cs_pin_3=20
units = "f"

thermocouple1=MAX31855(cs_pin_1, clock_pin, data_pin, units)
thermocouple2=MAX31855(cs_pin_2, clock_pin, data_pin, units)
thermocouple3=MAX31855(cs_pin_3, clock_pin, data_pin, units)

```
