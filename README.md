# BuckPSU Modified
Attempt to modify Arduino library for inexpensive (~$30) remotely controllable and monitored DC-DC converters.
** that have no UART port on the motherboard ** 

Some poorly written documentation for the protocol from Drok:
https://www.droking.com/cs/support/topic/200220-dc-dc-buck-converter-uart/#post-35186

## Library commands
|Library function| Prototol command |  Use |
| ------------- | ------------- | ------------- |
| setVoltageMilliVolts(uint16_t millivolts) | awu (milivolts) | Sets output Volage in mV |
| setCurrentMilliAmps(uint16_t milliamps) | awi (miliamps) | Sets output Current in mA |
| enableOutput(bool status) | :wo1 / :wo0 | Enables/Disables the Output |
| enableAuto(bool status) | :wy1 / :wy0 | Enables/Disables if output enabled at power up |
| enableLock(bool status) | :wl1 / :wl0| Enables/Disables lock on power supply buttons - local control |
| enableDisplay(bool status) | :wd1 / :wd0 | Enables/Disables the 4 digit display |
| setMemory(int loc) | :ws (loc) | Set values in memory (0-9) *See Note 1 |
| getMemory(int loc) | :wm (loc) | Get values from memory (0-9) |
| readVoltageMilliVolts() | :ru | Returns active output Voltage |
| readCurrentMilliAmps() | :ri | Returns acive output Current |
| readSetMilliVolts() | :rv | Returns set output Voltage |
| readSetMilliAmps() | :ra | Returns set output Current |
| readTimer() | :rt | Returns number of seconds supply has run |
| readCapacity() | :rc | Returns total amp hours in thousandth of AH |
| getOutputEnabled() | :ro | Get the status of the output |
| getAutoEnabled() | :ry | Get the status if output is on or off at power up |
| getLockEnabled() | :rl | Get if the front panel is locked |

**Note:** Preset memory location zero sets the default power up values.

Fun fact: When the Power Supply is polled by the MCU, it causes the four digit numeric display appear to flicker.

## Compatible converters
DC-DC converters sold under the brand names Juntek seem to be compatible with these commands.
Such as:
* DKP3608 (commands not yet tested) 
* DKP3003 (not yet tested)

Searching "DC to DC  Power Supply Module 10V-65V" or "DKP6012" yield the search results to find them for purchase.



## Wiring connections:

| Power Supply| Raiser Module (not UART port on the motherboard) |
| ------------- | ------------- |
| T | RX |
| G | Signal and DC ground for power supply. |
| R | TX |
| V | +5VDC - *See Note 2 |



