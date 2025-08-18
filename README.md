# ESP-24V-16CH
ESP32 based board with 16x 24 VDC inputs and 16x 24 VDC outputs for external actuators. V3.1 added an AHT20 temperature and Humidity sensor for cabinet environmental monitoring. V3.2 added a ADS1115 A/D converter with i2c communication for use with NTC thermistors. Thermistors 1 and 2 can be connected using the provided connector. Thermistors 3 and 4 must use the provided copper pads on the top layer of the board.

The dimensions were chosen for mounting on a PCB DIN rail holder from the Brazilian manufacturer Metaltex, check [here](https://www.metaltex.com.br/produtos/suportes-para-pci/suportes-para-pci) for details.

![alt text](https://github.com/thermseekr/ESP-24v-16ch/blob/main/V4/esp-24v-16ch-v4.1.0.png "ESP-24V-16CH V4.1")

## VERSION HISTORY

ESP-24V-16CH V4.1 - Redesigned NTC inputs for using differential mode for better immunity against noise. Also the low pass filters were redesigned, the original ones were pretty much useless for any cable larger that 2 meters.

ESP-24V-16CH V4.0 - Redesigned digital inputs for better tolerance to long cable runs in noisy environment. Removed pads for NTC inputs 3 and 4, tied them to GND.

ESP-24V-16CH V3.2 - Added 4 NTC inputs using an ADS1115 A/D converter with i2c. Reduced current on the LEDs, brightness was too high. Added series resistor and rerouted clock track for better impedance and ring control. Rerouted TX/RX and SCL/SDA tracks for improved signal quality. Layers reordered so the ground plane is directly below the top layer. Returned ESP32 to 16MB version.

ESP-24V-16CH V3.1 - Added AHT20 onboard temperature and humidity sensor for cabinet environment monitoring. Replaced ESP32 16MB for 4MB because no stock at JLCPCB.

ESP-24V-16CH V3 - Power LED moved to 5V bus. Individual resistors replaced for rpacks where applicable. Moved from 2 to 4 layers, board reduced 30mm in lenght. USB connector repositioned and replaced for horizontal version.

ESP-24V-16CH V2 - All GPIOs moved to MCP23017 expanders. MCP interrupt pins connected to GPIOs on the ESP32. USB connector changed for USB type C.

ESP-24V-16CH V1 - Initial version, not released. The first 8 inputs used native ESP32 GPIOs, other inputs and all outputs were wired through MCP GPIO expanders.

## LICENSE

This project is licensed under the [Creative Commons BY-NC 4.0 License](https://creativecommons.org/licenses/by-nc/4.0/).
Commercial use is not permitted without prior written consent. See the [LICENSE.txt](LICENSE.txt) file for details.
