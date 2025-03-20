---
title: API
tags:
---


## Message Types Breakdown

### Temperature Sensor (Message Type 1)

|  | Byte 1 | Byte 2 | Byte 3 | Byte 4 | Byte 5 | Byte 6 | Byte 7 | Byte 8 | Byte 9 | Byte 10-62 | Byte 63 | Byte 64 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Variable Name | prefix_1 | prefix_2 | source_id | destination_id | message_type | temp_id | status | temp_data_integer | temp_data_fraction | Unused | suffix_1 | suffix_2 |
| Variable Type | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t | uint8_t |
| Min Value | 0x41 | 0x5a | 3 | 1 | 0x10 | 1 | 0 | -40 | 0 | 0x00 | 0x59 | 0x42 |
| Max Value | 0x41 | 0x5a | 3 | 88 | 0x10 | 255 | 1 | 155 | 99 | 0x00 | 0x59 | 0x42 |
| Example Value | 0x41 | 0x5a |	0x03 |	0x58 |	0x10 |	0x01 |	0x01 |	25 |	50 |	0x00 |	0x59 |	0x42 |

### Other way


### Fan Control (Message Type 2)

