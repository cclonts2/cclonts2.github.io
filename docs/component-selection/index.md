---
title: Component Selection
---

*Table 1*

**Microcontroller**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <img src="MFG_Attachment-2-ESP32-S3-WROOM-1.jpg" width="150"><br>Option 1.<br> ESP32-S3-WROOM-1-N4<br>$2.95/each<br>[link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639?s=N4IgjCBcpgbFoDGUBmBDANgZwKYBoQB7KAbRACY4BWWAFhAF0CAHAFyhAGVWAnASwB2AcxABfAlXrQQySOmz4ipELADsVVQE4AHIxbtIXXoJHiVmhDNSZcBYpDK0ADJoDMbvSDYdu-YWIIwd0tZeVslB3ByTU1yck9vQ18TAPBaeOlQm0V7MlVyV21XeiYvAyM-UwJyKgykawU7ZUpyWEoE8uT-M3JVeEyG8NyKJ3JtdtLEipSzVyd%2B%2Brlspsig7U0NDp9jboJaWl0BpcaIsjAnJ1c%2BraSdqpANQ8WwnObtNRob6d2Qcaln5anFTqLTwSadO6pcYLKzHIbKD5aKhfLr3TSwZFHF4rMiFKjzJwoyFmHT-WHYoGSbRUTQQcHbSqpMDacYhQavVZExlmZlFNlwjm48hOVTaEr6BkzQIsslZE7DLTaXlcqXgHQWLGA4aEhg9WCaVT8ikK-G0Wkqn4AWggmvlyjAmicJTMltl7JxIE0zhqjBdmIBds51RA1Vorl9BEthtt8MisDmsFg2jwDqdvtEoiAA) | \* Versatile <br>\* Wifi and Bluetooth<br>\* Meets surface mount constraint of project | \* No Dedicated SRAM |
| <img src="MFG_Attachment-2-ESP32-S3-WROOM-1.jpg" width="150"><br>\* Option 2. <br>\* ESP32-S3-WROOM-1-N16R8 <br>\* $3.90/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N16R8/16162642) | \* 16MB of memory <br>\* Wifi and Bluetooth | * More expensive <br>\* Slow shipping speed |
| <img src="MFG_ESP32-WROOM-32E-(4MB-HIGH-TEMP).jpg" width="150"><br>\* Option 3. <br>\* ESP32-WROOM-32E-H4 <br>\* $2.68/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-WROOM-32E-H4/12696413) | \* Wider operating temperature range <br>\* Wifi and Bluetooth | * Low Inventory <br>\* Slow shipping speed |

**Choice:** Option 1: ESP32-S3-WROOM-1-N4.

**Rationale:** The ESP32-S3-WROOM-1-N4 is the optimal choice because it provides a balance of features, cost, and compatibility with the project requirements. Its integrated Wi-Fi and Bluetooth v5.0 capabilities, surface mount design, and sufficient memory make it ideal for bidirectional internet communication. While it has some limitations, such as limited RAM and a moderate operating temperature range, these are not critical for the project.


*Table 2*

**USB Connector**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <img src="10118193-0001LF.jpg" width="150"><br>Option 1.<br> E10118193-0001LF<br>$0.41/each<br>[link to product](https://www.digikey.com/en/products/detail/amphenol-cs-fci/10118193-0001LF/2785388)  | \* Right Angle Mounting <br>\*Through hole and SMD Mounting <br>\* Shielded | \* Through hole and SMD complexity |
| <img src="10118192-0002LF.jpg" width="150"><br>\* Option 2. <br>\* 10118192-0002LF <br>\* $0.38/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/amphenol-cs-fci/10118192-0002LF/6817756) | \* Right Angle Mounting <br>\* Shielded | * More expensive <br>\* 7 Week Lead Time |
| <img src="MFG_USB3140-30-0170-1-C.jpg" width="150"><br>\* Option 3. <br>\* USB3140-30-0170-1-C <br>\* $0.77/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/gct/USB3140-30-0170-1-C/9859645) | \* Wider operating temperature range <br>\* Shielded | * SMD Mounting only <br>\* Vertical Mounting |

**Choice:** Option 1: 10118193-0001LF.

**Rationale:** The 10118193-0001LF is the optimal choice because it provides a balance of high current handling, robust shielding, and mounting flexibility. Its 10,000 mating cycles and wide operating temperature range ensure durability and reliability

*Table 3*

**Linear Voltage Regulator**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <img src="DPak-TO-263-5-Leads.jpg" width="150"><br>Option 1.<br> NCP5662DS33R4G<br>$1.32/each<br>[link to product](https://www.digikey.com/en/products/detail/onsemi/NCP5662DS33R4G/1483762)                 |<br>\* Over-Current Protection <br>\* Enable Pin  | \* Obsolete Status <br>\* Bulk Quantity Ordering |
| <img src="296~4073225-4~PWP~20.jpg" width="150"><br>\* Option 2. <br>\* TPS75133QPWPR <br>\* $4.12/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/TPS75133QPWPR/1673042) | \* Wide Temp Range <br>\* Advance Features (Reset Pin, etc.) | * Low Dropout Voltage <br>\* Input Voltage 5.5 |
| <img src="488~506AX-01~MN~6.jpg" width="150"><br>\* Option 3. <br>\* NCP565MN33T2G <br>\* $0.89/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/onsemi/NCP565MN33T2G/1792550) | \* Compact Design <br>\* Wide Temperature Range | * Difficult SMD mounting <br>\* Obsolete Status |
| <img src="296~4200577-3~KTT~3.jpg" width="150"><br>\* Option 3. <br>\* LM1086ISX-3.3/NOPB <br>\* $1.98/each <br>\* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM1086ISX-3-3-NOPB/366718) | \* Larger Package Size <br>\* Wide Voltage Input Range | * High Dropout Voltage |

**Choice:** Option 4: LM1086ISX-3.3/NOPB.

**Rationale:** The LM1086ISX-3.3/NOPB is the optimal choice because it provides a balance of wide input voltage range, high current output, and robust protection features. Its wide operating temperature range ensures stable and reliable operation in various environments. Although it has a higher dropout voltage and quiescent current, these are outweighed by its performance and reliability, making it the best fit for the project.
