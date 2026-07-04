# eumesmo-io-24v16ch
ESP32 based board with 16x optoisolated 24 VDC active high inputs, and 16x open collector 24 VDC outputs.

The outputs are based on the MMBT2222A SMD transistor and are rated for a maximum of 500mA, although it is recommended to limit the current to 350 mA for continous operation. If driving inductive loads like relays, a freewheeling diode or a snubber circuit should be used to limit the switching transients and protect the transistors.

Also included is a 1-Wire interface for external sensors. This interface can be switched to connect either to GPIO16 for use with a bitbang driver like the one available in Tasmota, or to a DS2482S-100 1-Wire master for building more complex networks. Selection is made via SW2, according to the description printed on the PCB. **Attention:** only one dip-switch can be on at any given time.

The board is compatible with the SP7 DIN rail system from [Metaltex](https://www.metaltex.com.br/).

## Hardware Specifications

| Feature | Specification |
| :--- | :--- |
| **Microcontroller** | ESP32-WROOM-32UE-N16 (16MB flash) |
| **Inputs** | 16x 24VDC (optoisolated, active high) |
| **Outputs** | 16x 24VDC (open collector, 350mA cont. / 500mA peak) |
| **Peripherals** | 1-Wire Interface, GPIO or 1-Wire master |
| **Form Factor** | Metaltex DIN Rail Compatible |

![eumesmo-io-24v16ch V6.0](https://github.com/thermseekr/eumesmo-io-24v16ch/raw/main/V6/eumesmo-io-24v16ch-v6.2.png)

## VERSION HISTORY

V6.3 - 2026/07/02 - Added CPU health LED.

V6.2 - 2026/06/13 - Repository renamed from ESP-24V-16CH to eumesmo-io-24v16ch to align the design with the **eumesmo** line of building automation products.

V6.1 - 2026/06/09 - Added voltage monitors for the reset pins on the ESP32 and LAN8710A, replacing the RC circuits. The idea is to get more reliability on the power up sequence with a more controlled reset scheme and a sharper edge on the reset signal. For the ESP32 a TPS3820-33 was selected, which has a reset delay of 25ms. The LAN8710A received a TPS3823-33 with a 200ms delay. The sequence is: ESP32 gets power and goes out of reset 25ms after power good is detected at the 3V3 rail. After boot GPIO12 will go high enabling the 3V3LAN power rail and feeding power to both LAN8710A and TPS3823-33. Then, 200ms after power good is detected on the 3V3LAN rail, the LAN8710A will go out of reset and the power sequence is completed.

V6.0 - 2026/06/06 - The ESP32 was repositioned to allow for better routing to/from the PHY. Test points and a shunt resistor on the 5V rail were added to be used during tests. Will be remove in later versions. A separate GND plane and connector for optocouplers inputs was included. New ethernet connector, with tab up for easier integration with DIN holders from Metaltex. Connectors were replaced for 3.5mm pitch versions for easier wiring installation in the field. The board had to grow 10mm to accomodate these. SMD capacitor sizes were revised for better performance. Transistor base current for the ouputs was increased from 2,3mA to 5,5mA to ensure better saturation. Now, higher loads can be driven without the risk of putting the transistor in the active region. The MCP23017 expander for the inputs was replaced by 2x MCP23008 to avoid the infamous MCP23017 input bug. Rpacks were replaced for individual resistors for more flexible layout. Talking about layout, it was fully revised with better impedance matching for LAN8710 Tx/Rx signal traces. At last, the loads for 3V3A and 3V3LAN rails were revised.

V5.2 - 2026/02/10 - Pins GPA7 and GPB7 of the input MCP23017 were disabled as recommended by Microchip. Inputs 1 and 2 were assigned to GPIO34 and GPIO35 on the ESP32. The mentioned pins were pulled down to 0V and disabled on the mcp23x.dat template. Templates and GPIO assignment information on the schematics were updated.

V5.1 - Corrected footprint of R7 and repositioned the RESET switch as noted by [@yvkoch](https://github.com/yvkoch). Thanks Yrjö! Improved the 1-Wire bus interface aiming for cable runs up to 50m, still to be tested. Also included the option to connect a GPIO to the 1-Wire bus. ATENTION, SW2 can only have one switch ON at any given time, to connect either the DS2482 or GPIO16 to the 1-Wire bus.

V5.0 - Removed the onboard temperature sensor, too sensitive to be on a PCB and also measure the ambient temperature inside the cabinet. Even with cuts around the sensor, it was better at measuring each transistor's influence on the PCB's temperature than the temperature of the environment. Replaced the analog NTC inputs for a 1-Wire i2c interface. Mixing analog and digital circuits on a PCB requires more testing and developing time than I have available. So, fully digital we go. Decreased the brightness of the LEDs, maybe this time I'll get them right :) Repositioned components and rerouted the whole board following the valuable insights taken from [Phil's Lab](https://github.com/pms67) latest videos about Kicad. Thank you very much, Phil.

V4.1 - Redesigned NTC inputs for using differential mode for better immunity against noise. Also the low pass filters were redesigned, the original ones were pretty much useless for any cable larger that 2 meters.

V4.0 - Redesigned digital inputs for better tolerance to long cable runs in noisy environment. Removed pads for NTC inputs 3 and 4, tied them to GND.

V3.2 - Added 4 NTC inputs using an ADS1115 A/D converter with i2c. Reduced current on the LEDs, brightness was too high. Added series resistor and rerouted clock track for better impedance and ring control. Rerouted TX/RX and SCL/SDA tracks for improved signal quality. Layers reordered so the ground plane is directly below the top layer. Returned ESP32 to 16MB version.

V3.1 - Added AHT20 onboard temperature and humidity sensor for cabinet environment monitoring. Replaced ESP32 16MB for 4MB because no stock at JLCPCB.

V3 - Power LED moved to 5V bus. Individual resistors replaced for rpacks where applicable. Moved from 2 to 4 layers, board reduced 30mm in lenght. USB connector repositioned and replaced for horizontal version.

V2 - All GPIOs moved to MCP23017 expanders. MCP interrupt pins connected to GPIOs on the ESP32. USB connector changed for USB type C.

V1 - Initial version, not released. The first 8 inputs used native ESP32 GPIOs, other inputs and all outputs were wired through MCP GPIO expanders.

## LICENSE

This project is licensed under the [Creative Commons BY-NC 4.0 License](https://creativecommons.org/licenses/by-nc/4.0/).
Commercial use is not permitted without prior written consent. See the [LICENSE.txt](LICENSE.txt) file for details.
