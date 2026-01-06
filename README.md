# ESP-24V-16CH
ESP32 based board with 16x 24 VDC inputs and 16x 24 VDC transistor outputs for external relays. Also included is a 1-Wire interface for external sensors.

The dimensions were chosen for mounting on a PCB DIN rail holder from the Brazilian manufacturer Metaltex, check [here](https://www.metaltex.com.br/produtos/suportes-para-pci/suportes-para-pci) for details.

![alt text](https://github.com/thermseekr/ESP-24v-16ch/blob/main/V5/esp-24v-16ch-v5.1.0.png "ESP-24V-16CH V5.1")

## VERSION HISTORY

ESP-24V-16CH V5.1 - Corrected footprint of R7 and repositioned the RESET switch as noted by [@yvkoch](https://github.com/yvkoch). Thanks Yrjö! Improved the 1-Wire bus interface aiming for cable runs up to 50m, still to be tested. Also included the option to connect a GPIO to the 1-Wire bus. ATENTION, SW2 can only have one switch ON at any given time, to connect either the DS2482 or GPIO16 to the 1-Wire bus.

ESP-24V-16CH V5.0 - Removed the onboard temperature sensor, too sensitive to be on a PCB and also measure the ambient temperature inside the cabinet. Even with cuts around the sensor, it was better at measuring each transistor's influence on the PCB's temperature than the temperature of the environment. Replaced the analog NTC inputs for a 1-Wire i2c interface. Mixing analog and digital circuits on a PCB requires more testing and developing time than I have available. So, fully digital we go. Decreased the brightness of the LEDs, maybe this time I'll get them right :) Repositioned components and rerouted the whole board following the valuable insights taken from [Phil's Lab](https://github.com/pms67) latest videos about Kicad. Thank you very much, Phil.

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
