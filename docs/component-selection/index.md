---
title: Component Selection
---

---

### **Microcontroller**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <img src="MFG_Attachment-2-ESP32-S3-WROOM-1.jpg" width="150"><br>Option 1.<br> **ESP32-S3-WROOM-1-N4** <br>$2.95/each<br>[link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639?s=N4IgjCBcpgbFoDGUBmBDANgZwKYBoQB7KAbRACY4BWWAFhAF0CAHAFyhAGVWAnASwB2AcxABfAlXrQQySOmz4ipELADsVVQE4AHIxbtIXXoJHiVmhDNSZcBYpDK0ADJoDMbvSDYdu-YWIIwd0tZeVslB3ByTU1yck9vQ18TAPBaeOlQm0V7MlVyV21XeiYvAyM-UwJyKgykawU7ZUpyWEoE8uT-M3JVeEyG8NyKJ3JtdtLEipSzVyd%2B%2Brlspsig7U0NDp9jboJaWl0BpcaIsjAnJ1c%2BraSdqpANQ8WwnObtNRob6d2Qcaln5anFTqLTwSadO6pcYLKzHIbKD5aKhfLr3TSwZFHF4rMiFKjzJwoyFmHT-WHYoGSbRUTQQcHbSqpMDacYhQavVZExlmZlFNlwjm48hOVTaEr6BkzQIsslZE7DLTaXlcqXgHQWLGA4aEhg9WCaVT8ikK-G0Wkqn4AWggmvlyjAmicJTMltl7JxIE0zhqjBdmIBds51RA1Vorl9BEthtt8MisDmsFg2jwDqdvtEoiAA) | Versatile <br> Wifi and Bluetooth <br> Meets surface mount constraint of project | No Dedicated SRAM |
| <img src="MFG_Attachment-2-ESP32-S3-WROOM-1.jpg" width="150"><br> Option 2. <br> ESP32-S3-WROOM-1-N16R8 <br> $3.90/each <br> [Link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N16R8/16162642) | 16MB of memory <br> Wifi and Bluetooth |  More expensive <br> Slow shipping speed |
| <img src="MFG_ESP32-WROOM-32E-(4MB-HIGH-TEMP).jpg" width="150"><br> Option 3. <br> ESP32-WROOM-32E-H4 <br> $2.68/each <br> [Link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-WROOM-32E-H4/12696413) |  Wider operating temperature range <br> Wifi and Bluetooth |  Low Inventory <br> Slow shipping speed |

**Choice:** Option 1: ESP32-S3-WROOM-1-N4.

**Rationale:** The ESP32-S3-WROOM-1-N4 is the optimal choice because it provides a balance of features, cost, and compatibility with the project requirements. Its integrated Wi-Fi and Bluetooth v5.0 capabilities, surface mount design, and sufficient memory make it ideal for bidirectional internet communication. While it has some limitations, such as limited RAM and a moderate operating temperature range, these are not critical for the project.


---

### **USB Connector**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <img src="10118193-0001LF.jpg" width="150"><br> **Option 1.** <br> E10118193-0001LF<br>$0.41/each<br>[link to product](https://www.digikey.com/en/products/detail/amphenol-cs-fci/10118193-0001LF/2785388)  | Right Angle Mounting <br> Through hole and SMD Mounting <br> Shielded | Through hole and SMD complexity |
| <img src="10118192-0002LF.jpg" width="150"><br> Option 2. <br> 10118192-0002LF <br> $0.38/each <br> [Link to product](https://www.digikey.com/en/products/detail/amphenol-cs-fci/10118192-0002LF/6817756) | Right Angle Mounting <br> Shielded | More expensive <br> 7 Week Lead Time |
| <img src="MFG_USB3140-30-0170-1-C.jpg" width="150"><br> Option 3. <br> USB3140-30-0170-1-C <br> $0.77/each <br> [Link to product](https://www.digikey.com/en/products/detail/gct/USB3140-30-0170-1-C/9859645) | Wider operating temperature range <br> Shielded | SMD Mounting only <br> Vertical Mounting |

**Choice:** Option 1: 10118193-0001LF.

**Rationale:** The 10118193-0001LF is the optimal choice because it provides a balance of high current handling, robust shielding, and mounting flexibility. Its 10,000 mating cycles and wide operating temperature range ensure durability and reliability

---

### **Linear Voltage Regulator**

| **Solution**                                                                                                                                                                                      | **Pros**                                                                                                                                    | **Cons**                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| <img src="DPak-TO-263-5-Leads.jpg" width="150"><br>Option 1.<br> NCP5662DS33R4G<br>$1.32/each<br>[link to product](https://www.digikey.com/en/products/detail/onsemi/NCP5662DS33R4G/1483762)                 |<br> Over-Current Protection <br>\ Enable Pin  | Obsolete Status <br> Bulk Quantity Ordering |
| <img src="296~4073225-4~PWP~20.jpg" width="150"><br>\ Option 2. <br> TPS75133QPWPR <br> $4.12/each <br> [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/TPS75133QPWPR/1673042) | Wide Temp Range <br> Advance Features (Reset Pin, etc.) | Low Dropout Voltage <br> Input Voltage 5.5 |
| <img src="488~506AX-01~MN~6.jpg" width="150"><br> Option 3. <br> NCP565MN33T2G <br> $0.89/each <br> [Link to product](https://www.digikey.com/en/products/detail/onsemi/NCP565MN33T2G/1792550) | Compact Design <br> Wide Temperature Range | Difficult SMD mounting <br> Obsolete Status |
| <img src="ap62300twu-7.jpg" width="150"><br> **Option 4.** <br> AP62300TWU-7 <br> $0.71/each <br> [Link to product](https://www.digikey.com/en/products/detail/diodes-incorporated/AP62300TWU-7/12702558) | Larger Package Size <br> Wide Voltage Input Range (4.2V - 18V) <br> High Efficiency | 85°C Top Temperature |
| <img src="ts1117bcw33rpg.jpg" width="150"><br> **Option 5.** <br> TS1117BCW33 RPG <br> $0.82/each <br> [Link to product](https://www.digikey.com/en/products/detail/taiwan-semiconductor-corporation/TS1117BCW33-RPG/7370078) | Fixed 3.3V Output <br> Simple Design <br> Overcurrent & Thermal Protection <br> | High Dropout Voltage <br> Lower Efficiency |

**Choice:** Option 4 & 5: AP62300TWU-7; TS1117BCW33 RPG

**Rationale:** The combination of the **AP62300TWU-7** and **TS1117BCW33 RPG** provides a versatile power regulation solution. The AP62300TWU-7, a high-efficiency buck converter, efficiently steps down higher input voltages (4.2V - 18V) while delivering up to 3A output current, making it ideal for applications requiring higher power efficiency. However, its switching nature may introduce noise.

The TS1117BCW33 RPG, a low-dropout (LDO) regulator, provides a clean and stable 3.3V output with built-in overcurrent and thermal protection, making it well-suited for noise-sensitive components and 5V PC Programming. Though less efficient than the buck converter, its simplicity and low dropout performance (for lower currents) make it a good secondary choice.
