---
ESP32 Table
---

| ESP Info                                      | Answer |                                                                                                      |
| --------------------------------------------- | ------ | --------------------------------------------------------------------------------------------------------- |
| Model                                         | ESP32-S3-WROOM-1      |           |
| Product Page URL                              | [espressif](https://www.espressif.com/en/products/modules)      | Found on Espressif.com                                                                                    |
| ESP32-S3-WROOM-1-N4 Datasheet URL             | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf)      |                                               |
| ESP32 S3 Datasheet URL                        | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf)      | Has more detail on functions                                                                              |
| ESP32 S3 Technical Reference Manual URL       | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_technical_reference_manual_en.pdf)      | Has details on I/O multiplexing, USB, and others                                                          |
| Vendor link                                   | [digikey](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639?s=N4IgjCBcpgbFoDGUBmBDANgZwKYBoQB7KAbRACY4BWWAFhAF0CAHAFyhAGVWAnASwB2AcxABfAlXrQQySOmz4ipELADsVVQE4AHIxbtIXXoJHiVmhDNSZcBYpDK0ADJoDMbvSDYdu-YWIIwd0tZeVslB3ByTU1yck9vQ18TAPBaeOlQm0V7MlVyV21XeiYvAyM-UwJyKgykawU7ZUpyWEoE8uT-M3JVeEyG8NyKJ3JtdtLEipSzVyd%2B%2Brlspsig7U0NDp9jboJaWl0BpcaIsjAnJ1c%2BraSdqpANQ8WwnObtNRob6d2Qcaln5anFTqLTwSadO6pcYLKzHIbKD5aKhfLr3TSwZFHF4rMiFKjzJwoyFmHT-WHYoGSbRUTQQcHbSqpMDacYhQavVZExlmZlFNlwjm48hOVTaEr6BkzQIsslZE7DLTaXlcqXgHQWLGA4aEhg9WCaVT8ikK-G0Wkqn4AWggmvlyjAmicJTMltl7JxIE0zhqjBdmIBds51RA1Vorl9BEthtt8MisDmsFg2jwDqdvtEoiAA)      |                       |
| Code Examples                                 | [Link](https://github.com/ESP32DE/ESP32-S3-DevKitC-1https://github.com/ESP32DE/ESP32-S3-DevKitC-1)      | url(s) for libraries on github or other sites related to the microcontroller and your planned peripherals |
| Unit cost                                     | $2.95      |                                                                |
| Absolute Maximum Current for entire IC        | 500ma      | Find in the microcontroller datasheet                                                                     |
| Supply Voltage Range                          | 3.0V / 3.3V / 3.6V      | Min / Nominal / Max / Absolute Max, as found in datasheet                                                 |
| Maximum GPIO current <br> (per pin)           | 20mA / 40mA      | Nominal / Max                                                                                    |
| Supports External Interrupts?                 | Yes      | as found in datasheet                                                                                     |
| Required Programming Hardware, Cost, URL      | [Link]{https://docs.espressif.com/projects/esp-idf/en/latest/esp32s3/get-started/index.html}      | as found in datasheet                                                                                     |

| Module         | # Available | Needed | Associated Pins (or * for any) |
| -------------- | ----------- | ------ | ------------------------------ |
| UART           | 3 modules           | 1      | 36 37                              |
| SPI            | 8           | ?      | 5 12 13 14 15 18 19 23                              |
| I2C            | 4           | ?      | 16 17 21 22                              |
| GPIO           | 43          | ?      | *                              |
| ADC            | 2 modules           | ?      | 4 5 6 7 12 15 17 18 19 20 21 22 23 24 25 26 27 28 38 39                              |
| LED PWM        | 8 channels           | ?      | *                              |
| Motor PWM      | 2 modules           | ?      | *                              |



\* The ESP32-S2 has multiple SPI interfaces, but some are for internal use
