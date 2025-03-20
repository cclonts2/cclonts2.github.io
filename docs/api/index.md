---
title: API
tags:
---

## Message ID

| Member        | System            | ID  | Address |
|---------------|-------------------|-----|---------|
| Cade Clonts   | Wifi              | 1   | 0x01    |
| Jahmel        | Human Interface   | 2   | 0x02    |
| Tyler         | Temp Sensor       | 3   | 0x03    |
| Dan           | Fan Control       | 4   | 0x04    |
| Broadcast     | All               | 88  | 0x58    |

### Status
| Status | Code  |
|--------|-------|
| Normal | 0x00  |
| Error  | 0x01  |

## Message Types

| Category         | Status/Code |
|------------------|-------------|
| Temp Data        | -40 to 155  |
| Fan Control      | 0-125       |
| System Status    | Normal (0x00), Error (0x01) |
| System Initialize| Pending (0x00), Complete (0x01) |
| Error            | Error Code  |

### Temperature Sensor (Message Type 1)

|               | Byte 1   | Byte 2   | Byte 3    | Byte 4         | Byte 5       | Byte 6  | Byte 7 | Byte 8    | Byte 9 | Byte 10-62 | Byte 63 | Byte 64 |
|---------------|----------|----------|-----------|----------------|--------------|---------|--------|-----------|--------|------------|---------|---------|
| Variable Name | prefix_1 | prefix_2 | source_id | destination_id | message_type | temp_id | status | temp_data_integer | temp_data_fraction | Unused  | suffix_1 | suffix_2 |
| Variable Type | uint8_t  | uint8_t  | uint8_t   | uint8_t        | uint8_t      | uint8_t | uint8_t | uint8_t  | uint8_t  | uint8_t | uint8_t | uint8_t |
| Min Value     | 0x41     | 0x5a     | 3         | 1              | 0x10         | 1       | 0      | -40       | 0        | 0x00    | 0x59    | 0x42    |
| Max Value     | 0x41     | 0x5a     | 3         | 88             | 0x10         | 255     | 1      | 155       | 99       | 0x00    | 0x59    | 0x42    |
| Example Value | 0x41     | 0x5a     | 0x03      | 0x58           | 0x10         | 0x01    | 0x01   | 25        | 50       | 0x00    | 0x59    | 0x42    |

### Inverted
| Byte | Variable Name | Variable Type | Min Value | Max Value | Example Value |
|---|------------------|--------------|-----------|-----------|--------------|
| 1 | prefix_1        | uint8_t      | 0x41      | 0x41      | 0x41         |
| 2 | prefix_2        | uint8_t      | 0x5a      | 0x5a      | 0x5a         |
| 3 | source_id       | uint8_t      | 3         | 3         | 0x03         |
| 4 | destination_id  | uint8_t      | 1         | 88        | 0x58         |
| 5 | message_type    | uint8_t      | 0x10      | 0x10      | 0x10         |
| 6 | temp_id         | uint8_t      | 1         | 255       | 0x01         |
| 7 | status          | uint8_t      | 0         | 1         | 0x01         |
| 8 | temp_data_integer | uint8_t    | -40       | 155       | 25           |
| 9 | temp_data_fraction | uint8_t   | 0         | 99        | 50           |
| 10-62 | Unused       | uint8_t     | 0x00       | 0x00     | 0x00         |
| 63 | suffix_1        | uint8_t      | 0x59      | 0x59      | 0x59         |
| 64 | suffix_2        | uint8_t      | 0x42      | 0x42      | 0x42         |

### Fan Control (Message Type 2)

|               | Byte 1   | Byte 2   | Byte 3    | Byte 4         | Byte 5       | Byte 6  | Byte 7 | Byte 8    | Byte 9-62 | Byte 63 | Byte 64 |
|---------------|----------|----------|-----------|----------------|--------------|---------|--------|-----------|--------|----------|----------|
| Variable Name | prefix_1 | prefix_2 | source_id | destination_id | message_type | fan_id | status | Fan Speed | Unused | suffix_1 | suffix_2 |
| Variable Type | uint8_t  | uint8_t  | uint8_t   | uint8_t        | uint8_t      | uint8_t | uint8_t | uint8_t  | uint8_t | uint8_t | uint8_t |
| Min Value     | 0x41     | 0x5a     | 1         | 4              | 0x20         | 1       | 0      | 0         | 0x00   | 0x59     | 0x42 |
| Max Value     | 0x41     | 0x5a     | 2         | 4              | 0x20         | 255     | 1      | 254       | 0x00   | 0x59     | 0x42 |
| Example Value | 0x41     | 0x5a     | 0x01      | 0x04           | 0x20         | 0x02    | 0x01   | 25        | 0x00   | 0x59     | 0x42 |

### Inverted
| Byte  | Variable Name      | Variable Type | Min Value | Max Value | Example Value |
|-------|-------------------|--------------|-----------|-----------|--------------|
| 1     | prefix_1         | uint8_t      | 0x41      | 0x41      | 0x41         |
| 2     | prefix_2         | uint8_t      | 0x5a      | 0x5a      | 0x5a         |
| 3     | source_id        | uint8_t      | 1         | 2         | 0x01         |
| 4     | destination_id   | uint8_t      | 4         | 4         | 0x04         |
| 5     | message_type     | uint8_t      | 0x20      | 0x20      | 0x20         |
| 6     | fan_id          | uint8_t      | 1         | 255       | 0x02         |
| 7     | status          | uint8_t      | 0         | 1         | 0x01         |
| 8     | Fan Speed       | uint8_t      | 0         | 254       | 25           |
| 9-62  | Unused          | uint8_t      | 0x00      | 0x00      | 0x00         |
| 63    | suffix_1        | uint8_t      | 0x59      | 0x59      | 0x59         |
| 64    | suffix_2        | uint8_t      | 0x42      | 0x42      | 0x42         |
