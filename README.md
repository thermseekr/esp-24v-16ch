# ESP-24V-16CH
ESP32 based board with 16x 24 VDC inputs and 16x 24 VDC outputs for external actuators.

The dimensions are such that the board can be mounted on a PCB DIN rail holder from the Brazilian manufacturer Metaltex, check [here](https://www.metaltex.com.br/produtos/componentes/suportes/sp7-suporte-para-montagem-de-placa-de-circuito-impresso-em-trilho-din) for details.

![alt text](https://github.com/thermseekr/ESP-24v-16ch/blob/main/V3/esp-24v-16ch-v3.1.0.png "ESP-24V-16CH")

## VERSION HISTORY

ESP-24V-16CH-V3 - Power LED moved to 5V bus. Individual resistors replaced for rpacks where applicable. Moved from 2 to 4 layers, board reduced 30mm in lenght. USB connector repositioned and replaced for horizontal version.

ESP-24V-16CH-V2 - All GPIOs moved to MCP23017 expanders. MCP interrupt pins connected to GPIOs on the ESP32. USB connector changed for USB type C.

ESP-24V-16CH-V1 - Initial version, not released. The first 8 inputs used native ESP32 GPIOs, other inputs and all outputs were wired through MCP GPIO expanders.
